---
title: C# Deyimleri - C# dilinde bir tur
description: İfadeleri kullanarak bir C# programının eylemlerini oluşturursunuz
ms.date: 02/27/2020
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: ced13b1bfd17977acb98bf33c0a477161cf08a93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159110"
---
# <a name="statements"></a><span data-ttu-id="0b76b-103">Deyimler</span><span class="sxs-lookup"><span data-stu-id="0b76b-103">Statements</span></span>

<span data-ttu-id="0b76b-104">Bir programın eylemleri *ifadeleri*kullanılarak ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="0b76b-104">The actions of a program are expressed using *statements*.</span></span> <span data-ttu-id="0b76b-105">C#, bir dizi katıştırılmış deyim ler açısından tanımlanan birkaç farklı ifade yi destekler.</span><span class="sxs-lookup"><span data-stu-id="0b76b-105">C# supports several different kinds of statements, a number of which are defined in terms of embedded statements.</span></span>

<span data-ttu-id="0b76b-106">*Blok,* tek bir deyimin izin verildiği bağlamlarda birden çok deyimin yazılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="0b76b-106">A *block* permits multiple statements to be written in contexts where a single statement is allowed.</span></span> <span data-ttu-id="0b76b-107">Blok, sınır layıcılar `{` ve `}`.</span><span class="sxs-lookup"><span data-stu-id="0b76b-107">A block consists of a list of statements written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="0b76b-108">*Bildirim deyimleri* yerel değişkenleri ve sabitleri bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b76b-108">*Declaration statements* are used to declare local variables and constants.</span></span>

<span data-ttu-id="0b76b-109">*İfade ifadeleri* ifadeleri değerlendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b76b-109">*Expression statements* are used to evaluate expressions.</span></span> <span data-ttu-id="0b76b-110">Deyim olarak kullanılabilecek ifadeler yöntem çağrılarını, `new` işleci kullanan nesne ayırmaları, `=` kullanılan atamaları ve bileşik atama işleçlerini, `++` ve `--` işleçleri ve `await` ifadeleri kullanarak artırma ve decrement işlemlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0b76b-110">Expressions that can be used as statements include method invocations, object allocations using the `new` operator, assignments using `=` and the compound assignment operators, increment and decrement operations using the `++` and `--` operators and `await` expressions.</span></span>

<span data-ttu-id="0b76b-111">*Seçim deyimleri,* bazı ifadelerin değerine bağlı olarak yürütme için olası ifadelerden birini seçmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b76b-111">*Selection statements* are used to select one of a number of possible statements for execution based on the value of some expression.</span></span> <span data-ttu-id="0b76b-112">Bu grup `if` ve `switch` ifadeler içerir.</span><span class="sxs-lookup"><span data-stu-id="0b76b-112">This group contains the `if` and `switch` statements.</span></span>

<span data-ttu-id="0b76b-113">*Yineleme deyimleri,* katıştırılmış bir deyimi tekrar tekrar yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b76b-113">*Iteration statements* are used to execute repeatedly an embedded statement.</span></span> <span data-ttu-id="0b76b-114">Bu grup `while`, `do` `for`, `foreach` ve ifadeler içerir.</span><span class="sxs-lookup"><span data-stu-id="0b76b-114">This group contains the `while`, `do`, `for`, and `foreach` statements.</span></span>

<span data-ttu-id="0b76b-115">*Atlama deyimleri* denetimi aktarmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b76b-115">*Jump statements* are used to transfer control.</span></span> <span data-ttu-id="0b76b-116">Bu grup `break`, `continue` `goto`, `throw` `return`, `yield` , , ve ifadeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0b76b-116">This group contains the `break`, `continue`, `goto`, `throw`, `return`, and `yield` statements.</span></span>

<span data-ttu-id="0b76b-117">Bu `try`... `catch` deyimi bir blok yürütülmesi sırasında meydana gelen özel durumları `try`yakalamak için kullanılır ve ... `finally` deyimi, bir özel durum oluştu veya değil, her zaman yürütülen sonlandırma kodunu belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b76b-117">The `try`...`catch` statement is used to catch exceptions that occur during execution of a block, and the `try`...`finally` statement is used to specify finalization code that is always executed, whether an exception occurred or not.</span></span>

