---
title: TemplateBinding Biçimlendirme Uzantısı
ms.date: 03/30/2017
f1_keywords:
- TemplateBinding
- TemplateBindingExtension
helpviewer_keywords:
- XAML [WPF], TemplateBinding markup extension
- TemplateBinding markup extensions [WPF]
ms.assetid: 1d25bbfc-dbc2-499d-9f12-419d23d4ac6a
ms.openlocfilehash: 1e4adc4c0b5579ca6c75324f358e70edd48273cc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372236"
---
# <a name="templatebinding-markup-extension"></a><span data-ttu-id="b6939-102">TemplateBinding Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="b6939-102">TemplateBinding Markup Extension</span></span>
<span data-ttu-id="b6939-103">Denetim şablonunda bir özelliğin değerini, şablonlu denetim üzerinde açıkça gösterilen başka bir özelliğin değerine bağlar.</span><span class="sxs-lookup"><span data-stu-id="b6939-103">Links the value of a property in a control template to be the value of another property on the templated control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="b6939-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="b6939-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a><span data-ttu-id="b6939-105">XAML Öznitelik Kullanımı (şablon veya stilde Ayarlayıcı özelliği için)</span><span class="sxs-lookup"><span data-stu-id="b6939-105">XAML Attribute Usage (for Setter property in template or style)</span></span>  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="b6939-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="b6939-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`propertyName`|<span data-ttu-id="b6939-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> ayarlayıcı sözdiziminde ayarlanan özelliği.</span><span class="sxs-lookup"><span data-stu-id="b6939-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> of the property being set in the setter syntax.</span></span>|  
|`sourceProperty`|<span data-ttu-id="b6939-108">Tarafından belirtilen şablonu, oluşturulan türde bulunan başka bir bağımlılık özelliği, <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b6939-108">Another dependency property that exists on the type being templated, specified by its <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span></span><br /><br /> <span data-ttu-id="b6939-109">- veya -</span><span class="sxs-lookup"><span data-stu-id="b6939-109">- or -</span></span><br /><br /> <span data-ttu-id="b6939-110">Şablonu oluşturulan hedef türünden farklı bir tür tarafından tanımlanan "aşağı noktalanmış" özellik adı.</span><span class="sxs-lookup"><span data-stu-id="b6939-110">A "dotted-down" property name that is defined by a different type than the target type being templated.</span></span> <span data-ttu-id="b6939-111">Bu, aslında bir <xref:System.Windows.PropertyPath>.</span><span class="sxs-lookup"><span data-stu-id="b6939-111">This is actually a <xref:System.Windows.PropertyPath>.</span></span> <span data-ttu-id="b6939-112">Bkz: [PropertyPath XAML söz dizimi](propertypath-xaml-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="b6939-112">See [PropertyPath XAML Syntax](propertypath-xaml-syntax.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6939-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6939-113">Remarks</span></span>  
 <span data-ttu-id="b6939-114">A `TemplateBinding` en iyi duruma getirilmiş formudur bir [bağlama](binding-markup-extension.md) , şablon senaryoları için benzer bir `Binding` ile oluşturulan `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span><span class="sxs-lookup"><span data-stu-id="b6939-114">A `TemplateBinding` is an optimized form of a [Binding](binding-markup-extension.md) for template scenarios, analogous to a `Binding` constructed with `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="b6939-115">A `TemplateBinding` özellikler iki yönlü bağlamaya varsayılan yapsa bile her zaman bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="b6939-115">A `TemplateBinding` is always a one-way binding, even if properties involved default to two-way binding.</span></span> <span data-ttu-id="b6939-116">İlgili iki özellik de bağımlılık özellikleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b6939-116">Both properties involved must be dependency properties.</span></span> <span data-ttu-id="b6939-117">Elde etmek için bir şablonlu üst öğeye iki yönlü bir bağlama kullanın şu bağlama ifadesi `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`.</span><span class="sxs-lookup"><span data-stu-id="b6939-117">In order to achieve two-way binding to a templated parent use the following binding statement instead `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`.</span></span> 
  
 <span data-ttu-id="b6939-118">[RelativeSource](relativesource-markupextension.md) bazen yerine veya ile birlikte kullanılan başka bir işaretleme uzantısı `TemplateBinding` şablon içinde göreli özellik bağlamasını gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="b6939-118">[RelativeSource](relativesource-markupextension.md) is another markup extension that is sometimes used in conjunction with or instead of `TemplateBinding` in order to perform relative property binding within a template.</span></span>  
  
 <span data-ttu-id="b6939-119">Kavram olarak denetim şablonları açıklayan burada kapsanmıyor; Daha fazla bilgi için [denetim stilleri ve şablonları](../controls/control-styles-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="b6939-119">Describing control templates as a concept is not covered here; for more information, see [Control Styles and Templates](../controls/control-styles-and-templates.md).</span></span>  
  
 <span data-ttu-id="b6939-120">Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="b6939-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="b6939-121">Sonra sağlanan dize belirteci `TemplateBinding` tanımlayıcı dizesi olarak atandığı <xref:System.Windows.TemplateBindingExtension.Property%2A> temel değer <xref:System.Windows.TemplateBindingExtension> uzantısı sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b6939-121">The string token provided after the `TemplateBinding` identifier string is assigned as the <xref:System.Windows.TemplateBindingExtension.Property%2A> value of the underlying <xref:System.Windows.TemplateBindingExtension> extension class.</span></span>  
  
 <span data-ttu-id="b6939-122">Nesne öğesi sözdizimi mümkündür, ancak gerçekçi uygulamaya sahip olmadığından gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="b6939-122">Object element syntax is possible, but it is not shown because it has no realistic application.</span></span> <span data-ttu-id="b6939-123">`TemplateBinding` kullanarak, ayarlayıcılar içinde değerleri değerlendirilmiş ifadeler doldurmak için kullanılır ve nesne öğesi sözdizimi `TemplateBinding` doldurmak için `<Setter.Property>` özellik öğesi sözdizimine gereksiz yere ayrıntılıdır.</span><span class="sxs-lookup"><span data-stu-id="b6939-123">`TemplateBinding` is used to fill values within setters, using evaluated expressions, and using object element syntax for `TemplateBinding` to fill `<Setter.Property>` property element syntax is unnecessarily verbose.</span></span>  
  
 <span data-ttu-id="b6939-124">`TemplateBinding` belirten ayrıntılı öznitelik kullanımında da ayrıca kullanılabilir <xref:System.Windows.TemplateBindingExtension.Property%2A> bir özellik olarak özellik değer eşleştirmesi:</span><span class="sxs-lookup"><span data-stu-id="b6939-124">`TemplateBinding` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.TemplateBindingExtension.Property%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 <span data-ttu-id="b6939-125">Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b6939-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="b6939-126">Çünkü `TemplateBinding` yalnızca gerekli olan bir ayarlanabilir özelliği, bu ayrıntılı kullanım tipik değildir.</span><span class="sxs-lookup"><span data-stu-id="b6939-126">Because `TemplateBinding` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="b6939-127">İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemci uygulamasında, bu işaretleme uzantısının işlenmesi tarafından tanımlanır <xref:System.Windows.TemplateBindingExtension> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b6939-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.TemplateBindingExtension> class.</span></span>  
  
 <span data-ttu-id="b6939-128">`TemplateBinding` bir işaretleme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="b6939-128">`TemplateBinding` is a markup extension.</span></span> <span data-ttu-id="b6939-129">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b6939-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="b6939-130">XAML kullanım içindeki tüm biçimlendirme uzantıları `{` ve `}` karakter olarak bir XAML işlemcisinin bir işaretleme uzantısı özniteliği işlenmesi gerektiğini, kuralına göre kendi öznitelik sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="b6939-130">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="b6939-131">Daha fazla bilgi için [biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="b6939-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6939-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6939-132">See also</span></span>
- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="b6939-133">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b6939-133">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="b6939-134">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="b6939-134">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="b6939-135">İşaretleme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="b6939-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="b6939-136">RelativeSource İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="b6939-136">RelativeSource MarkupExtension</span></span>](relativesource-markupextension.md)
- [<span data-ttu-id="b6939-137">İşaretleme Uzantısı Bağlama</span><span class="sxs-lookup"><span data-stu-id="b6939-137">Binding Markup Extension</span></span>](binding-markup-extension.md)
