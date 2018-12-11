---
title: try-finally - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 2bfdc4e94f5c5dc613eac06efcd69407576b0db4
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239270"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="524f4-102">try-finally (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="524f4-102">try-finally (C# Reference)</span></span>

<span data-ttu-id="524f4-103">Kullanarak bir `finally` bloğu içinde ayrılan tüm kaynakları temizleyebilirsiniz bir [deneyin](try-catch.md) bloğu ve kodu çalıştırabilir bir özel durum meydana gelse bile `try` blok.</span><span class="sxs-lookup"><span data-stu-id="524f4-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="524f4-104">Genellikle, deyimleri bir `finally` denetimi terk ettiğinde çalıştırmak blok bir `try` deyimi.</span><span class="sxs-lookup"><span data-stu-id="524f4-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="524f4-105">Denetim aktarımı yürütülmesini normal yürütülmesi sonucunda oluşabilir bir `break`, `continue`, `goto`, veya `return` deyimi veya bir özel durumun yayılmasının `try` deyimi.</span><span class="sxs-lookup"><span data-stu-id="524f4-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>

<span data-ttu-id="524f4-106">İşlenen özel durum, ilişkili içinde `finally` blokun çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="524f4-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="524f4-107">Ancak, özel durum işlenmezse yürütülmesini `finally` bloğunun nasıl özel durumu geriye doğru izlenme işleminin tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="524f4-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="524f4-108">Buna karşılık, bilgisayarınızın nasıl ayarlandığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="524f4-108">That, in turn, is dependent on how your computer is set up.</span></span>

<span data-ttu-id="524f4-109">Genelde işlenmeyen bir özel durum sona erdiğinde bir uygulama olup olmadığını `finally` blokunun çalıştırılıp çalıştırılmaması önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="524f4-109">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="524f4-110">Ancak, varsa bir `finally` bile bu durumda, tek bir çözüm çalıştırılması gereken bloğudur eklemek için bir `catch` bloğunu `try` - `finally` deyimi.</span><span class="sxs-lookup"><span data-stu-id="524f4-110">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="524f4-111">Alternatif olarak, oluşturulmuş olabilecek istisnayı yakalamak mümkündür `try` bloğu bir `try` - `finally` çağrı yığınının üstlerinde deyimi.</span><span class="sxs-lookup"><span data-stu-id="524f4-111">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="524f4-112">Diğer bir deyişle, özel durum içeren yöntemi çağıran yöntemi yakalayabilir `try` - `finally` deyimi, veya bu yöntemi çağıran yöntemdeki veya çağrı yığınındaki herhangi bir yöntemi.</span><span class="sxs-lookup"><span data-stu-id="524f4-112">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="524f4-113">Özel durum yakalanmazsa yürütülmesini `finally` blok bağlı olup bir işletim sistemi bir özel durum harekete seçer üzerinde bırakma işlemi.</span><span class="sxs-lookup"><span data-stu-id="524f4-113">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>

## <a name="example"></a><span data-ttu-id="524f4-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="524f4-114">Example</span></span>

<span data-ttu-id="524f4-115">Aşağıdaki örnekte, geçersiz dönüştürme deyimi neden olan bir `System.InvalidCastException` özel durum.</span><span class="sxs-lookup"><span data-stu-id="524f4-115">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="524f4-116">İşlenmeyen özel durum.</span><span class="sxs-lookup"><span data-stu-id="524f4-116">The exception is unhandled.</span></span>

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

<span data-ttu-id="524f4-117">Aşağıdaki örnekte, bir özel durumdan `TryCast` yöntemi bir yöntem çağrı yığınında yığınından uzakta yakalandı.</span><span class="sxs-lookup"><span data-stu-id="524f4-117">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

<span data-ttu-id="524f4-118">Hakkında daha fazla bilgi için `finally`, bkz: [try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="524f4-118">For more information about `finally`, see [try-catch-finally](try-catch-finally.md).</span></span>

<span data-ttu-id="524f4-119">C# ayrıca içerir [using deyimi](using-statement.md), için benzer işlevsellik sağlayan <xref:System.IDisposable> bir sözdizimindeki nesneleri.</span><span class="sxs-lookup"><span data-stu-id="524f4-119">C# also contains the [using statement](using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="524f4-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="524f4-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="524f4-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="524f4-121">See Also</span></span>

- [<span data-ttu-id="524f4-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="524f4-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="524f4-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="524f4-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="524f4-124">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="524f4-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="524f4-125">try, throw ve catch Deyimleri (C++)</span><span class="sxs-lookup"><span data-stu-id="524f4-125">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="524f4-126">Özel Durum İşleme Deyimleri</span><span class="sxs-lookup"><span data-stu-id="524f4-126">Exception Handling Statements</span></span>](exception-handling-statements.md)
- [<span data-ttu-id="524f4-127">throw</span><span class="sxs-lookup"><span data-stu-id="524f4-127">throw</span></span>](throw.md)
- [<span data-ttu-id="524f4-128">try-catch</span><span class="sxs-lookup"><span data-stu-id="524f4-128">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="524f4-129">Nasıl yapılır: Açıkça özel durumlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="524f4-129">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)