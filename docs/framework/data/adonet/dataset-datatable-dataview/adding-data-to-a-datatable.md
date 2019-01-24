---
title: Bir DataTable tablosuna veri ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: adf2378cead054efcef10a73bfd00ef541940949
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494126"
---
# <a name="adding-data-to-a-datatable"></a>Bir DataTable tablosuna veri ekleme
Oluşturduktan sonra bir <xref:System.Data.DataTable> ve sütunları ve kısıtlamaları kullanarak yapısını tanımlamak, tabloya yeni satır veri ekleyin. Yeni bir satır eklemek için yeni bir değişken türü olarak bildirin <xref:System.Data.DataRow>. Yeni bir **DataRow** çağırdığınızda nesnesi döndürülen <xref:System.Data.DataTable.NewRow%2A> yöntemi. **DataTable** oluşturur sonra **DataRow** nesne temel tablosunun yapısı üzerinde tarafından tanımlanan <xref:System.Data.DataColumnCollection>.  
  
 Aşağıdaki örnek yeni bir satır çağırarak denetlediği oluşturma işlemini gösterir **NewRow** yöntemi.  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 Ardından, aşağıdaki örnekte gösterildiği gibi bir dizini veya sütun adı'nı kullanarak yeni eklenen satır işleyebilirsiniz.  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 Yeni satır veri eklendikten sonra **Ekle** satır eklemek için kullanılan yöntemi <xref:System.Data.DataRowCollection>aşağıdaki kodda gösterilen.  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 Ayrıca, çağırabilirsiniz **Ekle** değerleri dizisi geçirerek yeni bir satır eklemek için yöntemi yazılı olarak <xref:System.Object>aşağıdaki örnekte gösterildiği gibi.  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 Bir dizisi olarak yazılan değerlerin geçirerek **nesne**, **Ekle** yöntemi içindeki tabloya yeni bir satır oluşturur ve nesne dizideki değerleri için sütun değerlerini ayarlar. Dizideki değerleri tablodaki göründükleri sıraya göre sütunlara sıralı olarak eşleştirilir unutmayın.  
  
 Aşağıdaki örnek 10 satır, yeni oluşturulan ekler **müşteriler** tablo.  
  
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
- [DataTable Verilerini Düzenleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
