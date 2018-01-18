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
# <a name="adding-data-to-a-datatable"></a><span data-ttu-id="a453c-102">DataTable tablosuna veri ekleme</span><span class="sxs-lookup"><span data-stu-id="a453c-102">Adding Data to a DataTable</span></span>
<span data-ttu-id="a453c-103">Oluşturduktan sonra bir <xref:System.Data.DataTable> ve sütunları ve kısıtlamaları kullanarak yapısını tanımlamak, yeni veri satırları tabloya ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a453c-103">After you create a <xref:System.Data.DataTable> and define its structure using columns and constraints, you can add new rows of data to the table.</span></span> <span data-ttu-id="a453c-104">Yeni bir satır eklemek için yeni bir değişken türü olarak bildirme <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="a453c-104">To add a new row, declare a new variable as type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="a453c-105">Yeni bir **DataRow** çağırdığınızda nesnesi döndürülen <xref:System.Data.DataTable.NewRow%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a453c-105">A new **DataRow** object is returned when you call the <xref:System.Data.DataTable.NewRow%2A> method.</span></span> <span data-ttu-id="a453c-106">**DataTable** sonra oluşturur **DataRow** nesne tarafından tanımlanan tablosu yapısına bağlı <xref:System.Data.DataColumnCollection>.</span><span class="sxs-lookup"><span data-stu-id="a453c-106">The **DataTable** then creates the **DataRow** object based on the structure of the table, as defined by the <xref:System.Data.DataColumnCollection>.</span></span>  
  
 <span data-ttu-id="a453c-107">Aşağıdaki örnekte nasıl yeni bir satır çağırarak oluşturulduğunu gösteren **NewRow** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a453c-107">The following example demonstrates how to create a new row by calling the **NewRow** method.</span></span>  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 <span data-ttu-id="a453c-108">Ardından, aşağıdaki örnekte gösterildiği gibi bir dizin veya sütun adını kullanarak yeni eklenen satır yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a453c-108">You then can manipulate the newly added row using an index or the column name, as shown in the following example.</span></span>  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 <span data-ttu-id="a453c-109">Veri yeni satır eklendikten sonra **Ekle** yöntemi için satır eklemek için kullanılan <xref:System.Data.DataRowCollection>, aşağıdaki kodda gösterildiği.</span><span class="sxs-lookup"><span data-stu-id="a453c-109">After data is inserted into the new row, the **Add** method is used to add the row to the <xref:System.Data.DataRowCollection>, shown in the following code.</span></span>  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 <span data-ttu-id="a453c-110">Ayrıca, çağırabilirsiniz **Ekle** değerleri, bir dizi geçirerek yeni bir satır eklemek için yöntemini yazılan olarak <xref:System.Object>, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="a453c-110">You can also call the **Add** method to add a new row by passing in an array of values, typed as <xref:System.Object>, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 <span data-ttu-id="a453c-111">Bir dizi olarak yazılan değerlerin geçirme **nesne**, **Ekle** yöntemi tablosunun içine yeni bir satır oluşturur ve nesne dizisinin değerler sütun değerlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a453c-111">Passing an array of values, typed as **Object**, to the **Add** method creates a new row inside the table and sets its column values to the values in the object array.</span></span> <span data-ttu-id="a453c-112">Dizideki tabloda görünme sırasını göre sütunlara sıralı olarak eşleştirilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a453c-112">Note that values in the array are matched sequentially to the columns, based on the order in which they appear in the table.</span></span>  
  
 <span data-ttu-id="a453c-113">Aşağıdaki örnek, 10 satır yeni oluşturulan ekler **müşteriler** tablo.</span><span class="sxs-lookup"><span data-stu-id="a453c-113">The following example adds 10 rows to the newly created **Customers** table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a453c-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a453c-114">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="a453c-115">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="a453c-115">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="a453c-116">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="a453c-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
