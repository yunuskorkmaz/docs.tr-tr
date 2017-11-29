---
title: "İfade sütunları oluşturma"
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
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 315944262136e5db453ea01eae64fff6cb0d534d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-expression-columns"></a><span data-ttu-id="01c11-102">İfade sütunları oluşturma</span><span class="sxs-lookup"><span data-stu-id="01c11-102">Creating Expression Columns</span></span>
<span data-ttu-id="01c11-103">Bir ifadenin bir sütun için tanımlayabilirsiniz, bir değer içerecek şekilde etkinleştirme diğer sütun değerleri aynı satırda veya birden çok satır tablosundaki sütun değerlerinden hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="01c11-103">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="01c11-104">Değerlendirilecek ifade tanımlamak için <xref:System.Data.DataColumn.Expression%2A> ve hedef sütun kullanımı özelliği <xref:System.Data.DataColumn.ColumnName%2A> diğer sütunlara ifadede başvurmak için özellik.</span><span class="sxs-lookup"><span data-stu-id="01c11-104">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="01c11-105"><xref:System.Data.DataColumn.DataType%2A> İfade için sütun için ifade döndürür değer uygun olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="01c11-105">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="01c11-106">Aşağıdaki tabloda, bir tablodaki ifade sütunları birkaç olası kullanımları listeler.</span><span class="sxs-lookup"><span data-stu-id="01c11-106">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="01c11-107">İfade türü</span><span class="sxs-lookup"><span data-stu-id="01c11-107">Expression type</span></span>|<span data-ttu-id="01c11-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="01c11-108">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="01c11-109">Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="01c11-109">Comparison</span></span>|<span data-ttu-id="01c11-110">"Toplam > 500 ="</span><span class="sxs-lookup"><span data-stu-id="01c11-110">"Total >= 500"</span></span>|  
|<span data-ttu-id="01c11-111">Hesaplama</span><span class="sxs-lookup"><span data-stu-id="01c11-111">Computation</span></span>|<span data-ttu-id="01c11-112">"UnitPrice * miktar"</span><span class="sxs-lookup"><span data-stu-id="01c11-112">"UnitPrice * Quantity"</span></span>|  
|<span data-ttu-id="01c11-113">Toplama</span><span class="sxs-lookup"><span data-stu-id="01c11-113">Aggregation</span></span>|<span data-ttu-id="01c11-114">SUM(price)</span><span class="sxs-lookup"><span data-stu-id="01c11-114">Sum(Price)</span></span>|  
  
 <span data-ttu-id="01c11-115">Ayarlayabileceğiniz **ifade** varolan özelliğini **DataColumn** nesne veya içerebilir özelliği için geçirilen üçüncü bağımsız değişken olarak <xref:System.Data.DataColumn> aşağıdaki örnekte gösterildiği gibi Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="01c11-115">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="01c11-116">İfadeler diğer ifade sütunları başvurusu yapabilir; Ancak, iki ifadeye birbirine, başvuru bir döngüsel başvuru bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="01c11-116">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="01c11-117">İfadeleri yazma hakkında daha fazla kuralları için bkz: <xref:System.Data.DataColumn.Expression%2A> özelliği **DataColumn** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="01c11-117">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01c11-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="01c11-118">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="01c11-119">DataTable şema tanımı</span><span class="sxs-lookup"><span data-stu-id="01c11-119">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="01c11-120">DataTables</span><span class="sxs-lookup"><span data-stu-id="01c11-120">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="01c11-121">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="01c11-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
