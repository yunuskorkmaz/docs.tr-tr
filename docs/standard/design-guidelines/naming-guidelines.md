---
title: "Adlandırma yönergeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], about naming guidelines
- naming guidelines [.NET Framework]
- class library design guidelines [.NET Framework], names
- formatting [.NET Framework], names
- identifiers, class library element names
- names [.NET Framework]
- format naming guidelines [.NET Framework]
ms.assetid: fc076d66-9b5f-42d3-aa65-61d970c794a3
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 713a11f822dd30e77e6442c0bb082a40755b1832
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="naming-guidelines"></a><span data-ttu-id="8d668-102">Adlandırma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="8d668-102">Naming Guidelines</span></span>
<span data-ttu-id="8d668-103">Adlandırma kuralları çerçevenin geliştirmede tutarlı bir dizi aşağıdaki framework'ün kullanılabilirlik önemli bir katkısı olabilir.</span><span class="sxs-lookup"><span data-stu-id="8d668-103">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="8d668-104">Yaygın olarak ayrılmış projelerde birçok geliştiriciler tarafından kullanılması için çerçeveyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d668-104">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="8d668-105">Tutarlılık formunun ötesinde framework öğelerin adları kolayca anlaşılması gerekir ve her öğenin işlevi iletmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d668-105">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="8d668-106">Bu bölümün amacı, geliştiricilerin hemen anlamlı adları sonuçlanır tutarlı adlandırma kuralları kümesi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="8d668-106">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="8d668-107">Genel kod geliştirme yönergeleri, tüm kodunuzda daha tutarlı adlandırmada oluşacak şekilde adlandırma kurallarına benimsenmesi rağmen yalnızca genel olarak sunulan API'leri uygulamak için gereklidir (genel veya korumalı türleri ve üyeleri ve açıkça arabirimleri uygulanan).</span><span class="sxs-lookup"><span data-stu-id="8d668-107">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8d668-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8d668-108">In This Section</span></span>  
 [<span data-ttu-id="8d668-109">Büyük/Küçük Harf Kuralları</span><span class="sxs-lookup"><span data-stu-id="8d668-109">Capitalization Conventions</span></span>](../../../docs/standard/design-guidelines/capitalization-conventions.md)  
 [<span data-ttu-id="8d668-110">Genel Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="8d668-110">General Naming Conventions</span></span>](../../../docs/standard/design-guidelines/general-naming-conventions.md)  
 [<span data-ttu-id="8d668-111">Bütünleştirilmiş Kod ve DLL Adları</span><span class="sxs-lookup"><span data-stu-id="8d668-111">Names of Assemblies and DLLs</span></span>](../../../docs/standard/design-guidelines/names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="8d668-112">Ad Alanlarının Adları</span><span class="sxs-lookup"><span data-stu-id="8d668-112">Names of Namespaces</span></span>](../../../docs/standard/design-guidelines/names-of-namespaces.md)  
 [<span data-ttu-id="8d668-113">Sınıf, Yapı ve Arabirimlerin Adları</span><span class="sxs-lookup"><span data-stu-id="8d668-113">Names of Classes, Structs, and Interfaces</span></span>](../../../docs/standard/design-guidelines/names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="8d668-114">Tür Üyelerinin Adları</span><span class="sxs-lookup"><span data-stu-id="8d668-114">Names of Type Members</span></span>](../../../docs/standard/design-guidelines/names-of-type-members.md)  
 [<span data-ttu-id="8d668-115">Adlandırma Parametreleri</span><span class="sxs-lookup"><span data-stu-id="8d668-115">Naming Parameters</span></span>](../../../docs/standard/design-guidelines/naming-parameters.md)  
 [<span data-ttu-id="8d668-116">Adlandırma Kaynakları</span><span class="sxs-lookup"><span data-stu-id="8d668-116">Naming Resources</span></span>](../../../docs/standard/design-guidelines/naming-resources.md)  
 <span data-ttu-id="8d668-117">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="8d668-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="8d668-118">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="8d668-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d668-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8d668-119">See Also</span></span>  
 [<span data-ttu-id="8d668-120">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="8d668-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
