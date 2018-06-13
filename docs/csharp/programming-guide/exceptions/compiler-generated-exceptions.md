---
title: Derleyicinin Ürettiği Özel Durumlar (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: a1746a492685cf25869bd06935bfd056de257fea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331447"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a><span data-ttu-id="a18a4-102">Derleyicinin Ürettiği Özel Durumlar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a18a4-102">Compiler-Generated Exceptions (C# Programming Guide)</span></span>
<span data-ttu-id="a18a4-103">Temel işlemleri başarısız olduğunda bazı otomatik olarak .NET Framework'ün ortak dil çalışma zamanı tarafından (CLR) özel durumlar.</span><span class="sxs-lookup"><span data-stu-id="a18a4-103">Some exceptions are thrown automatically by the .NET Framework's common language runtime (CLR) when basic operations fail.</span></span> <span data-ttu-id="a18a4-104">Bu özel durumlar ve bunların hata koşulları aşağıdaki tabloda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="a18a4-104">These exceptions and their error conditions are listed in the following table.</span></span>  
  
|<span data-ttu-id="a18a4-105">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="a18a4-105">Exception</span></span>|<span data-ttu-id="a18a4-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a18a4-106">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|<span data-ttu-id="a18a4-107">Gibi aritmetik işlemler sırasında oluşan özel durumlar için temel sınıf <xref:System.DivideByZeroException> ve <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="a18a4-107">A base class for exceptions that occur during arithmetic operations, such as <xref:System.DivideByZeroException> and <xref:System.OverflowException>.</span></span>|  
|<xref:System.ArrayTypeMismatchException>|<span data-ttu-id="a18a4-108">Öğesinin gerçek türü dizi gerçek türü ile uyumlu olmadığı için belirli bir öğenin diziyi depolanamıyor zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a18a4-108">Thrown when an array cannot store a given element because the actual type of the element is incompatible with the actual type of the array.</span></span>|  
|<xref:System.DivideByZeroException>|<span data-ttu-id="a18a4-109">Bir tam sayı değeri bölmek için sıfıra girişimde zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a18a4-109">Thrown when an attempt is made to divide an integral value by zero.</span></span>|  
|<xref:System.IndexOutOfRangeException>|<span data-ttu-id="a18a4-110">Dizini sıfırdan küçük veya dizinin sınırları dışında olduğunda bir dizi dizini oluşturmak için bir girişimde zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a18a4-110">Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.</span></span>|  
|<xref:System.InvalidCastException>|<span data-ttu-id="a18a4-111">Taban türünden bir açık dönüştürme bir arabirim veya türetilmiş bir tür için çalışma zamanında başarısız olduğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a18a4-111">Thrown when an explicit conversion from a base type to an interface or to a derived type fails at runtime.</span></span>|  
|<xref:System.NullReferenceException>|<span data-ttu-id="a18a4-112">Değeri olan bir nesne başvurusu denediğinizde durum [null](../../../csharp/language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="a18a4-112">Thrown when you attempt to reference an object whose value is [null](../../../csharp/language-reference/keywords/null.md).</span></span>|  
|<xref:System.OutOfMemoryException>|<span data-ttu-id="a18a4-113">Bellek kullanarak ayırma girişimi zaman oluşturulur [yeni](../../../csharp/language-reference/keywords/new-operator.md) işleci başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="a18a4-113">Thrown when an attempt to allocate memory using the [new](../../../csharp/language-reference/keywords/new-operator.md) operator fails.</span></span> <span data-ttu-id="a18a4-114">Bu, ortak dil çalışma zamanı için kullanılabilir bellek tükendi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a18a4-114">This indicates that the memory available to the common language runtime has been exhausted.</span></span>|  
|<xref:System.OverflowException>|<span data-ttu-id="a18a4-115">Aritmetik bir işlem, zaman oluşturulan bir `checked` bağlamı taşar.</span><span class="sxs-lookup"><span data-stu-id="a18a4-115">Thrown when an arithmetic operation in a `checked` context overflows.</span></span>|  
|<xref:System.StackOverflowException>|<span data-ttu-id="a18a4-116">Yürütme yığını çok fazla bekleyen yöntem çağrılarını sağlayarak kaldığında oluşturulur; genellikle çok derin veya sonsuz özyineleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="a18a4-116">Thrown when the execution stack is exhausted by having too many pending method calls; usually indicates a very deep or infinite recursion.</span></span>|  
|<xref:System.TypeInitializationException>|<span data-ttu-id="a18a4-117">Statik Oluşturucusu bir özel durum ve hiçbir uyumlu oluşturduğunda durum `catch` yan tümcesi var. Bu yakalamak için.</span><span class="sxs-lookup"><span data-stu-id="a18a4-117">Thrown when a static constructor throws an exception and no compatible `catch` clause exists to catch it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a18a4-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a18a4-118">See Also</span></span>  
 [<span data-ttu-id="a18a4-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a18a4-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a18a4-120">Özel Durumlar ve Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="a18a4-120">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)  
 [<span data-ttu-id="a18a4-121">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="a18a4-121">Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/exception-handling.md)  
 [<span data-ttu-id="a18a4-122">try-catch</span><span class="sxs-lookup"><span data-stu-id="a18a4-122">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="a18a4-123">try-finally</span><span class="sxs-lookup"><span data-stu-id="a18a4-123">try-finally</span></span>](../../../csharp/language-reference/keywords/try-finally.md)  
 [<span data-ttu-id="a18a4-124">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="a18a4-124">try-catch-finally</span></span>](../../../csharp/language-reference/keywords/try-catch-finally.md)
