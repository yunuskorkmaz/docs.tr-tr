---
title: ThemeDictionary Biçimlendirme Uzantısı
ms.date: 03/30/2017
f1_keywords:
- ThemeDictionaryExtension
- ThemeDictionary
helpviewer_keywords:
- ThemeDictionary markup extension [WPF]
- XAML [WPF], ThemeDictionary markup extension
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
ms.openlocfilehash: 0bc4b2a11927bd2551dc322c5a856ade9a85c8b7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364807"
---
# <a name="themedictionary-markup-extension"></a><span data-ttu-id="4cf4b-102">ThemeDictionary Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="4cf4b-102">ThemeDictionary Markup Extension</span></span>
<span data-ttu-id="4cf4b-103">Özel denetim yazarlar veya üçüncü taraf denetimleri temaya özgü kaynak sözlükleri bir denetime stil içinde kullanmak için yüklenecek tümleşen uygulamaları için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-103">Provides a way for custom control authors or applications that integrate third-party controls to load theme-specific resource dictionaries to use in styling the control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="4cf4b-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="4cf4b-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="4cf4b-105">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="4cf4b-105">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="4cf4b-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="4cf4b-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`assemblyUri`|<span data-ttu-id="4cf4b-107">[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] Tema bilgileri içeren derleme.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-107">The [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] of the assembly that contains theme information.</span></span> <span data-ttu-id="4cf4b-108">Genellikle, bir paketi büyük paketinde bir derlemeye başvuran bir URI budur.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-108">Typically, this is a pack URI that references an assembly in the larger package.</span></span> <span data-ttu-id="4cf4b-109">Derleme kaynakları ve paketi URI'ler dağıtım sorunlarını basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-109">Assembly resources and pack URIs simplify deployment issues.</span></span> <span data-ttu-id="4cf4b-110">Daha fazla bilgi için [paketi URI ' WPF'de](../app-development/pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="4cf4b-110">For more information see [Pack URIs in WPF](../app-development/pack-uris-in-wpf.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4cf4b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4cf4b-111">Remarks</span></span>  
 <span data-ttu-id="4cf4b-112">Bu uzantı yalnızca bir özel özellik değerini doldurmak için tasarlanmıştır: bir değer <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-112">This extension is intended to fill only one specific property value: a value for <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="4cf4b-113">Bu uzantıyı kullanarak yalnızca kullanmak için bazı stilleri içeren tek bir yalnızca kaynak derleme belirtebilirsiniz [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] temayı kullanıcının sistem, Luna teması etkin vb. olduğunda diğer stil uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-113">By using this extension, you can specify a single resources-only assembly that contains some styles to use only when the [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] theme is applied to the user's system, other styles when Luna theme is active, and so on.</span></span> <span data-ttu-id="4cf4b-114">Bu uzantıyı kullanarak bir özel denetim kaynak sözlüğü içeriğini otomatik olarak geçersiz kılınan ve gerektiğinde başka bir tema için belirli olacak şekilde yeniden.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-114">By using this extension, the contents of a control-specific resource dictionary can be automatically invalidated and reloaded to be specific for another theme when required.</span></span>  
  
 <span data-ttu-id="4cf4b-115">`assemblyUri` Dize (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> özellik değerinin) belirli bir temaya hangi sözlüğün uygulandığını tanımlayan bir adlandırma kuralı temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-115">The `assemblyUri` string (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property value) forms the basis of a naming convention that identifies which dictionary applies for a particular theme.</span></span> <span data-ttu-id="4cf4b-116"><xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> Mantığı `ThemeDictionary` oluşturarak kuralı tamamlar bir [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] işaret eden bir tema belirli sözlük değişkenine önceden derlenmiş kaynak derleme içinde yer alan olarak.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-116">The <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> logic for `ThemeDictionary` completes the convention by generating a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] that points to a particular theme dictionary variant, as contained within a precompiled resource assembly.</span></span> <span data-ttu-id="4cf4b-117">Bu kuralı veya tema etkileşim genel denetimi stil ve sayfa/uygulama düzeyi stili oluşturma, kavram olarak açıklayan tam olarak burada kapsamaz.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-117">Describing this convention, or theme interactions with general control styling and page/application level styling as a concept, is not covered fully here.</span></span> <span data-ttu-id="4cf4b-118">Kullanmak için temel senaryo `ThemeDictionary` belirtmektir <xref:System.Windows.ResourceDictionary.Source%2A> özelliği bir `ResourceDictionary` uygulama düzeyinde bildirilir.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-118">The basic scenario for using `ThemeDictionary` is to specify the <xref:System.Windows.ResourceDictionary.Source%2A> property of a `ResourceDictionary` declared at the application level.</span></span> <span data-ttu-id="4cf4b-119">Sağladığınız ne zaman bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] derleme için bir `ThemeDictionary` uzantısı yerine doğrudan [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], sistem tema değiştiğinde uygulanan geçersiz kılma mantığını uzantı mantığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-119">When you provide a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the assembly through a `ThemeDictionary` extension rather than as a direct [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], the extension logic will provide invalidation logic that applies whenever the system theme changes.</span></span>  
  
 <span data-ttu-id="4cf4b-120">Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="4cf4b-121">Sonra sağlanan dize belirteci `ThemeDictionary` tanımlayıcı dizesi olarak atandığı <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> temel değer <xref:System.Windows.ThemeDictionaryExtension> uzantısı sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-121">The string token provided after the `ThemeDictionary` identifier string is assigned as the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> value of the underlying <xref:System.Windows.ThemeDictionaryExtension> extension class.</span></span>  
  
 <span data-ttu-id="4cf4b-122">`ThemeDictionary` Ayrıca nesne öğesi sözdiziminde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-122">`ThemeDictionary` may also be used in object element syntax.</span></span> <span data-ttu-id="4cf4b-123">Bu durumda, değerini belirterek <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> özelliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-123">In this case, specifying the value of the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property is required.</span></span>  
  
 <span data-ttu-id="4cf4b-124">`ThemeDictionary` belirten ayrıntılı öznitelik kullanımında da ayrıca kullanılabilir <xref:System.Windows.Markup.StaticExtension.Member%2A> bir özellik olarak özellik değer eşleştirmesi:</span><span class="sxs-lookup"><span data-stu-id="4cf4b-124">`ThemeDictionary` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.Markup.StaticExtension.Member%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 <span data-ttu-id="4cf4b-125">Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="4cf4b-126">Çünkü `ThemeDictionary` yalnızca gerekli olan bir ayarlanabilir özelliği, bu ayrıntılı kullanım tipik değildir.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-126">Because `ThemeDictionary` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="4cf4b-127">İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci uygulamasında, bu işaretleme uzantısının işlenmesi tarafından tanımlanır <xref:System.Windows.ThemeDictionaryExtension> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.ThemeDictionaryExtension> class.</span></span>  
  
 <span data-ttu-id="4cf4b-128">`ThemeDictionary` bir işaretleme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-128">`ThemeDictionary` is a markup extension.</span></span> <span data-ttu-id="4cf4b-129">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="4cf4b-130">İçindeki tüm biçimlendirme uzantıları [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanmak {ve} kuralına göre kendi öznitelik sözdizimi içinde karakterler bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisinin bir işaretleme uzantısı özniteliği işlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-130">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="4cf4b-131">Daha fazla bilgi için [biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="4cf4b-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf4b-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cf4b-132">See also</span></span>
- [<span data-ttu-id="4cf4b-133">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4cf4b-133">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="4cf4b-134">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="4cf4b-134">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="4cf4b-135">İşaretleme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="4cf4b-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="4cf4b-136">WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları</span><span class="sxs-lookup"><span data-stu-id="4cf4b-136">WPF Application Resource, Content, and Data Files</span></span>](../app-development/wpf-application-resource-content-and-data-files.md)
