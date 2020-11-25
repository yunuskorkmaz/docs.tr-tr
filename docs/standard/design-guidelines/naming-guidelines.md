---
title: Adlandırma Kuralları
description: Bu genel bakışta, çerçeve geliştirmede kullanılacak adlandırma kuralları hakkında bilgi edinin. Büyük/küçük harf, genel adlandırma ve diğer yönergeleri kapsayan makalelere gidin.
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], about naming guidelines
- naming guidelines [.NET Framework]
- class library design guidelines [.NET Framework], names
- formatting [.NET Framework], names
- identifiers, class library element names
- names [.NET Framework]
- format naming guidelines [.NET Framework]
ms.assetid: fc076d66-9b5f-42d3-aa65-61d970c794a3
ms.openlocfilehash: de68eeb287b13bc9f55230243f23cd03508f2561
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706430"
---
# <a name="naming-guidelines"></a><span data-ttu-id="96f3f-104">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="96f3f-104">Naming Guidelines</span></span>

<span data-ttu-id="96f3f-105">Bir çerçeve geliştirmede tutarlı bir adlandırma kuralları kümesi takip etmek framework 'ün kullanılabilirlik açısından önemli bir katkı olabilir.</span><span class="sxs-lookup"><span data-stu-id="96f3f-105">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="96f3f-106">Framework 'ün yaygın olarak ayrılmış projeler üzerinde birçok geliştirici tarafından kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="96f3f-106">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="96f3f-107">Formun tutarlılığı ötesinde, Framework öğelerinin adları kolayca anlaşılmalıdır ve her bir öğenin işlevini iletmelidir.</span><span class="sxs-lookup"><span data-stu-id="96f3f-107">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="96f3f-108">Bu bölümün amacı, geliştiricilere anında anlam veren adlara neden olan tutarlı bir adlandırma kuralları kümesi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="96f3f-108">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="96f3f-109">Bu adlandırma kurallarını genel kod geliştirme yönergeleri olarak benimseme, kodunuzun tamamında daha tutarlı adlandırma oluşmasına neden olsa da, bunları yalnızca herkese açık olan API 'lere (ortak veya korumalı türler ve Üyeler ve açıkça uygulanan arabirimler) uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="96f3f-109">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="96f3f-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="96f3f-110">In This Section</span></span>  

 [<span data-ttu-id="96f3f-111">Büyük harfe dönüştürme kuralları</span><span class="sxs-lookup"><span data-stu-id="96f3f-111">Capitalization Conventions</span></span>](capitalization-conventions.md)  
 [<span data-ttu-id="96f3f-112">Genel adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="96f3f-112">General Naming Conventions</span></span>](general-naming-conventions.md)  
 [<span data-ttu-id="96f3f-113">Derlemelerin ve DLL 'Lerin adları</span><span class="sxs-lookup"><span data-stu-id="96f3f-113">Names of Assemblies and DLLs</span></span>](names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="96f3f-114">Ad alanlarının adları</span><span class="sxs-lookup"><span data-stu-id="96f3f-114">Names of Namespaces</span></span>](names-of-namespaces.md)  
 [<span data-ttu-id="96f3f-115">Sınıfların, yapıların ve arabirimlerin adları</span><span class="sxs-lookup"><span data-stu-id="96f3f-115">Names of Classes, Structs, and Interfaces</span></span>](names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="96f3f-116">Üye türü adları</span><span class="sxs-lookup"><span data-stu-id="96f3f-116">Names of Type Members</span></span>](names-of-type-members.md)  
 [<span data-ttu-id="96f3f-117">Adlandırma parametreleri</span><span class="sxs-lookup"><span data-stu-id="96f3f-117">Naming Parameters</span></span>](naming-parameters.md)  
 [<span data-ttu-id="96f3f-118">Kaynakları adlandırma</span><span class="sxs-lookup"><span data-stu-id="96f3f-118">Naming Resources</span></span>](naming-resources.md)  
 <span data-ttu-id="96f3f-119">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="96f3f-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="96f3f-120">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="96f3f-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96f3f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96f3f-121">See also</span></span>

- [<span data-ttu-id="96f3f-122">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="96f3f-122">Framework Design Guidelines</span></span>](index.md)
