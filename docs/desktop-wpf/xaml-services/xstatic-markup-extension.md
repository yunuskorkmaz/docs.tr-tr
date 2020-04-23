---
title: x:Static İşaretleme Uzantısı
ms.date: 03/30/2017
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
ms.openlocfilehash: fb9ee6807135f17fd9e0c799533bba28b369ebe2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072027"
---
# <a name="xstatic-markup-extension"></a><span data-ttu-id="3127b-102">x:Static İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="3127b-102">x:Static Markup Extension</span></span>

<span data-ttu-id="3127b-103">Ortak Dil Belirtimi (CLS) uyumlu bir şekilde tanımlanan statik by-value kodu varlığına başvurur.</span><span class="sxs-lookup"><span data-stu-id="3127b-103">References any static by-value code entity that is defined in a Common Language Specification (CLS)–compliant way.</span></span> <span data-ttu-id="3127b-104">Başvurulan statik özellik XAML'deki bir özelliğin değerini sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3127b-104">The static property that is referenced can be used to provide the value of a property in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="3127b-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="3127b-105">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Static prefix:typeName.staticMemberName}" .../>
```

## <a name="xaml-values"></a><span data-ttu-id="3127b-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="3127b-106">XAML Values</span></span>

| | |
|-|-|
|`prefix`|<span data-ttu-id="3127b-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3127b-107">Optional.</span></span> <span data-ttu-id="3127b-108">Eşlenen, varsayılan olmayan XAML ad alanına başvuran bir önek.</span><span class="sxs-lookup"><span data-stu-id="3127b-108">A prefix that refers to a mapped, non-default XAML namespace.</span></span> <span data-ttu-id="3127b-109">`prefix`varsayılan XAML ad alanından gelen statik özelliklere nadiren başvuru yaptığınızdan, kullanımda açıkça gösterilir.</span><span class="sxs-lookup"><span data-stu-id="3127b-109">`prefix` is shown explicitly in the usage because you rarely reference static properties that come from a default XAML namespace.</span></span> <span data-ttu-id="3127b-110">Bkz. Açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="3127b-110">See Remarks.</span></span>|
|`typeName`|<span data-ttu-id="3127b-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3127b-111">Required.</span></span> <span data-ttu-id="3127b-112">İstenilen statik üyeyi tanımlayan türün adı.</span><span class="sxs-lookup"><span data-stu-id="3127b-112">The name of the type that defines the desired static member.</span></span>|
|`staticMemberName`|<span data-ttu-id="3127b-113">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3127b-113">Required.</span></span> <span data-ttu-id="3127b-114">İstenilen statik değer üyesinin adı (sabit, statik özellik, alan veya numaralandırma değeri).</span><span class="sxs-lookup"><span data-stu-id="3127b-114">The name of the desired static value member (a constant, a static property, a field, or an enumeration value).</span></span>|

## <a name="remarks"></a><span data-ttu-id="3127b-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3127b-115">Remarks</span></span>

<span data-ttu-id="3127b-116">Başvurulan kod varlığı aşağıdakilerden biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="3127b-116">The code entity that is referenced must be one of the following:</span></span>

- <span data-ttu-id="3127b-117">Bir sabit</span><span class="sxs-lookup"><span data-stu-id="3127b-117">A constant</span></span>
- <span data-ttu-id="3127b-118">Statik bir özellik</span><span class="sxs-lookup"><span data-stu-id="3127b-118">A static property</span></span>
- <span data-ttu-id="3127b-119">Bir alan</span><span class="sxs-lookup"><span data-stu-id="3127b-119">A field</span></span>
- <span data-ttu-id="3127b-120">Numaralandırma değeri</span><span class="sxs-lookup"><span data-stu-id="3127b-120">An enumeration value</span></span>

<span data-ttu-id="3127b-121">Statik olmayan bir özellik gibi başka bir kod varlığı belirtmek, XAML biçimlendirme derlenmişse derleme zamanı hatasına veya XAML yük zamanı ayrıştırma özel durumu haline gelir.</span><span class="sxs-lookup"><span data-stu-id="3127b-121">Specifying any other code entity, such as a nonstatic property, causes a compile-time error if the XAML is markup compiled, or a XAML load-time parse exception.</span></span>

<span data-ttu-id="3127b-122">Geçerli XAML belgesi için varsayılan XAML ad alanında olmayan statik alanlara veya özelliklere `x:Static` başvuru yapabilirsiniz; ancak, bu bir önek eşleme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3127b-122">You can make `x:Static` references to static fields or properties that are not in the default XAML namespace for the current XAML document; however, this requires a prefix mapping.</span></span> <span data-ttu-id="3127b-123">XAML ad alanları, XAML belgesinin kök öğesi üzerinde hemen hemen her zaman tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3127b-123">XAML namespaces are almost always defined on the root element of the XAML document.</span></span>

<span data-ttu-id="3127b-124">Statik özellikleri için arama işlemleri .NET XAML Hizmetleri ve xaml okuyucuları ve XAML yazarları tarafından, varsayılan XAML şeması bağlamı yla çalışırken gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3127b-124">The lookup operations for static properties can be performed by .NET XAML Services and its XAML readers and XAML writers, when they are running with the default XAML schema context.</span></span> <span data-ttu-id="3127b-125">Bu XAML şeması bağlamı, nesne grafiği yapısı için gerekli statik değerleri sağlamak için CLR yansımasını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="3127b-125">This XAML schema context can use CLR reflection to provide the necessary static values for object graph construction.</span></span> <span data-ttu-id="3127b-126">Varsayılan `typeName` XAML şeması bağlamını kullanırken veya varolan tüm CLR tabanlı XAML uygulama çerçevelerini kullanırken bunlar temelde aynı ad olmasına rağmen, belirttiğiniz şey aslında bir CLR türü adı değil, BIR CLR türü adıdır.</span><span class="sxs-lookup"><span data-stu-id="3127b-126">The `typeName` you specify is actually a XAML type name, not a CLR type name, although these are essentially the same name when using the default XAML schema context or when using all existing CLR-based XAML-implementing frameworks.</span></span>

<span data-ttu-id="3127b-127">Doğrudan bir özelliğin değeri türü olmayan başvurular yaparken `x:Static` dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="3127b-127">Use caution when you make `x:Static` references that are not directly the type of a property's value.</span></span> <span data-ttu-id="3127b-128">XAML işleme dizisinde, biçimlendirme uzantısından sağlanan değerler ek değer dönüştürmeyi çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="3127b-128">In the XAML processing sequence, provided values from a markup extension do not invoke additional value conversion.</span></span> <span data-ttu-id="3127b-129">Başvurunuz `x:Static` bir metin dizesi oluştursa ve metin dizesini temel alan öznitelik değerleri için bir değer dönüştürmesi genellikle belirli bir üye veya iade türündeki herhangi bir üye değerleri için gerçekleşse bile bu durum geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3127b-129">This is true even if your `x:Static` reference creates a text string, and a value conversion for attribute values based on text string typically occurs either for that specific member or for any member values of the return type.</span></span>

<span data-ttu-id="3127b-130">Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="3127b-130">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="3127b-131">Tanımlayıcı dizesonra sağlanan `x:Static` dize belirteci alttaki <xref:System.Windows.Markup.StaticExtension.Member%2A> <xref:System.Windows.Markup.StaticExtension> uzantı sınıfının değeri olarak atanır.</span><span class="sxs-lookup"><span data-stu-id="3127b-131">The string token provided after the `x:Static` identifier string is assigned as the <xref:System.Windows.Markup.StaticExtension.Member%2A> value of the underlying <xref:System.Windows.Markup.StaticExtension> extension class.</span></span>

<span data-ttu-id="3127b-132">Teknik olarak mümkün olan iki XAML kullanımı daha vardır.</span><span class="sxs-lookup"><span data-stu-id="3127b-132">There are two other XAML usages that are technically possible.</span></span> <span data-ttu-id="3127b-133">Ancak, gereksiz yere ayrıntılı olduğundan bu kullanımlar daha az yaygındır:</span><span class="sxs-lookup"><span data-stu-id="3127b-133">However, these usages are less common because they are unnecessarily verbose:</span></span>

01. <span data-ttu-id="3127b-134">Nesne öğesi sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="3127b-134">Object element syntax.</span></span>

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

02. <span data-ttu-id="3127b-135">Başlatma dizesi için açık Üye özelliği ile sözdizimini atfedin.</span><span class="sxs-lookup"><span data-stu-id="3127b-135">Attribute syntax with explicit Member property for initialization string.</span></span>

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

<span data-ttu-id="3127b-136">.NET XAML Hizmetleri uygulamasında, bu biçimlendirme uzantısı için <xref:System.Windows.Markup.StaticExtension> işleme sınıf tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3127b-136">In .NET XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.StaticExtension> class.</span></span>

<span data-ttu-id="3127b-137">`x:Static`biçimlendirme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="3127b-137">`x:Static` is a markup extension.</span></span> <span data-ttu-id="3127b-138">XAML'deki tüm biçimlendirme `{` uzantıları, bir XAML işlemcisinin biçimlendirme uzantısının bir değer sağlaması gerektiğini kabul ettiği kural olan öznitelik sözdiziminde karakterleri kullanır. `}`</span><span class="sxs-lookup"><span data-stu-id="3127b-138">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must provide a value.</span></span> <span data-ttu-id="3127b-139">Biçimlendirme uzantıları hakkında daha fazla bilgi için [XAML Genel Bakış için Biçimlendirme Uzantıları'na](markup-extensions-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="3127b-139">For more information about markup extensions, see [Markup Extensions for XAML Overview](markup-extensions-overview.md).</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="3127b-140">WPF Kullanım Notları</span><span class="sxs-lookup"><span data-stu-id="3127b-140">WPF Usage Notes</span></span>

<span data-ttu-id="3127b-141">WPF programlama için kullandığınız varsayılan XAML ad alanı çok yararlı statik özellikler içermez ve yararlı statik özelliklerin çoğu gerektirmeden `{x:Static}` kullanımı kolaylaştıran tür dönüştürücüler gibi destek vardır.</span><span class="sxs-lookup"><span data-stu-id="3127b-141">The default XAML namespace you use for WPF programming does not contain many useful static properties, and most of the useful static properties have support such as type converters that facilitate the usage without requiring `{x:Static}` .</span></span> <span data-ttu-id="3127b-142">Statik özellikler için, aşağıdakilerden biri doğruysa, XAML ad alanı için bir önek eşlemelisiniz:</span><span class="sxs-lookup"><span data-stu-id="3127b-142">For static properties, you must map a prefix for a XAML namespace if one of the following is true:</span></span>

- <span data-ttu-id="3127b-143">WPF'de var olan ancak WPF için varsayılan XAML ad alanının bir`http://schemas.microsoft.com/winfx/2006/xaml/presentation`parçası olmayan bir türe başvurursunuz ( ).</span><span class="sxs-lookup"><span data-stu-id="3127b-143">You are referencing a type that exists in WPF but is not part of the default XAML namespace for WPF (`http://schemas.microsoft.com/winfx/2006/xaml/presentation`).</span></span> <span data-ttu-id="3127b-144">Bu kullanmak `x:Static`için oldukça yaygın bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="3127b-144">This is a fairly common scenario for using `x:Static`.</span></span> <span data-ttu-id="3127b-145">Örneğin, <xref:System.Environment> sınıfın statik `x:Static` özelliklerine başvurmak için <xref:System> CLR ad alanı ve mscorlib derlemesine XAML ad alanı eşlemesi içeren bir başvuru kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3127b-145">For example, you might use an `x:Static` reference with a XAML namespace mapping to the <xref:System> CLR namespace and mscorlib assembly in order to reference the static properties of the <xref:System.Environment> class.</span></span>

