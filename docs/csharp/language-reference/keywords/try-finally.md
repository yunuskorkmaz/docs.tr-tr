---
title: try-finally- C# Reference
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 2c4c69b1e104aed968bc24bac690de83026643a0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713020"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="9d981-102">try-finally (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9d981-102">try-finally (C# Reference)</span></span>

<span data-ttu-id="9d981-103">Bir `finally` bloğu kullanarak, bir [TRY](try-catch.md) bloğunda ayrılan tüm kaynakları temizleyebilir ve `try` bloğunda bir özel durum meydana gelirse bile kodu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d981-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="9d981-104">Genellikle, denetim bir `try` deyiminden ayrıldığında `finally` bloğunun deyimleri çalışır.</span><span class="sxs-lookup"><span data-stu-id="9d981-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="9d981-105">Denetim aktarımı, `break`, `continue`, `goto`veya `return` deyimlerinin yürütülmesi ya da `try` deyimindeki bir özel durumun yayılmasından kaynaklanan normal yürütmenin sonucu olarak ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="9d981-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>

<span data-ttu-id="9d981-106">İşlenmiş bir özel durum içinde, ilişkili `finally` bloğunun çalıştırılması garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="9d981-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="9d981-107">Ancak, özel durum işlenmemiş ise, `finally` bloğunun yürütülmesi özel durum geriye doğru izleme işleminin nasıl tetiklendiğine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9d981-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="9d981-108">Bu da, bilgisayarınızın nasıl ayarlanmayacağına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9d981-108">That, in turn, is dependent on how your computer is set up.</span></span>

<span data-ttu-id="9d981-109">Genellikle, işlenmeyen bir özel durum uygulamayı sona erdirdiğinde, `finally` bloğunun çalıştırılıp çalıştırılmayacağı önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="9d981-109">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="9d981-110">Ancak, bu durumda bile çalıştırılması gereken bir `finally` bloğunda deyiminiz varsa, tek bir çözüm `try`-`finally` ifadesine bir `catch` bloğu eklemektir.</span><span class="sxs-lookup"><span data-stu-id="9d981-110">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="9d981-111">Alternatif olarak, çağrı yığınında daha yüksek bir `try`-`finally` ifadesinin `try` bloğunda oluşturulan özel durumu yakalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d981-111">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="9d981-112">Diğer bir deyişle, `try`-`finally` ifadesini veya bu yöntemi çağıran yöntemi ya da çağrı yığınındaki herhangi bir yöntemi çağıran yöntemi çağıran özel durumu yakalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d981-112">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="9d981-113">Özel durum yakalanmadığında, `finally` bloğunun yürütülmesi işletim sisteminin özel durum geriye doğru izleme işlemi tetiklemeyi seçip seçmeyeceğini bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9d981-113">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>

## <a name="example"></a><span data-ttu-id="9d981-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d981-114">Example</span></span>

<span data-ttu-id="9d981-115">Aşağıdaki örnekte, geçersiz bir dönüştürme ekstresi `System.InvalidCastException` bir özel duruma neden olur.</span><span class="sxs-lookup"><span data-stu-id="9d981-115">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="9d981-116">Özel durum işlenmemiş olur.</span><span class="sxs-lookup"><span data-stu-id="9d981-116">The exception is unhandled.</span></span>

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

<span data-ttu-id="9d981-117">Aşağıdaki örnekte, `TryCast` yönteminden bir özel durum, çağrı yığınının ardından bir yöntemde yakalanır.</span><span class="sxs-lookup"><span data-stu-id="9d981-117">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

<span data-ttu-id="9d981-118">`finally`hakkında daha fazla bilgi için bkz. [try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="9d981-118">For more information about `finally`, see [try-catch-finally](try-catch-finally.md).</span></span>

<span data-ttu-id="9d981-119">C#Ayrıca, uygun bir sözdiziminde <xref:System.IDisposable> nesneler için benzer işlevler sağlayan [using ifadesini](using-statement.md)de içerir.</span><span class="sxs-lookup"><span data-stu-id="9d981-119">C# also contains the [using statement](using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9d981-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="9d981-120">C# language specification</span></span>

<span data-ttu-id="9d981-121">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [TRY deyimin](~/_csharplang/spec/statements.md#the-try-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9d981-121">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9d981-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d981-122">See also</span></span>

- [<span data-ttu-id="9d981-123">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="9d981-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9d981-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9d981-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9d981-125">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="9d981-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9d981-126">try, throw ve catch Deyimleri (C++)</span><span class="sxs-lookup"><span data-stu-id="9d981-126">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="9d981-127">throw</span><span class="sxs-lookup"><span data-stu-id="9d981-127">throw</span></span>](throw.md)
- [<span data-ttu-id="9d981-128">try-catch</span><span class="sxs-lookup"><span data-stu-id="9d981-128">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="9d981-129">Nasıl yapılır: Açıkça Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9d981-129">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
