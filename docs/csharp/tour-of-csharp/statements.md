---
title: C#Deyimler- C# dilin turu
description: Deyimleri kullanarak bir C# programın eylemlerini oluşturun
ms.date: 02/27/2020
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: ced13b1bfd17977acb98bf33c0a477161cf08a93
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159110"
---
# <a name="statements"></a><span data-ttu-id="1b32e-103">Deyimler</span><span class="sxs-lookup"><span data-stu-id="1b32e-103">Statements</span></span>

<span data-ttu-id="1b32e-104">Bir programın eylemleri *deyimler*kullanılarak ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="1b32e-104">The actions of a program are expressed using *statements*.</span></span> <span data-ttu-id="1b32e-105">C#, birden çok farklı türde deyimi destekler, bu sayı katıştırılmış deyimler bakımından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="1b32e-105">C# supports several different kinds of statements, a number of which are defined in terms of embedded statements.</span></span>

<span data-ttu-id="1b32e-106">Bir *blok* , tek bir ifadeye izin verilen bağlamlarda birden çok deyimin yazılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="1b32e-106">A *block* permits multiple statements to be written in contexts where a single statement is allowed.</span></span> <span data-ttu-id="1b32e-107">Bir blok `{` ve `}`sınırlayıcıları arasına yazılan deyimler listesinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="1b32e-107">A block consists of a list of statements written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="1b32e-108">*Bildirim deyimleri* yerel değişkenleri ve sabitleri bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b32e-108">*Declaration statements* are used to declare local variables and constants.</span></span>

<span data-ttu-id="1b32e-109">*İfade deyimleri* , ifadeleri değerlendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b32e-109">*Expression statements* are used to evaluate expressions.</span></span> <span data-ttu-id="1b32e-110">Deyimler olarak kullanılabilecek ifadeler, `new` işleci kullanılarak nesne ayırmaları, `=` ve bileşik atama işleçleri kullanılarak atamalar, `++` ve `--` işleçlerini ve `await` ifadelerini kullanarak işlemleri artırma ve azaltma işlemlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1b32e-110">Expressions that can be used as statements include method invocations, object allocations using the `new` operator, assignments using `=` and the compound assignment operators, increment and decrement operations using the `++` and `--` operators and `await` expressions.</span></span>

<span data-ttu-id="1b32e-111">*Seçim deyimleri* , bazı deyimlerin değerine göre yürütme için bir dizi olası deyimden birini seçmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b32e-111">*Selection statements* are used to select one of a number of possible statements for execution based on the value of some expression.</span></span> <span data-ttu-id="1b32e-112">Bu grup `if` ve `switch` deyimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1b32e-112">This group contains the `if` and `switch` statements.</span></span>

<span data-ttu-id="1b32e-113">*Yineleme deyimleri* , art arda gömülü bir deyimi yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b32e-113">*Iteration statements* are used to execute repeatedly an embedded statement.</span></span> <span data-ttu-id="1b32e-114">Bu grup `while`, `do`, `for`ve `foreach` deyimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1b32e-114">This group contains the `while`, `do`, `for`, and `foreach` statements.</span></span>

<span data-ttu-id="1b32e-115">*Sıçrama deyimleri* , denetimi aktarmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b32e-115">*Jump statements* are used to transfer control.</span></span> <span data-ttu-id="1b32e-116">Bu grup `break`, `continue`, `goto`, `throw`, `return`ve `yield` deyimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1b32e-116">This group contains the `break`, `continue`, `goto`, `throw`, `return`, and `yield` statements.</span></span>

<span data-ttu-id="1b32e-117">`try`...`catch` deyimleri, bir bloğun yürütülmesi sırasında oluşan özel durumları yakalamak için kullanılır ve bir özel durumun gerçekleşmediği, her zaman yürütülen sonlandırma kodunu belirtmek için `try`...`finally` deyimleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b32e-117">The `try`...`catch` statement is used to catch exceptions that occur during execution of a block, and the `try`...`finally` statement is used to specify finalization code that is always executed, whether an exception occurred or not.</span></span>

