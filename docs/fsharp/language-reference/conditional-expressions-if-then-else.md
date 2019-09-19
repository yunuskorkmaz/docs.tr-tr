---
title: 'Koşullu Ifadeler: if... sonra... değilse'
description: Farklı kod dallarını yürütmek için ' F# de koşullu ifadeler yazmayı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: d9763f37cd9170c42e968282b54a3ce925e92591
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083026"
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="a03f3-103">Koşullu Ifadeler:`if...then...else`</span><span class="sxs-lookup"><span data-stu-id="a03f3-103">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="a03f3-104">İfade `if...then...else` , kodun farklı dallarını çalıştırır ve ayrıca verilen Boolean ifadeye bağlı olarak farklı bir değer olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a03f3-104">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>

## <a name="syntax"></a><span data-ttu-id="a03f3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a03f3-105">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="a03f3-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a03f3-106">Remarks</span></span>

<span data-ttu-id="a03f3-107">Önceki sözdiziminde *İfade1* , Boolean ifadesi olarak `true`değerlendirildiğinde çalıştırılır; Aksi takdirde, *İfade2* çalışır.</span><span class="sxs-lookup"><span data-stu-id="a03f3-107">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="a03f3-108">Diğer dillerden farklı olarak, `if...then...else` yapı deyim değil bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="a03f3-108">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="a03f3-109">Yani, yürüten daldaki son ifadenin değeri olan bir değer üretir.</span><span class="sxs-lookup"><span data-stu-id="a03f3-109">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="a03f3-110">Her dalda üretilen değerlerin türleri eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="a03f3-110">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="a03f3-111">Açık `else` dal yoksa, türü ' dir `unit`.</span><span class="sxs-lookup"><span data-stu-id="a03f3-111">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="a03f3-112">Bu nedenle, `then` dalın türü dışında `unit`herhangi bir tür ise, aynı dönüş türüne sahip bir `else` dal olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a03f3-112">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="a03f3-113">İfadeleri birlikte `if...then...else` zincirlerse, yerine `else if`anahtar sözcüğünü `elif` kullanabilirsiniz; bunlar eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="a03f3-113">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="a03f3-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="a03f3-114">Example</span></span>

<span data-ttu-id="a03f3-115">Aşağıdaki örnek, `if...then...else` ifadesinin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a03f3-115">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```console
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="a03f3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a03f3-116">See also</span></span>

- [<span data-ttu-id="a03f3-117">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a03f3-117">F# Language Reference</span></span>](index.md)
