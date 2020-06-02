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
ms.openlocfilehash: 762ba99c4751ba40f5f33e99455cf950af35cdf6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290155"
---
# <a name="naming-resources"></a><span data-ttu-id="cf6e2-102">Adlandırma Kaynakları</span><span class="sxs-lookup"><span data-stu-id="cf6e2-102">Naming Resources</span></span>
<span data-ttu-id="cf6e2-103">Yerelleştirilebilir kaynaklara, özellikler gibi belirli nesneler aracılığıyla başvurulabildiğinden, kaynaklarla ilgili adlandırma yönergeleri Özellik yönergelerine benzer.</span><span class="sxs-lookup"><span data-stu-id="cf6e2-103">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>

 <span data-ttu-id="cf6e2-104">✔️, kaynak anahtarlarında Pascalbüyük harfleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="cf6e2-104">✔️ DO use PascalCasing in resource keys.</span></span>

 <span data-ttu-id="cf6e2-105">✔️, kısa tanımlayıcılar yerine açıklayıcı bir ad sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf6e2-105">✔️ DO provide descriptive rather than short identifiers.</span></span>

 <span data-ttu-id="cf6e2-106">❌Ana CLR dillerinin dile özgü anahtar sözcüklerini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="cf6e2-106">❌ DO NOT use language-specific keywords of the main CLR languages.</span></span>

 <span data-ttu-id="cf6e2-107">✔️, adlandırma kaynaklarında yalnızca alfasayısal karakterler ve alt çizgi kullanır.</span><span class="sxs-lookup"><span data-stu-id="cf6e2-107">✔️ DO use only alphanumeric characters and underscores in naming resources.</span></span>

 <span data-ttu-id="cf6e2-108">✔️, özel durum iletisi kaynakları için aşağıdaki adlandırma kuralını kullanır.</span><span class="sxs-lookup"><span data-stu-id="cf6e2-108">✔️ DO use the following naming convention for exception message resources.</span></span>

 <span data-ttu-id="cf6e2-109">Kaynak tanımlayıcısı, özel durum türü adı artı özel durumun kısa bir tanımlayıcısı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="cf6e2-109">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>

 <span data-ttu-id="cf6e2-110">`ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`</span><span class="sxs-lookup"><span data-stu-id="cf6e2-110">`ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`</span></span>
 `ArgumentExceptionFileNameIsMalformed`

 <span data-ttu-id="cf6e2-111">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="cf6e2-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="cf6e2-112">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="cf6e2-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="cf6e2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf6e2-113">See also</span></span>

- [<span data-ttu-id="cf6e2-114">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="cf6e2-114">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="cf6e2-115">Adlandırma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="cf6e2-115">Naming Guidelines</span></span>](naming-guidelines.md)
