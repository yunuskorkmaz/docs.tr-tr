---
title: Sabit Listesi Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
ms.openlocfilehash: 3b24bfefd3edb0585e9c6369e9b8151b17151661
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741706"
---
# <a name="enum-design"></a><span data-ttu-id="5cd19-102">Sabit Listesi Tasarımı</span><span class="sxs-lookup"><span data-stu-id="5cd19-102">Enum Design</span></span>

<span data-ttu-id="5cd19-103">Numaralandırmalar özel bir tür değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="5cd19-103">Enums are a special kind of value type.</span></span> <span data-ttu-id="5cd19-104">İki tür numaralandırmalar vardır: basit numaralandırmalar ve bayrak Numaralandırmalar.</span><span class="sxs-lookup"><span data-stu-id="5cd19-104">There are two kinds of enums: simple enums and flag enums.</span></span>

<span data-ttu-id="5cd19-105">Basit numaralandırmalar küçük kapalı seçim kümelerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5cd19-105">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="5cd19-106">Basit sabit listesinin yaygın bir örneği bir renk kümesidir.</span><span class="sxs-lookup"><span data-stu-id="5cd19-106">A common example of the simple enum is a set of colors.</span></span>

<span data-ttu-id="5cd19-107">Bayrak numaralandırmalarında, sabit listesi değerlerinde bit düzeyinde işlemleri destekleyecek şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5cd19-107">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="5cd19-108">Flags numaralandırmasının ortak bir örneği, seçeneklerin listesidir.</span><span class="sxs-lookup"><span data-stu-id="5cd19-108">A common example of the flags enum is a list of options.</span></span>

<span data-ttu-id="5cd19-109">✔️, parametreleri, özellikleri ve değer kümelerini temsil eden dönüş değerlerini kesin bir şekilde yazmak için enum kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cd19-109">✔️ DO use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>

<span data-ttu-id="5cd19-110">✔️ statik sabitler yerine bir numaralandırma kullanmayı tercih edin.</span><span class="sxs-lookup"><span data-stu-id="5cd19-110">✔️ DO favor using an enum instead of static constants.</span></span>

<span data-ttu-id="5cd19-111">❌, açık kümeler (örneğin, işletim sistemi sürümü, arkadaşlarınızın adları vb.) için bir sabit listesi kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="5cd19-111">❌ DO NOT use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>

<span data-ttu-id="5cd19-112">❌, gelecekte kullanılmak üzere tasarlanan ayrılmış sabit listesi değerleri sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="5cd19-112">❌ DO NOT provide reserved enum values that are intended for future use.</span></span>

<span data-ttu-id="5cd19-113">Daha sonraki bir aşamada mevcut sabit listesine her zaman bir değer ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cd19-113">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="5cd19-114">Numaralandırmaların değerlerini ekleme hakkında daha fazla ayrıntı için bkz. [numaralandırmalar Için değer ekleme](#add_value) .</span><span class="sxs-lookup"><span data-stu-id="5cd19-114">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="5cd19-115">Ayrılmış değerler yalnızca gerçek değerler kümesini Pollute ve Kullanıcı hatalarına neden olacak şekilde eğilimlidir.</span><span class="sxs-lookup"><span data-stu-id="5cd19-115">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>

<span data-ttu-id="5cd19-116">❌, Numaralandırmaların tek bir değerle genel olarak kullanıma sunulmasını ÖNLEYIN.</span><span class="sxs-lookup"><span data-stu-id="5cd19-116">❌ AVOID publicly exposing enums with only one value.</span></span>

<span data-ttu-id="5cd19-117">C API 'Lerinde gelecekteki genişletilebilirliği sağlamaya yönelik yaygın bir uygulama, ayrılmış parametreleri Yöntem imzalarına eklemektir.</span><span class="sxs-lookup"><span data-stu-id="5cd19-117">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="5cd19-118">Bu tür ayrılmış parametreler, tek bir varsayılan değer ile enum olarak ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="5cd19-118">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="5cd19-119">Bu, yönetilen API 'lerde yapılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5cd19-119">This should not be done in managed APIs.</span></span> <span data-ttu-id="5cd19-120">Yöntem aşırı yüklemesi gelecekteki sürümlerde parametre eklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="5cd19-120">Method overloading allows adding parameters in future releases.</span></span>

<span data-ttu-id="5cd19-121">❌ numaralandırmalarda Sentinel değerlerini dahil etmez.</span><span class="sxs-lookup"><span data-stu-id="5cd19-121">❌ DO NOT include sentinel values in enums.</span></span>

