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
ms.openlocfilehash: a558547f0e6770e7e76ca31f760d6e2f55c712db
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289791"
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="08b71-102">Özel Durumlar ve Performans</span><span class="sxs-lookup"><span data-stu-id="08b71-102">Exceptions and Performance</span></span>
<span data-ttu-id="08b71-103">Özel durumlarla ilgili yaygın bir sorun, düzenli olarak başarısız olan kod için özel durumlar kullanılıyorsa, uygulamanın performansının kabul edilemez olacağı bir konudur.</span><span class="sxs-lookup"><span data-stu-id="08b71-103">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="08b71-104">Bu, geçerli bir konudur.</span><span class="sxs-lookup"><span data-stu-id="08b71-104">This is a valid concern.</span></span> <span data-ttu-id="08b71-105">Bir üye özel durum oluşturduğunda, performansı daha yavaş olabilir.</span><span class="sxs-lookup"><span data-stu-id="08b71-105">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="08b71-106">Ancak, hata kodlarının kullanılmasına izin vermeyen özel durum yönergelerine tam olarak uyurken iyi bir performans elde etmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="08b71-106">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="08b71-107">Bu bölümde açıklanan iki desen bunu yapmak için yollar önerir.</span><span class="sxs-lookup"><span data-stu-id="08b71-107">Two patterns described in this section suggest ways to do this.</span></span>

 <span data-ttu-id="08b71-108">❌Özel durumların performansı olumsuz etkileyebilecek sorunlar nedeniyle hata kodlarını kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="08b71-108">❌ DO NOT use error codes because of concerns that exceptions might affect performance negatively.</span></span>

 <span data-ttu-id="08b71-109">Performansı artırmak için, sonraki iki bölümde açıklanan sınayıcı-doer deseninin veya TRY-Parse deseninin kullanılması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="08b71-109">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>

## <a name="tester-doer-pattern"></a><span data-ttu-id="08b71-110">Sınayıcı-doer stili</span><span class="sxs-lookup"><span data-stu-id="08b71-110">Tester-Doer Pattern</span></span>
 <span data-ttu-id="08b71-111">Bazen özel durum atma üyesinin performansı, üyenin iki içine bölünerek artırılabilir.</span><span class="sxs-lookup"><span data-stu-id="08b71-111">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="08b71-112"><xref:System.Collections.Generic.ICollection%601.Add%2A>Arabirimin yöntemine bakalım <xref:System.Collections.Generic.ICollection%601> .</span><span class="sxs-lookup"><span data-stu-id="08b71-112">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 <span data-ttu-id="08b71-113">`Add`Koleksiyon salt okunurdur, yöntemi atar.</span><span class="sxs-lookup"><span data-stu-id="08b71-113">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="08b71-114">Bu, yöntem çağrısının genellikle başarısız olması beklenen senaryolarda bir performans sorunu olabilir.</span><span class="sxs-lookup"><span data-stu-id="08b71-114">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="08b71-115">Sorunu hafifletmenin yöntemlerinden biri, bir değer eklemeye çalışmadan önce koleksiyonun yazılabilir olup olmadığını test eteklemektir.</span><span class="sxs-lookup"><span data-stu-id="08b71-115">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 <span data-ttu-id="08b71-116">Örneğimizde bir koşulu test etmek için kullanılan üye, `IsReadOnly` sınayıcı olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="08b71-116">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="08b71-117">Olası bir atma işlemini gerçekleştirmek için kullanılan üye, `Add` örneğimizdeki yöntemi, doer olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="08b71-117">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>

 <span data-ttu-id="08b71-118">✔️ özel durumlarla ilgili performans sorunlarından kaçınmak için ortak senaryolarda özel durumlar oluşturabilecek Üyeler için sınayıcı-doer modelini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="08b71-118">✔️ CONSIDER the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

## <a name="try-parse-pattern"></a><span data-ttu-id="08b71-119">TRY-Parse kriteri</span><span class="sxs-lookup"><span data-stu-id="08b71-119">Try-Parse Pattern</span></span>
 <span data-ttu-id="08b71-120">Son derece performansa duyarlı API 'Ler için, önceki bölümde açıklanan sınayıcı-doer deseninin daha da hızlı bir şekilde kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="08b71-120">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="08b71-121">Model, üye semantiğinin bir parçası olarak iyi tanımlanmış bir test çalışması yapmak için üye adını ayarlamayı çağırır.</span><span class="sxs-lookup"><span data-stu-id="08b71-121">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="08b71-122">Örneğin, <xref:System.DateTime> <xref:System.DateTime.Parse%2A> bir dizeyi ayrıştırma başarısız olursa özel durum oluşturan bir yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="08b71-122">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="08b71-123">Ayrıca <xref:System.DateTime.TryParse%2A> , ayrıştırmaya deneyen karşılık gelen bir yöntemi tanımlar, ancak ayrıştırma başarısız olursa false döndürür ve bir parametre kullanarak başarılı bir ayrıştırma sonucunu döndürür `out` .</span><span class="sxs-lookup"><span data-stu-id="08b71-123">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>

```csharp
public struct DateTime
{
    public static DateTime Parse(string dateTime)
    {
        ...
    }
    public static bool TryParse(string dateTime, out DateTime result)
    {
        ...
    }
}
```

 <span data-ttu-id="08b71-124">Bu model kullanılırken, TRY işlevlerini katı koşullarda tanımlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="08b71-124">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="08b71-125">Üye, iyi tanımlanmış deneme dışında herhangi bir nedenle başarısız olursa, üye yine de karşılık gelen bir özel durum oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="08b71-125">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>

 <span data-ttu-id="08b71-126">✔️ özel durumlarla ilgili performans sorunlarından kaçınmak için ortak senaryolarda özel durumlar oluşturabilecek Üyeler için TRY-Parse modelini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="08b71-126">✔️ CONSIDER the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

 <span data-ttu-id="08b71-127">✔️, bu kalıbı uygulayan yöntemler için "TRY" önekini ve Boole dönüş türünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="08b71-127">✔️ DO use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>

 <span data-ttu-id="08b71-128">✔️, TRY-Parse modelini kullanarak her üye için bir özel durum atma üyesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="08b71-128">✔️ DO provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>

 <span data-ttu-id="08b71-129">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="08b71-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="08b71-130">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="08b71-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="08b71-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08b71-131">See also</span></span>

- [<span data-ttu-id="08b71-132">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="08b71-132">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="08b71-133">Özel Durumlar için Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="08b71-133">Design Guidelines for Exceptions</span></span>](exceptions.md)
