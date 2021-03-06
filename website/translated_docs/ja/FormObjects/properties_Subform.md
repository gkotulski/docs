---
id: propertiesSubform
title: Subform
---

---
## 削除を許可

Specifies if the user can delete subrecords in a list subform.

#### JSON 文法

| 名               | データタイプ  | とりうる値                     |
| --------------- | ------- | ------------------------- |
| deletableInList | boolean | true, false (デフォルトは true) |

#### 対象オブジェクト

[Subform](subform_overview.md)


---
## 詳細フォーム

You use this property to declare the detail form to use in the subform. It can be:

- a widget, i.e. a page-type subform endowed with specific functions. In this case, the [list subform](#list-form) and [Source](#source) properties must be empty or not present.   
  You can select a component form name when it is published in the component.
> You can generate [components](Concepts/components.md) providing additional functionalities through subforms.

- the detail form to associate a with the [list subform](#list-form). The detail form can be used to enter or view subrecords. It generally contains more information than the list subform. Naturally, the detail form must belong to the same table as the subform. You normally use an Output form as the list form and an Input form as the detail form. If you do not specify the form to use for full page entry, 4D automatically uses the default Input format of the table.


#### JSON 文法

| 名          | データタイプ | とりうる値                                                                                                                               |
| ---------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------- |
| detailForm | string | Name (string) of table or project form, a POSIX path (string) to a .json file describing the form, or an object describing the form |

#### 対象オブジェクト

[Subform](subform_overview.md)

---
## 空行をダブルクリック

Action to perform in case of a double-click on an empty line of a list subform. The following options are available:
- Do nothing: Ignores double-click.
- Add Record: Creates a new record in the subform and changes to editing mode. The record will be created directly in the list if the [Enterable in List] property is enabled. Otherwise, it will be created in page mode, in the [detail form](detail-form) associated with the subform.


#### JSON 文法

| 名                            | データタイプ | とりうる値                              |
| ---------------------------- | ------ | ---------------------------------- |
| doubleClickInEmptyAreaAction | string | "addSubrecord" or "" to do nothing |

#### 対象オブジェクト

[Subform](subform_overview.md)

#### 参照
[Double click on row](#double-click-on-row)

---
## 行をダブルクリック

`List subform`

Sets the action to be performed when a user double-clicks on a row in a list subform. The available options are:

*   **Do nothing** (default): Double-clicking a row does not trigger any automatic action.
*   **Edit Record**: Double-clicking a row displays the corresponding record in the [detail form defined for the list subform](#detail-form). The record is opened in read-write mode so it can be modified.
*   **Display Record**: Identical to the previous action, except that the record is opened in read-only mode so it cannot be modified.

Regardless of the action selected/chosen, the `On Double clicked` form event is generated.

For the last two actions, the On `Open Detail` form event is also generated. The `On Close Detail` is then generated when a record displayed in the detail form associated with the list box is about to be closed (regardless of whether or not the record was modified).

#### JSON 文法

| 名                      | データタイプ | とりうる値                               |
| ---------------------- | ------ | ----------------------------------- |
| doubleClickInRowAction | string | "editSubrecord", "displaySubrecord" |

#### 対象オブジェクト

[Subform](subform_overview.md)


#### 参照
[Double click on empty row](#double-click-on-empty-row)

---
## リスト更新可

When a list subform has this property enabled, the user can modify record data directly in the list, without having to use the [associated detail form](#detail-form).

> To do this, simply click twice on the field to be modified in order to switch it to editing mode (make sure to leave enough time between the two clicks so as not to generate a double-click).


#### JSON 文法

| 名               | データタイプ  | とりうる値       |
| --------------- | ------- | ----------- |
| enterableInList | boolean | true, false |


#### 対象オブジェクト

[Subform](subform_overview.md)


---
## リストフォーム

You use this property to declare the list form to use in the subform.  A list subform lets you enter, view, and modify data in other tables.

List subforms can be used for data entry in two ways: the user can enter data directly in the subform, or enter it in an [input form](#detail-form). In this configuration, the form used as the subform is referred to as the List form. The input form is referred to as the Detail form.

You can also allow the user to enter data in the List form.

#### JSON 文法

| 名        | データタイプ | とりうる値                                                                                                                               |
| -------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------- |
| listForm | string | Name (string) of table or project form, a POSIX path (string) to a .json file describing the form, or an object describing the form |

#### 対象オブジェクト

[Subform](subform_overview.md)



---
## ソース

Specifies the table that the list subform belongs to (if any).

#### JSON 文法

| 名     | データタイプ | とりうる値                             |
| ----- | ------ | --------------------------------- |
| table | string | 4D table name, or "" if no table. |

#### 対象オブジェクト

[Subform](subform_overview.md)

---
## 選択モード

Designates the option for allowing users to select rows:
- **None**: Rows cannot be selected if this mode is chosen. Clicking on the list will have no effect unless the [Enterable in list](subform_overview.md#enterable-in-list) option is enabled. The navigation keys only cause the list to scroll; the `On Selection Change` form event is not generated.
- **Single**: One row at a time can be selected in this mode. Clicking on a row will select it. A **Ctrl+click** (Windows) or **Command+click** (macOS) on a row toggles its state (between selected or not).  
  The Up and Down arrow keys select the previous/next row in the list. The other navigation keys scroll the list. The `On Selection Change` form event is generated every time the current row is changed.
- **Multiple**: Several rows can be selected simultaneously in this mode.
    - The selected subrecords are returned by the `GET HIGHLIGHTED RECORDS` command.
    - Clicking on the record will select it, but it does not modify the current record.
    - A **Ctrl+click** (Windows) or **Command+click** (macOS) on a record toggles its state (between selected or not). The Up and Down arrow keys select the previous/next record in the list. The other navigation keys scroll the list. The `On Selection Change` form event is generated every time the selected record is changed.


#### JSON 文法

| 名             | データタイプ | とりうる値                        |
| ------------- | ------ | ---------------------------- |
| selectionMode | string | "multiple", "single", "none" |

#### 対象オブジェクト

[Subform](subform_overview.md)
