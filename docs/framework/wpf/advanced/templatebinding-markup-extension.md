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
ms.openlocfilehash: 399e4ac223d2fcb728ece2c92d25a087990992f2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458663"
---
# <a name="templatebinding-markup-extension"></a><span data-ttu-id="b9f51-102">TemplateBinding Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="b9f51-102">TemplateBinding Markup Extension</span></span>
<span data-ttu-id="b9f51-103">Denetim şablonunda bir özelliğin değerini, şablonlu denetim üzerinde açıkça gösterilen başka bir özelliğin değerine bağlar.</span><span class="sxs-lookup"><span data-stu-id="b9f51-103">Links the value of a property in a control template to be the value of another property on the templated control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="b9f51-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="b9f51-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a><span data-ttu-id="b9f51-105">XAML Öznitelik Kullanımı (şablon veya stilde Ayarlayıcı özelliği için)</span><span class="sxs-lookup"><span data-stu-id="b9f51-105">XAML Attribute Usage (for Setter property in template or style)</span></span>  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="b9f51-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="b9f51-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`propertyName`|<span data-ttu-id="b9f51-107">ayarlayıcı sözdiziminde ayarlanan özelliğin <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b9f51-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> of the property being set in the setter syntax.</span></span>|  
|`sourceProperty`|<span data-ttu-id="b9f51-108">Şablonlu tür üzerinde bulunan ve <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>tarafından belirtilen başka bir bağımlılık özelliği.</span><span class="sxs-lookup"><span data-stu-id="b9f51-108">Another dependency property that exists on the type being templated, specified by its <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span></span><br /><br /> <span data-ttu-id="b9f51-109">veya</span><span class="sxs-lookup"><span data-stu-id="b9f51-109">- or -</span></span><br /><br /> <span data-ttu-id="b9f51-110">Şablonu oluşturulan hedef türünden farklı bir tür tarafından tanımlanan "aşağı noktalanmış" özellik adı.</span><span class="sxs-lookup"><span data-stu-id="b9f51-110">A "dotted-down" property name that is defined by a different type than the target type being templated.</span></span> <span data-ttu-id="b9f51-111">Bu aslında bir <xref:System.Windows.PropertyPath>.</span><span class="sxs-lookup"><span data-stu-id="b9f51-111">This is actually a <xref:System.Windows.PropertyPath>.</span></span> <span data-ttu-id="b9f51-112">Bkz. [PROPERTYPATH XAML sözdizimi](propertypath-xaml-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="b9f51-112">See [PropertyPath XAML Syntax](propertypath-xaml-syntax.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9f51-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9f51-113">Remarks</span></span>  
 <span data-ttu-id="b9f51-114">`TemplateBinding`, `{Binding RelativeSource={RelativeSource TemplatedParent}}`ile oluşturulmuş bir `Binding` benzer şablon senaryoları için en iyileştirilmiş bir [bağlama](binding-markup-extension.md) biçimidir.</span><span class="sxs-lookup"><span data-stu-id="b9f51-114">A `TemplateBinding` is an optimized form of a [Binding](binding-markup-extension.md) for template scenarios, analogous to a `Binding` constructed with `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="b9f51-115">Bir `TemplateBinding` her zaman tek yönlü bir bağlamadır ve özellikler varsayılan olarak iki yönlü bağlamaya dahil olur.</span><span class="sxs-lookup"><span data-stu-id="b9f51-115">A `TemplateBinding` is always a one-way binding, even if properties involved default to two-way binding.</span></span> <span data-ttu-id="b9f51-116">İlgili iki özellik de bağımlılık özellikleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b9f51-116">Both properties involved must be dependency properties.</span></span> <span data-ttu-id="b9f51-117">Şablonlu bir üst öğeye iki yönlü bağlama ulaşmak için `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`yerine aşağıdaki bağlama ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b9f51-117">In order to achieve two-way binding to a templated parent use the following binding statement instead `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`.</span></span> 
  
 <span data-ttu-id="b9f51-118">[RelativeSource](relativesource-markupextension.md) , bir şablon içinde göreli Özellik bağlamayı gerçekleştirmek için bazen `TemplateBinding` veya yerine ile birlikte kullanılan başka bir işaretleme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="b9f51-118">[RelativeSource](relativesource-markupextension.md) is another markup extension that is sometimes used in conjunction with or instead of `TemplateBinding` in order to perform relative property binding within a template.</span></span>  
  
 <span data-ttu-id="b9f51-119">Bir kavram olarak denetim şablonlarının açıklaması burada ele alınmıyor; daha fazla bilgi için bkz. [denetim stilleri ve şablonları](../controls/control-styles-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="b9f51-119">Describing control templates as a concept is not covered here; for more information, see [Control Styles and Templates](../controls/control-styles-and-templates.md).</span></span>  
  
 <span data-ttu-id="b9f51-120">Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="b9f51-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="b9f51-121">`TemplateBinding` tanımlayıcı dizeden sonra belirtilen dize belirteci, temel <xref:System.Windows.TemplateBindingExtension> uzantı sınıfının <xref:System.Windows.TemplateBindingExtension.Property%2A> değeri olarak atanır.</span><span class="sxs-lookup"><span data-stu-id="b9f51-121">The string token provided after the `TemplateBinding` identifier string is assigned as the <xref:System.Windows.TemplateBindingExtension.Property%2A> value of the underlying <xref:System.Windows.TemplateBindingExtension> extension class.</span></span>  
  
 <span data-ttu-id="b9f51-122">Nesne öğesi sözdizimi mümkündür, ancak gerçekçi uygulamaya sahip olmadığından gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="b9f51-122">Object element syntax is possible, but it is not shown because it has no realistic application.</span></span> <span data-ttu-id="b9f51-123">`TemplateBinding`, değerlendirilmiş ifadeler kullanılarak ayarlayıcıdaki değerleri ve `TemplateBinding` için nesne öğesi söz dizimini `<Setter.Property>` Özellik öğesi söz dizimini kullanarak doldurmanız için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b9f51-123">`TemplateBinding` is used to fill values within setters, using evaluated expressions, and using object element syntax for `TemplateBinding` to fill `<Setter.Property>` property element syntax is unnecessarily verbose.</span></span>  
  
 <span data-ttu-id="b9f51-124">`TemplateBinding`, özellik = değer çifti olarak <xref:System.Windows.TemplateBindingExtension.Property%2A> özelliğini belirten ayrıntılı bir öznitelik kullanımında de kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="b9f51-124">`TemplateBinding` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.TemplateBindingExtension.Property%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 <span data-ttu-id="b9f51-125">Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b9f51-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="b9f51-126">`TemplateBinding`, gereken tek bir ayarlanabilir özelliğe sahip olduğundan, bu ayrıntılı kullanım tipik değildir.</span><span class="sxs-lookup"><span data-stu-id="b9f51-126">Because `TemplateBinding` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="b9f51-127">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemci uygulamasında, bu biçimlendirme uzantısının işlenmesi <xref:System.Windows.TemplateBindingExtension> sınıfı tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b9f51-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.TemplateBindingExtension> class.</span></span>  
  
 <span data-ttu-id="b9f51-128">`TemplateBinding`, biçimlendirme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="b9f51-128">`TemplateBinding` is a markup extension.</span></span> <span data-ttu-id="b9f51-129">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b9f51-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="b9f51-130">XAML 'deki tüm biçimlendirme uzantıları, `{` ve `}` karakterlerini öznitelik sözdiziminde kullanır. Bu, XAML işlemcisinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini tanıdığı bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="b9f51-130">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="b9f51-131">Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="b9f51-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9f51-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9f51-132">See also</span></span>

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="b9f51-133">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b9f51-133">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="b9f51-134">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="b9f51-134">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="b9f51-135">İşaretleme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="b9f51-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="b9f51-136">RelativeSource İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="b9f51-136">RelativeSource MarkupExtension</span></span>](relativesource-markupextension.md)
- [<span data-ttu-id="b9f51-137">İşaretleme Uzantısı Bağlama</span><span class="sxs-lookup"><span data-stu-id="b9f51-137">Binding Markup Extension</span></span>](binding-markup-extension.md)
