---
title: 'Lambda Ifadeleri: Eğlenceli anahtar sözcüğü'
description: Anonim bir işlev olan bir F# lambda ifadesi tanımlamak için ' Fun ' anahtar sözcüğünü nasıl kullanacağınızı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 9818724686dd83a7e352fb36819289fa19b002df
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630669"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="3fe0f-103">Lambda Ifadeleri: Fun anahtar sözcüğü (F#)</span><span class="sxs-lookup"><span data-stu-id="3fe0f-103">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="3fe0f-104">`fun` Anahtar sözcüğü bir lambda ifadesi, yani anonim bir işlev tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3fe0f-104">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>

## <a name="syntax"></a><span data-ttu-id="3fe0f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3fe0f-105">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="3fe0f-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3fe0f-106">Remarks</span></span>

<span data-ttu-id="3fe0f-107">*Parametre listesi* genellikle ad ve isteğe bağlı olarak parametre türlerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="3fe0f-107">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="3fe0f-108">Daha genel olarak, *parametre listesi* herhangi bir F# desenden oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="3fe0f-108">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="3fe0f-109">Olası desenlerin tam listesi için bkz. [desen eşleştirme](../pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="3fe0f-109">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="3fe0f-110">Geçerli parametrelerin listeleri aşağıdaki örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3fe0f-110">Lists of valid parameters include the following examples.</span></span>

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

<span data-ttu-id="3fe0f-111">*İfade* , bir dönüş değeri üreten son ifadesi olan işlevinin gövdesidir.</span><span class="sxs-lookup"><span data-stu-id="3fe0f-111">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="3fe0f-112">Geçerli lambda ifadesi örnekleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="3fe0f-112">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a><span data-ttu-id="3fe0f-113">Lambda İfadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="3fe0f-113">Using Lambda Expressions</span></span>

<span data-ttu-id="3fe0f-114">Lambda ifadeleri özellikle bir liste veya başka bir koleksiyon üzerinde işlemler gerçekleştirmek istediğinizde ve bir işlev tanımlamayı önlemek istediğinizde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="3fe0f-114">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="3fe0f-115">Birçok F# kitaplık işlevi işlev değerlerini bağımsız değişken olarak alır ve özellikle bu durumlarda bir lambda ifadesi kullanmak kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3fe0f-115">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="3fe0f-116">Aşağıdaki kod, bir listenin öğelerine bir lambda ifadesi uygular.</span><span class="sxs-lookup"><span data-stu-id="3fe0f-116">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="3fe0f-117">Bu durumda, anonim işlev bir listenin her öğesine 1 ekler.</span><span class="sxs-lookup"><span data-stu-id="3fe0f-117">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a><span data-ttu-id="3fe0f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fe0f-118">See also</span></span>

- [<span data-ttu-id="3fe0f-119">İşlevler</span><span class="sxs-lookup"><span data-stu-id="3fe0f-119">Functions</span></span>](index.md)
