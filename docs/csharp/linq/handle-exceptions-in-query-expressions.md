---
title: Sorgu ifadelerindeki özel durumları işleme (C#'da LINQ)
description: C#'daki LINQ sorgu ifadelerindeki özel durumları nasıl işleyeceğinizi öğrenin.
ms.date: 12/01/2016
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: f900669412026e69598d3939c51ff8208b51b7ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688507"
---
# <a name="handle-exceptions-in-query-expressions"></a><span data-ttu-id="3657a-103">Sorgu ifadelerinde özel durumları işleme</span><span class="sxs-lookup"><span data-stu-id="3657a-103">Handle exceptions in query expressions</span></span>

<span data-ttu-id="3657a-104">Sorgu ifadesi bağlamında herhangi bir yöntemi çağırmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="3657a-104">It's possible to call any method in the context of a query expression.</span></span> <span data-ttu-id="3657a-105">Ancak, sorgu ifadesinde veri kaynağının içeriğini değiştirme veya özel durum atma gibi bir yan etki oluşturabilecek herhangi bir yöntemi çağırmaktan kaçınmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="3657a-105">However, we recommend that you avoid calling any method in a query expression that can create a side effect such as modifying the contents of the data source or throwing an exception.</span></span> <span data-ttu-id="3657a-106">Bu örnek, özel durum işleme genel .NET yönergelerini ihlal etmeden bir sorgu ifadesinde yöntemleri çağırdığınızda özel durumlar alabilmeyi nasıl önleyisiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="3657a-106">This example shows how to avoid raising exceptions when you call methods in a query expression without violating the general .NET guidelines on exception handling.</span></span> <span data-ttu-id="3657a-107">Bu yönergeler, belirli bir içeriğe neden atıldığını anladığınızda belirli bir özel durumu yakalamanın kabul edilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3657a-107">Those guidelines state that it's acceptable to catch a specific exception when you understand why it's thrown in a given context.</span></span> <span data-ttu-id="3657a-108">Daha fazla bilgi [için Özel Durumlar için En İyi Uygulamalar'a](../../standard/exceptions/best-practices-for-exceptions.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="3657a-108">For more information, see [Best Practices for Exceptions](../../standard/exceptions/best-practices-for-exceptions.md).</span></span>

<span data-ttu-id="3657a-109">Son örnek, sorgunun yürütülmesi sırasında bir özel durum atmanız gerektiğinde bu servis taleplerini nasıl işleyeceğinizgöster.</span><span class="sxs-lookup"><span data-stu-id="3657a-109">The final example shows how to handle those cases when you must throw an exception during execution of a query.</span></span>

## <a name="example"></a><span data-ttu-id="3657a-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="3657a-110">Example</span></span>

<span data-ttu-id="3657a-111">Aşağıdaki örnek, özel durum işleme kodunun sorgu ifadesinin dışına nasıl taşınılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3657a-111">The following example shows how to move exception handling code outside a query expression.</span></span> <span data-ttu-id="3657a-112">Bu, yalnızca yöntem sorgunun yerel değişkenlerine bağlı olmadığında mümkündür.</span><span class="sxs-lookup"><span data-stu-id="3657a-112">This is only possible when the method does not depend on any variables local to the query.</span></span>

[!code-csharp[csProgGuideLINQ#10](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]

## <a name="example"></a><span data-ttu-id="3657a-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="3657a-113">Example</span></span>

<span data-ttu-id="3657a-114">Bazı durumlarda, sorgu nun içinden atılan bir özel durum için en iyi yanıt, sorgu yürütmesini hemen durdurmak olabilir.</span><span class="sxs-lookup"><span data-stu-id="3657a-114">In some cases, the best response to an exception that is thrown from within a query might be to stop the query execution immediately.</span></span> <span data-ttu-id="3657a-115">Aşağıdaki örnek, sorgu gövdesinin içinden atılabilecek özel durumların nasıl işleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3657a-115">The following example shows how to handle exceptions that might be thrown from inside a query body.</span></span> <span data-ttu-id="3657a-116">Sorgu `SomeMethodThatMightThrow` yürütmesinin durmasını gerektiren bir özel durum neden olabileceğini varsayalım.</span><span class="sxs-lookup"><span data-stu-id="3657a-116">Assume that `SomeMethodThatMightThrow` can potentially cause an exception that requires the query execution to stop.</span></span>

<span data-ttu-id="3657a-117">Bloğun sorgunun `try` kendisini değil, döngüyü `foreach` kapladığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3657a-117">Note that the `try` block encloses the `foreach` loop, and not the query itself.</span></span> <span data-ttu-id="3657a-118">Bunun nedeni, `foreach` döngünün sorgunun gerçekte yürütüldolduğu nokta olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="3657a-118">This is because the `foreach` loop is the point at which the query is actually executed.</span></span> <span data-ttu-id="3657a-119">Daha fazla bilgi için [LINQ sorgularına giriş etüt ünt.'e](../programming-guide/concepts/linq/introduction-to-linq-queries.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="3657a-119">For more information, see [Introduction to LINQ queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

[!code-csharp[csProgGuideLINQ#12](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]

## <a name="see-also"></a><span data-ttu-id="3657a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3657a-120">See also</span></span>

- [<span data-ttu-id="3657a-121">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="3657a-121">Language Integrated Query (LINQ)</span></span>](index.md)
