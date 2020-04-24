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
ms.openlocfilehash: 5ccda8ba8f41a30e0ce1c832a6d3176b7fb8e8c2
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646269"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource Biçimlendirme Uzantısı
Bu değeri tanımlı bir kaynağa başvuru olarak erteleyerek herhangi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir özellik özniteliği için bir değer sağlar. Bu kaynağın arama davranışı, çalışma zamanı aramaya benzer.  
  
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
|`key`|İstenen kaynağın anahtarı. Bu anahtar başlangıçta [x:Key Yönergesi](../../../desktop-wpf/xaml-services/xkey-directive.md) tarafından bir kaynak biçimlendirme de `key` oluşturulduysa <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> veya kaynak kod olarak oluşturulduysa parametre olarak sağlanmışsa atanmıştır.|  
  
## <a name="remarks"></a>Açıklamalar  
 A, `DynamicResource` ilk derleme sırasında geçici bir ifade oluşturur ve böylece bir nesne oluşturmak için istenen kaynak değeri gerçekten gerekli olana kadar kaynakları aramayı erteler. Bu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfa yüklendikten sonra olabilir. Kaynak değeri, geçerli sayfa kapsamından başlayarak tüm etkin kaynak sözlüklerine karşı anahtar aramasına göre bulunur ve derlemedeki yer tutucu ifadesinin yerine geçer.  
  
> [!IMPORTANT]
> Bağımlılık özelliği önceliği açısından, bir `DynamicResource` ifade dinamik kaynak başvurusu uygulanan konuma eşdeğerdir. Daha önce yerel değer olarak bir ifade `DynamicResource` olan bir özellik için `DynamicResource` yerel bir değer ayarlarsanız, bu tamamen kaldırılır. Ayrıntılar için Bkz. [Bağımlılık Özelliği Değeri Önceliği.](dependency-property-value-precedence.md)  
  
 Belirli kaynak erişim senaryoları, `DynamicResource` statik kaynak [biçimlendirme uzantısı](staticresource-markup-extension.md)yerine özellikle uygundur. Göreceli yararları ve performans etkileri hakkında bir tartışma için `DynamicResource` [XAML Kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md) bakın ve. `StaticResource`  
  
 Belirtilenler <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> sayfanızda, uygulamanızda, kullanılabilir denetim temaları ve dış kaynaklar veya sistem kaynaklarının belirli bir düzeyinde [x:Key Yönergesi](../../../desktop-wpf/xaml-services/xkey-directive.md) tarafından belirlenen varolan bir kaynağa karşılık gelmelidir ve kaynak araması bu sırada gerçekleşir. Statik ve dinamik kaynaklar için kaynak araması hakkında daha fazla bilgi için [Bkz. XAML Kaynakları.](../../../desktop-wpf/fundamentals/xaml-resources-define.md)  
  
 Kaynak anahtarı [XamlName Grammar'da](../../../desktop-wpf/xaml-services/xamlname-grammar.md)tanımlanan herhangi bir dize olabilir. Kaynak anahtarı, <xref:System.Type>başka nesne türleri de olabilir. Anahtar, <xref:System.Type> denetimlerin temalar tarafından nasıl şekillendirilebildiği konusunda temel dir. Daha fazla bilgi için [bkz.](../controls/control-authoring-overview.md)  
  
 Kaynak değerlerinin araması için API'ler, örneğin, <xref:System.Windows.FrameworkElement.FindResource%2A>tarafından `DynamicResource`kullanılan aynı kaynak arama mantığını izleyin.  
  
 Bir kaynağa başvurmanın alternatif bildirimsel yolu [Statik Kaynak Biçimlendirme Uzantısı](staticresource-markup-extension.md)olarakdır.  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. Tanımlayıcı dizesonra sağlanan `DynamicResource` dize belirteci alttaki <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> <xref:System.Windows.DynamicResourceExtension> uzantı sınıfının değeri olarak atanır.  
  
 `DynamicResource`nesne öğesi sözdiziminde kullanılabilir. Bu durumda, <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> özelliğin değerini belirterek gereklidir.  
  
 `DynamicResource`<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> özelliği özellik=değer çifti olarak belirten ayrıntılı bir öznitelik kullanımında da kullanılabilir:  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır. Yalnızca `DynamicResource` bir ayarlanabilen özelliği olduğundan, bu ayrıntılı kullanım tipik değildir.  
  
 İşlemci uygulamasında, bu biçimlendirme uzantısı için işleme <xref:System.Windows.DynamicResourceExtension> sınıf tarafından tanımlanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `DynamicResource`biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. Öznitelik sözdiziminde { ve } karakterlerini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanan tüm biçimlendirme uzantıları, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini kabul ettiği kuraldır. Daha fazla bilgi için [bkz: Biçimlendirme Uzantıları ve WPF XAML.](markup-extensions-and-wpf-xaml.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML Kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Kaynaklar ve Kod](resources-and-code.md)
- [x:Key Yönergesi](../../../desktop-wpf/xaml-services/xkey-directive.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Biçimlendirme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [StaticResource Biçimlendirme Uzantısı](staticresource-markup-extension.md)
- [Biçimlendirme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
