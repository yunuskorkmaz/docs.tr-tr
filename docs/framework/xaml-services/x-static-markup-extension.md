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
ms.openlocfilehash: 8a14b00fe762d325028072cd0ea3eecf9b9206e3
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47083484"
---
# <a name="xstatic-markup-extension"></a><span data-ttu-id="11fa2-102">x:Static İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="11fa2-102">x:Static Markup Extension</span></span>
<span data-ttu-id="11fa2-103">Tanımlanan herhangi bir statik değere göre kod varlığa başvuran bir [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]– uyumlu şekilde.</span><span class="sxs-lookup"><span data-stu-id="11fa2-103">References any static by-value code entity that is defined in a [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]–compliant way.</span></span> <span data-ttu-id="11fa2-104">Başvurulan statik özelliği, XAML içinde bir özelliğinin değeri sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="11fa2-104">The static property that is referenced can be used to provide the value of a property in XAML.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="11fa2-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="11fa2-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="11fa2-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="11fa2-106">XAML Values</span></span>  
  
| | |  
|-|-|  
|`prefix`|<span data-ttu-id="11fa2-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="11fa2-107">Optional.</span></span> <span data-ttu-id="11fa2-108">Eşlenmiş, varsayılan olmayan bir XAML ad alanına başvuruda önek.</span><span class="sxs-lookup"><span data-stu-id="11fa2-108">A prefix that refers to a mapped, non-default XAML namespace.</span></span> <span data-ttu-id="11fa2-109">`prefix` açıkça varsayılan XAML ad alanından gelen statik özellikler nadiren aldığından kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="11fa2-109">`prefix` is shown explicitly in the usage because you rarely reference static properties that come from a default XAML namespace.</span></span> <span data-ttu-id="11fa2-110">Açıklamalara bakın.</span><span class="sxs-lookup"><span data-stu-id="11fa2-110">See Remarks.</span></span>|  
|`typeName`|<span data-ttu-id="11fa2-111">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="11fa2-111">Required.</span></span> <span data-ttu-id="11fa2-112">İstenen statik üyeyi tanımlayan türü adı.</span><span class="sxs-lookup"><span data-stu-id="11fa2-112">The name of the type that defines the desired static member.</span></span>|  
|`staticMemberName`|<span data-ttu-id="11fa2-113">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="11fa2-113">Required.</span></span> <span data-ttu-id="11fa2-114">(Bir sabit, statik bir özellik, alan veya bir sabit listesi değeri) istenen statik değere üyesinin adı.</span><span class="sxs-lookup"><span data-stu-id="11fa2-114">The name of the desired static value member (a constant, a static property, a field, or an enumeration value).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11fa2-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="11fa2-115">Remarks</span></span>  

<span data-ttu-id="11fa2-116">Başvurulan kod varlık aşağıdakilerden biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="11fa2-116">The code entity that is referenced must be one of the following:</span></span>  
  
-   <span data-ttu-id="11fa2-117">Bir sabiti</span><span class="sxs-lookup"><span data-stu-id="11fa2-117">A constant</span></span>  
-   <span data-ttu-id="11fa2-118">Statik bir özellik</span><span class="sxs-lookup"><span data-stu-id="11fa2-118">A static property</span></span>  
-   <span data-ttu-id="11fa2-119">Bir alan</span><span class="sxs-lookup"><span data-stu-id="11fa2-119">A field</span></span>  
-   <span data-ttu-id="11fa2-120">Bir sabit listesi değeri</span><span class="sxs-lookup"><span data-stu-id="11fa2-120">An enumeration value</span></span>

<span data-ttu-id="11fa2-121">XAML biçimlendirme veya bir XAML yükleme zamanı ayrıştırma özel durumu ise başka kod bir varlık, statik olmayan bir özellik gibi belirten bir derleme zamanı hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="11fa2-121">Specifying any other code entity, such as a nonstatic property, causes a compile-time error if the XAML is markup compiled, or a XAML load-time parse exception.</span></span>  

<span data-ttu-id="11fa2-122">Yapabileceğiniz `x:Static` başvurularını statik alanlar veya geçerli XAML belgesinin; varsayılan XAML ad alanı olmayan özellikler ancak bu bir ön ek eşleştirmesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="11fa2-122">You can make `x:Static` references to static fields or properties that are not in the default XAML namespace for the current XAML document; however, this requires a prefix mapping.</span></span> <span data-ttu-id="11fa2-123">XAML ad alanları, neredeyse her zaman XAML belgesinin kök öğesinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="11fa2-123">XAML namespaces are almost always defined on the root element of the XAML document.</span></span>  

