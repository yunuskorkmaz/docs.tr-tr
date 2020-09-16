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
ms.openlocfilehash: 634a480b4d7446ed09708f6c91276d1c2f61d4a9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551617"
---
# <a name="xstatic-markup-extension"></a><span data-ttu-id="ce030-102">x:Static İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="ce030-102">x:Static Markup Extension</span></span>

<span data-ttu-id="ce030-103">Ortak dil belirtimi (CLS) ile uyumlu bir şekilde tanımlanan herhangi bir statik değere sahip kod varlığına başvurur.</span><span class="sxs-lookup"><span data-stu-id="ce030-103">References any static by-value code entity that is defined in a Common Language Specification (CLS)–compliant way.</span></span> <span data-ttu-id="ce030-104">Başvurulan static özelliği, XAML içindeki bir özelliğin değerini sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ce030-104">The static property that is referenced can be used to provide the value of a property in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="ce030-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="ce030-105">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Static prefix:typeName.staticMemberName}" .../>
```

## <a name="xaml-values"></a><span data-ttu-id="ce030-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="ce030-106">XAML Values</span></span>

| | |
|-|-|
|`prefix`|<span data-ttu-id="ce030-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ce030-107">Optional.</span></span> <span data-ttu-id="ce030-108">Eşlenmiş, varsayılan olmayan XAML ad alanına başvuran bir ön ek.</span><span class="sxs-lookup"><span data-stu-id="ce030-108">A prefix that refers to a mapped, non-default XAML namespace.</span></span> <span data-ttu-id="ce030-109">`prefix` , bir varsayılan XAML ad alanından gelen statik özelliklere nadiren başvurmanız nedeniyle açıkça kullanımda olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="ce030-109">`prefix` is shown explicitly in the usage because you rarely reference static properties that come from a default XAML namespace.</span></span> <span data-ttu-id="ce030-110">Bkz. açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="ce030-110">See Remarks.</span></span>|
|`typeName`|<span data-ttu-id="ce030-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ce030-111">Required.</span></span> <span data-ttu-id="ce030-112">İstenen statik üyeyi tanımlayan türün adı.</span><span class="sxs-lookup"><span data-stu-id="ce030-112">The name of the type that defines the desired static member.</span></span>|
|`staticMemberName`|<span data-ttu-id="ce030-113">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ce030-113">Required.</span></span> <span data-ttu-id="ce030-114">İstenen statik değer üyesinin adı (bir sabit, statik özellik, bir alan veya bir numaralandırma değeri).</span><span class="sxs-lookup"><span data-stu-id="ce030-114">The name of the desired static value member (a constant, a static property, a field, or an enumeration value).</span></span>|

## <a name="remarks"></a><span data-ttu-id="ce030-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce030-115">Remarks</span></span>

<span data-ttu-id="ce030-116">Başvurulan kod varlığı aşağıdakilerden biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="ce030-116">The code entity that is referenced must be one of the following:</span></span>

- <span data-ttu-id="ce030-117">Bir sabit</span><span class="sxs-lookup"><span data-stu-id="ce030-117">A constant</span></span>
- <span data-ttu-id="ce030-118">Statik Özellik</span><span class="sxs-lookup"><span data-stu-id="ce030-118">A static property</span></span>
- <span data-ttu-id="ce030-119">Bir alan</span><span class="sxs-lookup"><span data-stu-id="ce030-119">A field</span></span>
- <span data-ttu-id="ce030-120">Sabit listesi değeri</span><span class="sxs-lookup"><span data-stu-id="ce030-120">An enumeration value</span></span>

<span data-ttu-id="ce030-121">Statik olmayan bir özellik gibi başka bir kod varlığının belirtilmesi, XAML biçimlendirme derlenmişse ya da XAML yükleme zamanı ayrıştırma özel durumu olduğunda derleme zamanı hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="ce030-121">Specifying any other code entity, such as a nonstatic property, causes a compile-time error if the XAML is markup compiled, or a XAML load-time parse exception.</span></span>

<span data-ttu-id="ce030-122">`x:Static`GEÇERLI xaml belgesi için varsayılan xaml ad alanında olmayan statik alanlara veya özelliklere başvurular yapabilirsiniz; ancak bu, bir önek eşlemesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ce030-122">You can make `x:Static` references to static fields or properties that are not in the default XAML namespace for the current XAML document; however, this requires a prefix mapping.</span></span> <span data-ttu-id="ce030-123">Xaml ad alanları, XAML belgesinin kök öğesinde neredeyse her zaman tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ce030-123">XAML namespaces are almost always defined on the root element of the XAML document.</span></span>

<span data-ttu-id="ce030-124">Statik özellikler için arama işlemleri, .NET XAML Hizmetleri ve XAML okuyucuları ve XAML yazarları tarafından, varsayılan XAML şeması bağlamıyla çalışırken gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ce030-124">The lookup operations for static properties can be performed by .NET XAML Services and its XAML readers and XAML writers, when they are running with the default XAML schema context.</span></span> <span data-ttu-id="ce030-125">Bu XAML şema bağlamı, nesne grafiğinin oluşturulması için gerekli statik değerleri sağlamak üzere CLR yansımasını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="ce030-125">This XAML schema context can use CLR reflection to provide the necessary static values for object graph construction.</span></span> <span data-ttu-id="ce030-126">`typeName`Aslında BIR CLR tür adı değil, BIR xaml tür adı değil, bu, varsayılan xaml şema bağlamı kullanılırken veya var olan tüm clr tabanlı xaml uygulayan çerçeveler kullanılırken aynı ada sahip olsa da.</span><span class="sxs-lookup"><span data-stu-id="ce030-126">The `typeName` you specify is actually a XAML type name, not a CLR type name, although these are essentially the same name when using the default XAML schema context or when using all existing CLR-based XAML-implementing frameworks.</span></span>

<span data-ttu-id="ce030-127">`x:Static`Doğrudan bir özelliğin değerinin türü olmayan başvurular yaparken dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="ce030-127">Use caution when you make `x:Static` references that are not directly the type of a property's value.</span></span> <span data-ttu-id="ce030-128">XAML işleme dizisinde, bir biçimlendirme uzantısından gelen değerler, ek değer dönüşümü çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="ce030-128">In the XAML processing sequence, provided values from a markup extension do not invoke additional value conversion.</span></span> <span data-ttu-id="ce030-129">Bu, `x:Static` başvurunuz bir metin dizesi oluştursa ve metin dizesine dayalı öznitelik değerleri için değer dönüştürmesi genellikle söz konusu üye veya dönüş türünün herhangi bir üye değeri için ortaya çıkarsa, bu durum geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ce030-129">This is true even if your `x:Static` reference creates a text string, and a value conversion for attribute values based on text string typically occurs either for that specific member or for any member values of the return type.</span></span>

<span data-ttu-id="ce030-130">Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="ce030-130">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="ce030-131">Tanımlayıcı dizeden sonra belirtilen dize belirteci, `x:Static` <xref:System.Windows.Markup.StaticExtension.Member%2A> temel uzantı sınıfının değeri olarak atanır <xref:System.Windows.Markup.StaticExtension> .</span><span class="sxs-lookup"><span data-stu-id="ce030-131">The string token provided after the `x:Static` identifier string is assigned as the <xref:System.Windows.Markup.StaticExtension.Member%2A> value of the underlying <xref:System.Windows.Markup.StaticExtension> extension class.</span></span>

<span data-ttu-id="ce030-132">Teknik olarak mümkün olan iki farklı XAML kullanımı vardır.</span><span class="sxs-lookup"><span data-stu-id="ce030-132">There are two other XAML usages that are technically possible.</span></span> <span data-ttu-id="ce030-133">Ancak, bu kullanımlar gereksiz bir şekilde ayrıntılıdır, çünkü bu kullanımlar çok daha yaygındır:</span><span class="sxs-lookup"><span data-stu-id="ce030-133">However, these usages are less common because they are unnecessarily verbose:</span></span>

01. <span data-ttu-id="ce030-134">Nesne öğesi sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="ce030-134">Object element syntax.</span></span>

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

02. <span data-ttu-id="ce030-135">Başlatma dizesi için açık üye özelliği olan öznitelik sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="ce030-135">Attribute syntax with explicit Member property for initialization string.</span></span>

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

<span data-ttu-id="ce030-136">.NET XAML Hizmetleri uygulamasında, bu biçimlendirme uzantısının işlenmesi sınıfı tarafından tanımlanır <xref:System.Windows.Markup.StaticExtension> .</span><span class="sxs-lookup"><span data-stu-id="ce030-136">In .NET XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.StaticExtension> class.</span></span>

<span data-ttu-id="ce030-137">`x:Static` bir biçimlendirme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="ce030-137">`x:Static` is a markup extension.</span></span> <span data-ttu-id="ce030-138">XAML 'deki tüm biçimlendirme uzantıları, bir `{` `}` XAML işlemcisinin bir değer sağlaması gerektiğini tanıdığı kural olan öznitelik sözdiziminde ve karakterlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ce030-138">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must provide a value.</span></span> <span data-ttu-id="ce030-139">Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [xaml Için biçimlendirme uzantıları genel bakış](markup-extensions-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ce030-139">For more information about markup extensions, see [Markup Extensions for XAML Overview](markup-extensions-overview.md).</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="ce030-140">WPF kullanım notları</span><span class="sxs-lookup"><span data-stu-id="ce030-140">WPF Usage Notes</span></span>

<span data-ttu-id="ce030-141">WPF programlama için kullandığınız varsayılan XAML ad alanı çok sayıda faydalı statik özellik içermez ve yararlı statik özelliklerin çoğu, gerek olmadan kullanımı kolaylaştıran tür dönüştürücüler gibi destek içerir `{x:Static}` .</span><span class="sxs-lookup"><span data-stu-id="ce030-141">The default XAML namespace you use for WPF programming does not contain many useful static properties, and most of the useful static properties have support such as type converters that facilitate the usage without requiring `{x:Static}` .</span></span> <span data-ttu-id="ce030-142">Statik özellikler için aşağıdakilerden biri geçerliyse XAML ad alanı için bir ön eki eşlemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="ce030-142">For static properties, you must map a prefix for a XAML namespace if one of the following is true:</span></span>

- <span data-ttu-id="ce030-143">WPF 'de bulunan ancak WPF () için varsayılan XAML ad alanının bir parçası olmayan bir türe başvuruyorsunuz `http://schemas.microsoft.com/winfx/2006/xaml/presentation` .</span><span class="sxs-lookup"><span data-stu-id="ce030-143">You are referencing a type that exists in WPF but is not part of the default XAML namespace for WPF (`http://schemas.microsoft.com/winfx/2006/xaml/presentation`).</span></span> <span data-ttu-id="ce030-144">Bu, kullanımı için oldukça yaygın bir senaryodur `x:Static` .</span><span class="sxs-lookup"><span data-stu-id="ce030-144">This is a fairly common scenario for using `x:Static`.</span></span> <span data-ttu-id="ce030-145">Örneğin, `x:Static` <xref:System> sınıfın statik özelliklerine başvurmak için clr ad alanı ve mscorlib DERLEMESI için xaml ad alanı eşlemesi ile bir başvuru kullanabilirsiniz <xref:System.Environment> .</span><span class="sxs-lookup"><span data-stu-id="ce030-145">For example, you might use an `x:Static` reference with a XAML namespace mapping to the <xref:System> CLR namespace and mscorlib assembly in order to reference the static properties of the <xref:System.Environment> class.</span></span>

