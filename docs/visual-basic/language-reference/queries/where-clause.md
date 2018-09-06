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
ms.openlocfilehash: de7b4bf3e7dc1145b7e95197c7bd05c66acdabd6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43859442"
---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="ba331-102">Where Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba331-102">Where Clause (Visual Basic)</span></span>
<span data-ttu-id="ba331-103">Bir sorgu için filtreleme koşulunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ba331-103">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba331-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba331-104">Syntax</span></span>  
  
```  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="ba331-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="ba331-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="ba331-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ba331-106">Required.</span></span> <span data-ttu-id="ba331-107">Bir ifade koleksiyondaki geçerli öğe değerlerini çıkış koleksiyonda bulunup bulunmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="ba331-107">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="ba331-108">İfade değerlendirilmelidir bir `Boolean` değeri veya eşdeğer bir `Boolean` değeri.</span><span class="sxs-lookup"><span data-stu-id="ba331-108">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="ba331-109">İçin değerlendirilen koşul yoksa `True`öğe sorgu sonucuna dahil, aksi takdirde, sorgu sonucu öğe çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="ba331-109">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba331-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba331-110">Remarks</span></span>  
 <span data-ttu-id="ba331-111">`Where` Yan tümcesi yalnızca belirli ölçütlere uyan öğeleri seçerek sorgu verilerini filtrelemek etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="ba331-111">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="ba331-112">Değerleri neden öğeleri `Where` yan tümcesi için değerlendirilecek `True` sorgu sonucunda; dahil edilen diğer öğeleri hariç tutulur.</span><span class="sxs-lookup"><span data-stu-id="ba331-112">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="ba331-113">Kullanılan ifade bir `Where` yan tümcesi gerekir değerlendirmek için bir `Boolean` veya eşdeğer bir `Boolean`, değerlendiren bir tamsayı gibi `False` değeri sıfır olduğunda.</span><span class="sxs-lookup"><span data-stu-id="ba331-113">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="ba331-114">Birden çok ifadeleri birleştirebilirsiniz bir `Where` mantıksal işleçler gibi kullanarak yan tümcesi `And`, `Or`, `AndAlso`, `OrElse`, `Is`, ve `IsNot`.</span><span class="sxs-lookup"><span data-stu-id="ba331-114">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="ba331-115">Varsayılan olarak, bunlar erişene kadar sorgu ifadeleri değerlendirilmeyen — Örneğin, olduklarında veri bağlama veya içinde aracılığıyla tekrarlayan bir `For` döngü.</span><span class="sxs-lookup"><span data-stu-id="ba331-115">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="ba331-116">Sonuç olarak, `Where` yan tümce sorgu erişinceye kadar değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="ba331-116">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="ba331-117">Değerleri için kullanılan sorgu dış olup olmadığını `Where` yan tümcesi, uygun değeri olarak kullanıldığından emin olun `Where` sorgu yürütüldüğünde zaman yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="ba331-117">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="ba331-118">Sorgu yürütme hakkında daha fazla bilgi için bkz: [bilgisayarınızı ilk LINQ sorgusu yazma](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="ba331-118">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="ba331-119">İşlevler içinde çağırabilirsiniz bir `Where` yan geçerli öğe koleksiyonundaki bir hesaplama veya bir değer işlemi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="ba331-119">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="ba331-120">Bir işlev arayan bir `Where` yan tümcesi, erişildiğinde ne zaman yerine tanımlanan hemen yürütülecek sorgu neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ba331-120">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="ba331-121">Sorgu yürütme hakkında daha fazla bilgi için bkz: [bilgisayarınızı ilk LINQ sorgusu yazma](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="ba331-121">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba331-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="ba331-122">Example</span></span>  
 <span data-ttu-id="ba331-123">Aşağıdaki sorgu ifadesi kullanan bir `From` yan tümcesinin aralık değişkenini bildirmek için `cust` her `Customer` nesnesine `customers` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ba331-123">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="ba331-124">`Where` Yan tümcesi, çıkış belirtilen bölgeden müşterilere kısıtlamak için aralık değişkeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="ba331-124">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="ba331-125">`For Each` Döngü, her müşteri için şirket adı sorgu sonucu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ba331-125">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="ba331-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="ba331-126">Example</span></span>  
 <span data-ttu-id="ba331-127">Aşağıdaki örnekte `And` ve `Or` mantıksal işleçler `Where` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="ba331-127">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#31](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ba331-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ba331-128">See Also</span></span>  
 [<span data-ttu-id="ba331-129">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="ba331-129">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="ba331-130">Sorgular</span><span class="sxs-lookup"><span data-stu-id="ba331-130">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="ba331-131">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="ba331-131">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="ba331-132">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="ba331-132">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="ba331-133">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="ba331-133">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
