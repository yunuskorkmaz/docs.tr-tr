---
title: Çerçeve Tasarım Yönergeleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 623391de63891c1695a63482a424bb76a861deba
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709315"
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="bebd3-102">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="bebd3-102">Framework Design Guidelines</span></span>
<span data-ttu-id="bebd3-103">Bu bölüm, .NET Framework genişleten ve etkileşime geçen kitaplıklar tasarlamak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bebd3-103">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="bebd3-104">Amaç, geliştirme için kullanılan programlama dilinden bağımsız bir Birleşik programlama modeli sunarak, kitaplık tasarımcılarının API tutarlılığını ve kullanım kolaylığını sağladığından yardım sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="bebd3-104">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="bebd3-105">.NET Framework genişleten sınıfları ve bileşenleri geliştirirken bu tasarım kılavuzlarını izlemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="bebd3-105">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="bebd3-106">Tutarsız kitaplık tasarımı, geliştirici üretkenliğini ve etkilenmeden benimsemesini olumsuz etkiler.</span><span class="sxs-lookup"><span data-stu-id="bebd3-106">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="bebd3-107">Yönergeler `Do`, `Consider`, `Avoid`ve `Do not`koşullara önek olarak basit öneriler olarak düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="bebd3-107">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="bebd3-108">Bu yönergeler, sınıf kitaplığı tasarımcılarının farklı çözümler arasındaki dengeleri anlamalarına yardımcı olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bebd3-108">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="bebd3-109">İyi kitaplık tasarımının bu tasarım kılavuzlarını ihlal etmeniz gerektiği durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="bebd3-109">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="bebd3-110">Bu tür durumlar nadir olmalıdır ve kararınız için açık ve ilgi çekici bir nedeniniz olması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="bebd3-110">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="bebd3-111">Bu yönergeler kitap *çerçevesi tasarım yönergelerinden alınmıştır: kurallar, deyimler ve yeniden kullanılabilir .NET kitaplıkları, 2. sürüm*, Vazysztof Cwalina ve atacan Abkms tarafından yapılır.</span><span class="sxs-lookup"><span data-stu-id="bebd3-111">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bebd3-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="bebd3-112">In This Section</span></span>  
 [<span data-ttu-id="bebd3-113">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="bebd3-113">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 <span data-ttu-id="bebd3-114">Derleme derlemeleri, ad alanları, türler ve sınıf kitaplıkları içindeki Üyeler için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bebd3-114">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="bebd3-115">Tür Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="bebd3-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 <span data-ttu-id="bebd3-116">Statik ve soyut sınıflar, arabirimler, numaralandırmalar, yapılar ve diğer türleri kullanmak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bebd3-116">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="bebd3-117">Üye Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="bebd3-117">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 <span data-ttu-id="bebd3-118">Özellikleri, yöntemleri, oluşturucuları, alanları, olayları, işleçleri ve parametreleri tasarlamak ve kullanmak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bebd3-118">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="bebd3-119">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="bebd3-119">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 <span data-ttu-id="bebd3-120">Olaylar, sanal üyeler ve geri çağırmalar kullanılarak altsınıflama gibi genişletilebilirlik mekanizmalarını açıklar ve çerçeve gereksinimlerinizi en iyi şekilde karşılayan mekanizmaların nasıl seçileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="bebd3-120">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="bebd3-121">Özel Durumlar için Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="bebd3-121">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)  
 <span data-ttu-id="bebd3-122">Özel durumları tasarlamak, oluşturmak ve yakalamak için tasarım yönergeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="bebd3-122">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="bebd3-123">Kullanım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="bebd3-123">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 <span data-ttu-id="bebd3-124">Diziler, öznitelikler ve Koleksiyonlar gibi ortak türleri kullanma, serileştirme destekleme ve eşitlik işleçlerini aşırı yükleme için yönergeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="bebd3-124">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="bebd3-125">Ortak Tasarım Desenleri</span><span class="sxs-lookup"><span data-stu-id="bebd3-125">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 <span data-ttu-id="bebd3-126">Bağımlılık özelliklerini seçme ve uygulama için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bebd3-126">Provides guidelines for choosing and implementing dependency properties.</span></span>  
  
 <span data-ttu-id="bebd3-127">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="bebd3-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="bebd3-128">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="bebd3-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bebd3-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bebd3-129">See also</span></span>

- [<span data-ttu-id="bebd3-130">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="bebd3-130">Overview</span></span>](../../../docs/framework/get-started/overview.md)
- [<span data-ttu-id="bebd3-131">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bebd3-131">Development Guide</span></span>](../../../docs/framework/development-guide.md)
