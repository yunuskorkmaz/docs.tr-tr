---
title: 'Özel Durumlar: try...with İfadesi (F#)'
description: "Özel durum işleme için F # 'ile... deneyin' ifadesi kullanmayı öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 5e6e16d5fba88841d567512ba7e08a2e8d17bdba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565294"
---
# <a name="exceptions-the-trywith-expression"></a><span data-ttu-id="38d55-103">Özel Durumlar: try...with İfadesi</span><span class="sxs-lookup"><span data-stu-id="38d55-103">Exceptions: The try...with Expression</span></span>

<span data-ttu-id="38d55-104">Bu konuda açıklanmaktadır `try...with` ifade, özel durum işleme F # dili için kullanılan ifade.</span><span class="sxs-lookup"><span data-stu-id="38d55-104">This topic describes the `try...with` expression, the expression that is used for exception handling in the F# language.</span></span>


## <a name="syntax"></a><span data-ttu-id="38d55-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38d55-105">Syntax</span></span>

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a><span data-ttu-id="38d55-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38d55-106">Remarks</span></span>
<span data-ttu-id="38d55-107">`try...with` İfade F # özel durumları işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38d55-107">The `try...with` expression is used to handle exceptions in F#.</span></span> <span data-ttu-id="38d55-108">Aşağıdakine benzer `try...catch` C# deyimi.</span><span class="sxs-lookup"><span data-stu-id="38d55-108">It is similar to the `try...catch` statement in C#.</span></span> <span data-ttu-id="38d55-109">Önceki sözdiziminde, kodda *İfade1* bir özel durum oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="38d55-109">In the preceding syntax, the code in *expression1* might generate an exception.</span></span> <span data-ttu-id="38d55-110">`try...with` İfade bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="38d55-110">The `try...with` expression returns a value.</span></span> <span data-ttu-id="38d55-111">Hiçbir özel durum, tüm ifadenin değerini döndürür. *İfade1*.</span><span class="sxs-lookup"><span data-stu-id="38d55-111">If no exception is thrown, the whole expression returns the value of *expression1*.</span></span> <span data-ttu-id="38d55-112">Bir özel durum oluşur, her *düzeni* özel ve karşılık gelen ilk eşleştirme deseni için sırayla karşılaştırılır *ifade*, olarak bilinen *özel durum işleyici*, o şubedeki yürütülür ve genel ifade bu özel durum işleyici ifadesinin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="38d55-112">If an exception is thrown, each *pattern* is compared in turn with the exception, and for the first matching pattern, the corresponding *expression*, known as the *exception handler*, for that branch is executed, and the overall expression returns the value of the expression in that exception handler.</span></span> <span data-ttu-id="38d55-113">Hiçbir desen eşleşirse, eşleşen bir işleyici bulunana kadar özel durum çağrı yığınına yayar.</span><span class="sxs-lookup"><span data-stu-id="38d55-113">If no pattern matches, the exception propagates up the call stack until a matching handler is found.</span></span> <span data-ttu-id="38d55-114">Özel durum işleyicileri her ifadesinden döndürdüğü değer türü ifadesinde döndürülen türüyle eşleşmelidir `try` bloğu.</span><span class="sxs-lookup"><span data-stu-id="38d55-114">The types of the values returned from each expression in the exception handlers must match the type returned from the expression in the `try` block.</span></span>

<span data-ttu-id="38d55-115">Sık sık hatayla de oluştuğunu olgu her özel durum işleyici ifadelerinde öğesinden döndürülen geçerli bir değer olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="38d55-115">Frequently, the fact that an error occurred also means that there is no valid value that can be returned from the expressions in each exception handler.</span></span> <span data-ttu-id="38d55-116">Sık kullanılan bir desen bir seçenek türü ifadesinin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="38d55-116">A frequent pattern is to have the type of the expression be an option type.</span></span> <span data-ttu-id="38d55-117">Aşağıdaki kod örneği, bu deseni gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="38d55-117">The following code example illustrates this pattern.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

<span data-ttu-id="38d55-118">Özel durumlar, .NET özel durumları veya F # özel durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="38d55-118">Exceptions can be .NET exceptions, or they can be F# exceptions.</span></span> <span data-ttu-id="38d55-119">Kullanarak F # özel durumlar tanımlayabilirsiniz `exception` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="38d55-119">You can define F# exceptions by using the `exception` keyword.</span></span>

<span data-ttu-id="38d55-120">Özel durum türü ve diğer koşulları filtrelemek için desenleri çeşitli kullanabilirsiniz; seçenekleri aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="38d55-120">You can use a variety of patterns to filter on the exception type and other conditions; the options are summarized in the following table.</span></span>


