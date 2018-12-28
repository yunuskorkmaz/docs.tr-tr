---
title: 'Koşullu ifadeler: if... then... else'
description: Koşullu ifadeler yazılacağını öğrenin F# farklı dallara kod yürütmek için.
ms.date: 05/16/2016
ms.openlocfilehash: eade8c20c1b62a2e9a54700550d832798308f368
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614065"
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="5aee4-103">Koşullu ifadeler: `if...then...else`</span><span class="sxs-lookup"><span data-stu-id="5aee4-103">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="5aee4-104">`if...then...else` İfade kod farklı dallara çalıştırır ve verilen bir Boole ifadesi bağlı olarak farklı bir değer için değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="5aee4-104">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>

## <a name="syntax"></a><span data-ttu-id="5aee4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5aee4-105">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="5aee4-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5aee4-106">Remarks</span></span>

<span data-ttu-id="5aee4-107">Önceki sözdiziminde, *İfade1* Boole ifadesi olarak değerlendirildiğinde çalıştıran `true`; Aksi takdirde *expression2* çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="5aee4-107">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="5aee4-108">Aksine başka dillerde `if...then...else` yapıdır deyim olmayan bir ifade.</span><span class="sxs-lookup"><span data-stu-id="5aee4-108">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="5aee4-109">Son yürütülen dal ifade değeri bir değer üretir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5aee4-109">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="5aee4-110">Her dalda üretilen değer türleri eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="5aee4-110">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="5aee4-111">Varsa ACE'si `else` dalı, kendi türüdür `unit`.</span><span class="sxs-lookup"><span data-stu-id="5aee4-111">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="5aee4-112">Bu nedenle, türünü `then` dalı olan her türlü dışında `unit`, olmalıdır bir `else` dal aynı dönüş türüne sahip.</span><span class="sxs-lookup"><span data-stu-id="5aee4-112">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="5aee4-113">Zincirleme olduğunda `if...then...else` ifadeler birlikte anahtar sözcüğü kullanabileceğiniz `elif` yerine `else if`; bunlar eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="5aee4-113">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="5aee4-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="5aee4-114">Example</span></span>

<span data-ttu-id="5aee4-115">Aşağıdaki örnekte nasıl kullanılacağı gösterilmektedir `if...then...else` ifade.</span><span class="sxs-lookup"><span data-stu-id="5aee4-115">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="5aee4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5aee4-116">See also</span></span>

- [<span data-ttu-id="5aee4-117">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="5aee4-117">F# Language Reference</span></span>](index.md)