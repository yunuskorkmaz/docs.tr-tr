---
title: DataSet İçeriklerini Kopyalama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: de13e07eb5c19b8beffa724fec4a128c418a4fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151370"
---
# <a name="copying-dataset-contents"></a>DataSet İçeriklerini Kopyalama
Özgün verileri etkilemeden <xref:System.Data.DataSet> verilerle çalışabilmeniz veya **bir DataSet'ten**gelen verilerin bir alt kümesiyle çalışabilmeniz için bir kopyasını oluşturabilirsiniz. **Bir DataSet'i**kopyalarken şunları yapabilirsiniz:  
  
- Şema, veri, satır durumu bilgileri ve satır sürümleri de dahil olmak üzere **DataSet'in**tam bir kopyasını oluşturun.  
  
- Varolan bir **DataSet'in**şemasını içeren, ancak yalnızca değiştirilen satırları içeren bir **DataSet** oluşturun. Değiştirilen tüm satırları döndürebilir veya belirli bir **DataRowState**belirtebilirsiniz. Satır durumları hakkında daha fazla bilgi için [Bkz. Satır Durumları ve Satır Sürümleri.](row-states-and-row-versions.md)  
  
- **Yalnızca DataSet'in** şemaveya ilişkisel yapısını, herhangi bir satır kopyalamadan kopyalayın. Satırlar varolan <xref:System.Data.DataTable> bir kullanarak <xref:System.Data.DataTable.ImportRow%2A>içe aktarılabilir.  
  
 Hem şema hem de veri içeren **DataSet'in** tam <xref:System.Data.DataSet.Copy%2A> bir kopyasını oluşturmak için **DataSet'in**yöntemini kullanın. Aşağıdaki kod **örneği, DataSet'in**tam bir kopyasının nasıl oluşturulabildiğini gösterir.  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 Şema ve yalnızca **Eklenen,** **Değiştirilen**veya **Silinmiş** satırları temsil eden verileri içeren bir <xref:System.Data.DataSet.GetChanges%2A> **DataSet** kopyasını oluşturmak için **DataSet**yöntemini kullanın. GetChanges'ı ararken **DataRowState** değerini geçerek yalnızca belirli bir satır durumu olan satırları döndürmek için **GetChanges'ı** da kullanabilirsiniz. **GetChanges** Aşağıdaki kod **örneği, GetChanges'ı**ararken **DataRowState'in** nasıl geçirilebildiğini gösterir.  
  
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
  
 Yalnızca şema içeren bir **DataSet** kopyasını oluşturmak için <xref:System.Data.DataSet.Clone%2A> **DataSet**yöntemini kullanın. **DataTable'ın** **ImportRow** yöntemini kullanarak klonlanmış **DataSet'e** varolan satırları da ekleyebilirsiniz. **ImportRow,** belirtilen tabloya veri, satır durumu ve satır sürüm bilgilerini ekler. Sütun değerleri yalnızca sütun adının eşleştiği ve veri türünün uyumlu olduğu yerlerde eklenir.  
  
 Aşağıdaki kod örneği bir **DataSet** klonu oluşturur ve ardından **CountryRegion** sütununda "Almanya" değerine sahip müşteriler için **Veri Seti** klonunda orijinal **DataSet'ten** **müşteriler** tablosuna satırlar ekler.  
  
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
- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
