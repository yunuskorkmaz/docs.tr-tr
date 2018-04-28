---
title: 'Eşleşme ifadeleri (F #)'
description: 'F # eşleşme ifadesi karşılaştırmaya ifade desenleri dayalı dallanma denetim nasıl sağladığını öğrenin.'
author: cartermp
ms.author: phcart
ms.date: 04/19/2018
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: f6930f782384464f0d44b205ea77cbaf43898213
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="match-expressions"></a><span data-ttu-id="d3d59-103">Eşleşme ifadeleri</span><span class="sxs-lookup"><span data-stu-id="d3d59-103">Match expressions</span></span>

<span data-ttu-id="d3d59-104">`match` İfade karşılaştırmaya ifade desenleri dayalı dallanma denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3d59-104">The `match` expression provides branching control that is based on the comparison of an expression with a set of patterns.</span></span>

## <a name="syntax"></a><span data-ttu-id="d3d59-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3d59-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="d3d59-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3d59-106">Remarks</span></span>

<span data-ttu-id="d3d59-107">Desen eşleştirme ifadeleri karşılaştırmaya test ifadesinin desenleri dayalı karmaşık dallanma için izin verir.</span><span class="sxs-lookup"><span data-stu-id="d3d59-107">The pattern matching expressions allow for complex branching based on the comparison of a test expression with a set of patterns.</span></span> <span data-ttu-id="d3d59-108">İçinde `match` ifadesi *test ifade* açın ve bir eşleşme bulunduğunda, karşılık gelen her deseni ile karşılaştırıldığında *sonuç ifadesi* değerlendirilir ve çıkan değeri eşleşme ifadesi değeri olarak döndürdü.</span><span class="sxs-lookup"><span data-stu-id="d3d59-108">In the `match` expression, the *test-expression* is compared with each pattern in turn, and when a match is found, the corresponding *result-expression* is evaluated and the resulting value is returned as the value of the match expression.</span></span>

<span data-ttu-id="d3d59-109">Desen eşleştirme önceki sözdiziminde gösterilen işlevi hangi desen eşleştirme hemen bağımsız gerçekleştirilir lambda ifadesi ' dir.</span><span class="sxs-lookup"><span data-stu-id="d3d59-109">The pattern matching function shown in the previous syntax is a lambda expression in which pattern matching is performed immediately on the argument.</span></span> <span data-ttu-id="d3d59-110">Desen eşleştirme önceki sözdiziminde gösterilen işlevi şuna eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="d3d59-110">The pattern matching function shown in the previous syntax is equivalent to the following.</span></span>

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

<span data-ttu-id="d3d59-111">Lambda ifadeleri hakkında daha fazla bilgi için bkz: [Lambda ifadeleri: `fun` anahtar sözcüğü](functions/lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="d3d59-111">For more information about lambda expressions, see [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md).</span></span>

<span data-ttu-id="d3d59-112">Desenler tam kümesi giriş değişkenin tüm olası eşleşmeler kapsamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3d59-112">The whole set of patterns should cover all the possible matches of the input variable.</span></span> <span data-ttu-id="d3d59-113">Joker karakter deseni sık kullandığınız (`_`) daha önce eşleşmeyen tüm giriş değerlerini eşleştirmek için son desen olarak.</span><span class="sxs-lookup"><span data-stu-id="d3d59-113">Frequently, you use the wildcard pattern (`_`) as the last pattern to match any previously unmatched input values.</span></span>

<span data-ttu-id="d3d59-114">Aşağıdaki kod, yollardan bazılarını gösterir `match` ifade kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d3d59-114">The following code illustrates some of the ways in which the `match` expression is used.</span></span> <span data-ttu-id="d3d59-115">Bir başvuru ve kullanılabilir tüm olası düzeni örnekleri için bkz: [desen eşleştirme](pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="d3d59-115">For a reference and examples of all the possible patterns that can be used, see [Pattern Matching](pattern-matching.md).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a><span data-ttu-id="d3d59-116">Modeli koruyucuları</span><span class="sxs-lookup"><span data-stu-id="d3d59-116">Guards on patterns</span></span>

<span data-ttu-id="d3d59-117">Kullanabileceğiniz bir `when` değişkeni bir desenle eşleşen için karşılaması gereken ek bir koşulu belirtmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d3d59-117">You can use a `when` clause to specify an additional condition that the variable must satisfy to match a pattern.</span></span> <span data-ttu-id="d3d59-118">Bu tür bir yan tümce olarak adlandırılır bir *koruma*.</span><span class="sxs-lookup"><span data-stu-id="d3d59-118">Such a clause is referred to as a *guard*.</span></span> <span data-ttu-id="d3d59-119">İfade aşağıdaki `when` anahtar sözcüğü bu koruyucusu ile ilişkili desenle eşleşen bir kılmadığınız sürece değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="d3d59-119">The expression following the `when` keyword is not evaluated unless a match is made to the pattern associated with that guard.</span></span>

<span data-ttu-id="d3d59-120">Aşağıdaki örnekte değişken deseni için sayısal bir aralık belirtmek için bir koruma kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d3d59-120">The following example illustrates the use of a guard to specify a numeric range for a variable pattern.</span></span> <span data-ttu-id="d3d59-121">Boole işleçleri kullanarak birden çok koşul birleştirilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d3d59-121">Note that multiple conditions are combined by using Boolean operators.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

<span data-ttu-id="d3d59-122">Değişmez değerler dışında değerleri düzende kullanılamadığından kullanmanız gerektiğini unutmayın bir `when` değerle giriş kısmı karşılaştırmak varsa, yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d3d59-122">Note that because values other than literals cannot be used in the pattern, you must use a `when` clause if you have to compare some part of the input against a value.</span></span> <span data-ttu-id="d3d59-123">Bu aşağıdaki kodda gösterilir:</span><span class="sxs-lookup"><span data-stu-id="d3d59-123">This is shown in the following code:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

<span data-ttu-id="d3d59-124">Birleşim deseni koruyucu tarafından kapsanan, koruma için geçerli olduğunu unutmayın **tüm** yalnızca sonuncu desen.</span><span class="sxs-lookup"><span data-stu-id="d3d59-124">Note that when a union pattern is covered by a guard, the guard applies to **all** of the patterns, not just the last one.</span></span> <span data-ttu-id="d3d59-125">Örneğin, aşağıdaki kod, koruma verilen `when a > 12` hem de geçerli `A a` ve `B a`:</span><span class="sxs-lookup"><span data-stu-id="d3d59-125">For example, given the following code, the guard `when a > 12` applies to both `A a` and `B a`:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d3d59-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3d59-126">See also</span></span>

[<span data-ttu-id="d3d59-127">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="d3d59-127">F# Language Reference</span></span>](index.md)  
[<span data-ttu-id="d3d59-128">Etkin Desenler</span><span class="sxs-lookup"><span data-stu-id="d3d59-128">Active Patterns</span></span>](active-patterns.md)  
[<span data-ttu-id="d3d59-129">Desen Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="d3d59-129">Pattern Matching</span></span>](pattern-matching.md)  
