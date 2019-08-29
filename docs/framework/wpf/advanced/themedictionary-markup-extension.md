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
# <a name="themedictionary-markup-extension"></a>ThemeDictionary Biçimlendirme Uzantısı
Özel denetim yazarları veya üçüncü taraf denetimleri, denetimin stillendirmede kullanılacak temaya özgü kaynak sözlükleri yüklemek üzere tümleştiren uygulamalar için bir yol sağlar.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`assemblyUri`|[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] Tema bilgilerini içeren derlemenin. Genellikle, bu, daha büyük paketteki bir derlemeye başvuran bir paket URI 'sidir. Derleme kaynakları ve paket URI 'Leri dağıtım sorunlarını basitleştirir. Daha fazla bilgi için bkz. [WPF 'de paket URI 'leri](../app-development/pack-uris-in-wpf.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu uzantı yalnızca bir özel özellik değerini doldurmaya yöneliktir: için <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>bir değer.  
  
 Bu uzantıyı kullanarak yalnızca Windows Aero teması Kullanıcı sistemine uygulandığında kullanılacak bazı stilleri, yalnızca Luna teması etkin olduğunda diğer stilleri ve bu şekilde devam eden tek bir kaynak derleme belirtebilirsiniz. Bu uzantıyı kullanarak, denetime özgü bir kaynak sözlüğünün içeriği gerektiğinde başka bir temaya özgü olacak şekilde otomatik olarak geçersiz kılınabilir ve yeniden yüklenebilir.  
  
 `assemblyUri` Dize(<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> Özellik değeri), belirli bir tema için hangi sözlüğün uygulanacağını belirleyen bir adlandırma kuralının temelini oluşturur. İçin <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] mantığı, önceden derlenmiş bir kaynak derlemesinde yer alan belirli bir tema sözlüğü değişkenine işaret eden bir oluşturarak kuralı tamamlar. `ThemeDictionary` Bu kuralı veya genel denetim stili ve sayfa/uygulama düzeyi stillendirme ile bir kavram olarak tema etkileşimleri, burada tam olarak kapsanmaz. Kullanmanın `ThemeDictionary` temel senaryosu, uygulama düzeyinde `ResourceDictionary` belirtilen öğesinin <xref:System.Windows.ResourceDictionary.Source%2A> özelliğini belirtmektir. Doğrudan `ThemeDictionary` [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] biruzantıaracılığıyladerlemeiçinbir,derlememantığı,sistemtemasıherdeğiştiğindegeçerliolangeçersizkılmamantığısağlar.[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. `ThemeDictionary` Tanımlayıcı dizeden sonra belirtilen dize belirteci, temel <xref:System.Windows.ThemeDictionaryExtension> uzantı sınıfının <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> değeri olarak atanır.  
  
 `ThemeDictionary`, nesne öğesi söz diziminde de kullanılabilir. Bu durumda, <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> özelliğinin değerini belirtmek gereklidir.  
  
 `ThemeDictionary`, <xref:System.Windows.Markup.StaticExtension.Member%2A> özelliği özellik = değer çifti olarak belirten ayrıntılı bir öznitelik kullanımında de kullanılabilir:  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır. , `ThemeDictionary` Gereken tek bir ayarlanabilir özelliğe sahip olduğundan, bu ayrıntılı kullanım tipik değildir.  
  
 İşlemci uygulamasında, bu biçimlendirme <xref:System.Windows.ThemeDictionaryExtension> uzantısının işlenmesi sınıfı tarafından tanımlanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `ThemeDictionary`bir biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. İçindeki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tüm biçimlendirme uzantıları öznitelik sözdiziminde {ve} karakteri kullanır. Bu, bir işlemcinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tanıdığı bir kuraldır. Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Stil ve Şablon Oluşturma](../controls/styling-and-templating.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları](../app-development/wpf-application-resource-content-and-data-files.md)
