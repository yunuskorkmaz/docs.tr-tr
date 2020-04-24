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
ms.openlocfilehash: f6ba0fe45aa11063c79d673b26794072968f4200
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646186"
---
# <a name="themedictionary-markup-extension"></a>ThemeDictionary Biçimlendirme Uzantısı
Denetimi şekillendirmede kullanmak üzere temaya özgü kaynak sözlüklerini yüklemek için üçüncü taraf denetimlerini tümleştiren özel denetim yazarları veya uygulamaları için bir yol sağlar.  
  
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
|`assemblyUri`|Tema bilgilerini içeren derlemenin tek düze kaynak tanımlayıcısı (URI). Genellikle, bu büyük paketteki bir derlemeye başvuran bir uri paketidir. Derleme kaynakları ve paket URI'leri dağıtım sorunlarını basitleştirir. Daha fazla bilgi için [WPF'deki Paket URI'leri'ne](../app-development/pack-uris-in-wpf.md)bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu uzantı yalnızca belirli bir özellik değerini <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>doldurmak için tasarlanmıştır: bir değer.  
  
 Bu uzantıyı kullanarak, yalnızca Windows Aero teması kullanıcının sistemine uygulandığında, diğer stilleri yalnızca Luna teması etkin olduğunda ve benzeri olarak kullanmak üzere yalnızca kaynak derlemesi içeren tek bir kaynak derlemesi belirtebilirsiniz. Bu uzantı kullanılarak, denetime özgü kaynak sözlüğünün içeriği otomatik olarak geçersiz kılınabilir ve gerektiğinde başka bir tema için özel olacak şekilde yeniden yüklenebilir.  
  
 Dize `assemblyUri` <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> (özellik değeri), belirli bir tema için hangi sözlüğün geçerli olduğunu tanımlayan bir adlandırma kuralının temelini oluşturur. Mantık, <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> `ThemeDictionary` önceden derlenmiş bir kaynak derlemesinde yer aldığı gibi belirli bir tema sözlüğü varyantına işaret eden tek bir kaynak tanımlayıcısı (URI) oluşturarak kuralı tamamlar. Bu kuralın veya genel kontrol ve sayfa/uygulama düzeyi stili ile tema etkileşimlerinin bir kavram olarak tanımlanması burada tam olarak ele alınmaz. Kullanmak `ThemeDictionary` için temel senaryo, <xref:System.Windows.ResourceDictionary.Source%2A> uygulama düzeyinde `ResourceDictionary` bildirilen bir özelliği belirtmektir. Doğrudan URI yerine bir `ThemeDictionary` uzantı aracılığıyla montaj için bir URI sağladığınızda, uzantı mantığı sistem teması değiştiğinde geçerli olan geçersiz işeylasyon mantığını sağlar.  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. Tanımlayıcı dizesonra sağlanan `ThemeDictionary` dize belirteci alttaki <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> <xref:System.Windows.ThemeDictionaryExtension> uzantı sınıfının değeri olarak atanır.  
  
 `ThemeDictionary`nesne öğesi sözdiziminde de kullanılabilir. Bu durumda, <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> özelliğin değerini belirterek gereklidir.  
  
 `ThemeDictionary`<xref:System.Windows.Markup.StaticExtension.Member%2A> özelliği özellik=değer çifti olarak belirten ayrıntılı bir öznitelik kullanımında da kullanılabilir:  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır. Yalnızca `ThemeDictionary` bir ayarlanabilen özelliği olduğundan, bu ayrıntılı kullanım tipik değildir.  
  
 İşlemci uygulamasında, bu biçimlendirme uzantısı için işleme <xref:System.Windows.ThemeDictionaryExtension> sınıf tarafından tanımlanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `ThemeDictionary`biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. Öznitelik sözdiziminde { ve } karakterlerini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanan tüm biçimlendirme uzantıları, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini kabul ettiği kuraldır. Daha fazla bilgi için [bkz: Biçimlendirme Uzantıları ve WPF XAML.](markup-extensions-and-wpf-xaml.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Biçimlendirme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları](../app-development/wpf-application-resource-content-and-data-files.md)
