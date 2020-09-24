---
title: DataTable’a Veri Ekleme
description: Bir DataTable oluşturduktan sonra ve sütununu ve kısıtlamalarını kullanarak yapısını tanımladıktan sonra, ADO.NET içindeki bir tabloya yeni veri satırları eklemek için bu örnek koda bakın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: aac2d90cc57a4af823c42f8c7eb2adcd43c63caf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164824"
---
# <a name="adding-data-to-a-datatable"></a><span data-ttu-id="7c24f-103">DataTable’a Veri Ekleme</span><span class="sxs-lookup"><span data-stu-id="7c24f-103">Adding Data to a DataTable</span></span>

<span data-ttu-id="7c24f-104">' <xref:System.Data.DataTable> I oluşturup, sütunları ve kısıtlamalarını kullanarak yapısını tanımladıktan sonra, tabloya yeni veri satırları ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c24f-104">After you create a <xref:System.Data.DataTable> and define its structure using columns and constraints, you can add new rows of data to the table.</span></span> <span data-ttu-id="7c24f-105">Yeni bir satır eklemek için yeni bir değişkeni tür olarak bildirin <xref:System.Data.DataRow> .</span><span class="sxs-lookup"><span data-stu-id="7c24f-105">To add a new row, declare a new variable as type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="7c24f-106">Yöntemini çağırdığınızda yeni bir **DataRow** nesnesi döndürülür <xref:System.Data.DataTable.NewRow%2A> .</span><span class="sxs-lookup"><span data-stu-id="7c24f-106">A new **DataRow** object is returned when you call the <xref:System.Data.DataTable.NewRow%2A> method.</span></span> <span data-ttu-id="7c24f-107">**DataTable** daha sonra, tarafından tanımlandığı gibi, tablosunun yapısına bağlı olarak **DataRow** nesnesini oluşturur <xref:System.Data.DataColumnCollection> .</span><span class="sxs-lookup"><span data-stu-id="7c24f-107">The **DataTable** then creates the **DataRow** object based on the structure of the table, as defined by the <xref:System.Data.DataColumnCollection>.</span></span>  
  
 <span data-ttu-id="7c24f-108">Aşağıdaki örnek, **NewRow** yöntemini çağırarak yeni bir satır oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7c24f-108">The following example demonstrates how to create a new row by calling the **NewRow** method.</span></span>  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 <span data-ttu-id="7c24f-109">Daha sonra, aşağıdaki örnekte gösterildiği gibi, yeni eklenen satırı bir dizin veya sütun adı kullanarak düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c24f-109">You then can manipulate the newly added row using an index or the column name, as shown in the following example.</span></span>  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 <span data-ttu-id="7c24f-110">Veriler yeni satıra eklendikten sonra, **Add** <xref:System.Data.DataRowCollection> aşağıdaki kodda gösterildiği gibi ekleme yöntemi satırı öğesine eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7c24f-110">After data is inserted into the new row, the **Add** method is used to add the row to the <xref:System.Data.DataRowCollection>, shown in the following code.</span></span>  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 <span data-ttu-id="7c24f-111">Ayrıca **Add** <xref:System.Object> , aşağıdaki örnekte gösterildiği gibi, bir değerler dizisine geçirerek yeni bir satır eklemek için Add yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c24f-111">You can also call the **Add** method to add a new row by passing in an array of values, typed as <xref:System.Object>, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 <span data-ttu-id="7c24f-112">**Add** yöntemine **nesne**olarak yazılan bir değer dizisinin geçirilmesi, tablonun içinde yeni bir satır oluşturur ve sütun değerlerini nesne dizisindeki değerler olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7c24f-112">Passing an array of values, typed as **Object**, to the **Add** method creates a new row inside the table and sets its column values to the values in the object array.</span></span> <span data-ttu-id="7c24f-113">Dizideki değerlerin, tabloda göründükleri sıraya göre sütunları sırayla eşleştirdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7c24f-113">Note that values in the array are matched sequentially to the columns, based on the order in which they appear in the table.</span></span>  
  
 <span data-ttu-id="7c24f-114">Aşağıdaki örnek, yeni oluşturulan **müşteriler** tablosuna 10 satır ekler.</span><span class="sxs-lookup"><span data-stu-id="7c24f-114">The following example adds 10 rows to the newly created **Customers** table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7c24f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c24f-115">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="7c24f-116">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="7c24f-116">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="7c24f-117">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7c24f-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
