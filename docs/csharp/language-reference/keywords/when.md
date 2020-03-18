---
title: bağlamsal anahtar kelime - C# Reference
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: 6a61c42ba2d01e84ffae376bf95c99877437be85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712838"
---
# <a name="when-c-reference"></a><span data-ttu-id="0319e-102">ne zaman (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="0319e-102">when (C# Reference)</span></span>

<span data-ttu-id="0319e-103">`when` Bir filtre koşulunu iki bağlamda belirtmek için bağlamsal anahtar sözcüğü kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0319e-103">You can use the `when` contextual keyword to specify a filter condition in two contexts:</span></span>

- <span data-ttu-id="0319e-104">Bir `catch` [deneyin / yakalamak](try-catch.md) veya denemek / yakalamak [/ nihayet](try-catch-finally.md) blok ifadesinde.</span><span class="sxs-lookup"><span data-stu-id="0319e-104">In the `catch` statement of a [try/catch](try-catch.md) or [try/catch/finally](try-catch-finally.md) block.</span></span>
- <span data-ttu-id="0319e-105">Anahtar `case` deyiminin [switch](switch.md) etiketinde.</span><span class="sxs-lookup"><span data-stu-id="0319e-105">In the `case` label of a [switch](switch.md) statement.</span></span>

## <a name="when-in-a-catch-statement"></a><span data-ttu-id="0319e-106">`when`bir `catch` açıklamada</span><span class="sxs-lookup"><span data-stu-id="0319e-106">`when` in a `catch` statement</span></span>

<span data-ttu-id="0319e-107">C# 6 ile `when` başlayarak, `catch` belirli bir özel durum yürütmek için işleyici için doğru olması gereken bir koşul belirtmek için bir deyim kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0319e-107">Starting with C# 6, `when` can be used in a `catch` statement to specify a condition that must be true for the handler for a specific exception to execute.</span></span> <span data-ttu-id="0319e-108">Sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="0319e-108">Its syntax is:</span></span>

```csharp
catch (ExceptionType [e]) when (expr)
```

<span data-ttu-id="0319e-109">*expr* bir Boolean değerine değerlendiren bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="0319e-109">where *expr* is an expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="0319e-110">Dönerse, `true`özel durum işleyicisi yürütür; eğer `false`, bu değil.</span><span class="sxs-lookup"><span data-stu-id="0319e-110">If it returns `true`, the exception handler executes; if `false`, it does not.</span></span>

<span data-ttu-id="0319e-111">Aşağıdaki örnek, `when` özel durum iletisinin metnine <xref:System.Net.Http.HttpRequestException> bağlı olarak işleyicileri koşullu olarak yürütmek için anahtar sözcüğü kullanır.</span><span class="sxs-lookup"><span data-stu-id="0319e-111">The following example uses the `when` keyword to conditionally execute handlers for an <xref:System.Net.Http.HttpRequestException> depending on the text of the exception message.</span></span>

[!code-csharp[when-with-catch](~/samples/snippets/csharp/language-reference/keywords/when/catch.cs)]

## <a name="when-in-a-switch-statement"></a><span data-ttu-id="0319e-112">`when`bir `switch` açıklamada</span><span class="sxs-lookup"><span data-stu-id="0319e-112">`when` in a `switch` statement</span></span>

<span data-ttu-id="0319e-113">C# 7.0 ile `case` başlayarak, etiketlerin artık birbirini dışlayan `case` olması gerekmez `switch` ve bir deyimde etiketlerin görünme sırası hangi anahtar bloğunun yürütüleceğini belirleyebilir.</span><span class="sxs-lookup"><span data-stu-id="0319e-113">Starting with C# 7.0, `case` labels no longer need be mutually exclusive, and the order in which `case` labels appear in a `switch` statement can determine which switch block executes.</span></span> <span data-ttu-id="0319e-114">Anahtar `when` kelime, yalnızca filtre koşulu da doğruysa ilişkili durum etiketinin doğru olmasını sağlayan bir filtre koşulu belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0319e-114">The `when` keyword can be used to specify a filter condition that causes its associated case label to be true only if the filter condition is also true.</span></span> <span data-ttu-id="0319e-115">Sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="0319e-115">Its syntax is:</span></span>

```csharp
case (expr) when (when-condition):
```

<span data-ttu-id="0319e-116">*expr* eşleşme ifadesi ile karşılaştırıldığında sabit bir desen veya tür deseni nerede ve *ne zaman koşul* herhangi bir Boolean ifadedir.</span><span class="sxs-lookup"><span data-stu-id="0319e-116">where *expr* is a constant pattern or type pattern that is compared to the match expression, and *when-condition* is any Boolean expression.</span></span>

<span data-ttu-id="0319e-117">Aşağıdaki `when` örnekte, sıfır lık `Shape` bir alana sahip nesneler için test etmek ve sıfırdan `Shape` büyük bir alana sahip çeşitli nesneleri sınamak için anahtar kelime kullanır.</span><span class="sxs-lookup"><span data-stu-id="0319e-117">The following example uses the `when` keyword to test for `Shape` objects that have an area of zero, as well as to test for a variety of `Shape` objects that have an area greater than zero.</span></span>

[!code-csharp[when-with-case#1](~/samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]

## <a name="see-also"></a><span data-ttu-id="0319e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0319e-118">See also</span></span>

- [<span data-ttu-id="0319e-119">anahtar deyimi</span><span class="sxs-lookup"><span data-stu-id="0319e-119">switch statement</span></span>](switch.md)
- [<span data-ttu-id="0319e-120">try/catch deyimi</span><span class="sxs-lookup"><span data-stu-id="0319e-120">try/catch statement</span></span>](try-catch.md)
- [<span data-ttu-id="0319e-121">try/catch/finally deyimi</span><span class="sxs-lookup"><span data-stu-id="0319e-121">try/catch/finally statement</span></span>](try-catch-finally.md)
