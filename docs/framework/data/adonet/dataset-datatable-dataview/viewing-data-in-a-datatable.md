---
title: DataTable'daki verileri görüntüleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: de745633060dd4f7b1610492d0ff57ec7a4f545b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43536872"
---
# <a name="viewing-data-in-a-datatable"></a>DataTable'daki verileri görüntüleme
İçeriğini erişebileceğiniz bir <xref:System.Data.DataTable> kullanarak **satırları** ve **sütunları** koleksiyonları **DataTable**. Ayrıca <xref:System.Data.DataTable.Select%2A> verilerin alt kümelerine döndürülecek yöntemi bir **DataTable** arama ölçütleri gibi ölçütlere göre sıralama düzeni ve satır durumu. Ayrıca, kullanabileceğiniz <xref:System.Data.DataRowCollection.Find%2A> yöntemi **DataRowCollection** birincil bir anahtar değeri kullanarak belirli bir satır için arama yaparken.  
  
 **Seçin** yöntemi **DataTable** nesnesi döndüren bir dizi <xref:System.Data.DataRow> belirtilen ölçütlerle eşleşen nesneleri. **Seçin** sıralama ifadesi bir filtre ifadesi, isteğe bağlı bağımsız değişkeni alır ve **DataViewRowState**. Filtre ifadesi göre döndürülecek hangi satırların tanımlayan **DataColumn** gibi değerleri `LastName = 'Smith'`. Sıralama ifadesi sütunları, örneğin sıralama için standart SQL kurallarına `LastName ASC, FirstName ASC`. İfadeler yazma hakkında daha fazla kuralları için bkz: <xref:System.Data.DataColumn.Expression%2A> özelliği **DataColumn** sınıfı.  
  
> [!TIP]
>  Çağrı sayısı gerçekleştiriyorsanız **seçin** yöntemi bir **DataTable**, ilk oluşturarak, performansı artırmak bir <xref:System.Data.DataView> için **DataTable**. Oluşturma **DataView** tablonun satırlarını dizinler. **Seçin** yöntemi sonra dizin, usees sorgu sonucu üretmek için gereken süreyi önemli ölçüde azaltır. Oluşturma hakkında daha fazla bilgi için bir **DataView** için bir **DataTable**, bkz: [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
 **Seçin** yöntemi belirler satırları görüntülemek veya yönetmek için hangi sürümünün temel bir <xref:System.Data.DataViewRowState>. Aşağıdaki tabloda olası açıklanmaktadır **DataViewRowState** sabit listesi değerleri.  
  
|DataViewRowState değeri|Açıklama|  
|----------------------------|-----------------|  
|**CurrentRows**|Geçerli satır değişmeden, eklenen ve değiştirilmiş satırları dahil etme.|  
|**silindi**|Silinen bir satır.|  
|**ModifiedCurrent**|Özgün veri değiştirilmiş bir sürümü olan bir geçerli sürümü. (Bkz **ModifiedOriginal**.)|  
|**ModifiedOriginal**|Tüm değiştirilmiş satırları orijinal sürümü. Geçerli sürüm kullanılarak kullanılabilir **ModifiedCurrent**.|  
|**Eklendi**|Yeni bir satır.|  
|**Yok**|Yok.|  
|**OriginalRows**|Özgün satır, değişmez ve silinen satırları dahil etme.|  
|**değişmedi**|Değişmeyen bir satır.|  
  
 Aşağıdaki örnekte, **veri kümesi** böylece yalnızca satır ile ayarlanmış çalıştığınız nesne filtrelenmiş **DataViewRowState** ayarlanır **CurrentRows**.  
  
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
  
 **Seçin** bakımından farklı olan satırlar döndürülecek yöntemi kullanılabilir **RowState** değerleri veya alan değerleri. Aşağıdaki örnek döndüren bir **DataRow** silinmiş ve başka döndürür tüm satırları başvuran bir dizi **DataRow** sıralı başvuran tüm satırları, dizinin tarafından **CustLName**burada **CustId** sütun, 5'ten büyüktür. Bilgileri görüntüleme hakkında bilgi için **silinmiş** satır bkz [satır durumları ve satır sürümleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
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
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
