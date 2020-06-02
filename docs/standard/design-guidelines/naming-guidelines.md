---
title: Adlandırma Kuralları
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
ms.openlocfilehash: 1b137be60f4c8c1c7cf1fa1f807841d4bc209089
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290181"
---
# <a name="naming-guidelines"></a><span data-ttu-id="db83e-102">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="db83e-102">Naming Guidelines</span></span>
<span data-ttu-id="db83e-103">Bir çerçeve geliştirmede tutarlı bir adlandırma kuralları kümesi takip etmek framework 'ün kullanılabilirlik açısından önemli bir katkı olabilir.</span><span class="sxs-lookup"><span data-stu-id="db83e-103">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="db83e-104">Framework 'ün yaygın olarak ayrılmış projeler üzerinde birçok geliştirici tarafından kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="db83e-104">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="db83e-105">Formun tutarlılığı ötesinde, Framework öğelerinin adları kolayca anlaşılmalıdır ve her bir öğenin işlevini iletmelidir.</span><span class="sxs-lookup"><span data-stu-id="db83e-105">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="db83e-106">Bu bölümün amacı, geliştiricilere anında anlam veren adlara neden olan tutarlı bir adlandırma kuralları kümesi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="db83e-106">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="db83e-107">Bu adlandırma kurallarını genel kod geliştirme yönergeleri olarak benimseme, kodunuzun tamamında daha tutarlı adlandırma oluşmasına neden olsa da, bunları yalnızca herkese açık olan API 'lere (ortak veya korumalı türler ve Üyeler ve açıkça uygulanan arabirimler) uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="db83e-107">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db83e-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="db83e-108">In This Section</span></span>  
 [<span data-ttu-id="db83e-109">Büyük harfe dönüştürme kuralları</span><span class="sxs-lookup"><span data-stu-id="db83e-109">Capitalization Conventions</span></span>](capitalization-conventions.md)  
 [<span data-ttu-id="db83e-110">Genel adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="db83e-110">General Naming Conventions</span></span>](general-naming-conventions.md)  
 [<span data-ttu-id="db83e-111">Derlemelerin ve DLL 'Lerin adları</span><span class="sxs-lookup"><span data-stu-id="db83e-111">Names of Assemblies and DLLs</span></span>](names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="db83e-112">Ad alanlarının adları</span><span class="sxs-lookup"><span data-stu-id="db83e-112">Names of Namespaces</span></span>](names-of-namespaces.md)  
 [<span data-ttu-id="db83e-113">Sınıfların, yapıların ve arabirimlerin adları</span><span class="sxs-lookup"><span data-stu-id="db83e-113">Names of Classes, Structs, and Interfaces</span></span>](names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="db83e-114">Üye türü adları</span><span class="sxs-lookup"><span data-stu-id="db83e-114">Names of Type Members</span></span>](names-of-type-members.md)  
 [<span data-ttu-id="db83e-115">Adlandırma parametreleri</span><span class="sxs-lookup"><span data-stu-id="db83e-115">Naming Parameters</span></span>](naming-parameters.md)  
 [<span data-ttu-id="db83e-116">Kaynakları adlandırma</span><span class="sxs-lookup"><span data-stu-id="db83e-116">Naming Resources</span></span>](naming-resources.md)  
 <span data-ttu-id="db83e-117">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="db83e-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="db83e-118">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="db83e-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db83e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db83e-119">See also</span></span>

- [<span data-ttu-id="db83e-120">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="db83e-120">Framework Design Guidelines</span></span>](index.md)
