---
title: zaman (C# Başvurusu)
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: a71cbdce256b1c1bd5d101d66f216fb229d70adf
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47401137"
---
 # <a name="when-c-reference"></a><span data-ttu-id="f3970-102">zaman (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f3970-102">when (C# Reference)</span></span>

<span data-ttu-id="f3970-103">Kullanabileceğiniz `when` iki bağlamlarda bir filtre koşulu belirtmek için bağlamsal anahtar sözcük:</span><span class="sxs-lookup"><span data-stu-id="f3970-103">You can use the `when` contextual keyword to specify a filter condition in two contexts:</span></span>

- <span data-ttu-id="f3970-104">İçinde `catch` deyiminin bir [try/catch](try-catch.md) veya [try/catch/finally](try-catch-finally.md) blok.</span><span class="sxs-lookup"><span data-stu-id="f3970-104">In the `catch` statement of a [try/catch](try-catch.md) or [try/catch/finally](try-catch-finally.md) block.</span></span>
- <span data-ttu-id="f3970-105">İçinde `case` etiketi bir [geçiş](switch.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="f3970-105">In the `case` label of a [switch](switch.md) statement.</span></span>

## <a name="when-in-a-catch-statement"></a><span data-ttu-id="f3970-106">`when` içinde bir `catch` deyimi</span><span class="sxs-lookup"><span data-stu-id="f3970-106">`when` in a `catch` statement</span></span>

<span data-ttu-id="f3970-107">C# 6 ile başlayarak `When` kullanılabilir bir `catch` deyimini yürütmek belirli bir özel durum işleyicisi için doğru bir koşulu belirtin.</span><span class="sxs-lookup"><span data-stu-id="f3970-107">Starting with C# 6, `When` can be used in a `catch` statement to specify a condition that must be true for the handler for a specific exception to execute.</span></span> <span data-ttu-id="f3970-108">Kendi sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f3970-108">Its syntax is:</span></span>

```csharp
catch ExceptionType [e] when (expr)
```
<span data-ttu-id="f3970-109">Burada *expr* bir Boole değerini döndüren bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="f3970-109">where *expr* is an expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="f3970-110">Döndürürse `true`, özel durum işleyicisi; ise yürütülür `false`, yok.</span><span class="sxs-lookup"><span data-stu-id="f3970-110">If it returns `true`, the exception handler executes; if `false`, it does not.</span></span> 

<span data-ttu-id="f3970-111">Aşağıdaki örnekte `when` işleyicileri için koşullu olarak yürütülecek anahtar sözcüğü bir <xref:System.Net.Http.HttpRequestException> bağlı özel durum iletisi metni görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f3970-111">The following example uses the `when` keyword to conditionally execute handlers for an <xref:System.Net.Http.HttpRequestException> depending on the text of the exception message.</span></span>

 [!code-csharp[when-with-catch](../../../../samples/snippets/csharp/language-reference/keywords/when/catch.cs)]  
  
## <a name="when-in-a-switch-statement"></a><span data-ttu-id="f3970-112">`when` içinde bir `switch` deyimi</span><span class="sxs-lookup"><span data-stu-id="f3970-112">`when` in a `switch` statement</span></span>

<span data-ttu-id="f3970-113">C# 7.0 ile başlayan `case` etiketleri artık olması birbirini özel ve sırayı `case` etiketler görünür bir `switch` deyimi, hangi anahtar bloğu belirleyebilir yürütür.</span><span class="sxs-lookup"><span data-stu-id="f3970-113">Starting with C# 7.0, `case` labels no longer need be mutually exclusive, and the order in which `case` labels appear in a `switch` statement can determine which switch block executes.</span></span> <span data-ttu-id="f3970-114">`when` Anahtar sözcüğü, yalnızca filtre koşulu da true ise true olması, ilişkili case etiketi neden olan bir filtre koşulu belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f3970-114">The `when` keyword can be used to specify a filter condition that causes its associated case label to be true only if the filter condition is also true.</span></span> <span data-ttu-id="f3970-115">Kendi sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f3970-115">Its syntax is:</span></span>

```csharp
case (expr) when (when-condition):
```
<span data-ttu-id="f3970-116">Burada *expr* bir sabit desen veya eşleşme ifadesi için karşılaştırma türü desendir ve *olduğunda koşul* herhangi bir Boolean ifadesi.</span><span class="sxs-lookup"><span data-stu-id="f3970-116">where *expr* is a constant pattern or type pattern that is compared to the match expression, and *when-condition* is any Boolean expression.</span></span> 

<span data-ttu-id="f3970-117">Aşağıdaki örnekte `when` sınamak için anahtar sözcüğü `Shape` çeşitli için test etmek için sıfır de bir alan olan nesneleri `Shape` sıfırdan büyük bir alan olan nesne.</span><span class="sxs-lookup"><span data-stu-id="f3970-117">The following example uses the `when` keyword to test for `Shape` objects that have an area of zero, as well as to test for a variety of `Shape` objects that have an area greater than zero.</span></span> 

 [!code-csharp[when-with-case#1](../../../../samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]  

## <a name="see-also"></a><span data-ttu-id="f3970-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3970-118">See also</span></span>

- [<span data-ttu-id="f3970-119">switch deyimi</span><span class="sxs-lookup"><span data-stu-id="f3970-119">switch statement</span></span>](switch.md)  
- [<span data-ttu-id="f3970-120">try/catch deyimi</span><span class="sxs-lookup"><span data-stu-id="f3970-120">try/catch statement</span></span>](try-catch.md)  
- [<span data-ttu-id="f3970-121">try/catch/finally deyimi</span><span class="sxs-lookup"><span data-stu-id="f3970-121">try/catch/finally statement</span></span>](try-catch-finally.md) 
