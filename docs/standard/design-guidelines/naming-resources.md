---
title: "Adlandırma kaynakları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0387d820cc660bdf6cbafb9d76bbf0184c111881
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="naming-resources"></a><span data-ttu-id="6a1ef-102">Adlandırma kaynakları</span><span class="sxs-lookup"><span data-stu-id="6a1ef-102">Naming Resources</span></span>
<span data-ttu-id="6a1ef-103">Yerelleştirilebilir kaynaklar özellikleri değilmiş gibi belirli nesneleri başvurulabilir olduğundan kaynaklar için adlandırma kuralları özellik Kılavuzu benzerdir.</span><span class="sxs-lookup"><span data-stu-id="6a1ef-103">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>  
  
 <span data-ttu-id="6a1ef-104">**✓ YAPMAK** PascalCasing kaynak tuşlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a1ef-104">**✓ DO** use PascalCasing in resource keys.</span></span>  
  
 <span data-ttu-id="6a1ef-105">**✓ YAPMAK** yerine kısa tanımlayıcıları açıklayıcı sağlayın.</span><span class="sxs-lookup"><span data-stu-id="6a1ef-105">**✓ DO** provide descriptive rather than short identifiers.</span></span>  
  
 <span data-ttu-id="6a1ef-106">**X yok** ana CLR dillerin dile özgü anahtar sözcükler kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a1ef-106">**X DO NOT** use language-specific keywords of the main CLR languages.</span></span>  
  
 <span data-ttu-id="6a1ef-107">**✓ YAPMAK** yalnızca alfasayısal karakterler ve kaynakları adlandırma, alt çizgiler kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a1ef-107">**✓ DO** use only alphanumeric characters and underscores in naming resources.</span></span>  
  
 <span data-ttu-id="6a1ef-108">**✓ YAPMAK** özel durum iletisi kaynaklar için aşağıdaki adlandırma kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a1ef-108">**✓ DO** use the following naming convention for exception message resources.</span></span>  
  
 <span data-ttu-id="6a1ef-109">Kaynak tanımlayıcısı, özel durum türü adına ve özel durumun kısa bir tanımlayıcı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="6a1ef-109">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 <span data-ttu-id="6a1ef-110">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="6a1ef-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6a1ef-111">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="6a1ef-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a1ef-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6a1ef-112">See Also</span></span>  
 [<span data-ttu-id="6a1ef-113">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6a1ef-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="6a1ef-114">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="6a1ef-114">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
