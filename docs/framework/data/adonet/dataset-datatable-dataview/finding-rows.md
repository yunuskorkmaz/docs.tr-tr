---
title: "Satırları bulma"
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
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 96a65761cb6ddf31c0bb4c14077aed37336183f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="finding-rows"></a>Satırları bulma
Satırları sıralama anahtar değerlerine göre kullanarak arayabilirsiniz <xref:System.Data.DataView.Find%2A> ve <xref:System.Data.DataView.FindRows%2A> yöntemlerini <xref:System.Data.DataView>. Arama büyük/küçük harfe duyarlılık değeri **Bul** ve **FindRows** yöntemleri tarafından belirlenir **CaseSensitive** temel özellik <xref:System.Data.DataTable>. Arama değerleri bir sonuç dönebilmek için var olan sıralama anahtarı değerleri tamamen eşleşmesi gerekir.  
  
 **Bul** yöntemi dizini bir tamsayı döndürür <xref:System.Data.DataRowView> arama ölçütleriyle eşleşen. Birden fazla satır, yalnızca ilk eşleşen dizini arama ölçütleri eşleşirse **DataRowView** döndürülür. Herhangi bir eşleşme bulunmazsa, **Bul** -1 döndürür.  
  
 Birden çok satır ile arama sonuçları döndürmek için kullanın **FindRows** yöntemi. **FindRows** works olduğu gibi **Bul** şekilde döndürür dışında yöntemi, bir **DataRowView** tüm eşleşen satırları başvuran dizi **DataView**. Herhangi bir eşleşme bulunmazsa, **DataRowView** dizi boş olacaktır.  
  
 Kullanılacak **Bul** veya **FindRows** sıralama belirtmelisiniz yöntemleri ayarlayarak ya da sipariş **ApplyDefaultSort** için **true** veya kullanarak **Sıralama** özelliği. Sıralama düzeni belirtilirse, özel durum oluşur.  
  
 **Bul** ve **FindRows** yöntemleri uzunluğunu eşleşen sıralama düzeni sütun sayısını giriş olarak bir dizi değere alın. Tek bir sütun üzerinde sıralama söz konusu olduğunda, tek bir değer geçirebilirsiniz. Birden çok sütun içeren sıralama düzenleri için nesnelerinin bir dizisi geçirin. Birden çok sütun sıralama için belirtilen sütunların sırasını nesne dizideki eşleşmesi gerektiğini unutmayın **sıralama** özelliği **DataView**.  
  
 Aşağıdaki örnekte gösterildiği kod **Bul** karşı çağrılan yöntemi bir **DataView** bir tek sütun sıralama ile.  
  
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
  
 Varsa, **sıralama** özelliği, birden çok sütun belirtir, tarafından belirtilen sırada bir nesne dizisinin her sütun için arama değerlerle geçmelidir **sıralama** özelliği, aşağıdaki kod örneğinde olduğu gibi.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
