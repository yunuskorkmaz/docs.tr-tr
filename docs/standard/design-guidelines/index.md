---
title: Çerçeve Tasarım Yönergeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df2ccf3d778e26e16937554304ae847f624cfec0
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085646"
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="799cd-102">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="799cd-102">Framework Design Guidelines</span></span>
<span data-ttu-id="799cd-103">Bu bölüm, genişleten ve .NET Framework ile etkileşim kitaplıklar tasarlama için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="799cd-103">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="799cd-104">Bağımsız geliştirme için kullanılan programlama dili olan birleşik bir programlama modeli sağlayarak API tutarlığı ve kullanım kolaylığı sağlamak kitaplığı tasarımcıları yardımcı olmaktır.</span><span class="sxs-lookup"><span data-stu-id="799cd-104">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="799cd-105">Sınıfları ve genişleten .NET Framework bileşenleri geliştirirken bu tasarım ilkelerine uyun öneririz.</span><span class="sxs-lookup"><span data-stu-id="799cd-105">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="799cd-106">Tutarsız kitaplığı tasarım olumsuz geliştirici üretkenliğinizi etkiler ve benimseme gerçekleştirilmesini önler.</span><span class="sxs-lookup"><span data-stu-id="799cd-106">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="799cd-107">Kılavuzları basit önerileri şartlarını önek olarak düzenlenir `Do`, `Consider`, `Avoid`, ve `Do not`.</span><span class="sxs-lookup"><span data-stu-id="799cd-107">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="799cd-108">Bu yönergeleri, sınıf kitaplığı tasarımcıları farklı çözümler gereksinimlerimi karşılamama anlamanıza yardımcı olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="799cd-108">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="799cd-109">Bu tasarım yönergeleri ihlal iyi kitaplığı tasarım burada gerektirir durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="799cd-109">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="799cd-110">Bu gibi durumlarda nadiren olmalıdır ve kararınız için NET ve ilgi çekici bir neden olması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="799cd-110">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="799cd-111">Bu yönergeleri defterinden adlı çalışmasından *çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler*, Krzysztof Cwalina ve Brad Abrams.</span><span class="sxs-lookup"><span data-stu-id="799cd-111">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="799cd-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="799cd-112">In This Section</span></span>  
 [<span data-ttu-id="799cd-113">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="799cd-113">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 <span data-ttu-id="799cd-114">Derlemeler, ad alanları, türler ve üyeler sınıf kitaplıkları olarak adlandırmak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="799cd-114">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="799cd-115">Tür Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="799cd-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 <span data-ttu-id="799cd-116">Statik ve soyut sınıflar, arabirimler, numaralandırmalar, yapılar ve diğer türleri kullanma yönergeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="799cd-116">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="799cd-117">Üye Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="799cd-117">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 <span data-ttu-id="799cd-118">Tasarlama ve özellikleri, yöntemleri, Oluşturucular, alanlar, olaylar, işleçler ve parametreleri kullanma için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="799cd-118">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="799cd-119">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="799cd-119">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 <span data-ttu-id="799cd-120">Genişletilebilirlik mekanizması sınıflara, olayları ve sanal üyeleri geri çağırmalar gibi açıklanır ve seçin, framework'ün gereksinimlerini en iyi mekanizmalarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="799cd-120">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="799cd-121">Özel Durumlar için Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="799cd-121">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)  
 <span data-ttu-id="799cd-122">Tasarlama, oluşturma ve çalýþýrçalýþma yakalama özel durumlar için tasarım yönergeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="799cd-122">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="799cd-123">Kullanım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="799cd-123">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 <span data-ttu-id="799cd-124">Ortak bir türleri dizilerini, öznitelikleri ve koleksiyonları gibi kullanarak, serileştirme destekleme ve eşitlik işleçleri aşırı yükleme yönergeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="799cd-124">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="799cd-125">Ortak Tasarım Desenleri</span><span class="sxs-lookup"><span data-stu-id="799cd-125">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 <span data-ttu-id="799cd-126">Seçme ve bağımlılık özellikleri ve dispose deseni uygulamak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="799cd-126">Provides guidelines for choosing and implementing dependency properties and the dispose pattern.</span></span>  
  
 <span data-ttu-id="799cd-127">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="799cd-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="799cd-128">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="799cd-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="799cd-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="799cd-129">See also</span></span>

- [<span data-ttu-id="799cd-130">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="799cd-130">Overview</span></span>](../../../docs/framework/get-started/overview.md)  
- [<span data-ttu-id="799cd-131">.NET Framework için yol haritası</span><span class="sxs-lookup"><span data-stu-id="799cd-131">Roadmap for the .NET Framework</span></span>](https://msdn.microsoft.com/library/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)  
- [<span data-ttu-id="799cd-132">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="799cd-132">Development Guide</span></span>](../../../docs/framework/development-guide.md)
