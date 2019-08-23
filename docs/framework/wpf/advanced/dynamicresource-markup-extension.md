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
ms.openlocfilehash: 06355c64d36d2688ef027c1940688d4c87e51ec8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964793"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource Biçimlendirme Uzantısı
Herhangi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir özellik özniteliği için, bu değerin tanımlı bir kaynağa başvuru olarak erteleyerek bir değer sağlar. Bu kaynak için arama davranışı, çalışma zamanı aramasına benzer.  
  
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
|`key`|İstenen kaynak için anahtar. Bu anahtar başlangıçta, biçimlendirme içinde bir kaynak oluşturulduysa veya kaynak kodda oluşturulduysa çağrılırken `key` <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> parametre olarak sağlanmışsa, [x:Key yönergesi](../../xaml-services/x-key-directive.md) tarafından atanır.|  
  
## <a name="remarks"></a>Açıklamalar  
 , İlk derleme sırasında geçici bir ifade oluşturur ve Bunedenle,istenenkaynakdeğerigerçektenbirnesneoluşturmakiçingerekliolanakadarkaynaklarıaramayıerteleyin.`DynamicResource` Bu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfa yüklendikten sonra olabilir. Kaynak değeri, geçerli sayfa kapsamından başlayarak etkin olan tüm kaynak sözlüklerine karşı anahtar aramasına göre bulunur ve derlemeden yer tutucu ifadesinin yerine konur.  
  
> [!IMPORTANT]
> Bağımlılık özelliği önceliği açısından, bir `DynamicResource` ifade dinamik kaynak başvurusunun uygulandığı konuma eşdeğerdir. Önceden yerel değer olarak bir `DynamicResource` ifadeye sahip olan bir özellik için yerel bir değer ayarlarsanız, `DynamicResource` tamamen kaldırılır. Ayrıntılar için bkz. [bağımlılık özelliği değer önceliği](dependency-property-value-precedence.md).  
  
 Belirli kaynak erişim senaryoları, bir `DynamicResource` [StaticResource İşaretleme uzantısının](staticresource-markup-extension.md)aksine özellikle uygundur. Ve ' `DynamicResource` ningörelibirleşmeveperformansetkilerihakkındabirtartışmaiçinbkz.xamlkaynakları.`StaticResource` [](xaml-resources.md)  
  
 Belirtilen <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> mevcut bir kaynağa karşılık gelen [x:Key yönergesi](../../xaml-services/x-key-directive.md) sayfa, uygulama, kullanılabilir denetim temaları ve dış kaynaklar ya da sistem kaynakları ve kaynak arama gerçekleşecektir. Bu sırada. Statik ve dinamik kaynaklar için kaynak arama hakkında daha fazla bilgi için bkz. [xaml kaynakları](xaml-resources.md).  
  
 Kaynak anahtarı [XamlName dilbilgisinde](../../xaml-services/xamlname-grammar.md)tanımlanmış herhangi bir dize olabilir. Kaynak anahtarı, <xref:System.Type>gibi diğer nesne türleri de olabilir. Bir <xref:System.Type> anahtar, denetimlerin temalar tarafından nasıl Stillenebilir. Daha fazla bilgi için bkz. [Denetim yazma genel bakış](../controls/control-authoring-overview.md).  
  
 Kaynak değerlerinin <xref:System.Windows.FrameworkElement.FindResource%2A>aranması için API 'ler, gibi, tarafından `DynamicResource`kullanılan kaynak arama mantığını da izler.  
  
 Bir kaynağa başvuruda bulunan alternatif bildirime dayalı bir değer, bir [StaticResource Işaretleme uzantısı](staticresource-markup-extension.md)olarak gelir.  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. `DynamicResource` Tanımlayıcı dizeden sonra belirtilen dize belirteci, temel <xref:System.Windows.DynamicResourceExtension> uzantı sınıfının <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> değeri olarak atanır.  
  
 `DynamicResource`nesne öğesi söz dizimi içinde kullanılabilir. Bu durumda, <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> özelliğinin değerini belirtmek gereklidir.  
  
 `DynamicResource`, <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> özelliği özellik = değer çifti olarak belirten ayrıntılı bir öznitelik kullanımında de kullanılabilir:  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır. , `DynamicResource` Gereken tek bir ayarlanabilir özelliğe sahip olduğundan, bu ayrıntılı kullanım tipik değildir.  
  
 İşlemci uygulamasında, bu biçimlendirme <xref:System.Windows.DynamicResourceExtension> uzantısının işlenmesi sınıfı tarafından tanımlanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `DynamicResource`bir biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. İçindeki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tüm biçimlendirme uzantıları öznitelik sözdiziminde {ve} karakteri kullanır. Bu, bir işlemcinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tanıdığı bir kuraldır. Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML Kaynakları](xaml-resources.md)
- [Kaynaklar ve Kod](resources-and-code.md)
- [x:Key Yönergesi](../../xaml-services/x-key-directive.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [StaticResource İşaretleme Uzantısı](staticresource-markup-extension.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
