---
title: Uzantı Metotları
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6247b6d1718f43d4b05d585cc12a05c5e0cc2035
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="extension-methods"></a><span data-ttu-id="81fc9-102">Uzantı Metotları</span><span class="sxs-lookup"><span data-stu-id="81fc9-102">Extension Methods</span></span>
<span data-ttu-id="81fc9-103">Genişletme yöntemleri örnek yöntemi çağrı sözdizimini kullanarak çağrılması için statik yöntemler sağlayan bir dil özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="81fc9-103">Extension methods are a language feature that allows static methods to be called using instance method call syntax.</span></span> <span data-ttu-id="81fc9-104">Bu yöntemler üzerinde çalışılacak yöntemdir örneğini gösteren en az bir parametre almalıdır.</span><span class="sxs-lookup"><span data-stu-id="81fc9-104">These methods must take at least one parameter, which represents the instance the method is to operate on.</span></span>  
  
 <span data-ttu-id="81fc9-105">Bu tür genişletme yöntemlerini açıklar sınıfı "sponsoru" sınıf olarak adlandırılır ve static olarak bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="81fc9-105">The class that defines such extension methods is referred to as the "sponsor" class, and it must be declared as static.</span></span> <span data-ttu-id="81fc9-106">Genişletme yöntemleri kullanmak için bir sponsoru sınıfı tanımlayan ad alanı almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="81fc9-106">To use extension methods, one must import the namespace defining the sponsor class.</span></span>  
  
 <span data-ttu-id="81fc9-107">**KAÇININ x** frivolously genişletme yöntemleri, özellikle yok kendi türlerinde tanımlama.</span><span class="sxs-lookup"><span data-stu-id="81fc9-107">**X AVOID** frivolously defining extension methods, especially on types you don’t own.</span></span>  
  
 <span data-ttu-id="81fc9-108">Kaynak kodu türü sahipseniz, normal örnek yöntemleri kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="81fc9-108">If you do own source code of a type, consider using regular instance methods instead.</span></span> <span data-ttu-id="81fc9-109">Size ait olmayan ve bir yöntem eklemek istiyorsanız, çok dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="81fc9-109">If you don’t own, and you want to add a method, be very careful.</span></span> <span data-ttu-id="81fc9-110">Genişletme yöntemleri serbest kullanımını API'leri bu yöntemleri için tasarlanmamıştır türlerinin alanınızda karışıklık, olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="81fc9-110">Liberal use of extension methods has the potential of cluttering APIs of types that were not designed to have these methods.</span></span>  
  
 <span data-ttu-id="81fc9-111">**✓ DÜŞÜNÜN** genişletme yöntemleri aşağıdaki senaryolardan birini kullanarak:</span><span class="sxs-lookup"><span data-stu-id="81fc9-111">**✓ CONSIDER** using extension methods in any of the following scenarios:</span></span>  
  
-   <span data-ttu-id="81fc9-112">Yardımcı sağlamak için işlevselliği denirse, ilgili her bir arabirim uygulama için işlevselliği açısından çekirdek arabirimi yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="81fc9-112">To provide helper functionality relevant to every implementation of an interface, if said functionality can be written in terms of the core interface.</span></span> <span data-ttu-id="81fc9-113">Somut uygulamaları aksi arabirimlerine atanamaz olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="81fc9-113">This is because concrete implementations cannot otherwise be assigned to interfaces.</span></span> <span data-ttu-id="81fc9-114">Örneğin, `LINQ to Objects` işleçleri uzantı yöntemleri olarak tüm uygulanır <xref:System.Collections.Generic.IEnumerable%601> türleri.</span><span class="sxs-lookup"><span data-stu-id="81fc9-114">For example, the `LINQ to Objects` operators are implemented as extension methods for all <xref:System.Collections.Generic.IEnumerable%601> types.</span></span> <span data-ttu-id="81fc9-115">Bu nedenle, herhangi bir `IEnumerable<>` otomatik olarak LINQ etkin uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="81fc9-115">Thus, any `IEnumerable<>` implementation is automatically LINQ-enabled.</span></span>  
  
