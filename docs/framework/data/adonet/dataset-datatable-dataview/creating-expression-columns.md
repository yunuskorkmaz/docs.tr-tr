---
title: İfade Sütunları Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: ad14e4d3d6a1107f994d9536485257f9dc1851f5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166852"
---
# <a name="creating-expression-columns"></a><span data-ttu-id="51124-102">İfade Sütunları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="51124-102">Creating Expression Columns</span></span>

<span data-ttu-id="51124-103">Bir sütun için bir ifade tanımlayabilir, bu değerin aynı satırdaki diğer sütun değerlerinden veya tablodaki birden çok satırın sütun değerlerinden hesaplanan bir değer içermesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51124-103">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="51124-104">Değerlendirilecek ifadeyi tanımlamak için, <xref:System.Data.DataColumn.Expression%2A> hedef sütunun özelliğini kullanın ve <xref:System.Data.DataColumn.ColumnName%2A> ifadedeki diğer sütunlara başvurmak için özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="51124-104">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="51124-105"><xref:System.Data.DataColumn.DataType%2A>İfade sütunu için, ifadenin döndürdüğü değer için uygun olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="51124-105">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="51124-106">Aşağıdaki tabloda, bir tablodaki ifade sütunlarının birkaç olası kullanımı listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="51124-106">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="51124-107">İfade türü</span><span class="sxs-lookup"><span data-stu-id="51124-107">Expression type</span></span>|<span data-ttu-id="51124-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="51124-108">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="51124-109">Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="51124-109">Comparison</span></span>|<span data-ttu-id="51124-110">"Toplam >= 500"</span><span class="sxs-lookup"><span data-stu-id="51124-110">"Total >= 500"</span></span>|  
|<span data-ttu-id="51124-111">Hesaplamada</span><span class="sxs-lookup"><span data-stu-id="51124-111">Computation</span></span>|<span data-ttu-id="51124-112">"BirimFiyat \* miktar"</span><span class="sxs-lookup"><span data-stu-id="51124-112">"UnitPrice \* Quantity"</span></span>|  
|<span data-ttu-id="51124-113">Toplama</span><span class="sxs-lookup"><span data-stu-id="51124-113">Aggregation</span></span>|<span data-ttu-id="51124-114">Toplam (fiyat)</span><span class="sxs-lookup"><span data-stu-id="51124-114">Sum(Price)</span></span>|  
  
 <span data-ttu-id="51124-115">Var olan bir **DataColumn** nesnesi üzerinde **Expression** özelliğini ayarlayabilir veya özelliği <xref:System.Data.DataColumn> Aşağıdaki örnekte gösterildiği gibi oluşturucuya geçirilen üçüncü bağımsız değişken olarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51124-115">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="51124-116">İfadeler, diğer ifade sütunlarına başvurabilir; Ancak, iki ifadenin birbirini bildirdiği döngüsel bir başvuru, bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="51124-116">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="51124-117">İfadeleri yazma hakkında kurallar için bkz <xref:System.Data.DataColumn.Expression%2A> . **DataColumn** sınıfının özelliği.</span><span class="sxs-lookup"><span data-stu-id="51124-117">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51124-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51124-118">See also</span></span>

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="51124-119">DataTable Şema Tanımı</span><span class="sxs-lookup"><span data-stu-id="51124-119">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="51124-120">DataTables</span><span class="sxs-lookup"><span data-stu-id="51124-120">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="51124-121">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="51124-121">ADO.NET Overview</span></span>](../ado-net-overview.md)
