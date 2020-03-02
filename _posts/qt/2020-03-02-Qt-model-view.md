---
title: "(Qt) Model과 View에 관한 사항 정리"
date: 2020-03-02 00:00:00 -0000
---

## 목차

* [시작]((https://goodayth.github.io/obs-sourcetree-model-view/#시작/)
* [모델 세팅](https://goodayth.github.io/obs-sourcetree-model-view/#모델-세팅/)
* [아이템 세팅](https://goodayth.github.io/obs-sourcetree-model-view/#아이템-세팅/)

---

## 시작

> 우선 Model이 어떻게 사용되는지 먼저 보기 위해 다음의 예제를 사용한다.

* [56. QStringListModel 사용](https://goodayth.github.io/Qt-GDI-S6-56/)

![](/file/image/qt-gdi-s6-56-image-1.png)

* [Github](https://github.com/GoodayTH/QStringListModel)

```cpp
Widget::Widget(QWidget *parent) :
    QWidget(parent),
    ui(new Ui::Widget)
{
    ui->setupUi(this);
    colorList = QColor::colorNames();

    model  = new QStringListModel(colorList,this);

    ui->listView->setModel(model);      
    // 사용법은 간단하다 특정 widget에 setmodel을 지정하면 model이 선정!
}
```

---

## 모델 세팅

> 그럼 모델의 수정은 어떻게 하는데?<br>
> 다음의 예제에서 잘 설명이 된다.

* [58. list, table, tree personal view 만들기](https://goodayth.github.io/Qt-GDI-S6-58/)

![](/file/image/qt-gdi-s6-58-image-1.png)

* [Github](https://github.com/GoodayTH/personalmodel)

```cpp
Widget::Widget(QWidget *parent) :
    QWidget(parent),
    ui(new Ui::Widget)
{
    ui->setupUi(this);

    PersonModel * model = new PersonModel(this);

    ui->listView->setModel(model);
    ui->tableView->setModel(model);
    ui->treeView->setModel(model);
    // 이 예제에서는 model을 생성 후 각 widget에 모델을 설정하고 어떻게 출력이 되는지 본다.
}
```

```cpp
// 모델은 이렇게 구현된다.

// PersonModel.h
#ifndef PERSONMODEL_H
#define PERSONMODEL_H

#include <QAbstractListModel>
#include "person.h"

class PersonModel : public QAbstractListModel
{
    Q_OBJECT
public:
    explicit PersonModel(QObject *parent = nullptr);
    ~PersonModel() override;
    // QAbstractItemModel interface
    int rowCount(const QModelIndex &parent) const override;
    QVariant data(const QModelIndex &index, int role) const override;
signals:
public slots:
private:
    QList<Person * > persons;
};

#endif // PERSONMODEL_H
```

```cpp
// PersonModel.cpp
#include "personmodel.h"

PersonModel::PersonModel(QObject *parent) : QAbstractListModel(parent)
{
    //Populate with initial data
    persons.append (new Person("Jamie Lannister","red",33));
    persons.append(new Person("Marry Lane","cyan",26));
    persons.append(new Person("Steve Moors","yellow",44));
    persons.append(new Person("Victor Trunk","dodgerblue",30));
    persons.append(new Person("Ariel Geeny","blue",33));
    persons.append(new Person("Knut Vikran","lightblue",26));
}

PersonModel::~PersonModel()
{
    qDeleteAll(persons);
}

int PersonModel::rowCount(const QModelIndex &parent) const
{
    Q_UNUSED(parent);
    return  persons.size();
}

QVariant PersonModel::data(const QModelIndex &index, int role) const
{
    // 이렇게 설정하면 각 widget에 맞게 데이터가 들어가게 된다.
    if (index.row() < 0 || index.row() >= persons.count())
        return QVariant();
    Person * person = persons[index.row()];
    if(role == Qt::DisplayRole){
        return  person->names() + " " + QString::number(person->age())
                +" " + person->favoriteColor();
    }

    if(role == Qt::ToolTipRole){
        return  person->names() + " " + QString::number(index.row());
    }
    return  QVariant();

}
```

---

## 아이템 세팅

> 아래 예제가 적당하다.

* [64. item paint 기능 추가](https://goodayth.github.io/Qt-GDI-S6-64/)

![](/file/image/qt-gdi-s6-64-image-1.png)

* [Github](https://github.com/GoodayTH/paintitem)

```cpp
Widget::Widget(QWidget *parent) :
    QWidget(parent),
    ui(new Ui::Widget)
{
    ui->setupUi(this);

    PersonDelegate * personDelegate = new PersonDelegate(this);

    model = new PersonModel(this);

    ui->listView->setModel(model);
    ui->tableView->setModel(model);
    ui->tableView->setItemDelegateForColumn(2,personDelegate);
    ui->treeView->setModel(model);
    ui->treeView->setItemDelegate(personDelegate);
    // setItemDelegateForColumn, setItemDelegate을 통해서 새로 그릴수 있다.

    ui->tableView->setSelectionModel(ui->listView->selectionModel());
    ui->treeView->setSelectionModel(ui->listView->selectionModel());
}
```

```cpp
#ifndef PERSONDELEGATE_H
#define PERSONDELEGATE_H

#include <QStyledItemDelegate>

class PersonDelegate : public QStyledItemDelegate
{
    Q_OBJECT
public:
    explicit PersonDelegate(QObject *parent = nullptr);


    // QAbstractItemDelegate interface
public:
    QWidget *createEditor(QWidget *parent, const QStyleOptionViewItem &option, const QModelIndex &index) const override;
    void setEditorData(QWidget *editor, const QModelIndex &index) const override;
    void setModelData(QWidget *editor, QAbstractItemModel *model, const QModelIndex &index) const override;
    void updateEditorGeometry(QWidget *editor, const QStyleOptionViewItem &option, const QModelIndex &index) const override;
    QSize sizeHint(const QStyleOptionViewItem &option, const QModelIndex &index) const override;
    void paint(QPainter *painter, const QStyleOptionViewItem &option, const QModelIndex &index) const override;
};

#endif // PERSONDELEGATE_H
```

```cpp
#include "persondelegate.h"
#include "personmodel.h"
#include <QComboBox>
#include <QPainter>

PersonDelegate::PersonDelegate(QObject *parent) : QStyledItemDelegate(parent)
{

}

QWidget *PersonDelegate::createEditor(QWidget *parent, const QStyleOptionViewItem &option,
                                      const QModelIndex &index) const
{
    if(index.column() == 2){

        QComboBox *editor = new QComboBox(parent);

        foreach (QString color, QColor::colorNames()) {
            QPixmap mPix(50,50);
            mPix.fill(QColor(color));
            editor->addItem(QIcon(mPix),color);
        }

        return editor;
    }else{
        return QStyledItemDelegate::createEditor(parent,option,index);
    }

}

void PersonDelegate::setEditorData(QWidget *editor, const QModelIndex &index) const
{
    if(index.column() == 2){
        QComboBox *combo = static_cast<QComboBox *>(editor);
        int idx = QColor::colorNames().indexOf(index.data(Qt::DisplayRole).toString());
        combo->setCurrentIndex(idx);
    }else{
        QStyledItemDelegate::setEditorData(editor,index);
    }

}

void PersonDelegate::setModelData(QWidget *editor, QAbstractItemModel *model,
                                  const QModelIndex &index) const
{
    if(index.column() == 2){
        QComboBox *combo = static_cast<QComboBox *>(editor);
        model->setData(index,combo->currentText(),PersonModel::FavoriteColorRole);
        //model->setData(index,combo->currentText(),Qt::EditRole);
    }else{
        QStyledItemDelegate::setModelData(editor,model,index);
    }

}

void PersonDelegate::updateEditorGeometry(QWidget *editor,
                                          const QStyleOptionViewItem &option,
                                          const QModelIndex &index) const
{
    Q_UNUSED(index);

    editor->setGeometry(option.rect);

}

QSize PersonDelegate::sizeHint(const QStyleOptionViewItem &option, const QModelIndex &index) const
{
    return QStyledItemDelegate::sizeHint(option, index).
            expandedTo(QSize(64,option.fontMetrics.height() + 10));
}

void PersonDelegate::paint(QPainter *painter, const QStyleOptionViewItem &option,
                           const QModelIndex &index) const
{
     if(index.column() == 2){

         //Highlight selected cell
         if (option.state & QStyle::State_Selected)
                     painter->fillRect(option.rect, option.palette.highlight());

         //Get fav color
         QString favColor = index.data(PersonModel::FavoriteColorRole).toString();

         painter->save();

         painter->setBrush(QBrush(QColor(favColor)));

         //Draw color rect
         painter->drawRect(option.rect.adjusted(3,3,-3,-3));

         //Text Size
         QSize textSize= option.fontMetrics.size(Qt::TextSingleLine,favColor);

         painter->setBrush(QBrush(QColor(Qt::white)));


         //Adustments for inner white rectangle
         int widthAdjust = (option.rect.width() - textSize.width())/2 - 3;
         int heightAdjust = (option.rect.height() - textSize.height())/2;

         painter->drawRect(option.rect.adjusted(widthAdjust,heightAdjust,
                                                -widthAdjust,-heightAdjust));

         painter->drawText(option.rect,favColor,Qt::AlignHCenter|Qt::AlignVCenter);


         painter->restore();

     }else{
         QStyledItemDelegate::paint(painter,option,index);
     }

}
```