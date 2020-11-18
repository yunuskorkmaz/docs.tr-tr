---
title: Sabit Listesi Tasarımı
description: Özel bir tür değer türü olan Numaralandırmalar için tasarım. Basit numaralandırmalar küçük ve kapalı seçim kümelerini tutar. Bayrak numaralandırmalarında sabit listesi değerlerinde bit düzeyinde işlemler desteklenir.
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
ms.openlocfilehash: a2e19197b114daa2a0956a6fc87231a6a81de916
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821365"
---
# <a name="enum-design"></a><span data-ttu-id="748ed-105">Sabit Listesi Tasarımı</span><span class="sxs-lookup"><span data-stu-id="748ed-105">Enum Design</span></span>

<span data-ttu-id="748ed-106">Numaralandırmalar özel bir tür değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="748ed-106">Enums are a special kind of value type.</span></span> <span data-ttu-id="748ed-107">İki tür numaralandırmalar vardır: basit numaralandırmalar ve bayrak Numaralandırmalar.</span><span class="sxs-lookup"><span data-stu-id="748ed-107">There are two kinds of enums: simple enums and flag enums.</span></span>

<span data-ttu-id="748ed-108">Basit numaralandırmalar küçük kapalı seçim kümelerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="748ed-108">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="748ed-109">Basit sabit listesinin yaygın bir örneği bir renk kümesidir.</span><span class="sxs-lookup"><span data-stu-id="748ed-109">A common example of the simple enum is a set of colors.</span></span>

<span data-ttu-id="748ed-110">Bayrak numaralandırmalarında, sabit listesi değerlerinde bit düzeyinde işlemleri destekleyecek şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="748ed-110">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="748ed-111">Flags numaralandırmasının ortak bir örneği, seçeneklerin listesidir.</span><span class="sxs-lookup"><span data-stu-id="748ed-111">A common example of the flags enum is a list of options.</span></span>

<span data-ttu-id="748ed-112">✔️, parametreleri, özellikleri ve değer kümelerini temsil eden dönüş değerlerini kesin bir şekilde yazmak için enum kullanın.</span><span class="sxs-lookup"><span data-stu-id="748ed-112">✔️ DO use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>

<span data-ttu-id="748ed-113">✔️ statik sabitler yerine bir numaralandırma kullanmayı tercih edin.</span><span class="sxs-lookup"><span data-stu-id="748ed-113">✔️ DO favor using an enum instead of static constants.</span></span>

<span data-ttu-id="748ed-114">❌ Açık kümeler (örneğin, işletim sistemi sürümü, arkadaşlarınızın adları vb.) için bir sabit listesi kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="748ed-114">❌ DO NOT use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>

<span data-ttu-id="748ed-115">❌ Gelecekte kullanılmak üzere tasarlanan ayrılmış sabit listesi değerleri SAĞLAMAMıŞTıR.</span><span class="sxs-lookup"><span data-stu-id="748ed-115">❌ DO NOT provide reserved enum values that are intended for future use.</span></span>