<span data-ttu-id="5cd19-122">Bazen Framework geliştiricilerine faydalı olsalar da, Sentinel değerleri Framework kullanıcılarına kafa karıştırıcı olur.</span><span class="sxs-lookup"><span data-stu-id="5cd19-122">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="5cd19-123">Numaralandırıcılardan temsil edilen kümeden biri yerine sabit listesinin durumunu izlemek için kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="5cd19-123">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>

<span data-ttu-id="5cd19-124">✔️ basit numaralandırmalar üzerinde sıfır değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5cd19-124">✔️ DO provide a value of zero on simple enums.</span></span>

<span data-ttu-id="5cd19-125">"None" gibi bir değer çağırmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="5cd19-125">Consider calling the value something like "None."</span></span> <span data-ttu-id="5cd19-126">Böyle bir değer bu sabit listesi için uygun değilse, sabit listesi için en yaygın varsayılan değere sıfır değeri atanmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5cd19-126">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>

<span data-ttu-id="5cd19-127">✔️, aşağıdakilerden herhangi biri doğru olmadığı sürece bir sabit listesinin temel alınan türü olarak <xref:System.Int32> (çoğu programlama dilinde varsayılan değer) kullanmayı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="5cd19-127">✔️ CONSIDER using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>

- <span data-ttu-id="5cd19-128">Sabit listesi bir bayrak numaralandırıcıdır ve 32 ' den fazla bayrak veya daha fazlasını bekliyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="5cd19-128">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>

- <span data-ttu-id="5cd19-129">Temel alınan türün, farklı boyutlu numaralandırmalar bekleyen yönetilmeyen kodla daha kolay birlikte çalışabilirlik için <xref:System.Int32> 'den farklı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cd19-129">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>

- <span data-ttu-id="5cd19-130">Daha küçük bir temel alınan tür, alana önemli ölçüde tasarruf oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="5cd19-130">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="5cd19-131">Numaralandırmanın genellikle denetim akışı için bağımsız değişken olarak kullanılmasını bekleliyorsanız, boyut biraz fark yapar.</span><span class="sxs-lookup"><span data-stu-id="5cd19-131">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="5cd19-132">Boyut tasarrufları önemli olabilir:</span><span class="sxs-lookup"><span data-stu-id="5cd19-132">The size savings might be significant if:</span></span>

  - <span data-ttu-id="5cd19-133">Sabit listesinin çok sık oluşturulan bir yapıda veya sınıfta bir alan olarak kullanılmasını beklediğinizi.</span><span class="sxs-lookup"><span data-stu-id="5cd19-133">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>

  - <span data-ttu-id="5cd19-134">Kullanıcıların, sabit listesi örneklerinin büyük dizilerini veya koleksiyonlarını oluşturmasını bekleolursunuz.</span><span class="sxs-lookup"><span data-stu-id="5cd19-134">You expect users to create large arrays or collections of the enum instances.</span></span>

  - <span data-ttu-id="5cd19-135">Sabit listesinin serileştirilmesi için çok sayıda örnek beklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cd19-135">You expect a large number of instances of the enum to be serialized.</span></span>

<span data-ttu-id="5cd19-136">Bellek içi kullanım için, yönetilen nesnelerin her zaman `DWORD`hizalı olduğunu unutmayın. bu nedenle, fark oluşturmak için bir örnekte birden çok sabit listesi veya diğer küçük yapıların, bir farklılık yapmak üzere bir örnek olarak daha küçük bir numaralandırma paketleyeceğinden, her zaman bir `DWORD`yukarı yuvarlanmasını sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="5cd19-136">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>

<span data-ttu-id="5cd19-137">✔️, çoğul isimler veya isim tümcecikleriyle sabit numaralandırmalar ve tekil isimler veya isim tümcecikleriyle basit Numaralandırmalar.</span><span class="sxs-lookup"><span data-stu-id="5cd19-137">✔️ DO name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>

<span data-ttu-id="5cd19-138">❌ doğrudan <xref:System.Enum?displayProperty=nameWithType> genişletmez.</span><span class="sxs-lookup"><span data-stu-id="5cd19-138">❌ DO NOT extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>

<span data-ttu-id="5cd19-139"><xref:System.Enum?displayProperty=nameWithType>, CLR tarafından Kullanıcı tanımlı numaralandırmalar oluşturmak için kullanılan özel bir türdür.</span><span class="sxs-lookup"><span data-stu-id="5cd19-139"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="5cd19-140">Çoğu programlama dili, bu işlevselliğe erişmenizi sağlayan bir programlama öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5cd19-140">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="5cd19-141">Örneğin, C# `enum` anahtar sözcüğü bir sabit listesini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5cd19-141">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>

<a name="design"></a>

