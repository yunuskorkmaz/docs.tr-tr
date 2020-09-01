---
description: Bağlamsal anahtar sözcük-C# başvurusu
title: Bağlamsal anahtar sözcük-C# başvurusu
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: bd3a7beeb7d3c4b62d6b70e2b1c6f38ab4b6804f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138221"
---
# <a name="when-c-reference"></a><span data-ttu-id="9d721-103">ne zaman (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9d721-103">when (C# Reference)</span></span>

<span data-ttu-id="9d721-104">`when`Aşağıdaki bağlamlarda bir filtre koşulu belirtmek için bağlamsal anahtar sözcüğünü kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9d721-104">You can use the `when` contextual keyword to specify a filter condition in the following contexts:</span></span>

- <span data-ttu-id="9d721-105">`catch` [Try/catch](try-catch.md) veya [try/catch/finally](try-catch-finally.md) bloğunun bildiriminde.</span><span class="sxs-lookup"><span data-stu-id="9d721-105">In the `catch` statement of a [try/catch](try-catch.md) or [try/catch/finally](try-catch-finally.md) block.</span></span>
- <span data-ttu-id="9d721-106">`case`Bir [Switch](switch.md) ifadesinin etiketinde.</span><span class="sxs-lookup"><span data-stu-id="9d721-106">In the `case` label of a [switch](switch.md) statement.</span></span>
- <span data-ttu-id="9d721-107">[ `switch` İfadesi](../operators/switch-expression.md).</span><span class="sxs-lookup"><span data-stu-id="9d721-107">In the [`switch` expression](../operators/switch-expression.md).</span></span>

## <a name="when-in-a-catch-statement"></a><span data-ttu-id="9d721-108">`when` bir `catch` ifadede</span><span class="sxs-lookup"><span data-stu-id="9d721-108">`when` in a `catch` statement</span></span>

<span data-ttu-id="9d721-109">C# 6 ' dan itibaren, `when` `catch` belirli bir özel durumun yürütülmesi için doğru olması gereken bir koşul belirtmek üzere bir bildirimde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d721-109">Starting with C# 6, `when` can be used in a `catch` statement to specify a condition that must be true for the handler for a specific exception to execute.</span></span> <span data-ttu-id="9d721-110">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="9d721-110">Its syntax is:</span></span>

```csharp
catch (ExceptionType [e]) when (expr)
```

<span data-ttu-id="9d721-111">Burada *Expr* , Boolean değer değerlendiren bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="9d721-111">where *expr* is an expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="9d721-112">Döndürürse `true` , özel durum işleyicisi yürütülür; varsa, yapmaz `false` .</span><span class="sxs-lookup"><span data-stu-id="9d721-112">If it returns `true`, the exception handler executes; if `false`, it does not.</span></span>

<span data-ttu-id="9d721-113">Aşağıdaki örnek, `when` <xref:System.Net.Http.HttpRequestException> özel durum iletisinin metnine bağlı olarak işleyicileri koşullu olarak yürütmek için anahtar sözcüğünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="9d721-113">The following example uses the `when` keyword to conditionally execute handlers for an <xref:System.Net.Http.HttpRequestException> depending on the text of the exception message.</span></span>

[!code-csharp[when-with-catch](~/samples/snippets/csharp/language-reference/keywords/when/catch.cs)]

## <a name="when-in-a-switch-statement"></a><span data-ttu-id="9d721-114">`when` bir `switch` ifadede</span><span class="sxs-lookup"><span data-stu-id="9d721-114">`when` in a `switch` statement</span></span>

<span data-ttu-id="9d721-115">C# 7,0 ' den başlayarak `case` etiketlerin artık birbirini dışlamalı olması gerekmez ve `case` etiketlerin bir bildirimde görünme sırası `switch` hangi anahtar bloğunun çalıştırılacağını tespit edebilir.</span><span class="sxs-lookup"><span data-stu-id="9d721-115">Starting with C# 7.0, `case` labels no longer need be mutually exclusive, and the order in which `case` labels appear in a `switch` statement can determine which switch block executes.</span></span> <span data-ttu-id="9d721-116">`when`Anahtar sözcüğü, ilişkili Case etiketinin doğru olmasına neden olan bir filtre koşulunu belirtmek için kullanılabilir ve yalnızca filtre koşulu da geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="9d721-116">The `when` keyword can be used to specify a filter condition that causes its associated case label to be true only if the filter condition is also true.</span></span> <span data-ttu-id="9d721-117">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="9d721-117">Its syntax is:</span></span>

```csharp
case (expr) when (when-condition):
```

<span data-ttu-id="9d721-118">Burada *Expr* , Match ifadesiyle karşılaştırılan sabit bir model veya tür deseninin olduğu *durumlarda-Condition* herhangi bir Boolean ifadedir.</span><span class="sxs-lookup"><span data-stu-id="9d721-118">where *expr* is a constant pattern or type pattern that is compared to the match expression, and *when-condition* is any Boolean expression.</span></span>

<span data-ttu-id="9d721-119">Aşağıdaki örnek, `when` `Shape` bir alanı sıfır olan nesneleri test etmek ve `Shape` sıfırdan büyük bir alana sahip çeşitli nesneleri test etmek için anahtar sözcüğünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="9d721-119">The following example uses the `when` keyword to test for `Shape` objects that have an area of zero, as well as to test for a variety of `Shape` objects that have an area greater than zero.</span></span>

[!code-csharp[when-with-case#1](~/samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]

## <a name="see-also"></a><span data-ttu-id="9d721-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d721-120">See also</span></span>

- [<span data-ttu-id="9d721-121">switch deyimi</span><span class="sxs-lookup"><span data-stu-id="9d721-121">switch statement</span></span>](switch.md)
- [<span data-ttu-id="9d721-122">Try/Catch ekstresi</span><span class="sxs-lookup"><span data-stu-id="9d721-122">try/catch statement</span></span>](try-catch.md)
- [<span data-ttu-id="9d721-123">try/catch/finally ekstresi</span><span class="sxs-lookup"><span data-stu-id="9d721-123">try/catch/finally statement</span></span>](try-catch-finally.md)
