---
title: DataTable’daki Verileri Görüntüleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: c13f0b802b2714a17ea4014625a65ebd1b0011f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785859"
---
# <a name="viewing-data-in-a-datatable"></a>DataTable’daki Verileri Görüntüleme

**DataTable**'ın **Satırlar** ve **sütunlar** koleksiyonlarını kullanarak <xref:System.Data.DataTable> bir öğesinin içeriğine erişebilirsiniz. Ayrıca, <xref:System.Data.DataTable.Select%2A> arama ölçütleri, sıralama düzeni ve satır durumu gibi ölçütlere göre **DataTable** içindeki verilerin alt kümelerini döndürmek için yöntemini de kullanabilirsiniz. Ek olarak, bir birincil anahtar <xref:System.Data.DataRowCollection.Find%2A> değeri kullanarak belirli bir satırı ararken **DataRowCollection** yöntemini de kullanabilirsiniz.

**DataTable** nesnesinin <xref:System.Data.DataRow> **Select** yöntemi, belirtilen ölçütlerle eşleşen bir nesne kümesi döndürüyor. Bir filtre ifadesinin, Sort ifadesinin ve **DataViewRowState**bağımsız değişkenlerini alır ' i **seçin** . Filtre ifadesi,, `LastName = 'Smith'`gibi **DataColumn** değerlerine göre döndürülecek satırları belirler. Sıralama ifadesi, örneğin `LastName ASC, FirstName ASC`sütunları SıRALAMAK için standart SQL kurallarını izler. İfadeleri yazma hakkında kurallar için bkz <xref:System.Data.DataColumn.Expression%2A> . **DataColumn** sınıfının özelliği.

> [!TIP]
> **DataTable**'ın <xref:System.Data.DataView> **Select** yöntemine bir dizi çağrı gerçekleştiriyorsanız, öncelikle **DataTable**için bir oluşturarak performansı artırabilirsiniz. **DataView** oluşturmak tablo satırlarını dizine ekler. **Select** yöntemi daha sonra bu dizini kullanır ve bu da sorgu sonucunu oluşturma süresini önemli ölçüde azaltır. **DataTable**Için bir **DataView** oluşturma hakkında daha fazla bilgi için bkz. [DataView](dataviews.md).

**Select** yöntemi, bir <xref:System.Data.DataViewRowState>öğesine göre hangi satır sürümünün görüntüleneceğini veya değiştirileceğini belirler. Aşağıdaki tabloda olası **DataViewRowState** numaralandırma değerleri açıklanmaktadır.

|DataViewRowState değeri|Açıklama|
|----------------------------|-----------------|
|**CurrentRows**|Değiştirilmemiş, eklenen ve değiştirilen satırları içeren geçerli satırlar.|
|**Miyor**|Silinen bir satır.|
|**ModifiedCurrent**|Özgün verilerin değiştirilmiş bir sürümü olan geçerli bir sürüm. (Bkz. **Modifiedorijinal.** )|
|**Modifiedorijinal**|Değiştirilen tüm satırların orijinal sürümü. Geçerli sürüm, **ModifiedCurrent**kullanılarak kullanılabilir.|
|**Eklenirse**|Yeni bir satır.|
|**Yok.**|Yok.|
|**OriginalRows**|Değiştirilmemiş ve silinen satırlar dahil olmak üzere orijinal satırlar.|
|**Değiştirilmediği**|Değiştirilmemiş bir satır.|

Aşağıdaki örnekte, **veri kümesi** nesnesi filtrelenmiştir, böylece yalnızca **DataViewRowState** **CurrentRows**olarak ayarlanan satırlarla çalışmanız gerekir.

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

**Select** yöntemi, farklı **RowState** değerlerini veya alan değerlerini içeren satırları döndürmek için kullanılabilir. Aşağıdaki örnek, silinmiş tüm satırlara başvuran bir **DataRow** dizisi döndürür ve **CustId** sütununun 5 ' ten büyük olduğu **CustLName**tarafından sıralanan tüm satırlara başvuran başka bir **DataRow** dizisi döndürür. **Silinen** satırdaki bilgileri görüntüleme hakkında daha fazla bilgi için bkz. [Satır durumları ve satır sürümleri](row-states-and-row-versions.md).

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

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataViewRowState>
- [DataTable Verilerini Düzenleme](manipulating-data-in-a-datatable.md)
- [Satır Durumları ve Satır Sürümleri](row-states-and-row-versions.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