- <span data-ttu-id="3127b-146">Özel bir derlemeden bir türe başvuruyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="3127b-146">You are referencing a type from a custom assembly.</span></span>

- <span data-ttu-id="3127b-147">WPF derlemesinde var olan bir türe başvuruyorsunuz, ancak bu tür WPF varsayılan XAML ad alanının bir parçası olarak eşlenmemiş bir CLR ad alanı içindedir.</span><span class="sxs-lookup"><span data-stu-id="3127b-147">You are referencing a type that exists in a WPF assembly, but that type is within a CLR namespace that was not mapped to be part of the WPF default XAML namespace.</span></span> <span data-ttu-id="3127b-148">CLR ad alanlarının WPF için varsayılan XAML ad alanına eşlemesi çeşitli WPF derlemelerinde tanımlarla gerçekleştirilir (bu kavram hakkında daha fazla bilgi için Bkz. [XAML İsim Alanları ve WPF XAML için Namespace Eşleme).](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)</span><span class="sxs-lookup"><span data-stu-id="3127b-148">The mapping of CLR namespaces into the default XAML namespace for WPF is performed by definitions in the various WPF assemblies (for more information about this concept, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)).</span></span> <span data-ttu-id="3127b-149">Bu CLR ad alanı çoğunlukla XAML için tasarlanmayan sınıf tanımlarından oluşuyorsa, eşlenen CLR <xref:System.Windows.Threading>ad alanları kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3127b-149">Non-mapped CLR namespaces can exist if that CLR namespace is composed mostly of class definitions that are not typically intended for XAML, such as <xref:System.Windows.Threading>.</span></span>

<span data-ttu-id="3127b-150">WPF için öneklerin ve XAML ad alanlarının nasıl kullanılacağı hakkında daha fazla bilgi [için WPF XAML için XAML Ad Alanları ve Ad Alanı Eşleme'ye](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="3127b-150">For more information on how to use prefixes and XAML namespaces for WPF, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3127b-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3127b-151">See also</span></span>

- [<span data-ttu-id="3127b-152">x:Type İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="3127b-152">x:Type Markup Extension</span></span>](xtype-markup-extension.md)
- [<span data-ttu-id="3127b-153">WPF'den System.Xaml'e Geçirilen Türler</span><span class="sxs-lookup"><span data-stu-id="3127b-153">Types Migrated from WPF to System.Xaml</span></span>](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
