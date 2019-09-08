---
title: İfade Sütunları Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: 1c4e0b368a8eb154207382ae70b9767f5a5fe64d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785440"
---
# <a name="creating-expression-columns"></a><span data-ttu-id="8a9b3-102">İfade Sütunları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8a9b3-102">Creating Expression Columns</span></span>
<span data-ttu-id="8a9b3-103">Bir sütun için bir ifade tanımlayabilir, bu değerin aynı satırdaki diğer sütun değerlerinden veya tablodaki birden çok satırın sütun değerlerinden hesaplanan bir değer içermesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a9b3-103">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="8a9b3-104">Değerlendirilecek ifadeyi tanımlamak için, hedef sütunun <xref:System.Data.DataColumn.Expression%2A> özelliğini kullanın ve ifadedeki diğer sütunlara başvurmak için <xref:System.Data.DataColumn.ColumnName%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8a9b3-104">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="8a9b3-105">İfade <xref:System.Data.DataColumn.DataType%2A> sütunu için, ifadenin döndürdüğü değer için uygun olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8a9b3-105">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="8a9b3-106">Aşağıdaki tabloda, bir tablodaki ifade sütunlarının birkaç olası kullanımı listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="8a9b3-106">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="8a9b3-107">İfade türü</span><span class="sxs-lookup"><span data-stu-id="8a9b3-107">Expression type</span></span>|<span data-ttu-id="8a9b3-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a9b3-108">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="8a9b3-109">Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="8a9b3-109">Comparison</span></span>|<span data-ttu-id="8a9b3-110">"Toplam > = 500"</span><span class="sxs-lookup"><span data-stu-id="8a9b3-110">"Total >= 500"</span></span>|  
|<span data-ttu-id="8a9b3-111">Hesaplamada</span><span class="sxs-lookup"><span data-stu-id="8a9b3-111">Computation</span></span>|<span data-ttu-id="8a9b3-112">"BirimFiyat \* miktar"</span><span class="sxs-lookup"><span data-stu-id="8a9b3-112">"UnitPrice \* Quantity"</span></span>|  
|<span data-ttu-id="8a9b3-113">Toplama</span><span class="sxs-lookup"><span data-stu-id="8a9b3-113">Aggregation</span></span>|<span data-ttu-id="8a9b3-114">Toplam (fiyat)</span><span class="sxs-lookup"><span data-stu-id="8a9b3-114">Sum(Price)</span></span>|  
  
 <span data-ttu-id="8a9b3-115">Var olan bir **DataColumn** nesnesi üzerinde <xref:System.Data.DataColumn> **Expression** özelliğini ayarlayabilir veya özelliği aşağıdaki örnekte gösterildiği gibi oluşturucuya geçirilen üçüncü bağımsız değişken olarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a9b3-115">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="8a9b3-116">İfadeler, diğer ifade sütunlarına başvurabilir; Ancak, iki ifadenin birbirini bildirdiği döngüsel bir başvuru, bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8a9b3-116">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="8a9b3-117">İfadeleri yazma hakkında kurallar için bkz <xref:System.Data.DataColumn.Expression%2A> . **DataColumn** sınıfının özelliği.</span><span class="sxs-lookup"><span data-stu-id="8a9b3-117">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a9b3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a9b3-118">See also</span></span>

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="8a9b3-119">DataTable Şema Tanımı</span><span class="sxs-lookup"><span data-stu-id="8a9b3-119">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="8a9b3-120">DataTables</span><span class="sxs-lookup"><span data-stu-id="8a9b3-120">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="8a9b3-121">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8a9b3-121">ADO.NET Overview</span></span>](../ado-net-overview.md)
