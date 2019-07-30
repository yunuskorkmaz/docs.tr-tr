---
title: 'Özel durumlar: try...with İfadesi'
description: F# ' TRY... ' yı kullanmayı öğrenin ' i ' de, özel durum işleme için ifadesi.
ms.date: 05/16/2016
ms.openlocfilehash: e4d615086a93e26b76cca460e797659ca13792b5
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630251"
---
# <a name="exceptions-the-trywith-expression"></a><span data-ttu-id="03f9a-103">Özel durumlar: try...with İfadesi</span><span class="sxs-lookup"><span data-stu-id="03f9a-103">Exceptions: The try...with Expression</span></span>

<span data-ttu-id="03f9a-104">Bu konuda, `try...with` F# dildeki özel durum işleme için kullanılan ifade olan ifade açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="03f9a-104">This topic describes the `try...with` expression, the expression that is used for exception handling in the F# language.</span></span>

## <a name="syntax"></a><span data-ttu-id="03f9a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="03f9a-105">Syntax</span></span>

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a><span data-ttu-id="03f9a-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03f9a-106">Remarks</span></span>

<span data-ttu-id="03f9a-107">İfade `try...with` , içindeki F#özel durumları işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="03f9a-107">The `try...with` expression is used to handle exceptions in F#.</span></span> <span data-ttu-id="03f9a-108">İçindeki `try...catch` C#ifadeye benzerdir.</span><span class="sxs-lookup"><span data-stu-id="03f9a-108">It is similar to the `try...catch` statement in C#.</span></span> <span data-ttu-id="03f9a-109">Önceki sözdiziminde, *İfade1* içindeki kod bir özel durum oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="03f9a-109">In the preceding syntax, the code in *expression1* might generate an exception.</span></span> <span data-ttu-id="03f9a-110">`try...with` İfade bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="03f9a-110">The `try...with` expression returns a value.</span></span> <span data-ttu-id="03f9a-111">Özel durum oluşturulursa, tüm ifade *İfade1*değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="03f9a-111">If no exception is thrown, the whole expression returns the value of *expression1*.</span></span> <span data-ttu-id="03f9a-112">Bir özel durum oluşursa, her bir *Düzen* özel durumla karşılaştırılır ve ilk eşleşen düzen için, *özel durum işleyicisi*olarak bilinen karşılık gelen *ifade*, bu dal için yürütülür ve genel ifade Bu özel durum işleyicisindeki ifadenin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="03f9a-112">If an exception is thrown, each *pattern* is compared in turn with the exception, and for the first matching pattern, the corresponding *expression*, known as the *exception handler*, for that branch is executed, and the overall expression returns the value of the expression in that exception handler.</span></span> <span data-ttu-id="03f9a-113">Herhangi bir model eşleşmesi yoksa, özel durum, eşleşen bir işleyici bulunana kadar çağrı yığınını yayar.</span><span class="sxs-lookup"><span data-stu-id="03f9a-113">If no pattern matches, the exception propagates up the call stack until a matching handler is found.</span></span> <span data-ttu-id="03f9a-114">Özel durum işleyicilerindeki her bir ifadeden döndürülen değerlerin türleri, `try` bloktaki ifadeden döndürülen türle aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="03f9a-114">The types of the values returned from each expression in the exception handlers must match the type returned from the expression in the `try` block.</span></span>

<span data-ttu-id="03f9a-115">Genellikle bir hata oluştuğu için, her bir özel durum işleyicisindeki ifadelerden döndürülebilecek geçerli bir değer olmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="03f9a-115">Frequently, the fact that an error occurred also means that there is no valid value that can be returned from the expressions in each exception handler.</span></span> <span data-ttu-id="03f9a-116">Sık kullanılan bir düzende, ifadenin türü bir seçenek türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="03f9a-116">A frequent pattern is to have the type of the expression be an option type.</span></span> <span data-ttu-id="03f9a-117">Aşağıdaki kod örneğinde bu desenler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="03f9a-117">The following code example illustrates this pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

<span data-ttu-id="03f9a-118">Özel durumlar .NET özel durumları olabilir veya F# özel durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="03f9a-118">Exceptions can be .NET exceptions, or they can be F# exceptions.</span></span> <span data-ttu-id="03f9a-119">`exception` Anahtar sözcüğünü kullanarak F# özel durumlar tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03f9a-119">You can define F# exceptions by using the `exception` keyword.</span></span>

<span data-ttu-id="03f9a-120">Özel durum türü ve diğer koşulları filtrelemek için çeşitli desenler kullanabilirsiniz; Seçenekler aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="03f9a-120">You can use a variety of patterns to filter on the exception type and other conditions; the options are summarized in the following table.</span></span>

