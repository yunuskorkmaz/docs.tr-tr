---
title: Özellik Tasarım
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6dcb164daea6809f0d0e9c221f182d5019385bc1
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="property-design"></a><span data-ttu-id="bc390-102">Özellik Tasarım</span><span class="sxs-lookup"><span data-stu-id="bc390-102">Property Design</span></span>
<span data-ttu-id="bc390-103">Özellikler teknik olarak yöntemlere çok benzer olmakla birlikte, bunların kullanım senaryoları açısından oldukça farklı.</span><span class="sxs-lookup"><span data-stu-id="bc390-103">Although properties are technically very similar to methods, they are quite different in terms of their usage scenarios.</span></span> <span data-ttu-id="bc390-104">Akıllı alanlar olarak görülmelidir.</span><span class="sxs-lookup"><span data-stu-id="bc390-104">They should be seen as smart fields.</span></span> <span data-ttu-id="bc390-105">Alanları arama söz dizimi ve yöntemleri esnekliğini sahiptirler.</span><span class="sxs-lookup"><span data-stu-id="bc390-105">They have the calling syntax of fields, and the flexibility of methods.</span></span>  
  
 <span data-ttu-id="bc390-106">**✓ YAPMAK** çağıran özelliğin değerini değiştirmek açmaması gereken, yalnızca get özellikleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bc390-106">**✓ DO** create get-only properties if the caller should not be able to change the value of the property.</span></span>  
  
 <span data-ttu-id="bc390-107">Olması durumunda türünü unutmayın özelliği kesilebilir başvuru türü, özellik değeri yalnızca get olsa bile özellik değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="bc390-107">Keep in mind that if the type of the property is a mutable reference type, the property value can be changed even if the property is get-only.</span></span>  
  
 <span data-ttu-id="bc390-108">**X yok** alıcı daha geniş erişilebilirlik sahip ayarlayıcı yalnızca küme özellikleri veya özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc390-108">**X DO NOT** provide set-only properties or properties with the setter having broader accessibility than the getter.</span></span>  
  
 <span data-ttu-id="bc390-109">Örneğin, özellikler, ortak bir Ayarlayıcısı ve korumalı bir alıcı ile kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="bc390-109">For example, do not use properties with a public setter and a protected getter.</span></span>  
  
 <span data-ttu-id="bc390-110">Özellik alıcısı sağlanamaz, bunun yerine işlevi bir yöntem olarak uygular.</span><span class="sxs-lookup"><span data-stu-id="bc390-110">If the property getter cannot be provided, implement the functionality as a method instead.</span></span> <span data-ttu-id="bc390-111">Yöntem adı ile başlayan göz önünde bulundurun `Set` ve ne özelliği adlı ile izleyin.</span><span class="sxs-lookup"><span data-stu-id="bc390-111">Consider starting the method name with `Set` and follow with what you would have named the property.</span></span> <span data-ttu-id="bc390-112">Örneğin, <xref:System.AppDomain> sahip olarak adlandırılan bir yöntem `SetCachePath` adlı yalnızca kümesi özelliğine sahip yerine `CachePath`.</span><span class="sxs-lookup"><span data-stu-id="bc390-112">For example, <xref:System.AppDomain> has a method called `SetCachePath` instead of having a set-only property called `CachePath`.</span></span>  
  
 <span data-ttu-id="bc390-113">**✓ YAPMAK** tüm özellikleri, varsayılan bir güvenlik açığı veya çok verimsiz kodu yol açmamasını sağlamak için duyarlı varsayılan değerler sağlayın.</span><span class="sxs-lookup"><span data-stu-id="bc390-113">**✓ DO** provide sensible default values for all properties, ensuring that the defaults do not result in a security hole or terribly inefficient code.</span></span>  
  
 <span data-ttu-id="bc390-114">**✓ YAPMAK** bu nesne bir geçici geçersiz durumda sonuçları olsa bile herhangi bir sırada ayarlanacak özellikler izin verir.</span><span class="sxs-lookup"><span data-stu-id="bc390-114">**✓ DO** allow properties to be set in any order even if this results in a temporary invalid state of the object.</span></span>  
  
 <span data-ttu-id="bc390-115">Diğer özelliklerin değerlerine aynı nesne üzerinde verilen burada bir özelliğin bazı değerler geçersiz olabilir bir noktasına birbiriyle ilişkili olarak iki veya daha fazla özellik yaygındır.</span><span class="sxs-lookup"><span data-stu-id="bc390-115">It is common for two or more properties to be interrelated to a point where some values of one property might be invalid given the values of other properties on the same object.</span></span> <span data-ttu-id="bc390-116">Birbiriyle ilişkili özellikler gerçekte birlikte nesne tarafından kullanılan kadar bu gibi durumlarda, özel durumlar geçersiz durumdan kaynaklanan Ertelenen.</span><span class="sxs-lookup"><span data-stu-id="bc390-116">In such cases, exceptions resulting from the invalid state should be postponed until the interrelated properties are actually used together by the object.</span></span>  
  
 <span data-ttu-id="bc390-117">**✓ YAPMAK** özellik set yordamı bir özel durum oluşturursa önceki değeri korumak.</span><span class="sxs-lookup"><span data-stu-id="bc390-117">**✓ DO** preserve the previous value if a property setter throws an exception.</span></span>  
  
 <span data-ttu-id="bc390-118">**KAÇININ x** özellik alıcıları özel durumları atma.</span><span class="sxs-lookup"><span data-stu-id="bc390-118">**X AVOID** throwing exceptions from property getters.</span></span>  
  
 <span data-ttu-id="bc390-119">Özellik alıcıları basit işlemler olmalıdır ve tüm önkoşullara sahip olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc390-119">Property getters should be simple operations and should not have any preconditions.</span></span> <span data-ttu-id="bc390-120">Bir alıcı bir özel durum, bir yöntem için büyük olasılıkla tasarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc390-120">If a getter can throw an exception, it should probably be redesigned to be a method.</span></span> <span data-ttu-id="bc390-121">Bu kural dizin oluşturucular, bağımsız değişkenler doğrulama sonucu olarak özel durumlar burada bekliyoruz uygulanmaz dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="bc390-121">Notice that this rule does not apply to indexers, where we do expect exceptions as a result of validating the arguments.</span></span>  
  