<span data-ttu-id="11fa2-124">Varsayılan XAML şema içeriği ile çalışırken statik özellikler için arama işlemleri, .NET Framework XAML hizmetlerinde ve XAML okuyucular ve XAML yazarları tarafından gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="11fa2-124">The lookup operations for static properties can be performed by .NET Framework XAML Services and its XAML readers and XAML writers, when they are running with the default XAML schema context.</span></span> <span data-ttu-id="11fa2-125">Bu XAML şema içeriği CLR yansıma, gerekli statik değerler için Nesne grafiği oluşturmayı sağlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11fa2-125">This XAML schema context can use CLR reflection to provide the necessary static values for object graph construction.</span></span> <span data-ttu-id="11fa2-126">`typeName` Belirtmeniz aslında bir XAML türü adı, bir CLR türü adı değil, bunlar aslında aynı ada varsayılan XAML şema içeriği kullanırken ya da tüm var olan CLR tabanlı XAML-uygulama çerçeveleri kullanırken olmasına rağmen.</span><span class="sxs-lookup"><span data-stu-id="11fa2-126">The `typeName` you specify is actually a XAML type name, not a CLR type name, although these are essentially the same name when using the default XAML schema context or when using all existing CLR-based XAML-implementing frameworks.</span></span>  

<span data-ttu-id="11fa2-127">Yaptığınız kullanırken dikkatli `x:Static` doğrudan bir özelliğin değerinin türü olmayan başvurular.</span><span class="sxs-lookup"><span data-stu-id="11fa2-127">Use caution when you make `x:Static` references that are not directly the type of a property's value.</span></span> <span data-ttu-id="11fa2-128">XAML içinde dizisi, bir işaretleme uzantısı değerlerinden sağlanan işleme çağrılamadı ek değer dönüştürme.</span><span class="sxs-lookup"><span data-stu-id="11fa2-128">In the XAML processing sequence, provided values from a markup extension do not invoke additional value conversion.</span></span> <span data-ttu-id="11fa2-129">Bu doğru olsa bile, `x:Static` başvuru bir metin dizesi oluşturur ve bu belirli üye veya dönüş türünün hiçbir üyesi değerler için genellikle metin dizesine dayalı öznitelik değerleri için bir değer dönüştürme gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="11fa2-129">This is true even if your `x:Static` reference creates a text string, and a value conversion for attribute values based on text string typically occurs either for that specific member or for any member values of the return type.</span></span>  

<span data-ttu-id="11fa2-130">Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="11fa2-130">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="11fa2-131">Sonra sağlanan dize belirteci `x:Static` tanımlayıcı dizesi olarak atandığı <xref:System.Windows.Markup.StaticExtension.Member%2A> temel değer <xref:System.Windows.Markup.StaticExtension> uzantısı sınıfı.</span><span class="sxs-lookup"><span data-stu-id="11fa2-131">The string token provided after the `x:Static` identifier string is assigned as the <xref:System.Windows.Markup.StaticExtension.Member%2A> value of the underlying <xref:System.Windows.Markup.StaticExtension> extension class.</span></span>  

<span data-ttu-id="11fa2-132">Teknik olarak mümkün olan diğer iki XAML kullanımları vardır.</span><span class="sxs-lookup"><span data-stu-id="11fa2-132">There are two other XAML usages that are technically possible.</span></span> <span data-ttu-id="11fa2-133">Ancak, bu kullanımları gereksiz yere ayrıntılıdır oldukları için daha az yaygın olan:</span><span class="sxs-lookup"><span data-stu-id="11fa2-133">However, these usages are less common because they are unnecessarily verbose:</span></span>  

1.  <span data-ttu-id="11fa2-134">Nesne öğesi sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="11fa2-134">Object element syntax.</span></span>

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

2.  <span data-ttu-id="11fa2-135">Başlatma dizesi için açık bir üye özelliği ile söz dizimi özniteliği.</span><span class="sxs-lookup"><span data-stu-id="11fa2-135">Attribute syntax with explicit Member property for initialization string.</span></span>

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

<span data-ttu-id="11fa2-136">.NET Framework XAML hizmetlerinde uygulamasında, bu işaretleme uzantısının işlenmesi tarafından tanımlanan <xref:System.Windows.Markup.StaticExtension> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="11fa2-136">In the .NET Framework XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.StaticExtension> class.</span></span>  

