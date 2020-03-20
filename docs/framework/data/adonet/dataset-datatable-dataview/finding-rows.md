---
title: Satırları Bulma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: cfd4587f0dde7687ecf88bf6b31c44b90a2287ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151149"
---
# <a name="finding-rows"></a>Satırları Bulma
Satırları sıralama anahtar değerlerine göre, <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> <xref:System.Data.DataView>'nin yöntemlerini ve yöntemlerini kullanarak arayabilirsiniz. **Find** ve **FindRows** yöntemlerindeki arama değerlerinin durum duyarlılığı, altta yatan <xref:System.Data.DataTable> **CaseSensitive** özelliği tarafından belirlenir. Arama değerleri, bir sonucu döndürmek için varolan anahtar değerleri tam olarak eşleştirmelidir.  
  
 **Bul** yöntemi, arama ölçütleriyle <xref:System.Data.DataRowView> eşleşen dizinin isini içeren bir arayıcı döndürür. Birden fazla satır arama ölçütleriyle eşleşirse, yalnızca ilk eşleşen **DataRowView** dizini döndürülür. Eşleşme bulunmazsa, **Find** -1 döndürür bulun.  
  
 Birden çok satırla eşleşen arama sonuçlarını döndürmek için **FindRows** yöntemini kullanın. **FindRows,** **DataView'daki**tüm eşleşen satırlara başvuran bir **DataRowView** dizisini döndürmesi dışında, **Bul** yöntemi gibi çalışır. Eşler bulunmazsa, **DataRowView** dizisi boş olur.  
  
 **Find** or **FindRows** yöntemlerini kullanmak **için, ApplyDefaultSort'u** **doğru** olarak ayarlayarak veya **Sıralama** özelliğini kullanarak bir sıralama sırası belirtmeniz gerekir. Sıralama sırası belirtilmemişse, bir özel durum atılır.  
  
 **Find** and **FindRows** yöntemleri, uzunlukları sıralama sırasındaki sütun sayısıyla eşleşen giriş olarak bir dizi değer alır. Tek bir sütunda bir sıralama durumunda, tek bir değer geçirebilirsiniz. Birden çok sütun içeren sıralama siparişleri için, bir dizi nesne geçersiniz. Birden çok sütundaki sıralama için nesne dizisindeki değerlerin **DataView'ın** **Sıralama** özelliğinde belirtilen sütunların sırasına uyması gerektiğini unutmayın.  
  
 Aşağıdaki kod örneği, tek bir sütun sıralama sırasına sahip bir **DataView'a** karşı çağrılan **Bul** yöntemini gösterir.  
  
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
  
 **Sıralama** özelliğiniz birden çok sütun belirtse, aşağıdaki kod örneğinde olduğu gibi **Sıralama** özelliği tarafından belirtilen sırada her sütun için arama değerlerini içeren bir nesne dizisini geçmeniz gerekir.  
  
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
- [DataViews](dataviews.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
