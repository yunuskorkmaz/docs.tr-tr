---
title: "Eşleşme İfadeleri (F#)"
description: "F # eşleşme ifadesi karşılaştırmaya ifade desenleri dayalı dallanma denetim nasıl sağladığını öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8854b713-255a-408d-942a-e80ab52fd2a4
ms.openlocfilehash: c8b9be744cfa7bc76f0d663b12abd66f8757fc56
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="match-expressions"></a><span data-ttu-id="4ffeb-104">Eşleşme İfadeleri</span><span class="sxs-lookup"><span data-stu-id="4ffeb-104">Match Expressions</span></span>

<span data-ttu-id="4ffeb-105">`match` İfade karşılaştırmaya ifade desenleri dayalı dallanma denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ffeb-105">The `match` expression provides branching control that is based on the comparison of an expression with a set of patterns.</span></span>

## <a name="syntax"></a><span data-ttu-id="4ffeb-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ffeb-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="4ffeb-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ffeb-107">Remarks</span></span>

<span data-ttu-id="4ffeb-108">Desen eşleştirme ifadeleri karşılaştırmaya test ifadesinin desenleri dayalı karmaşık dallanma için izin verir.</span><span class="sxs-lookup"><span data-stu-id="4ffeb-108">The pattern matching expressions allow for complex branching based on the comparison of a test expression with a set of patterns.</span></span> <span data-ttu-id="4ffeb-109">İçinde `match` ifadesi *test ifade* açın ve bir eşleşme bulunduğunda, karşılık gelen her deseni ile karşılaştırıldığında *sonuç ifadesi* değerlendirilir ve çıkan değeri eşleşme ifadesi değeri olarak döndürdü.</span><span class="sxs-lookup"><span data-stu-id="4ffeb-109">In the `match` expression, the *test-expression* is compared with each pattern in turn, and when a match is found, the corresponding *result-expression* is evaluated and the resulting value is returned as the value of the match expression.</span></span>

<span data-ttu-id="4ffeb-110">Desen eşleştirme önceki sözdiziminde gösterilen işlevi hangi desen eşleştirme hemen bağımsız gerçekleştirilir lambda ifadesi ' dir.</span><span class="sxs-lookup"><span data-stu-id="4ffeb-110">The pattern matching function shown in the previous syntax is a lambda expression in which pattern matching is performed immediately on the argument.</span></span> <span data-ttu-id="4ffeb-111">Desen eşleştirme önceki sözdiziminde gösterilen işlevi şuna eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="4ffeb-111">The pattern matching function shown in the previous syntax is equivalent to the following.</span></span>

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```    

<span data-ttu-id="4ffeb-112">Lambda ifadeleri hakkında daha fazla bilgi için bkz: [Lambda ifadeleri: `fun` anahtar sözcüğü](functions/lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="4ffeb-112">For more information about lambda expressions, see [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md).</span></span>

<span data-ttu-id="4ffeb-113">Desenler tam kümesi giriş değişkenin tüm olası eşleşmeler kapsamalıdır.</span><span class="sxs-lookup"><span data-stu-id="4ffeb-113">The whole set of patterns should cover all the possible matches of the input variable.</span></span> <span data-ttu-id="4ffeb-114">Joker karakter deseni sık kullandığınız (`_`) daha önce eşleşmeyen tüm giriş değerlerini eşleştirmek için son desen olarak.</span><span class="sxs-lookup"><span data-stu-id="4ffeb-114">Frequently, you use the wildcard pattern (`_`) as the last pattern to match any previously unmatched input values.</span></span>

<span data-ttu-id="4ffeb-115">Aşağıdaki kod, yollardan bazılarını gösterir `match` ifade kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4ffeb-115">The following code illustrates some of the ways in which the `match` expression is used.</span></span> <span data-ttu-id="4ffeb-116">Bir başvuru ve kullanılabilir tüm olası düzeni örnekleri için bkz: [desen eşleştirme](pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="4ffeb-116">For a reference and examples of all the possible patterns that can be used, see [Pattern Matching](pattern-matching.md).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a><span data-ttu-id="4ffeb-117">Modeli koruyucuları</span><span class="sxs-lookup"><span data-stu-id="4ffeb-117">Guards on Patterns</span></span>

<span data-ttu-id="4ffeb-118">Kullanabileceğiniz bir `when` değişkeni bir desenle eşleşen için karşılaması gereken ek bir koşulu belirtmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4ffeb-118">You can use a `when` clause to specify an additional condition that the variable must satisfy to match a pattern.</span></span> <span data-ttu-id="4ffeb-119">Bu tür bir yan tümce olarak adlandırılır bir *koruma*.</span><span class="sxs-lookup"><span data-stu-id="4ffeb-119">Such a clause is referred to as a *guard*.</span></span> <span data-ttu-id="4ffeb-120">İfade aşağıdaki `when` anahtar sözcüğü bu koruyucusu ile ilişkili desenle eşleşen bir kılmadığınız sürece değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="4ffeb-120">The expression following the `when` keyword is not evaluated unless a match is made to the pattern associated with that guard.</span></span>

<span data-ttu-id="4ffeb-121">Aşağıdaki örnekte değişken deseni için sayısal bir aralık belirtmek için bir koruma kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="4ffeb-121">The following example illustrates the use of a guard to specify a numeric range for a variable pattern.</span></span> <span data-ttu-id="4ffeb-122">Boole işleçleri kullanarak birden çok koşul birleştirilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4ffeb-122">Note that multiple conditions are combined by using Boolean operators.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

<span data-ttu-id="4ffeb-123">Değişmez değerler dışında değerleri düzende kullanılamadığından kullanmanız gerektiğini unutmayın bir `when` değerle giriş kısmı karşılaştırmak varsa, yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4ffeb-123">Note that because values other than literals cannot be used in the pattern, you must use a `when` clause if you have to compare some part of the input against a value.</span></span> <span data-ttu-id="4ffeb-124">Bu aşağıdaki kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="4ffeb-124">This is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

## <a name="see-also"></a><span data-ttu-id="4ffeb-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4ffeb-125">See Also</span></span>

[<span data-ttu-id="4ffeb-126">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="4ffeb-126">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="4ffeb-127">Etkin desenler</span><span class="sxs-lookup"><span data-stu-id="4ffeb-127">Active Patterns</span></span>](active-patterns.md)

[<span data-ttu-id="4ffeb-128">Desen eşleştirme</span><span class="sxs-lookup"><span data-stu-id="4ffeb-128">Pattern Matching</span></span>](pattern-matching.md)
