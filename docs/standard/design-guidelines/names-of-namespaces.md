---
title: Ad Alanlarının Adları
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
ms.openlocfilehash: 0678f695e3ae7c40660031862c9073a21fd72491
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709237"
---
# <a name="names-of-namespaces"></a><span data-ttu-id="4ff9c-102">Ad Alanlarının Adları</span><span class="sxs-lookup"><span data-stu-id="4ff9c-102">Names of Namespaces</span></span>
<span data-ttu-id="4ff9c-103">Diğer adlandırma kılavuzlarında olduğu gibi, ad alanlarını Adlandırmanın amacı, programlama çerçevesini kullanarak, ad alanının içeriğinin büyük olasılıkla ne olduğunu hemen bilmenin ne kadar anlaşılır olduğunu oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-103">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="4ff9c-104">Aşağıdaki şablon ad alanlarını adlandırmak için genel kuralı belirtir:</span><span class="sxs-lookup"><span data-stu-id="4ff9c-104">The following template specifies the general rule for naming namespaces:</span></span>  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 <span data-ttu-id="4ff9c-105">Aşağıda örnekler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4ff9c-105">The following are examples:</span></span>  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 <span data-ttu-id="4ff9c-106">**✓ DO** önek ad alanı adları ile aynı ada sahip öğesinden farklı şirketler ad alanlarını önlemek için bir şirket adı.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-106">**✓ DO** prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>  
  
 <span data-ttu-id="4ff9c-107">**✓ DO** ad alanı adı ikinci düzeyde kararlı ve sürüm bağımsız ürün adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-107">**✓ DO** use a stable, version-independent product name at the second level of a namespace name.</span></span>  
  
 <span data-ttu-id="4ff9c-108">**X DO NOT** grup adlarını kuruluşlar içinde kısa süreli olma eğilimindedir için kuruluş hiyerarşileri temel olarak ad alanı hiyerarşileri adları kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-108">**X DO NOT** use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="4ff9c-109">İlgili teknolojilerin grupları etrafında ad alanlarının hiyerarşisini düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-109">Organize the hierarchy of namespaces around groups of related technologies.</span></span>  
  
 <span data-ttu-id="4ff9c-110">**✓ DO** PascalCasing ve ayrı ad alanı bileşenler süreleriyle kullanır (örn., `Microsoft.Office.PowerPoint`).</span><span class="sxs-lookup"><span data-stu-id="4ff9c-110">**✓ DO** use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="4ff9c-111">Markanız geleneksel olmayan büyük harfe kullanıyorsa, normal ad alanı büyük küçük harfe göre farklılık gösterir olsa da markanız tarafından tanımlanan büyük/küçük harfleri izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-111">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>  
  
 <span data-ttu-id="4ff9c-112">**✓ CONSIDER** uygun olan yerlerde çoğul ad alanı adlarını kullanarak.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-112">**✓ CONSIDER** using plural namespace names where appropriate.</span></span>  
  
 <span data-ttu-id="4ff9c-113">Örneğin, `System.Collection`yerine `System.Collections` kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-113">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="4ff9c-114">Ancak, marka adları ve kısaltmalar bu kuralın istisnalardır.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-114">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="4ff9c-115">Örneğin, `System.IOs`yerine `System.IO` kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-115">For example, use `System.IO` instead of `System.IOs`.</span></span>  
  
 <span data-ttu-id="4ff9c-116">**X DO NOT** bu ad alanında bir ad alanı ve türü için aynı adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-116">**X DO NOT** use the same name for a namespace and a type in that namespace.</span></span>  
  
 <span data-ttu-id="4ff9c-117">Örneğin, `Debug` ad alanı adı olarak kullanmayın ve ayrıca aynı ad alanında `Debug` adlı bir sınıf sağlayın.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-117">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="4ff9c-118">Çeşitli derleyiciler, bu tür türlerin tam nitelikli olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-118">Several compilers require such types to be fully qualified.</span></span>  
  
### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="4ff9c-119">Ad alanları ve tür adı çakışmaları</span><span class="sxs-lookup"><span data-stu-id="4ff9c-119">Namespaces and Type Name Conflicts</span></span>  
 <span data-ttu-id="4ff9c-120">**X DO NOT** genel tür adları gibi tanıtmak `Element`, `Node`, `Log`, ve `Message`.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-120">**X DO NOT** introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>  
  
 <span data-ttu-id="4ff9c-121">Bunu yapmanın çok büyük bir olasılığı, yaygın senaryolarda tür adı çakışmalarına yol açacaktır.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-121">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="4ff9c-122">Genel tür adlarını (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`) nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-122">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>  
  
 <span data-ttu-id="4ff9c-123">Farklı ad alanları kategorileri için tür adı çakışmalarını önlemeye yönelik özel yönergeler vardır.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-123">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>  
  
