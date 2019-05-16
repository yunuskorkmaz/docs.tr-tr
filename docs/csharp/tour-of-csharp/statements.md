---
title: C#Deyimleri - Turu C# dil
description: Eylemler, oluşturduğunuz bir C# deyimleri kullanarak program
ms.date: 11/06/2016
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: 26b151bc116dde9120757f954bdcf3aee041c5f5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634540"
---
# <a name="statements"></a><span data-ttu-id="13f52-103">Deyimler</span><span class="sxs-lookup"><span data-stu-id="13f52-103">Statements</span></span>

<span data-ttu-id="13f52-104">Bir programın eylemleri kullanılarak ifade edilir *deyimleri*.</span><span class="sxs-lookup"><span data-stu-id="13f52-104">The actions of a program are expressed using *statements*.</span></span> <span data-ttu-id="13f52-105">C# ifadeleri açısından katıştırılmış deyimi bir dizi tanımlanmış birkaç farklı türde destekler.</span><span class="sxs-lookup"><span data-stu-id="13f52-105">C# supports several different kinds of statements, a number of which are defined in terms of embedded statements.</span></span>

<span data-ttu-id="13f52-106">A *blok* bağlamlarda yazılacak birden çok deyime burada tek bir deyimde izin verir.</span><span class="sxs-lookup"><span data-stu-id="13f52-106">A *block* permits multiple statements to be written in contexts where a single statement is allowed.</span></span> <span data-ttu-id="13f52-107">Sınırlayıcılar yazılan deyimlerin listesini bir blok oluşan `{` ve `}`.</span><span class="sxs-lookup"><span data-stu-id="13f52-107">A block consists of a list of statements written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="13f52-108">*Bildirim deyimleri* yerel değişkenleri ve sabitleri bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="13f52-108">*Declaration statements* are used to declare local variables and constants.</span></span>

<span data-ttu-id="13f52-109">*İfade deyimleri* ifadeler değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="13f52-109">*Expression statements* are used to evaluate expressions.</span></span> <span data-ttu-id="13f52-110">Deyimleri kullanılabilir ifadeler, yöntem çağrılarını içeren nesne ayırmaları kullanarak `new` işleç, atamaları kullanarak `=` ve bileşik atama işleçleri, artırma ve azaltma işlemlerini kullanarak`++`ve `--` işleçler ve `await` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="13f52-110">Expressions that can be used as statements include method invocations, object allocations using the `new` operator, assignments using `=` and the compound assignment operators, increment and decrement operations using the `++` and `--` operators and `await` expressions.</span></span>

<span data-ttu-id="13f52-111">*Seçim deyimleri* olası deyimleri yürütme bazı ifadesinin değerine göre bir dizi birini seçmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="13f52-111">*Selection statements* are used to select one of a number of possible statements for execution based on the value of some expression.</span></span> <span data-ttu-id="13f52-112">Bu gruba `if` ve `switch` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="13f52-112">In this group are the `if` and `switch` statements.</span></span>

<span data-ttu-id="13f52-113">*Yineleme deyimleri* sürekli bir katıştırılmış deyimi yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="13f52-113">*Iteration statements* are used to execute repeatedly an embedded statement.</span></span> <span data-ttu-id="13f52-114">Bu gruba `while`, `do`, `for`, ve `foreach` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="13f52-114">In this group are the `while`, `do`, `for`, and `foreach` statements.</span></span>

<span data-ttu-id="13f52-115">*Atlama deyimleri* denetim aktarmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="13f52-115">*Jump statements* are used to transfer control.</span></span> <span data-ttu-id="13f52-116">Bu gruba `break`, `continue`, `goto`, `throw`, `return`, ve `yield` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="13f52-116">In this group are the `break`, `continue`, `goto`, `throw`, `return`, and `yield` statements.</span></span>

<span data-ttu-id="13f52-117">`try`... `catch` deyimi, bir blok yürütülmesi sırasında oluşan özel durumları yakalamak için kullanılır ve `try`... `finally` deyimi veya bir özel durum oluştu olup olmadığını her zaman yürütülür, sonlandırma kodu belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="13f52-117">The `try`...`catch` statement is used to catch exceptions that occur during execution of a block, and the `try`...`finally` statement is used to specify finalization code that is always executed, whether an exception occurred or not.</span></span>

