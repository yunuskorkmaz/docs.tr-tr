---
title: Satırları Bulma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: ad10557a55b498fe004bff6ce89801e975e7138b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786324"
---
# <a name="finding-rows"></a>Satırları Bulma
<xref:System.Data.DataView.Find%2A> Ve<xref:System.Data.DataView.FindRows%2A> yöntemlerini<xref:System.Data.DataView>kullanarak sıralama anahtarı değerlerine göre satırları arayabilirsiniz. **Find** ve **FindRows** metotlarındaki arama değerlerinin büyük/küçük harf duyarlılığı, temeldeki <xref:System.Data.DataTable>öğesinin **CaseSensitive** özelliğine göre belirlenir. Bir sonuç döndürmek için, arama değerleri, mevcut sıralama anahtarı değerleriyle eşleşmelidir.  
  
 **Find** yöntemi, arama ölçütleriyle eşleşen öğesinin <xref:System.Data.DataRowView> diziniyle bir tamsayı döndürür. Arama ölçütleriyle eşleşen birden fazla satır varsa, yalnızca ilk eşleşen **DataRowView** 'ın dizini döndürülür. Eşleşme bulunmazsa, **bul** -1 döndürür.  
  
 Birden çok satırla eşleşen arama sonuçları döndürmek için **FindRows** yöntemini kullanın. **FindRows** , **Find** yöntemi gibi çalışarak, **DataView**Içindeki tüm eşleşen satırlara başvuran bir **DataRowView** dizisi döndürür. Hiçbir eşleşme bulunmazsa, **DataRowView** dizisi boş olur.  
  
 **Find** veya **FindRows** yöntemlerini kullanmak için, **ApplyDefaultSort** ' i **true** olarak ayarlayarak ya da **Sort** özelliğini kullanarak bir sıralama düzeni belirtmeniz gerekir. Sıralama düzeni belirtilmemişse, bir özel durum oluşturulur.  
  
 **Find** ve **FindRows** yöntemleri, uzunluğu sıralama düzeninde olan sütun sayısıyla eşleşen girdi olarak bir dizi değer alır. Tek bir sütunda sıralama söz konusu olduğunda tek bir değer geçirebilirsiniz. Birden çok sütun içeren sıralama düzenleri için bir nesne dizisi geçirirsiniz. Birden çok sütunda sıralama için, nesne dizisindeki değerlerin **DataView**'ın **Sort** özelliğinde belirtilen sütunların sırasıyla eşleşmesi gerektiğini unutmayın.  
  
 Aşağıdaki kod örneğinde, tek sütunlu sıralama düzeninde bir **DataView** Ile çağrılan **Find** yöntemi gösterilmektedir.  
  
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
  
 **Sıralama** özelliği birden çok sütun belirtiyorsa, her bir sütunun arama değerleriyle birlikte, aşağıdaki kod örneğinde olduğu gibi **sıralama** özelliği tarafından belirtilen sırada bir nesne dizisi geçirmeniz gerekir.  
  
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
