---
description: 'Hakkında daha fazla bilgi edinin: DataTable içindeki verileri görüntüleme'
title: DataTable’daki Verileri Görüntüleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: ffaa8283da17c98fc58486af8dad741a61bbafc8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651385"
---
# <a name="viewing-data-in-a-datatable"></a>DataTable’daki Verileri Görüntüleme

<xref:System.Data.DataTable> **DataTable**'ın **Satırlar** ve **sütunlar** koleksiyonlarını kullanarak bir öğesinin içeriğine erişebilirsiniz. Ayrıca, <xref:System.Data.DataTable.Select%2A> arama ölçütleri, sıralama düzeni ve satır durumu gibi ölçütlere göre **DataTable** içindeki verilerin alt kümelerini döndürmek için yöntemini de kullanabilirsiniz. Ek olarak, <xref:System.Data.DataRowCollection.Find%2A> bir birincil anahtar değeri kullanarak belirli bir satırı ararken **DataRowCollection** yöntemini de kullanabilirsiniz.

**DataTable** nesnesinin **Select** yöntemi, <xref:System.Data.DataRow> belirtilen ölçütlerle eşleşen bir nesne kümesi döndürüyor. Bir filtre ifadesinin, Sort ifadesinin ve **DataViewRowState** bağımsız değişkenlerini alır ' i **seçin** . Filtre ifadesi,, gibi **DataColumn** değerlerine göre döndürülecek satırları belirler `LastName = 'Smith'` . Sıralama ifadesi, örneğin sütunları sıralamak için standart SQL kurallarını izler `LastName ASC, FirstName ASC` . İfadeleri yazma hakkında kurallar için bkz <xref:System.Data.DataColumn.Expression%2A> . **DataColumn** sınıfının özelliği.

> [!TIP]
> **DataTable**'ın **Select** yöntemine bir dizi çağrı gerçekleştiriyorsanız, öncelikle <xref:System.Data.DataView> **DataTable** için bir oluşturarak performansı artırabilirsiniz. **DataView** oluşturmak tablo satırlarını dizine ekler. **Select** yöntemi daha sonra bu dizini kullanır ve bu da sorgu sonucunu oluşturma süresini önemli ölçüde azaltır. **DataTable** Için bir **DataView** oluşturma hakkında daha fazla bilgi için bkz. [DataView](dataviews.md).

**Select** yöntemi, bir öğesine göre hangi satır sürümünün görüntüleneceğini veya değiştirileceğini belirler <xref:System.Data.DataViewRowState> . Aşağıdaki tabloda olası **DataViewRowState** numaralandırma değerleri açıklanmaktadır.

|DataViewRowState değeri|Description|
|----------------------------|-----------------|
|**CurrentRows**|Değiştirilmemiş, eklenen ve değiştirilen satırları içeren geçerli satırlar.|
|**Silindi**|Silinen bir satır.|
|**ModifiedCurrent**|Özgün verilerin değiştirilmiş bir sürümü olan geçerli bir sürüm. (Bkz. **Modifiedorijinal.**)|
|**Modifiedorijinal**|Değiştirilen tüm satırların orijinal sürümü. Geçerli sürüm, **ModifiedCurrent** kullanılarak kullanılabilir.|
|**Eklenirse**|Yeni bir satır.|
|**Hiçbiri**|Yok.|
|**OriginalRows**|Değiştirilmemiş ve silinen satırlar dahil olmak üzere orijinal satırlar.|
|**Değiştirilmediği**|Değiştirilmemiş bir satır.|

Aşağıdaki örnekte, **veri kümesi** nesnesi filtrelenmiştir, böylece yalnızca **DataViewRowState** **CurrentRows** olarak ayarlanan satırlarla çalışmanız gerekir.

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

**Select** yöntemi, farklı **RowState** değerlerini veya alan değerlerini içeren satırları döndürmek için kullanılabilir. Aşağıdaki örnek, silinmiş tüm satırlara başvuran bir **DataRow** dizisi döndürür ve **CustId** sütununun 5 ' ten büyük olduğu **CustLName** tarafından sıralanan tüm satırlara başvuran başka bir **DataRow** dizisi döndürür. **Silinen** satırdaki bilgileri görüntüleme hakkında daha fazla bilgi için bkz. [Satır durumları ve satır sürümleri](row-states-and-row-versions.md).

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
