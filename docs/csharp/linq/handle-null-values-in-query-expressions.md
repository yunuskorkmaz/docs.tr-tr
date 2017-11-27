---
title: "Sorgu ifadelerinde boş değerler işleme"
description: "Sorgu ifadelerinde boş değerler nasıl ele alınacağını."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: d16256e31b073a599504ffef6501ed34430a7694
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="handle-null-values-in-query-expressions"></a><span data-ttu-id="3672e-104">Sorgu ifadelerinde boş değerler işleme</span><span class="sxs-lookup"><span data-stu-id="3672e-104">Handle null values in query expressions</span></span>

<span data-ttu-id="3672e-105">Bu örnek kaynak koleksiyonlarda olası null değerler nasıl ele alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3672e-105">This example shows how to handle possible null values in source collections.</span></span> <span data-ttu-id="3672e-106">Bir nesne koleksiyonu gibi bir <xref:System.Collections.Generic.IEnumerable%601> öğelerine içerebilir [null](../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="3672e-106">An object collection such as an <xref:System.Collections.Generic.IEnumerable%601> can contain elements whose value is [null](../language-reference/keywords/null.md).</span></span> <span data-ttu-id="3672e-107">Bir kaynak koleksiyonu null veya null değeri olan bir öğe içeriyor ve sorgunuzu null değerleri işlemiyor bir <xref:System.NullReferenceException> sorgu yürütülürken oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3672e-107">If a source collection is null or contains an element whose value is null, and your query does not handle null values, a <xref:System.NullReferenceException> will be thrown when you execute the query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3672e-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="3672e-108">Example</span></span>

 <span data-ttu-id="3672e-109">Aşağıdaki örnekte gösterildiği gibi bir null başvuru özel durumu önlemek için biçimde geliştirmelisiniz kodu:</span><span class="sxs-lookup"><span data-stu-id="3672e-109">You can code defensively to avoid a null reference exception as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#82](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]  
  
 <span data-ttu-id="3672e-110">Önceki örnekte, `where` kategoriler dizisi null tüm öğeler filtreleyen yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="3672e-110">In the previous example, the `where` clause filters out all null elements in the categories sequence.</span></span> <span data-ttu-id="3672e-111">Bu teknik JOIN yan tümcesinde null denetimi bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="3672e-111">This technique is independent of the null check in the join clause.</span></span> <span data-ttu-id="3672e-112">Bu örnekte null ile koşullu ifade çalışır olduğundan `Products.CategoryID` türü `int?` için kestirme olduğu `Nullable<int>`.</span><span class="sxs-lookup"><span data-stu-id="3672e-112">The conditional expression with null in this example works because `Products.CategoryID` is of type `int?` which is shorthand for `Nullable<int>`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3672e-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="3672e-113">Example</span></span>

 <span data-ttu-id="3672e-114">Karşılaştırma anahtarlarından birini bir boş değer atanabilir değer türü yalnızca JOIN yan tümcesinde, boş değer atanabilir bir tür için diğer sorgu ifadesinde çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3672e-114">In a join clause, if only one of the comparison keys is a nullable value type, you can cast the other to a nullable type in the query expression.</span></span> <span data-ttu-id="3672e-115">Aşağıdaki örnekte, varsayımında `EmployeeID` türü değerleri içeren bir sütun `int?`:</span><span class="sxs-lookup"><span data-stu-id="3672e-115">In the following example, assume that `EmployeeID` is a column that contains values of type `int?`:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#83](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3672e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3672e-116">See also</span></span>  
 <xref:System.Nullable%601>  
 [<span data-ttu-id="3672e-117">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="3672e-117">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="3672e-118">Boş değer atanabilir türler</span><span class="sxs-lookup"><span data-stu-id="3672e-118">Nullable types</span></span>](../programming-guide/nullable-types/index.md)
