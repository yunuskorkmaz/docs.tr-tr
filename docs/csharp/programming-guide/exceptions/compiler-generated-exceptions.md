---
title: Derleyici-Oluşturulan Özel Durumlar - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 2a6b2c3fa053f1c555856df8098975340e78e2b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705320"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a><span data-ttu-id="a0daf-102">Derleyicinin Ürettiği Özel Durumlar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a0daf-102">Compiler-Generated Exceptions (C# Programming Guide)</span></span>
<span data-ttu-id="a0daf-103">Bazı özel durumlar,.NET Framework'ün ortak dil çalışma süresi (CLR) tarafından temel işlemler başarısız olduğunda otomatik olarak atılır.</span><span class="sxs-lookup"><span data-stu-id="a0daf-103">Some exceptions are thrown automatically by the .NET Framework's common language runtime (CLR) when basic operations fail.</span></span> <span data-ttu-id="a0daf-104">Bu özel durumlar ve hata koşulları aşağıdaki tabloda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="a0daf-104">These exceptions and their error conditions are listed in the following table.</span></span>  
  
|<span data-ttu-id="a0daf-105">Özel durum</span><span class="sxs-lookup"><span data-stu-id="a0daf-105">Exception</span></span>|<span data-ttu-id="a0daf-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0daf-106">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|<span data-ttu-id="a0daf-107">Aritmetik işlemler sırasında oluşan özel durumlar için <xref:System.DivideByZeroException> bir <xref:System.OverflowException>taban sınıf, ve.</span><span class="sxs-lookup"><span data-stu-id="a0daf-107">A base class for exceptions that occur during arithmetic operations, such as <xref:System.DivideByZeroException> and <xref:System.OverflowException>.</span></span>|  
|<xref:System.ArrayTypeMismatchException>|<span data-ttu-id="a0daf-108">Öğenin gerçek türü dizinin gerçek türüyle uyumsuz olduğundan, bir dizi belirli bir öğeyi depolayamadığında atılır.</span><span class="sxs-lookup"><span data-stu-id="a0daf-108">Thrown when an array cannot store a given element because the actual type of the element is incompatible with the actual type of the array.</span></span>|  
|<xref:System.DivideByZeroException>|<span data-ttu-id="a0daf-109">İntegral değerini sıfıra bölmegirişiminde bulunulduğunda atılır.</span><span class="sxs-lookup"><span data-stu-id="a0daf-109">Thrown when an attempt is made to divide an integral value by zero.</span></span>|  
|<xref:System.IndexOutOfRangeException>|<span data-ttu-id="a0daf-110">Dizin sıfırdan küçükse veya dizinin sınırlarının dışında yken bir diziyi diziyi diziye dizidetme girişiminde bulunulduğunda atılır.</span><span class="sxs-lookup"><span data-stu-id="a0daf-110">Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.</span></span>|  
|<xref:System.InvalidCastException>|<span data-ttu-id="a0daf-111">Bir temel türden arabirime veya türetilmiş türe açık bir dönüştürme çalışma zamanında başarısız olduğunda atılır.</span><span class="sxs-lookup"><span data-stu-id="a0daf-111">Thrown when an explicit conversion from a base type to an interface or to a derived type fails at runtime.</span></span>|  
|<xref:System.NullReferenceException>|<span data-ttu-id="a0daf-112">Değeri [null](../../language-reference/keywords/null.md)olan bir nesneye başvuru yapmak için bir girişim yapıldığında atılan.</span><span class="sxs-lookup"><span data-stu-id="a0daf-112">Thrown when an attempt is made to reference an object whose value is [null](../../language-reference/keywords/null.md).</span></span>|  
|<xref:System.OutOfMemoryException>|<span data-ttu-id="a0daf-113">[Yeni](../../language-reference/operators/new-operator.md) işleci kullanarak bellek ayırma girişimi başarısız olduğunda atılır.</span><span class="sxs-lookup"><span data-stu-id="a0daf-113">Thrown when an attempt to allocate memory using the [new](../../language-reference/operators/new-operator.md) operator fails.</span></span> <span data-ttu-id="a0daf-114">Bu, ortak dil çalışma zamanı için kullanılabilir bellek tükendi gösterir.</span><span class="sxs-lookup"><span data-stu-id="a0daf-114">This indicates that the memory available to the common language runtime has been exhausted.</span></span>|  
|<xref:System.OverflowException>|<span data-ttu-id="a0daf-115">Bir `checked` bağlamda bir aritmetik işlem taştığında atılır.</span><span class="sxs-lookup"><span data-stu-id="a0daf-115">Thrown when an arithmetic operation in a `checked` context overflows.</span></span>|  
|<xref:System.StackOverflowException>|<span data-ttu-id="a0daf-116">Yürütme yığını çok fazla bekleyen yöntem çağrıları olan zaman atılır; genellikle çok derin veya sonsuz bir özyineleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="a0daf-116">Thrown when the execution stack is exhausted by having too many pending method calls; usually indicates a very deep or infinite recursion.</span></span>|  
|<xref:System.TypeInitializationException>|<span data-ttu-id="a0daf-117">Statik bir oluşturucu bir özel durum `catch` attığında ve onu yakalamak için uyumlu bir yan tümce olmadığında atılır.</span><span class="sxs-lookup"><span data-stu-id="a0daf-117">Thrown when a static constructor throws an exception and no compatible `catch` clause exists to catch it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a0daf-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0daf-118">See also</span></span>

- [<span data-ttu-id="a0daf-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a0daf-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a0daf-120">Özel Durumlar ve Özel Durum Kullanımı</span><span class="sxs-lookup"><span data-stu-id="a0daf-120">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="a0daf-121">Özel Durum Taşıma</span><span class="sxs-lookup"><span data-stu-id="a0daf-121">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="a0daf-122">try-catch</span><span class="sxs-lookup"><span data-stu-id="a0daf-122">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="a0daf-123">try-finally</span><span class="sxs-lookup"><span data-stu-id="a0daf-123">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="a0daf-124">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="a0daf-124">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
