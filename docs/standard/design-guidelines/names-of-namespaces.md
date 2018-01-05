---
title: "Ad alanı adları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bc298ad41884bfda84771a729990ebb4e6f776b7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="names-of-namespaces"></a><span data-ttu-id="bf1cc-102">Ad alanı adları</span><span class="sxs-lookup"><span data-stu-id="bf1cc-102">Names of Namespaces</span></span>
<span data-ttu-id="bf1cc-103">Olarak diğer adlandırma kuralları ile ad alanlarını adlandırırken hedef yeterli netlik hemen ad içeriği büyük olasılıkla ne olduğunu bilmeniz framework kullanarak programcı için oluşturuyor.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-103">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="bf1cc-104">Aşağıdaki şablonu ad alanları adlandırma genel kural belirtir:</span><span class="sxs-lookup"><span data-stu-id="bf1cc-104">The following template specifies the general rule for naming namespaces:</span></span>  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 <span data-ttu-id="bf1cc-105">Örnekleri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="bf1cc-105">The following are examples:</span></span>  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 <span data-ttu-id="bf1cc-106">**✓ YAPMAK** önek ad alanı adları ile aynı ada sahip öğesinden farklı şirketler ad alanlarını önlemek için bir şirket adı.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-106">**✓ DO** prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>  
  
 <span data-ttu-id="bf1cc-107">**✓ YAPMAK** ad alanı adı ikinci düzeyde kararlı ve sürüm bağımsız ürün adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-107">**✓ DO** use a stable, version-independent product name at the second level of a namespace name.</span></span>  
  
 <span data-ttu-id="bf1cc-108">**X yok** grup adlarını kuruluşlar içinde kısa süreli olma eğilimindedir için kuruluş hiyerarşileri temel olarak ad alanı hiyerarşileri adları kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-108">**X DO NOT** use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="bf1cc-109">İlgili teknolojiler grupları geçici ad alanları hiyerarşisi düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-109">Organize the hierarchy of namespaces around groups of related technologies.</span></span>  
  
 <span data-ttu-id="bf1cc-110">**✓ YAPMAK** PascalCasing ve ayrı ad alanı bileşenler süreleriyle kullanır (örn., `Microsoft.Office.PowerPoint`).</span><span class="sxs-lookup"><span data-stu-id="bf1cc-110">**✓ DO** use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="bf1cc-111">Marka nontraditional büyük/küçük harf içeriyorsa, gelen normal ad büyük/küçük harf farklılık göstermesi olsa bile, marka tarafından tanımlanan büyük küçük harf izlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-111">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>  
  
 <span data-ttu-id="bf1cc-112">**✓ DÜŞÜNÜN** uygun olan yerlerde çoğul ad alanı adlarını kullanarak.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-112">**✓ CONSIDER** using plural namespace names where appropriate.</span></span>  
  
 <span data-ttu-id="bf1cc-113">Örneğin, `System.Collections` yerine `System.Collection`.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-113">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="bf1cc-114">Marka adlar ve kısaltmalar bu kuralın ancak durumlardır.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-114">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="bf1cc-115">Örneğin, `System.IO` yerine `System.IOs`.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-115">For example, use `System.IO` instead of `System.IOs`.</span></span>  
  
 <span data-ttu-id="bf1cc-116">**X yok** bu ad alanında bir ad alanı ve türü için aynı adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-116">**X DO NOT** use the same name for a namespace and a type in that namespace.</span></span>  
  
 <span data-ttu-id="bf1cc-117">Örneğin, kullanmayın `Debug` bir ad alanı olarak adlandırın ve ayrıca adlı bir sınıf sağlayın `Debug` aynı ad alanında.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-117">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="bf1cc-118">Birkaç derleyicileri gibi türler tam olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-118">Several compilers require such types to be fully qualified.</span></span>  
  
### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="bf1cc-119">Ad alanları ve türü ad çakışmaları</span><span class="sxs-lookup"><span data-stu-id="bf1cc-119">Namespaces and Type Name Conflicts</span></span>  
 <span data-ttu-id="bf1cc-120">**X yok** genel tür adları gibi tanıtmak `Element`, `Node`, `Log`, ve `Message`.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-120">**X DO NOT** introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>  
  
 <span data-ttu-id="bf1cc-121">Adı yazmaya yol açacaktır böylece ortak senaryolar çakışmaları çok büyük bir olasılıkla yoktur.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-121">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="bf1cc-122">Genel tür adları nitelemeniz (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span><span class="sxs-lookup"><span data-stu-id="bf1cc-122">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>  
  
 <span data-ttu-id="bf1cc-123">Ad alanları farklı kategorileri için tür adı çakışmaları önleme için belirli yönergeler vardır.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-123">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>  
  
