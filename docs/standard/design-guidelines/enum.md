---
title: Sabit listesi tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
author: KrzysztofCwalina
ms.openlocfilehash: 429f2e3821ff12ff4fc51b73c102ee3799d0228d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148138"
---
# <a name="enum-design"></a><span data-ttu-id="9a9b9-102">Sabit listesi tasarımı</span><span class="sxs-lookup"><span data-stu-id="9a9b9-102">Enum Design</span></span>
<span data-ttu-id="9a9b9-103">Numaralandırmalar özel türde bir değer türü var.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-103">Enums are a special kind of value type.</span></span> <span data-ttu-id="9a9b9-104">İki enum türü vardır: Basit sabit listeleri ve bayrak sabit listeleri.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-104">There are two kinds of enums: simple enums and flag enums.</span></span>  
  
 <span data-ttu-id="9a9b9-105">Basit numaralandırmalar küçük kapalı seçenek kümeleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-105">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="9a9b9-106">Yaygın olarak karşılaşılan örneklerden basit Enum renkleri kümesidir.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-106">A common example of the simple enum is a set of colors.</span></span>  
  
 <span data-ttu-id="9a9b9-107">Bayrak sabit listeleri, sabit listesi değerlerinin bit düzeyinde işlemler destekleyecek şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-107">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="9a9b9-108">Yaygın olarak karşılaşılan örneklerden bayrak sabit listesinin seçenekleri listesidir.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-108">A common example of the flags enum is a list of options.</span></span>  
  
 <span data-ttu-id="9a9b9-109">**✓ DO** döndürülen değer kümesini temsil eden değerler ve kesin tür parametreleri, özellikler, için bir numaralandırma kullanın.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-109">**✓ DO** use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>  
  
 <span data-ttu-id="9a9b9-110">**✓ DO** enum yerine statik sabitleri kullanarak ayrıcalık tanıma.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-110">**✓ DO** favor using an enum instead of static constants.</span></span>  
  
 <span data-ttu-id="9a9b9-111">**X DO NOT** enum (örneğin, işletim sistemi sürümü, adlarını arkadaşlarınız, vb.) açık kümeleri için kullanın.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-111">**X DO NOT** use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>  
  
 <span data-ttu-id="9a9b9-112">**X DO NOT** gelecekte kullanılmak üzere tasarlanmıştır ayrılmış enum değerleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-112">**X DO NOT** provide reserved enum values that are intended for future use.</span></span>  
  
 <span data-ttu-id="9a9b9-113">Her zaman yalnızca var olan bir enum değerleri daha sonraki bir aşamada ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-113">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="9a9b9-114">Bkz: [numaralandırmalar değerlere ekleme](#add_value) numaralandırmalar için değer ekleme hakkında daha fazla bilgi.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-114">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="9a9b9-115">Ayrılmış bir değerler yalnızca gerçek değerler kümesini pollute ve kullanıcı hatalarına neden eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-115">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>  
  
 <span data-ttu-id="9a9b9-116">**X AVOID** genel olarak tek bir değer ile numaralandırmaları gösterme.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-116">**X AVOID** publicly exposing enums with only one value.</span></span>  
  
 <span data-ttu-id="9a9b9-117">C API'lerinin sonra genişletilebilmek sağlamaya yönelik yaygın bir uygulama, yöntem imzaları için ayrılmış parametreler eklemektir.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-117">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="9a9b9-118">Ayrılmış tür parametreleri sabit listeleri ile tek bir varsayılan değer olarak ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-118">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="9a9b9-119">Bu yönetilen API'leri yapılmalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-119">This should not be done in managed APIs.</span></span> <span data-ttu-id="9a9b9-120">Yöntem aşırı yükleme parametreleri gelecek sürümleri ekleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-120">Method overloading allows adding parameters in future releases.</span></span>  
  
 <span data-ttu-id="9a9b9-121">**X DO NOT** numaralandırmaları sentinel değerler içerir.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-121">**X DO NOT** include sentinel values in enums.</span></span>  
  
 <span data-ttu-id="9a9b9-122">Bazen framework geliştiricilere yararlı olmasına rağmen sentinel değerleri framework kullanıcıları için kafa karıştırıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-122">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="9a9b9-123">Enum tarafından temsil edilen kümesinden şu değerlerden birini yerine enum durumunu izlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-123">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>  
  
 <span data-ttu-id="9a9b9-124">**✓ DO** basit numaralandırmalar sıfır değerini sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-124">**✓ DO** provide a value of zero on simple enums.</span></span>  
  
 <span data-ttu-id="9a9b9-125">Değer "None." gibi bir şey çağırmayı düşünün</span><span class="sxs-lookup"><span data-stu-id="9a9b9-125">Consider calling the value something like "None."</span></span> <span data-ttu-id="9a9b9-126">Bu tür bir değer bu belirli enum için uygun değilse, temel alınan değeri sıfır enum için en sık kullanılan varsayılan değer atanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-126">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>  
  
 <span data-ttu-id="9a9b9-127">**✓ CONSIDER** kullanarak <xref:System.Int32> (varsayılan olarak çoğu programlama dilleri) enum temel alınan türü olarak aşağıdakilerin doğru değilse:</span><span class="sxs-lookup"><span data-stu-id="9a9b9-127">**✓ CONSIDER** using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>  
  