<span data-ttu-id="0b76b-118">Ve `checked` `unchecked` deyimler, integral türü aritmetik işlemler ve dönüşümler için taşma denetimi bağlamını denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b76b-118">The `checked` and `unchecked` statements are used to control the overflow-checking context for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="0b76b-119">İfade, `lock` belirli bir nesne için karşılıklı dışlama kilidi elde etmek, bir deyimi yürütmek ve kilidi serbest bırakmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b76b-119">The `lock` statement is used to obtain the mutual-exclusion lock for a given object, execute a statement, and then release the lock.</span></span>

<span data-ttu-id="0b76b-120">Deyim, `using` bir kaynak elde etmek, bir deyim yürütmek ve sonra bu kaynağı elden çıkarmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b76b-120">The `using` statement is used to obtain a resource, execute a statement, and then dispose of that resource.</span></span>

<span data-ttu-id="0b76b-121">Aşağıda kullanılabilecek deyim türlerini listeler ve her biri için bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b76b-121">The following lists the kinds of statements that can be used, and provides an example for each.</span></span>

* <span data-ttu-id="0b76b-122">Yerel değişken bildirimi:</span><span class="sxs-lookup"><span data-stu-id="0b76b-122">Local variable declaration:</span></span>

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* <span data-ttu-id="0b76b-123">Yerel sabit bildirim:</span><span class="sxs-lookup"><span data-stu-id="0b76b-123">Local constant declaration:</span></span>

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* <span data-ttu-id="0b76b-124">İfade deyimi:</span><span class="sxs-lookup"><span data-stu-id="0b76b-124">Expression statement:</span></span>

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* <span data-ttu-id="0b76b-125">`if`Deyim:</span><span class="sxs-lookup"><span data-stu-id="0b76b-125">`if` statement:</span></span>

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* <span data-ttu-id="0b76b-126">`switch`Deyim:</span><span class="sxs-lookup"><span data-stu-id="0b76b-126">`switch` statement:</span></span>

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* <span data-ttu-id="0b76b-127">`while`Deyim:</span><span class="sxs-lookup"><span data-stu-id="0b76b-127">`while` statement:</span></span>

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* <span data-ttu-id="0b76b-128">`do`Deyim:</span><span class="sxs-lookup"><span data-stu-id="0b76b-128">`do` statement:</span></span>

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* <span data-ttu-id="0b76b-129">`for`Deyim:</span><span class="sxs-lookup"><span data-stu-id="0b76b-129">`for` statement:</span></span>

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* <span data-ttu-id="0b76b-130">`foreach`Deyim:</span><span class="sxs-lookup"><span data-stu-id="0b76b-130">`foreach` statement:</span></span>

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* <span data-ttu-id="0b76b-131">`break`Deyim:</span><span class="sxs-lookup"><span data-stu-id="0b76b-131">`break` statement:</span></span>

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* <span data-ttu-id="0b76b-132">`continue`Deyim:</span><span class="sxs-lookup"><span data-stu-id="0b76b-132">`continue` statement:</span></span>

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* <span data-ttu-id="0b76b-133">`goto`Deyim:</span><span class="sxs-lookup"><span data-stu-id="0b76b-133">`goto` statement:</span></span>

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* <span data-ttu-id="0b76b-134">`return`Deyim:</span><span class="sxs-lookup"><span data-stu-id="0b76b-134">`return` statement:</span></span>

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* <span data-ttu-id="0b76b-135">`yield`Deyim:</span><span class="sxs-lookup"><span data-stu-id="0b76b-135">`yield` statement:</span></span>

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* <span data-ttu-id="0b76b-136">`throw`ifadeler `try` ve ifadeler:</span><span class="sxs-lookup"><span data-stu-id="0b76b-136">`throw` statements and `try` statements:</span></span>

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* <span data-ttu-id="0b76b-137">`checked`ve `unchecked` ifadeler:</span><span class="sxs-lookup"><span data-stu-id="0b76b-137">`checked` and `unchecked` statements:</span></span>

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* <span data-ttu-id="0b76b-138">`lock`Deyim:</span><span class="sxs-lookup"><span data-stu-id="0b76b-138">`lock` statement:</span></span>

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* <span data-ttu-id="0b76b-139">`using`Deyim:</span><span class="sxs-lookup"><span data-stu-id="0b76b-139">`using` statement:</span></span>

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
><span data-ttu-id="0b76b-140">[Önceki](expressions.md)
>[Sonraki](classes-and-objects.md)</span><span class="sxs-lookup"><span data-stu-id="0b76b-140">[Previous](expressions.md)
[Next](classes-and-objects.md)</span></span>