- <span data-ttu-id="4ff9c-124">**Uygulama modeli ad alanları**</span><span class="sxs-lookup"><span data-stu-id="4ff9c-124">**Application model namespaces**</span></span>  
  
     <span data-ttu-id="4ff9c-125">Tek bir uygulama modeline ait olan ad alanları birlikte çok sık kullanılır, ancak bunlar, diğer uygulama modelleriyle ilgili ad alanları ile neredeyse hiç kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-125">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="4ff9c-126">Örneğin, <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı <xref:System.Web.UI?displayProperty=nameWithType> ad alanıyla birlikte çok seyrek kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-126">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="4ff9c-127">Aşağıda, iyi bilinen uygulama modeli ad alanı gruplarının listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4ff9c-127">The following is a list of well-known application model namespace groups:</span></span>  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     <span data-ttu-id="4ff9c-128">**X DO NOT** tek bir uygulama modeli içindeki ad alanlarında türleri için aynı adı verin.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-128">**X DO NOT** give the same name to types in namespaces within a single application model.</span></span>  
  
     <span data-ttu-id="4ff9c-129">Örneğin, <xref:System.Web.UI?displayProperty=nameWithType> ad alanı zaten `Page`adlı bir tür içerdiğinden, <xref:System.Web.UI.Adapters?displayProperty=nameWithType> ad alanına `Page` adlı bir tür eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-129">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>  
  
- <span data-ttu-id="4ff9c-130">**Altyapı ad alanları**</span><span class="sxs-lookup"><span data-stu-id="4ff9c-130">**Infrastructure namespaces**</span></span>  
  
     <span data-ttu-id="4ff9c-131">Bu grup, ortak uygulamaların geliştirilmesi sırasında nadiren içeri aktarılan ad alanlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-131">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="4ff9c-132">Örneğin, `.Design` ad alanları genellikle programlama araçları geliştirilirken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-132">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="4ff9c-133">Bu ad alanlarında bulunan çakışmaları önleme kritik değildir.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-133">Avoiding conflicts with types in these namespaces is not critical.</span></span>  
  
- <span data-ttu-id="4ff9c-134">**Çekirdek ad alanları**</span><span class="sxs-lookup"><span data-stu-id="4ff9c-134">**Core namespaces**</span></span>  
  
     <span data-ttu-id="4ff9c-135">Çekirdek ad alanları, uygulama modellerinin ad alanları ve altyapı ad alanları hariç tüm `System` ad alanlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-135">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="4ff9c-136">Temel ad alanları, diğerleri, `System`, `System.IO`, `System.Xml`ve `System.Net`arasında yer alır.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-136">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>  
  
     <span data-ttu-id="4ff9c-137">**X DO NOT** verin çekirdek ad alanlarında herhangi bir türü ile çakışan adları türleri.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-137">**X DO NOT** give types names that would conflict with any type in the Core namespaces.</span></span>  
  
     <span data-ttu-id="4ff9c-138">Örneğin, hiçbir `Stream` tür adı olarak kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-138">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="4ff9c-139">Yaygın olarak kullanılan bir tür olan <xref:System.IO.Stream?displayProperty=nameWithType>ile çakışır.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-139">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>  
  
- <span data-ttu-id="4ff9c-140">**Teknoloji ad alanı grupları**</span><span class="sxs-lookup"><span data-stu-id="4ff9c-140">**Technology namespace groups**</span></span>  
  
     <span data-ttu-id="4ff9c-141">Bu kategori, `Microsoft.Build.Utilities` ve `Microsoft.Build.Tasks`gibi aynı ilk iki ad alanı düğümüne sahip tüm ad alanlarını içerir `(<Company>.<Technology>*`).</span><span class="sxs-lookup"><span data-stu-id="4ff9c-141">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="4ff9c-142">Tek bir teknolojiye ait olan türlerin birbirleriyle çakışmaması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-142">It is important that types belonging to a single technology do not conflict with each other.</span></span>  
  
     <span data-ttu-id="4ff9c-143">**X DO NOT** tek bir teknoloji içindeki diğer türleriyle çakışabilir tür adları atayın.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-143">**X DO NOT** assign type names that would conflict with other types within a single technology.</span></span>  
  
     <span data-ttu-id="4ff9c-144">**X DO NOT** (teknoloji uygulama modeli ile kullanılmak üzere tasarlanmamıştır sürece) teknolojisi ad alanlarında türleri ve bir uygulama model ad arasındaki ad çakışmalarının türü tanıtır.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-144">**X DO NOT** introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>  
  
 <span data-ttu-id="4ff9c-145">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="4ff9c-145">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4ff9c-146">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="4ff9c-146">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ff9c-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-147">See also</span></span>

- [<span data-ttu-id="4ff9c-148">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="4ff9c-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="4ff9c-149">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="4ff9c-149">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
