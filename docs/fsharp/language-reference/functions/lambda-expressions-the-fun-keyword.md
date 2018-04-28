---
title: 'Lambda İfadeleri: fun Anahtar Sözcüğü (F#)'
description: "F # 'eğlenceli' anahtar sözcüğü adsız bir işlev bir lambda ifadesi tanımlamak için nasıl kullanılacağını öğrenin."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: f2f15a1b482ce3971d0b3d5ffc4f6dcc9ccf1569
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="88c91-103">Lambda İfadeleri: fun Anahtar Sözcüğü (F#)</span><span class="sxs-lookup"><span data-stu-id="88c91-103">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="88c91-104">`fun` Anahtar sözcüğü bir lambda ifadesi, başka bir deyişle, adsız bir işlev tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="88c91-104">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>


## <a name="syntax"></a><span data-ttu-id="88c91-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88c91-105">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="88c91-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88c91-106">Remarks</span></span>
<span data-ttu-id="88c91-107">*Parametre listesi* genellikle adları ve parametre türlerini, isteğe bağlı olarak, oluşur.</span><span class="sxs-lookup"><span data-stu-id="88c91-107">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="88c91-108">Daha fazla genel olarak, *parametre listesi* herhangi F # desenlerini oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="88c91-108">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="88c91-109">Olası desenleri tam bir listesi için bkz: [desen eşleştirme](../pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="88c91-109">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="88c91-110">Geçerli parametreler listesi örnek olarak şunlar gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="88c91-110">Lists of valid parameters include the following examples.</span></span>

```fsharp
// Lambda expressions with parameter lists.
fun a b c -> ...
fun (a: int) b c -> ...
fun (a : int) (b : string) (c:float) -> ...

// A lambda expression with a tuple pattern.
fun (a, b) -> …

// A lambda expression with a list pattern.
fun head :: tail -> …
```

<span data-ttu-id="88c91-111">*İfade* gövdesi işlevinin biri son deyim dönüş değeri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="88c91-111">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="88c91-112">Geçerli lambda ifadeleri örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="88c91-112">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]
    
## <a name="using-lambda-expressions"></a><span data-ttu-id="88c91-113">Lambda İfadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="88c91-113">Using Lambda Expressions</span></span>
<span data-ttu-id="88c91-114">Lambda ifadeleri bir liste veya diğer koleksiyon üzerinde işlem gerçekleştirmek ve bir işlev tanımlamanın ek iş önlemek istiyorsanız istediğinizde özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="88c91-114">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="88c91-115">Birçok F # kitaplığı işlevi bağımsız değişken olarak işlevi değerleri alır ve bir lambda ifadesi bu gibi durumlarda kullanılacak özellikle kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="88c91-115">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="88c91-116">Aşağıdaki kod bir lambda ifadesi bir liste öğelerine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="88c91-116">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="88c91-117">Bu durumda, anonim işlevi listesini her öğeye 1 ekler.</span><span class="sxs-lookup"><span data-stu-id="88c91-117">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]
    
## <a name="see-also"></a><span data-ttu-id="88c91-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="88c91-118">See Also</span></span>
[<span data-ttu-id="88c91-119">İşlevler</span><span class="sxs-lookup"><span data-stu-id="88c91-119">Functions</span></span>](index.md)