### <a name="designing-flag-enums"></a><span data-ttu-id="5cd19-142">Bayrak numaralandırmaları tasarlama</span><span class="sxs-lookup"><span data-stu-id="5cd19-142">Designing Flag Enums</span></span>

<span data-ttu-id="5cd19-143">✔️ numaralandırmalarını işaretlemek için <xref:System.FlagsAttribute?displayProperty=nameWithType> uygulayın.</span><span class="sxs-lookup"><span data-stu-id="5cd19-143">✔️ DO apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="5cd19-144">Bu özniteliği basit Numaralandırmalar için uygulamayın.</span><span class="sxs-lookup"><span data-stu-id="5cd19-144">Do not apply this attribute to simple enums.</span></span>

<span data-ttu-id="5cd19-145">✔️, bir bit düzeyinde OR işlemi kullanılarak serbestçe birleştirilebilmesi için bayrak Enum değerleri için ikinin üslerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5cd19-145">✔️ DO use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>

<span data-ttu-id="5cd19-146">✔️, bayrakların yaygın olarak kullanılan birleşimleri için özel Enum değerleri sağlamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="5cd19-146">✔️ CONSIDER providing special enum values for commonly used combinations of flags.</span></span>

<span data-ttu-id="5cd19-147">Bit düzeyinde işlemler gelişmiş bir kavramdır ve basit görevler için gerekli olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5cd19-147">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="5cd19-148"><xref:System.IO.FileAccess.ReadWrite>, bu tür özel bir değere örnektir.</span><span class="sxs-lookup"><span data-stu-id="5cd19-148"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>

<span data-ttu-id="5cd19-149">❌ belirli değer birleşimlerinin geçersiz olduğu bayrak numaralandırmalarını oluşturmaktan KAÇıNıN.</span><span class="sxs-lookup"><span data-stu-id="5cd19-149">❌ AVOID creating flag enums where certain combinations of values are invalid.</span></span>

<span data-ttu-id="5cd19-150">değer "tüm bayraklar temizlenmedi" ve uygun şekilde adlandırılmış ve bir sonraki kılavuz tarafından belirtilen şekilde adlandırılmadığı sürece, sıfıra bayrak Enum değerlerini kullanmaktan KAÇıNıN. ❌</span><span class="sxs-lookup"><span data-stu-id="5cd19-150">❌ AVOID using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>

<span data-ttu-id="5cd19-151">✔️ `None`bayrak Numaralandırmaların sıfır değeri.</span><span class="sxs-lookup"><span data-stu-id="5cd19-151">✔️ DO name the zero value of flag enums `None`.</span></span> <span data-ttu-id="5cd19-152">Bayrak numaralandırması için, değer her zaman "tüm bayraklar temizlenmelidir." anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5cd19-152">For a flag enum, the value must always mean "all flags are cleared."</span></span>

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a><span data-ttu-id="5cd19-153">Numaralandırmalar için değer ekleme</span><span class="sxs-lookup"><span data-stu-id="5cd19-153">Adding Value to Enums</span></span>

<span data-ttu-id="5cd19-154">Zaten sevk ettikten sonra bir sabit listesine değer eklemeniz gerektiğini saptamak çok yaygındır.</span><span class="sxs-lookup"><span data-stu-id="5cd19-154">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="5cd19-155">Varolan bir API 'den yeni eklenen değer döndürüldüğünde olası bir uygulama uyumluluk sorunu vardır, çünkü kötü yazılmış uygulamalar yeni değeri doğru şekilde işleyemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="5cd19-155">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>

<span data-ttu-id="5cd19-156">✔️, küçük bir uyumluluk riskine karşın Numaralandırmaların değerlerini eklemeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="5cd19-156">✔️ CONSIDER adding values to enums, despite a small compatibility risk.</span></span>

<span data-ttu-id="5cd19-157">Bir sabit listesine eklemelere neden olan uygulama uyumsuzluklarını hakkında gerçek verileriniz varsa, yeni ve eski değerleri döndüren yeni bir API eklemeyi ve eski API 'yi kullanımdan kaldırmayı ve yalnızca eski değerleri döndürmeye devam etmeyi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="5cd19-157">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="5cd19-158">Bu, mevcut uygulamalarınızın uyumlu kalmasını sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="5cd19-158">This will ensure that your existing applications remain compatible.</span></span>

<span data-ttu-id="5cd19-159">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="5cd19-159">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="5cd19-160">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="5cd19-160">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="5cd19-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cd19-161">See also</span></span>

- [<span data-ttu-id="5cd19-162">Tür Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="5cd19-162">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="5cd19-163">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="5cd19-163">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
