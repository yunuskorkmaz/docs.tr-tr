---
title: 'Lambda İfadeleri: fun Anahtar Sözcüğü (F#)'
description: "Anonim bir işlevdir bir lambda ifadesi tanımlamak için F # 'eğlenceli' anahtar sözcüğünü kullanmayı öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: a37757f6b7328cd348bbf13f058a6dbc881769cf
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46525525"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="7ea34-103">Lambda İfadeleri: fun Anahtar Sözcüğü (F#)</span><span class="sxs-lookup"><span data-stu-id="7ea34-103">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="7ea34-104">`fun` Anahtar sözcüğü, bir lambda ifadesi, başka bir deyişle, anonim bir işlev tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7ea34-104">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>

## <a name="syntax"></a><span data-ttu-id="7ea34-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ea34-105">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="7ea34-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ea34-106">Remarks</span></span>

<span data-ttu-id="7ea34-107">*Parametre-listesi* genellikle adları ve parametre türleri, isteğe bağlı olarak oluşur.</span><span class="sxs-lookup"><span data-stu-id="7ea34-107">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="7ea34-108">Daha genel *parametre-listesi* tüm F # desenlerini oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="7ea34-108">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="7ea34-109">Olası desenleri tam bir listesi için bkz. [desen eşleştirme](../pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="7ea34-109">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="7ea34-110">Geçerli parametrelerin bir listesi aşağıdaki örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="7ea34-110">Lists of valid parameters include the following examples.</span></span>

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

<span data-ttu-id="7ea34-111">*İfade* biri son deyim dönüş değeri oluşturur işlev gövdesidir.</span><span class="sxs-lookup"><span data-stu-id="7ea34-111">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="7ea34-112">Geçerli lambda ifadeleri örnekleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="7ea34-112">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a><span data-ttu-id="7ea34-113">Lambda İfadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="7ea34-113">Using Lambda Expressions</span></span>

<span data-ttu-id="7ea34-114">Lambda ifadeleri, özellikle bir liste veya diğer toplama işlemleri ve bir işlevi tanımlayan kaynaklanan ek yükten kaçınmak istiyorsanız istediğinizde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="7ea34-114">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="7ea34-115">İşlev değerleri olarak bağımsız değişkenler çoğu F # kitaplığı işlevleri yararlanın ve bir lambda ifadesi bu gibi durumlarda kullanılacak özellikle kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7ea34-115">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="7ea34-116">Aşağıdaki kod bir lambda ifadesi bir liste öğelerine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7ea34-116">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="7ea34-117">Bu durumda, anonim işlev listesini her öğeye 1 ekler.</span><span class="sxs-lookup"><span data-stu-id="7ea34-117">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a><span data-ttu-id="7ea34-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ea34-118">See also</span></span>

- [<span data-ttu-id="7ea34-119">İşlevler</span><span class="sxs-lookup"><span data-stu-id="7ea34-119">Functions</span></span>](index.md)
