---
title: Bağlamsal anahtar sözcük C# referansı
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: 6a61c42ba2d01e84ffae376bf95c99877437be85
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712838"
---
# <a name="when-c-reference"></a><span data-ttu-id="51c4f-102">ne zamanC# (başvuru)</span><span class="sxs-lookup"><span data-stu-id="51c4f-102">when (C# Reference)</span></span>

<span data-ttu-id="51c4f-103">İki bağlamda bir filtre koşulu belirtmek için `when` bağlamsal anahtar sözcüğünü kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="51c4f-103">You can use the `when` contextual keyword to specify a filter condition in two contexts:</span></span>

- <span data-ttu-id="51c4f-104">[Try/catch](try-catch.md) veya [try/catch/finally](try-catch-finally.md) bloğunun `catch` bildiriminde.</span><span class="sxs-lookup"><span data-stu-id="51c4f-104">In the `catch` statement of a [try/catch](try-catch.md) or [try/catch/finally](try-catch-finally.md) block.</span></span>
- <span data-ttu-id="51c4f-105">[Switch](switch.md) ifadesinin `case` etiketinde.</span><span class="sxs-lookup"><span data-stu-id="51c4f-105">In the `case` label of a [switch](switch.md) statement.</span></span>

## <a name="when-in-a-catch-statement"></a><span data-ttu-id="51c4f-106">`catch` bildiriminde `when`</span><span class="sxs-lookup"><span data-stu-id="51c4f-106">`when` in a `catch` statement</span></span>

<span data-ttu-id="51c4f-107">C# 6 ' dan itibaren, belirli bir özel durumun yürütülmesi için doğru olması gereken bir koşul belirtmek üzere bir `catch` bildiriminde `when` kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="51c4f-107">Starting with C# 6, `when` can be used in a `catch` statement to specify a condition that must be true for the handler for a specific exception to execute.</span></span> <span data-ttu-id="51c4f-108">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="51c4f-108">Its syntax is:</span></span>

```csharp
catch (ExceptionType [e]) when (expr)
```

<span data-ttu-id="51c4f-109">Burada *Expr* , Boolean değer değerlendiren bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="51c4f-109">where *expr* is an expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="51c4f-110">`true`döndürürse, özel durum işleyicisi yürütülür; `false`, değildir.</span><span class="sxs-lookup"><span data-stu-id="51c4f-110">If it returns `true`, the exception handler executes; if `false`, it does not.</span></span>

<span data-ttu-id="51c4f-111">Aşağıdaki örnek, özel durum iletisinin metnine bağlı olarak bir <xref:System.Net.Http.HttpRequestException> için işleyicileri koşullu olarak yürütmek üzere `when` anahtar sözcüğünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="51c4f-111">The following example uses the `when` keyword to conditionally execute handlers for an <xref:System.Net.Http.HttpRequestException> depending on the text of the exception message.</span></span>

[!code-csharp[when-with-catch](~/samples/snippets/csharp/language-reference/keywords/when/catch.cs)]

## <a name="when-in-a-switch-statement"></a><span data-ttu-id="51c4f-112">`switch` bildiriminde `when`</span><span class="sxs-lookup"><span data-stu-id="51c4f-112">`when` in a `switch` statement</span></span>

<span data-ttu-id="51c4f-113">7,0 ile C# başlayarak, artık `case` etiketlere gerek kalmaz ve `case` etiketlerin `switch` bir bildirimde görünme sırası, hangi anahtar bloğunun çalıştırılacağını tespit edebilir.</span><span class="sxs-lookup"><span data-stu-id="51c4f-113">Starting with C# 7.0, `case` labels no longer need be mutually exclusive, and the order in which `case` labels appear in a `switch` statement can determine which switch block executes.</span></span> <span data-ttu-id="51c4f-114">`when` anahtar sözcüğü, ilişkili Case etiketinin doğru olmasına neden olan filtre koşulunu belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="51c4f-114">The `when` keyword can be used to specify a filter condition that causes its associated case label to be true only if the filter condition is also true.</span></span> <span data-ttu-id="51c4f-115">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="51c4f-115">Its syntax is:</span></span>

```csharp
case (expr) when (when-condition):
```

<span data-ttu-id="51c4f-116">Burada *Expr* , Match ifadesiyle karşılaştırılan sabit bir model veya tür deseninin olduğu *durumlarda-Condition* herhangi bir Boolean ifadedir.</span><span class="sxs-lookup"><span data-stu-id="51c4f-116">where *expr* is a constant pattern or type pattern that is compared to the match expression, and *when-condition* is any Boolean expression.</span></span>

<span data-ttu-id="51c4f-117">Aşağıdaki örnek, bir alanı sıfır olan `Shape` nesneleri test etmek için `when` anahtar sözcüğünü ve sıfırdan büyük bir alana sahip çeşitli `Shape` nesnelerini test etmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="51c4f-117">The following example uses the `when` keyword to test for `Shape` objects that have an area of zero, as well as to test for a variety of `Shape` objects that have an area greater than zero.</span></span>

[!code-csharp[when-with-case#1](~/samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]

## <a name="see-also"></a><span data-ttu-id="51c4f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51c4f-118">See also</span></span>

- [<span data-ttu-id="51c4f-119">Switch deyimleri</span><span class="sxs-lookup"><span data-stu-id="51c4f-119">switch statement</span></span>](switch.md)
- [<span data-ttu-id="51c4f-120">Try/Catch ekstresi</span><span class="sxs-lookup"><span data-stu-id="51c4f-120">try/catch statement</span></span>](try-catch.md)
- [<span data-ttu-id="51c4f-121">try/catch/finally ekstresi</span><span class="sxs-lookup"><span data-stu-id="51c4f-121">try/catch/finally statement</span></span>](try-catch-finally.md)
