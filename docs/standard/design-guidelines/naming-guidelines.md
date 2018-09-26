---
title: Adlandırma kuralları
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 70888e068782add5ebe5ae1c7da3bdee842faea8
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070220"
---
# <a name="naming-guidelines"></a><span data-ttu-id="e5065-102">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="e5065-102">Naming Guidelines</span></span>
<span data-ttu-id="e5065-103">Tutarlı bir adlandırma kuralları geliştirmeye yönelik bir çerçeve kümesi uygulayarak framework'ün kullanılabilirlik önemli bir katkısı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e5065-103">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="e5065-104">Yaygın olarak ayrılmış projelerde birçok geliştirici tarafından kullanılmak üzere çerçevesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5065-104">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="e5065-105">Tutarlılık formunun ötesinde framework öğelerinin adlarını kolayca anlaşılır olmasını ve her öğenin işlevi iletmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5065-105">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="e5065-106">Bu bölümün amacı, geliştiricilerin hemen anlamlı adlar sonuçlanır tutarlı adlandırma kuralları kümesi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="e5065-106">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="e5065-107">Genel kod geliştirme yönergeleri, tüm kodunuzda daha tutarlı adlandırma içinde neden olarak bu adlandırma kurallarını uygulamak olsa da, bunları yalnızca genel olarak kullanıma sunulan API'ler uygulamak için gereklidir (ortak veya korumalı türler ve üyeler, ve "açıkça arabirimleri uygulanmış).</span><span class="sxs-lookup"><span data-stu-id="e5065-107">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5065-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e5065-108">In This Section</span></span>  
 [<span data-ttu-id="e5065-109">Büyük/Küçük Harf Kuralları</span><span class="sxs-lookup"><span data-stu-id="e5065-109">Capitalization Conventions</span></span>](../../../docs/standard/design-guidelines/capitalization-conventions.md)  
 [<span data-ttu-id="e5065-110">Genel Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="e5065-110">General Naming Conventions</span></span>](../../../docs/standard/design-guidelines/general-naming-conventions.md)  
 [<span data-ttu-id="e5065-111">Bütünleştirilmiş Kod ve DLL Adları</span><span class="sxs-lookup"><span data-stu-id="e5065-111">Names of Assemblies and DLLs</span></span>](../../../docs/standard/design-guidelines/names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="e5065-112">Ad Alanlarının Adları</span><span class="sxs-lookup"><span data-stu-id="e5065-112">Names of Namespaces</span></span>](../../../docs/standard/design-guidelines/names-of-namespaces.md)  
 [<span data-ttu-id="e5065-113">Sınıf, Yapı ve Arabirimlerin Adları</span><span class="sxs-lookup"><span data-stu-id="e5065-113">Names of Classes, Structs, and Interfaces</span></span>](../../../docs/standard/design-guidelines/names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="e5065-114">Tür Üyelerinin Adları</span><span class="sxs-lookup"><span data-stu-id="e5065-114">Names of Type Members</span></span>](../../../docs/standard/design-guidelines/names-of-type-members.md)  
 [<span data-ttu-id="e5065-115">Adlandırma Parametreleri</span><span class="sxs-lookup"><span data-stu-id="e5065-115">Naming Parameters</span></span>](../../../docs/standard/design-guidelines/naming-parameters.md)  
 [<span data-ttu-id="e5065-116">Adlandırma Kaynakları</span><span class="sxs-lookup"><span data-stu-id="e5065-116">Naming Resources</span></span>](../../../docs/standard/design-guidelines/naming-resources.md)  
 <span data-ttu-id="e5065-117">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="e5065-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e5065-118">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="e5065-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5065-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5065-119">See also</span></span>

- [<span data-ttu-id="e5065-120">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e5065-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