<span data-ttu-id="11fa2-137">`x:Static` bir işaretleme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="11fa2-137">`x:Static` is a markup extension.</span></span> <span data-ttu-id="11fa2-138">XAML kullanım içindeki tüm biçimlendirme uzantıları `{` ve `}` karakter kendi öznitelik sözdizimi kuralı tarafından bir XAML işlemcisinin bir işaretleme uzantısı bir değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="11fa2-138">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must provide a value.</span></span> <span data-ttu-id="11fa2-139">Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz: [genel XAML işaretleme uzantılarına](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="11fa2-139">For more information about markup extensions, see [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="11fa2-140">WPF kullanım notları</span><span class="sxs-lookup"><span data-stu-id="11fa2-140">WPF Usage Notes</span></span>  
 <span data-ttu-id="11fa2-141">WPF programlama için kullandığınız varsayılan XAML ad alanı birçok yararlı statik özellikleri içermiyor ve kullanışlı statik özelliklerin çoğu sahip gerek kalmadan, kullanımı kolaylaştırmak tür dönüştürücüleri gibi desteği `{x:Static}` .</span><span class="sxs-lookup"><span data-stu-id="11fa2-141">The default XAML namespace you use for WPF programming does not contain many useful static properties, and most of the useful static properties have support such as type converters that facilitate the usage without requiring `{x:Static}` .</span></span> <span data-ttu-id="11fa2-142">Statik özellikler için aşağıdakilerden biri doğruysa bir XAML ad alanı için bir önek eşlemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="11fa2-142">For static properties, you must map a prefix for a XAML namespace if one of the following is true:</span></span>  
  
-   <span data-ttu-id="11fa2-143">WPF içinde var, ancak WPF için varsayılan XAML ad alanı bir parçası olmayan bir türe başvuruyor ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="11fa2-143">You are referencing a type that exists in WPF but is not part of the default XAML namespace for WPF ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)]).</span></span> <span data-ttu-id="11fa2-144">Bunu kullanmak için oldukça sık karşılaşılan bir senaryodur `x:Static`.</span><span class="sxs-lookup"><span data-stu-id="11fa2-144">This is a fairly common scenario for using `x:Static`.</span></span> <span data-ttu-id="11fa2-145">Örneğin, kullanabilirsiniz bir `x:Static` bir XAML ad alanı eşlemesi ile başvuru <xref:System> statik özelliklerini başvurmak için CLR ad alanı ve mscorlib derlemesi <xref:System.Environment> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="11fa2-145">For example, you might use an `x:Static` reference with a XAML namespace mapping to the <xref:System> CLR namespace and mscorlib assembly in order to reference the static properties of the <xref:System.Environment> class.</span></span>  
  
-   <span data-ttu-id="11fa2-146">Özel bir derlemeden bir tür başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="11fa2-146">You are referencing a type from a custom assembly.</span></span>  
  
-   <span data-ttu-id="11fa2-147">Varsayılan WPF XAML ad alanı bir parçası olarak eşlenmedi CLR ad alanı içinde türüdür, ancak bir WPF derlemede mevcut bir türe başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="11fa2-147">You are referencing a type that exists in a WPF assembly, but that type is within a CLR namespace that was not mapped to be part of the WPF default XAML namespace.</span></span> <span data-ttu-id="11fa2-148">CLR ad alanları için WPF eşleme varsayılan XAML ad alanına çeşitli WPF derlemeleri tanımlarında tarafından gerçekleştirilen (Bu kavramı hakkında daha fazla bilgi için bkz: [XAML ad alanları ve WPF XAML için Namespace eşlemesi](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)).</span><span class="sxs-lookup"><span data-stu-id="11fa2-148">The mapping of CLR namespaces into the default XAML namespace for WPF is performed by definitions in the various WPF assemblies (for more information about this concept, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)).</span></span> <span data-ttu-id="11fa2-149">XAML için genellikle gibi amaçlanmayan çoğunlukla sınıf tanımları, CLR ad uzayı oluşturuluyorsa olmayan eşlenen bir CLR ad alanları varolabilir <xref:System.Windows.Threading>.</span><span class="sxs-lookup"><span data-stu-id="11fa2-149">Non-mapped CLR namespaces can exist if that CLR namespace is composed mostly of class definitions that are not typically intended for XAML, such as <xref:System.Windows.Threading>.</span></span>  
  
 <span data-ttu-id="11fa2-150">WPF için ön ekleri ve XAML ad alanları kullanma hakkında daha fazla bilgi için bkz. [XAML ad alanları ve WPF XAML Namespace eşleme](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="11fa2-150">For more information on how to use prefixes and XAML namespaces for WPF, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11fa2-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="11fa2-151">See Also</span></span>  
 [<span data-ttu-id="11fa2-152">x:Type İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="11fa2-152">x:Type Markup Extension</span></span>](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [<span data-ttu-id="11fa2-153">WPF'den System.Xaml'e Geçirilen Türler</span><span class="sxs-lookup"><span data-stu-id="11fa2-153">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
