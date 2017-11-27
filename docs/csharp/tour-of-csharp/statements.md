---
title: C# ifadelerinin - C# dili turu
description: "Using deyimleri C# programının eylemler oluşturun"
keywords: ".NET, csharp, deyimleri, sözdizimi"
author: BillWagner
ms.author: wiwagn
ms.date: 11/06/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: 99ec2489daf89926da9b8c4e148965412826a8a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="statements"></a><span data-ttu-id="db1c5-104">Deyimler</span><span class="sxs-lookup"><span data-stu-id="db1c5-104">Statements</span></span>

<span data-ttu-id="db1c5-105">Bir program Eylemler Java'daki *deyimleri*.</span><span class="sxs-lookup"><span data-stu-id="db1c5-105">The actions of a program are expressed using *statements*.</span></span> <span data-ttu-id="db1c5-106">C# birkaç farklı türde bir dizi katıştırılmış ifadeler bakımından tanımlanmış ifadeleri destekler.</span><span class="sxs-lookup"><span data-stu-id="db1c5-106">C# supports several different kinds of statements, a number of which are defined in terms of embedded statements.</span></span>

<span data-ttu-id="db1c5-107">A *blok* bağlamlarda yazılması için birden çok deyime burada tek bir deyimde izin verir.</span><span class="sxs-lookup"><span data-stu-id="db1c5-107">A *block* permits multiple statements to be written in contexts where a single statement is allowed.</span></span> <span data-ttu-id="db1c5-108">Bir blok arasında sınırlayıcıları yazılmış deyimleri listesini oluşur `{` ve `}`.</span><span class="sxs-lookup"><span data-stu-id="db1c5-108">A block consists of a list of statements written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="db1c5-109">*Bildirim deyimleri* yerel değişkenleri ve sabitleri bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db1c5-109">*Declaration statements* are used to declare local variables and constants.</span></span>

<span data-ttu-id="db1c5-110">*İfade deyimleri* ifadeleri değerlendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db1c5-110">*Expression statements* are used to evaluate expressions.</span></span> <span data-ttu-id="db1c5-111">Nesne kullanan ayırmaları deyimleri kullanılabilir ifadeler içeren yöntemi çağrılarını `new` işleç, kullanarak atamaları `=` ve bileşik atama işleçleri, kullanarakartırmaveazaltmaişlemleri`++`ve `--` işleçler ve `await` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="db1c5-111">Expressions that can be used as statements include method invocations, object allocations using the `new` operator, assignments using `=` and the compound assignment operators, increment and decrement operations using the `++` and `--` operators and `await` expressions.</span></span>

<span data-ttu-id="db1c5-112">*Seçim deyimleri* değerine göre bazı ifade yürütme için olası bilgilerinin sayısı birini seçmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db1c5-112">*Selection statements* are used to select one of a number of possible statements for execution based on the value of some expression.</span></span> <span data-ttu-id="db1c5-113">Bu gruba `if` ve `switch` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="db1c5-113">In this group are the `if` and `switch` statements.</span></span>

<span data-ttu-id="db1c5-114">*Yineleme deyimleri* art arda katıştırılmış bir deyim yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db1c5-114">*Iteration statements* are used to execute repeatedly an embedded statement.</span></span> <span data-ttu-id="db1c5-115">Bu gruba `while`, `do`, `for`, ve `foreach` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="db1c5-115">In this group are the `while`, `do`, `for`, and `foreach` statements.</span></span>

<span data-ttu-id="db1c5-116">*Atlama deyimleri* denetim aktarmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db1c5-116">*Jump statements* are used to transfer control.</span></span> <span data-ttu-id="db1c5-117">Bu gruba `break`, `continue`, `goto`, `throw`, `return`, ve `yield` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="db1c5-117">In this group are the `break`, `continue`, `goto`, `throw`, `return`, and `yield` statements.</span></span>

<span data-ttu-id="db1c5-118">`try`... `catch` deyimi bir blok yürütülmesi sırasında oluşan özel durumları yakalamak için kullanılır ve `try`... `finally` deyimi her zaman yürütülür sonlandırma kodu veya bir özel durum oluştu olup olmadığını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db1c5-118">The `try`...`catch` statement is used to catch exceptions that occur during execution of a block, and the `try`...`finally` statement is used to specify finalization code that is always executed, whether an exception occurred or not.</span></span>