<span data-ttu-id="1b32e-118">`checked` ve `unchecked` deyimleri, tam sayı türü aritmetik işlemler ve dönüştürmeler için taşma denetimi bağlamını denetlemek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b32e-118">The `checked` and `unchecked` statements are used to control the overflow-checking context for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="1b32e-119">`lock` deyimleri, belirli bir nesne için karşılıklı dışlama kilidini almak, bir ifadeyi yürütmek ve sonra kilidi serbest bırakmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b32e-119">The `lock` statement is used to obtain the mutual-exclusion lock for a given object, execute a statement, and then release the lock.</span></span>

<span data-ttu-id="1b32e-120">`using` deyimleri, kaynak almak, bir ifadeyi yürütmek ve ardından bu kaynağı atmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b32e-120">The `using` statement is used to obtain a resource, execute a statement, and then dispose of that resource.</span></span>

<span data-ttu-id="1b32e-121">Aşağıdakiler, kullanılabilecek deyimlerin türlerini listeler ve her biri için bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b32e-121">The following lists the kinds of statements that can be used, and provides an example for each.</span></span>

* <span data-ttu-id="1b32e-122">Yerel değişken bildirimi:</span><span class="sxs-lookup"><span data-stu-id="1b32e-122">Local variable declaration:</span></span>

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* <span data-ttu-id="1b32e-123">Yerel sabit bildirimi:</span><span class="sxs-lookup"><span data-stu-id="1b32e-123">Local constant declaration:</span></span>

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* <span data-ttu-id="1b32e-124">İfade deyimi:</span><span class="sxs-lookup"><span data-stu-id="1b32e-124">Expression statement:</span></span>

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* <span data-ttu-id="1b32e-125">`if` ekstresi:</span><span class="sxs-lookup"><span data-stu-id="1b32e-125">`if` statement:</span></span>

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* <span data-ttu-id="1b32e-126">`switch` ekstresi:</span><span class="sxs-lookup"><span data-stu-id="1b32e-126">`switch` statement:</span></span>

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* <span data-ttu-id="1b32e-127">`while` ekstresi:</span><span class="sxs-lookup"><span data-stu-id="1b32e-127">`while` statement:</span></span>

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* <span data-ttu-id="1b32e-128">`do` ekstresi:</span><span class="sxs-lookup"><span data-stu-id="1b32e-128">`do` statement:</span></span>

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* <span data-ttu-id="1b32e-129">`for` ekstresi:</span><span class="sxs-lookup"><span data-stu-id="1b32e-129">`for` statement:</span></span>

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* <span data-ttu-id="1b32e-130">`foreach` ekstresi:</span><span class="sxs-lookup"><span data-stu-id="1b32e-130">`foreach` statement:</span></span>

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* <span data-ttu-id="1b32e-131">`break` ekstresi:</span><span class="sxs-lookup"><span data-stu-id="1b32e-131">`break` statement:</span></span>

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* <span data-ttu-id="1b32e-132">`continue` ekstresi:</span><span class="sxs-lookup"><span data-stu-id="1b32e-132">`continue` statement:</span></span>

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* <span data-ttu-id="1b32e-133">`goto` ekstresi:</span><span class="sxs-lookup"><span data-stu-id="1b32e-133">`goto` statement:</span></span>

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* <span data-ttu-id="1b32e-134">`return` ekstresi:</span><span class="sxs-lookup"><span data-stu-id="1b32e-134">`return` statement:</span></span>

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* <span data-ttu-id="1b32e-135">`yield` ekstresi:</span><span class="sxs-lookup"><span data-stu-id="1b32e-135">`yield` statement:</span></span>

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* <span data-ttu-id="1b32e-136">`throw` deyimleri ve `try` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="1b32e-136">`throw` statements and `try` statements:</span></span>

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* <span data-ttu-id="1b32e-137">`checked` ve `unchecked` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="1b32e-137">`checked` and `unchecked` statements:</span></span>

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* <span data-ttu-id="1b32e-138">`lock` ekstresi:</span><span class="sxs-lookup"><span data-stu-id="1b32e-138">`lock` statement:</span></span>

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* <span data-ttu-id="1b32e-139">`using` ekstresi:</span><span class="sxs-lookup"><span data-stu-id="1b32e-139">`using` statement:</span></span>

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
><span data-ttu-id="1b32e-140">[Önceki](expressions.md)
>[İleri](classes-and-objects.md)</span><span class="sxs-lookup"><span data-stu-id="1b32e-140">[Previous](expressions.md)
[Next](classes-and-objects.md)</span></span>
