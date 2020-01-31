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
ms.openlocfilehash: 95aff35569e58eacfd064609140a29b53e0036da
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743820"
---
# <a name="naming-resources"></a><span data-ttu-id="872bd-102">Adlandırma Kaynakları</span><span class="sxs-lookup"><span data-stu-id="872bd-102">Naming Resources</span></span>
<span data-ttu-id="872bd-103">Yerelleştirilebilir kaynaklara, özellikler gibi belirli nesneler aracılığıyla başvurulabildiğinden, kaynaklarla ilgili adlandırma yönergeleri Özellik yönergelerine benzer.</span><span class="sxs-lookup"><span data-stu-id="872bd-103">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>

 <span data-ttu-id="872bd-104">✔️, kaynak anahtarlarında Pascalbüyük harfleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="872bd-104">✔️ DO use PascalCasing in resource keys.</span></span>

 <span data-ttu-id="872bd-105">✔️, kısa tanımlayıcılar yerine açıklayıcı bir ad sağlar.</span><span class="sxs-lookup"><span data-stu-id="872bd-105">✔️ DO provide descriptive rather than short identifiers.</span></span>

 <span data-ttu-id="872bd-106">❌ ana CLR dillerinin dile özgü anahtar sözcüklerini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="872bd-106">❌ DO NOT use language-specific keywords of the main CLR languages.</span></span>

 <span data-ttu-id="872bd-107">✔️, adlandırma kaynaklarında yalnızca alfasayısal karakterler ve alt çizgi kullanır.</span><span class="sxs-lookup"><span data-stu-id="872bd-107">✔️ DO use only alphanumeric characters and underscores in naming resources.</span></span>

 <span data-ttu-id="872bd-108">✔️, özel durum iletisi kaynakları için aşağıdaki adlandırma kuralını kullanır.</span><span class="sxs-lookup"><span data-stu-id="872bd-108">✔️ DO use the following naming convention for exception message resources.</span></span>

 <span data-ttu-id="872bd-109">Kaynak tanımlayıcısı, özel durum türü adı artı özel durumun kısa bir tanımlayıcısı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="872bd-109">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>

 <span data-ttu-id="872bd-110">`ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`</span><span class="sxs-lookup"><span data-stu-id="872bd-110">`ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`</span></span>
 `ArgumentExceptionFileNameIsMalformed`

 <span data-ttu-id="872bd-111">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="872bd-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="872bd-112">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="872bd-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="872bd-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="872bd-113">See also</span></span>

- [<span data-ttu-id="872bd-114">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="872bd-114">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="872bd-115">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="872bd-115">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
