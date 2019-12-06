
```js
    
    var that = this;
      var aData = [
        {
          qual: '1',
          ol: 100
        },
        {
          qual: '2',
          ol: 200
        }
      ];

      var aColumnData = [
        {
          columnId: 'qual'
        },
        {
          columnId: 'ol'
        }
        
      ];

      var oMetaModel = new sap.ui.model.json.JSONModel(aColumnData);
      var oDataModel = new sap.ui.model.json.JSONModel(aData);

      this.getView().setModel(oMetaModel, 'column');
      this.getView().setModel(oDataModel, 'data');

      var oTable = this.getView().byId('MyTable');

      oTable.bindColumns('column>/', function(index, oContext) {
        var sColumnId = oContext.getObject().columnId;

        return new sap.ui.table.Column({
          id: sColumnId,
          label: sColumnId,
          template: that.renderFunc(sColumnId)
        });
      });
      oTable.bindRows('data>/');


```