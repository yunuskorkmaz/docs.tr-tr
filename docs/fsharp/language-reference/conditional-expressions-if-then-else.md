---
title: "Koşullu İfadeler: if... then...else (F#)"
description: "Koşullu deyimler F farklı dalları kod yürütmek için #'de yazma öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 16e1871c-4d4d-4691-9ab2-bd2c6f65589a
ms.openlocfilehash: 3531a112eb53657d5e9102d5e5f3be988360b76e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="b9c20-104">Koşullu ifadeler:`if...then...else`</span><span class="sxs-lookup"><span data-stu-id="b9c20-104">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="b9c20-105">`if...then...else` İfade kodunun farklı dalları çalıştırır ve verilen Boole ifadesi bağlı olarak farklı bir değere de değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="b9c20-105">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>


## <a name="syntax"></a><span data-ttu-id="b9c20-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b9c20-106">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="b9c20-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9c20-107">Remarks</span></span>
<span data-ttu-id="b9c20-108">Önceki sözdiziminde *İfade1* Boole ifadesi olarak değerlendirildiğinde çalıştıran `true`; Aksi halde, *İfade2* çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="b9c20-108">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="b9c20-109">Aksine başka dillerde `if...then...else` yapıdır bir ifade, bir ifade.</span><span class="sxs-lookup"><span data-stu-id="b9c20-109">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="b9c20-110">Yürütür şube son ifade değeri bir değer üreten anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b9c20-110">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="b9c20-111">Her dalda üretilen değerlerin türleri eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="b9c20-111">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="b9c20-112">Varsa ACE'si `else` dal, kendi türüdür `unit`.</span><span class="sxs-lookup"><span data-stu-id="b9c20-112">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="b9c20-113">Bu nedenle, varsa türünü `then` dalı olan herhangi bir tür dışında `unit`, olmalıdır bir `else` şube aynı dönüş türüne sahip.</span><span class="sxs-lookup"><span data-stu-id="b9c20-113">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="b9c20-114">Zincirleme zaman `if...then...else` ifadeleri birlikte, anahtar sözcüğünü kullanabilirsiniz `elif` yerine `else if`; bunlar eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="b9c20-114">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="b9c20-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="b9c20-115">Example</span></span>
<span data-ttu-id="b9c20-116">Aşağıdaki örnekte nasıl kullanılacağını anlatan `if...then...else` ifade.</span><span class="sxs-lookup"><span data-stu-id="b9c20-116">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
John
910 is less than 20
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="b9c20-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b9c20-117">See Also</span></span>
[<span data-ttu-id="b9c20-118">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="b9c20-118">F# Language Reference</span></span>](index.md)

