---
title: Özel Durumlar ve Performans
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
author: KrzysztofCwalina
ms.openlocfilehash: f9fe3045d8bd8b4d625c5cd49bc18574ebb740de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026438"
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="2093f-102">Özel Durumlar ve Performans</span><span class="sxs-lookup"><span data-stu-id="2093f-102">Exceptions and Performance</span></span>
<span data-ttu-id="2093f-103">Özel durumlar için ilgili bir sık karşılaşılan özel durumlar için düzenli olarak başarısız kodu kullandıysanız, uygulama performansını kabul edilemez olduğunu konusudur.</span><span class="sxs-lookup"><span data-stu-id="2093f-103">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="2093f-104">Bu geçerli bir konudur.</span><span class="sxs-lookup"><span data-stu-id="2093f-104">This is a valid concern.</span></span> <span data-ttu-id="2093f-105">Üye bir özel durum oluşturduğunda, kendi performans kat daha yavaş olabilir.</span><span class="sxs-lookup"><span data-stu-id="2093f-105">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="2093f-106">Ancak, hata kodlarını kullanarak izin vermeyin. özel durum yönergeleri kesinlikle bağlılığı sırasında iyi performans elde etmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="2093f-106">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="2093f-107">Bu bölümde açıklanan iki deseni, bunu yapmak için yöntemler önerir.</span><span class="sxs-lookup"><span data-stu-id="2093f-107">Two patterns described in this section suggest ways to do this.</span></span>  
  
 <span data-ttu-id="2093f-108">**X DO NOT** özel durumlar performansı olumsuz etkileyebilir sorunları nedeniyle hata kodları kullanın.</span><span class="sxs-lookup"><span data-stu-id="2093f-108">**X DO NOT** use error codes because of concerns that exceptions might affect performance negatively.</span></span>  
  
 <span data-ttu-id="2093f-109">Performansı artırmak için test edici Doer desen veya deneyin-Parse sonraki iki bölümde açıklanan düzeni kullanmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="2093f-109">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>  
  
## <a name="tester-doer-pattern"></a><span data-ttu-id="2093f-110">Test edici Doer düzeni</span><span class="sxs-lookup"><span data-stu-id="2093f-110">Tester-Doer Pattern</span></span>  
 <span data-ttu-id="2093f-111">Bazen bir özel durum atma üye performansını üye ikiye bölerek geliştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2093f-111">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="2093f-112">Bakalım <xref:System.Collections.Generic.ICollection%601.Add%2A> yöntemi <xref:System.Collections.Generic.ICollection%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="2093f-112">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 <span data-ttu-id="2093f-113">Yöntem `Add` koleksiyonu salt okunur ise oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2093f-113">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="2093f-114">Bu yöntem çağrısında burada sık sık başarısız beklenmektedir senaryolarda bir performans sorunu olabilir.</span><span class="sxs-lookup"><span data-stu-id="2093f-114">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="2093f-115">Sorunu azaltmak için yollarla değer eklemek denemeden önce koleksiyona yazılabilir olup olmadığını sınamak için biridir.</span><span class="sxs-lookup"><span data-stu-id="2093f-115">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 <span data-ttu-id="2093f-116">Bizim örneğimizde, özellik koşulunu test etmek için kullanılan bir üye `IsReadOnly`, test edici adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2093f-116">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="2093f-117">Olası oluşturma bir işlemi gerçekleştirmek için kullanılan bir üye `Add` yöntemi örneğimizde doer adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2093f-117">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>  
  
 <span data-ttu-id="2093f-118">**✓ CONSIDER** Tester Doer düzeni özel durumlar oluşturma üyeleri için özel durumlar ortak senaryolar performans sorunlarını önlemek için ilgili.</span><span class="sxs-lookup"><span data-stu-id="2093f-118">**✓ CONSIDER** the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
## <a name="try-parse-pattern"></a><span data-ttu-id="2093f-119">Try-ayrıştırma desenindeki</span><span class="sxs-lookup"><span data-stu-id="2093f-119">Try-Parse Pattern</span></span>  
 <span data-ttu-id="2093f-120">Son derece performans açısından duyarlı API'leri için önceki bölümde açıklanan test edici Doer düzeni daha daha hızlı bir desen kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2093f-120">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="2093f-121">Desen, bir üye semantiği parçası case iyi tanımlanmış bir test yapmak için üye adı ayarlamak için çağırır.</span><span class="sxs-lookup"><span data-stu-id="2093f-121">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="2093f-122">Örneğin, <xref:System.DateTime> tanımlayan bir <xref:System.DateTime.Parse%2A> yöntemi bir dizeyi ayrıştırma başarısız olursa, bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2093f-122">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="2093f-123">Ayrıca, karşılık gelen tanımlar <xref:System.DateTime.TryParse%2A> ayrıştırmak için çalışır yöntemi ancak false döndürürse ayrıştırma başarısız ve başarılı ayrıştırma kullanarak bir sonuç döndürür bir `out` parametresi.</span><span class="sxs-lookup"><span data-stu-id="2093f-123">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>  
  
```  
public struct DateTime {  
    public static DateTime Parse(string dateTime){   
        ...   
    }  
    public static bool TryParse(string dateTime, out DateTime result){  
        ...  
    }  
}  
```  
  
 <span data-ttu-id="2093f-124">Bu model kullanılırken, try işlevi katı koşullarını tanımlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2093f-124">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="2093f-125">Üye, iyi tanımlanmış try dışındaki herhangi bir nedenle başarısız olursa, üye karşılık gelen bir özel durum throw gerekir.</span><span class="sxs-lookup"><span data-stu-id="2093f-125">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>  
  
 <span data-ttu-id="2093f-126">**✓ CONSIDER** deneyin ayrıştırma düzeni özel durumlar oluşturma üyeleri için özel durumlar ortak senaryolar performans sorunlarını önlemek için ilgili.</span><span class="sxs-lookup"><span data-stu-id="2093f-126">**✓ CONSIDER** the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
 <span data-ttu-id="2093f-127">**✓ DO** bu düzeni uygulama yöntemleri için "Deneme" ve Boolean dönüş türü önekini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2093f-127">**✓ DO** use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>  
  
 <span data-ttu-id="2093f-128">**✓ DO** deneyin ayrıştırma desenini kullanarak her üyesi için bir özel durum atma üye sağlayın.</span><span class="sxs-lookup"><span data-stu-id="2093f-128">**✓ DO** provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>  
  
 <span data-ttu-id="2093f-129">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="2093f-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="2093f-130">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*</span><span class="sxs-lookup"><span data-stu-id="2093f-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2093f-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2093f-131">See also</span></span>

- [<span data-ttu-id="2093f-132">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2093f-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="2093f-133">Özel Durumlar için Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2093f-133">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
