---
title: 'Özel Durumlar: try...with İfadesi (F#)'
description: "Özel durum işleme için F # 'ile … Dene' ifadesi kullanmayı öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 588960c0f8ccedb431c37d0f1314bf1a293b638c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042172"
---
# <a name="exceptions-the-trywith-expression"></a><span data-ttu-id="1b621-103">Özel Durumlar: try...with İfadesi</span><span class="sxs-lookup"><span data-stu-id="1b621-103">Exceptions: The try...with Expression</span></span>

<span data-ttu-id="1b621-104">Bu konu başlığı altında açıklanır `try...with` ifade, özel durum F # dilinde işleme için kullanılan ifade.</span><span class="sxs-lookup"><span data-stu-id="1b621-104">This topic describes the `try...with` expression, the expression that is used for exception handling in the F# language.</span></span>

## <a name="syntax"></a><span data-ttu-id="1b621-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b621-105">Syntax</span></span>

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a><span data-ttu-id="1b621-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b621-106">Remarks</span></span>

<span data-ttu-id="1b621-107">`try...with` İfade, F # içinde özel durumları işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b621-107">The `try...with` expression is used to handle exceptions in F#.</span></span> <span data-ttu-id="1b621-108">Benzer `try...catch` C# deyimi.</span><span class="sxs-lookup"><span data-stu-id="1b621-108">It is similar to the `try...catch` statement in C#.</span></span> <span data-ttu-id="1b621-109">Önceki sözdiziminde, kodda *İfade1* bir özel durum oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="1b621-109">In the preceding syntax, the code in *expression1* might generate an exception.</span></span> <span data-ttu-id="1b621-110">`try...with` İfade bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="1b621-110">The `try...with` expression returns a value.</span></span> <span data-ttu-id="1b621-111">Hiçbir özel durum oluşturulursa, ifadenin değerini döndürür. *İfade1*.</span><span class="sxs-lookup"><span data-stu-id="1b621-111">If no exception is thrown, the whole expression returns the value of *expression1*.</span></span> <span data-ttu-id="1b621-112">Bir özel durum oluşur, her *deseni* sırayla karşılık gelen ilk eşleşen deseni yanı sıra, özel durum ile karşılaştırıldığında *ifade*olarak bilinen *özel durum işleyicisi*, o dalı çalıştırılır ve genel ifade, özel durum işleyicisinde ifadenin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="1b621-112">If an exception is thrown, each *pattern* is compared in turn with the exception, and for the first matching pattern, the corresponding *expression*, known as the *exception handler*, for that branch is executed, and the overall expression returns the value of the expression in that exception handler.</span></span> <span data-ttu-id="1b621-113">Herhangi bir desen eşleşirse, eşleşen bir işleyici bulunana kadar özel durum çağrı yığınına yayar.</span><span class="sxs-lookup"><span data-stu-id="1b621-113">If no pattern matches, the exception propagates up the call stack until a matching handler is found.</span></span> <span data-ttu-id="1b621-114">Özel durum işleyicileri her ifadesinden döndürülen değerlerin türleri ifade öğesinden döndürülen tür eşleşmelidir `try` blok.</span><span class="sxs-lookup"><span data-stu-id="1b621-114">The types of the values returned from each expression in the exception handlers must match the type returned from the expression in the `try` block.</span></span>

<span data-ttu-id="1b621-115">Sık sık hatayla ayrıca oluştu her özel durum işleyicisi ifadelerinde döndürüldüğü geçerli bir değer yoktur anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1b621-115">Frequently, the fact that an error occurred also means that there is no valid value that can be returned from the expressions in each exception handler.</span></span> <span data-ttu-id="1b621-116">Bir seçenek türünde ifade türüne sahip sık kullanılan bir desendir.</span><span class="sxs-lookup"><span data-stu-id="1b621-116">A frequent pattern is to have the type of the expression be an option type.</span></span> <span data-ttu-id="1b621-117">Aşağıdaki kod örneği, bu deseni gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1b621-117">The following code example illustrates this pattern.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

<span data-ttu-id="1b621-118">Özel durum .NET özel durumları olabilir veya F # özel durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b621-118">Exceptions can be .NET exceptions, or they can be F# exceptions.</span></span> <span data-ttu-id="1b621-119">F # özel durumları kullanarak tanımlayabilirsiniz `exception` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="1b621-119">You can define F# exceptions by using the `exception` keyword.</span></span>

<span data-ttu-id="1b621-120">Özel durum türü ve diğer koşulları filtrelemek için desenler çeşitli kullanabilirsiniz; Seçenekler aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="1b621-120">You can use a variety of patterns to filter on the exception type and other conditions; the options are summarized in the following table.</span></span>

