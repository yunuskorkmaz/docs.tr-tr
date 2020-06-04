---
title: Where Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: b80bb047551dee8ab23cfac06b961996992d69b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359547"
---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="c8d54-102">Where Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8d54-102">Where Clause (Visual Basic)</span></span>
<span data-ttu-id="c8d54-103">Bir sorgu için filtreleme koşulunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c8d54-103">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8d54-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8d54-104">Syntax</span></span>  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="c8d54-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c8d54-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="c8d54-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c8d54-106">Required.</span></span> <span data-ttu-id="c8d54-107">Koleksiyonda geçerli öğenin değerlerinin çıkış koleksiyonuna dahil edilip edilmeyeceğini belirleyen bir ifade.</span><span class="sxs-lookup"><span data-stu-id="c8d54-107">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="c8d54-108">İfade bir değere veya bir değerin eşdeğeri olarak değerlendirilmelidir `Boolean` `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="c8d54-108">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="c8d54-109">Koşul olarak değerlendirilirse `True` , öğe sorgu sonucuna dahil edilir; Aksi takdirde, öğe sorgu sonucundan çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="c8d54-109">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8d54-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8d54-110">Remarks</span></span>  
 <span data-ttu-id="c8d54-111">`Where`Yan tümcesi yalnızca belirli ölçütlere uyan öğeleri seçerek sorgu verilerini filtrelemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8d54-111">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="c8d54-112">Değerleri, `Where` yan tümcesinin değerlendirilmesine neden olan öğeler `True` sorgu sonucuna dahil edilir; diğer öğeler hariç tutulur.</span><span class="sxs-lookup"><span data-stu-id="c8d54-112">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="c8d54-113">Bir `Where` yan tümcesinde kullanılan ifade `Boolean` `Boolean` , değeri sıfır olduğunda olarak değerlendirilen bir tamsayı gibi bir veya eşdeğerini vermelidir `False` .</span><span class="sxs-lookup"><span data-stu-id="c8d54-113">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="c8d54-114">,,,, `Where` Ve gibi mantıksal işleçleri kullanarak bir yan tümcede birden çok ifadeyi birleştirebilirsiniz `And` `Or` `AndAlso` `OrElse` `Is` `IsNot` .</span><span class="sxs-lookup"><span data-stu-id="c8d54-114">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="c8d54-115">Varsayılan olarak, sorgu ifadeleri erişilene kadar değerlendirilmez — Örneğin, veri bağladığında veya bir döngüyle aracılığıyla yinelendiğinde `For` .</span><span class="sxs-lookup"><span data-stu-id="c8d54-115">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="c8d54-116">Sonuç olarak, bir `Where` sorgu erişilene kadar yan tümce değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="c8d54-116">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="c8d54-117">Yan tümcesinde kullanılan sorguya dış değerler varsa `Where` , `Where` sorgu yürütüldüğü sırada yan tümcesinde uygun değerin kullanıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="c8d54-117">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="c8d54-118">Sorgu yürütme hakkında daha fazla bilgi için, bkz. [Ilk LINQ sorgunuzu yazma](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="c8d54-118">For more information about query execution, see [Writing Your First LINQ Query](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="c8d54-119">Bir `Where` yan tümce içindeki işlevleri, koleksiyondaki geçerli öğeden bir değer üzerinde bir hesaplama veya işlem gerçekleştirmek için çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8d54-119">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="c8d54-120">Bir yan tümcedeki bir işlevi çağırmak, `Where` sorgunun ne zaman tanımlanmadığında hemen yürütülmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="c8d54-120">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="c8d54-121">Sorgu yürütme hakkında daha fazla bilgi için, bkz. [Ilk LINQ sorgunuzu yazma](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="c8d54-121">For more information about query execution, see [Writing Your First LINQ Query](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8d54-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="c8d54-122">Example</span></span>  
 <span data-ttu-id="c8d54-123">Aşağıdaki sorgu ifadesi, `From` koleksiyondaki her bir nesne için bir Aralık değişkeni bildirmek üzere bir yan tümce kullanır `cust` `Customer` `customers` .</span><span class="sxs-lookup"><span data-stu-id="c8d54-123">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="c8d54-124">`Where`Yan tümcesi, belirtilen bölgedeki müşterilere çıktıyı kısıtlamak için Aralık değişkenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c8d54-124">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="c8d54-125">`For Each`Döngü, sorgu sonucunda her müşteri için şirket adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c8d54-125">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a><span data-ttu-id="c8d54-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="c8d54-126">Example</span></span>  
 <span data-ttu-id="c8d54-127">Aşağıdaki örnek `And` `Or` , yan tümcesindeki ve mantıksal işleçleri kullanır `Where` .</span><span class="sxs-lookup"><span data-stu-id="c8d54-127">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="c8d54-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8d54-128">See also</span></span>

- [<span data-ttu-id="c8d54-129">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="c8d54-129">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="c8d54-130">Sorgular</span><span class="sxs-lookup"><span data-stu-id="c8d54-130">Queries</span></span>](index.md)
- [<span data-ttu-id="c8d54-131">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="c8d54-131">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="c8d54-132">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="c8d54-132">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="c8d54-133">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="c8d54-133">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
