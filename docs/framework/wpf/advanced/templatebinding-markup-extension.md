---
title: "TemplateBinding Biçimlendirme Uzantısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TemplateBinding
- TemplateBindingExtension
helpviewer_keywords:
- XAML [WPF], TemplateBinding markup extension
- TemplateBinding markup extensions [WPF]
ms.assetid: 1d25bbfc-dbc2-499d-9f12-419d23d4ac6a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ab8645de78a79f4bd47fa436699af002db99b9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="templatebinding-markup-extension"></a><span data-ttu-id="c28ce-102">TemplateBinding Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="c28ce-102">TemplateBinding Markup Extension</span></span>
<span data-ttu-id="c28ce-103">Denetim şablonunda bir özelliğin değerini, şablonlu denetim üzerinde açıkça gösterilen başka bir özelliğin değerine bağlar.</span><span class="sxs-lookup"><span data-stu-id="c28ce-103">Links the value of a property in a control template to be the value of another property on the templated control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="c28ce-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="c28ce-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a><span data-ttu-id="c28ce-105">XAML Öznitelik Kullanımı (şablon veya stilde Ayarlayıcı özelliği için)</span><span class="sxs-lookup"><span data-stu-id="c28ce-105">XAML Attribute Usage (for Setter property in template or style)</span></span>  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="c28ce-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="c28ce-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`propertyName`|<span data-ttu-id="c28ce-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>ayarlayıcı sözdiziminde ayarlanan özelliği.</span><span class="sxs-lookup"><span data-stu-id="c28ce-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> of the property being set in the setter syntax.</span></span>|  
|`sourceProperty`|<span data-ttu-id="c28ce-108">Belirtilen şablonu, oluşturulan türünde bulunan başka bir bağımlılık özelliği tarafından kendi <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c28ce-108">Another dependency property that exists on the type being templated, specified by its <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span></span><br /><br /> <span data-ttu-id="c28ce-109">- veya -</span><span class="sxs-lookup"><span data-stu-id="c28ce-109">- or -</span></span><br /><br /> <span data-ttu-id="c28ce-110">Şablonu oluşturulan hedef türünden farklı bir tür tarafından tanımlanan "aşağı noktalanmış" özellik adı.</span><span class="sxs-lookup"><span data-stu-id="c28ce-110">A "dotted-down" property name that is defined by a different type than the target type being templated.</span></span> <span data-ttu-id="c28ce-111">Bu gerçekten olan bir <xref:System.Windows.PropertyPath>.</span><span class="sxs-lookup"><span data-stu-id="c28ce-111">This is actually a <xref:System.Windows.PropertyPath>.</span></span> <span data-ttu-id="c28ce-112">Bkz: [PropertyPath XAML sözdizimi](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="c28ce-112">See [PropertyPath XAML Syntax](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c28ce-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c28ce-113">Remarks</span></span>  
 <span data-ttu-id="c28ce-114">A `TemplateBinding` en iyi duruma getirilmiş bir biçimidir bir [bağlama](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) alınmak üzere benzer şablon senaryoları için bir `Binding` ile oluşturulan `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span><span class="sxs-lookup"><span data-stu-id="c28ce-114">A `TemplateBinding` is an optimized form of a [Binding](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) for template scenarios, analogous to a `Binding` constructed with `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="c28ce-115">A `TemplateBinding` iki yönlü bağlama için varsayılan özellikler dahil her zaman bir tek yönlü bağlama, olsa dahi.</span><span class="sxs-lookup"><span data-stu-id="c28ce-115">A `TemplateBinding` is always a one-way binding, even if properties involved default to two-way binding.</span></span> <span data-ttu-id="c28ce-116">İlgili iki özellik de bağımlılık özellikleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c28ce-116">Both properties involved must be dependency properties.</span></span>  
  
 <span data-ttu-id="c28ce-117">[RelativeSource](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md) bazen yerine veya ile birlikte kullanılan başka bir işaretleme uzantısı `TemplateBinding` şablon içinde göreli özellik bağlamasını gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="c28ce-117">[RelativeSource](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md) is another markup extension that is sometimes used in conjunction with or instead of `TemplateBinding` in order to perform relative property binding within a template.</span></span>  
  
 <span data-ttu-id="c28ce-118">Kavram olarak denetim şablonları açıklayan burada kapsanmayan; Daha fazla bilgi için bkz: [denetim stilleri ve şablonları](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="c28ce-118">Describing control templates as a concept is not covered here; for more information, see [Control Styles and Templates](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).</span></span>  
  
 <span data-ttu-id="c28ce-119">Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="c28ce-119">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="c28ce-120">Sonra sağlanan dize belirteci `TemplateBinding` kimlik dizesi olarak atandığı <xref:System.Windows.TemplateBindingExtension.Property%2A> temel değer <xref:System.Windows.TemplateBindingExtension> uzantısı sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c28ce-120">The string token provided after the `TemplateBinding` identifier string is assigned as the <xref:System.Windows.TemplateBindingExtension.Property%2A> value of the underlying <xref:System.Windows.TemplateBindingExtension> extension class.</span></span>  
  
 <span data-ttu-id="c28ce-121">Nesne öğesi sözdizimi mümkündür, ancak gerçekçi uygulamaya sahip olmadığından gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="c28ce-121">Object element syntax is possible, but it is not shown because it has no realistic application.</span></span> <span data-ttu-id="c28ce-122">`TemplateBinding`kullanarak, ayarlayıcılar içinde değerleri değerlendirilmiş ifadeler doldurmak için kullanılır ve nesne öğesi sözdizimini kullanarak `TemplateBinding` doldurmak için `<Setter.Property>` özellik öğesi sözdizimini gereksiz yere ayrıntılıdır.</span><span class="sxs-lookup"><span data-stu-id="c28ce-122">`TemplateBinding` is used to fill values within setters, using evaluated expressions, and using object element syntax for `TemplateBinding` to fill `<Setter.Property>` property element syntax is unnecessarily verbose.</span></span>  
  
 <span data-ttu-id="c28ce-123">`TemplateBinding`belirten bir ayrıntılı öznitelik kullanımı da kullanılabilir <xref:System.Windows.TemplateBindingExtension.Property%2A> özelliği bir özellik olarak değer çifti =:</span><span class="sxs-lookup"><span data-stu-id="c28ce-123">`TemplateBinding` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.TemplateBindingExtension.Property%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 <span data-ttu-id="c28ce-124">Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c28ce-124">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="c28ce-125">Çünkü `TemplateBinding` yalnızca gerekli olan bir ayarlanabilir özelliği, bu ayrıntılı kullanım tipik sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c28ce-125">Because `TemplateBinding` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="c28ce-126">İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemci uygulamasında, bu biçimlendirme uzantısı işlenmesi tarafından tanımlanan <xref:System.Windows.TemplateBindingExtension> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c28ce-126">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.TemplateBindingExtension> class.</span></span>  
  
 <span data-ttu-id="c28ce-127">`TemplateBinding`bir biçimlendirme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="c28ce-127">`TemplateBinding` is a markup extension.</span></span> <span data-ttu-id="c28ce-128">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c28ce-128">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="c28ce-129">XAML Kullanımdaki tüm biçimlendirme uzantıları `{` ve `}` olarak XAML işlemci tanıdığı biçimlendirme uzantısı öznitelik işlemelidir kuralı kendi öznitelik sözdiziminde karakterler.</span><span class="sxs-lookup"><span data-stu-id="c28ce-129">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="c28ce-130">Daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="c28ce-130">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c28ce-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c28ce-131">See Also</span></span>  
 <xref:System.Windows.Style>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="c28ce-132">Stil ve şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="c28ce-132">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="c28ce-133">XAML genel bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="c28ce-133">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="c28ce-134">Biçimlendirme uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="c28ce-134">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="c28ce-135">RelativeSource MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="c28ce-135">RelativeSource MarkupExtension</span></span>](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md)  
 [<span data-ttu-id="c28ce-136">Bağlama biçimlendirme uzantısı</span><span class="sxs-lookup"><span data-stu-id="c28ce-136">Binding Markup Extension</span></span>](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)
