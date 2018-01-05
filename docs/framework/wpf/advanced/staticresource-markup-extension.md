---
title: "StaticResource Biçimlendirme Uzantısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97b83feb9d19760208d9cc103290c5c6293c30c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="staticresource-markup-extension"></a><span data-ttu-id="d5b30-102">StaticResource Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="d5b30-102">StaticResource Markup Extension</span></span>
<span data-ttu-id="d5b30-103">İçin herhangi bir değer sağlar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] önceden tanımlanan bir kaynağa başvuru bakarak özellik özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d5b30-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="d5b30-104">Bu kaynak için arama davranışı önceden geçerli yüklenen kaynakları arar yükleme zamanı aramasına benzer [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfasında yanı sıra diğer uygulama kaynakları ve kaynak değeri olarak oluşturur çalışma zamanı nesnelerindeki özellik değeri.</span><span class="sxs-lookup"><span data-stu-id="d5b30-104">Lookup behavior for that resource is analogous to load-time lookup, which will look for resources that were previously loaded from the markup of the current [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page as well as other application sources, and will generate that resource value as the property value in the run-time objects.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="d5b30-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="d5b30-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="d5b30-106">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="d5b30-106">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="d5b30-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="d5b30-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="d5b30-108">İstenen kaynak için anahtar.</span><span class="sxs-lookup"><span data-stu-id="d5b30-108">The key for the requested resource.</span></span> <span data-ttu-id="d5b30-109">Bu anahtar tarafından başlangıçta atandığı [x: Key yönergesi](../../../../docs/framework/xaml-services/x-key-directive.md) bir kaynak biçimlendirme içinde oluşturulduğu veya olarak sağlanan `key` çağırırken parametre <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> kaynak kodunda oluşturduysanız.</span><span class="sxs-lookup"><span data-stu-id="d5b30-109">This key was initially assigned by the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5b30-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5b30-110">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d5b30-111">A `StaticResource` tanımlanan bir kaynağa ileriye doğru bir başvuru yapmak çalışmamalısınız içinde sözcüksel [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya.</span><span class="sxs-lookup"><span data-stu-id="d5b30-111">A `StaticResource` must not attempt to make a forward reference to a resource that is defined lexically further within the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="d5b30-112">Bunu yapmak çalışırken desteklenmiyor ve bu tür bir başvuru başarısız olsa bile, ileri başvuru girişimi yükleme zamanı performans cezasına sebep olabilir zaman temsil eden iç karma tabloları bir <xref:System.Windows.ResourceDictionary> aranır.</span><span class="sxs-lookup"><span data-stu-id="d5b30-112">Attempting to do so is not supported, and even if such a reference does not fail, attempting the forward reference will incur a load time performance penalty when the internal hash tables representing a <xref:System.Windows.ResourceDictionary> are searched.</span></span> <span data-ttu-id="d5b30-113">En iyi sonuçlar için İleri başvuruları önlenebilir gibi kaynak sözlüklerindeki oluşumunu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d5b30-113">For best results, adjust the composition of your resource dictionaries such that forward references can be avoided.</span></span> <span data-ttu-id="d5b30-114">İleriye doğru bir başvuru yoksayılamaz kullanırsanız [DynamicResource Biçimlendirme Uzantısı](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="d5b30-114">If you cannot avoid a forward reference, use [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) instead.</span></span>  
  
 <span data-ttu-id="d5b30-115">Belirtilen <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> ile tanımlanan, varolan bir kaynağa karşılık gelmelidir bir [x: Key yönergesi](../../../../docs/framework/xaml-services/x-key-directive.md) sayfanızı, uygulama, kullanılabilir denetim temalar ve dış kaynaklara veya sistem kaynakları düzeyde.</span><span class="sxs-lookup"><span data-stu-id="d5b30-115">The specified <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> should correspond to an existing resource, identified with an [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) at some level in your page, application, the available control themes and external resources, or system resources.</span></span> <span data-ttu-id="d5b30-116">Kaynak arama, o sırada oluşur.</span><span class="sxs-lookup"><span data-stu-id="d5b30-116">The resource lookup occurs in that order.</span></span> <span data-ttu-id="d5b30-117">Statik ve dinamik kaynaklara kaynak arama davranışı hakkında daha fazla bilgi için bkz: [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="d5b30-117">For more information about resource lookup behavior for static and dynamic resources, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="d5b30-118">Kaynak anahtarı içinde tanımlanan herhangi bir dize olabilir [XamlName Dilbilgisi](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="d5b30-118">A resource key can be any string defined in the [XamlName Grammar](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="d5b30-119">Kaynak anahtarı da diğer nesne türleri gibi olabilir bir <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="d5b30-119">A resource key can also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="d5b30-120">A <xref:System.Type> anahtarıdır nasıl denetimleri temalar tarafından örtülü stil anahtarı biçimlendirilebilir için temel.</span><span class="sxs-lookup"><span data-stu-id="d5b30-120">A <xref:System.Type> key is fundamental to how controls can be styled by themes, through an implicit style key.</span></span> <span data-ttu-id="d5b30-121">Daha fazla bilgi için bkz: [denetimine genel bakış yazma](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d5b30-121">For more information, see [Control Authoring Overview](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="d5b30-122">Alternatif bildirime dayanan bir kaynağa başvuran olduğundan bir [DynamicResource Biçimlendirme Uzantısı](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="d5b30-122">The alternative declarative means of referencing a resource is as a [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="d5b30-123">Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="d5b30-123">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="d5b30-124">Sonra sağlanan dize belirteci `StaticResource` kimlik dizesi olarak atandığı <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> temel değer <xref:System.Windows.StaticResourceExtension> uzantısı sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d5b30-124">The string token provided after the `StaticResource` identifier string is assigned as the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.StaticResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="d5b30-125">`StaticResource`nesne öğesi sözdiziminde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5b30-125">`StaticResource` can be used in object element syntax.</span></span> <span data-ttu-id="d5b30-126">Bu durumda, değerini belirten <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> özelliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d5b30-126">In this case, specifying the value of the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="d5b30-127">`StaticResource`belirten bir ayrıntılı öznitelik kullanımı da kullanılabilir <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> özelliği bir özellik olarak değer çifti =:</span><span class="sxs-lookup"><span data-stu-id="d5b30-127">`StaticResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="d5b30-128">Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d5b30-128">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="d5b30-129">Çünkü `StaticResource` yalnızca gerekli olan bir ayarlanabilir özelliği, bu ayrıntılı kullanım tipik sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d5b30-129">Because `StaticResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="d5b30-130">İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci uygulamasında, bu biçimlendirme uzantısı işlenmesi tarafından tanımlanan <xref:System.Windows.StaticResourceExtension> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d5b30-130">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.StaticResourceExtension> class.</span></span>  
  
 <span data-ttu-id="d5b30-131">`StaticResource`bir biçimlendirme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="d5b30-131">`StaticResource` is a markup extension.</span></span> <span data-ttu-id="d5b30-132">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d5b30-132">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="d5b30-133">İçindeki tüm biçimlendirme uzantıları [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanmak {ve} kurala göre kendi öznitelik sözdiziminde karakterler bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci tanıdığı biçimlendirme uzantısı öznitelik işlemelidir.</span><span class="sxs-lookup"><span data-stu-id="d5b30-133">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="d5b30-134">Daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="d5b30-134">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5b30-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d5b30-135">See Also</span></span>  
 [<span data-ttu-id="d5b30-136">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d5b30-136">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="d5b30-137">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="d5b30-137">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="d5b30-138">İşaretleme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="d5b30-138">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="d5b30-139">XAML Kaynakları</span><span class="sxs-lookup"><span data-stu-id="d5b30-139">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="d5b30-140">Kaynaklar ve Kod</span><span class="sxs-lookup"><span data-stu-id="d5b30-140">Resources and Code</span></span>](../../../../docs/framework/wpf/advanced/resources-and-code.md)