### <a name="indexed-property-design"></a><span data-ttu-id="bc390-122">Dizin oluşturulmuş özellik Tasarım</span><span class="sxs-lookup"><span data-stu-id="bc390-122">Indexed Property Design</span></span>  
 <span data-ttu-id="bc390-123">Dizinli bir özelliği, parametreleri ve bir dizi dizin oluşturma için benzer özel bir sözdizimi ile çağrılabilir özel bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="bc390-123">An indexed property is a special property that can have parameters and can be called with special syntax similar to array indexing.</span></span>  
  
 <span data-ttu-id="bc390-124">Dizinli Özellikler, yaygın olarak dizin oluşturucular da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="bc390-124">Indexed properties are commonly referred to as indexers.</span></span> <span data-ttu-id="bc390-125">Dizin Oluşturucular, mantıksal bir koleksiyondaki öğelerin erişim sağlayan API'lerde kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc390-125">Indexers should be used only in APIs that provide access to items in a logical collection.</span></span> <span data-ttu-id="bc390-126">Örneğin, bir dizeyi karakter ve oluşturucuda koleksiyonudur <xref:System.String?displayProperty=nameWithType> kendi karakter erişmek için eklendi.</span><span class="sxs-lookup"><span data-stu-id="bc390-126">For example, a string is a collection of characters, and the indexer on <xref:System.String?displayProperty=nameWithType> was added to access its characters.</span></span>  
  
 <span data-ttu-id="bc390-127">**✓ DÜŞÜNÜN** iç dizisinde depolanan verilere erişim sağlamak için dizin oluşturucular kullanma.</span><span class="sxs-lookup"><span data-stu-id="bc390-127">**✓ CONSIDER** using indexers to provide access to data stored in an internal array.</span></span>  
  
 <span data-ttu-id="bc390-128">**✓ DÜŞÜNÜN** öğe koleksiyonunu temsil eden türlerinde dizin oluşturucular sağlama.</span><span class="sxs-lookup"><span data-stu-id="bc390-128">**✓ CONSIDER** providing indexers on types representing collections of items.</span></span>  
  
 <span data-ttu-id="bc390-129">**KAÇININ x** dizin oluşturulmuş özellikleri birden fazla parametresiyle kullanarak.</span><span class="sxs-lookup"><span data-stu-id="bc390-129">**X AVOID** using indexed properties with more than one parameter.</span></span>  
  
 <span data-ttu-id="bc390-130">Tasarım birden çok parametre gerektiriyorsa, özellik, bir erişimci gerçekten mantıksal bir koleksiyonu temsil eder. olup olmadığını alan.</span><span class="sxs-lookup"><span data-stu-id="bc390-130">If the design requires multiple parameters, reconsider whether the property really represents an accessor to a logical collection.</span></span> <span data-ttu-id="bc390-131">Yoksa, bunun yerine yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc390-131">If it does not, use methods instead.</span></span> <span data-ttu-id="bc390-132">Yöntem adı ile başlayan göz önünde bulundurun `Get` veya `Set`.</span><span class="sxs-lookup"><span data-stu-id="bc390-132">Consider starting the method name with `Get` or `Set`.</span></span>  
  
 <span data-ttu-id="bc390-133">**KAÇININ x** dışında parametre türleri oluşturucularla <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, veya enum.</span><span class="sxs-lookup"><span data-stu-id="bc390-133">**X AVOID** indexers with parameter types other than <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, or an enum.</span></span>  
  
 <span data-ttu-id="bc390-134">Tasarım diğer türleri parametre gerektiriyorsa, API, erişimci gerçekten mantıksal bir koleksiyonu temsil eder. olup olmadığını kesinlikle yeniden.</span><span class="sxs-lookup"><span data-stu-id="bc390-134">If the design requires other types of parameters, strongly reevaluate whether the API really represents an accessor to a logical collection.</span></span> <span data-ttu-id="bc390-135">Yoksa, bir yöntem kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc390-135">If it does not, use a method.</span></span> <span data-ttu-id="bc390-136">Yöntem adı ile başlayan göz önünde bulundurun `Get` veya `Set`.</span><span class="sxs-lookup"><span data-stu-id="bc390-136">Consider starting the method name with `Get` or `Set`.</span></span>  
  
 <span data-ttu-id="bc390-137">**✓ YAPMAK** adını kullanın `Item` için tabii daha iyi bir adı olmadıkça özellikleri dizine (örn., bkz: <xref:System.String.Chars%2A> özellikte `System.String`).</span><span class="sxs-lookup"><span data-stu-id="bc390-137">**✓ DO** use the name `Item` for indexed properties unless there is an obviously better name (e.g., see the <xref:System.String.Chars%2A> property on `System.String`).</span></span>  
  
 <span data-ttu-id="bc390-138">C# ' ta dizin oluşturucular öğesi adlı varsayılan olarak gelir.</span><span class="sxs-lookup"><span data-stu-id="bc390-138">In C#, indexers are by default named Item.</span></span> <span data-ttu-id="bc390-139"><xref:System.Runtime.CompilerServices.IndexerNameAttribute> Bu adını özelleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc390-139">The <xref:System.Runtime.CompilerServices.IndexerNameAttribute> can be used to customize this name.</span></span>  
  
 <span data-ttu-id="bc390-140">**X yok** hem bir dizin oluşturucu hem de anlam olarak eşdeğerdir yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc390-140">**X DO NOT** provide both an indexer and methods that are semantically equivalent.</span></span>  
  
 <span data-ttu-id="bc390-141">**X yok** aşırı yüklenmiş dizin oluşturucular bir türde birden fazla ailesi sağlayın.</span><span class="sxs-lookup"><span data-stu-id="bc390-141">**X DO NOT** provide more than one family of overloaded indexers in one type.</span></span>  
  
 <span data-ttu-id="bc390-142">Bu, C# Derleyici tarafından zorlanır.</span><span class="sxs-lookup"><span data-stu-id="bc390-142">This is enforced by the C# compiler.</span></span>  
  
 <span data-ttu-id="bc390-143">**X yok** kullanım varsayılan olmayan dizin oluşturulmuş özellikleri.</span><span class="sxs-lookup"><span data-stu-id="bc390-143">**X DO NOT** use nondefault indexed properties.</span></span>  
  
 <span data-ttu-id="bc390-144">Bu, C# Derleyici tarafından zorlanır.</span><span class="sxs-lookup"><span data-stu-id="bc390-144">This is enforced by the C# compiler.</span></span>  
  
