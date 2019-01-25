---
title: Adlandırma kaynakları
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
author: KrzysztofCwalina
ms.openlocfilehash: 44627aafd9ec779625413a0862412a8f6c408109
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497611"
---
# <a name="naming-resources"></a><span data-ttu-id="9a53c-102">Adlandırma kaynakları</span><span class="sxs-lookup"><span data-stu-id="9a53c-102">Naming Resources</span></span>
<span data-ttu-id="9a53c-103">Yerelleştirilebilir kaynaklar özellikleri değilmiş gibi belirli nesneler başvurulabilir olduğundan kaynakları için adlandırma kuralları için özellik kılavuzları benzerdir.</span><span class="sxs-lookup"><span data-stu-id="9a53c-103">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>  
  
 <span data-ttu-id="9a53c-104">**✓ DO** PascalCasing kaynak tuşlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="9a53c-104">**✓ DO** use PascalCasing in resource keys.</span></span>  
  
 <span data-ttu-id="9a53c-105">**✓ DO** yerine kısa tanımlayıcıları açıklayıcı sağlayın.</span><span class="sxs-lookup"><span data-stu-id="9a53c-105">**✓ DO** provide descriptive rather than short identifiers.</span></span>  
  
 <span data-ttu-id="9a53c-106">**X DO NOT** ana CLR dillerin dile özgü anahtar sözcükler kullanın.</span><span class="sxs-lookup"><span data-stu-id="9a53c-106">**X DO NOT** use language-specific keywords of the main CLR languages.</span></span>  
  
 <span data-ttu-id="9a53c-107">**✓ DO** yalnızca alfasayısal karakterler ve kaynakları adlandırma, alt çizgiler kullanın.</span><span class="sxs-lookup"><span data-stu-id="9a53c-107">**✓ DO** use only alphanumeric characters and underscores in naming resources.</span></span>  
  
 <span data-ttu-id="9a53c-108">**✓ DO** özel durum iletisi kaynaklar için aşağıdaki adlandırma kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="9a53c-108">**✓ DO** use the following naming convention for exception message resources.</span></span>  
  
 <span data-ttu-id="9a53c-109">Kaynak tanımlayıcısı, özel durum türü adına ve özel durumun kısa bir tanımlayıcı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="9a53c-109">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 <span data-ttu-id="9a53c-110">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="9a53c-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9a53c-111">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*</span><span class="sxs-lookup"><span data-stu-id="9a53c-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a53c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a53c-112">See also</span></span>

- [<span data-ttu-id="9a53c-113">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9a53c-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="9a53c-114">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="9a53c-114">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