-   <span data-ttu-id="bf1cc-124">**Uygulama modeli ad alanları**</span><span class="sxs-lookup"><span data-stu-id="bf1cc-124">**Application model namespaces**</span></span>  
  
     <span data-ttu-id="bf1cc-125">Neredeyse hiçbir zaman başka uygulama modelleri ad alanları ile kullanılan ancak tek bir uygulama modeline ait olan ad alanları çok sık birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-125">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="bf1cc-126">Örneğin, <xref:System.Windows.Forms?displayProperty=nameWithType> ad ile birlikte kullanılan nadiren <xref:System.Web.UI?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-126">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="bf1cc-127">İyi bilinen uygulama modeli ad grupları listesi aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="bf1cc-127">The following is a list of well-known application model namespace groups:</span></span>  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     <span data-ttu-id="bf1cc-128">**X yok** tek bir uygulama modeli içindeki ad alanlarında türleri için aynı adı verin.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-128">**X DO NOT** give the same name to types in namespaces within a single application model.</span></span>  
  
     <span data-ttu-id="bf1cc-129">Örneğin, adlı tür eklemeyin `Page` için <xref:System.Web.UI.Adapters?displayProperty=nameWithType> ad alanı, çünkü <xref:System.Web.UI?displayProperty=nameWithType> ad alanı zaten var. adlı tür `Page`.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-129">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>  
  
-   <span data-ttu-id="bf1cc-130">**Altyapı ad alanları**</span><span class="sxs-lookup"><span data-stu-id="bf1cc-130">**Infrastructure namespaces**</span></span>  
  
     <span data-ttu-id="bf1cc-131">Bu grup, nadiren ortak uygulamaları geliştirme sırasında içeri aktarılan ad alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-131">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="bf1cc-132">Örneğin, `.Design` ad alanları programlama geliştirme araçları, temel olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-132">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="bf1cc-133">Bu ad alanlarında türleri ile çakışmaları önleme kritik değildir.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-133">Avoiding conflicts with types in these namespaces is not critical.</span></span>  
  
-   <span data-ttu-id="bf1cc-134">**Çekirdek ad alanları**</span><span class="sxs-lookup"><span data-stu-id="bf1cc-134">**Core namespaces**</span></span>  
  
     <span data-ttu-id="bf1cc-135">Çekirdek ad alanlarını dahil tüm `System` ad alanları, bir uygulama modelini ad alanları ve altyapı ad alanlarını hariç.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-135">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="bf1cc-136">Çekirdek ad alanlarını dahil, başka şeylerin yanı sıra `System`, `System.IO`, `System.Xml`, ve `System.Net`.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-136">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>  
  
     <span data-ttu-id="bf1cc-137">**X yok** verin çekirdek ad alanlarında herhangi bir türü ile çakışan adları türleri.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-137">**X DO NOT** give types names that would conflict with any type in the Core namespaces.</span></span>  
  
     <span data-ttu-id="bf1cc-138">Örneğin, hiçbir zaman kullanmayın `Stream` bir tür adı olarak.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-138">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="bf1cc-139">İle çakışabilir <xref:System.IO.Stream?displayProperty=nameWithType>, bir çok kullanılan türü.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-139">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>  
  
-   <span data-ttu-id="bf1cc-140">**Teknoloji ad grupları**</span><span class="sxs-lookup"><span data-stu-id="bf1cc-140">**Technology namespace groups**</span></span>  
  
     <span data-ttu-id="bf1cc-141">Bu kategorideki tüm ad alanlarını aynı ilk iki ad alanı düğümlerle içeren `(<Company>.<Technology>*`), aşağıdaki gibi `Microsoft.Build.Utilities` ve `Microsoft.Build.Tasks`.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-141">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="bf1cc-142">Tek bir teknoloji ait türleri birbirleri ile çakışmadığını önemlidir.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-142">It is important that types belonging to a single technology do not conflict with each other.</span></span>  
  
     <span data-ttu-id="bf1cc-143">**X yok** tek bir teknoloji içindeki diğer türleriyle çakışabilir tür adları atayın.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-143">**X DO NOT** assign type names that would conflict with other types within a single technology.</span></span>  
  
     <span data-ttu-id="bf1cc-144">**X yok** (teknoloji uygulama modeli ile kullanılmak üzere tasarlanmamıştır sürece) teknolojisi ad alanlarında türleri ve bir uygulama model ad arasındaki ad çakışmalarının türü tanıtır.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-144">**X DO NOT** introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>  
  
 <span data-ttu-id="bf1cc-145">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="bf1cc-145">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="bf1cc-146">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="bf1cc-146">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf1cc-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-147">See Also</span></span>  
 [<span data-ttu-id="bf1cc-148">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="bf1cc-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="bf1cc-149">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="bf1cc-149">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
