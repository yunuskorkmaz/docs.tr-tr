---
description: 'Hakkında daha fazla bilgi edinin: WHERE tümcesi (Visual Basic)'
title: Where Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: 11f9a7e586a1fdea826df4fb34a7227747c8cebd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730323"
---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="f843f-103">Where Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f843f-103">Where Clause (Visual Basic)</span></span>

<span data-ttu-id="f843f-104">Bir sorgu için filtreleme koşulunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f843f-104">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f843f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f843f-105">Syntax</span></span>  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="f843f-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="f843f-106">Parts</span></span>  

 `condition`  
 <span data-ttu-id="f843f-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f843f-107">Required.</span></span> <span data-ttu-id="f843f-108">Koleksiyonda geçerli öğenin değerlerinin çıkış koleksiyonuna dahil edilip edilmeyeceğini belirleyen bir ifade.</span><span class="sxs-lookup"><span data-stu-id="f843f-108">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="f843f-109">İfade bir değere veya bir değerin eşdeğeri olarak değerlendirilmelidir `Boolean` `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="f843f-109">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="f843f-110">Koşul olarak değerlendirilirse `True` , öğe sorgu sonucuna dahil edilir; Aksi takdirde, öğe sorgu sonucundan çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="f843f-110">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f843f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f843f-111">Remarks</span></span>  

 <span data-ttu-id="f843f-112">`Where`Yan tümcesi yalnızca belirli ölçütlere uyan öğeleri seçerek sorgu verilerini filtrelemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f843f-112">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="f843f-113">Değerleri, `Where` yan tümcesinin değerlendirilmesine neden olan öğeler `True` sorgu sonucuna dahil edilir; diğer öğeler hariç tutulur.</span><span class="sxs-lookup"><span data-stu-id="f843f-113">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="f843f-114">Bir `Where` yan tümcesinde kullanılan ifade `Boolean` `Boolean` , değeri sıfır olduğunda olarak değerlendirilen bir tamsayı gibi bir veya eşdeğerini vermelidir `False` .</span><span class="sxs-lookup"><span data-stu-id="f843f-114">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="f843f-115">,,,, `Where` Ve gibi mantıksal işleçleri kullanarak bir yan tümcede birden çok ifadeyi birleştirebilirsiniz `And` `Or` `AndAlso` `OrElse` `Is` `IsNot` .</span><span class="sxs-lookup"><span data-stu-id="f843f-115">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="f843f-116">Varsayılan olarak, sorgu ifadeleri erişilene kadar değerlendirilmez — Örneğin, veri bağladığında veya bir döngüyle aracılığıyla yinelendiğinde `For` .</span><span class="sxs-lookup"><span data-stu-id="f843f-116">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="f843f-117">Sonuç olarak, bir `Where` sorgu erişilene kadar yan tümce değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="f843f-117">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="f843f-118">Yan tümcesinde kullanılan sorguya dış değerler varsa `Where` , `Where` sorgu yürütüldüğü sırada yan tümcesinde uygun değerin kullanıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="f843f-118">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="f843f-119">Sorgu yürütme hakkında daha fazla bilgi için, bkz. [Ilk LINQ sorgunuzu yazma](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="f843f-119">For more information about query execution, see [Writing Your First LINQ Query](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="f843f-120">Bir `Where` yan tümce içindeki işlevleri, koleksiyondaki geçerli öğeden bir değer üzerinde bir hesaplama veya işlem gerçekleştirmek için çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f843f-120">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="f843f-121">Bir yan tümcedeki bir işlevi çağırmak, `Where` sorgunun ne zaman tanımlanmadığında hemen yürütülmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f843f-121">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="f843f-122">Sorgu yürütme hakkında daha fazla bilgi için, bkz. [Ilk LINQ sorgunuzu yazma](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="f843f-122">For more information about query execution, see [Writing Your First LINQ Query](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f843f-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="f843f-123">Example</span></span>  

 <span data-ttu-id="f843f-124">Aşağıdaki sorgu ifadesi, `From` koleksiyondaki her bir nesne için bir Aralık değişkeni bildirmek üzere bir yan tümce kullanır `cust` `Customer` `customers` .</span><span class="sxs-lookup"><span data-stu-id="f843f-124">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="f843f-125">`Where`Yan tümcesi, belirtilen bölgedeki müşterilere çıktıyı kısıtlamak için Aralık değişkenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f843f-125">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="f843f-126">`For Each`Döngü, sorgu sonucunda her müşteri için şirket adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f843f-126">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a><span data-ttu-id="f843f-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="f843f-127">Example</span></span>  

 <span data-ttu-id="f843f-128">Aşağıdaki örnek `And` `Or` , yan tümcesindeki ve mantıksal işleçleri kullanır `Where` .</span><span class="sxs-lookup"><span data-stu-id="f843f-128">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="f843f-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f843f-129">See also</span></span>

- [<span data-ttu-id="f843f-130">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="f843f-130">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="f843f-131">Sorgular</span><span class="sxs-lookup"><span data-stu-id="f843f-131">Queries</span></span>](index.md)
- [<span data-ttu-id="f843f-132">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="f843f-132">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="f843f-133">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="f843f-133">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="f843f-134">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="f843f-134">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
