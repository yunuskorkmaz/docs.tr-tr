---
title: "Özel durumları ve performans"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9a876a818086e0d54251f53a1e8f83cc74a574ae
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="23b98-102">Özel durumları ve performans</span><span class="sxs-lookup"><span data-stu-id="23b98-102">Exceptions and Performance</span></span>
<span data-ttu-id="23b98-103">Özel durumlar için ilgili bir ortak özel durumlar için düzenli olarak başarısız kodu kullandıysanız, uygulama performansını kabul edilemez olduğunu konusudur.</span><span class="sxs-lookup"><span data-stu-id="23b98-103">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="23b98-104">Bu geçerli bir konudur.</span><span class="sxs-lookup"><span data-stu-id="23b98-104">This is a valid concern.</span></span> <span data-ttu-id="23b98-105">Üye bir özel durum oluşturduğunda, kendi performansını büyüklük yavaş olabilir.</span><span class="sxs-lookup"><span data-stu-id="23b98-105">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="23b98-106">Ancak, kesinlikle hata kodlarını kullanarak izin vermeyecek özel durum yönergelerine uymak sırasında iyi performans elde etmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="23b98-106">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="23b98-107">Bu bölümde açıklanan iki desenleri Bunu yapmak için yöntemler önerir.</span><span class="sxs-lookup"><span data-stu-id="23b98-107">Two patterns described in this section suggest ways to do this.</span></span>  
  
 <span data-ttu-id="23b98-108">**X yok** özel durumlar performansı olumsuz etkileyebilir sorunları nedeniyle hata kodları kullanın.</span><span class="sxs-lookup"><span data-stu-id="23b98-108">**X DO NOT** use error codes because of concerns that exceptions might affect performance negatively.</span></span>  
  
 <span data-ttu-id="23b98-109">Performansı artırmak için Tester Doer desen veya deneyin ayrıştırma sonraki iki bölümde açıklanan düzeni kullanmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="23b98-109">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>  
  
## <a name="tester-doer-pattern"></a><span data-ttu-id="23b98-110">Tester Doer düzeni</span><span class="sxs-lookup"><span data-stu-id="23b98-110">Tester-Doer Pattern</span></span>  
 <span data-ttu-id="23b98-111">Bazen bir özel durum atma üye performansını üye ikiye bölerek geliştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="23b98-111">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="23b98-112">Bakalım <xref:System.Collections.Generic.ICollection%601.Add%2A> yöntemi <xref:System.Collections.Generic.ICollection%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="23b98-112">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 <span data-ttu-id="23b98-113">Yöntem `Add` koleksiyon salt okunur ise oluşturur.</span><span class="sxs-lookup"><span data-stu-id="23b98-113">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="23b98-114">Bu yöntem çağrısının sık sık başarısız olmasına beklenirken senaryolarda bir performans sorunu olabilir.</span><span class="sxs-lookup"><span data-stu-id="23b98-114">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="23b98-115">Sorunu çözmek için yollardan değer eklemek denemeden önce koleksiyona yazılabilir olup olmadığını sınamak için biridir.</span><span class="sxs-lookup"><span data-stu-id="23b98-115">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 <span data-ttu-id="23b98-116">Özelliği, örneğimizde bir koşulu test etmek için kullanılan üye `IsReadOnly`, tester adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="23b98-116">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="23b98-117">Olası oluşturma işlemi gerçekleştirmek için kullanılan üye `Add` örneğimizde yöntemi doer adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="23b98-117">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>  
  
 <span data-ttu-id="23b98-118">**✓ DÜŞÜNÜN** Tester Doer düzeni özel durumlar oluşturma üyeleri için özel durumlar ortak senaryolar performans sorunlarını önlemek için ilgili.</span><span class="sxs-lookup"><span data-stu-id="23b98-118">**✓ CONSIDER** the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
## <a name="try-parse-pattern"></a><span data-ttu-id="23b98-119">Try-ayrıştırma düzeni</span><span class="sxs-lookup"><span data-stu-id="23b98-119">Try-Parse Pattern</span></span>  
 <span data-ttu-id="23b98-120">Son derece performans duyarlı API'ler, önceki bölümde açıklanan Tester Doer düzeni daha daha hızlı bir desen kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="23b98-120">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="23b98-121">Üye semantiğini parçası durumda iyi tanımlanmış bir test yapmak için üye adı ayarlamak için desen çağırır.</span><span class="sxs-lookup"><span data-stu-id="23b98-121">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="23b98-122">Örneğin, <xref:System.DateTime> tanımlayan bir <xref:System.DateTime.Parse%2A> yöntemi dizesi ayrıştırma başarısız olursa, bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="23b98-122">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="23b98-123">Ayrıca bir karşılık gelen tanımlar <xref:System.DateTime.TryParse%2A> ayrıştırmak için çalışır yöntemi ancak yanlış döndürür ayrıştırma başarısız olur ve bir başarılı ayrıştırma kullanmanın sonucu döndürürse bir `out` parametresi.</span><span class="sxs-lookup"><span data-stu-id="23b98-123">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>  
  
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
  
 <span data-ttu-id="23b98-124">Bu deseni kullanılırken deneyin işlevselliği katı koşullarını tanımlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="23b98-124">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="23b98-125">Üye iyi tanımlanmış deneyin dışındaki herhangi bir nedenle başarısız olursa, üye karşılık gelen bir özel durum gerekir.</span><span class="sxs-lookup"><span data-stu-id="23b98-125">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>  
  
 <span data-ttu-id="23b98-126">**✓ DÜŞÜNÜN** deneyin ayrıştırma düzeni özel durumlar oluşturma üyeleri için özel durumlar ortak senaryolar performans sorunlarını önlemek için ilgili.</span><span class="sxs-lookup"><span data-stu-id="23b98-126">**✓ CONSIDER** the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
 <span data-ttu-id="23b98-127">**✓ YAPMAK** bu düzeni uygulama yöntemleri için "Deneme" ve Boolean dönüş türü önekini kullanın.</span><span class="sxs-lookup"><span data-stu-id="23b98-127">**✓ DO** use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>  
  
 <span data-ttu-id="23b98-128">**✓ YAPMAK** deneyin ayrıştırma desenini kullanarak her üyesi için bir özel durum atma üye sağlayın.</span><span class="sxs-lookup"><span data-stu-id="23b98-128">**✓ DO** provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>  
  
 <span data-ttu-id="23b98-129">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="23b98-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="23b98-130">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="23b98-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23b98-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="23b98-131">See Also</span></span>  
 [<span data-ttu-id="23b98-132">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="23b98-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="23b98-133">Özel Durumlar için Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="23b98-133">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
