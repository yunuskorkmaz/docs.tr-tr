---
title: Çerçeve Tasarım Yönergeleri
description: API tutarlılığı ve kullanım kolaylığını sağlamak üzere .NET ile genişleyen ve etkileşime geçen kitaplıklar tasarlamak için bkz. çerçeve tasarım yönergeleri.
titleSuffix: ''
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 17998adb1d18579f6763a80a82944e742e284e4e
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769073"
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="0d9b3-103">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0d9b3-103">Framework Design Guidelines</span></span>
<span data-ttu-id="0d9b3-104">Bu bölüm, .NET Framework genişleten ve etkileşime geçen kitaplıklar tasarlamak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d9b3-104">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="0d9b3-105">Amaç, geliştirme için kullanılan programlama dilinden bağımsız bir Birleşik programlama modeli sunarak, kitaplık tasarımcılarının API tutarlılığını ve kullanım kolaylığını sağladığından yardım sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="0d9b3-105">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="0d9b3-106">.NET Framework genişleten sınıfları ve bileşenleri geliştirirken bu tasarım kılavuzlarını izlemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="0d9b3-106">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="0d9b3-107">Tutarsız kitaplık tasarımı, geliştirici üretkenliğini ve etkilenmeden benimsemesini olumsuz etkiler.</span><span class="sxs-lookup"><span data-stu-id="0d9b3-107">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="0d9b3-108">Yönergeler,, ve koşulları ön eki olan basit öneriler olarak `Do` düzenlenir `Consider` `Avoid` `Do not` .</span><span class="sxs-lookup"><span data-stu-id="0d9b3-108">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="0d9b3-109">Bu yönergeler, sınıf kitaplığı tasarımcılarının farklı çözümler arasındaki dengeleri anlamalarına yardımcı olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0d9b3-109">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="0d9b3-110">İyi kitaplık tasarımının bu tasarım kılavuzlarını ihlal etmeniz gerektiği durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="0d9b3-110">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="0d9b3-111">Bu tür durumlar nadir olmalıdır ve kararınız için açık ve ilgi çekici bir nedeniniz olması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="0d9b3-111">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="0d9b3-112">Bu yönergeler kitap *çerçevesi tasarım yönergelerinden alınmıştır: kurallar, deyimler ve yeniden kullanılabilir .NET kitaplıkları, 2. sürüm*, Vazysztof Cwalina ve atacan Abkms tarafından yapılır.</span><span class="sxs-lookup"><span data-stu-id="0d9b3-112">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0d9b3-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0d9b3-113">In This Section</span></span>  
 [<span data-ttu-id="0d9b3-114">Adlandırma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0d9b3-114">Naming Guidelines</span></span>](naming-guidelines.md)  
 <span data-ttu-id="0d9b3-115">Derleme derlemeleri, ad alanları, türler ve sınıf kitaplıkları içindeki Üyeler için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d9b3-115">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="0d9b3-116">Tür tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0d9b3-116">Type Design Guidelines</span></span>](type.md)  
 <span data-ttu-id="0d9b3-117">Statik ve soyut sınıflar, arabirimler, numaralandırmalar, yapılar ve diğer türleri kullanmak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d9b3-117">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="0d9b3-118">Üye tasarımı yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0d9b3-118">Member Design Guidelines</span></span>](member.md)  
 <span data-ttu-id="0d9b3-119">Özellikleri, yöntemleri, oluşturucuları, alanları, olayları, işleçleri ve parametreleri tasarlamak ve kullanmak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d9b3-119">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="0d9b3-120">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="0d9b3-120">Designing for Extensibility</span></span>](designing-for-extensibility.md)  
 <span data-ttu-id="0d9b3-121">Olaylar, sanal üyeler ve geri çağırmalar kullanılarak altsınıflama gibi genişletilebilirlik mekanizmalarını açıklar ve çerçeve gereksinimlerinizi en iyi şekilde karşılayan mekanizmaların nasıl seçileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0d9b3-121">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="0d9b3-122">Özel Durumlar için Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0d9b3-122">Design Guidelines for Exceptions</span></span>](exceptions.md)  
 <span data-ttu-id="0d9b3-123">Özel durumları tasarlamak, oluşturmak ve yakalamak için tasarım yönergeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="0d9b3-123">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="0d9b3-124">Kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0d9b3-124">Usage Guidelines</span></span>](usage-guidelines.md)  
 <span data-ttu-id="0d9b3-125">Diziler, öznitelikler ve Koleksiyonlar gibi ortak türleri kullanma, serileştirme destekleme ve eşitlik işleçlerini aşırı yükleme için yönergeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="0d9b3-125">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="0d9b3-126">Ortak tasarım desenleri</span><span class="sxs-lookup"><span data-stu-id="0d9b3-126">Common Design Patterns</span></span>](common-design-patterns.md)  
 <span data-ttu-id="0d9b3-127">Bağımlılık özelliklerini seçme ve uygulama için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d9b3-127">Provides guidelines for choosing and implementing dependency properties.</span></span>  
  
 <span data-ttu-id="0d9b3-128">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="0d9b3-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="0d9b3-129">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="0d9b3-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d9b3-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d9b3-130">See also</span></span>

- [<span data-ttu-id="0d9b3-131">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0d9b3-131">Overview</span></span>](../../framework/get-started/overview.md)
- [<span data-ttu-id="0d9b3-132">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0d9b3-132">Development Guide</span></span>](../../framework/development-guide.md)