### <a name="property-change-notification-events"></a><span data-ttu-id="bc390-145">Özellik değişikliği bildirim olayı</span><span class="sxs-lookup"><span data-stu-id="bc390-145">Property Change Notification Events</span></span>  
 <span data-ttu-id="bc390-146">Bazen bir özellik değeri değişiklikleri kullanıcı bildiren bir olay sağlamak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="bc390-146">Sometimes it is useful to provide an event notifying the user of changes in a property value.</span></span> <span data-ttu-id="bc390-147">Örneğin, `System.Windows.Forms.Control` başlatır bir `TextChanged` olayından sonra değerini kendi `Text` özelliği değişti.</span><span class="sxs-lookup"><span data-stu-id="bc390-147">For example, `System.Windows.Forms.Control` raises a `TextChanged` event after the value of its `Text` property has changed.</span></span>  
  
 <span data-ttu-id="bc390-148">**✓ DÜŞÜNÜN** değişiklik üst düzey API'leri (genellikle Tasarımcı bileşenleri) özellik değerlerinde değişiklik yapıldığında bildirim olayları oluşturma.</span><span class="sxs-lookup"><span data-stu-id="bc390-148">**✓ CONSIDER** raising change notification events when property values in high-level APIs (usually designer components) are modified.</span></span>  
  
 <span data-ttu-id="bc390-149">Bir kullanıcının ne zaman bir nesnenin bir özelliğini değiştirme bilmek iyi bir senaryo ise, nesnenin bir özellik için bir değişiklik bildirimi olayı tetiklemelidir.</span><span class="sxs-lookup"><span data-stu-id="bc390-149">If there is a good scenario for a user to know when a property of an object is changing, the object should raise a change notification event for the property.</span></span>  
  
 <span data-ttu-id="bc390-150">Ancak, temel türleri veya koleksiyon gibi alt düzey API'ler için bu gibi olaylar yükseltmek için ek yükü değerinde olması olası değil.</span><span class="sxs-lookup"><span data-stu-id="bc390-150">However, it is unlikely to be worth the overhead to raise such events for low-level APIs such as base types or collections.</span></span> <span data-ttu-id="bc390-151">Örneğin, <xref:System.Collections.Generic.List%601> listesine yeni bir öğe eklendiğinde bu gibi olaylar oluşturmaz ve `Count` özellik değişikliği.</span><span class="sxs-lookup"><span data-stu-id="bc390-151">For example, <xref:System.Collections.Generic.List%601> would not raise such events when a new item is added to the list and the `Count` property changes.</span></span>  
  
 <span data-ttu-id="bc390-152">**✓ DÜŞÜNÜN** değişiklik bir özelliğin değerini dış zorlar değiştiğinde bildirim olayları oluşturma.</span><span class="sxs-lookup"><span data-stu-id="bc390-152">**✓ CONSIDER** raising change notification events when the value of a property changes via external forces.</span></span>  
  
 <span data-ttu-id="bc390-153">Bazı dış yürürlükte (nesne üzerinde yöntemleri çağırarak bir yol dışında) aracılığıyla bir özellik değeri değişiklikleri olursa olayları belirtmek için geliştirici değeri değişen ve değişti.</span><span class="sxs-lookup"><span data-stu-id="bc390-153">If a property value changes via some external force (in a way other than by calling methods on the object), raise events indicate to the developer that the value is changing and has changed.</span></span> <span data-ttu-id="bc390-154">İyi bir örnektir `Text` metin kutusu denetiminin özelliği.</span><span class="sxs-lookup"><span data-stu-id="bc390-154">A good example is the `Text` property of a text box control.</span></span> <span data-ttu-id="bc390-155">Ne zaman kullanıcı türleri metinde bir `TextBox`, özellik değeri otomatik olarak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bc390-155">When the user types text in a `TextBox`, the property value automatically changes.</span></span>  
  
 <span data-ttu-id="bc390-156">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="bc390-156">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="bc390-157">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="bc390-157">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc390-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bc390-158">See Also</span></span>  
 [<span data-ttu-id="bc390-159">Üye Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="bc390-159">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="bc390-160">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="bc390-160">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
