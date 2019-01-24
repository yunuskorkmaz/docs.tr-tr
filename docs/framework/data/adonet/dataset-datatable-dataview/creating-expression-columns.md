---
title: İfade sütunları oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: db38d42e9c7dc1657e06030599ae2b8ba66ef6b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549882"
---
# <a name="creating-expression-columns"></a><span data-ttu-id="55b02-102">İfade sütunları oluşturma</span><span class="sxs-lookup"><span data-stu-id="55b02-102">Creating Expression Columns</span></span>
<span data-ttu-id="55b02-103">Bir ifadenin bir sütun için tanımlayabileceğiniz, bir değer içermesi için etkinleştirme ile aynı satırdaki diğer sütun değerleri veya birden çok satır'tablosundaki sütun değerlerini hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="55b02-103">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="55b02-104">Değerlendirilecek ifade tanımlamak için <xref:System.Data.DataColumn.Expression%2A> ve hedef sütun kullanımı özelliği <xref:System.Data.DataColumn.ColumnName%2A> ifade diğer sütunlara başvurmak için özellik.</span><span class="sxs-lookup"><span data-stu-id="55b02-104">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="55b02-105"><xref:System.Data.DataColumn.DataType%2A> Sütun ifade için ifadenin döndürdüğü değeri uygun olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="55b02-105">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="55b02-106">Aşağıdaki tabloda, bir tablodaki ifade sütunları birkaç olası kullanımları listeler.</span><span class="sxs-lookup"><span data-stu-id="55b02-106">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="55b02-107">İfade türü</span><span class="sxs-lookup"><span data-stu-id="55b02-107">Expression type</span></span>|<span data-ttu-id="55b02-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="55b02-108">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="55b02-109">Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="55b02-109">Comparison</span></span>|<span data-ttu-id="55b02-110">"Toplam > 500 ="</span><span class="sxs-lookup"><span data-stu-id="55b02-110">"Total >= 500"</span></span>|  
|<span data-ttu-id="55b02-111">Hesaplama</span><span class="sxs-lookup"><span data-stu-id="55b02-111">Computation</span></span>|<span data-ttu-id="55b02-112">"UnitPrice \* Quantity"</span><span class="sxs-lookup"><span data-stu-id="55b02-112">"UnitPrice \* Quantity"</span></span>|  
|<span data-ttu-id="55b02-113">Toplama</span><span class="sxs-lookup"><span data-stu-id="55b02-113">Aggregation</span></span>|<span data-ttu-id="55b02-114">SUM(price)</span><span class="sxs-lookup"><span data-stu-id="55b02-114">Sum(Price)</span></span>|  
  
 <span data-ttu-id="55b02-115">Ayarlayabileceğiniz **ifade** var olan bir özellik **DataColumn** nesne veya içerebilir özelliği için geçirilen üçüncü bağımsız değişken olarak <xref:System.Data.DataColumn> oluşturucusu, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="55b02-115">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="55b02-116">İfadeler, diğer ifade sütunları başvurabilir; Ancak, iki ifadeleri birbiriyle başvuru döngüsel bir başvuru, bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="55b02-116">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="55b02-117">İfadeler yazma hakkında daha fazla kuralları için bkz: <xref:System.Data.DataColumn.Expression%2A> özelliği **DataColumn** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="55b02-117">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55b02-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55b02-118">See also</span></span>
- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="55b02-119">DataTable Şema Tanımı</span><span class="sxs-lookup"><span data-stu-id="55b02-119">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [<span data-ttu-id="55b02-120">DataTables</span><span class="sxs-lookup"><span data-stu-id="55b02-120">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [<span data-ttu-id="55b02-121">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="55b02-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
