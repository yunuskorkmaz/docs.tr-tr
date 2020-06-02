---
title: Ad Alanlarının Adları
description: .NET kitaplıklarını genişleten ve bunlarla etkileşime geçen kitaplıklar tasarlamanın bir parçası olarak ad alanlarını adlandırmak için bu yönergeleri kullanın.
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
ms.openlocfilehash: e435e0281165b4a9f12bbccbeb10401b57375dcb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290207"
---
# <a name="names-of-namespaces"></a><span data-ttu-id="41e59-103">Ad Alanlarının Adları</span><span class="sxs-lookup"><span data-stu-id="41e59-103">Names of Namespaces</span></span>
<span data-ttu-id="41e59-104">Diğer adlandırma kılavuzlarında olduğu gibi, ad alanlarını Adlandırmanın amacı, programlama çerçevesini kullanarak, ad alanının içeriğinin büyük olasılıkla ne olduğunu hemen bilmenin ne kadar anlaşılır olduğunu oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="41e59-104">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="41e59-105">Aşağıdaki şablon ad alanlarını adlandırmak için genel kuralı belirtir:</span><span class="sxs-lookup"><span data-stu-id="41e59-105">The following template specifies the general rule for naming namespaces:</span></span>

 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`

 <span data-ttu-id="41e59-106">Aşağıda örnekleri verilmektedir:</span><span class="sxs-lookup"><span data-stu-id="41e59-106">The following are examples:</span></span>

 <span data-ttu-id="41e59-107">`Fabrikam.Math` `Litware.Security`</span><span class="sxs-lookup"><span data-stu-id="41e59-107">`Fabrikam.Math` `Litware.Security`</span></span>

 <span data-ttu-id="41e59-108">farklı şirketlerin ad alanlarının aynı ada sahip olmasını engellemek için, önek ad alanı adlarını bir şirket adıyla ✔️.</span><span class="sxs-lookup"><span data-stu-id="41e59-108">✔️ DO prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>

 <span data-ttu-id="41e59-109">✔️ bir ad alanı adının ikinci düzeyinde kararlı, sürümden bağımsız bir ürün adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="41e59-109">✔️ DO use a stable, version-independent product name at the second level of a namespace name.</span></span>

 <span data-ttu-id="41e59-110">❌Kurumların içindeki Grup adları kısa süreli olmaya eğiltiğinden, kuruluş hiyerarşilerini ad alanı hiyerarşilerindeki adların temeli olarak kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="41e59-110">❌ DO NOT use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="41e59-111">İlgili teknolojilerin grupları etrafında ad alanlarının hiyerarşisini düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="41e59-111">Organize the hierarchy of namespaces around groups of related technologies.</span></span>

 <span data-ttu-id="41e59-112">✔️ Pascalbüyük harfleri kullanır ve ad alanı bileşenlerini noktalarla ayırın (ör. `Microsoft.Office.PowerPoint` ).</span><span class="sxs-lookup"><span data-stu-id="41e59-112">✔️ DO use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="41e59-113">Markanız geleneksel olmayan büyük harfe kullanıyorsa, normal ad alanı büyük küçük harfe göre farklılık gösterir olsa da markanız tarafından tanımlanan büyük/küçük harfleri izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="41e59-113">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>

 <span data-ttu-id="41e59-114">✔️ Çoğul ad alanı adlarını kullanmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="41e59-114">✔️ CONSIDER using plural namespace names where appropriate.</span></span>

 <span data-ttu-id="41e59-115">Örneğin `System.Collection` yerine `System.Collections` kullanın.</span><span class="sxs-lookup"><span data-stu-id="41e59-115">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="41e59-116">Ancak, marka adları ve kısaltmalar bu kuralın istisnalardır.</span><span class="sxs-lookup"><span data-stu-id="41e59-116">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="41e59-117">Örneğin `System.IOs` yerine `System.IO` kullanın.</span><span class="sxs-lookup"><span data-stu-id="41e59-117">For example, use `System.IO` instead of `System.IOs`.</span></span>

 <span data-ttu-id="41e59-118">❌Ad alanı için aynı adı ve bu ad alanındaki türü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="41e59-118">❌ DO NOT use the same name for a namespace and a type in that namespace.</span></span>

 <span data-ttu-id="41e59-119">Örneğin, `Debug` ad alanı adı olarak kullanmayın ve ayrıca `Debug` aynı ad alanında adlı bir sınıf sağlayın.</span><span class="sxs-lookup"><span data-stu-id="41e59-119">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="41e59-120">Çeşitli derleyiciler, bu tür türlerin tam nitelikli olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="41e59-120">Several compilers require such types to be fully qualified.</span></span>

### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="41e59-121">Ad alanları ve tür adı çakışmaları</span><span class="sxs-lookup"><span data-stu-id="41e59-121">Namespaces and Type Name Conflicts</span></span>
 <span data-ttu-id="41e59-122">❌,, Ve gibi genel tür adları sunmaz `Element` `Node` `Log` `Message` .</span><span class="sxs-lookup"><span data-stu-id="41e59-122">❌ DO NOT introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>

 <span data-ttu-id="41e59-123">Bunu yapmanın çok büyük bir olasılığı, yaygın senaryolarda tür adı çakışmalarına yol açacaktır.</span><span class="sxs-lookup"><span data-stu-id="41e59-123">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="41e59-124">Genel tür adlarını (,,,) nitelemeniz gerekir `FormElement` `XmlNode` `EventLog` `SoapMessage` .</span><span class="sxs-lookup"><span data-stu-id="41e59-124">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>

 <span data-ttu-id="41e59-125">Farklı ad alanları kategorileri için tür adı çakışmalarını önlemeye yönelik özel yönergeler vardır.</span><span class="sxs-lookup"><span data-stu-id="41e59-125">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>

- <span data-ttu-id="41e59-126">**Uygulama modeli ad alanları**</span><span class="sxs-lookup"><span data-stu-id="41e59-126">**Application model namespaces**</span></span>

     <span data-ttu-id="41e59-127">Tek bir uygulama modeline ait olan ad alanları birlikte çok sık kullanılır, ancak bunlar, diğer uygulama modelleriyle ilgili ad alanları ile neredeyse hiç kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="41e59-127">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="41e59-128">Örneğin, ad alanı, <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanıyla birlikte çok seyrek kullanılır <xref:System.Web.UI?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="41e59-128">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="41e59-129">Aşağıda, iyi bilinen uygulama modeli ad alanı gruplarının listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="41e59-129">The following is a list of well-known application model namespace groups:</span></span>

     <span data-ttu-id="41e59-130">`System.Windows*` `System.Web.UI*`</span><span class="sxs-lookup"><span data-stu-id="41e59-130">`System.Windows*` `System.Web.UI*`</span></span>

     <span data-ttu-id="41e59-131">❌Tek bir uygulama modelinde ad alanlarında bulunan türlere aynı adı vermeyin.</span><span class="sxs-lookup"><span data-stu-id="41e59-131">❌ DO NOT give the same name to types in namespaces within a single application model.</span></span>

     <span data-ttu-id="41e59-132">Örneğin, ad alanı `Page` <xref:System.Web.UI.Adapters?displayProperty=nameWithType> <xref:System.Web.UI?displayProperty=nameWithType> zaten adlı bir tür içerdiğinden ad alanına adlı bir tür eklemeyin `Page` .</span><span class="sxs-lookup"><span data-stu-id="41e59-132">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>

- <span data-ttu-id="41e59-133">**Altyapı ad alanları**</span><span class="sxs-lookup"><span data-stu-id="41e59-133">**Infrastructure namespaces**</span></span>

     <span data-ttu-id="41e59-134">Bu grup, ortak uygulamaların geliştirilmesi sırasında nadiren içeri aktarılan ad alanlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="41e59-134">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="41e59-135">Örneğin, `.Design` ad alanları genellikle programlama araçları geliştirilirken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="41e59-135">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="41e59-136">Bu ad alanlarında bulunan çakışmaları önleme kritik değildir.</span><span class="sxs-lookup"><span data-stu-id="41e59-136">Avoiding conflicts with types in these namespaces is not critical.</span></span>

- <span data-ttu-id="41e59-137">**Çekirdek ad alanları**</span><span class="sxs-lookup"><span data-stu-id="41e59-137">**Core namespaces**</span></span>

     <span data-ttu-id="41e59-138">Çekirdek ad alanları `System` , uygulama modellerinin ad alanları ve altyapı ad alanları hariç tüm ad alanlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="41e59-138">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="41e59-139">Çekirdek ad alanları, diğerleri,,, ve arasında bulunur `System` `System.IO` `System.Xml` `System.Net` .</span><span class="sxs-lookup"><span data-stu-id="41e59-139">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>

     <span data-ttu-id="41e59-140">❌Çekirdek ad alanlarında herhangi bir türle çakışabilecek tür adları vermeyin.</span><span class="sxs-lookup"><span data-stu-id="41e59-140">❌ DO NOT give types names that would conflict with any type in the Core namespaces.</span></span>

     <span data-ttu-id="41e59-141">Örneğin, hiçbir koşulda `Stream` tür adı olarak kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="41e59-141">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="41e59-142"><xref:System.IO.Stream?displayProperty=nameWithType>Yaygın olarak kullanılan bir tür ile çakışır.</span><span class="sxs-lookup"><span data-stu-id="41e59-142">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>

- <span data-ttu-id="41e59-143">**Teknoloji ad alanı grupları**</span><span class="sxs-lookup"><span data-stu-id="41e59-143">**Technology namespace groups**</span></span>

     <span data-ttu-id="41e59-144">Bu kategori, ve gibi aynı ilk iki ad alanı düğümüne sahip tüm ad alanlarını içerir `(<Company>.<Technology>*` `Microsoft.Build.Utilities` `Microsoft.Build.Tasks` .</span><span class="sxs-lookup"><span data-stu-id="41e59-144">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="41e59-145">Tek bir teknolojiye ait olan türlerin birbirleriyle çakışmaması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="41e59-145">It is important that types belonging to a single technology do not conflict with each other.</span></span>

     <span data-ttu-id="41e59-146">❌Tek bir teknoloji içindeki diğer türlerle çakışacak tür adları atamayın.</span><span class="sxs-lookup"><span data-stu-id="41e59-146">❌ DO NOT assign type names that would conflict with other types within a single technology.</span></span>

     <span data-ttu-id="41e59-147">❌Teknoloji ad alanları ve uygulama modeli ad alanındaki türler arasında tür adı çakışmalarını tanıtmayın (teknoloji uygulama modeliyle kullanılmak amaçlanmamışsa).</span><span class="sxs-lookup"><span data-stu-id="41e59-147">❌ DO NOT introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>

 <span data-ttu-id="41e59-148">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="41e59-148">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="41e59-149">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="41e59-149">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="41e59-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41e59-150">See also</span></span>

- [<span data-ttu-id="41e59-151">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="41e59-151">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="41e59-152">Adlandırma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="41e59-152">Naming Guidelines</span></span>](naming-guidelines.md)
