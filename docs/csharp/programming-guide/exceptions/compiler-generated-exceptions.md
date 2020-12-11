---
title: Compiler-Generated özel durumları-C# Programlama Kılavuzu
description: Derleyicinin ürettiği özel durumlar hakkında bilgi edinin. Otomatik olarak oluşturulan özel durumların ve bunların hata koşullarının listesini gözden geçirin.
ms.date: 12/09/2020
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 43bacbb1025bc0af3a5f21979315b3d1b0d61066
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110357"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a><span data-ttu-id="28f29-104">Derleyicinin Ürettiği Özel Durumlar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="28f29-104">Compiler-Generated Exceptions (C# Programming Guide)</span></span>

<span data-ttu-id="28f29-105">Bazı özel durumlar, temel işlemler başarısız olduğunda .NET çalışma zamanı tarafından otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="28f29-105">Some exceptions are thrown automatically by the .NET runtime when basic operations fail.</span></span> <span data-ttu-id="28f29-106">Bu özel durumlar ve bunların hata koşulları aşağıdaki tabloda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="28f29-106">These exceptions and their error conditions are listed in the following table.</span></span>

|<span data-ttu-id="28f29-107">Özel durum</span><span class="sxs-lookup"><span data-stu-id="28f29-107">Exception</span></span>|<span data-ttu-id="28f29-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28f29-108">Description</span></span>|
|---------------|-----------------|
|<xref:System.ArithmeticException>|<span data-ttu-id="28f29-109">Ve gibi aritmetik işlemler sırasında oluşan özel durumlar için temel sınıf <xref:System.DivideByZeroException> <xref:System.OverflowException> .</span><span class="sxs-lookup"><span data-stu-id="28f29-109">A base class for exceptions that occur during arithmetic operations, such as <xref:System.DivideByZeroException> and <xref:System.OverflowException>.</span></span>|
|<xref:System.ArrayTypeMismatchException>|<span data-ttu-id="28f29-110">Öğenin gerçek türü dizinin gerçek türüyle uyumlu olmadığından, bir dizi belirli bir öğeyi depolayamadığı zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="28f29-110">Thrown when an array can't store a given element because the actual type of the element is incompatible with the actual type of the array.</span></span>|
|<xref:System.DivideByZeroException>|<span data-ttu-id="28f29-111">İntegral değeri sıfıra bölmek için bir deneme yapıldığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="28f29-111">Thrown when an attempt is made to divide an integral value by zero.</span></span>|
|<xref:System.IndexOutOfRangeException>|<span data-ttu-id="28f29-112">Dizin sıfırdan küçükse veya dizinin sınırları dışında bir diziyi dizinlemek için bir girişim yapıldığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="28f29-112">Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.</span></span>|
|<xref:System.InvalidCastException>|<span data-ttu-id="28f29-113">Temel türden bir arabirime ya da türetilmiş bir türe açık bir dönüştürme çalışma zamanında başarısız olduğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="28f29-113">Thrown when an explicit conversion from a base type to an interface or to a derived type fails at runtime.</span></span>|
|<xref:System.NullReferenceException>|<span data-ttu-id="28f29-114">Değeri [null](../../language-reference/keywords/null.md)olan bir nesneye başvuru yapıldığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="28f29-114">Thrown when an attempt is made to reference an object whose value is [null](../../language-reference/keywords/null.md).</span></span>|
|<xref:System.OutOfMemoryException>|<span data-ttu-id="28f29-115">[New](../../language-reference/operators/new-operator.md) işlecini kullanarak bellek ayırma girişimi başarısız olduğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="28f29-115">Thrown when an attempt to allocate memory using the [new](../../language-reference/operators/new-operator.md) operator fails.</span></span> <span data-ttu-id="28f29-116">Bu özel durum, ortak dil çalışma zamanı için kullanılabilir belleğin tükendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="28f29-116">This exception indicates that the memory available to the common language runtime has been exhausted.</span></span>|
|<xref:System.OverflowException>|<span data-ttu-id="28f29-117">`checked`Bağlamdaki aritmetik işlem taştığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="28f29-117">Thrown when an arithmetic operation in a `checked` context overflows.</span></span>|
|<xref:System.StackOverflowException>|<span data-ttu-id="28f29-118">Yürütme yığını çok fazla sayıda bekleyen Yöntem çağrısı ile tükendiğinde oluşturulur; genellikle çok derin veya sonsuz özyineleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="28f29-118">Thrown when the execution stack is exhausted by having too many pending method calls; usually indicates a very deep or infinite recursion.</span></span>|
|<xref:System.TypeInitializationException>|<span data-ttu-id="28f29-119">Statik bir Oluşturucu bir özel durum oluşturduğunda ve `catch` bunu yakalamak için uyumlu bir yan tümce yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="28f29-119">Thrown when a static constructor throws an exception and no compatible `catch` clause exists to catch it.</span></span>|

## <a name="see-also"></a><span data-ttu-id="28f29-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28f29-120">See also</span></span>

- [<span data-ttu-id="28f29-121">try-catch</span><span class="sxs-lookup"><span data-stu-id="28f29-121">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="28f29-122">try-finally</span><span class="sxs-lookup"><span data-stu-id="28f29-122">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="28f29-123">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="28f29-123">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