<span data-ttu-id="748ed-116">Daha sonraki bir aşamada mevcut sabit listesine her zaman bir değer ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="748ed-116">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="748ed-117">Numaralandırmaların değerlerini ekleme hakkında daha fazla ayrıntı için bkz. [numaralandırmalar Için değer ekleme](#add_value) .</span><span class="sxs-lookup"><span data-stu-id="748ed-117">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="748ed-118">Ayrılmış değerler yalnızca gerçek değerler kümesini Pollute ve Kullanıcı hatalarına neden olacak şekilde eğilimlidir.</span><span class="sxs-lookup"><span data-stu-id="748ed-118">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>

<span data-ttu-id="748ed-119">❌ Yalnızca bir değerli Numaralandırmaların genel kullanıma sunulmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="748ed-119">❌ AVOID publicly exposing enums with only one value.</span></span>

<span data-ttu-id="748ed-120">C API 'Lerinde gelecekteki genişletilebilirliği sağlamaya yönelik yaygın bir uygulama, ayrılmış parametreleri Yöntem imzalarına eklemektir.</span><span class="sxs-lookup"><span data-stu-id="748ed-120">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="748ed-121">Bu tür ayrılmış parametreler, tek bir varsayılan değer ile enum olarak ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="748ed-121">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="748ed-122">Bu, yönetilen API 'lerde yapılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="748ed-122">This should not be done in managed APIs.</span></span> <span data-ttu-id="748ed-123">Yöntem aşırı yüklemesi gelecekteki sürümlerde parametre eklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="748ed-123">Method overloading allows adding parameters in future releases.</span></span>

<span data-ttu-id="748ed-124">❌ Numaralandırmalarda Sentinel değerlerini eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="748ed-124">❌ DO NOT include sentinel values in enums.</span></span>

<span data-ttu-id="748ed-125">Bazen Framework geliştiricilerine faydalı olsalar da, Sentinel değerleri Framework kullanıcılarına kafa karıştırıcı olur.</span><span class="sxs-lookup"><span data-stu-id="748ed-125">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="748ed-126">Numaralandırıcılardan temsil edilen kümeden biri yerine sabit listesinin durumunu izlemek için kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="748ed-126">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>

<span data-ttu-id="748ed-127">✔️ basit numaralandırmalar üzerinde sıfır değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="748ed-127">✔️ DO provide a value of zero on simple enums.</span></span>

<span data-ttu-id="748ed-128">"None" gibi bir değer çağırmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="748ed-128">Consider calling the value something like "None."</span></span> <span data-ttu-id="748ed-129">Böyle bir değer bu sabit listesi için uygun değilse, sabit listesi için en yaygın varsayılan değere sıfır değeri atanmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="748ed-129">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>

<span data-ttu-id="748ed-130">✔️, <xref:System.Int32> aşağıdakilerden biri doğru olmadığı sürece bir sabit listesinin temel alınan türü olarak (çoğu programlama dilinde varsayılan değer) kullanmayı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="748ed-130">✔️ CONSIDER using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>

- <span data-ttu-id="748ed-131">Sabit listesi bir bayrak numaralandırıcıdır ve 32 ' den fazla bayrak veya daha fazlasını bekliyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="748ed-131">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>

- <span data-ttu-id="748ed-132">Temel alınan türün, <xref:System.Int32> farklı boyutlu numaralandırmalar bekleyen yönetilmeyen kodla daha kolay birlikte çalışabilirliğiyle farklı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="748ed-132">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>

- <span data-ttu-id="748ed-133">Daha küçük bir temel alınan tür, alana önemli ölçüde tasarruf oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="748ed-133">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="748ed-134">Numaralandırmanın genellikle denetim akışı için bağımsız değişken olarak kullanılmasını bekleliyorsanız, boyut biraz fark yapar.</span><span class="sxs-lookup"><span data-stu-id="748ed-134">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="748ed-135">Boyut tasarrufları önemli olabilir:</span><span class="sxs-lookup"><span data-stu-id="748ed-135">The size savings might be significant if:</span></span>

  - <span data-ttu-id="748ed-136">Sabit listesinin çok sık oluşturulan bir yapıda veya sınıfta bir alan olarak kullanılmasını beklediğinizi.</span><span class="sxs-lookup"><span data-stu-id="748ed-136">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>

  - <span data-ttu-id="748ed-137">Kullanıcıların, sabit listesi örneklerinin büyük dizilerini veya koleksiyonlarını oluşturmasını bekleolursunuz.</span><span class="sxs-lookup"><span data-stu-id="748ed-137">You expect users to create large arrays or collections of the enum instances.</span></span>

  - <span data-ttu-id="748ed-138">Sabit listesinin serileştirilmesi için çok sayıda örnek beklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="748ed-138">You expect a large number of instances of the enum to be serialized.</span></span>

<span data-ttu-id="748ed-139">Bellek içi kullanım için, yönetilen nesnelerin her zaman `DWORD` hizalandığını unutmayın. bu nedenle, fark oluşturmak için bir örnekte birden çok sabit listesi veya diğer küçük yapıların, bir farklılık yapmak için bir örnek içinde daha küçük bir numaralandırma paketleyeceğinden, her zaman bir değer vermek için, toplam örnek boyutu her zaman bir için yuvarlanır `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="748ed-139">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>

<span data-ttu-id="748ed-140">✔️, çoğul isimler veya isim tümcecikleriyle sabit numaralandırmalar ve tekil isimler veya isim tümcecikleriyle basit Numaralandırmalar.</span><span class="sxs-lookup"><span data-stu-id="748ed-140">✔️ DO name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>

<span data-ttu-id="748ed-141">❌ Doğrudan genişlemeyin <xref:System.Enum?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="748ed-141">❌ DO NOT extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>

<span data-ttu-id="748ed-142"><xref:System.Enum?displayProperty=nameWithType> , CLR tarafından Kullanıcı tanımlı numaralandırmalar oluşturmak için kullanılan özel bir türdür.</span><span class="sxs-lookup"><span data-stu-id="748ed-142"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="748ed-143">Çoğu programlama dili, bu işlevselliğe erişmenizi sağlayan bir programlama öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="748ed-143">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="748ed-144">Örneğin, C# ' de, `enum` bir sabit listesi tanımlamak için anahtar sözcüğü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="748ed-144">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>

<a name="design"></a>

### <a name="designing-flag-enums"></a><span data-ttu-id="748ed-145">Bayrak numaralandırmaları tasarlama</span><span class="sxs-lookup"><span data-stu-id="748ed-145">Designing Flag Enums</span></span>

<span data-ttu-id="748ed-146">✔️, <xref:System.FlagsAttribute?displayProperty=nameWithType> bayrak numaralandırmalarını uygulayın.</span><span class="sxs-lookup"><span data-stu-id="748ed-146">✔️ DO apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="748ed-147">Bu özniteliği basit Numaralandırmalar için uygulamayın.</span><span class="sxs-lookup"><span data-stu-id="748ed-147">Do not apply this attribute to simple enums.</span></span>

<span data-ttu-id="748ed-148">✔️, bir bit düzeyinde OR işlemi kullanılarak serbestçe birleştirilebilmesi için bayrak Enum değerleri için ikinin üslerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="748ed-148">✔️ DO use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>

<span data-ttu-id="748ed-149">✔️, bayrakların yaygın olarak kullanılan birleşimleri için özel Enum değerleri sağlamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="748ed-149">✔️ CONSIDER providing special enum values for commonly used combinations of flags.</span></span>

<span data-ttu-id="748ed-150">Bit düzeyinde işlemler gelişmiş bir kavramdır ve basit görevler için gerekli olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="748ed-150">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="748ed-151"><xref:System.IO.FileAccess.ReadWrite> , bu tür özel bir değere örnektir.</span><span class="sxs-lookup"><span data-stu-id="748ed-151"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>

<span data-ttu-id="748ed-152">❌ Belirli değer birleşimlerinin geçersiz olduğu bayrak numaralandırmalarını oluşturmaktan KAÇıNıN.</span><span class="sxs-lookup"><span data-stu-id="748ed-152">❌ AVOID creating flag enums where certain combinations of values are invalid.</span></span>

<span data-ttu-id="748ed-153">❌ Değer "tüm bayraklar temizlenmedi" ve uygun şekilde adlandırılmış ve bir sonraki kılavuz tarafından belirtilen şekilde adlandırılmadığı sürece, sıfır bayrak Enum değerlerini kullanmaktan KAÇıNıN.</span><span class="sxs-lookup"><span data-stu-id="748ed-153">❌ AVOID using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>

<span data-ttu-id="748ed-154">✔️ bayrak Numaralandırmaların sıfır değeri `None` .</span><span class="sxs-lookup"><span data-stu-id="748ed-154">✔️ DO name the zero value of flag enums `None`.</span></span> <span data-ttu-id="748ed-155">Bayrak numaralandırması için, değer her zaman "tüm bayraklar temizlenmelidir." anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="748ed-155">For a flag enum, the value must always mean "all flags are cleared."</span></span>

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a><span data-ttu-id="748ed-156">Numaralandırmalar için değer ekleme</span><span class="sxs-lookup"><span data-stu-id="748ed-156">Adding Value to Enums</span></span>

<span data-ttu-id="748ed-157">Zaten sevk ettikten sonra bir sabit listesine değer eklemeniz gerektiğini saptamak çok yaygındır.</span><span class="sxs-lookup"><span data-stu-id="748ed-157">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="748ed-158">Varolan bir API 'den yeni eklenen değer döndürüldüğünde olası bir uygulama uyumluluk sorunu vardır, çünkü kötü yazılmış uygulamalar yeni değeri doğru şekilde işleyemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="748ed-158">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>

<span data-ttu-id="748ed-159">✔️, küçük bir uyumluluk riskine karşın Numaralandırmaların değerlerini eklemeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="748ed-159">✔️ CONSIDER adding values to enums, despite a small compatibility risk.</span></span>

<span data-ttu-id="748ed-160">Bir sabit listesine eklemelere neden olan uygulama uyumsuzluklarını hakkında gerçek verileriniz varsa, yeni ve eski değerleri döndüren yeni bir API eklemeyi ve eski API 'yi kullanımdan kaldırmayı ve yalnızca eski değerleri döndürmeye devam etmeyi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="748ed-160">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="748ed-161">Bu, mevcut uygulamalarınızın uyumlu kalmasını sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="748ed-161">This will ensure that your existing applications remain compatible.</span></span>

<span data-ttu-id="748ed-162">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="748ed-162">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="748ed-163">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="748ed-163">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="748ed-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="748ed-164">See also</span></span>

- [<span data-ttu-id="748ed-165">Tür tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="748ed-165">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="748ed-166">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="748ed-166">Framework Design Guidelines</span></span>](index.md)
