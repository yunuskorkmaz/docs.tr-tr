---
title: DataTable’a Veri Ekleme
description: Bir DataTable oluşturduktan sonra ve sütununu ve kısıtlamalarını kullanarak yapısını tanımladıktan sonra, ADO.NET içindeki bir tabloya yeni veri satırları eklemek için bu örnek koda bakın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: 94ebc97d5f90b5bb92186ba6f33015633bd01127
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286940"
---
# <a name="adding-data-to-a-datatable"></a>DataTable’a Veri Ekleme
' <xref:System.Data.DataTable> I oluşturup, sütunları ve kısıtlamalarını kullanarak yapısını tanımladıktan sonra, tabloya yeni veri satırları ekleyebilirsiniz. Yeni bir satır eklemek için yeni bir değişkeni tür olarak bildirin <xref:System.Data.DataRow> . Yöntemini çağırdığınızda yeni bir **DataRow** nesnesi döndürülür <xref:System.Data.DataTable.NewRow%2A> . **DataTable** daha sonra, tarafından tanımlandığı gibi, tablosunun yapısına bağlı olarak **DataRow** nesnesini oluşturur <xref:System.Data.DataColumnCollection> .  
  
 Aşağıdaki örnek, **NewRow** yöntemini çağırarak yeni bir satır oluşturmayı gösterir.  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 Daha sonra, aşağıdaki örnekte gösterildiği gibi, yeni eklenen satırı bir dizin veya sütun adı kullanarak düzenleyebilirsiniz.  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 Veriler yeni satıra eklendikten sonra, **Add** <xref:System.Data.DataRowCollection> aşağıdaki kodda gösterildiği gibi ekleme yöntemi satırı öğesine eklemek için kullanılır.  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 Ayrıca **Add** <xref:System.Object> , aşağıdaki örnekte gösterildiği gibi, bir değerler dizisine geçirerek yeni bir satır eklemek için Add yöntemini çağırabilirsiniz.  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 **Add** yöntemine **nesne**olarak yazılan bir değer dizisinin geçirilmesi, tablonun içinde yeni bir satır oluşturur ve sütun değerlerini nesne dizisindeki değerler olarak ayarlar. Dizideki değerlerin, tabloda göründükleri sıraya göre sütunları sırayla eşleştirdiğini unutmayın.  
  
 Aşağıdaki örnek, yeni oluşturulan **müşteriler** tablosuna 10 satır ekler.  
  
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
