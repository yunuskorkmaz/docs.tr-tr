---
title: Veri kümesi içeriği kopyalama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: bee91a6406fd48894580ce6223a5682dbadab380
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757300"
---
# <a name="copying-dataset-contents"></a>Veri kümesi içeriği kopyalama
Bir kopyasını oluşturabilirsiniz bir <xref:System.Data.DataSet> böylece iş verilerle özgün veriler etkilenmeden veya iş verilerini bir kümeyle bir **DataSet**. Kopyalama işlemi sırasında bir **DataSet**, şunları yapabilirsiniz:  
  
-   Tam bir kopyasını oluşturmak **DataSet**şema, verileri, satır durumu bilgileri ve satır sürümleri dahil olmak üzere.  
  
-   Oluşturma bir **DataSet** varolan şema içeren **DataSet**, ancak yalnızca değiştirilmiş satırları. Değiştirilmiş tüm satırları döndürür veya belirli bir belirtin **DataRowState**. Satır durumları hakkında daha fazla bilgi için bkz: [satır durumları ve satır sürümleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
-   Şema veya ilişkisel yapısı kopyası **DataSet** herhangi bir satır kopyalama olmadan yalnızca,. Satırlar, var olan içine alınabilir <xref:System.Data.DataTable> kullanarak <xref:System.Data.DataTable.ImportRow%2A>.  
  
 Tam bir kopyasını oluşturmak için **DataSet** hem şema hem de veri içeren, kullanın <xref:System.Data.DataSet.Copy%2A> yöntemi **DataSet**. Aşağıdaki kod örneğinde, tam bir kopyasını oluşturmak gösterilmiştir **DataSet**.  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 Bir kopyasını oluşturmak için bir **DataSet** şema ve yalnızca verileri temsil eden içeren **eklenen**, **değiştirilen**, veya **silinmiş** satır kullanın <xref:System.Data.DataSet.GetChanges%2A> yöntemi **DataSet**. Aynı zamanda **GetChanges** geçirerek yalnızca satırları belirtilen satır durumuna döndürmek için bir **DataRowState** değer çağrılırken **GetChanges**. Aşağıdaki kod örneğinde nasıl iletileceğini gösterir bir **DataRowState** çağrılırken **GetChanges**.  
  
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
  
 Bir kopyasını oluşturmak için bir **DataSet** yalnızca şema içeren, kullanın <xref:System.Data.DataSet.Clone%2A> yöntemi **DataSet**. Ayrıca var olan satırları kopyalanan ekleyebilirsiniz **DataSet** kullanarak **ImportRow** yöntemi **DataTable**. **ImportRow** verileri, satır durumu ve satır sürüm bilgilerini belirtilen tabloya ekler. Sütun değerleri eklenir yalnızca sütun adı eşleştiği ve veri türü uyumludur.  
  
 Aşağıdaki kod örneğinde bir kopyasını oluşturur bir **DataSet** ve sonra özgün satırları ekler **DataSet** için **müşteriler** tablosundaki **veri kümesi**  kopya müşteriler için burada **CountryRegion alanı** sütun "Almanya" değerine sahip.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