|<span data-ttu-id="1b621-121">Desen</span><span class="sxs-lookup"><span data-stu-id="1b621-121">Pattern</span></span>|<span data-ttu-id="1b621-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b621-122">Description</span></span>|
|-------|-----------|
|<span data-ttu-id="1b621-123">:?</span><span class="sxs-lookup"><span data-stu-id="1b621-123">:?</span></span> <span data-ttu-id="1b621-124">*özel durum türü*</span><span class="sxs-lookup"><span data-stu-id="1b621-124">*exception-type*</span></span>|<span data-ttu-id="1b621-125">Belirtilen .NET özel durum türüyle eşleşen.</span><span class="sxs-lookup"><span data-stu-id="1b621-125">Matches the specified .NET exception type.</span></span>|
|<span data-ttu-id="1b621-126">:?</span><span class="sxs-lookup"><span data-stu-id="1b621-126">:?</span></span> <span data-ttu-id="1b621-127">*özel durum türü* olarak *tanımlayıcısı*</span><span class="sxs-lookup"><span data-stu-id="1b621-127">*exception-type* as *identifier*</span></span>|<span data-ttu-id="1b621-128">Belirtilen .NET özel durum türüyle eşleşen, ancak özel durum adlandırılmış bir değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b621-128">Matches the specified .NET exception type, but gives the exception a named value.</span></span>|
|<span data-ttu-id="1b621-129">*özel durum adı*(*bağımsız değişkenleri*)</span><span class="sxs-lookup"><span data-stu-id="1b621-129">*exception-name*(*arguments*)</span></span>|<span data-ttu-id="1b621-130">Bir F # özel durum türüyle eşleşen ve bağımsız değişkenler bağlar.</span><span class="sxs-lookup"><span data-stu-id="1b621-130">Matches an F# exception type and binds the arguments.</span></span>|
|<span data-ttu-id="1b621-131">*tanımlayıcı*</span><span class="sxs-lookup"><span data-stu-id="1b621-131">*identifier*</span></span>|<span data-ttu-id="1b621-132">Herhangi bir özel durum ile eşleşen ve adı özel durum nesnesine bağlar.</span><span class="sxs-lookup"><span data-stu-id="1b621-132">Matches any exception and binds the name to the exception object.</span></span> <span data-ttu-id="1b621-133">Eşdeğer \**:? System.Exception olarak \*\*\* tanımlayıcısı*</span><span class="sxs-lookup"><span data-stu-id="1b621-133">Equivalent to \**:? System.Exception as\*\*\*identifier*</span></span>|
|<span data-ttu-id="1b621-134">*tanımlayıcı* olduğunda *koşulu*</span><span class="sxs-lookup"><span data-stu-id="1b621-134">*identifier* when *condition*</span></span>|<span data-ttu-id="1b621-135">Koşul true ise bir özel durumla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="1b621-135">Matches any exception if the condition is true.</span></span>|

## <a name="examples"></a><span data-ttu-id="1b621-136">Örnekler</span><span class="sxs-lookup"><span data-stu-id="1b621-136">Examples</span></span>

<span data-ttu-id="1b621-137">Aşağıdaki kod örnekleri, çeşitli özel durum işleyicisi desenlerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b621-137">The following code examples illustrate the use of the various exception handler patterns.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

>[!NOTE]
<span data-ttu-id="1b621-138">`try...with` Yapıdır ayrı bir ifadeden `try...finally` ifade.</span><span class="sxs-lookup"><span data-stu-id="1b621-138">The `try...with` construct is a separate expression from the `try...finally` expression.</span></span> <span data-ttu-id="1b621-139">Bu nedenle, kodunuzu hem gerektiriyorsa bir `with` blok ve `finally` bloğu iki ifadelerini iç içe gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="1b621-139">Therefore, if your code requires both a `with` block and a `finally` block, you will have to nest the two expressions.</span></span>

>[!NOTE]
<span data-ttu-id="1b621-140">Kullanabileceğiniz `try...with` içinde zaman uyumsuz iş akışları ve özelleştirilmiş sürümü durumda diğer hesaplama ifadeleri, hangi `try...with` ifade kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b621-140">You can use `try...with` in asynchronous workflows and other computation expressions, in which case a customized version of the `try...with` expression is used.</span></span> <span data-ttu-id="1b621-141">Daha fazla bilgi için [zaman uyumsuz iş akışları](../asynchronous-workflows.md), ve [hesaplama ifadeleri](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1b621-141">For more information, see [Asynchronous Workflows](../asynchronous-workflows.md), and [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1b621-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b621-142">See also</span></span>

- [<span data-ttu-id="1b621-143">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="1b621-143">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="1b621-144">Özel Durum Türleri</span><span class="sxs-lookup"><span data-stu-id="1b621-144">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="1b621-145">Özel durumlar: `try...finally` ifadesi</span><span class="sxs-lookup"><span data-stu-id="1b621-145">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