|<span data-ttu-id="38d55-121">Desen</span><span class="sxs-lookup"><span data-stu-id="38d55-121">Pattern</span></span>|<span data-ttu-id="38d55-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38d55-122">Description</span></span>|
|-------|-----------|
|<span data-ttu-id="38d55-123">:?</span><span class="sxs-lookup"><span data-stu-id="38d55-123">:?</span></span> <span data-ttu-id="38d55-124">*özel durum türü*</span><span class="sxs-lookup"><span data-stu-id="38d55-124">*exception-type*</span></span>|<span data-ttu-id="38d55-125">Belirtilen .NET özel durum türü eşleşir.</span><span class="sxs-lookup"><span data-stu-id="38d55-125">Matches the specified .NET exception type.</span></span>|
|<span data-ttu-id="38d55-126">:?</span><span class="sxs-lookup"><span data-stu-id="38d55-126">:?</span></span> <span data-ttu-id="38d55-127">*özel durum türü* olarak *tanımlayıcısı*</span><span class="sxs-lookup"><span data-stu-id="38d55-127">*exception-type* as *identifier*</span></span>|<span data-ttu-id="38d55-128">Belirtilen .NET özel durum türü eşleşir, ancak özel bir adlandırılmış değeri verir.</span><span class="sxs-lookup"><span data-stu-id="38d55-128">Matches the specified .NET exception type, but gives the exception a named value.</span></span>|
|<span data-ttu-id="38d55-129">*özel durum adı*(*bağımsız değişkenleri*)</span><span class="sxs-lookup"><span data-stu-id="38d55-129">*exception-name*(*arguments*)</span></span>|<span data-ttu-id="38d55-130">F # özel durum türü ile eşleşen ve bağımsız değişkenler bağlar.</span><span class="sxs-lookup"><span data-stu-id="38d55-130">Matches an F# exception type and binds the arguments.</span></span>|
|<span data-ttu-id="38d55-131">*Tanımlayıcı*</span><span class="sxs-lookup"><span data-stu-id="38d55-131">*identifier*</span></span>|<span data-ttu-id="38d55-132">Herhangi bir özel durum ile eşleşen ve özel durum nesnesi adı bağlar.</span><span class="sxs-lookup"><span data-stu-id="38d55-132">Matches any exception and binds the name to the exception object.</span></span> <span data-ttu-id="38d55-133">Eşdeğer **:? System.Exception olarak *** tanımlayıcısı*</span><span class="sxs-lookup"><span data-stu-id="38d55-133">Equivalent to **:? System.Exception as***identifier*</span></span>|
|<span data-ttu-id="38d55-134">*tanımlayıcı* zaman *koşulu*</span><span class="sxs-lookup"><span data-stu-id="38d55-134">*identifier* when *condition*</span></span>|<span data-ttu-id="38d55-135">Koşul doğru ise, bir özel durumla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="38d55-135">Matches any exception if the condition is true.</span></span>|

## <a name="examples"></a><span data-ttu-id="38d55-136">Örnekler</span><span class="sxs-lookup"><span data-stu-id="38d55-136">Examples</span></span>
<span data-ttu-id="38d55-137">Aşağıdaki kod örneğinde çeşitli özel durum işleyici desenlerini kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="38d55-137">The following code examples illustrate the use of the various exception handler patterns.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]
    
>[!NOTE] 
<span data-ttu-id="38d55-138">`try...with` Yapıdır ayrı ifadesinden `try...finally` ifade.</span><span class="sxs-lookup"><span data-stu-id="38d55-138">The `try...with` construct is a separate expression from the `try...finally` expression.</span></span> <span data-ttu-id="38d55-139">Bu nedenle, kodunuzun her ikisi de gerektiriyorsa bir `with` bloğu ve `finally` bloğu, iki ifadeleri iç içe gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="38d55-139">Therefore, if your code requires both a `with` block and a `finally` block, you will have to nest the two expressions.</span></span>

>[!NOTE] 
<span data-ttu-id="38d55-140">Kullanabileceğiniz `try...with` içinde zaman uyumsuz iş akışları ve özelleştirilmiş bir sürümünü durumda diğer hesaplama ifadeleri, hangi `try...with` ifade kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38d55-140">You can use `try...with` in asynchronous workflows and other computation expressions, in which case a customized version of the `try...with` expression is used.</span></span> <span data-ttu-id="38d55-141">Daha fazla bilgi için bkz: [zaman uyumsuz iş akışları](../asynchronous-workflows.md), ve [hesaplama ifadeleri](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="38d55-141">For more information, see [Asynchronous Workflows](../asynchronous-workflows.md), and [Computation Expressions](../computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="38d55-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38d55-142">See Also</span></span>
[<span data-ttu-id="38d55-143">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="38d55-143">Exception Handling</span></span>](index.md)

[<span data-ttu-id="38d55-144">Özel Durum Türleri</span><span class="sxs-lookup"><span data-stu-id="38d55-144">Exception Types</span></span>](exception-types.md)

[<span data-ttu-id="38d55-145">Özel durumlar: `try...finally` ifade</span><span class="sxs-lookup"><span data-stu-id="38d55-145">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
