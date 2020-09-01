---
description: try-finally-C# başvurusu
title: try-finally-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 621c5bf1607136361b72f978681607ec2aec150f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141978"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="0ffcb-103">try-finally (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0ffcb-103">try-finally (C# Reference)</span></span>

<span data-ttu-id="0ffcb-104">Bir blok kullanarak `finally` , bir [TRY](try-catch.md) bloğunda ayrılan tüm kaynakları temizleyebilir ve bir özel durum bloğunda meydana gelirse bile kodu çalıştırabilirsiniz `try` .</span><span class="sxs-lookup"><span data-stu-id="0ffcb-104">By using a `finally` block, you can clean up any resources that are allocated in a [try](try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="0ffcb-105">Genellikle, `finally` Denetim bir deyiminden ayrıldığında blok deyimleri çalışır `try` .</span><span class="sxs-lookup"><span data-stu-id="0ffcb-105">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="0ffcb-106">Denetimin aktarımı normal yürütme,,, `break` `continue` `goto` veya `return` bildiriminin yürütülmesi ya da deyimden bir özel durumun yayılmasından kaynaklanıyor olabilir `try` .</span><span class="sxs-lookup"><span data-stu-id="0ffcb-106">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>

<span data-ttu-id="0ffcb-107">İşlenmiş bir özel durum içinde, ilişkili `finally` bloğun çalıştırılması garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="0ffcb-107">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="0ffcb-108">Ancak, özel durum işlenmemiş ise, `finally` bloğun yürütülmesi özel durum geriye doğru tetikleme işleminin tetiklendiği duruma bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0ffcb-108">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="0ffcb-109">Bu da, bilgisayarınızın nasıl ayarlanmayacağına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0ffcb-109">That, in turn, is dependent on how your computer is set up.</span></span>

<span data-ttu-id="0ffcb-110">Genellikle, işlenmeyen bir özel durum uygulamayı sona erdirdiğinde, `finally` bloğun çalıştırılıp çalıştırılmayacağı önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="0ffcb-110">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="0ffcb-111">Ancak, `finally` Bu durumda bile çalıştırılması gereken bir blokta deyimler varsa, bir çözüm `catch` ifadeye bir blok eklemektir `try` - `finally` .</span><span class="sxs-lookup"><span data-stu-id="0ffcb-111">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="0ffcb-112">Alternatif olarak, `try` `try` - çağrı yığınının üst kısmında yer alan bir deyimin bloğunda ortaya atılmış olabilecek özel durumu yakalayabilirsiniz `finally` .</span><span class="sxs-lookup"><span data-stu-id="0ffcb-112">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="0ffcb-113">Diğer bir deyişle, bir yöntemi `try` - `finally` , ifadeyi içeren yöntemi veya bu yöntemi çağıran yöntemi ya da çağrı yığınında herhangi bir yöntemi çağıran yöntemini yakalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ffcb-113">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="0ffcb-114">Özel durum yakalanmadığında, `finally` bloğun yürütülmesi işletim sisteminin özel durum geriye doğru izleme işlemi tetiklemeyi seçip seçmediğine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0ffcb-114">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>

## <a name="example"></a><span data-ttu-id="0ffcb-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ffcb-115">Example</span></span>

<span data-ttu-id="0ffcb-116">Aşağıdaki örnekte, geçersiz bir dönüştürme açıklaması özel duruma neden olur `System.InvalidCastException` .</span><span class="sxs-lookup"><span data-stu-id="0ffcb-116">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="0ffcb-117">Özel durum işlenmemiş olur.</span><span class="sxs-lookup"><span data-stu-id="0ffcb-117">The exception is unhandled.</span></span>

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

<span data-ttu-id="0ffcb-118">Aşağıdaki örnekte, yöntem içindeki bir özel durum, `TryCast` çağrı yığınının ardından bir yöntemde yakalanır.</span><span class="sxs-lookup"><span data-stu-id="0ffcb-118">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

<span data-ttu-id="0ffcb-119">Hakkında daha fazla bilgi için `finally` bkz. [try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="0ffcb-119">For more information about `finally`, see [try-catch-finally](try-catch-finally.md).</span></span>

<span data-ttu-id="0ffcb-120">C# Ayrıca, uygun bir sözdiziminde nesneler için benzer işlevler sağlayan [using ifadesini](using-statement.md)de içerir <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="0ffcb-120">C# also contains the [using statement](using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0ffcb-121">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="0ffcb-121">C# language specification</span></span>

<span data-ttu-id="0ffcb-122">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [TRY deyimin](~/_csharplang/spec/statements.md#the-try-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0ffcb-122">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0ffcb-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ffcb-123">See also</span></span>

- [<span data-ttu-id="0ffcb-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0ffcb-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0ffcb-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0ffcb-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0ffcb-126">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0ffcb-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0ffcb-127">try, throw ve catch Deyimleri (C++)</span><span class="sxs-lookup"><span data-stu-id="0ffcb-127">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="0ffcb-128">throw</span><span class="sxs-lookup"><span data-stu-id="0ffcb-128">throw</span></span>](throw.md)
- [<span data-ttu-id="0ffcb-129">try-catch</span><span class="sxs-lookup"><span data-stu-id="0ffcb-129">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="0ffcb-130">Nasıl yapılır: Açıkça Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0ffcb-130">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
