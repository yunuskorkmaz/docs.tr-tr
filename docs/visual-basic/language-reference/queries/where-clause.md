---
title: Where Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: 404dd848058f7e5c9bc8a74b6d89df18c6c55fad
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005006"
---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="2d0ff-102">Where Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d0ff-102">Where Clause (Visual Basic)</span></span>
<span data-ttu-id="2d0ff-103">Bir sorgu için filtreleme koşulunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d0ff-103">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d0ff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d0ff-104">Syntax</span></span>  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="2d0ff-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="2d0ff-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="2d0ff-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2d0ff-106">Required.</span></span> <span data-ttu-id="2d0ff-107">Koleksiyonda geçerli öğenin değerlerinin çıkış koleksiyonuna dahil edilip edilmeyeceğini belirleyen bir ifade.</span><span class="sxs-lookup"><span data-stu-id="2d0ff-107">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="2d0ff-108">İfade `Boolean` değeri veya `Boolean` değerinin eşdeğerini olarak değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="2d0ff-108">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="2d0ff-109">Koşul `True` olarak değerlendirilirse, öğe sorgu sonucuna dahil edilir; Aksi takdirde, öğe sorgu sonucundan çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="2d0ff-109">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d0ff-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d0ff-110">Remarks</span></span>  
 <span data-ttu-id="2d0ff-111">@No__t-0 yan tümcesi yalnızca belirli ölçütlere uyan öğeleri seçerek sorgu verilerini filtrelemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d0ff-111">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="2d0ff-112">Değerleri `Where` yan tümcesinin `True` olarak değerlendirilmesine neden olan öğeler sorgu sonucuna dahil edilir; diğer öğeler hariç tutulur.</span><span class="sxs-lookup"><span data-stu-id="2d0ff-112">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="2d0ff-113">@No__t-0 yan tümcesinde kullanılan ifade, değeri sıfır olduğunda `False` ' i değerlendiren bir tamsayı gibi bir `Boolean` veya `Boolean` eşdeğerini değerlendirmelidir.</span><span class="sxs-lookup"><span data-stu-id="2d0ff-113">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="2d0ff-114">@No__t-0 yan tümcesinde birden çok ifadeyi `And`, `Or`, `AndAlso`, `OrElse`, `Is` ve `IsNot` gibi mantıksal işleçler kullanarak birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d0ff-114">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="2d0ff-115">Varsayılan olarak, sorgu ifadeleri erişilene kadar değerlendirilmez — Örneğin, veri bağladığında veya bir `For` döngüsüyle aracılığıyla tekrarlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2d0ff-115">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="2d0ff-116">Sonuç olarak, `Where` yan tümcesi sorguya erişilene kadar değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="2d0ff-116">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="2d0ff-117">@No__t-0 yan tümcesinde kullanılan sorguya harici değerleriniz varsa, sorgu yürütüldüğü sırada `Where` yan tümcesinde uygun değerin kullanıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="2d0ff-117">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="2d0ff-118">Sorgu yürütme hakkında daha fazla bilgi için, bkz. [Ilk LINQ sorgunuzu yazma](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="2d0ff-118">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="2d0ff-119">Koleksiyondaki geçerli öğeden bir değer üzerinde hesaplama veya işlem gerçekleştirmek için bir `Where` yan tümcesindeki işlevleri çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d0ff-119">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="2d0ff-120">Bir `Where` yan tümcesinde bir işlevi çağırmak sorgunun ne zaman tanımlanmadığında değil, sorgunun doğrudan yürütülmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="2d0ff-120">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="2d0ff-121">Sorgu yürütme hakkında daha fazla bilgi için, bkz. [Ilk LINQ sorgunuzu yazma](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="2d0ff-121">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d0ff-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="2d0ff-122">Example</span></span>  
 <span data-ttu-id="2d0ff-123">Aşağıdaki sorgu ifadesi, `customers` koleksiyonundaki her bir `Customer` nesnesi için bir Aralık değişkeni `cust` olarak bildirmek üzere bir `From` yan tümcesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="2d0ff-123">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="2d0ff-124">@No__t-0 yan tümcesi, belirtilen bölgedeki müşterilere çıktıyı kısıtlamak için Aralık değişkenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2d0ff-124">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="2d0ff-125">@No__t-0 döngüsü sorgu sonucunda her müşteri için şirket adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2d0ff-125">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a><span data-ttu-id="2d0ff-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="2d0ff-126">Example</span></span>  
 <span data-ttu-id="2d0ff-127">Aşağıdaki örnek `Where` yan tümcesinde `And` ve `Or` mantıksal işleçler kullanır.</span><span class="sxs-lookup"><span data-stu-id="2d0ff-127">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="2d0ff-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d0ff-128">See also</span></span>

- [<span data-ttu-id="2d0ff-129">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="2d0ff-129">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="2d0ff-130">Sorgular</span><span class="sxs-lookup"><span data-stu-id="2d0ff-130">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="2d0ff-131">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="2d0ff-131">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="2d0ff-132">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="2d0ff-132">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="2d0ff-133">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d0ff-133">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