-   <span data-ttu-id="9a9b9-128">Sabit listesi flags sabit listesi olduğu ve 32'den fazla bayraklarınız veya ileride daha fazlasına sahip olmayı beklediğiniz.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-128">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>  
  
-   <span data-ttu-id="9a9b9-129">Temel alınan türü farklı olması gereken <xref:System.Int32> boyutu farklı numaralandırmalar bekleniyor yönetilmeyen kod ile daha kolay birlikte çalışabilirlik.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-129">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>  
  
-   <span data-ttu-id="9a9b9-130">Küçük temel alınan türü alan önemli ölçüde tasarruf sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-130">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="9a9b9-131">Denetim akışı için bir bağımsız değişken olarak esas olarak kullanılmak üzere enum bekliyorsanız, boyutu küçük fark eder.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-131">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="9a9b9-132">Boyut tasarrufları önemli değilse:</span><span class="sxs-lookup"><span data-stu-id="9a9b9-132">The size savings might be significant if:</span></span>  
  
    -   <span data-ttu-id="9a9b9-133">Beklediğiniz alan çok sık örneklenmiş yapısı veya sınıf olarak kullanılacak sabit.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-133">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>  
  
    -   <span data-ttu-id="9a9b9-134">Büyük diziler veya koleksiyonları numaralandırma örnekleri oluşturmak için kullanıcıları beklediğiniz.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-134">You expect users to create large arrays or collections of the enum instances.</span></span>  
  
    -   <span data-ttu-id="9a9b9-135">Çok sayıda serileştirilecek enum örneklerini beklediğiniz.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-135">You expect a large number of instances of the enum to be serialized.</span></span>  
  
 <span data-ttu-id="9a9b9-136">Bellek içi kullanım için yönetilen nesneler her zaman olduğunu unutmayın `DWORD`-hizalı etkili bir şekilde birden fazla sıralanmış sabit veya bir örneğindeki toplam örnek boyutu her zaman olduğu için daha küçük bir enum ile paketini bir fark yaratmak için diğer küçük yapıları gerekir en fazla yuvarlanacak giderek bir `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-136">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>  
  
 <span data-ttu-id="9a9b9-137">**✓ DO** ad bayrağı numaralandırmaları çoğul adlar ve isim ifadeler ile ve basit numaralandırmaları tekil isimleri veya isim deyimleri ile.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-137">**✓ DO** name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="9a9b9-138">**X DO NOT** genişletmek <xref:System.Enum?displayProperty=nameWithType> doğrudan.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-138">**X DO NOT** extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>  
  
 <span data-ttu-id="9a9b9-139"><xref:System.Enum?displayProperty=nameWithType> özel bir türü CLR tarafından kullanıcı tanımlı sabit listeleri oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-139"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="9a9b9-140">Çoğu programlama dili, erişim için bu işlevi sağlayan bir programlama öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-140">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="9a9b9-141">Örneğin, C# dilinde `enum` anahtar sözcüğü bir numaralandırma tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-141">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a><span data-ttu-id="9a9b9-142">Tasarlama bayrak sabit listeleri</span><span class="sxs-lookup"><span data-stu-id="9a9b9-142">Designing Flag Enums</span></span>  
 <span data-ttu-id="9a9b9-143">**✓ DO** uygulamak <xref:System.FlagsAttribute?displayProperty=nameWithType> bayrağı numaralandırmalar için.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-143">**✓ DO** apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="9a9b9-144">Bu öznitelik basit numaralandırmalar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-144">Do not apply this attribute to simple enums.</span></span>  
  
 <span data-ttu-id="9a9b9-145">**✓ DO** bayrak enum değerleri için iki tabanların kullandığından, bunlar serbestçe bit düzeyinde OR işlemi kullanılarak birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-145">**✓ DO** use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>  
  
 <span data-ttu-id="9a9b9-146">**✓ CONSIDER** özel enum değerleri için yaygın olarak sağlayarak kullanılan bayrakları birleşimlerini.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-146">**✓ CONSIDER** providing special enum values for commonly used combinations of flags.</span></span>  
  
 <span data-ttu-id="9a9b9-147">Bit düzeyinde işlemler, Gelişmiş bir kavram olarak oldukça basittir ve Basit görevler için gerekli olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-147">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="9a9b9-148"><xref:System.IO.FileAccess.ReadWrite> özel bir değere örneğidir.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-148"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>  
  
 <span data-ttu-id="9a9b9-149">**X AVOID** burada belirli değerleri birleşimleridir geçersiz bayrak numaralandırmaları oluşturma.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-149">**X AVOID** creating flag enums where certain combinations of values are invalid.</span></span>  
  
 <span data-ttu-id="9a9b9-150">**X AVOID** kullanarak bayrak enum değerleri sıfır sürece değeri "tüm bayraklar temizlenmiştir" temsil eder ve uygun şekilde, bir sonraki kural tarafından belirlenen olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-150">**X AVOID** using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>  
  
 <span data-ttu-id="9a9b9-151">**✓ DO** bayrağı numaralandırmalar sıfır değeri adı `None`.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-151">**✓ DO** name the zero value of flag enums `None`.</span></span> <span data-ttu-id="9a9b9-152">Bayrak sabit listesi için değer her zaman "tüm bayraklar temizlenir." ortalama gerekir</span><span class="sxs-lookup"><span data-stu-id="9a9b9-152">For a flag enum, the value must always mean "all flags are cleared."</span></span>  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a><span data-ttu-id="9a9b9-153">Numaralandırmalar için değer ekleme</span><span class="sxs-lookup"><span data-stu-id="9a9b9-153">Adding Value to Enums</span></span>  
 <span data-ttu-id="9a9b9-154">Zaten kullanıma sonra bir sabit listesi için değerleri eklemeniz gerektiğini bulmak için çok yaygındır.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-154">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="9a9b9-155">Bir olası uygulama uyumluluğu sorun var. mevcut bir API'ye yeni eklenen değer döndürüldüğünde kötü yazılmış uygulamaları yeni değeri doğru şekilde işlememesi çünkü</span><span class="sxs-lookup"><span data-stu-id="9a9b9-155">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>  
  
 <span data-ttu-id="9a9b9-156">**✓ CONSIDER** küçük uyumluluk riski rağmen numaralandırmaları değerleri ekleme.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-156">**✓ CONSIDER** adding values to enums, despite a small compatibility risk.</span></span>  
  
 <span data-ttu-id="9a9b9-157">Uygulama uyumsuzlukları enum eklemeler nedeni ile ilgili gerçek veriler varsa, yeni ve eski değerleri döndüren yeni bir API eklemeyi göz önünde bulundurun ve yalnızca eski değerler döndüren sürmelidir eski API'yi kullanımdan.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-157">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="9a9b9-158">Bu işlem, mevcut uygulamalarınızı uyumlu kalmasını sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-158">This will ensure that your existing applications remain compatible.</span></span>  
  
 <span data-ttu-id="9a9b9-159">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="9a9b9-159">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9a9b9-160">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*</span><span class="sxs-lookup"><span data-stu-id="9a9b9-160">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a9b9-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-161">See also</span></span>

- [<span data-ttu-id="9a9b9-162">Tür Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9a9b9-162">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
- [<span data-ttu-id="9a9b9-163">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9a9b9-163">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
