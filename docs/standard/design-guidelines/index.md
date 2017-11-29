---
title: "Framework tasarım yönergeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a812207fb58e6c87c263966081060d02f8038963
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="2f455-102">Framework tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2f455-102">Framework Design Guidelines</span></span>
<span data-ttu-id="2f455-103">Bu bölüm, genişletme ve .NET Framework ile etkileşim kitaplıkları tasarlamak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f455-103">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="2f455-104">Hedef kitaplığı tasarımcıları geliştirme için kullanılan programlama dili bağımsızdır birleşik bir programlama modeli sağlayarak API tutarlılık ve kullanım kolaylığı olun yardımcı olmaktır.</span><span class="sxs-lookup"><span data-stu-id="2f455-104">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="2f455-105">Sınıfları ve .NET Framework genişleten bileşenleri geliştirirken, aşağıdaki tasarım yönergelere uymanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="2f455-105">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="2f455-106">Tutarsız kitaplık tasarımı olumsuz Geliştirici üretkenliği etkiler ve benimseme zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="2f455-106">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="2f455-107">Yönergeler koşulları önekli basit öneriler olarak düzenlenir `Do`, `Consider`, `Avoid`, ve `Do not`.</span><span class="sxs-lookup"><span data-stu-id="2f455-107">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="2f455-108">Bu yönergeleri sınıf kitaplığı tasarımcıları dengelemeler farklı çözümler arasında anlamanıza yardımcı olmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2f455-108">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="2f455-109">Bu tasarım yönergeleri ihlal iyi kitaplık tasarımı burada gerektirir durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="2f455-109">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="2f455-110">Bu gibi durumlarda seyrek olmalıdır ve kararınızı NET ve ilgi çekici bir nedeni olması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2f455-110">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="2f455-111">Bu yönergeleri Defteri'nden adlı çalışmasından *Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri*, Krzysztof Cwalina ve Brad Abrams göre.</span><span class="sxs-lookup"><span data-stu-id="2f455-111">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2f455-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2f455-112">In This Section</span></span>  
 [<span data-ttu-id="2f455-113">Adlandırma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2f455-113">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 <span data-ttu-id="2f455-114">Derlemeler, ad alanlarını, türleri ve sınıf kitaplıkları üyelerinde adlandırmak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f455-114">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="2f455-115">Türü tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2f455-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 <span data-ttu-id="2f455-116">Statik ve soyut sınıflar, arabirimler, numaralandırmalar, yapılar ve diğer türleri kullanma yönergeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f455-116">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="2f455-117">Üye tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2f455-117">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 <span data-ttu-id="2f455-118">Tasarlama ve özellikleri, yöntemleri, Oluşturucular, alanlar, olaylar, işleçler ve parametreleri kullanma için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f455-118">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="2f455-119">Genişletilebilirlik için tasarlama</span><span class="sxs-lookup"><span data-stu-id="2f455-119">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 <span data-ttu-id="2f455-120">Olaylar, sanal üyeleri ve geri çağırmalar kullanarak sınıflara gibi genişletilebilirlik mekanizmaları açıklanır ve framework'ün gereksinimlerini en iyi karşılayan mekanizmaları seçin açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2f455-120">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="2f455-121">Özel durumlar için tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2f455-121">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)  
 <span data-ttu-id="2f455-122">Tasarlama, atma ve çalýþýrçalýþma yakalama özel durumlar için tasarım yönergeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="2f455-122">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="2f455-123">Kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2f455-123">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 <span data-ttu-id="2f455-124">Diziler, öznitelikleri ve koleksiyonları gibi ortak türlerini kullanarak, serileştirme destekleme ve eşitlik işleçleri aşırı yükleme yönergelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="2f455-124">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="2f455-125">Ortak tasarım desenleri</span><span class="sxs-lookup"><span data-stu-id="2f455-125">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 <span data-ttu-id="2f455-126">Seçme ve bağımlılık özellikleri ve dispose desen uygulamak için kılavuz bilgiler verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2f455-126">Provides guidelines for choosing and implementing dependency properties and the dispose pattern.</span></span>  
  
 <span data-ttu-id="2f455-127">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="2f455-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="2f455-128">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="2f455-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f455-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2f455-129">See Also</span></span>  
 [<span data-ttu-id="2f455-130">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="2f455-130">Overview</span></span>](../../../docs/framework/get-started/overview.md)  
 [<span data-ttu-id="2f455-131">.NET Framework için yol haritası</span><span class="sxs-lookup"><span data-stu-id="2f455-131">Roadmap for the .NET Framework</span></span>](http://msdn.microsoft.com/en-us/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)  
 [<span data-ttu-id="2f455-132">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2f455-132">Development Guide</span></span>](../../../docs/framework/development-guide.md)
