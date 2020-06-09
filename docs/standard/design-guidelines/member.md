---
title: Üye Tasarımı Yönergeleri
description: .NET 'teki üye tasarımı kılavuzlarını öğrenin. Üyeler, Yöntemler, özellikler, olaylar, oluşturucular ve alanları içerir.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
ms.openlocfilehash: a1f0c1d74e8bffa7cfef975c7dafb9fd01479470
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594497"
---
# <a name="member-design-guidelines"></a><span data-ttu-id="9c97c-104">Üye Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9c97c-104">Member Design Guidelines</span></span>
<span data-ttu-id="9c97c-105">Yöntemler, özellikler, olaylar, oluşturucular ve alanlar topluca üye olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="9c97c-105">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="9c97c-106">Üyeler, son olarak çerçeve işlevselliğinin bir çerçevenin son kullanıcılarına sunulduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9c97c-106">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="9c97c-107">Üyeler sanal veya sanal olmayan, somut veya soyut, statik veya örnek olabilir ve birçok farklı erişilebilirlik kapsamlarına sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="9c97c-107">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="9c97c-108">Tüm bu çok sayıda inanılmaz ifade sağlar, ancak aynı zamanda Framework Tasarımcısı 'nın parçası için dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9c97c-108">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="9c97c-109">Bu bölümde, herhangi bir türde üye tasarlarken izlenmesi gereken temel yönergeler sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9c97c-109">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c97c-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9c97c-110">In This Section</span></span>  
 [<span data-ttu-id="9c97c-111">Üye aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="9c97c-111">Member Overloading</span></span>](member-overloading.md)  
 [<span data-ttu-id="9c97c-112">Özellik tasarımı</span><span class="sxs-lookup"><span data-stu-id="9c97c-112">Property Design</span></span>](property.md)  
 [<span data-ttu-id="9c97c-113">Oluşturucu tasarımı</span><span class="sxs-lookup"><span data-stu-id="9c97c-113">Constructor Design</span></span>](constructor.md)  
 [<span data-ttu-id="9c97c-114">Olay tasarımı</span><span class="sxs-lookup"><span data-stu-id="9c97c-114">Event Design</span></span>](event.md)  
 [<span data-ttu-id="9c97c-115">Alan tasarımı</span><span class="sxs-lookup"><span data-stu-id="9c97c-115">Field Design</span></span>](field.md)  
 [<span data-ttu-id="9c97c-116">Uzantı Metotları</span><span class="sxs-lookup"><span data-stu-id="9c97c-116">Extension Methods</span></span>](extension-methods.md)  
 [<span data-ttu-id="9c97c-117">İşleç aşırı yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="9c97c-117">Operator Overloads</span></span>](operator-overloads.md)  
 [<span data-ttu-id="9c97c-118">Parametre tasarımı</span><span class="sxs-lookup"><span data-stu-id="9c97c-118">Parameter Design</span></span>](parameter-design.md)  
 <span data-ttu-id="9c97c-119">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="9c97c-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9c97c-120">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="9c97c-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c97c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c97c-121">See also</span></span>

- [<span data-ttu-id="9c97c-122">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9c97c-122">Framework Design Guidelines</span></span>](index.md)