|<span data-ttu-id="03f9a-121">Desen</span><span class="sxs-lookup"><span data-stu-id="03f9a-121">Pattern</span></span>|<span data-ttu-id="03f9a-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03f9a-122">Description</span></span>|
|-------|-----------|
|<span data-ttu-id="03f9a-123">:?</span><span class="sxs-lookup"><span data-stu-id="03f9a-123">:?</span></span> <span data-ttu-id="03f9a-124">*özel durum türü*</span><span class="sxs-lookup"><span data-stu-id="03f9a-124">*exception-type*</span></span>|<span data-ttu-id="03f9a-125">Belirtilen .NET özel durum türüyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="03f9a-125">Matches the specified .NET exception type.</span></span>|
|<span data-ttu-id="03f9a-126">:?</span><span class="sxs-lookup"><span data-stu-id="03f9a-126">:?</span></span> <span data-ttu-id="03f9a-127">*özel durum-* *tanımlayıcı* olarak tür</span><span class="sxs-lookup"><span data-stu-id="03f9a-127">*exception-type* as *identifier*</span></span>|<span data-ttu-id="03f9a-128">Belirtilen .NET özel durum türüyle eşleşir, ancak özel duruma adlandırılmış bir değer verir.</span><span class="sxs-lookup"><span data-stu-id="03f9a-128">Matches the specified .NET exception type, but gives the exception a named value.</span></span>|
|<span data-ttu-id="03f9a-129">*özel durum-adı* (*bağımsız değişkenler*)</span><span class="sxs-lookup"><span data-stu-id="03f9a-129">*exception-name*(*arguments*)</span></span>|<span data-ttu-id="03f9a-130">Bir F# özel durum türüyle eşleşir ve bağımsız değişkenleri bağlar.</span><span class="sxs-lookup"><span data-stu-id="03f9a-130">Matches an F# exception type and binds the arguments.</span></span>|
|<span data-ttu-id="03f9a-131">*Tanımlayıcısını*</span><span class="sxs-lookup"><span data-stu-id="03f9a-131">*identifier*</span></span>|<span data-ttu-id="03f9a-132">Herhangi bir özel durumla eşleşir ve adı özel durum nesnesine bağlar.</span><span class="sxs-lookup"><span data-stu-id="03f9a-132">Matches any exception and binds the name to the exception object.</span></span> <span data-ttu-id="03f9a-133">**Eşdeğer:? System. Exception as**_Identifier_</span><span class="sxs-lookup"><span data-stu-id="03f9a-133">Equivalent to **:? System.Exception as**_identifier_</span></span>|
|<span data-ttu-id="03f9a-134">*koşul* olduğunda *tanımlayıcı*</span><span class="sxs-lookup"><span data-stu-id="03f9a-134">*identifier* when *condition*</span></span>|<span data-ttu-id="03f9a-135">Koşul doğru ise herhangi bir özel durumla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="03f9a-135">Matches any exception if the condition is true.</span></span>|

## <a name="examples"></a><span data-ttu-id="03f9a-136">Örnekler</span><span class="sxs-lookup"><span data-stu-id="03f9a-136">Examples</span></span>

<span data-ttu-id="03f9a-137">Aşağıdaki kod örnekleri çeşitli özel durum işleyici desenlerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="03f9a-137">The following code examples illustrate the use of the various exception handler patterns.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

> [!NOTE]
> <span data-ttu-id="03f9a-138">Yapı, `try...finally` ifadeden ayrı bir ifadedir. `try...with`</span><span class="sxs-lookup"><span data-stu-id="03f9a-138">The `try...with` construct is a separate expression from the `try...finally` expression.</span></span> <span data-ttu-id="03f9a-139">Bu nedenle, kodunuz hem `with` blok `finally` hem de blok gerektiriyorsa, iki ifadeyi iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03f9a-139">Therefore, if your code requires both a `with` block and a `finally` block, you will have to nest the two expressions.</span></span>

> [!NOTE]
> <span data-ttu-id="03f9a-140">Zaman uyumsuz iş `try...with` akışları ve diğer hesaplama ifadelerinde kullanabilirsiniz, bu durumda `try...with` ifadenin özelleştirilmiş bir sürümü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="03f9a-140">You can use `try...with` in asynchronous workflows and other computation expressions, in which case a customized version of the `try...with` expression is used.</span></span> <span data-ttu-id="03f9a-141">Daha fazla bilgi için bkz. [zaman uyumsuz Iş akışları](../asynchronous-workflows.md)ve [Hesaplama ifadeleri](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="03f9a-141">For more information, see [Asynchronous Workflows](../asynchronous-workflows.md), and [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="03f9a-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03f9a-142">See also</span></span>

- [<span data-ttu-id="03f9a-143">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="03f9a-143">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="03f9a-144">Özel Durum Türleri</span><span class="sxs-lookup"><span data-stu-id="03f9a-144">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="03f9a-145">Özel Durumlar: `try...finally` İfade</span><span class="sxs-lookup"><span data-stu-id="03f9a-145">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