<span data-ttu-id="13f52-118">`checked` Ve `unchecked` ifadeler Tamsayı türünde aritmetik işlemler ve dönüştürmeler için taşma denetimi bağlamını denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="13f52-118">The `checked` and `unchecked` statements are used to control the overflow-checking context for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="13f52-119">`lock` Deyimi belirli bir nesne için karşılıklı dışlama kilidini almak, bir deyimi yürütün ve sonra kilidi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="13f52-119">The `lock` statement is used to obtain the mutual-exclusion lock for a given object, execute a statement, and then release the lock.</span></span>

<span data-ttu-id="13f52-120">`using` Deyimi bir kaynağı almak, bir deyimi yürütün ve sonra o kaynağını atma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="13f52-120">The `using` statement is used to obtain a resource, execute a statement, and then dispose of that resource.</span></span>

<span data-ttu-id="13f52-121">Aşağıda, her biri için bir örnek sağlar ve kullanılabilir deyimleri türlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="13f52-121">The following lists the kinds of statements that can be used, and provides an example for each.</span></span>

* <span data-ttu-id="13f52-122">Yerel değişken bildirimi:</span><span class="sxs-lookup"><span data-stu-id="13f52-122">Local variable declaration:</span></span>

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* <span data-ttu-id="13f52-123">Yerel sabit bildiriminde:</span><span class="sxs-lookup"><span data-stu-id="13f52-123">Local constant declaration:</span></span>

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* <span data-ttu-id="13f52-124">İfade deyimi:</span><span class="sxs-lookup"><span data-stu-id="13f52-124">Expression statement:</span></span>

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* <span data-ttu-id="13f52-125">`if` deyimi:</span><span class="sxs-lookup"><span data-stu-id="13f52-125">`if` statement:</span></span>

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* <span data-ttu-id="13f52-126">`switch` deyimi:</span><span class="sxs-lookup"><span data-stu-id="13f52-126">`switch` statement:</span></span>

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* <span data-ttu-id="13f52-127">`while` deyimi:</span><span class="sxs-lookup"><span data-stu-id="13f52-127">`while` statement:</span></span>

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* <span data-ttu-id="13f52-128">`do` deyimi:</span><span class="sxs-lookup"><span data-stu-id="13f52-128">`do` statement:</span></span>

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* <span data-ttu-id="13f52-129">`for` deyimi:</span><span class="sxs-lookup"><span data-stu-id="13f52-129">`for` statement:</span></span>

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* <span data-ttu-id="13f52-130">`foreach` deyimi:</span><span class="sxs-lookup"><span data-stu-id="13f52-130">`foreach` statement:</span></span>

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* <span data-ttu-id="13f52-131">`break` deyimi:</span><span class="sxs-lookup"><span data-stu-id="13f52-131">`break` statement:</span></span>

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* <span data-ttu-id="13f52-132">`continue` deyimi:</span><span class="sxs-lookup"><span data-stu-id="13f52-132">`continue` statement:</span></span>

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* <span data-ttu-id="13f52-133">`goto` deyimi:</span><span class="sxs-lookup"><span data-stu-id="13f52-133">`goto` statement:</span></span>

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* <span data-ttu-id="13f52-134">`return` deyimi:</span><span class="sxs-lookup"><span data-stu-id="13f52-134">`return` statement:</span></span>

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* <span data-ttu-id="13f52-135">`yield` deyimi:</span><span class="sxs-lookup"><span data-stu-id="13f52-135">`yield` statement:</span></span>

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* <span data-ttu-id="13f52-136">`throw` deyimleri ve `try` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="13f52-136">`throw` statements and `try` statements:</span></span>

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* <span data-ttu-id="13f52-137">`checked` ve `unchecked` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="13f52-137">`checked` and `unchecked` statements:</span></span>

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* <span data-ttu-id="13f52-138">`lock` deyimi:</span><span class="sxs-lookup"><span data-stu-id="13f52-138">`lock` statement:</span></span>

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* <span data-ttu-id="13f52-139">`using` deyimi:</span><span class="sxs-lookup"><span data-stu-id="13f52-139">`using` statement:</span></span>

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
><span data-ttu-id="13f52-140">[Önceki](expressions.md)
>[İleri](classes-and-objects.md)</span><span class="sxs-lookup"><span data-stu-id="13f52-140">[Previous](expressions.md)
[Next](classes-and-objects.md)</span></span>
