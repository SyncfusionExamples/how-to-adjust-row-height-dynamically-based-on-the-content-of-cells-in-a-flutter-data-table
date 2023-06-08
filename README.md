# How to adjust row height dynamically based on the content of cells in a Flutter DataTable (SfDataGrid)?

In this article, We will explain how to modify the row heights in a [Flutter DataGrid](https://www.syncfusion.com/flutter-widgets/flutter-datagrid) to ensure that all the content is adequately displayed, regardless of its length.

## STEP 1:
Initialize the [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) widget with all the required properties. Set the [onQueryRowHeight](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/onQueryRowHeight.html) callback to handle row height adjustments dynamically. Use the [RowHeightDetails.getIntrinsicRowHeight](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/RowHeightDetails/getIntrinsicRowHeight.html) method to compute the suitable row height by considering the content of the cells in that row. To obtain the intrinsic height for a specific row, you can provide details.rowIndex as an argument to the getIntrinsicRowHeight method.

 ```dart
@override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Syncfusion Flutter DataGrid'),
      ),
      body: SfDataGrid(
        source: employeeDataSource,
        columnWidthMode: ColumnWidthMode.fill,
        onQueryRowHeight: (details) {
          return details.getIntrinsicRowHeight(details.rowIndex);
        },
        columns: <GridColumn>[
          GridColumn(
              columnName: 'id',
              label: Container(
                  padding: EdgeInsets.all(16.0),
                  alignment: Alignment.center,
                  child: Text(
                    'ID',
                    softWrap: true,
                  ))),
          GridColumn(
              columnName: 'name',
              label: Container(
                  padding: EdgeInsets.all(8.0),
                  alignment: Alignment.center,
                  child: Text(
                    'Name of the Employee ',
                    softWrap: true,
                  ))),
          GridColumn(
              columnName: 'designation',
              label: Container(
                  padding: EdgeInsets.all(8.0),
                  alignment: Alignment.center,
                  child: Text(
                    'Role of the Employee',
                    softWrap: true,
                  ))),
          GridColumn(
              columnName: 'salary',
              label: Container(
                  padding: EdgeInsets.all(8.0),
                  alignment: Alignment.center,
                  child: Text(
                    'Salary',
                    softWrap: true,
                  ))),
        ],
      ),
    );
  }

 ```