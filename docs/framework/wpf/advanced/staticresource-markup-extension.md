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
ms.openlocfilehash: 7392be182aedeeebe6b7092f9868c1fabfaafcb7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963457"
---
# <a name="staticresource-markup-extension"></a><span data-ttu-id="4fb78-102">StaticResource Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="4fb78-102">StaticResource Markup Extension</span></span>
<span data-ttu-id="4fb78-103">Önceden tanımlanmış bir kaynağa başvuru [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arayarak herhangi bir özellik özniteliği için bir değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="4fb78-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="4fb78-104">Bu kaynak için arama davranışı, daha önce geçerli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfanın ve diğer uygulama kaynaklarının biçimlendirmesine göre yüklenen kaynakları arayan yükleme zamanı aramasına benzer ve bu kaynak değeri şu şekilde oluşturur çalışma zamanı nesnelerinde Özellik değeri.</span><span class="sxs-lookup"><span data-stu-id="4fb78-104">Lookup behavior for that resource is analogous to load-time lookup, which will look for resources that were previously loaded from the markup of the current [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page as well as other application sources, and will generate that resource value as the property value in the run-time objects.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="4fb78-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="4fb78-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="4fb78-106">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="4fb78-106">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="4fb78-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="4fb78-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="4fb78-108">İstenen kaynak için anahtar.</span><span class="sxs-lookup"><span data-stu-id="4fb78-108">The key for the requested resource.</span></span> <span data-ttu-id="4fb78-109">Bu anahtar başlangıçta, biçimlendirme içinde bir kaynak oluşturulduysa veya kaynak kodda oluşturulduysa çağrılırken `key` <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> parametre olarak sağlanmışsa, [x:Key yönergesi](../../xaml-services/x-key-directive.md) tarafından atanır.</span><span class="sxs-lookup"><span data-stu-id="4fb78-109">This key was initially assigned by the [x:Key Directive](../../xaml-services/x-key-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fb78-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4fb78-110">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4fb78-111">`StaticResource` ,[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Dosya içinde Sözcüksel olarak tanımlanmış bir kaynağa ileri bir başvuru yapmayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="4fb78-111">A `StaticResource` must not attempt to make a forward reference to a resource that is defined lexically further within the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="4fb78-112">Bunun denenmemesi desteklenmez, ancak böyle bir başvurunun başarısız olmasına rağmen, ileri başvurunun denenmemesi, bir <xref:System.Windows.ResourceDictionary> yükü temsil eden iç karma tabloları arandığı zaman bir yükleme süresi performans cezası olur.</span><span class="sxs-lookup"><span data-stu-id="4fb78-112">Attempting to do so is not supported, and even if such a reference does not fail, attempting the forward reference will incur a load time performance penalty when the internal hash tables representing a <xref:System.Windows.ResourceDictionary> are searched.</span></span> <span data-ttu-id="4fb78-113">En iyi sonuçları elde etmek için, kaynak sözlüklerinizin, ileri başvuruların önlenebilir şekilde ayarlanmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fb78-113">For best results, adjust the composition of your resource dictionaries such that forward references can be avoided.</span></span> <span data-ttu-id="4fb78-114">İleri başvuruyu önlememeniz durumunda, bunun yerine [DynamicResource Biçimlendirme Uzantısı](dynamicresource-markup-extension.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="4fb78-114">If you cannot avoid a forward reference, use [DynamicResource Markup Extension](dynamicresource-markup-extension.md) instead.</span></span>  
  
 <span data-ttu-id="4fb78-115">Belirtilen <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> var olan bir kaynağa karşılık gelmelidir; sayfanızda, uygulamanızda, kullanılabilir denetim temalarından ve dış kaynaklarda veya Sistem kaynaklarında bir [x:Key yönergesi](../../xaml-services/x-key-directive.md) ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4fb78-115">The specified <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> should correspond to an existing resource, identified with an [x:Key Directive](../../xaml-services/x-key-directive.md) at some level in your page, application, the available control themes and external resources, or system resources.</span></span> <span data-ttu-id="4fb78-116">Kaynak arama bu sırada oluşur.</span><span class="sxs-lookup"><span data-stu-id="4fb78-116">The resource lookup occurs in that order.</span></span> <span data-ttu-id="4fb78-117">Statik ve dinamik kaynaklar için kaynak arama davranışı hakkında daha fazla bilgi için bkz. [xaml kaynakları](xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="4fb78-117">For more information about resource lookup behavior for static and dynamic resources, see [XAML Resources](xaml-resources.md).</span></span>  
  
 <span data-ttu-id="4fb78-118">Kaynak anahtarı [XamlName dilbilgisinde](../../xaml-services/xamlname-grammar.md)tanımlanmış herhangi bir dize olabilir.</span><span class="sxs-lookup"><span data-stu-id="4fb78-118">A resource key can be any string defined in the [XamlName Grammar](../../xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="4fb78-119">Kaynak anahtarı, <xref:System.Type>gibi diğer nesne türleri de olabilir.</span><span class="sxs-lookup"><span data-stu-id="4fb78-119">A resource key can also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="4fb78-120">Bir <xref:System.Type> anahtar, bir örtülü stil anahtarı aracılığıyla denetimlerin temalar tarafından nasıl Stillenebilir.</span><span class="sxs-lookup"><span data-stu-id="4fb78-120">A <xref:System.Type> key is fundamental to how controls can be styled by themes, through an implicit style key.</span></span> <span data-ttu-id="4fb78-121">Daha fazla bilgi için bkz. [Denetim yazma genel bakış](../controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4fb78-121">For more information, see [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="4fb78-122">Bir kaynağa başvuran alternatif bildirime dayalı yol, [DynamicResource Biçimlendirme Uzantısı](dynamicresource-markup-extension.md)olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="4fb78-122">The alternative declarative means of referencing a resource is as a [DynamicResource Markup Extension](dynamicresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="4fb78-123">Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="4fb78-123">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="4fb78-124">`StaticResource` Tanımlayıcı dizeden sonra belirtilen dize belirteci, temel <xref:System.Windows.StaticResourceExtension> uzantı sınıfının <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> değeri olarak atanır.</span><span class="sxs-lookup"><span data-stu-id="4fb78-124">The string token provided after the `StaticResource` identifier string is assigned as the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.StaticResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="4fb78-125">`StaticResource`nesne öğesi söz dizimi içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4fb78-125">`StaticResource` can be used in object element syntax.</span></span> <span data-ttu-id="4fb78-126">Bu durumda, <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> özelliğinin değerini belirtmek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4fb78-126">In this case, specifying the value of the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="4fb78-127">`StaticResource`, <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> özelliği özellik = değer çifti olarak belirten ayrıntılı bir öznitelik kullanımında de kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="4fb78-127">`StaticResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="4fb78-128">Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="4fb78-128">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="4fb78-129">, `StaticResource` Gereken tek bir ayarlanabilir özelliğe sahip olduğundan, bu ayrıntılı kullanım tipik değildir.</span><span class="sxs-lookup"><span data-stu-id="4fb78-129">Because `StaticResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="4fb78-130">İşlemci uygulamasında, bu biçimlendirme <xref:System.Windows.StaticResourceExtension> uzantısının işlenmesi sınıfı tarafından tanımlanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fb78-130">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.StaticResourceExtension> class.</span></span>  
  
 <span data-ttu-id="4fb78-131">`StaticResource`bir biçimlendirme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="4fb78-131">`StaticResource` is a markup extension.</span></span> <span data-ttu-id="4fb78-132">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4fb78-132">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="4fb78-133">İçindeki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tüm biçimlendirme uzantıları öznitelik sözdiziminde {ve} karakteri kullanır. Bu, bir işlemcinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tanıdığı bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="4fb78-133">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="4fb78-134">Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="4fb78-134">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fb78-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fb78-135">See also</span></span>

- [<span data-ttu-id="4fb78-136">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4fb78-136">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="4fb78-137">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="4fb78-137">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="4fb78-138">İşaretleme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="4fb78-138">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="4fb78-139">XAML Kaynakları</span><span class="sxs-lookup"><span data-stu-id="4fb78-139">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="4fb78-140">Kaynaklar ve Kod</span><span class="sxs-lookup"><span data-stu-id="4fb78-140">Resources and Code</span></span>](resources-and-code.md)
