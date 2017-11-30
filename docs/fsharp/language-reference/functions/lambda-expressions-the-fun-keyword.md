---
title: "Lambda İfadeleri: fun Anahtar Sözcüğü (F#)"
description: "F # 'eğlenceli' anahtar sözcüğü adsız bir işlev bir lambda ifadesi tanımlamak için nasıl kullanılacağını öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e5d3565c-d7cc-433f-a619-886ed92523a7
ms.openlocfilehash: 09f1c1787bbb4b86ec40f9e973e08104919631aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="01950-104">Lambda İfadeleri: fun Anahtar Sözcüğü (F#)</span><span class="sxs-lookup"><span data-stu-id="01950-104">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="01950-105">`fun` Anahtar sözcüğü bir lambda ifadesi, başka bir deyişle, adsız bir işlev tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="01950-105">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>


## <a name="syntax"></a><span data-ttu-id="01950-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01950-106">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="01950-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01950-107">Remarks</span></span>
<span data-ttu-id="01950-108">*Parametre listesi* genellikle adları ve parametre türlerini, isteğe bağlı olarak, oluşur.</span><span class="sxs-lookup"><span data-stu-id="01950-108">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="01950-109">Daha fazla genel olarak, *parametre listesi* herhangi F # desenlerini oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="01950-109">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="01950-110">Olası desenleri tam bir listesi için bkz: [desen eşleştirme](../pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="01950-110">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="01950-111">Geçerli parametreler listesi örnek olarak şunlar gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="01950-111">Lists of valid parameters include the following examples.</span></span>

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

<span data-ttu-id="01950-112">*İfade* gövdesi işlevinin biri son deyim dönüş değeri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="01950-112">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="01950-113">Geçerli lambda ifadeleri örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="01950-113">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]
    
## <a name="using-lambda-expressions"></a><span data-ttu-id="01950-114">Lambda İfadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="01950-114">Using Lambda Expressions</span></span>
<span data-ttu-id="01950-115">Lambda ifadeleri bir liste veya diğer koleksiyon üzerinde işlem gerçekleştirmek ve bir işlev tanımlamanın ek iş önlemek istiyorsanız istediğinizde özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="01950-115">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="01950-116">Birçok F # kitaplığı işlevi bağımsız değişken olarak işlevi değerleri alır ve bir lambda ifadesi bu gibi durumlarda kullanılacak özellikle kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="01950-116">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="01950-117">Aşağıdaki kod bir lambda ifadesi bir liste öğelerine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="01950-117">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="01950-118">Bu durumda, anonim işlevi listesini her öğeye 1 ekler.</span><span class="sxs-lookup"><span data-stu-id="01950-118">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]
    
## <a name="see-also"></a><span data-ttu-id="01950-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="01950-119">See Also</span></span>
[<span data-ttu-id="01950-120">İşlevler</span><span class="sxs-lookup"><span data-stu-id="01950-120">Functions</span></span>](index.md)
