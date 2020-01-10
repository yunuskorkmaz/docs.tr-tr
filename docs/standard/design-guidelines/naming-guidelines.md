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
ms.openlocfilehash: ad98c0f3b02bdc81e6348493b4e0a02f9cb20ed4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709198"
---
# <a name="naming-guidelines"></a><span data-ttu-id="13be5-102">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="13be5-102">Naming Guidelines</span></span>
<span data-ttu-id="13be5-103">Bir çerçeve geliştirmede tutarlı bir adlandırma kuralları kümesi takip etmek framework 'ün kullanılabilirlik açısından önemli bir katkı olabilir.</span><span class="sxs-lookup"><span data-stu-id="13be5-103">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="13be5-104">Framework 'ün yaygın olarak ayrılmış projeler üzerinde birçok geliştirici tarafından kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="13be5-104">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="13be5-105">Formun tutarlılığı ötesinde, Framework öğelerinin adları kolayca anlaşılmalıdır ve her bir öğenin işlevini iletmelidir.</span><span class="sxs-lookup"><span data-stu-id="13be5-105">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="13be5-106">Bu bölümün amacı, geliştiricilere anında anlam veren adlara neden olan tutarlı bir adlandırma kuralları kümesi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="13be5-106">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="13be5-107">Bu adlandırma kurallarını genel kod geliştirme yönergeleri olarak benimseme, kodunuzun tamamında daha tutarlı adlandırmaya neden olacağından, bunları yalnızca herkese açık olan (genel veya korumalı türler ve Üyeler) API 'Lerine uygulamanız gerekir ve açıkça uygulanan arabirimler).</span><span class="sxs-lookup"><span data-stu-id="13be5-107">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13be5-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="13be5-108">In This Section</span></span>  
 [<span data-ttu-id="13be5-109">Büyük/Küçük Harf Kuralları</span><span class="sxs-lookup"><span data-stu-id="13be5-109">Capitalization Conventions</span></span>](../../../docs/standard/design-guidelines/capitalization-conventions.md)  
 [<span data-ttu-id="13be5-110">Genel Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="13be5-110">General Naming Conventions</span></span>](../../../docs/standard/design-guidelines/general-naming-conventions.md)  
 [<span data-ttu-id="13be5-111">Bütünleştirilmiş Kod ve DLL Adları</span><span class="sxs-lookup"><span data-stu-id="13be5-111">Names of Assemblies and DLLs</span></span>](../../../docs/standard/design-guidelines/names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="13be5-112">Ad Alanlarının Adları</span><span class="sxs-lookup"><span data-stu-id="13be5-112">Names of Namespaces</span></span>](../../../docs/standard/design-guidelines/names-of-namespaces.md)  
 [<span data-ttu-id="13be5-113">Sınıf, Yapı ve Arabirimlerin Adları</span><span class="sxs-lookup"><span data-stu-id="13be5-113">Names of Classes, Structs, and Interfaces</span></span>](../../../docs/standard/design-guidelines/names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="13be5-114">Tür Üyelerinin Adları</span><span class="sxs-lookup"><span data-stu-id="13be5-114">Names of Type Members</span></span>](../../../docs/standard/design-guidelines/names-of-type-members.md)  
 [<span data-ttu-id="13be5-115">Adlandırma Parametreleri</span><span class="sxs-lookup"><span data-stu-id="13be5-115">Naming Parameters</span></span>](../../../docs/standard/design-guidelines/naming-parameters.md)  
 [<span data-ttu-id="13be5-116">Adlandırma Kaynakları</span><span class="sxs-lookup"><span data-stu-id="13be5-116">Naming Resources</span></span>](../../../docs/standard/design-guidelines/naming-resources.md)  
 <span data-ttu-id="13be5-117">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="13be5-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="13be5-118">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="13be5-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13be5-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13be5-119">See also</span></span>

- [<span data-ttu-id="13be5-120">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="13be5-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
