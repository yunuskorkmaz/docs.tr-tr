---
title: Eşleşme ifadeleri
description: Bilgi nasıl F# eşleştirme ifadesi ifade desenleri ile karşılaştırma temel alan dallanma denetim sağlar.
ms.date: 04/19/2018
ms.openlocfilehash: 8972cc012d2746cb720eeed1acee403948941425
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611574"
---
# <a name="match-expressions"></a><span data-ttu-id="b9d8b-103">Eşleşme ifadeleri</span><span class="sxs-lookup"><span data-stu-id="b9d8b-103">Match expressions</span></span>

<span data-ttu-id="b9d8b-104">`match` İfade karşılaştırma ifade desenleri temel alan dallanma denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9d8b-104">The `match` expression provides branching control that is based on the comparison of an expression with a set of patterns.</span></span>

## <a name="syntax"></a><span data-ttu-id="b9d8b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b9d8b-105">Syntax</span></span>

```fsharp
// Match expression.
match test-expression with
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...

// Pattern matching function.
function
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...
```

## <a name="remarks"></a><span data-ttu-id="b9d8b-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9d8b-106">Remarks</span></span>

<span data-ttu-id="b9d8b-107">Desen eşleştirme ifadeler, karşılaştırma test ifade desenleri temel karmaşık dallara ayırmaya olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b9d8b-107">The pattern matching expressions allow for complex branching based on the comparison of a test expression with a set of patterns.</span></span> <span data-ttu-id="b9d8b-108">İçinde `match` ifade *test ifade* etkinleştirin ve bir eşleşme bulunduğunda, karşılık gelen her desen ile karşılaştırıldığında *sonuç ifadesi* değerlendirilir ve elde edilen değer eşleştirme ifadesi değerini döndürdü.</span><span class="sxs-lookup"><span data-stu-id="b9d8b-108">In the `match` expression, the *test-expression* is compared with each pattern in turn, and when a match is found, the corresponding *result-expression* is evaluated and the resulting value is returned as the value of the match expression.</span></span>

<span data-ttu-id="b9d8b-109">Önceki sözdiziminde gösterilen işlev desen, hangi desen eşleştirme hemen bağımsız değişken üzerinde gerçekleştirilen bir lambda ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="b9d8b-109">The pattern matching function shown in the previous syntax is a lambda expression in which pattern matching is performed immediately on the argument.</span></span> <span data-ttu-id="b9d8b-110">Önceki sözdiziminde gösterilen işlev desen aşağıdakine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="b9d8b-110">The pattern matching function shown in the previous syntax is equivalent to the following.</span></span>

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

<span data-ttu-id="b9d8b-111">Lambda ifadeleri hakkında daha fazla bilgi için bkz. [Lambda ifadeleri: `fun` Anahtar sözcüğü](functions/lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="b9d8b-111">For more information about lambda expressions, see [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md).</span></span>

<span data-ttu-id="b9d8b-112">Desenler tam kümesini giriş değişkeni, tüm olası eşleşmeler kapsamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b9d8b-112">The whole set of patterns should cover all the possible matches of the input variable.</span></span> <span data-ttu-id="b9d8b-113">Joker karakter deseni sıkça kullandığınız (`_`) olarak daha önce eşleşmeyen tüm giriş değerlerini eşleştirmek için son desen.</span><span class="sxs-lookup"><span data-stu-id="b9d8b-113">Frequently, you use the wildcard pattern (`_`) as the last pattern to match any previously unmatched input values.</span></span>

<span data-ttu-id="b9d8b-114">Aşağıdaki kod, bazı yöntemler gösterir `match` ifade kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b9d8b-114">The following code illustrates some of the ways in which the `match` expression is used.</span></span> <span data-ttu-id="b9d8b-115">Başvuru ve kullanılabilir tüm olası düzeni örnekleri için bkz: [desen eşleştirme](pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="b9d8b-115">For a reference and examples of all the possible patterns that can be used, see [Pattern Matching](pattern-matching.md).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a><span data-ttu-id="b9d8b-116">Cf desenleriyle ilgili</span><span class="sxs-lookup"><span data-stu-id="b9d8b-116">Guards on patterns</span></span>

<span data-ttu-id="b9d8b-117">Kullanabileceğiniz bir `when` yan tümcesi değişkeni bir desenle eşleşen için karşılaması gereken ek bir koşulu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="b9d8b-117">You can use a `when` clause to specify an additional condition that the variable must satisfy to match a pattern.</span></span> <span data-ttu-id="b9d8b-118">Böyle bir yan tümce olarak adlandırılır bir *koruyucu*.</span><span class="sxs-lookup"><span data-stu-id="b9d8b-118">Such a clause is referred to as a *guard*.</span></span> <span data-ttu-id="b9d8b-119">İfade aşağıdaki `when` anahtar sözcüğü bir eşleşme deseni, koruyucusu ile ilişkili yapılmıyorsa değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="b9d8b-119">The expression following the `when` keyword is not evaluated unless a match is made to the pattern associated with that guard.</span></span>

<span data-ttu-id="b9d8b-120">Aşağıdaki örnek, bir değişken desen için sayısal bir aralık belirtmek için bir koruma kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b9d8b-120">The following example illustrates the use of a guard to specify a numeric range for a variable pattern.</span></span> <span data-ttu-id="b9d8b-121">Not Boole işleçleri kullanarak birden çok koşulu birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b9d8b-121">Note that multiple conditions are combined by using Boolean operators.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

<span data-ttu-id="b9d8b-122">Değişmez değerler dışındaki değerler desende kullanılamaz çünkü kullanmanız gerektiğini unutmayın bir `when` değerle giriş kısmı Karşılaştırılacak varsa yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="b9d8b-122">Note that because values other than literals cannot be used in the pattern, you must use a `when` clause if you have to compare some part of the input against a value.</span></span> <span data-ttu-id="b9d8b-123">Bu, aşağıdaki kodda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b9d8b-123">This is shown in the following code:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

<span data-ttu-id="b9d8b-124">Bir birleşim deseni guard tarafından ele alınmıştır, koruma için geçerli olduğunu unutmayın **tüm** yalnızca sonuncu desenlerinin.</span><span class="sxs-lookup"><span data-stu-id="b9d8b-124">Note that when a union pattern is covered by a guard, the guard applies to **all** of the patterns, not just the last one.</span></span> <span data-ttu-id="b9d8b-125">Örneğin, aşağıdaki kod, koruma verilen `when a > 12` hem `A a` ve `B a`:</span><span class="sxs-lookup"><span data-stu-id="b9d8b-125">For example, given the following code, the guard `when a > 12` applies to both `A a` and `B a`:</span></span>

```fsharp
type Union =
    | A of int
    | B of int

let foo() =
    let test = A 42
    match test with
    | A a
    | B a when a > 41 -> a // the guard applies to both patterns
    | _ -> 1

foo() // returns 42
```

## <a name="see-also"></a><span data-ttu-id="b9d8b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9d8b-126">See also</span></span>

- [<span data-ttu-id="b9d8b-127">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b9d8b-127">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="b9d8b-128">Etkin Desenler</span><span class="sxs-lookup"><span data-stu-id="b9d8b-128">Active Patterns</span></span>](active-patterns.md)
- [<span data-ttu-id="b9d8b-129">Desen Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="b9d8b-129">Pattern Matching</span></span>](pattern-matching.md)