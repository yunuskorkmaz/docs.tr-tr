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
ms.openlocfilehash: 52fee0dfaff284c2c1a6afcb8aa7530c28a60d65
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744145"
---
# <a name="names-of-namespaces"></a><span data-ttu-id="43360-102">Ad Alanlarının Adları</span><span class="sxs-lookup"><span data-stu-id="43360-102">Names of Namespaces</span></span>
<span data-ttu-id="43360-103">Diğer adlandırma kılavuzlarında olduğu gibi, ad alanlarını Adlandırmanın amacı, programlama çerçevesini kullanarak, ad alanının içeriğinin büyük olasılıkla ne olduğunu hemen bilmenin ne kadar anlaşılır olduğunu oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="43360-103">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="43360-104">Aşağıdaki şablon ad alanlarını adlandırmak için genel kuralı belirtir:</span><span class="sxs-lookup"><span data-stu-id="43360-104">The following template specifies the general rule for naming namespaces:</span></span>

 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`

 <span data-ttu-id="43360-105">Aşağıda örnekler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="43360-105">The following are examples:</span></span>

 <span data-ttu-id="43360-106">`Fabrikam.Math` `Litware.Security`</span><span class="sxs-lookup"><span data-stu-id="43360-106">`Fabrikam.Math` `Litware.Security`</span></span>

 <span data-ttu-id="43360-107">farklı şirketlerin ad alanlarının aynı ada sahip olmasını engellemek için, önek ad alanı adlarını bir şirket adıyla ✔️.</span><span class="sxs-lookup"><span data-stu-id="43360-107">✔️ DO prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>

 <span data-ttu-id="43360-108">✔️ bir ad alanı adının ikinci düzeyinde kararlı, sürümden bağımsız bir ürün adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="43360-108">✔️ DO use a stable, version-independent product name at the second level of a namespace name.</span></span>

 <span data-ttu-id="43360-109">❌, şirketler içindeki Grup adları kısa süreli olmaya eğiltiğinden, ad alanı hiyerarşilerindeki adların temeli olarak kurumsal hiyerarşileri kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="43360-109">❌ DO NOT use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="43360-110">İlgili teknolojilerin grupları etrafında ad alanlarının hiyerarşisini düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="43360-110">Organize the hierarchy of namespaces around groups of related technologies.</span></span>

 <span data-ttu-id="43360-111">✔️ Pascalbüyük harfleri kullanır ve ad alanı bileşenlerini noktalarla ayırın (örn. `Microsoft.Office.PowerPoint`).</span><span class="sxs-lookup"><span data-stu-id="43360-111">✔️ DO use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="43360-112">Markanız geleneksel olmayan büyük harfe kullanıyorsa, normal ad alanı büyük küçük harfe göre farklılık gösterir olsa da markanız tarafından tanımlanan büyük/küçük harfleri izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="43360-112">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>

 <span data-ttu-id="43360-113">✔️ Çoğul ad alanı adlarını kullanmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="43360-113">✔️ CONSIDER using plural namespace names where appropriate.</span></span>

 <span data-ttu-id="43360-114">Örneğin, `System.Collection`yerine `System.Collections` kullanın.</span><span class="sxs-lookup"><span data-stu-id="43360-114">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="43360-115">Ancak, marka adları ve kısaltmalar bu kuralın istisnalardır.</span><span class="sxs-lookup"><span data-stu-id="43360-115">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="43360-116">Örneğin, `System.IOs`yerine `System.IO` kullanın.</span><span class="sxs-lookup"><span data-stu-id="43360-116">For example, use `System.IO` instead of `System.IOs`.</span></span>

 <span data-ttu-id="43360-117">❌ ad alanı için aynı adı ve bu ad alanındaki türü kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="43360-117">❌ DO NOT use the same name for a namespace and a type in that namespace.</span></span>

 <span data-ttu-id="43360-118">Örneğin, `Debug` ad alanı adı olarak kullanmayın ve ayrıca aynı ad alanında `Debug` adlı bir sınıf sağlayın.</span><span class="sxs-lookup"><span data-stu-id="43360-118">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="43360-119">Çeşitli derleyiciler, bu tür türlerin tam nitelikli olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="43360-119">Several compilers require such types to be fully qualified.</span></span>

### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="43360-120">Ad alanları ve tür adı çakışmaları</span><span class="sxs-lookup"><span data-stu-id="43360-120">Namespaces and Type Name Conflicts</span></span>
 <span data-ttu-id="43360-121">❌ `Element`, `Node`, `Log`ve `Message`gibi genel tür adları sunmaz.</span><span class="sxs-lookup"><span data-stu-id="43360-121">❌ DO NOT introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>

 <span data-ttu-id="43360-122">Bunu yapmanın çok büyük bir olasılığı, yaygın senaryolarda tür adı çakışmalarına yol açacaktır.</span><span class="sxs-lookup"><span data-stu-id="43360-122">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="43360-123">Genel tür adlarını (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`) nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="43360-123">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>

 <span data-ttu-id="43360-124">Farklı ad alanları kategorileri için tür adı çakışmalarını önlemeye yönelik özel yönergeler vardır.</span><span class="sxs-lookup"><span data-stu-id="43360-124">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>

