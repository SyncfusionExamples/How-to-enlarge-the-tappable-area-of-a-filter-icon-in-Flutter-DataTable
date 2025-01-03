# How to increase the tappable area of a filter icon in Flutter DataTable?

In this article, we will show you how to increase the tappable area of filter icon in [Flutter DataTable](https://www.syncfusion.com/flutter-widgets/flutter-datagrid).

Initialize the [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) widget with all the necessary properties. By default, the filter icon shares space with the sort icon in the column header. To customize the filter icon, use the [SfDataGridThemeData.filterIcon](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/filterIcon.html) property. Use a [builder](https://api.flutter.dev/flutter/widgets/Builder-class.html) widget to update the icon dynamically based on its state-either filtering or filtered. Wrap the icon in a SizedBox or Container and specify the desired width and height to create a tappable area for the filter icon. This ensures a clearly defined space, enabling consistent and reliable interaction with the filter popup.

```dart
SfDataGridThemeData(
  filterIcon: Builder(
    builder: (context) {
      Widget? icon;
      String columnName = '';
      context.visitAncestorElements((element) {
        if (element is GridHeaderCellElement) {
          columnName = element.column.columnName;
        }
        return true;
      });
      var column = employeeDataSource.filterConditions.keys
          .where((element) => element == columnName)
          .firstOrNull;
      if (column != null) {
        icon = const Icon(
          Icons.filter_alt_outlined,
          size: 20,
          color: Colors.purple,
        );
      }
      return Container(
        color: Colors.greenAccent,
        width: 40,
        height: 40,
        child: icon ??
            const Icon(
              Icons.filter_alt_off_outlined,
              size: 20,
              color: Colors.deepOrange,
            ),
      );
    },
  ),
)
```

You can download this example on [GitHub](https://github.com/SyncfusionExamples/How-to-enlarge-the-tappable-area-of-a-filter-icon-in-Flutter-DataTable).