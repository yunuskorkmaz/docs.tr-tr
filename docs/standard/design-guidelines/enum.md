---
title: "Enum tasarım"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b7e1686dca2b96e339917b6dd4861f0f43d20d66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="enum-design"></a><span data-ttu-id="835f3-102">Enum tasarım</span><span class="sxs-lookup"><span data-stu-id="835f3-102">Enum Design</span></span>
<span data-ttu-id="835f3-103">Numaralandırmalar özel türde bir değer türü var.</span><span class="sxs-lookup"><span data-stu-id="835f3-103">Enums are a special kind of value type.</span></span> <span data-ttu-id="835f3-104">Numaralandırmalar iki tür vardır: Basit numaralandırmaları ve bayrağı numaralandırmaları.</span><span class="sxs-lookup"><span data-stu-id="835f3-104">There are two kinds of enums: simple enums and flag enums.</span></span>  
  
 <span data-ttu-id="835f3-105">Basit numaralandırmaları seçenek küçük kapalı kümeleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="835f3-105">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="835f3-106">Basit liste yaygın bir örneği, renkler kümesidir.</span><span class="sxs-lookup"><span data-stu-id="835f3-106">A common example of the simple enum is a set of colors.</span></span>  
  
 <span data-ttu-id="835f3-107">Bayrak numaralandırmalarında enum değerlerin Bitsel işlemleri desteklemek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="835f3-107">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="835f3-108">Bir ortak bayrakları enum seçeneklerin bir listesini örnektir.</span><span class="sxs-lookup"><span data-stu-id="835f3-108">A common example of the flags enum is a list of options.</span></span>  
  
 <span data-ttu-id="835f3-109">**✓ YAPMAK** döndürülen değer kümesini temsil eden değerler ve kesin tür parametreleri, özellikler, için bir numaralandırma kullanın.</span><span class="sxs-lookup"><span data-stu-id="835f3-109">**✓ DO** use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>  
  
 <span data-ttu-id="835f3-110">**✓ YAPMAK** enum yerine statik sabitleri kullanarak ayrıcalık tanıma.</span><span class="sxs-lookup"><span data-stu-id="835f3-110">**✓ DO** favor using an enum instead of static constants.</span></span>  
  
 <span data-ttu-id="835f3-111">**X yok** enum (örneğin, işletim sistemi sürümü, adlarını arkadaşlarınız, vb.) açık kümeleri için kullanın.</span><span class="sxs-lookup"><span data-stu-id="835f3-111">**X DO NOT** use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>  
  
 <span data-ttu-id="835f3-112">**X yok** gelecekte kullanılmak üzere tasarlanmıştır ayrılmış enum değerleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="835f3-112">**X DO NOT** provide reserved enum values that are intended for future use.</span></span>  
  
 <span data-ttu-id="835f3-113">Her zaman yalnızca daha sonraki bir aşamada varolan enum değerleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="835f3-113">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="835f3-114">Bkz: [numaralandırmaları değerleri ekleyerek](#add_value) numaralandırmalar için değer ekleme hakkında daha fazla bilgi.</span><span class="sxs-lookup"><span data-stu-id="835f3-114">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="835f3-115">Ayrılmış değerler yalnızca gerçek değerleri kümesi pollute ve kullanıcı hatalarına neden olma eğilimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="835f3-115">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>  
  
 <span data-ttu-id="835f3-116">**KAÇININ x** genel olarak tek bir değer ile numaralandırmaları gösterme.</span><span class="sxs-lookup"><span data-stu-id="835f3-116">**X AVOID** publicly exposing enums with only one value.</span></span>  
  
 <span data-ttu-id="835f3-117">C API'leri gelecekteki genişletilebilirlik sağlamaya yönelik yaygın bir yöntemi imzalar için ayrılmış parametreler eklemek için uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="835f3-117">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="835f3-118">Bu tür ayrılmış parametreleri tek varsayılan bir değerle numaralandırmaları olarak ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="835f3-118">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="835f3-119">Bu yönetilen API'leri yapılmalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="835f3-119">This should not be done in managed APIs.</span></span> <span data-ttu-id="835f3-120">Yöntem aşırı yükleme parametrelerini gelecekteki Sunumlarda eklemeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="835f3-120">Method overloading allows adding parameters in future releases.</span></span>  
  
 <span data-ttu-id="835f3-121">**X yok** numaralandırmaları sentinel değerler içerir.</span><span class="sxs-lookup"><span data-stu-id="835f3-121">**X DO NOT** include sentinel values in enums.</span></span>  
  
 <span data-ttu-id="835f3-122">Bazen framework geliştiricileri için faydalı olsa da, sentinel framework kullanıcılar için kafa karıştırıcı değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="835f3-122">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="835f3-123">Enum tarafından temsil edilen kümesinden olma değerlerden biri yerine enum durumunu izlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="835f3-123">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>  
  
 <span data-ttu-id="835f3-124">**✓ YAPMAK** basit numaralandırmalar sıfır değerini sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="835f3-124">**✓ DO** provide a value of zero on simple enums.</span></span>  
  
 <span data-ttu-id="835f3-125">Değer "None" gibi bir şey çağırmayı düşünün</span><span class="sxs-lookup"><span data-stu-id="835f3-125">Consider calling the value something like "None."</span></span> <span data-ttu-id="835f3-126">Böyle bir değer bu belirli enum için uygun değilse, temel alınan değerin sıfır enum için en sık kullanılan varsayılan değer atanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="835f3-126">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>  
  
 <span data-ttu-id="835f3-127">**✓ DÜŞÜNÜN** kullanarak <xref:System.Int32> (varsayılan olarak çoğu programlama dilleri) enum temel alınan türü olarak aşağıdakilerin doğru değilse:</span><span class="sxs-lookup"><span data-stu-id="835f3-127">**✓ CONSIDER** using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>  
  
-   <span data-ttu-id="835f3-128">Enum bayrakları enum olduğu ve 32'den fazla bayrakları sahip veya gelecekte daha fazla olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="835f3-128">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>  
  
-   <span data-ttu-id="835f3-129">Temel alınan türü farklı olması gereken <xref:System.Int32> boyutu farklı numaralandırmaları bekleniyor yönetilmeyen kod ile daha kolay birlikte çalışabilirlik.</span><span class="sxs-lookup"><span data-stu-id="835f3-129">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>  
  
-   <span data-ttu-id="835f3-130">Bir küçük temel alınan Tür alanında önemli tasarrufu neden olur.</span><span class="sxs-lookup"><span data-stu-id="835f3-130">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="835f3-131">Çoğunlukla akış denetimi için bağımsız değişken olarak kullanılacak enum bekliyorsanız, boyutu çok az fark etmez.</span><span class="sxs-lookup"><span data-stu-id="835f3-131">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="835f3-132">Boyut tasarrufları önemli varsa:</span><span class="sxs-lookup"><span data-stu-id="835f3-132">The size savings might be significant if:</span></span>  
  
    -   <span data-ttu-id="835f3-133">Çok sık örneklenen yapısı veya sınıf alanı olarak kullanılacak enum bekler.</span><span class="sxs-lookup"><span data-stu-id="835f3-133">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>  
  
    -   <span data-ttu-id="835f3-134">Enum örneklerinin koleksiyonlarını veya büyük diziler oluşturmak için kullanıcıların bekler.</span><span class="sxs-lookup"><span data-stu-id="835f3-134">You expect users to create large arrays or collections of the enum instances.</span></span>  
  
    -   <span data-ttu-id="835f3-135">Çok sayıda serileştirilmesi için enum örneklerini bekler.</span><span class="sxs-lookup"><span data-stu-id="835f3-135">You expect a large number of instances of the enum to be serialized.</span></span>  
  
 <span data-ttu-id="835f3-136">Bellek içi kullanım için yönetilen nesneler her zaman olduğunu unutmayın `DWORD`-hizalı birden çok numaralandırmaları veya diğer küçük yapıları örneğindeki toplam örnek boyutu her zaman olduğu için bir fark yapmak için daha küçük bir enum ile paketlemek için etkili bir şekilde gerekiyor en fazla yuvarlanmasını devam eden bir `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="835f3-136">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>  
  
 <span data-ttu-id="835f3-137">**✓ YAPMAK** ad bayrağı numaralandırmaları çoğul adlar ve isim ifadeler ile ve basit numaralandırmaları tekil isimleri veya isim deyimleri ile.</span><span class="sxs-lookup"><span data-stu-id="835f3-137">**✓ DO** name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="835f3-138">**X yok** genişletmek <xref:System.Enum?displayProperty=nameWithType> doğrudan.</span><span class="sxs-lookup"><span data-stu-id="835f3-138">**X DO NOT** extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>  
  
 <span data-ttu-id="835f3-139"><xref:System.Enum?displayProperty=nameWithType>özel bir türü CLR tarafından kullanıcı tanımlı numaralandırmalar oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="835f3-139"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="835f3-140">Bu işlevsellik, erişim sağlayan bir programlama öğesi çoğu programlama dilleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="835f3-140">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="835f3-141">Örneğin, C# ' ta `enum` anahtar sözcüğü bir numaralandırma tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="835f3-141">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a><span data-ttu-id="835f3-142">Tasarlama bayrağı numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="835f3-142">Designing Flag Enums</span></span>  
 <span data-ttu-id="835f3-143">**✓ YAPMAK** uygulamak <xref:System.FlagsAttribute?displayProperty=nameWithType> bayrağı numaralandırmalar için.</span><span class="sxs-lookup"><span data-stu-id="835f3-143">**✓ DO** apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="835f3-144">Bu öznitelik basit Enum değerleri için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="835f3-144">Do not apply this attribute to simple enums.</span></span>  
  
 <span data-ttu-id="835f3-145">**✓ YAPMAK** bayrak enum değerleri için iki tabanların kullandığından, bunlar serbestçe bit düzeyinde OR işlemi kullanılarak birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="835f3-145">**✓ DO** use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>  
  
 <span data-ttu-id="835f3-146">**✓ DÜŞÜNÜN** özel enum değerleri için yaygın olarak sağlayarak kullanılan bayrakları birleşimlerini.</span><span class="sxs-lookup"><span data-stu-id="835f3-146">**✓ CONSIDER** providing special enum values for commonly used combinations of flags.</span></span>  
  
 <span data-ttu-id="835f3-147">Bit düzeyinde işlemler, Gelişmiş bir kavramıdır ve basit görevleri için gerekli olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="835f3-147">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="835f3-148"><xref:System.IO.FileAccess.ReadWrite>özel bir değere örneğidir.</span><span class="sxs-lookup"><span data-stu-id="835f3-148"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>  
  
 <span data-ttu-id="835f3-149">**KAÇININ x** burada belirli değerleri birleşimleridir geçersiz bayrak numaralandırmaları oluşturma.</span><span class="sxs-lookup"><span data-stu-id="835f3-149">**X AVOID** creating flag enums where certain combinations of values are invalid.</span></span>  
  
 <span data-ttu-id="835f3-150">**KAÇININ x** kullanarak bayrak enum değerleri sıfır sürece değeri "tüm bayraklar temizlenmiştir" temsil eder ve uygun şekilde, bir sonraki kural tarafından belirlenen olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="835f3-150">**X AVOID** using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>  
  
 <span data-ttu-id="835f3-151">**✓ YAPMAK** bayrağı numaralandırmalar sıfır değeri adı `None`.</span><span class="sxs-lookup"><span data-stu-id="835f3-151">**✓ DO** name the zero value of flag enums `None`.</span></span> <span data-ttu-id="835f3-152">Bayrak enum için değeri her zaman "tüm bayraklar temizlenmiştir." anlamı gerekir</span><span class="sxs-lookup"><span data-stu-id="835f3-152">For a flag enum, the value must always mean "all flags are cleared."</span></span>  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a><span data-ttu-id="835f3-153">Numaralandırmalar için değer ekleme</span><span class="sxs-lookup"><span data-stu-id="835f3-153">Adding Value to Enums</span></span>  
 <span data-ttu-id="835f3-154">Zaten sevk olan sonra bir enum değerleri eklemeniz gerekir bulmak için çok yaygındır.</span><span class="sxs-lookup"><span data-stu-id="835f3-154">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="835f3-155">Bir olası uygulama uyumluluğu sorun var. Varolan bir API öğesinden yeni eklenen değer döndürüldüğünde kötü yazılmış uygulamalar yeni değer düzgün bir şekilde işler değil çünkü</span><span class="sxs-lookup"><span data-stu-id="835f3-155">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>  
  
 <span data-ttu-id="835f3-156">**✓ DÜŞÜNÜN** küçük uyumluluk riski rağmen numaralandırmaları değerleri ekleme.</span><span class="sxs-lookup"><span data-stu-id="835f3-156">**✓ CONSIDER** adding values to enums, despite a small compatibility risk.</span></span>  
  
 <span data-ttu-id="835f3-157">Enum eklemeler nedeni uygulama uyumsuzlukları ile ilgili gerçek veri varsa, yeni ve eski değerleri döndürür yeni bir API eklemeyi göz önünde bulundurun ve yalnızca eski değerler döndüren devam etmesi gerektiğini eski API alanı onaylanamadı.</span><span class="sxs-lookup"><span data-stu-id="835f3-157">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="835f3-158">Bu, mevcut uygulamalarınızı uyumlu kalmasını güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="835f3-158">This will ensure that your existing applications remain compatible.</span></span>  
  
 <span data-ttu-id="835f3-159">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="835f3-159">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="835f3-160">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="835f3-160">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="835f3-161">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="835f3-161">See Also</span></span>  
 [<span data-ttu-id="835f3-162">Türü tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="835f3-162">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="835f3-163">Framework tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="835f3-163">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
