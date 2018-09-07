---
title: Ad alanlarının adları
ms.date: 03/30/2017
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d68966f60c5039fd67195a03facc1586b9ed154
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44097015"
---
# <a name="names-of-namespaces"></a><span data-ttu-id="40031-102">Ad alanlarının adları</span><span class="sxs-lookup"><span data-stu-id="40031-102">Names of Namespaces</span></span>
<span data-ttu-id="40031-103">Olarak diğer adlandırma kuralları ile hedef ad alanları adlandırırken yeterli netlik ad alanı içeriğini olma olasılığı nedir hemen bilmek framework kullanarak programcısı için oluşturuyor.</span><span class="sxs-lookup"><span data-stu-id="40031-103">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="40031-104">Aşağıdaki şablonu genel bir kural ad alanlarını adlandırma belirtir:</span><span class="sxs-lookup"><span data-stu-id="40031-104">The following template specifies the general rule for naming namespaces:</span></span>  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 <span data-ttu-id="40031-105">Örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="40031-105">The following are examples:</span></span>  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 <span data-ttu-id="40031-106">**✓ DO** önek ad alanı adları ile aynı ada sahip öğesinden farklı şirketler ad alanlarını önlemek için bir şirket adı.</span><span class="sxs-lookup"><span data-stu-id="40031-106">**✓ DO** prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>  
  
 <span data-ttu-id="40031-107">**✓ DO** ad alanı adı ikinci düzeyde kararlı ve sürüm bağımsız ürün adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="40031-107">**✓ DO** use a stable, version-independent product name at the second level of a namespace name.</span></span>  
  
 <span data-ttu-id="40031-108">**X DO NOT** grup adlarını kuruluşlar içinde kısa süreli olma eğilimindedir için kuruluş hiyerarşileri temel olarak ad alanı hiyerarşileri adları kullanın.</span><span class="sxs-lookup"><span data-stu-id="40031-108">**X DO NOT** use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="40031-109">İlgili teknolojiler gruplarının çevresinde ad alanları hiyerarşisi düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="40031-109">Organize the hierarchy of namespaces around groups of related technologies.</span></span>  
  
 <span data-ttu-id="40031-110">**✓ DO** PascalCasing ve ayrı ad alanı bileşenler süreleriyle kullanır (örn., `Microsoft.Office.PowerPoint`).</span><span class="sxs-lookup"><span data-stu-id="40031-110">**✓ DO** use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="40031-111">Markanızı nontraditional büyük/küçük harf içeriyorsa, bu normal bir ad alanı büyük küçük harflerini öğesinden farklılık göstermesi bile markanızı tarafından tanımlanan büyük/küçük harf izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="40031-111">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>  
  
 <span data-ttu-id="40031-112">**✓ CONSIDER** uygun olan yerlerde çoğul ad alanı adlarını kullanarak.</span><span class="sxs-lookup"><span data-stu-id="40031-112">**✓ CONSIDER** using plural namespace names where appropriate.</span></span>  
  
 <span data-ttu-id="40031-113">Örneğin, `System.Collections` yerine `System.Collection`.</span><span class="sxs-lookup"><span data-stu-id="40031-113">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="40031-114">Bu kuralın istisnası, marka adları ve kısaltmalar ancak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="40031-114">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="40031-115">Örneğin, `System.IO` yerine `System.IOs`.</span><span class="sxs-lookup"><span data-stu-id="40031-115">For example, use `System.IO` instead of `System.IOs`.</span></span>  
  
 <span data-ttu-id="40031-116">**X DO NOT** bu ad alanında bir ad alanı ve türü için aynı adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="40031-116">**X DO NOT** use the same name for a namespace and a type in that namespace.</span></span>  
  
 <span data-ttu-id="40031-117">Örneğin, kullanmayın `Debug` bir ad alanı olarak adlandırın ve sonra da adlı bir sınıf sağlayın `Debug` ad.</span><span class="sxs-lookup"><span data-stu-id="40031-117">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="40031-118">Bazı derleyiciler gibi türler tam olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="40031-118">Several compilers require such types to be fully qualified.</span></span>  
  
### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="40031-119">Ad alanları ve tür adı çakışıyor</span><span class="sxs-lookup"><span data-stu-id="40031-119">Namespaces and Type Name Conflicts</span></span>  
 <span data-ttu-id="40031-120">**X DO NOT** genel tür adları gibi tanıtmak `Element`, `Node`, `Log`, ve `Message`.</span><span class="sxs-lookup"><span data-stu-id="40031-120">**X DO NOT** introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>  
  
 <span data-ttu-id="40031-121">Ad önünü açacak yapılması, ortak senaryolar çakışıyor çok yüksek bir olasılık yoktur.</span><span class="sxs-lookup"><span data-stu-id="40031-121">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="40031-122">Genel tür adları nitelemeniz (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span><span class="sxs-lookup"><span data-stu-id="40031-122">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>  
  
 <span data-ttu-id="40031-123">Belirli ad alanları farklı kategorileri için tür adı çakışmalarını önleme ilkeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="40031-123">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>  
  
-   <span data-ttu-id="40031-124">**Uygulama modeli ad alanları**</span><span class="sxs-lookup"><span data-stu-id="40031-124">**Application model namespaces**</span></span>  
  
     <span data-ttu-id="40031-125">Tek bir uygulama modeline ait olan ad alanları sıklıkla birlikte kullanılır, ancak diğer uygulama modellerini ad alanları ile neredeyse hiçbir zaman kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40031-125">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="40031-126">Örneğin, <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı ile birlikte kullanılan nadiren <xref:System.Web.UI?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="40031-126">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="40031-127">İyi bilinen uygulama modeli ad gruplarının listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="40031-127">The following is a list of well-known application model namespace groups:</span></span>  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     <span data-ttu-id="40031-128">**X DO NOT** tek bir uygulama modeli içindeki ad alanlarında türleri için aynı adı verin.</span><span class="sxs-lookup"><span data-stu-id="40031-128">**X DO NOT** give the same name to types in namespaces within a single application model.</span></span>  
  
     <span data-ttu-id="40031-129">Örneğin, adlı bir tür eklemeyin `Page` için <xref:System.Web.UI.Adapters?displayProperty=nameWithType> ad alanı, çünkü <xref:System.Web.UI?displayProperty=nameWithType> ad alanını adlı bir tür zaten var. `Page`.</span><span class="sxs-lookup"><span data-stu-id="40031-129">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>  
  
-   <span data-ttu-id="40031-130">**Altyapı ad alanları**</span><span class="sxs-lookup"><span data-stu-id="40031-130">**Infrastructure namespaces**</span></span>  
  
     <span data-ttu-id="40031-131">Bu grup, nadiren uygulamaların ortak bir geliştirme sırasında içeri aktarılan ad alanlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="40031-131">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="40031-132">Örneğin, `.Design` ad alanları programlama geliştirme araçları oluştururken temel olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40031-132">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="40031-133">Bu ad alanlarında türleri ile çakışmaları önleme önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="40031-133">Avoiding conflicts with types in these namespaces is not critical.</span></span>  
  
-   <span data-ttu-id="40031-134">**Temel ad alanları**</span><span class="sxs-lookup"><span data-stu-id="40031-134">**Core namespaces**</span></span>  
  
     <span data-ttu-id="40031-135">Temel ad alanlarını dahil tüm `System` ad alanları, uygulama modellerin ad alanları ve altyapı ad alanlarını hariç.</span><span class="sxs-lookup"><span data-stu-id="40031-135">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="40031-136">Temel ad alanlarını içeren diğerleriyle birlikte, `System`, `System.IO`, `System.Xml`, ve `System.Net`.</span><span class="sxs-lookup"><span data-stu-id="40031-136">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>  
  
     <span data-ttu-id="40031-137">**X DO NOT** verin çekirdek ad alanlarında herhangi bir türü ile çakışan adları türleri.</span><span class="sxs-lookup"><span data-stu-id="40031-137">**X DO NOT** give types names that would conflict with any type in the Core namespaces.</span></span>  
  
     <span data-ttu-id="40031-138">Örneğin, hiçbir zaman kullanmayın `Stream` olarak bir tür adı.</span><span class="sxs-lookup"><span data-stu-id="40031-138">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="40031-139">İle çakışmadığı <xref:System.IO.Stream?displayProperty=nameWithType>, çok kullanılan tür.</span><span class="sxs-lookup"><span data-stu-id="40031-139">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>  
  
-   <span data-ttu-id="40031-140">**Teknoloji ad grupları**</span><span class="sxs-lookup"><span data-stu-id="40031-140">**Technology namespace groups**</span></span>  
  
     <span data-ttu-id="40031-141">Bu kategori, tüm ad alanları ile aynı ilk iki ad alanı düğümleri içerir `(<Company>.<Technology>*`), aşağıdakiler gibi `Microsoft.Build.Utilities` ve `Microsoft.Build.Tasks`.</span><span class="sxs-lookup"><span data-stu-id="40031-141">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="40031-142">Türler için tek bir teknoloji ait birbiriyle çakışmadığından emin önemlidir.</span><span class="sxs-lookup"><span data-stu-id="40031-142">It is important that types belonging to a single technology do not conflict with each other.</span></span>  
  
     <span data-ttu-id="40031-143">**X DO NOT** tek bir teknoloji içindeki diğer türleriyle çakışabilir tür adları atayın.</span><span class="sxs-lookup"><span data-stu-id="40031-143">**X DO NOT** assign type names that would conflict with other types within a single technology.</span></span>  
  
     <span data-ttu-id="40031-144">**X DO NOT** (teknoloji uygulama modeli ile kullanılmak üzere tasarlanmamıştır sürece) teknolojisi ad alanlarında türleri ve bir uygulama model ad arasındaki ad çakışmalarının türü tanıtır.</span><span class="sxs-lookup"><span data-stu-id="40031-144">**X DO NOT** introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>  
  
 <span data-ttu-id="40031-145">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="40031-145">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="40031-146">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="40031-146">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40031-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40031-147">See also</span></span>

- [<span data-ttu-id="40031-148">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="40031-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="40031-149">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="40031-149">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
