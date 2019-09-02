---
title: DataTable’a Veri Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: 91c635e2bc2ed617e8c45171d9ec7d7359b9ca88
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205485"
---
# <a name="adding-data-to-a-datatable"></a>DataTable’a Veri Ekleme
' I oluşturup <xref:System.Data.DataTable> , sütunları ve kısıtlamalarını kullanarak yapısını tanımladıktan sonra, tabloya yeni veri satırları ekleyebilirsiniz. Yeni bir satır eklemek için yeni bir değişkeni tür <xref:System.Data.DataRow>olarak bildirin. <xref:System.Data.DataTable.NewRow%2A> Yöntemini çağırdığınızda yeni bir **DataRow** nesnesi döndürülür. **DataTable** daha sonra, <xref:System.Data.DataColumnCollection>tarafından tanımlandığı gibi, tablosunun yapısına bağlı olarak **DataRow** nesnesini oluşturur.  
  
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
  
 Veriler yeni satıra eklendikten sonra, aşağıdaki kodda gösterildiği <xref:System.Data.DataRowCollection>gibi **ekleme** yöntemi satırı öğesine eklemek için kullanılır.  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 Ayrıca <xref:System.Object>, aşağıdaki örnekte gösterildiği gibi, bir değerler dizisine geçirerek yeni bir satır eklemek için **Add** yöntemini çağırabilirsiniz.  
  
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
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
