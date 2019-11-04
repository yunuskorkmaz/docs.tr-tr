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
ms.openlocfilehash: ab38c2c885e230183852fff895e0a8a8f1d7a666
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459480"
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
|`assemblyUri`|Tema bilgilerini içeren derlemenin Tekdüzen Kaynak tanımlayıcısı (URI). Genellikle, bu, daha büyük paketteki bir derlemeye başvuran bir paket URI 'sidir. Derleme kaynakları ve paket URI 'Leri dağıtım sorunlarını basitleştirir. Daha fazla bilgi için bkz. [WPF 'de paket URI 'leri](../app-development/pack-uris-in-wpf.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu uzantı yalnızca bir özel özellik değerini doldurmaya yöneliktir: <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>için bir değer.  
  
 Bu uzantıyı kullanarak yalnızca Windows Aero teması Kullanıcı sistemine uygulandığında kullanılacak bazı stilleri, yalnızca Luna teması etkin olduğunda diğer stilleri ve bu şekilde devam eden tek bir kaynak derleme belirtebilirsiniz. Bu uzantıyı kullanarak, denetime özgü bir kaynak sözlüğünün içeriği gerektiğinde başka bir temaya özgü olacak şekilde otomatik olarak geçersiz kılınabilir ve yeniden yüklenebilir.  
  
 `assemblyUri` dizesi (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> Özellik değeri), belirli bir tema için hangi sözlüğün uygulanacağını belirleyen bir adlandırma kuralının temelini oluşturur. `ThemeDictionary` için <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> mantığı, önceden derlenmiş bir kaynak derlemesi içinde yer alan belirli bir tema sözlüğü çeşidine işaret eden bir Tekdüzen Kaynak tanımlayıcısı (URI) oluşturarak kuralı tamamlar. Bu kuralı veya genel denetim stili ve sayfa/uygulama düzeyi stillendirme ile bir kavram olarak tema etkileşimleri, burada tam olarak kapsanmaz. `ThemeDictionary` kullanmaya yönelik temel senaryo, uygulama düzeyinde tanımlanan bir `ResourceDictionary` <xref:System.Windows.ResourceDictionary.Source%2A> özelliğini belirtmektir. Doğrudan URI yerine `ThemeDictionary` uzantısı aracılığıyla derleme için bir URI sağladığınızda, uzantı mantığı sistem teması her değiştiğinde geçerli olan geçersiz kılma mantığı sağlar.  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. `ThemeDictionary` tanımlayıcı dizeden sonra belirtilen dize belirteci, temel <xref:System.Windows.ThemeDictionaryExtension> uzantı sınıfının <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> değeri olarak atanır.  
  
 `ThemeDictionary`, nesne öğesi söz diziminde de kullanılabilir. Bu durumda, <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> özelliğinin değerini belirtmek gereklidir.  
  
 `ThemeDictionary`, özellik = değer çifti olarak <xref:System.Windows.Markup.StaticExtension.Member%2A> özelliğini belirten ayrıntılı bir öznitelik kullanımında de kullanılabilir:  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır. `ThemeDictionary`, gereken tek bir ayarlanabilir özelliğe sahip olduğundan, bu ayrıntılı kullanım tipik değildir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci uygulamasında, bu biçimlendirme uzantısının işlenmesi <xref:System.Windows.ThemeDictionaryExtension> sınıfı tarafından tanımlanır.  
  
 `ThemeDictionary`, biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tüm biçimlendirme uzantıları öznitelik sözdiziminde {ve} karakterlerini kullanır. Bu, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisinin, bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini tanıdığı bir kuraldır. Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Stil ve Şablon Oluşturma](../controls/styling-and-templating.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları](../app-development/wpf-application-resource-content-and-data-files.md)
