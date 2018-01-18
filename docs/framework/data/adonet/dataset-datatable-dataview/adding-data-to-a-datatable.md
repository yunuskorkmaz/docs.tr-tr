---
title: DataTable tablosuna veri ekleme
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
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 29ba4a62b2c896e4ce5fa01929307ee82753495f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="adding-data-to-a-datatable"></a>DataTable tablosuna veri ekleme
Oluşturduktan sonra bir <xref:System.Data.DataTable> ve sütunları ve kısıtlamaları kullanarak yapısını tanımlamak, yeni veri satırları tabloya ekleyebilirsiniz. Yeni bir satır eklemek için yeni bir değişken türü olarak bildirme <xref:System.Data.DataRow>. Yeni bir **DataRow** çağırdığınızda nesnesi döndürülen <xref:System.Data.DataTable.NewRow%2A> yöntemi. **DataTable** sonra oluşturur **DataRow** nesne tarafından tanımlanan tablosu yapısına bağlı <xref:System.Data.DataColumnCollection>.  
  
 Aşağıdaki örnekte nasıl yeni bir satır çağırarak oluşturulduğunu gösteren **NewRow** yöntemi.  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 Ardından, aşağıdaki örnekte gösterildiği gibi bir dizin veya sütun adını kullanarak yeni eklenen satır yönetebilirsiniz.  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 Veri yeni satır eklendikten sonra **Ekle** yöntemi için satır eklemek için kullanılan <xref:System.Data.DataRowCollection>, aşağıdaki kodda gösterildiği.  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 Ayrıca, çağırabilirsiniz **Ekle** değerleri, bir dizi geçirerek yeni bir satır eklemek için yöntemini yazılan olarak <xref:System.Object>, aşağıdaki örnekte gösterildiği gibi.  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 Bir dizi olarak yazılan değerlerin geçirme **nesne**, **Ekle** yöntemi tablosunun içine yeni bir satır oluşturur ve nesne dizisinin değerler sütun değerlerini ayarlar. Dizideki tabloda görünme sırasını göre sütunlara sıralı olarak eşleştirilir unutmayın.  
  
 Aşağıdaki örnek, 10 satır yeni oluşturulan ekler **müşteriler** tablo.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [DataTable Verilerini Düzenleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
