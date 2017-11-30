---
title: "ThemeDictionary Biçimlendirme Uzantısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ThemeDictionaryExtension
- ThemeDictionary
helpviewer_keywords:
- ThemeDictionary markup extension [WPF]
- XAML [WPF], ThemeDictionary markup extension
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45f878ce89dcf76ae800ade10a0e67f019741f65
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="themedictionary-markup-extension"></a><span data-ttu-id="541a9-102">ThemeDictionary Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="541a9-102">ThemeDictionary Markup Extension</span></span>
<span data-ttu-id="541a9-103">Özel denetim yazarlar ya da üçüncü taraf denetimlerinin denetime stil kullanmak için özel tema kaynak sözlüklerindeki yüklemek için tümleştirme uygulamaları için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="541a9-103">Provides a way for custom control authors or applications that integrate third-party controls to load theme-specific resource dictionaries to use in styling the control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="541a9-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="541a9-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="541a9-105">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="541a9-105">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="541a9-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="541a9-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`assemblyUri`|<span data-ttu-id="541a9-107">[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] Tema bilgilerini içeren derleme.</span><span class="sxs-lookup"><span data-stu-id="541a9-107">The [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] of the assembly that contains theme information.</span></span> <span data-ttu-id="541a9-108">Genellikle, bir paketi büyük paketindeki bir derlemeye başvurur URI budur.</span><span class="sxs-lookup"><span data-stu-id="541a9-108">Typically, this is a pack URI that references an assembly in the larger package.</span></span> <span data-ttu-id="541a9-109">Bütünleştirilmiş kod kaynakları ve paketi URI'ler dağıtım sorunlarını basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="541a9-109">Assembly resources and pack URIs simplify deployment issues.</span></span> <span data-ttu-id="541a9-110">Daha fazla bilgi için bkz: [Pack URI WPF'de](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="541a9-110">For more information see [Pack URIs in WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="541a9-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="541a9-111">Remarks</span></span>  
 <span data-ttu-id="541a9-112">Bu uzantı yalnızca bir özel özellik değerini doldurmak için tasarlanmıştır: için bir değer <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="541a9-112">This extension is intended to fill only one specific property value: a value for <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="541a9-113">Bu uzantıyı kullanarak, yalnızca kullanmak için bazı stilleri içeren tek bir yalnızca kaynak derleme belirtebilirsiniz [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] temayı kullanıcının sisteme Luna teması etkin vb. olduğunda diğer stilleri uygulanır.</span><span class="sxs-lookup"><span data-stu-id="541a9-113">By using this extension, you can specify a single resources-only assembly that contains some styles to use only when the [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] theme is applied to the user's system, other styles when Luna theme is active, and so on.</span></span> <span data-ttu-id="541a9-114">Bu uzantıyı kullanarak bir özel denetim kaynak sözlüğü içeriğini otomatik olarak geçersiz kılınan ve gerektiğinde başka bir tema için belirli olacak şekilde yeniden.</span><span class="sxs-lookup"><span data-stu-id="541a9-114">By using this extension, the contents of a control-specific resource dictionary can be automatically invalidated and reloaded to be specific for another theme when required.</span></span>  
  
 <span data-ttu-id="541a9-115">`assemblyUri` Dize (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> özellik değeri) hangi sözlüğün belirli bir temaya uygulandığını tanımlayan bir adlandırma kuralı temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="541a9-115">The `assemblyUri` string (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property value) forms the basis of a naming convention that identifies which dictionary applies for a particular theme.</span></span> <span data-ttu-id="541a9-116"><xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> Mantığı `ThemeDictionary` oluşturarak kuralı tamamlar bir [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] önceden derlenmiş kaynak assembly içinde yer alan gibi belirli tema sözlük değişkenine işaret.</span><span class="sxs-lookup"><span data-stu-id="541a9-116">The <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> logic for `ThemeDictionary` completes the convention by generating a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] that points to a particular theme dictionary variant, as contained within a precompiled resource assembly.</span></span> <span data-ttu-id="541a9-117">Bu kuralı veya genel denetim stil ve sayfa ve uygulama düzeyi stil bir kavram olarak ile tema etkileşimlerini açıklayan burada tam olarak ele alınmamıştır.</span><span class="sxs-lookup"><span data-stu-id="541a9-117">Describing this convention, or theme interactions with general control styling and page/application level styling as a concept, is not covered fully here.</span></span> <span data-ttu-id="541a9-118">Kullanmak için temel senaryo `ThemeDictionary` belirtmektir <xref:System.Windows.ResourceDictionary.Source%2A> özelliği bir `ResourceDictionary` uygulama düzeyinde bildirilmedi.</span><span class="sxs-lookup"><span data-stu-id="541a9-118">The basic scenario for using `ThemeDictionary` is to specify the <xref:System.Windows.ResourceDictionary.Source%2A> property of a `ResourceDictionary` declared at the application level.</span></span> <span data-ttu-id="541a9-119">Sağladığınız ne zaman bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] derleme için bir `ThemeDictionary` uzantısı yerine doğrudan [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], uzantı mantığı sistem teması değiştiğinde uygulayan geçersiz kılma mantığını sağlar.</span><span class="sxs-lookup"><span data-stu-id="541a9-119">When you provide a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the assembly through a `ThemeDictionary` extension rather than as a direct [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], the extension logic will provide invalidation logic that applies whenever the system theme changes.</span></span>  
  
 <span data-ttu-id="541a9-120">Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="541a9-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="541a9-121">Sonra sağlanan dize belirteci `ThemeDictionary` kimlik dizesi olarak atandığı <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> temel değer <xref:System.Windows.ThemeDictionaryExtension> uzantısı sınıfı.</span><span class="sxs-lookup"><span data-stu-id="541a9-121">The string token provided after the `ThemeDictionary` identifier string is assigned as the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> value of the underlying <xref:System.Windows.ThemeDictionaryExtension> extension class.</span></span>  
  
 <span data-ttu-id="541a9-122">`ThemeDictionary`Ayrıca nesne öğesi sözdiziminde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="541a9-122">`ThemeDictionary` may also be used in object element syntax.</span></span> <span data-ttu-id="541a9-123">Bu durumda, değerini belirten <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> özelliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="541a9-123">In this case, specifying the value of the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property is required.</span></span>  
  
 <span data-ttu-id="541a9-124">`ThemeDictionary`belirten bir ayrıntılı öznitelik kullanımı da kullanılabilir <xref:System.Windows.Markup.StaticExtension.Member%2A> özelliği bir özellik olarak değer çifti =:</span><span class="sxs-lookup"><span data-stu-id="541a9-124">`ThemeDictionary` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.Markup.StaticExtension.Member%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 <span data-ttu-id="541a9-125">Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="541a9-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="541a9-126">Çünkü `ThemeDictionary` yalnızca gerekli olan bir ayarlanabilir özelliği, bu ayrıntılı kullanım tipik sahiptir.</span><span class="sxs-lookup"><span data-stu-id="541a9-126">Because `ThemeDictionary` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="541a9-127">İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci uygulamasında, bu biçimlendirme uzantısı işlenmesi tarafından tanımlanan <xref:System.Windows.ThemeDictionaryExtension> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="541a9-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.ThemeDictionaryExtension> class.</span></span>  
  
 <span data-ttu-id="541a9-128">`ThemeDictionary`bir biçimlendirme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="541a9-128">`ThemeDictionary` is a markup extension.</span></span> <span data-ttu-id="541a9-129">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="541a9-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="541a9-130">İçindeki tüm biçimlendirme uzantıları [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanmak {ve} kurala göre kendi öznitelik sözdiziminde karakterler bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci tanıdığı biçimlendirme uzantısı öznitelik işlemelidir.</span><span class="sxs-lookup"><span data-stu-id="541a9-130">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="541a9-131">Daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="541a9-131">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="541a9-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="541a9-132">See Also</span></span>  
 [<span data-ttu-id="541a9-133">Stil ve şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="541a9-133">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="541a9-134">XAML genel bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="541a9-134">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="541a9-135">Biçimlendirme uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="541a9-135">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="541a9-136">WPF Uygulama kaynağı, içerik ve veri dosyaları</span><span class="sxs-lookup"><span data-stu-id="541a9-136">WPF Application Resource, Content, and Data Files</span></span>](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
