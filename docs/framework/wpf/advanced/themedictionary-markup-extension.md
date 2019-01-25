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
ms.openlocfilehash: 659af630f697d7f2742bc71006241c4bded842c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718929"
---
# <a name="themedictionary-markup-extension"></a>ThemeDictionary Biçimlendirme Uzantısı
Özel denetim yazarlar veya üçüncü taraf denetimleri temaya özgü kaynak sözlükleri bir denetime stil içinde kullanmak için yüklenecek tümleşen uygulamaları için bir yol sağlar.  
  
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
|`assemblyUri`|[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] Tema bilgileri içeren derleme. Genellikle, bir paketi büyük paketinde bir derlemeye başvuran bir URI budur. Derleme kaynakları ve paketi URI'ler dağıtım sorunlarını basitleştirir. Daha fazla bilgi için [paketi URI ' WPF'de](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu uzantı yalnızca bir özel özellik değerini doldurmak için tasarlanmıştır: bir değer <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.  
  
 Bu uzantıyı kullanarak yalnızca kullanmak için bazı stilleri içeren tek bir yalnızca kaynak derleme belirtebilirsiniz [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] temayı kullanıcının sistem, Luna teması etkin vb. olduğunda diğer stil uygulanır. Bu uzantıyı kullanarak bir özel denetim kaynak sözlüğü içeriğini otomatik olarak geçersiz kılınan ve gerektiğinde başka bir tema için belirli olacak şekilde yeniden.  
  
 `assemblyUri` Dize (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> özellik değerinin) belirli bir temaya hangi sözlüğün uygulandığını tanımlayan bir adlandırma kuralı temelini oluşturur. <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> Mantığı `ThemeDictionary` oluşturarak kuralı tamamlar bir [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] işaret eden bir tema belirli sözlük değişkenine önceden derlenmiş kaynak derleme içinde yer alan olarak. Bu kuralı veya tema etkileşim genel denetimi stil ve sayfa/uygulama düzeyi stili oluşturma, kavram olarak açıklayan tam olarak burada kapsamaz. Kullanmak için temel senaryo `ThemeDictionary` belirtmektir <xref:System.Windows.ResourceDictionary.Source%2A> özelliği bir `ResourceDictionary` uygulama düzeyinde bildirilir. Sağladığınız ne zaman bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] derleme için bir `ThemeDictionary` uzantısı yerine doğrudan [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], sistem tema değiştiğinde uygulanan geçersiz kılma mantığını uzantı mantığı sağlar.  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. Sonra sağlanan dize belirteci `ThemeDictionary` tanımlayıcı dizesi olarak atandığı <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> temel değer <xref:System.Windows.ThemeDictionaryExtension> uzantısı sınıfı.  
  
 `ThemeDictionary` Ayrıca nesne öğesi sözdiziminde kullanılabilir. Bu durumda, değerini belirterek <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> özelliği gereklidir.  
  
 `ThemeDictionary` belirten ayrıntılı öznitelik kullanımında da ayrıca kullanılabilir <xref:System.Windows.Markup.StaticExtension.Member%2A> bir özellik olarak özellik değer eşleştirmesi:  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır. Çünkü `ThemeDictionary` yalnızca gerekli olan bir ayarlanabilir özelliği, bu ayrıntılı kullanım tipik değildir.  
  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci uygulamasında, bu işaretleme uzantısının işlenmesi tarafından tanımlanır <xref:System.Windows.ThemeDictionaryExtension> sınıfı.  
  
 `ThemeDictionary` bir işaretleme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. İçindeki tüm biçimlendirme uzantıları [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanmak {ve} kuralına göre kendi öznitelik sözdizimi içinde karakterler bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisinin bir işaretleme uzantısı özniteliği işlemesi gerekir. Daha fazla bilgi için [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [İşaretleme Uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
