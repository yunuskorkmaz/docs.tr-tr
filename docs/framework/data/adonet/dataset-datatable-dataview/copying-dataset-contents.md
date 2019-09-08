---
title: DataSet İçeriklerini Kopyalama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: d8a7762c4ec5d650295ca0626180285723549051
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786520"
---
# <a name="copying-dataset-contents"></a>DataSet İçeriklerini Kopyalama
Özgün verileri etkilemeden verilerle çalışabilmeniz veya bir <xref:System.Data.DataSet> veri **kümesindeki**verilerin bir alt kümesiyle çalışmanız için bir kopyasını oluşturabilirsiniz. Bir **veri kümesini**kopyalarken şunları yapabilirsiniz:  
  
- Şema, veri, satır durum bilgileri ve satır sürümleri dahil olmak üzere **veri kümesinin**tam bir kopyasını oluşturun.  
  
- Mevcut bir **veri kümesinin**şemasını Içeren bir **veri kümesi** oluşturun, ancak yalnızca değiştirilmiş olan satırları. Değiştirilen tüm satırları döndürebilir veya belirli bir **DataRowState**belirtebilirsiniz. Satır durumları hakkında daha fazla bilgi için bkz. [Satır durumları ve satır sürümleri](row-states-and-row-versions.md).  
  
- Herhangi bir satırı kopyalamadan yalnızca **veri kümesinin** şemasını veya ilişkisel yapısını kopyalayın. Satırlar var olan <xref:System.Data.DataTable> bir using <xref:System.Data.DataTable.ImportRow%2A>öğesine aktarılabilir.  
  
 Hem şema hem de verileri içeren **veri kümesinin** tam bir kopyasını oluşturmak için, <xref:System.Data.DataSet.Copy%2A> **veri kümesinin**yöntemini kullanın. Aşağıdaki kod örneği, **veri kümesinin**tam bir kopyasının nasıl oluşturulacağını gösterir.  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 Şemayı ve yalnızca **eklenen**, **değiştirilen**veya **silinen** satırları temsil eden verileri içeren bir <xref:System.Data.DataSet.GetChanges%2A> **veri kümesinin** kopyasını oluşturmak için, **veri kümesinin**yöntemini kullanın. **GetChanges 'ı çağırırken yalnızca**belirtilen satır durumundaki satırları döndürmek için **GetChanges** 'ı da kullanabilirsiniz. Aşağıdaki kod örneği, **GetChanges**çağrılırken **DataRowState** 'in nasıl geçirileceğini gösterir.  
  
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
  
 Yalnızca şemayı içeren bir **veri kümesinin** kopyasını oluşturmak için <xref:System.Data.DataSet.Clone%2A> **veri kümesinin**yöntemini kullanın. Ayrıca, **DataTable**'ın **ImportRow** yöntemini kullanarak kopyalanan **veri kümesine** mevcut satırları ekleyebilirsiniz. **ImportRow** , belirtilen tabloya veri, satır durumu ve satır sürümü bilgilerini ekler. Sütun değerleri yalnızca sütun adının eşleştiği ve veri türünün uyumlu olduğu yerlerde eklenir.  
  
 Aşağıdaki kod örneği, bir **veri kümesinin** kopyasını oluşturur ve ardından orijinal **veri kümesindeki** satırları, **Ülke Bölgesi** sütununun "Almanya" değerine sahip olduğu müşteriler için **veri kümesi** kopyasının **müşteriler** tablosuna ekler. ".  
  
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