-   <span data-ttu-id="81fc9-116">Bir bağımlılık bazı türünde, ancak böyle bir bağımlılık örnek yöntemi zaman gösterebileceği bağımlılık Yönetimi kurallarını çalışmamasına neden.</span><span class="sxs-lookup"><span data-stu-id="81fc9-116">When an instance method would introduce a dependency on some type, but such a dependency would break dependency management rules.</span></span> <span data-ttu-id="81fc9-117">Örneğin, bir bağımlılık <xref:System.String> için <xref:System.Uri?displayProperty=nameWithType> arzu, büyük olasılıkla değil ve bu nedenle `String.ToUri()` döndüren örnek yöntemi `System.Uri` bağımlılık yönetim açısından yanlış tasarım olacaktır.</span><span class="sxs-lookup"><span data-stu-id="81fc9-117">For example, a dependency from <xref:System.String> to <xref:System.Uri?displayProperty=nameWithType> is probably not desirable, and so `String.ToUri()` instance method returning `System.Uri` would be the wrong design from a dependency management perspective.</span></span> <span data-ttu-id="81fc9-118">Statik genişletme yöntemi `Uri.ToUri(this string str)` döndüren `System.Uri` kadar daha iyi tasarım olacaktır.</span><span class="sxs-lookup"><span data-stu-id="81fc9-118">A static extension method `Uri.ToUri(this string str)` returning `System.Uri` would be a much better design.</span></span>  
  
 <span data-ttu-id="81fc9-119">**KAÇININ x** üzerinde genişletme yöntemleri tanımlama <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="81fc9-119">**X AVOID** defining extension methods on <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="81fc9-120">VB kullanıcılar tür yöntem uzantı yöntemi sözdizimini kullanarak nesne başvuruları üzerinde arayabilmesi için olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="81fc9-120">VB users will not be able to call such methods on object references using the extension method syntax.</span></span> <span data-ttu-id="81fc9-121">VB VB içinde nesne üzerinde geç olması için tüm yöntem çağrılarına zorlar gibi bir başvuru bildirme bağlı olduğundan, bu tür yöntemleri çağırma desteklemez (gerçek üye adlı çalışma zamanında belirlenir) bağlamaları genişletme yöntemleri için derleme zamanında (erken belirlenen sırada bağlı).</span><span class="sxs-lookup"><span data-stu-id="81fc9-121">VB does not support calling such methods because, in VB, declaring a reference as Object forces all method invocations on it to be late bound (actual member called is determined at runtime), while bindings to extension methods are determined at compile-time (early bound).</span></span>  
  
 <span data-ttu-id="81fc9-122">Kılavuz aynı bağlama davranışı mevcut olduğu veya nerede genişletme yöntemleri desteklenmez diğer diller için geçerli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="81fc9-122">Note that the guideline applies to other languages where the same binding behavior is present, or where extension methods are not supported.</span></span>  
  
 <span data-ttu-id="81fc9-123">**X yok** veya bağımlılık yönetimi yöntemleri arabirimlerine ekleme için olmadığı sürece, genişletilmiş türü aynı ad alanına genişletme yöntemleri uygulamak.</span><span class="sxs-lookup"><span data-stu-id="81fc9-123">**X DO NOT** put extension methods in the same namespace as the extended type unless it is for adding methods to interfaces or for dependency management.</span></span>  
  
 <span data-ttu-id="81fc9-124">**KAÇININ x** farklı ad alanlarında bulunuyorsa bile aynı imzayla iki veya daha fazla genişletme yöntemleri tanımlama.</span><span class="sxs-lookup"><span data-stu-id="81fc9-124">**X AVOID** defining two or more extension methods with the same signature, even if they reside in different namespaces.</span></span>  
  
 <span data-ttu-id="81fc9-125">**✓ DÜŞÜNÜN** türü bir arabirim ise ve çoğu veya tamamı durumlarda kullanılacak genişletme yöntemleri istediyseniz genişletilmiş türü olarak aynı ad alanında genişletme yöntemleri tanımlama.</span><span class="sxs-lookup"><span data-stu-id="81fc9-125">**✓ CONSIDER** defining extension methods in the same namespace as the extended type if the type is an interface and if the extension methods are meant to be used in most or all cases.</span></span>  
  
 <span data-ttu-id="81fc9-126">**X yok** normalde diğer özelliklerle ilişkili ad alanlarında bir özellik uygulama uzantı yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="81fc9-126">**X DO NOT** define extension methods implementing a feature in namespaces normally associated with other features.</span></span> <span data-ttu-id="81fc9-127">Bunun yerine, bunları ait özelliğiyle ilgili ad alanını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="81fc9-127">Instead, define them in the namespace associated with the feature they belong to.</span></span>  
  
 <span data-ttu-id="81fc9-128">**KAÇININ x** genel bir ad alanları adlandırma ayrılmış genişletme yöntemleri (örneğin, "uzantılarla").</span><span class="sxs-lookup"><span data-stu-id="81fc9-128">**X AVOID** generic naming of namespaces dedicated to extension methods (e.g., "Extensions").</span></span> <span data-ttu-id="81fc9-129">Açıklayıcı bir ad kullanın (örneğin, "yönlendirme") yerine.</span><span class="sxs-lookup"><span data-stu-id="81fc9-129">Use a descriptive name (e.g., "Routing") instead.</span></span>  
  
 <span data-ttu-id="81fc9-130">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="81fc9-130">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="81fc9-131">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="81fc9-131">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81fc9-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81fc9-132">See Also</span></span>  
 [<span data-ttu-id="81fc9-133">Üye Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="81fc9-133">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="81fc9-134">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="81fc9-134">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
