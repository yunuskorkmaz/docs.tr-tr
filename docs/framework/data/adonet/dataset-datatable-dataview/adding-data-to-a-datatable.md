---
title: DataTable’a Veri Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: 02d7f94259cc56513be404c5539ca7015d5f3533
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151539"
---
# <a name="adding-data-to-a-datatable"></a>DataTable’a Veri Ekleme
Sütunlar ve <xref:System.Data.DataTable> kısıtlamalar kullanarak bir yapı oluşturduktan ve yapısını tanımladıktan sonra, tabloya yeni veri satırları ekleyebilirsiniz. Yeni bir satır eklemek için, yeni <xref:System.Data.DataRow>bir değişkeni tür olarak bildirin. Yöntemi aradığınızda yeni bir **DataRow** nesnesi <xref:System.Data.DataTable.NewRow%2A> döndürülür. **DataTable** daha sonra tablonun yapısına göre **Veri Satırı** nesnesi <xref:System.Data.DataColumnCollection>oluşturur, tarafından tanımlanan .  
  
 Aşağıdaki örnek, **NewRow** yöntemini arayarak yeni bir satırOluşturmanın nasıl olduğunu gösterir.  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 Ardından, aşağıdaki örnekte gösterildiği gibi, bir dizin veya sütun adını kullanarak yeni eklenen satırı işleyebilirsiniz.  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 Veriler yeni satıra eklendikten sonra, **satırı** aşağıdaki kodda gösterilen <xref:System.Data.DataRowCollection>sıraya eklemek için Ekle yöntemi kullanılır.  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 Aşağıdaki örnekte **Add** gösterildiği gibi, <xref:System.Object>bir dizi değer geçirerek yeni bir satır eklemek için Ekle yöntemini de arayabilirsiniz.  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 **Nesne**olarak yazılan bir dizi değerin **Ekle** yöntemine geçirilmesi, tablonun içinde yeni bir satır oluşturur ve sütun değerlerini nesne dizisindeki değerlere ayarlar. Dizideki değerlerin, tabloda göründükleri sıraya göre sütunlar ile sırayla eşleştiğini unutmayın.  
  
 Aşağıdaki örnek, yeni oluşturulan **Müşteriler** tablosuna 10 satır ekler.  
  
```vb  
Dim workRow As DataRow  
Dim i As Integer  
  
For i = 0 To 9  
  workRow = workTable.NewRow()  
  workRow(0) = i  
  workRow(1) = "CustName" & I.ToString()  
  workTable.Rows.Add(workRow)  
Next  
```  
  
```csharp  
DataRow workRow;  
  
for (int i = 0; i <= 9; i++)
{  
  workRow = workTable.NewRow();  
  workRow[0] = i;  
  workRow[1] = "CustName" + i.ToString();  
  workTable.Rows.Add(workRow);  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [DataTable Verilerini Düzenleme](manipulating-data-in-a-datatable.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
