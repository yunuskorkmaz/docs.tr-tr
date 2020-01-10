---
title: Adlandırma Kaynakları
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
ms.openlocfilehash: b64a3ef6e12f8ea1abf7efd9c22f2f4333dda5c8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709172"
---
# <a name="naming-resources"></a><span data-ttu-id="c4a1f-102">Adlandırma Kaynakları</span><span class="sxs-lookup"><span data-stu-id="c4a1f-102">Naming Resources</span></span>
<span data-ttu-id="c4a1f-103">Yerelleştirilebilir kaynaklara, özellikler gibi belirli nesneler aracılığıyla başvurulabildiğinden, kaynaklarla ilgili adlandırma yönergeleri Özellik yönergelerine benzer.</span><span class="sxs-lookup"><span data-stu-id="c4a1f-103">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>  
  
 <span data-ttu-id="c4a1f-104">**✓ DO** PascalCasing kaynak tuşlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4a1f-104">**✓ DO** use PascalCasing in resource keys.</span></span>  
  
 <span data-ttu-id="c4a1f-105">**✓ DO** yerine kısa tanımlayıcıları açıklayıcı sağlayın.</span><span class="sxs-lookup"><span data-stu-id="c4a1f-105">**✓ DO** provide descriptive rather than short identifiers.</span></span>  
  
 <span data-ttu-id="c4a1f-106">**X DO NOT** ana CLR dillerin dile özgü anahtar sözcükler kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4a1f-106">**X DO NOT** use language-specific keywords of the main CLR languages.</span></span>  
  
 <span data-ttu-id="c4a1f-107">**✓ DO** yalnızca alfasayısal karakterler ve kaynakları adlandırma, alt çizgiler kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4a1f-107">**✓ DO** use only alphanumeric characters and underscores in naming resources.</span></span>  
  
 <span data-ttu-id="c4a1f-108">**✓ DO** özel durum iletisi kaynaklar için aşağıdaki adlandırma kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4a1f-108">**✓ DO** use the following naming convention for exception message resources.</span></span>  
  
 <span data-ttu-id="c4a1f-109">Kaynak tanımlayıcısı, özel durum türü adı artı özel durumun kısa bir tanımlayıcısı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="c4a1f-109">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 <span data-ttu-id="c4a1f-110">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="c4a1f-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="c4a1f-111">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="c4a1f-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4a1f-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4a1f-112">See also</span></span>

- [<span data-ttu-id="c4a1f-113">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c4a1f-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="c4a1f-114">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="c4a1f-114">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
