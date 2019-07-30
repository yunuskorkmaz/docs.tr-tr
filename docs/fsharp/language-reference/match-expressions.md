---
title: Match ifadeleri
description: F# Match ifadesinin bir desen kümesine sahip bir ifadenin karşılaştırmasına dayalı olarak dallanma denetimi nasıl sağladığını öğrenin.
ms.date: 04/19/2018
ms.openlocfilehash: 222cb0604300039d86ed0c80293651631d212eb6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627615"
---
# <a name="match-expressions"></a><span data-ttu-id="cdbcd-103">Match ifadeleri</span><span class="sxs-lookup"><span data-stu-id="cdbcd-103">Match expressions</span></span>

<span data-ttu-id="cdbcd-104">`match` İfade, bir ifadenin bir dizi deseniyle karşılaştırmasını temel alan dallanma denetimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-104">The `match` expression provides branching control that is based on the comparison of an expression with a set of patterns.</span></span>

## <a name="syntax"></a><span data-ttu-id="cdbcd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cdbcd-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="cdbcd-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cdbcd-106">Remarks</span></span>

<span data-ttu-id="cdbcd-107">Desen eşleştirme ifadeleri, bir dizi desenle bir test ifadesinin karşılaştırmasına bağlı olarak karmaşık dallandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-107">The pattern matching expressions allow for complex branching based on the comparison of a test expression with a set of patterns.</span></span> <span data-ttu-id="cdbcd-108">İfadede, *Test ifadesi* her bir düzen ile karşılaştırılır ve bir eşleşme bulunduğunda, karşılık gelen *Sonuç ifadesi* değerlendirilir ve elde edilen değer, eşleşme ifadesinin değeri olarak döndürülür. `match`</span><span class="sxs-lookup"><span data-stu-id="cdbcd-108">In the `match` expression, the *test-expression* is compared with each pattern in turn, and when a match is found, the corresponding *result-expression* is evaluated and the resulting value is returned as the value of the match expression.</span></span>

<span data-ttu-id="cdbcd-109">Önceki sözdiziminde gösterilen model eşleştirme işlevi, bir lambda ifadesidir ve bu ifade, bağımsız değişkende hemen bu düzende yapılır.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-109">The pattern matching function shown in the previous syntax is a lambda expression in which pattern matching is performed immediately on the argument.</span></span> <span data-ttu-id="cdbcd-110">Önceki sözdiziminde gösterilen kalıp eşleştirme işlevi aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-110">The pattern matching function shown in the previous syntax is equivalent to the following.</span></span>

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

<span data-ttu-id="cdbcd-111">Lambda ifadeleri hakkında daha fazla bilgi için bkz [. Lambda ifadeleri: `fun` Anahtar sözcüğü](./functions/lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="cdbcd-111">For more information about lambda expressions, see [Lambda Expressions: The `fun` Keyword](./functions/lambda-expressions-the-fun-keyword.md).</span></span>

<span data-ttu-id="cdbcd-112">Tüm desen kümesi, giriş değişkeninin tüm olası eşleşmelerini kapsamalıdır.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-112">The whole set of patterns should cover all the possible matches of the input variable.</span></span> <span data-ttu-id="cdbcd-113">Genellikle, daha önce eşleşmeyen giriş değerleriyle eşleştirmek`_`için en son model olarak () joker karakter stilini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-113">Frequently, you use the wildcard pattern (`_`) as the last pattern to match any previously unmatched input values.</span></span>

<span data-ttu-id="cdbcd-114">Aşağıdaki kod, `match` ifadenin kullanıldığı bazı yolları gösterir.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-114">The following code illustrates some of the ways in which the `match` expression is used.</span></span> <span data-ttu-id="cdbcd-115">Bir başvuru ve kullanılabilecek tüm olası desenlerin örnekleri için bkz. [desen eşleştirme](pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="cdbcd-115">For a reference and examples of all the possible patterns that can be used, see [Pattern Matching](pattern-matching.md).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a><span data-ttu-id="cdbcd-116">Desenlerdeki koruyucular</span><span class="sxs-lookup"><span data-stu-id="cdbcd-116">Guards on patterns</span></span>

<span data-ttu-id="cdbcd-117">Değişkenin bir düzeniyle eşleştirmek `when` için karşılaması gereken ek bir koşul belirtmek için bir yan tümce kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-117">You can use a `when` clause to specify an additional condition that the variable must satisfy to match a pattern.</span></span> <span data-ttu-id="cdbcd-118">Böyle bir yan tümce *koruma*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-118">Such a clause is referred to as a *guard*.</span></span> <span data-ttu-id="cdbcd-119">`when` Anahtar sözcüğünü izleyen ifade, bu Guard ile ilişkili bir eşleme yapılmadığı takdirde değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-119">The expression following the `when` keyword is not evaluated unless a match is made to the pattern associated with that guard.</span></span>

<span data-ttu-id="cdbcd-120">Aşağıdaki örnek, bir değişken deseninin sayısal aralığını belirtmek için bir koruyucu kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-120">The following example illustrates the use of a guard to specify a numeric range for a variable pattern.</span></span> <span data-ttu-id="cdbcd-121">Birden çok koşulun Boole işleçleri kullanılarak birleştirildiğine unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-121">Note that multiple conditions are combined by using Boolean operators.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

<span data-ttu-id="cdbcd-122">Değişmez değerler dışındaki değerlerin, düzende kullanılmadığından, girişin bazı bölümlerini bir değere göre karşılaştırmanız gerekiyorsa, `when` bir yan tümce kullanmanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-122">Note that because values other than literals cannot be used in the pattern, you must use a `when` clause if you have to compare some part of the input against a value.</span></span> <span data-ttu-id="cdbcd-123">Bu, aşağıdaki kodda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cdbcd-123">This is shown in the following code:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

<span data-ttu-id="cdbcd-124">Bir birleşim deseninin bir koruyucu kapsamında ele alındığına, koruanın yalnızca son bir değil, **Tüm** desenlere uygulandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-124">Note that when a union pattern is covered by a guard, the guard applies to **all** of the patterns, not just the last one.</span></span> <span data-ttu-id="cdbcd-125">Örneğin, aşağıdaki kod verildiğinde, koruma `when a > 12` `B a`hem hem de `A a` için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="cdbcd-125">For example, given the following code, the guard `when a > 12` applies to both `A a` and `B a`:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cdbcd-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-126">See also</span></span>

- [<span data-ttu-id="cdbcd-127">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="cdbcd-127">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="cdbcd-128">Etkin Desenler</span><span class="sxs-lookup"><span data-stu-id="cdbcd-128">Active Patterns</span></span>](active-patterns.md)
- [<span data-ttu-id="cdbcd-129">Desen Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="cdbcd-129">Pattern Matching</span></span>](pattern-matching.md)
