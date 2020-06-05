---
title: Adlandırma Kuralları
description: Bu genel bakışta, çerçeve geliştirmede kullanılacak adlandırma kuralları hakkında bilgi edinin. Büyük/küçük harf, genel adlandırma ve diğer yönergeleri kapsayan makalelere gidin.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], about naming guidelines
- naming guidelines [.NET Framework]
- class library design guidelines [.NET Framework], names
- formatting [.NET Framework], names
- identifiers, class library element names
- names [.NET Framework]
- format naming guidelines [.NET Framework]
ms.assetid: fc076d66-9b5f-42d3-aa65-61d970c794a3
ms.openlocfilehash: fbcf5ef5eb02a5e45b5c981b4247ffe1c9c2631b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447153"
---
# <a name="naming-guidelines"></a><span data-ttu-id="042b5-104">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="042b5-104">Naming Guidelines</span></span>
<span data-ttu-id="042b5-105">Bir çerçeve geliştirmede tutarlı bir adlandırma kuralları kümesi takip etmek framework 'ün kullanılabilirlik açısından önemli bir katkı olabilir.</span><span class="sxs-lookup"><span data-stu-id="042b5-105">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="042b5-106">Framework 'ün yaygın olarak ayrılmış projeler üzerinde birçok geliştirici tarafından kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="042b5-106">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="042b5-107">Formun tutarlılığı ötesinde, Framework öğelerinin adları kolayca anlaşılmalıdır ve her bir öğenin işlevini iletmelidir.</span><span class="sxs-lookup"><span data-stu-id="042b5-107">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="042b5-108">Bu bölümün amacı, geliştiricilere anında anlam veren adlara neden olan tutarlı bir adlandırma kuralları kümesi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="042b5-108">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="042b5-109">Bu adlandırma kurallarını genel kod geliştirme yönergeleri olarak benimseme, kodunuzun tamamında daha tutarlı adlandırma oluşmasına neden olsa da, bunları yalnızca herkese açık olan API 'lere (ortak veya korumalı türler ve Üyeler ve açıkça uygulanan arabirimler) uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="042b5-109">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="042b5-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="042b5-110">In This Section</span></span>  
 [<span data-ttu-id="042b5-111">Büyük harfe dönüştürme kuralları</span><span class="sxs-lookup"><span data-stu-id="042b5-111">Capitalization Conventions</span></span>](capitalization-conventions.md)  
 [<span data-ttu-id="042b5-112">Genel adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="042b5-112">General Naming Conventions</span></span>](general-naming-conventions.md)  
 [<span data-ttu-id="042b5-113">Derlemelerin ve DLL 'Lerin adları</span><span class="sxs-lookup"><span data-stu-id="042b5-113">Names of Assemblies and DLLs</span></span>](names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="042b5-114">Ad alanlarının adları</span><span class="sxs-lookup"><span data-stu-id="042b5-114">Names of Namespaces</span></span>](names-of-namespaces.md)  
 [<span data-ttu-id="042b5-115">Sınıfların, yapıların ve arabirimlerin adları</span><span class="sxs-lookup"><span data-stu-id="042b5-115">Names of Classes, Structs, and Interfaces</span></span>](names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="042b5-116">Üye türü adları</span><span class="sxs-lookup"><span data-stu-id="042b5-116">Names of Type Members</span></span>](names-of-type-members.md)  
 [<span data-ttu-id="042b5-117">Adlandırma parametreleri</span><span class="sxs-lookup"><span data-stu-id="042b5-117">Naming Parameters</span></span>](naming-parameters.md)  
 [<span data-ttu-id="042b5-118">Kaynakları adlandırma</span><span class="sxs-lookup"><span data-stu-id="042b5-118">Naming Resources</span></span>](naming-resources.md)  
 <span data-ttu-id="042b5-119">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="042b5-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="042b5-120">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="042b5-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="042b5-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="042b5-121">See also</span></span>

- [<span data-ttu-id="042b5-122">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="042b5-122">Framework Design Guidelines</span></span>](index.md)
