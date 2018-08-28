---
title: try-finally (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: beb54cf6c4e6dc87b9a08b81586b24d72f92b84b
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43001428"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="67909-102">try-finally (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="67909-102">try-finally (C# Reference)</span></span>
<span data-ttu-id="67909-103">Kullanarak bir `finally` bloğu içinde ayrılan tüm kaynakları temizleyebilirsiniz bir [deneyin](../../../csharp/language-reference/keywords/try-catch.md) bloğu ve kodu çalıştırabilir bir özel durum meydana gelse bile `try` blok.</span><span class="sxs-lookup"><span data-stu-id="67909-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](../../../csharp/language-reference/keywords/try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="67909-104">Genellikle, deyimleri bir `finally` denetimi terk ettiğinde çalıştırmak blok bir `try` deyimi.</span><span class="sxs-lookup"><span data-stu-id="67909-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="67909-105">Denetim aktarımı yürütülmesini normal yürütülmesi sonucunda oluşabilir bir `break`, `continue`, `goto`, veya `return` deyimi veya bir özel durumun yayılmasının `try` deyimi.</span><span class="sxs-lookup"><span data-stu-id="67909-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>  
  
 <span data-ttu-id="67909-106">İşlenen özel durum, ilişkili içinde `finally` blokun çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="67909-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="67909-107">Ancak, özel durum işlenmezse yürütülmesini `finally` bloğunun nasıl özel durumu geriye doğru izlenme işleminin tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="67909-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="67909-108">Buna karşılık, bilgisayarınızın nasıl ayarlandığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="67909-108">That, in turn, is dependent on how your computer is set up.</span></span>
  
 <span data-ttu-id="67909-109">Genelde işlenmeyen bir özel durum sona erdiğinde bir uygulama olup olmadığını `finally` blokunun çalıştırılıp çalıştırılmaması önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="67909-109">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="67909-110">Ancak, varsa bir `finally` bile bu durumda, tek bir çözüm çalıştırılması gereken bloğudur eklemek için bir `catch` bloğunu `try` - `finally` deyimi.</span><span class="sxs-lookup"><span data-stu-id="67909-110">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="67909-111">Alternatif olarak, oluşturulmuş olabilecek istisnayı yakalamak mümkündür `try` bloğu bir `try` - `finally` çağrı yığınının üstlerinde deyimi.</span><span class="sxs-lookup"><span data-stu-id="67909-111">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="67909-112">Diğer bir deyişle, özel durum içeren yöntemi çağıran yöntemi yakalayabilir `try` - `finally` deyimi, veya bu yöntemi çağıran yöntemdeki veya çağrı yığınındaki herhangi bir yöntemi.</span><span class="sxs-lookup"><span data-stu-id="67909-112">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="67909-113">Özel durum yakalanmazsa yürütülmesini `finally` blok bağlı olup bir işletim sistemi bir özel durum harekete seçer üzerinde bırakma işlemi.</span><span class="sxs-lookup"><span data-stu-id="67909-113">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67909-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="67909-114">Example</span></span>  
 <span data-ttu-id="67909-115">Aşağıdaki örnekte, geçersiz dönüştürme deyimi neden olan bir `System.InvalidCastException` özel durum.</span><span class="sxs-lookup"><span data-stu-id="67909-115">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="67909-116">İşlenmeyen özel durum.</span><span class="sxs-lookup"><span data-stu-id="67909-116">The exception is unhandled.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 <span data-ttu-id="67909-117">Aşağıdaki örnekte, bir özel durumdan `TryCast` yöntemi bir yöntem çağrı yığınında yığınından uzakta yakalandı.</span><span class="sxs-lookup"><span data-stu-id="67909-117">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 <span data-ttu-id="67909-118">Hakkında daha fazla bilgi için `finally`, bkz: [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="67909-118">For more information about `finally`, see [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span></span>  
  
 <span data-ttu-id="67909-119">C# ayrıca içerir [using deyimi](../../../csharp/language-reference/keywords/using-statement.md), için benzer işlevsellik sağlayan <xref:System.IDisposable> bir sözdizimindeki nesneleri.</span><span class="sxs-lookup"><span data-stu-id="67909-119">C# also contains the [using statement](../../../csharp/language-reference/keywords/using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="67909-120">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="67909-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="67909-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="67909-121">See Also</span></span>

- [<span data-ttu-id="67909-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="67909-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="67909-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="67909-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="67909-124">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="67909-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="67909-125">try, throw ve catch Deyimleri (C++)</span><span class="sxs-lookup"><span data-stu-id="67909-125">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)  
- [<span data-ttu-id="67909-126">Özel Durum İşleme Deyimleri</span><span class="sxs-lookup"><span data-stu-id="67909-126">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
- [<span data-ttu-id="67909-127">throw</span><span class="sxs-lookup"><span data-stu-id="67909-127">throw</span></span>](../../../csharp/language-reference/keywords/throw.md)  
- [<span data-ttu-id="67909-128">try-catch</span><span class="sxs-lookup"><span data-stu-id="67909-128">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
- [<span data-ttu-id="67909-129">Nasıl yapılır: Açıkça Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="67909-129">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
