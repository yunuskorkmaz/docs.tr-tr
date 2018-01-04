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
ms.workload: dotnet
ms.openlocfilehash: 2372961cdc889528f13e13dd1f1760608030275e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="themedictionary-markup-extension"></a>ThemeDictionary Biçimlendirme Uzantısı
Özel denetim yazarlar ya da üçüncü taraf denetimlerinin denetime stil kullanmak için özel tema kaynak sözlüklerindeki yüklemek için tümleştirme uygulamaları için bir yol sağlar.  
  
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
|`assemblyUri`|[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] Tema bilgilerini içeren derleme. Genellikle, bir paketi büyük paketindeki bir derlemeye başvurur URI budur. Bütünleştirilmiş kod kaynakları ve paketi URI'ler dağıtım sorunlarını basitleştirir. Daha fazla bilgi için bkz: [Pack URI WPF'de](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu uzantı yalnızca bir özel özellik değerini doldurmak için tasarlanmıştır: için bir değer <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.  
  
 Bu uzantıyı kullanarak, yalnızca kullanmak için bazı stilleri içeren tek bir yalnızca kaynak derleme belirtebilirsiniz [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] temayı kullanıcının sisteme Luna teması etkin vb. olduğunda diğer stilleri uygulanır. Bu uzantıyı kullanarak bir özel denetim kaynak sözlüğü içeriğini otomatik olarak geçersiz kılınan ve gerektiğinde başka bir tema için belirli olacak şekilde yeniden.  
  
 `assemblyUri` Dize (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> özellik değeri) hangi sözlüğün belirli bir temaya uygulandığını tanımlayan bir adlandırma kuralı temelini oluşturur. <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> Mantığı `ThemeDictionary` oluşturarak kuralı tamamlar bir [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] önceden derlenmiş kaynak assembly içinde yer alan gibi belirli tema sözlük değişkenine işaret. Bu kuralı veya genel denetim stil ve sayfa ve uygulama düzeyi stil bir kavram olarak ile tema etkileşimlerini açıklayan burada tam olarak ele alınmamıştır. Kullanmak için temel senaryo `ThemeDictionary` belirtmektir <xref:System.Windows.ResourceDictionary.Source%2A> özelliği bir `ResourceDictionary` uygulama düzeyinde bildirilmedi. Sağladığınız ne zaman bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] derleme için bir `ThemeDictionary` uzantısı yerine doğrudan [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], uzantı mantığı sistem teması değiştiğinde uygulayan geçersiz kılma mantığını sağlar.  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. Sonra sağlanan dize belirteci `ThemeDictionary` kimlik dizesi olarak atandığı <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> temel değer <xref:System.Windows.ThemeDictionaryExtension> uzantısı sınıfı.  
  
 `ThemeDictionary`Ayrıca nesne öğesi sözdiziminde kullanılabilir. Bu durumda, değerini belirten <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> özelliği gereklidir.  
  
 `ThemeDictionary`belirten bir ayrıntılı öznitelik kullanımı da kullanılabilir <xref:System.Windows.Markup.StaticExtension.Member%2A> özelliği bir özellik olarak değer çifti =:  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır. Çünkü `ThemeDictionary` yalnızca gerekli olan bir ayarlanabilir özelliği, bu ayrıntılı kullanım tipik sahiptir.  
  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci uygulamasında, bu biçimlendirme uzantısı işlenmesi tarafından tanımlanan <xref:System.Windows.ThemeDictionaryExtension> sınıfı.  
  
 `ThemeDictionary`bir biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. İçindeki tüm biçimlendirme uzantıları [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanmak {ve} kurala göre kendi öznitelik sözdiziminde karakterler bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci tanıdığı biçimlendirme uzantısı öznitelik işlemelidir. Daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [İşaretleme Uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