<span data-ttu-id="db1c5-119">`checked` Ve `unchecked` deyimleri integral türü aritmetik işlemler ve dönüşümleri taşma denetimi bağlamı denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db1c5-119">The `checked` and `unchecked` statements are used to control the overflow-checking context for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="db1c5-120">`lock` Deyimi, belirli bir nesne için karşılıklı dışlama kilidi elde etmek, bir deyim yürütmek ve kilidi serbest için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db1c5-120">The `lock` statement is used to obtain the mutual-exclusion lock for a given object, execute a statement, and then release the lock.</span></span>

<span data-ttu-id="db1c5-121">`using` Deyimi bu kaynağını atma bir kaynağı edinmek ve bir deyim yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db1c5-121">The `using` statement is used to obtain a resource, execute a statement, and then dispose of that resource.</span></span>

<span data-ttu-id="db1c5-122">Aşağıda, her biri için bir örnek sağlar ve kullanılabilir deyimleri türlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="db1c5-122">The following lists the kinds of statements that can be used, and provides an example for each.</span></span>

* <span data-ttu-id="db1c5-123">Yerel değişken bildirimi:</span><span class="sxs-lookup"><span data-stu-id="db1c5-123">Local variable declaration:</span></span>

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* <span data-ttu-id="db1c5-124">Yerel sabit bildirimi:</span><span class="sxs-lookup"><span data-stu-id="db1c5-124">Local constant declaration:</span></span>

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* <span data-ttu-id="db1c5-125">İfade deyimi:</span><span class="sxs-lookup"><span data-stu-id="db1c5-125">Expression statement:</span></span>

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* <span data-ttu-id="db1c5-126">`if`bildirimi:</span><span class="sxs-lookup"><span data-stu-id="db1c5-126">`if` statement:</span></span>

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* <span data-ttu-id="db1c5-127">`switch`bildirimi:</span><span class="sxs-lookup"><span data-stu-id="db1c5-127">`switch` statement:</span></span>

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* <span data-ttu-id="db1c5-128">`while`bildirimi:</span><span class="sxs-lookup"><span data-stu-id="db1c5-128">`while` statement:</span></span>

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* <span data-ttu-id="db1c5-129">`do`bildirimi:</span><span class="sxs-lookup"><span data-stu-id="db1c5-129">`do` statement:</span></span>

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* <span data-ttu-id="db1c5-130">`for`bildirimi:</span><span class="sxs-lookup"><span data-stu-id="db1c5-130">`for` statement:</span></span>

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* <span data-ttu-id="db1c5-131">`foreach`bildirimi:</span><span class="sxs-lookup"><span data-stu-id="db1c5-131">`foreach` statement:</span></span>

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* <span data-ttu-id="db1c5-132">`break`bildirimi:</span><span class="sxs-lookup"><span data-stu-id="db1c5-132">`break` statement:</span></span>

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* <span data-ttu-id="db1c5-133">`continue`bildirimi:</span><span class="sxs-lookup"><span data-stu-id="db1c5-133">`continue` statement:</span></span>

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* <span data-ttu-id="db1c5-134">`goto`bildirimi:</span><span class="sxs-lookup"><span data-stu-id="db1c5-134">`goto` statement:</span></span>

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* <span data-ttu-id="db1c5-135">`return`bildirimi:</span><span class="sxs-lookup"><span data-stu-id="db1c5-135">`return` statement:</span></span>

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* <span data-ttu-id="db1c5-136">`yield`bildirimi:</span><span class="sxs-lookup"><span data-stu-id="db1c5-136">`yield` statement:</span></span>

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* <span data-ttu-id="db1c5-137">`throw`deyimleri ve `try` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="db1c5-137">`throw` statements and `try` statements:</span></span>

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* <span data-ttu-id="db1c5-138">`checked`ve `unchecked` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="db1c5-138">`checked` and `unchecked` statements:</span></span>

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* <span data-ttu-id="db1c5-139">`lock`bildirimi:</span><span class="sxs-lookup"><span data-stu-id="db1c5-139">`lock` statement:</span></span>

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* <span data-ttu-id="db1c5-140">`using`bildirimi:</span><span class="sxs-lookup"><span data-stu-id="db1c5-140">`using` statement:</span></span>

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
<span data-ttu-id="db1c5-141">[Önceki](expressions.md)
[sonraki](classes-and-objects.md)</span><span class="sxs-lookup"><span data-stu-id="db1c5-141">[Previous](expressions.md)
[Next](classes-and-objects.md)</span></span>
