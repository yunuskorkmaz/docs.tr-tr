---
title: Üye Tasarımı Yönergeleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
ms.openlocfilehash: cf4f1d2fee73e3e65dc4d92ea97a62f4a7e4c4e5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709276"
---
# <a name="member-design-guidelines"></a><span data-ttu-id="e4ddc-102">Üye Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e4ddc-102">Member Design Guidelines</span></span>
<span data-ttu-id="e4ddc-103">Yöntemler, özellikler, olaylar, oluşturucular ve alanlar topluca üye olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e4ddc-103">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="e4ddc-104">Üyeler, son olarak çerçeve işlevselliğinin bir çerçevenin son kullanıcılarına sunulduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e4ddc-104">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="e4ddc-105">Üyeler sanal veya sanal olmayan, somut veya soyut, statik veya örnek olabilir ve birçok farklı erişilebilirlik kapsamlarına sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4ddc-105">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="e4ddc-106">Tüm bu çok sayıda inanılmaz ifade sağlar, ancak aynı zamanda Framework Tasarımcısı 'nın parçası için dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4ddc-106">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="e4ddc-107">Bu bölümde, herhangi bir türde üye tasarlarken izlenmesi gereken temel yönergeler sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e4ddc-107">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e4ddc-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e4ddc-108">In This Section</span></span>  
 [<span data-ttu-id="e4ddc-109">Üye Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="e4ddc-109">Member Overloading</span></span>](../../../docs/standard/design-guidelines/member-overloading.md)  
 [<span data-ttu-id="e4ddc-110">Özellik Tasarımı</span><span class="sxs-lookup"><span data-stu-id="e4ddc-110">Property Design</span></span>](../../../docs/standard/design-guidelines/property.md)  
 [<span data-ttu-id="e4ddc-111">Oluşturucu Tasarımı</span><span class="sxs-lookup"><span data-stu-id="e4ddc-111">Constructor Design</span></span>](../../../docs/standard/design-guidelines/constructor.md)  
 [<span data-ttu-id="e4ddc-112">Olay Tasarımı</span><span class="sxs-lookup"><span data-stu-id="e4ddc-112">Event Design</span></span>](../../../docs/standard/design-guidelines/event.md)  
 [<span data-ttu-id="e4ddc-113">Alan Tasarımı</span><span class="sxs-lookup"><span data-stu-id="e4ddc-113">Field Design</span></span>](../../../docs/standard/design-guidelines/field.md)  
 [<span data-ttu-id="e4ddc-114">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="e4ddc-114">Extension Methods</span></span>](../../../docs/standard/design-guidelines/extension-methods.md)  
 [<span data-ttu-id="e4ddc-115">İşleç Aşırı Yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="e4ddc-115">Operator Overloads</span></span>](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [<span data-ttu-id="e4ddc-116">Parametre Tasarımı</span><span class="sxs-lookup"><span data-stu-id="e4ddc-116">Parameter Design</span></span>](../../../docs/standard/design-guidelines/parameter-design.md)  
 <span data-ttu-id="e4ddc-117">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="e4ddc-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e4ddc-118">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="e4ddc-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4ddc-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4ddc-119">See also</span></span>

- [<span data-ttu-id="e4ddc-120">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e4ddc-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
