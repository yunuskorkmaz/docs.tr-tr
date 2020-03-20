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
# <a name="adding-data-to-a-datatable"></a><span data-ttu-id="76cc4-102">DataTable’a Veri Ekleme</span><span class="sxs-lookup"><span data-stu-id="76cc4-102">Adding Data to a DataTable</span></span>
<span data-ttu-id="76cc4-103">Sütunlar ve <xref:System.Data.DataTable> kısıtlamalar kullanarak bir yapı oluşturduktan ve yapısını tanımladıktan sonra, tabloya yeni veri satırları ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76cc4-103">After you create a <xref:System.Data.DataTable> and define its structure using columns and constraints, you can add new rows of data to the table.</span></span> <span data-ttu-id="76cc4-104">Yeni bir satır eklemek için, yeni <xref:System.Data.DataRow>bir değişkeni tür olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="76cc4-104">To add a new row, declare a new variable as type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="76cc4-105">Yöntemi aradığınızda yeni bir **DataRow** nesnesi <xref:System.Data.DataTable.NewRow%2A> döndürülür.</span><span class="sxs-lookup"><span data-stu-id="76cc4-105">A new **DataRow** object is returned when you call the <xref:System.Data.DataTable.NewRow%2A> method.</span></span> <span data-ttu-id="76cc4-106">**DataTable** daha sonra tablonun yapısına göre **Veri Satırı** nesnesi <xref:System.Data.DataColumnCollection>oluşturur, tarafından tanımlanan .</span><span class="sxs-lookup"><span data-stu-id="76cc4-106">The **DataTable** then creates the **DataRow** object based on the structure of the table, as defined by the <xref:System.Data.DataColumnCollection>.</span></span>  
  
 <span data-ttu-id="76cc4-107">Aşağıdaki örnek, **NewRow** yöntemini arayarak yeni bir satırOluşturmanın nasıl olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="76cc4-107">The following example demonstrates how to create a new row by calling the **NewRow** method.</span></span>  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 <span data-ttu-id="76cc4-108">Ardından, aşağıdaki örnekte gösterildiği gibi, bir dizin veya sütun adını kullanarak yeni eklenen satırı işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76cc4-108">You then can manipulate the newly added row using an index or the column name, as shown in the following example.</span></span>  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 <span data-ttu-id="76cc4-109">Veriler yeni satıra eklendikten sonra, **satırı** aşağıdaki kodda gösterilen <xref:System.Data.DataRowCollection>sıraya eklemek için Ekle yöntemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="76cc4-109">After data is inserted into the new row, the **Add** method is used to add the row to the <xref:System.Data.DataRowCollection>, shown in the following code.</span></span>  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 <span data-ttu-id="76cc4-110">Aşağıdaki örnekte **Add** gösterildiği gibi, <xref:System.Object>bir dizi değer geçirerek yeni bir satır eklemek için Ekle yöntemini de arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76cc4-110">You can also call the **Add** method to add a new row by passing in an array of values, typed as <xref:System.Object>, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 <span data-ttu-id="76cc4-111">**Nesne**olarak yazılan bir dizi değerin **Ekle** yöntemine geçirilmesi, tablonun içinde yeni bir satır oluşturur ve sütun değerlerini nesne dizisindeki değerlere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="76cc4-111">Passing an array of values, typed as **Object**, to the **Add** method creates a new row inside the table and sets its column values to the values in the object array.</span></span> <span data-ttu-id="76cc4-112">Dizideki değerlerin, tabloda göründükleri sıraya göre sütunlar ile sırayla eşleştiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="76cc4-112">Note that values in the array are matched sequentially to the columns, based on the order in which they appear in the table.</span></span>  
  
 <span data-ttu-id="76cc4-113">Aşağıdaki örnek, yeni oluşturulan **Müşteriler** tablosuna 10 satır ekler.</span><span class="sxs-lookup"><span data-stu-id="76cc4-113">The following example adds 10 rows to the newly created **Customers** table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="76cc4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76cc4-114">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="76cc4-115">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="76cc4-115">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="76cc4-116">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="76cc4-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
