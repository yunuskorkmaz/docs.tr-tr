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
ms.openlocfilehash: c160322fb3834fcd705c0482f5e55c8da32d143b
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141248"
---
# <a name="staticresource-markup-extension"></a><span data-ttu-id="46ac2-102">StaticResource Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="46ac2-102">StaticResource Markup Extension</span></span>
<span data-ttu-id="46ac2-103">Önceden tanımlanmış bir kaynağa başvuru [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arayarak herhangi bir özellik özniteliği için bir değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="46ac2-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="46ac2-104">Bu kaynak için arama davranışı, daha önce geçerli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfanın ve diğer uygulama kaynaklarının biçimlendirmesine göre yüklenen kaynakları arayan yükleme zamanı aramasına benzer ve çalışma zamanı nesnelerinde Özellik değeri olarak bu kaynak değerini oluşturacaktır.</span><span class="sxs-lookup"><span data-stu-id="46ac2-104">Lookup behavior for that resource is analogous to load-time lookup, which will look for resources that were previously loaded from the markup of the current [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page as well as other application sources, and will generate that resource value as the property value in the run-time objects.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="46ac2-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="46ac2-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{StaticResource key}" ... />  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="46ac2-106">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="46ac2-106">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" ... />  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="46ac2-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="46ac2-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="46ac2-108">İstenen kaynak için anahtar.</span><span class="sxs-lookup"><span data-stu-id="46ac2-108">The key for the requested resource.</span></span> <span data-ttu-id="46ac2-109">Bu anahtar başlangıçta, biçimlendirme içinde bir kaynak oluşturulduysa veya kaynak kodda oluşturulduysa çağrılırken `key` <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> parametre olarak sağlanmışsa, [x:Key yönergesi](../../../desktop-wpf/xaml-services/xkey-directive.md) tarafından atanır.</span><span class="sxs-lookup"><span data-stu-id="46ac2-109">This key was initially assigned by the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46ac2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46ac2-110">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="46ac2-111">`StaticResource` , [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Dosya içinde Sözcüksel olarak tanımlanmış bir kaynağa ileri bir başvuru yapmayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="46ac2-111">A `StaticResource` must not attempt to make a forward reference to a resource that is defined lexically further within the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="46ac2-112">Bunun denenmemesi desteklenmez, ancak böyle bir başvurunun başarısız olmasına rağmen, ileri başvurunun denenmemesi, bir <xref:System.Windows.ResourceDictionary> yükü temsil eden iç karma tabloları arandığı zaman bir yükleme süresi performans cezası olur.</span><span class="sxs-lookup"><span data-stu-id="46ac2-112">Attempting to do so is not supported, and even if such a reference does not fail, attempting the forward reference will incur a load time performance penalty when the internal hash tables representing a <xref:System.Windows.ResourceDictionary> are searched.</span></span> <span data-ttu-id="46ac2-113">En iyi sonuçları elde etmek için, kaynak sözlüklerinizin, ileri başvuruların önlenebilir şekilde ayarlanmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46ac2-113">For best results, adjust the composition of your resource dictionaries such that forward references can be avoided.</span></span> <span data-ttu-id="46ac2-114">İleri başvuruyu önlememeniz durumunda, bunun yerine [DynamicResource Biçimlendirme Uzantısı](dynamicresource-markup-extension.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="46ac2-114">If you cannot avoid a forward reference, use [DynamicResource Markup Extension](dynamicresource-markup-extension.md) instead.</span></span>  
  
 <span data-ttu-id="46ac2-115">Belirtilen <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> var olan bir kaynağa karşılık gelmelidir; sayfanızda, uygulamanızda, kullanılabilir denetim temalarından ve dış kaynaklarda veya Sistem kaynaklarında bir [x:Key yönergesi](../../../desktop-wpf/xaml-services/xkey-directive.md) ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="46ac2-115">The specified <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> should correspond to an existing resource, identified with an [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) at some level in your page, application, the available control themes and external resources, or system resources.</span></span> <span data-ttu-id="46ac2-116">Kaynak arama bu sırada oluşur.</span><span class="sxs-lookup"><span data-stu-id="46ac2-116">The resource lookup occurs in that order.</span></span> <span data-ttu-id="46ac2-117">Statik ve dinamik kaynaklar için kaynak arama davranışı hakkında daha fazla bilgi için bkz. [xaml kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="46ac2-117">For more information about resource lookup behavior for static and dynamic resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>  
  
 <span data-ttu-id="46ac2-118">Kaynak anahtarı [XamlName dilbilgisinde](../../../desktop-wpf/xaml-services/xamlname-grammar.md)tanımlanmış herhangi bir dize olabilir.</span><span class="sxs-lookup"><span data-stu-id="46ac2-118">A resource key can be any string defined in the [XamlName Grammar](../../../desktop-wpf/xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="46ac2-119">Kaynak anahtarı, gibi diğer nesne türleri de olabilir <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="46ac2-119">A resource key can also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="46ac2-120">Bir <xref:System.Type> anahtar, bir örtülü stil anahtarı aracılığıyla denetimlerin temalar tarafından nasıl Stillenebilir.</span><span class="sxs-lookup"><span data-stu-id="46ac2-120">A <xref:System.Type> key is fundamental to how controls can be styled by themes, through an implicit style key.</span></span> <span data-ttu-id="46ac2-121">Daha fazla bilgi için bkz. [Denetim yazma genel bakış](../controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="46ac2-121">For more information, see [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="46ac2-122">Bir kaynağa başvuran alternatif bildirime dayalı yol, [DynamicResource Biçimlendirme Uzantısı](dynamicresource-markup-extension.md)olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="46ac2-122">The alternative declarative means of referencing a resource is as a [DynamicResource Markup Extension](dynamicresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="46ac2-123">Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="46ac2-123">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="46ac2-124">`StaticResource` Tanımlayıcı dizeden sonra belirtilen dize belirteci, temel <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> <xref:System.Windows.StaticResourceExtension> uzantı sınıfının değeri olarak atanır.</span><span class="sxs-lookup"><span data-stu-id="46ac2-124">The string token provided after the `StaticResource` identifier string is assigned as the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.StaticResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="46ac2-125">`StaticResource`nesne öğesi söz dizimi içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="46ac2-125">`StaticResource` can be used in object element syntax.</span></span> <span data-ttu-id="46ac2-126">Bu durumda, <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> özelliğinin değerini belirtmek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="46ac2-126">In this case, specifying the value of the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="46ac2-127">`StaticResource`, <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> özelliği özellik = değer çifti olarak belirten ayrıntılı bir öznitelik kullanımında de kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="46ac2-127">`StaticResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{StaticResource ResourceKey=key}" ... />  
```  
  
 <span data-ttu-id="46ac2-128">Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="46ac2-128">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="46ac2-129">, `StaticResource` Gereken tek bir ayarlanabilir özelliğe sahip olduğundan, bu ayrıntılı kullanım tipik değildir.</span><span class="sxs-lookup"><span data-stu-id="46ac2-129">Because `StaticResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="46ac2-130">İşlemci uygulamasında, bu biçimlendirme uzantısının işlenmesi <xref:System.Windows.StaticResourceExtension> sınıfı tarafından tanımlanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46ac2-130">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.StaticResourceExtension> class.</span></span>  
  
 <span data-ttu-id="46ac2-131">`StaticResource`bir biçimlendirme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="46ac2-131">`StaticResource` is a markup extension.</span></span> <span data-ttu-id="46ac2-132">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="46ac2-132">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="46ac2-133">İçindeki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tüm biçimlendirme uzantıları öznitelik sözdiziminde {ve} karakteri kullanır. Bu, bir işlemcinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tanıdığı bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="46ac2-133">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="46ac2-134">Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="46ac2-134">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46ac2-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46ac2-135">See also</span></span>

- [<span data-ttu-id="46ac2-136">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="46ac2-136">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="46ac2-137">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="46ac2-137">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="46ac2-138">Biçimlendirme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="46ac2-138">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="46ac2-139">XAML Kaynakları</span><span class="sxs-lookup"><span data-stu-id="46ac2-139">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="46ac2-140">Kaynaklar ve Kod</span><span class="sxs-lookup"><span data-stu-id="46ac2-140">Resources and Code</span></span>](resources-and-code.md)
