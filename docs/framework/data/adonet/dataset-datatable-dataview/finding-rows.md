---
title: Satırları Bulma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: 72af4b049153ce647cc1ceb2d40c3b17cc7ed988
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206557"
---
# <a name="finding-rows"></a>Satırları Bulma
Satırları sıralama anahtar değerlerine göre kullanarak arayabilirsiniz <xref:System.Data.DataView.Find%2A> ve <xref:System.Data.DataView.FindRows%2A> yöntemlerinin <xref:System.Data.DataView>. Arama büyük/küçük harfe duyarlılık değeri **Bul** ve **FindRows** yöntemleri tarafından belirlenir **CaseSensitive** özelliği temel <xref:System.Data.DataTable>. Arama değerleri bir sonuç döndürmek için mevcut anahtar değerlerini sıralama tamamen eşleşmelidir.  
  
 **Bul** yöntemi dizini bir tamsayı döndürür <xref:System.Data.DataRowView> arama ölçütleriyle eşleşen. Birden fazla satır, yalnızca ilk eşleşen dizinine arama ölçütleri eşleşiyorsa **DataRowView** döndürülür. Herhangi bir eşleşme bulunursa **Bul** -1 döndürür.  
  
 Birden çok satır eşleşen arama sonuçları döndürmek için **FindRows** yöntemi. **FindRows** yalnızca gibi çalışır **Bul** yöntemi, BT'nin döndürür dışında bir **DataRowView** tüm eşleşen satırları başvuran bir dizi **DataView**. Herhangi bir eşleşme bulunursa **DataRowView** dizi, boş olacaktır.  
  
 Kullanılacak **Bul** veya **FindRows** sıralama belirtmelisiniz yöntemleri ayarlayarak ya da sipariş **ApplyDefaultSort** için **true** kullanarak veya **Sıralama** özelliği. Sıralama düzeni belirtilmediği takdirde, bir özel durum oluşturulur.  
  
 **Bul** ve **FindRows** yöntemleri bir dizi değere uzunluğunu sıralama düzeninde sütun sayısı ile eşleşen girdi olarak alır. Tek bir sütun üzerinde bir sıralama söz konusu olduğunda, tek bir değer geçirebilirsiniz. Birden çok sütun içeren sıralama düzenleri için bir nesne dizisi geçirin. Birden çok sütunu sıralama için belirtilen sütunların sırasını nesne dizideki değerlerin eşleşmesi gerektiğini unutmayın **sıralama** özelliği **DataView**.  
  
 Aşağıdaki örnekte gösterildiği kod **Bul** karşı çağrılan yöntemi bir **DataView** ile bir tek sütun sıralama düzeni.  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName", DataViewRowState.CurrentRows)  
  
Dim rowIndex As Integer = custView.Find("The Cracker Box")  
  
If rowIndex = -1 Then  
  Console.WriteLine("No match found.")  
Else  
  Console.WriteLine("{0}, {1}", _  
    custView(rowIndex)("CustomerID").ToString(), _  
    custView(rowIndex)("CompanyName").ToString())  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",   
  "CompanyName", DataViewRowState.CurrentRows);  
  
int rowIndex = custView.Find("The Cracker Box");  
  
if (rowIndex == -1)  
  Console.WriteLine("No match found.");  
else  
  Console.WriteLine("{0}, {1}",  
    custView[rowIndex]["CustomerID"].ToString(),  
    custView[rowIndex]["CompanyName"].ToString());  
```  
  
 Varsa, **sıralama** özelliği, birden çok sütun belirtir, her sütun için arama değerlerine sahip bir nesne dizisi tarafından belirtilen sırada geçmelidir **sıralama** özelliği, aşağıdaki kod örneğinde olduğu gibi.  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName, ContactName", _  
  DataViewRowState.CurrentRows)  
  
Dim foundRows() As DataRowView = _  
  custView.FindRows(New object() {"The Cracker Box", "Liu Wong"})  
  
If foundRows.Length = 0 Then  
  Console.WriteLine("No match found.")  
Else  
  Dim myDRV As DataRowView  
  For Each myDRV In foundRows  
    Console.WriteLine("{0}, {1}", _  
      myDRV("CompanyName").ToString(), myDRV("ContactName").ToString())  
  Next  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",  
  "CompanyName, ContactName",  
  DataViewRowState.CurrentRows);  
  
DataRowView[] foundRows =   
  custView.FindRows(new object[] {"The Cracker Box", "Liu Wong"});  
  
if (foundRows.Length == 0)  
  Console.WriteLine("No match found.");  
else  
  foreach (DataRowView myDRV in foundRows)  
    Console.WriteLine("{0}, {1}", myDRV["CompanyName"].ToString(),   
      myDRV["ContactName"].ToString());  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
