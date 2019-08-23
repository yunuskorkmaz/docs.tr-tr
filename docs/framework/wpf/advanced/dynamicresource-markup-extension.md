---
title: DynamicResource Biçimlendirme Uzantısı
ms.date: 03/30/2017
f1_keywords:
- DynamicResource
- DynamicResourceExtension
helpviewer_keywords:
- XAML [WPF], DynamicResource markup extension
- DynamicResource markup extensions [WPF]
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
ms.openlocfilehash: 06355c64d36d2688ef027c1940688d4c87e51ec8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964793"
---
# <a name="dynamicresource-markup-extension"></a><span data-ttu-id="18a9c-102">DynamicResource Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="18a9c-102">DynamicResource Markup Extension</span></span>
<span data-ttu-id="18a9c-103">Herhangi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir özellik özniteliği için, bu değerin tanımlı bir kaynağa başvuru olarak erteleyerek bir değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="18a9c-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by deferring that value to be a reference to a defined resource.</span></span> <span data-ttu-id="18a9c-104">Bu kaynak için arama davranışı, çalışma zamanı aramasına benzer.</span><span class="sxs-lookup"><span data-stu-id="18a9c-104">Lookup behavior for that resource is analogous to run-time lookup.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="18a9c-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="18a9c-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{DynamicResource key}" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="18a9c-106">XAML Özellik Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="18a9c-106">XAML Property Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="18a9c-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="18a9c-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="18a9c-108">İstenen kaynak için anahtar.</span><span class="sxs-lookup"><span data-stu-id="18a9c-108">The key for the requested resource.</span></span> <span data-ttu-id="18a9c-109">Bu anahtar başlangıçta, biçimlendirme içinde bir kaynak oluşturulduysa veya kaynak kodda oluşturulduysa çağrılırken `key` <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> parametre olarak sağlanmışsa, [x:Key yönergesi](../../xaml-services/x-key-directive.md) tarafından atanır.</span><span class="sxs-lookup"><span data-stu-id="18a9c-109">This key was initially assigned by the [x:Key Directive](../../xaml-services/x-key-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18a9c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="18a9c-110">Remarks</span></span>  
 <span data-ttu-id="18a9c-111">, İlk derleme sırasında geçici bir ifade oluşturur ve Bunedenle,istenenkaynakdeğerigerçektenbirnesneoluşturmakiçingerekliolanakadarkaynaklarıaramayıerteleyin.`DynamicResource`</span><span class="sxs-lookup"><span data-stu-id="18a9c-111">A `DynamicResource` will create a temporary expression during the initial compilation and thus defer lookup for resources until the requested resource value is actually required in order to construct an object.</span></span> <span data-ttu-id="18a9c-112">Bu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfa yüklendikten sonra olabilir.</span><span class="sxs-lookup"><span data-stu-id="18a9c-112">This may potentially be after the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is loaded.</span></span> <span data-ttu-id="18a9c-113">Kaynak değeri, geçerli sayfa kapsamından başlayarak etkin olan tüm kaynak sözlüklerine karşı anahtar aramasına göre bulunur ve derlemeden yer tutucu ifadesinin yerine konur.</span><span class="sxs-lookup"><span data-stu-id="18a9c-113">The resource value will be found based on key search against all active resource dictionaries starting from the current page scope, and is substituted for the placeholder expression from compilation.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="18a9c-114">Bağımlılık özelliği önceliği açısından, bir `DynamicResource` ifade dinamik kaynak başvurusunun uygulandığı konuma eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="18a9c-114">In terms of dependency property precedence, a `DynamicResource` expression is equivalent to the position where the dynamic resource reference is applied.</span></span> <span data-ttu-id="18a9c-115">Önceden yerel değer olarak bir `DynamicResource` ifadeye sahip olan bir özellik için yerel bir değer ayarlarsanız, `DynamicResource` tamamen kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="18a9c-115">If you set a local value for a property that previously had a `DynamicResource` expression as the local value, the `DynamicResource` is completely removed.</span></span> <span data-ttu-id="18a9c-116">Ayrıntılar için bkz. [bağımlılık özelliği değer önceliği](dependency-property-value-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="18a9c-116">For details, see [Dependency Property Value Precedence](dependency-property-value-precedence.md).</span></span>  
  
 <span data-ttu-id="18a9c-117">Belirli kaynak erişim senaryoları, bir `DynamicResource` [StaticResource İşaretleme uzantısının](staticresource-markup-extension.md)aksine özellikle uygundur.</span><span class="sxs-lookup"><span data-stu-id="18a9c-117">Certain resource access scenarios are particularly appropriate for `DynamicResource` as opposed to a [StaticResource Markup Extension](staticresource-markup-extension.md).</span></span> <span data-ttu-id="18a9c-118">Ve ' `DynamicResource` ningörelibirleşmeveperformansetkilerihakkındabirtartışmaiçinbkz.xamlkaynakları.`StaticResource` [](xaml-resources.md)</span><span class="sxs-lookup"><span data-stu-id="18a9c-118">See [XAML Resources](xaml-resources.md) for a discussion about the relative merits and performance implications of `DynamicResource` and `StaticResource`.</span></span>  
  
 <span data-ttu-id="18a9c-119">Belirtilen <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> mevcut bir kaynağa karşılık gelen [x:Key yönergesi](../../xaml-services/x-key-directive.md) sayfa, uygulama, kullanılabilir denetim temaları ve dış kaynaklar ya da sistem kaynakları ve kaynak arama gerçekleşecektir. Bu sırada.</span><span class="sxs-lookup"><span data-stu-id="18a9c-119">The specified <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> should correspond to an existing resource determined by [x:Key Directive](../../xaml-services/x-key-directive.md) at some level in your page, application, the available control themes and external resources, or system resources, and the resource lookup will happen in that order.</span></span> <span data-ttu-id="18a9c-120">Statik ve dinamik kaynaklar için kaynak arama hakkında daha fazla bilgi için bkz. [xaml kaynakları](xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="18a9c-120">For more information about resource lookup for static and dynamic resources, see [XAML Resources](xaml-resources.md).</span></span>  
  
 <span data-ttu-id="18a9c-121">Kaynak anahtarı [XamlName dilbilgisinde](../../xaml-services/xamlname-grammar.md)tanımlanmış herhangi bir dize olabilir.</span><span class="sxs-lookup"><span data-stu-id="18a9c-121">A resource key may be any string defined in the [XamlName Grammar](../../xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="18a9c-122">Kaynak anahtarı, <xref:System.Type>gibi diğer nesne türleri de olabilir.</span><span class="sxs-lookup"><span data-stu-id="18a9c-122">A resource key may also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="18a9c-123">Bir <xref:System.Type> anahtar, denetimlerin temalar tarafından nasıl Stillenebilir.</span><span class="sxs-lookup"><span data-stu-id="18a9c-123">A <xref:System.Type> key is fundamental to how controls can be styled by themes.</span></span> <span data-ttu-id="18a9c-124">Daha fazla bilgi için bkz. [Denetim yazma genel bakış](../controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="18a9c-124">For more information, see [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="18a9c-125">Kaynak değerlerinin <xref:System.Windows.FrameworkElement.FindResource%2A>aranması için API 'ler, gibi, tarafından `DynamicResource`kullanılan kaynak arama mantığını da izler.</span><span class="sxs-lookup"><span data-stu-id="18a9c-125">APIs for lookup of resource values, such as <xref:System.Windows.FrameworkElement.FindResource%2A>, follow the same resource lookup logic as used by `DynamicResource`.</span></span>  
  
 <span data-ttu-id="18a9c-126">Bir kaynağa başvuruda bulunan alternatif bildirime dayalı bir değer, bir [StaticResource Işaretleme uzantısı](staticresource-markup-extension.md)olarak gelir.</span><span class="sxs-lookup"><span data-stu-id="18a9c-126">The alternative declarative means of referencing a resource is as a [StaticResource Markup Extension](staticresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="18a9c-127">Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="18a9c-127">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="18a9c-128">`DynamicResource` Tanımlayıcı dizeden sonra belirtilen dize belirteci, temel <xref:System.Windows.DynamicResourceExtension> uzantı sınıfının <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> değeri olarak atanır.</span><span class="sxs-lookup"><span data-stu-id="18a9c-128">The string token provided after the `DynamicResource` identifier string is assigned as the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.DynamicResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="18a9c-129">`DynamicResource`nesne öğesi söz dizimi içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="18a9c-129">`DynamicResource` can be used in object element syntax.</span></span> <span data-ttu-id="18a9c-130">Bu durumda, <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> özelliğinin değerini belirtmek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="18a9c-130">In this case, specifying the value of the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="18a9c-131">`DynamicResource`, <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> özelliği özellik = değer çifti olarak belirten ayrıntılı bir öznitelik kullanımında de kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="18a9c-131">`DynamicResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="18a9c-132">Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="18a9c-132">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="18a9c-133">, `DynamicResource` Gereken tek bir ayarlanabilir özelliğe sahip olduğundan, bu ayrıntılı kullanım tipik değildir.</span><span class="sxs-lookup"><span data-stu-id="18a9c-133">Because `DynamicResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="18a9c-134">İşlemci uygulamasında, bu biçimlendirme <xref:System.Windows.DynamicResourceExtension> uzantısının işlenmesi sınıfı tarafından tanımlanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18a9c-134">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.DynamicResourceExtension> class.</span></span>  
  
 <span data-ttu-id="18a9c-135">`DynamicResource`bir biçimlendirme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="18a9c-135">`DynamicResource` is a markup extension.</span></span> <span data-ttu-id="18a9c-136">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="18a9c-136">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="18a9c-137">İçindeki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tüm biçimlendirme uzantıları öznitelik sözdiziminde {ve} karakteri kullanır. Bu, bir işlemcinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tanıdığı bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="18a9c-137">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="18a9c-138">Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="18a9c-138">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18a9c-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18a9c-139">See also</span></span>

- [<span data-ttu-id="18a9c-140">XAML Kaynakları</span><span class="sxs-lookup"><span data-stu-id="18a9c-140">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="18a9c-141">Kaynaklar ve Kod</span><span class="sxs-lookup"><span data-stu-id="18a9c-141">Resources and Code</span></span>](resources-and-code.md)
- [<span data-ttu-id="18a9c-142">x:Key Yönergesi</span><span class="sxs-lookup"><span data-stu-id="18a9c-142">x:Key Directive</span></span>](../../xaml-services/x-key-directive.md)
- [<span data-ttu-id="18a9c-143">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="18a9c-143">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="18a9c-144">İşaretleme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="18a9c-144">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="18a9c-145">StaticResource İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="18a9c-145">StaticResource Markup Extension</span></span>](staticresource-markup-extension.md)
- [<span data-ttu-id="18a9c-146">İşaretleme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="18a9c-146">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
