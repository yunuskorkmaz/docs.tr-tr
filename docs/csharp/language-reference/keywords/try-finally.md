---
title: "try-finally (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 927b851419f2c5245518ee39bf847cb1f1664917
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="67ad6-102">try-finally (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="67ad6-102">try-finally (C# Reference)</span></span>
<span data-ttu-id="67ad6-103">Kullanarak bir `finally` bloğu içinde ayrılan tüm kaynakları temizlemek bir [deneyin](../../../csharp/language-reference/keywords/try-catch.md) bloğu ve çalıştırabilirsiniz kod içinde bir özel durum oluştuğunda dahi `try` bloğu.</span><span class="sxs-lookup"><span data-stu-id="67ad6-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](../../../csharp/language-reference/keywords/try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="67ad6-104">Genellikle, bilgilerinin bir `finally` denetim ayrıldığında çalıştırmak blok bir `try` deyimi.</span><span class="sxs-lookup"><span data-stu-id="67ad6-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="67ad6-105">Denetim aktarımını yürütülmesi normal yürütülmesi sonucu olarak ortaya çıkabilir bir `break`, `continue`, `goto`, veya `return` deyimi, veya bir özel durum dışında yayılmasını `try` deyimi.</span><span class="sxs-lookup"><span data-stu-id="67ad6-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>  
  
 <span data-ttu-id="67ad6-106">Bir özel durumu, ilişkili içinde `finally` blok garanti çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="67ad6-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="67ad6-107">Ancak, işlenmemiş özel durum oluştu, yürütülmesi `finally` blok bağımlı olduğu nasıl özel durum bırakma işlemi tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="67ad6-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="67ad6-108">Buna karşılık, bilgisayarınızı nasıl ayarlanacağını bağımlı olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="67ad6-108">That, in turn, is dependent on how your computer is set up.</span></span>
  
 <span data-ttu-id="67ad6-109">Genellikle, işlenmeyen bir özel durum sona erdiğinde bir uygulama olup olmadığına `finally` blok çalıştırıldığında önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="67ad6-109">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="67ad6-110">Ancak, deyimleri varsa bir `finally` bile bu durumda, bir çözüm çalıştırılması gereken taşıdır eklemek için bir `catch` için engelleyin `try` - `finally` deyimi.</span><span class="sxs-lookup"><span data-stu-id="67ad6-110">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="67ad6-111">Alternatif olarak, bir durum içinde özel durum yakalayabilir `try` , engelleme bir `try` - `finally` deyimi çağrı yığınına daha yüksek.</span><span class="sxs-lookup"><span data-stu-id="67ad6-111">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="67ad6-112">Diğer bir deyişle, içeren yöntemini çağıran yöntemi özel durum yakalayabilir `try` - `finally` deyimi, ya da bu yöntemi çağırır yöntemi veya çağrı yığınında herhangi bir yöntemi.</span><span class="sxs-lookup"><span data-stu-id="67ad6-112">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="67ad6-113">Özel durum yakalandı, yürütülmesi `finally` blok bağlı olup olmadığını işletim sistemi bir özel durum harekete seçti üzerinde işlem bırakma.</span><span class="sxs-lookup"><span data-stu-id="67ad6-113">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67ad6-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="67ad6-114">Example</span></span>  
 <span data-ttu-id="67ad6-115">Aşağıdaki örnekte, bir geçersiz dönüştürme deyimi neden bir `System.InvalidCastException` özel durum.</span><span class="sxs-lookup"><span data-stu-id="67ad6-115">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="67ad6-116">İşlenmeyen özel durum kodudur.</span><span class="sxs-lookup"><span data-stu-id="67ad6-116">The exception is unhandled.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 <span data-ttu-id="67ad6-117">Aşağıdaki örnekte, bir özel durumundan `TryCast` yöntemi bir yöntemi uzağa çağrı yığını yakalanma yeri.</span><span class="sxs-lookup"><span data-stu-id="67ad6-117">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 <span data-ttu-id="67ad6-118">Hakkında daha fazla bilgi için `finally`, bkz: [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="67ad6-118">For more information about `finally`, see [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span></span>  
  
 <span data-ttu-id="67ad6-119">C# de içerir [deyimiyle](../../../csharp/language-reference/keywords/using-statement.md), için benzer bir işlevsellik sağlayan <xref:System.IDisposable> kullanışlı bir söz dizimi nesneleri.</span><span class="sxs-lookup"><span data-stu-id="67ad6-119">C# also contains the [using statement](../../../csharp/language-reference/keywords/using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="67ad6-120">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="67ad6-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="67ad6-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="67ad6-121">See Also</span></span>  
 [<span data-ttu-id="67ad6-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="67ad6-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="67ad6-123">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="67ad6-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="67ad6-124">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="67ad6-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="67ad6-125">deneyin, throw ve catch deyimleri (C++)</span><span class="sxs-lookup"><span data-stu-id="67ad6-125">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)  
 [<span data-ttu-id="67ad6-126">Özel durum işleme deyimleri</span><span class="sxs-lookup"><span data-stu-id="67ad6-126">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [<span data-ttu-id="67ad6-127">throw</span><span class="sxs-lookup"><span data-stu-id="67ad6-127">throw</span></span>](../../../csharp/language-reference/keywords/throw.md)  
 [<span data-ttu-id="67ad6-128">try-catch</span><span class="sxs-lookup"><span data-stu-id="67ad6-128">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="67ad6-129">Nasıl yapılır: açıkça özel durumlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="67ad6-129">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