- <span data-ttu-id="ce030-146">Özel bir derlemeden bir türe başvuruyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="ce030-146">You are referencing a type from a custom assembly.</span></span>

- <span data-ttu-id="ce030-147">WPF derlemesinde bulunan bir türe başvuruyorsunuz, ancak bu tür WPF varsayılan XAML ad alanının parçası olacak şekilde eşlenmemiş bir CLR ad alanı içinde.</span><span class="sxs-lookup"><span data-stu-id="ce030-147">You are referencing a type that exists in a WPF assembly, but that type is within a CLR namespace that was not mapped to be part of the WPF default XAML namespace.</span></span> <span data-ttu-id="ce030-148">CLR ad alanlarının WPF için varsayılan XAML ad alanı eşlemesi, çeşitli WPF derlemelerindeki tanımlar tarafından gerçekleştirilir (Bu kavram hakkında daha fazla bilgi için bkz. [WPF XAML Için xaml ad alanları ve ad alanı eşlemesi](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml)).</span><span class="sxs-lookup"><span data-stu-id="ce030-148">The mapping of CLR namespaces into the default XAML namespace for WPF is performed by definitions in the various WPF assemblies (for more information about this concept, see [XAML Namespaces and Namespace Mapping for WPF XAML](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml)).</span></span> <span data-ttu-id="ce030-149">Eşlenen clr ad alanları, genellikle, gibi XAML için amaçlanan sınıf tanımlarından oluşuyorsa, bu CLR ad alanı var olabilir <xref:System.Windows.Threading> .</span><span class="sxs-lookup"><span data-stu-id="ce030-149">Non-mapped CLR namespaces can exist if that CLR namespace is composed mostly of class definitions that are not typically intended for XAML, such as <xref:System.Windows.Threading>.</span></span>

<span data-ttu-id="ce030-150">WPF için ön ekleri ve XAML ad alanlarını kullanma hakkında daha fazla bilgi için bkz. [WPF XAML Için xaml ad alanları ve ad alanı eşlemesi](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml).</span><span class="sxs-lookup"><span data-stu-id="ce030-150">For more information on how to use prefixes and XAML namespaces for WPF, see [XAML Namespaces and Namespace Mapping for WPF XAML](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml).</span></span>

## <a name="see-also"></a><span data-ttu-id="ce030-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce030-151">See also</span></span>

- [<span data-ttu-id="ce030-152">x:Type İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="ce030-152">x:Type Markup Extension</span></span>](xtype-markup-extension.md)
- [<span data-ttu-id="ce030-153">WPF'den System.Xaml'e Geçirilen Türler</span><span class="sxs-lookup"><span data-stu-id="ce030-153">Types Migrated from WPF to System.Xaml</span></span>](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
