---
title: DataSet İçeriklerini Kopyalama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: cb2a172ac4e6a0ce4852f4c7cf7044583d9ab6c4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077776"
---
# <a name="copying-dataset-contents"></a>DataSet İçeriklerini Kopyalama
Bir kopyasını oluşturabilirsiniz bir <xref:System.Data.DataSet> böylece özgün veriler etkilenmeden verileri ile çalışma veya iş verilerin bir alt kümesi ile bir **veri kümesi**. Kopyalama işlemi sırasında bir **veri kümesi**, şunları yapabilirsiniz:  
  
-   Tam bir kopyasını oluşturma **veri kümesi**şema, veri, satır durum bilgilerini ve satır sürümleri dahil olmak üzere.  
  
-   Oluşturma bir **veri kümesi** varolan şema içeren **veri kümesi**, ancak yalnızca değiştirilen satırları. Değiştirilmiş tüm satırları döndürür veya belirli bir belirtin **DataRowState**. Satır durumları hakkında daha fazla bilgi için bkz: [satır durumları ve satır sürümleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
-   Şema veya ilişkisel yapısını kopyası **veri kümesi** yalnızca, tüm satırları kopyalama olmadan. Satırları, varolan içine aktarılabilir <xref:System.Data.DataTable> kullanarak <xref:System.Data.DataTable.ImportRow%2A>.  
  
 Tam bir kopyasını oluşturmak için **veri kümesi** hem şema hem de veri içeren, kullanın <xref:System.Data.DataSet.Copy%2A> yöntemi **veri kümesi**. Aşağıdaki kod örneği, tam bir kopyasını oluşturma işlemi gösterilmektedir **veri kümesi**.  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 Bir kopyasını oluşturmak için bir **veri kümesi** içeren şema ve yalnızca verileri temsil eden **eklenen**, **değiştirilen**, veya **silinmiş** satır kullanın <xref:System.Data.DataSet.GetChanges%2A> yöntemi **veri kümesi**. Ayrıca **GetChanges** geçirerek yalnızca belirtilen satır durumuna sahip satır döndürülecek bir **DataRowState** değer çağrılırken **GetChanges**. Aşağıdaki kod örneğinde nasıl geçirileceğini gösterir. bir **DataRowState** çağırırken **GetChanges**.  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 Bir kopyasını oluşturmak için bir **veri kümesi** kullanmak, yalnızca şema içeren <xref:System.Data.DataSet.Clone%2A> yöntemi **veri kümesi**. Ayrıca var olan satır kopyalanan ekleyebilirsiniz **veri kümesi** kullanarak **ImportRow** yöntemi **DataTable**. **ImportRow** veri satırı durumu ve satır sürüm bilgilerini belirtilen tabloya ekler. Sütun değerleri eklenir yalnızca sütun adı eşleştiği ve veri türü uyumludur.  
  
 Aşağıdaki kod örneği bir kopyasını oluşturur. bir **veri kümesi** ve ardından özgün satırları ekler **veri kümesi** için **müşteriler** tablosundaki **veri kümesi**  kopya müşteriler için burada **CountryRegion alanı** sütununun değeri "Germany".  
  
```vb  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =   
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
