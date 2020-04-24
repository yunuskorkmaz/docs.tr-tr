---
title: StaticResource Biçimlendirme Uzantısı
ms.date: 03/30/2017
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
ms.openlocfilehash: 5c0bb247bae525658d89d53f1672e57b87aba7bc
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646206"
---
# <a name="staticresource-markup-extension"></a><span data-ttu-id="7d5e2-102">StaticResource Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="7d5e2-102">StaticResource Markup Extension</span></span>
<span data-ttu-id="7d5e2-103">Zaten tanımlanmış bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kaynağa başvuruda bulunarak herhangi bir özellik özniteliği için bir değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="7d5e2-104">Bu kaynağın arama davranışı, daha önce geçerli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfanın biçimlendirmesinden yüklenen kaynakları ve diğer uygulama kaynaklarını arayacak ve bu kaynak değerini çalışma zamanı nesnelerindeki özellik değeri olarak oluşturacak yükleme zamanı aramaya benzer.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-104">Lookup behavior for that resource is analogous to load-time lookup, which will look for resources that were previously loaded from the markup of the current [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page as well as other application sources, and will generate that resource value as the property value in the run-time objects.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="7d5e2-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="7d5e2-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="7d5e2-106">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="7d5e2-106">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="7d5e2-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="7d5e2-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="7d5e2-108">İstenen kaynağın anahtarı.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-108">The key for the requested resource.</span></span> <span data-ttu-id="7d5e2-109">Bu anahtar başlangıçta [x:Key Yönergesi](../../../desktop-wpf/xaml-services/xkey-directive.md) tarafından bir kaynak biçimlendirme de `key` oluşturulduysa <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> veya kaynak kod olarak oluşturulduysa parametre olarak sağlanmışsa atanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-109">This key was initially assigned by the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d5e2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d5e2-110">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7d5e2-111">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] A, `StaticResource` dosya içinde sözlü olarak tanımlanan bir kaynağa ileri başvuru yapmaya çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-111">A `StaticResource` must not attempt to make a forward reference to a resource that is defined lexically further within the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="7d5e2-112">Bunu yapmaya çalışmak desteklenmez ve böyle bir başvuru başarısız olmasa bile, ileri başvuruyu denemek, bir <xref:System.Windows.ResourceDictionary> başvuruyu temsil eden iç karma tablolar arandığında bir yükleme süresi performans cezasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-112">Attempting to do so is not supported, and even if such a reference does not fail, attempting the forward reference will incur a load time performance penalty when the internal hash tables representing a <xref:System.Windows.ResourceDictionary> are searched.</span></span> <span data-ttu-id="7d5e2-113">En iyi sonuçlar için, kaynak sözlüklerinizin kompozisyonunu, ileriye dönük başvuruların önlenebileceği şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-113">For best results, adjust the composition of your resource dictionaries such that forward references can be avoided.</span></span> <span data-ttu-id="7d5e2-114">İleri ye dönük bir başvurudan kaçınamıyorsanız, bunun yerine [DynamicResource Biçimlendirme Uzantısı'nı](dynamicresource-markup-extension.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-114">If you cannot avoid a forward reference, use [DynamicResource Markup Extension](dynamicresource-markup-extension.md) instead.</span></span>  
  
 <span data-ttu-id="7d5e2-115">Belirtilen, <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> sayfanızda, uygulamanızda, kullanılabilir denetim temalarında ve dış kaynaklarda veya sistem kaynaklarında bir [düzeyde x:Key Yönergesi](../../../desktop-wpf/xaml-services/xkey-directive.md) ile tanımlanan varolan bir kaynağa karşılık gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-115">The specified <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> should correspond to an existing resource, identified with an [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) at some level in your page, application, the available control themes and external resources, or system resources.</span></span> <span data-ttu-id="7d5e2-116">Kaynak araması bu sırada gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-116">The resource lookup occurs in that order.</span></span> <span data-ttu-id="7d5e2-117">Statik ve dinamik kaynaklar için kaynak arama davranışı hakkında daha fazla bilgi için [Bkz. XAML Kaynakları.](../../../desktop-wpf/fundamentals/xaml-resources-define.md)</span><span class="sxs-lookup"><span data-stu-id="7d5e2-117">For more information about resource lookup behavior for static and dynamic resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>  
  
 <span data-ttu-id="7d5e2-118">Kaynak anahtarı [XamlName Grammar'da](../../../desktop-wpf/xaml-services/xamlname-grammar.md)tanımlanan herhangi bir dize olabilir.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-118">A resource key can be any string defined in the [XamlName Grammar](../../../desktop-wpf/xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="7d5e2-119">Kaynak anahtarı, <xref:System.Type>başka nesne türleri de olabilir.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-119">A resource key can also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="7d5e2-120">Anahtar, <xref:System.Type> denetimlerin örtülü bir stil anahtarı aracılığıyla temalar tarafından nasıl biçimlandırılabildiğini temel denedir.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-120">A <xref:System.Type> key is fundamental to how controls can be styled by themes, through an implicit style key.</span></span> <span data-ttu-id="7d5e2-121">Daha fazla bilgi için [bkz.](../controls/control-authoring-overview.md)</span><span class="sxs-lookup"><span data-stu-id="7d5e2-121">For more information, see [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="7d5e2-122">Bir kaynağa başvurmanın alternatif bildirimsel yolu [Dinamik Kaynak Biçimlendirme Uzantısı](dynamicresource-markup-extension.md)olarakdır.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-122">The alternative declarative means of referencing a resource is as a [DynamicResource Markup Extension](dynamicresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="7d5e2-123">Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-123">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="7d5e2-124">Tanımlayıcı dizesonra sağlanan `StaticResource` dize belirteci alttaki <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> <xref:System.Windows.StaticResourceExtension> uzantı sınıfının değeri olarak atanır.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-124">The string token provided after the `StaticResource` identifier string is assigned as the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.StaticResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="7d5e2-125">`StaticResource`nesne öğesi sözdiziminde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-125">`StaticResource` can be used in object element syntax.</span></span> <span data-ttu-id="7d5e2-126">Bu durumda, <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> özelliğin değerini belirterek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-126">In this case, specifying the value of the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="7d5e2-127">`StaticResource`<xref:System.Windows.StaticResourceExtension.ResourceKey%2A> özelliği özellik=değer çifti olarak belirten ayrıntılı bir öznitelik kullanımında da kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="7d5e2-127">`StaticResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="7d5e2-128">Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-128">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="7d5e2-129">Yalnızca `StaticResource` bir ayarlanabilen özelliği olduğundan, bu ayrıntılı kullanım tipik değildir.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-129">Because `StaticResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="7d5e2-130">İşlemci uygulamasında, bu biçimlendirme uzantısı için işleme <xref:System.Windows.StaticResourceExtension> sınıf tarafından tanımlanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d5e2-130">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.StaticResourceExtension> class.</span></span>  
  
 <span data-ttu-id="7d5e2-131">`StaticResource`biçimlendirme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-131">`StaticResource` is a markup extension.</span></span> <span data-ttu-id="7d5e2-132">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-132">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="7d5e2-133">Öznitelik sözdiziminde { ve } karakterlerini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanan tüm biçimlendirme uzantıları, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini kabul ettiği kuraldır.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-133">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="7d5e2-134">Daha fazla bilgi için [bkz: Biçimlendirme Uzantıları ve WPF XAML.](markup-extensions-and-wpf-xaml.md)</span><span class="sxs-lookup"><span data-stu-id="7d5e2-134">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d5e2-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d5e2-135">See also</span></span>

- [<span data-ttu-id="7d5e2-136">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7d5e2-136">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="7d5e2-137">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="7d5e2-137">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="7d5e2-138">Biçimlendirme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="7d5e2-138">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="7d5e2-139">XAML Kaynakları</span><span class="sxs-lookup"><span data-stu-id="7d5e2-139">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="7d5e2-140">Kaynaklar ve Kod</span><span class="sxs-lookup"><span data-stu-id="7d5e2-140">Resources and Code</span></span>](resources-and-code.md)
