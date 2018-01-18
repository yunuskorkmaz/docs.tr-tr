---
title: "Bir DataTable tablosundaki verileri görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2576c95ad7739d28e2ca822fd13fb6f176900814
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="viewing-data-in-a-datatable"></a>Bir DataTable tablosundaki verileri görüntüleme
İçeriğine erişmek için bir <xref:System.Data.DataTable> kullanarak **satırları** ve **sütunları** koleksiyonları **DataTable**. Aynı zamanda <xref:System.Data.DataTable.Select%2A> veri alt kümesi döndürülecek yöntemi bir **DataTable** arama ölçütleri gibi ölçütlere göre sıralama ve satır durumu. Ayrıca, kullanabileceğiniz <xref:System.Data.DataRowCollection.Find%2A> yöntemi **DataRowCollection** bir birincil anahtar değeri kullanarak belirli bir satır için arama yaparken.  
  
 **Seçin** yöntemi **DataTable** nesnesi döndüren bir dizi <xref:System.Data.DataRow> belirtilen ölçütlerle eşleşen nesneler. **Seçin** bir filtre ifadesi, sıralama ifadesi, isteğe bağlı bağımsız değişkenleri alır ve **DataViewRowState**. Filtre ifadesi temel alınarak döndürülecek hangi satırların tanımlayan **DataColumn** gibi değerler `LastName = 'Smith'`. Sütunları, örneğin sıralama için standart SQL kuralları sıralama ifadesi izler `LastName ASC, FirstName ASC`. İfadeleri yazma hakkında daha fazla kuralları için bkz: <xref:System.Data.DataColumn.Expression%2A> özelliği **DataColumn** sınıfı.  
  
> [!TIP]
>  Çağrı sayısı gerçekleştiriyorsanız **seçin** yöntemi bir **DataTable**, ilk oluşturarak performansı artırabilirsiniz bir <xref:System.Data.DataView> için **DataTable**. Oluşturma **DataView** tablonun satırlarını dizinler. **Seçin** yöntemi sonra dizin, usees sorgu sonucu oluşturmak için gereken süre önemli ölçüde azaltır. Oluşturma hakkında daha fazla bilgi için bir **DataView** için bir **DataTable**, bkz: [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
 **Seçin** yöntemi belirler satırları görüntülemek veya değiştirmek için hangi sürümünün dayalı bir <xref:System.Data.DataViewRowState>. Aşağıdaki tabloda olası açıklanmaktadır **DataViewRowState** numaralandırma değerleri.  
  
|DataViewRowState değeri|Açıklama|  
|----------------------------|-----------------|  
|**CurrentRows**|Geçerli satır değişmeden, eklenen ve değiştirilen satırları dahil olmak üzere.|  
|**Deleted**|Silinen satır.|  
|**ModifiedCurrent**|Özgün veriler değiştirilmiş bir sürümünü olan bir geçerli sürümü. (Bkz **ModifiedOriginal**.)|  
|**ModifiedOriginal**|Tüm değiştirilen satırları özgün sürümü. Geçerli sürümdür kullanılabilir kullanarak **ModifiedCurrent**.|  
|**Eklenen**|Yeni bir satır.|  
|**Yok**|Yok.|  
|**OriginalRows**|Özgün satırlar dahil olmak üzere, değiştirmeden ve silinen satır.|  
|**Değişmedi**|Değiştirilmemiş bir satır.|  
  
 Aşağıdaki örnekte, **DataSet** böylece yalnızca satırlarla özelliği çalıştığınız nesne filtre **DataViewRowState** ayarlanır **CurrentRows**.  
  
```vb  
Dim column As DataColumn  
Dim row As DataRow  
  
Dim currentRows() As DataRow = _  
    workTable.Select(Nothing, Nothing, DataViewRowState.CurrentRows)  
  
If (currentRows.Length < 1 ) Then  
  Console.WriteLine("No Current Rows Found")  
Else  
  For Each column in workTable.Columns  
    Console.Write(vbTab & column.ColumnName)  
  Next  
  
  Console.WriteLine(vbTab & "RowState")  
  
  For Each row In currentRows  
    For Each column In workTable.Columns  
      Console.Write(vbTab & row(column).ToString())  
    Next  
  
    Dim rowState As String = _  
        System.Enum.GetName(row.RowState.GetType(), row.RowState)  
    Console.WriteLine(vbTab & rowState)  
  Next  
End If  
```  
  
```csharp  
DataRow[] currentRows = workTable.Select(  
    null, null, DataViewRowState.CurrentRows);  
  
if (currentRows.Length < 1 )  
  Console.WriteLine("No Current Rows Found");  
else  
{  
  foreach (DataColumn column in workTable.Columns)  
    Console.Write("\t{0}", column.ColumnName);  
  
  Console.WriteLine("\tRowState");  
  
  foreach (DataRow row in currentRows)  
  {  
    foreach (DataColumn column in workTable.Columns)  
      Console.Write("\t{0}", row[column]);  
  
    Console.WriteLine("\t" + row.RowState);  
  }  
}  
```  
  
 **Seçin** yöntemi, farklı olan satırlar döndürülecek kullanılabilir **RowState** değerleri veya alan değerleri. Aşağıdaki örnek döndüren bir **DataRow** silinmiş ve başka döndüren tüm satırları başvuruda bulunan bir dizi **DataRow** tüm satırları başvuran dizi göre sıralayarak **CustLName**, burada **CustId** sütundur 5'ten büyük. Bilgileri görüntüleme hakkında bilgi için **silinmiş** satır için bkz: [satır durumları ve satır sürümleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
```vb  
' Retrieve all deleted rows.  
Dim deletedRows() As DataRow = workTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
' Retrieve rows where CustID > 5, and order by CustLName.  
Dim custRows() As DataRow = workTable.Select( _  
    "CustID > 5", "CustLName ASC")  
```  
  
```csharp  
// Retrieve all deleted rows.  
DataRow[] deletedRows = workTable.Select(  
    null, null, DataViewRowState.Deleted);  
  
// Retrieve rows where CustID > 5, and order by CustLName.  
DataRow[] custRows = workTable.Select("CustID > 5", "CustLName ASC");  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataViewRowState>  
 [DataTable Verilerini Düzenleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [Satır Durumları ve Satır Sürümleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
