---
title: DynamicResource Biçimlendirme Uzantısı
ms.date: 03/30/2017
f1_keywords:
- DynamicResource
- DynamicResourceExtension
helpviewer_keywords:
- XAML [WPF], DynamicResource markup extension
- DynamicResource markup extensions [WPF]
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
ms.openlocfilehash: a7b754ce3fb77314539e6391376b188fe9b15859
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369779"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource Biçimlendirme Uzantısı
İçin herhangi bir değer sağlar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] özellik özniteliği tarafından tanımlanan kaynağına başvuru olması için bu değeri erteleniyor. Bu kaynak için arama davranışı için çalışma zamanı arama benzerdir.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xml  
<object property="{DynamicResource key}" .../>  
```  
  
## <a name="xaml-property-element-usage"></a>XAML Özellik Öğesi Kullanımı  
  
```xml  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`key`|İstenen kaynak anahtarı. Bu anahtar tarafından başlangıçta atandığı [x: Key yönergesi](../../xaml-services/x-key-directive.md) kaynak biçimlendirme içinde oluşturulduysa veya olarak sağlanan `key` çağırırken parametre <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> kaynak kodunda oluşturulduysa.|  
  
## <a name="remarks"></a>Açıklamalar  
 A `DynamicResource` ilk derleme sırasında geçici bir ifade oluşturur ve istenen kaynak değeri bir nesne oluşturmak için gerçekten gerekli olana kadar bu nedenle kaynaklara arama erteleyin. Bu büyük olasılıkla sonra olabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfası yüklenir. Kaynak değeri geçerli sayfa kapsamdan başlayarak tüm etkin kaynak sözlükleri karşı anahtar arama göre bulundu ve derleme yer tutucu ifade için değiştirilir.  
  
> [!IMPORTANT]
>  Bağımlılık özelliği önceliği açısından bir `DynamicResource` ifade dinamik kaynak başvurusu uygulanan burada konuma eşdeğerdir. Daha önce sahip olan özellik için yerel bir değer ayarlarsanız bir `DynamicResource` yerel değer olarak ifade `DynamicResource` tamamen kaldırılır. Ayrıntılar için bkz [bağımlılık özelliği değer önceliği](dependency-property-value-precedence.md).  
  
 Belirli kaynak erişim senaryoları için uygun özellikle `DynamicResource` başlangıcı yerine sonundan bir [StaticResource işaretleme uzantısı](staticresource-markup-extension.md). Bkz: [XAML kaynakları](xaml-resources.md) göreli değeri ve performans etkilerini hakkında bir tartışma için `DynamicResource` ve `StaticResource`.  
  
 Belirtilen <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> mevcut bir kaynak tarafından belirlenen karşılık gelmelidir [x: Key yönergesi](../../xaml-services/x-key-directive.md) sayfanız, uygulama, kullanılabilir denetim temalar ve dış kaynaklar veya sistem kaynakları düzeyde ve Kaynak arama, o sırada gerçekleşir. Statik ve dinamik kaynaklar için kaynak araması hakkında daha fazla bilgi için bkz: [XAML kaynakları](xaml-resources.md).  
  
 Kaynak anahtarı içinde tanımlanan herhangi bir dize olabilir [XamlName Dilbilgisi](../../xaml-services/xamlname-grammar.md). Kaynak anahtarı diğer nesne türleri gibi de içerebilir bir <xref:System.Type>. A <xref:System.Type> anahtardır denetimleri tarafından temaları nasıl biçimlendirilebilir için temel. Daha fazla bilgi için [denetim yazmaya genel bakış](../controls/control-authoring-overview.md).  
  
 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] Kaynak değerler, arama için gibi <xref:System.Windows.FrameworkElement.FindResource%2A>, tarafından kullanılan aynı kaynak araması mantığını izleyin `DynamicResource`.  
  
 Alternatif bildirime dayanan bir kaynağa başvuran gibidir bir [StaticResource işaretleme uzantısı](staticresource-markup-extension.md).  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. Sonra sağlanan dize belirteci `DynamicResource` tanımlayıcı dizesi olarak atandığı <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> temel değer <xref:System.Windows.DynamicResourceExtension> uzantısı sınıfı.  
  
 `DynamicResource` nesne öğesi sözdiziminde kullanılabilir. Bu durumda, değerini belirterek <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> özelliği gereklidir.  
  
 `DynamicResource` belirten ayrıntılı öznitelik kullanımında da ayrıca kullanılabilir <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> bir özellik olarak özellik değer eşleştirmesi:  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır. Çünkü `DynamicResource` yalnızca gerekli olan bir ayarlanabilir özelliği, bu ayrıntılı kullanım tipik değildir.  
  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci uygulamasında, bu işaretleme uzantısının işlenmesi tarafından tanımlanır <xref:System.Windows.DynamicResourceExtension> sınıfı.  
  
 `DynamicResource` bir işaretleme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. İçindeki tüm biçimlendirme uzantıları [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanmak {ve} kuralına göre kendi öznitelik sözdizimi içinde karakterler bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisinin bir işaretleme uzantısı özniteliği işlemesi gerekir. Daha fazla bilgi için [biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [XAML Kaynakları](xaml-resources.md)
- [Kaynaklar ve Kod](resources-and-code.md)
- [x:Key Yönergesi](../../xaml-services/x-key-directive.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [StaticResource İşaretleme Uzantısı](staticresource-markup-extension.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