- <span data-ttu-id="43360-125">**Uygulama modeli ad alanları**</span><span class="sxs-lookup"><span data-stu-id="43360-125">**Application model namespaces**</span></span>

     <span data-ttu-id="43360-126">Tek bir uygulama modeline ait olan ad alanları birlikte çok sık kullanılır, ancak bunlar, diğer uygulama modelleriyle ilgili ad alanları ile neredeyse hiç kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="43360-126">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="43360-127">Örneğin, <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı <xref:System.Web.UI?displayProperty=nameWithType> ad alanıyla birlikte çok seyrek kullanılır.</span><span class="sxs-lookup"><span data-stu-id="43360-127">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="43360-128">Aşağıda, iyi bilinen uygulama modeli ad alanı gruplarının listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="43360-128">The following is a list of well-known application model namespace groups:</span></span>

     <span data-ttu-id="43360-129">`System.Windows*` `System.Web.UI*`</span><span class="sxs-lookup"><span data-stu-id="43360-129">`System.Windows*` `System.Web.UI*`</span></span>

     <span data-ttu-id="43360-130">❌, tek bir uygulama modeli içindeki ad alanlarında bulunan türlere aynı adı vermez.</span><span class="sxs-lookup"><span data-stu-id="43360-130">❌ DO NOT give the same name to types in namespaces within a single application model.</span></span>

     <span data-ttu-id="43360-131">Örneğin, <xref:System.Web.UI?displayProperty=nameWithType> ad alanı zaten `Page`adlı bir tür içerdiğinden, <xref:System.Web.UI.Adapters?displayProperty=nameWithType> ad alanına `Page` adlı bir tür eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="43360-131">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>

- <span data-ttu-id="43360-132">**Altyapı ad alanları**</span><span class="sxs-lookup"><span data-stu-id="43360-132">**Infrastructure namespaces**</span></span>

     <span data-ttu-id="43360-133">Bu grup, ortak uygulamaların geliştirilmesi sırasında nadiren içeri aktarılan ad alanlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="43360-133">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="43360-134">Örneğin, `.Design` ad alanları genellikle programlama araçları geliştirilirken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="43360-134">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="43360-135">Bu ad alanlarında bulunan çakışmaları önleme kritik değildir.</span><span class="sxs-lookup"><span data-stu-id="43360-135">Avoiding conflicts with types in these namespaces is not critical.</span></span>

- <span data-ttu-id="43360-136">**Çekirdek ad alanları**</span><span class="sxs-lookup"><span data-stu-id="43360-136">**Core namespaces**</span></span>

     <span data-ttu-id="43360-137">Çekirdek ad alanları, uygulama modellerinin ad alanları ve altyapı ad alanları hariç tüm `System` ad alanlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="43360-137">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="43360-138">Temel ad alanları, diğerleri, `System`, `System.IO`, `System.Xml`ve `System.Net`arasında yer alır.</span><span class="sxs-lookup"><span data-stu-id="43360-138">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>

     <span data-ttu-id="43360-139">❌, çekirdek ad alanlarında herhangi bir türle çakışacak tür adları vermez.</span><span class="sxs-lookup"><span data-stu-id="43360-139">❌ DO NOT give types names that would conflict with any type in the Core namespaces.</span></span>

     <span data-ttu-id="43360-140">Örneğin, hiçbir `Stream` tür adı olarak kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="43360-140">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="43360-141">Yaygın olarak kullanılan bir tür olan <xref:System.IO.Stream?displayProperty=nameWithType>ile çakışır.</span><span class="sxs-lookup"><span data-stu-id="43360-141">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>

- <span data-ttu-id="43360-142">**Teknoloji ad alanı grupları**</span><span class="sxs-lookup"><span data-stu-id="43360-142">**Technology namespace groups**</span></span>

     <span data-ttu-id="43360-143">Bu kategori, `Microsoft.Build.Utilities` ve `Microsoft.Build.Tasks`gibi aynı ilk iki ad alanı düğümüne sahip tüm ad alanlarını içerir `(<Company>.<Technology>*`).</span><span class="sxs-lookup"><span data-stu-id="43360-143">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="43360-144">Tek bir teknolojiye ait olan türlerin birbirleriyle çakışmaması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="43360-144">It is important that types belonging to a single technology do not conflict with each other.</span></span>

     <span data-ttu-id="43360-145">❌, tek bir teknoloji içindeki diğer türlerle çakışacak tür adları atamayın.</span><span class="sxs-lookup"><span data-stu-id="43360-145">❌ DO NOT assign type names that would conflict with other types within a single technology.</span></span>

     <span data-ttu-id="43360-146">❌, teknoloji ad alanları ve uygulama modeli ad alanındaki türler arasında tür adı çakışmaları sunmaz (teknoloji uygulama modeliyle kullanılmak amaçlanmamışsa).</span><span class="sxs-lookup"><span data-stu-id="43360-146">❌ DO NOT introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>

 <span data-ttu-id="43360-147">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="43360-147">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="43360-148">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="43360-148">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="43360-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43360-149">See also</span></span>

- [<span data-ttu-id="43360-150">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="43360-150">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="43360-151">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="43360-151">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
