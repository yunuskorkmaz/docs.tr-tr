---
title: Derleyicinin ürettiği özel durumlar-C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 1d2d561df3e496893657b050fa93b44c56542d97
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240739"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a><span data-ttu-id="b6fc3-102">Derleyicinin Ürettiği Özel Durumlar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b6fc3-102">Compiler-Generated Exceptions (C# Programming Guide)</span></span>

<span data-ttu-id="b6fc3-103">Bazı özel durumlar, temel işlemler başarısız olduğunda .NET çalışma zamanı tarafından otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b6fc3-103">Some exceptions are thrown automatically by the .NET runtime when basic operations fail.</span></span> <span data-ttu-id="b6fc3-104">Bu özel durumlar ve bunların hata koşulları aşağıdaki tabloda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="b6fc3-104">These exceptions and their error conditions are listed in the following table.</span></span>  
  
|<span data-ttu-id="b6fc3-105">Özel durum</span><span class="sxs-lookup"><span data-stu-id="b6fc3-105">Exception</span></span>|<span data-ttu-id="b6fc3-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6fc3-106">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|<span data-ttu-id="b6fc3-107">Ve gibi aritmetik işlemler sırasında oluşan özel durumlar için temel sınıf <xref:System.DivideByZeroException> <xref:System.OverflowException> .</span><span class="sxs-lookup"><span data-stu-id="b6fc3-107">A base class for exceptions that occur during arithmetic operations, such as <xref:System.DivideByZeroException> and <xref:System.OverflowException>.</span></span>|  
|<xref:System.ArrayTypeMismatchException>|<span data-ttu-id="b6fc3-108">Öğenin gerçek türü dizinin gerçek türüyle uyumlu olmadığından, bir dizi belirli bir öğeyi depolayamadığı zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b6fc3-108">Thrown when an array cannot store a given element because the actual type of the element is incompatible with the actual type of the array.</span></span>|  
|<xref:System.DivideByZeroException>|<span data-ttu-id="b6fc3-109">İntegral değeri sıfıra bölmek için bir deneme yapıldığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b6fc3-109">Thrown when an attempt is made to divide an integral value by zero.</span></span>|  
|<xref:System.IndexOutOfRangeException>|<span data-ttu-id="b6fc3-110">Dizin sıfırdan küçükse veya dizinin sınırları dışında bir diziyi dizinlemek için bir girişim yapıldığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b6fc3-110">Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.</span></span>|  
|<xref:System.InvalidCastException>|<span data-ttu-id="b6fc3-111">Temel türden bir arabirime ya da türetilmiş bir türe açık bir dönüştürme çalışma zamanında başarısız olduğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b6fc3-111">Thrown when an explicit conversion from a base type to an interface or to a derived type fails at runtime.</span></span>|  
|<xref:System.NullReferenceException>|<span data-ttu-id="b6fc3-112">Değeri [null](../../language-reference/keywords/null.md)olan bir nesneye başvuru yapıldığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b6fc3-112">Thrown when an attempt is made to reference an object whose value is [null](../../language-reference/keywords/null.md).</span></span>|  
|<xref:System.OutOfMemoryException>|<span data-ttu-id="b6fc3-113">[New](../../language-reference/operators/new-operator.md) işlecini kullanarak bellek ayırma girişimi başarısız olduğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b6fc3-113">Thrown when an attempt to allocate memory using the [new](../../language-reference/operators/new-operator.md) operator fails.</span></span> <span data-ttu-id="b6fc3-114">Bu, ortak dil çalışma zamanı için kullanılabilir belleğin tükendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6fc3-114">This indicates that the memory available to the common language runtime has been exhausted.</span></span>|  
|<xref:System.OverflowException>|<span data-ttu-id="b6fc3-115">`checked`Bağlamdaki aritmetik işlem taştığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b6fc3-115">Thrown when an arithmetic operation in a `checked` context overflows.</span></span>|  
|<xref:System.StackOverflowException>|<span data-ttu-id="b6fc3-116">Yürütme yığını çok fazla sayıda bekleyen Yöntem çağrısı ile tükendiğinde oluşturulur; genellikle çok derin veya sonsuz özyineleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6fc3-116">Thrown when the execution stack is exhausted by having too many pending method calls; usually indicates a very deep or infinite recursion.</span></span>|  
|<xref:System.TypeInitializationException>|<span data-ttu-id="b6fc3-117">Statik bir Oluşturucu bir özel durum oluşturduğunda ve `catch` bunu yakalamak için uyumlu bir yan tümce yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b6fc3-117">Thrown when a static constructor throws an exception and no compatible `catch` clause exists to catch it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b6fc3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6fc3-118">See also</span></span>

- [<span data-ttu-id="b6fc3-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b6fc3-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b6fc3-120">Özel Durumlar ve Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="b6fc3-120">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="b6fc3-121">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="b6fc3-121">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="b6fc3-122">try-catch</span><span class="sxs-lookup"><span data-stu-id="b6fc3-122">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="b6fc3-123">try-finally</span><span class="sxs-lookup"><span data-stu-id="b6fc3-123">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="b6fc3-124">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="b6fc3-124">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
