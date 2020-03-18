---
title: try-finally - C# Referans
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 2c4c69b1e104aed968bc24bac690de83026643a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713020"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="eba86-102">try-finally (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="eba86-102">try-finally (C# Reference)</span></span>

<span data-ttu-id="eba86-103">Bir `finally` blok kullanarak, [try](try-catch.md) bloğunda ayrılan kaynakları temizleyebilir ve `try` blokta bir özel durum oluşsa bile kodu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eba86-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="eba86-104">Genellikle, denetim bir `finally` `try` deyim bırakırken bir blok çalışması ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="eba86-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="eba86-105">Denetim aktarımı, normal yürütme, `break`bir , , `continue` `goto`, veya `return` deyimi, ya da `try` bir özel durum dış deyimi nin yayılması nın bir sonucu olarak oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="eba86-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>

<span data-ttu-id="eba86-106">İşlenen özel durum `finally` içinde, ilişkili bloğun çalıştırılması garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="eba86-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="eba86-107">Ancak, özel durum işlenmemişse, `finally` bloğun yürütülmesi özel durum gevşeme işleminin nasıl tetiklendirilen bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="eba86-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="eba86-108">Bu da bilgisayarınızın nasıl ayarlıyorumuna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="eba86-108">That, in turn, is dependent on how your computer is set up.</span></span>

<span data-ttu-id="eba86-109">Genellikle, işlenmemiş bir özel durum bir uygulamayı `finally` sona erdirdiğinde, bloğun çalışıp çalışmadığı önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="eba86-109">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="eba86-110">Ancak, bu durumda bile `finally` çalıştırılması gereken bir blokta ifadeler varsa, `catch` bir çözüm `try` - `finally` deyimi bir blok eklemektir.</span><span class="sxs-lookup"><span data-stu-id="eba86-110">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="eba86-111">Alternatif olarak, çağrı yığınının yukarısındaki `try` bir `try` - `finally` deyimin bloğuna atılabilecek özel durumu yakalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eba86-111">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="eba86-112">Diğer bir deyişle, `try` - `finally` deyimi içeren yöntemi çağıran yöntemde veya bu yöntemi çağıran yöntemde veya çağrı yığınındaki herhangi bir yöntemde özel durumu yakalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eba86-112">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="eba86-113">Özel durum yakalanmazsa, `finally` bloğun yürütülmesi işletim sisteminin bir özel durum gevşeme işlemini tetiklemeyi seçip seçmediğine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="eba86-113">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>

## <a name="example"></a><span data-ttu-id="eba86-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="eba86-114">Example</span></span>

<span data-ttu-id="eba86-115">Aşağıdaki örnekte, geçersiz bir dönüşüm `System.InvalidCastException` bildirimi özel bir özel durum neden olur.</span><span class="sxs-lookup"><span data-stu-id="eba86-115">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="eba86-116">Özel durum işlenmemiş.</span><span class="sxs-lookup"><span data-stu-id="eba86-116">The exception is unhandled.</span></span>

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

<span data-ttu-id="eba86-117">Aşağıdaki örnekte, yöntemden `TryCast` bir özel durum, çağrı yığınının daha yukarısındaki bir yöntemde yakalanır.</span><span class="sxs-lookup"><span data-stu-id="eba86-117">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

<span data-ttu-id="eba86-118">Hakkında `finally`daha fazla bilgi için, [try-catch-finally](try-catch-finally.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="eba86-118">For more information about `finally`, see [try-catch-finally](try-catch-finally.md).</span></span>

<span data-ttu-id="eba86-119">C# ayrıca, kullanışlı bir sözdiziminde nesneler için <xref:System.IDisposable> benzer işlevler sağlayan using [deyimini](using-statement.md)de içerir.</span><span class="sxs-lookup"><span data-stu-id="eba86-119">C# also contains the [using statement](using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="eba86-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="eba86-120">C# language specification</span></span>

<span data-ttu-id="eba86-121">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [try deyimi](~/_csharplang/spec/statements.md#the-try-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="eba86-121">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eba86-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eba86-122">See also</span></span>

- [<span data-ttu-id="eba86-123">C# Referans</span><span class="sxs-lookup"><span data-stu-id="eba86-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="eba86-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="eba86-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="eba86-125">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="eba86-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="eba86-126">try, throw ve catch Deyimleri (C++)</span><span class="sxs-lookup"><span data-stu-id="eba86-126">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="eba86-127">throw</span><span class="sxs-lookup"><span data-stu-id="eba86-127">throw</span></span>](throw.md)
- [<span data-ttu-id="eba86-128">try-catch</span><span class="sxs-lookup"><span data-stu-id="eba86-128">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="eba86-129">Nasıl yapılır: Açıkça Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="eba86-129">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
