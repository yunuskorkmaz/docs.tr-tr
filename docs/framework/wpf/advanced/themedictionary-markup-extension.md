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
ms.openlocfilehash: 7fa729d600f25b73028bae0dd6d9248b5839dd4c
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133869"
---
# <a name="themedictionary-markup-extension"></a><span data-ttu-id="62f02-102">ThemeDictionary Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="62f02-102">ThemeDictionary Markup Extension</span></span>
<span data-ttu-id="62f02-103">Özel denetim yazarları veya üçüncü taraf denetimleri, denetimin stillendirmede kullanılacak temaya özgü kaynak sözlükleri yüklemek üzere tümleştiren uygulamalar için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="62f02-103">Provides a way for custom control authors or applications that integrate third-party controls to load theme-specific resource dictionaries to use in styling the control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="62f02-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="62f02-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="62f02-105">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="62f02-105">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="62f02-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="62f02-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`assemblyUri`|<span data-ttu-id="62f02-107">[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] Tema bilgilerini içeren derlemenin.</span><span class="sxs-lookup"><span data-stu-id="62f02-107">The [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] of the assembly that contains theme information.</span></span> <span data-ttu-id="62f02-108">Genellikle, bu, daha büyük paketteki bir derlemeye başvuran bir paket URI 'sidir.</span><span class="sxs-lookup"><span data-stu-id="62f02-108">Typically, this is a pack URI that references an assembly in the larger package.</span></span> <span data-ttu-id="62f02-109">Derleme kaynakları ve paket URI 'Leri dağıtım sorunlarını basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="62f02-109">Assembly resources and pack URIs simplify deployment issues.</span></span> <span data-ttu-id="62f02-110">Daha fazla bilgi için bkz. [WPF 'de paket URI 'leri](../app-development/pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="62f02-110">For more information see [Pack URIs in WPF](../app-development/pack-uris-in-wpf.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62f02-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62f02-111">Remarks</span></span>  
 <span data-ttu-id="62f02-112">Bu uzantı yalnızca bir özel özellik değerini doldurmaya yöneliktir: için <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>bir değer.</span><span class="sxs-lookup"><span data-stu-id="62f02-112">This extension is intended to fill only one specific property value: a value for <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="62f02-113">Bu uzantıyı kullanarak yalnızca Windows Aero teması Kullanıcı sistemine uygulandığında kullanılacak bazı stilleri, yalnızca Luna teması etkin olduğunda diğer stilleri ve bu şekilde devam eden tek bir kaynak derleme belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62f02-113">By using this extension, you can specify a single resources-only assembly that contains some styles to use only when the Windows Aero theme is applied to the user's system, other styles only when the Luna theme is active, and so on.</span></span> <span data-ttu-id="62f02-114">Bu uzantıyı kullanarak, denetime özgü bir kaynak sözlüğünün içeriği gerektiğinde başka bir temaya özgü olacak şekilde otomatik olarak geçersiz kılınabilir ve yeniden yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="62f02-114">By using this extension, the contents of a control-specific resource dictionary can be automatically invalidated and reloaded to be specific for another theme when required.</span></span>  
  
 <span data-ttu-id="62f02-115">`assemblyUri` Dize(<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> Özellik değeri), belirli bir tema için hangi sözlüğün uygulanacağını belirleyen bir adlandırma kuralının temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="62f02-115">The `assemblyUri` string (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property value) forms the basis of a naming convention that identifies which dictionary applies for a particular theme.</span></span> <span data-ttu-id="62f02-116">İçin <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] mantığı, önceden derlenmiş bir kaynak derlemesinde yer alan belirli bir tema sözlüğü değişkenine işaret eden bir oluşturarak kuralı tamamlar. `ThemeDictionary`</span><span class="sxs-lookup"><span data-stu-id="62f02-116">The <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> logic for `ThemeDictionary` completes the convention by generating a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] that points to a particular theme dictionary variant, as contained within a precompiled resource assembly.</span></span> <span data-ttu-id="62f02-117">Bu kuralı veya genel denetim stili ve sayfa/uygulama düzeyi stillendirme ile bir kavram olarak tema etkileşimleri, burada tam olarak kapsanmaz.</span><span class="sxs-lookup"><span data-stu-id="62f02-117">Describing this convention, or theme interactions with general control styling and page/application level styling as a concept, is not covered fully here.</span></span> <span data-ttu-id="62f02-118">Kullanmanın `ThemeDictionary` temel senaryosu, uygulama düzeyinde `ResourceDictionary` belirtilen öğesinin <xref:System.Windows.ResourceDictionary.Source%2A> özelliğini belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="62f02-118">The basic scenario for using `ThemeDictionary` is to specify the <xref:System.Windows.ResourceDictionary.Source%2A> property of a `ResourceDictionary` declared at the application level.</span></span> <span data-ttu-id="62f02-119">Doğrudan `ThemeDictionary` [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] biruzantıaracılığıyladerlemeiçinbir,derlememantığı,sistemtemasıherdeğiştiğindegeçerliolangeçersizkılmamantığısağlar.[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62f02-119">When you provide a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the assembly through a `ThemeDictionary` extension rather than as a direct [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], the extension logic will provide invalidation logic that applies whenever the system theme changes.</span></span>  
  
 <span data-ttu-id="62f02-120">Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="62f02-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="62f02-121">`ThemeDictionary` Tanımlayıcı dizeden sonra belirtilen dize belirteci, temel <xref:System.Windows.ThemeDictionaryExtension> uzantı sınıfının <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> değeri olarak atanır.</span><span class="sxs-lookup"><span data-stu-id="62f02-121">The string token provided after the `ThemeDictionary` identifier string is assigned as the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> value of the underlying <xref:System.Windows.ThemeDictionaryExtension> extension class.</span></span>  
  
 <span data-ttu-id="62f02-122">`ThemeDictionary`, nesne öğesi söz diziminde de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="62f02-122">`ThemeDictionary` may also be used in object element syntax.</span></span> <span data-ttu-id="62f02-123">Bu durumda, <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> özelliğinin değerini belirtmek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="62f02-123">In this case, specifying the value of the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property is required.</span></span>  
  
 <span data-ttu-id="62f02-124">`ThemeDictionary`, <xref:System.Windows.Markup.StaticExtension.Member%2A> özelliği özellik = değer çifti olarak belirten ayrıntılı bir öznitelik kullanımında de kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="62f02-124">`ThemeDictionary` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.Markup.StaticExtension.Member%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 <span data-ttu-id="62f02-125">Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="62f02-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="62f02-126">, `ThemeDictionary` Gereken tek bir ayarlanabilir özelliğe sahip olduğundan, bu ayrıntılı kullanım tipik değildir.</span><span class="sxs-lookup"><span data-stu-id="62f02-126">Because `ThemeDictionary` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="62f02-127">İşlemci uygulamasında, bu biçimlendirme <xref:System.Windows.ThemeDictionaryExtension> uzantısının işlenmesi sınıfı tarafından tanımlanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62f02-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.ThemeDictionaryExtension> class.</span></span>  
  
 <span data-ttu-id="62f02-128">`ThemeDictionary`bir biçimlendirme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="62f02-128">`ThemeDictionary` is a markup extension.</span></span> <span data-ttu-id="62f02-129">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="62f02-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="62f02-130">İçindeki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tüm biçimlendirme uzantıları öznitelik sözdiziminde {ve} karakteri kullanır. Bu, bir işlemcinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tanıdığı bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="62f02-130">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="62f02-131">Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="62f02-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f02-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62f02-132">See also</span></span>

- [<span data-ttu-id="62f02-133">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="62f02-133">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="62f02-134">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="62f02-134">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="62f02-135">İşaretleme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="62f02-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="62f02-136">WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları</span><span class="sxs-lookup"><span data-stu-id="62f02-136">WPF Application Resource, Content, and Data Files</span></span>](../app-development/wpf-application-resource-content-and-data-files.md)
