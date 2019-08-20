---
title: Derleyicinin ürettiği özel durumlar- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: d0e0a304c8f7d77e7ba5c89b643fc5658c458558
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590360"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a><span data-ttu-id="29f84-102">Derleyicinin Ürettiği Özel Durumlar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="29f84-102">Compiler-Generated Exceptions (C# Programming Guide)</span></span>
<span data-ttu-id="29f84-103">Bazı özel durumlar, temel işlemler başarısız olduğunda .NET Framework ortak dil çalışma zamanı (CLR) tarafından otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="29f84-103">Some exceptions are thrown automatically by the .NET Framework's common language runtime (CLR) when basic operations fail.</span></span> <span data-ttu-id="29f84-104">Bu özel durumlar ve bunların hata koşulları aşağıdaki tabloda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="29f84-104">These exceptions and their error conditions are listed in the following table.</span></span>  
  
|<span data-ttu-id="29f84-105">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="29f84-105">Exception</span></span>|<span data-ttu-id="29f84-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29f84-106">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|<span data-ttu-id="29f84-107"><xref:System.DivideByZeroException> Ve<xref:System.OverflowException>gibi aritmetik işlemler sırasında oluşan özel durumlar için temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="29f84-107">A base class for exceptions that occur during arithmetic operations, such as <xref:System.DivideByZeroException> and <xref:System.OverflowException>.</span></span>|  
|<xref:System.ArrayTypeMismatchException>|<span data-ttu-id="29f84-108">Öğenin gerçek türü dizinin gerçek türüyle uyumlu olmadığından, bir dizi belirli bir öğeyi depolayamadığı zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="29f84-108">Thrown when an array cannot store a given element because the actual type of the element is incompatible with the actual type of the array.</span></span>|  
|<xref:System.DivideByZeroException>|<span data-ttu-id="29f84-109">İntegral değeri sıfıra bölmek için bir deneme yapıldığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="29f84-109">Thrown when an attempt is made to divide an integral value by zero.</span></span>|  
|<xref:System.IndexOutOfRangeException>|<span data-ttu-id="29f84-110">Dizin sıfırdan küçükse veya dizinin sınırları dışında bir diziyi dizinlemek için bir girişim yapıldığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="29f84-110">Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.</span></span>|  
|<xref:System.InvalidCastException>|<span data-ttu-id="29f84-111">Temel türden bir arabirime ya da türetilmiş bir türe açık bir dönüştürme çalışma zamanında başarısız olduğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="29f84-111">Thrown when an explicit conversion from a base type to an interface or to a derived type fails at runtime.</span></span>|  
|<xref:System.NullReferenceException>|<span data-ttu-id="29f84-112">Değeri [null](../../language-reference/keywords/null.md)olan bir nesneye başvuru yapmaya çalıştığınızda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="29f84-112">Thrown when you attempt to reference an object whose value is [null](../../language-reference/keywords/null.md).</span></span>|  
|<xref:System.OutOfMemoryException>|<span data-ttu-id="29f84-113">[New](../../language-reference/operators/new-operator.md) işlecini kullanarak bellek ayırma girişimi başarısız olduğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="29f84-113">Thrown when an attempt to allocate memory using the [new](../../language-reference/operators/new-operator.md) operator fails.</span></span> <span data-ttu-id="29f84-114">Bu, ortak dil çalışma zamanı için kullanılabilir belleğin tükendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="29f84-114">This indicates that the memory available to the common language runtime has been exhausted.</span></span>|  
|<xref:System.OverflowException>|<span data-ttu-id="29f84-115">`checked` Bağlamdaki aritmetik işlem taştığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="29f84-115">Thrown when an arithmetic operation in a `checked` context overflows.</span></span>|  
|<xref:System.StackOverflowException>|<span data-ttu-id="29f84-116">Yürütme yığını çok fazla sayıda bekleyen Yöntem çağrısı ile tükendiğinde oluşturulur; genellikle çok derin veya sonsuz özyineleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="29f84-116">Thrown when the execution stack is exhausted by having too many pending method calls; usually indicates a very deep or infinite recursion.</span></span>|  
|<xref:System.TypeInitializationException>|<span data-ttu-id="29f84-117">Statik bir Oluşturucu bir özel durum oluşturduğunda ve bunu yakalamak için `catch` uyumlu bir yan tümce yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="29f84-117">Thrown when a static constructor throws an exception and no compatible `catch` clause exists to catch it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29f84-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29f84-118">See also</span></span>

- [<span data-ttu-id="29f84-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="29f84-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="29f84-120">Özel Durumlar ve Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="29f84-120">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="29f84-121">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="29f84-121">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="29f84-122">try-catch</span><span class="sxs-lookup"><span data-stu-id="29f84-122">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="29f84-123">try-finally</span><span class="sxs-lookup"><span data-stu-id="29f84-123">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="29f84-124">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="29f84-124">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
