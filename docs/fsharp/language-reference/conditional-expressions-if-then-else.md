---
title: 'Koşullu İfadeler: if... then...else (F#)'
description: "Koşullu deyimler F farklı dalları kod yürütmek için #'de yazma öğrenin."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: bfb985f09be91034894e1d3eba88cebef6bb3fd4
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="cfbf5-103">Koşullu ifadeler: `if...then...else`</span><span class="sxs-lookup"><span data-stu-id="cfbf5-103">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="cfbf5-104">`if...then...else` İfade kodunun farklı dalları çalıştırır ve verilen Boole ifadesi bağlı olarak farklı bir değere de değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="cfbf5-104">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>


## <a name="syntax"></a><span data-ttu-id="cfbf5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cfbf5-105">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="cfbf5-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cfbf5-106">Remarks</span></span>
<span data-ttu-id="cfbf5-107">Önceki sözdiziminde *İfade1* Boole ifadesi olarak değerlendirildiğinde çalıştıran `true`; Aksi halde, *İfade2* çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="cfbf5-107">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="cfbf5-108">Aksine başka dillerde `if...then...else` yapıdır bir ifade, bir ifade.</span><span class="sxs-lookup"><span data-stu-id="cfbf5-108">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="cfbf5-109">Yürütür şube son ifade değeri bir değer üreten anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cfbf5-109">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="cfbf5-110">Her dalda üretilen değerlerin türleri eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="cfbf5-110">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="cfbf5-111">Varsa ACE'si `else` dal, kendi türüdür `unit`.</span><span class="sxs-lookup"><span data-stu-id="cfbf5-111">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="cfbf5-112">Bu nedenle, varsa türünü `then` dalı olan herhangi bir tür dışında `unit`, olmalıdır bir `else` şube aynı dönüş türüne sahip.</span><span class="sxs-lookup"><span data-stu-id="cfbf5-112">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="cfbf5-113">Zincirleme zaman `if...then...else` ifadeleri birlikte, anahtar sözcüğünü kullanabilirsiniz `elif` yerine `else if`; bunlar eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="cfbf5-113">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="cfbf5-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="cfbf5-114">Example</span></span>
<span data-ttu-id="cfbf5-115">Aşağıdaki örnekte nasıl kullanılacağını anlatan `if...then...else` ifade.</span><span class="sxs-lookup"><span data-stu-id="cfbf5-115">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="cfbf5-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cfbf5-116">See Also</span></span>
[<span data-ttu-id="cfbf5-117">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="cfbf5-117">F# Language Reference</span></span>](index.md)

