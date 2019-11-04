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
ms.openlocfilehash: a04e1569f77fed73a480fda3d63cabf6dbc30664
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460513"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource Biçimlendirme Uzantısı
, Bu değerin tanımlı bir kaynağa başvuru olması için bu değeri erteleyerek herhangi bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Özellik özniteliği için bir değer sağlar. Bu kaynak için arama davranışı, çalışma zamanı aramasına benzer.  
  
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
|`key`|İstenen kaynak için anahtar. Bu anahtar başlangıçta [X:Key yönergesi](../../xaml-services/x-key-directive.md) tarafından, bir kaynak biçimlendirme içinde oluşturulduysa veya kaynak kodda oluşturulduysa <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> çağrılırken `key` parametresi olarak sağlanmışsa.|  
  
## <a name="remarks"></a>Açıklamalar  
 `DynamicResource` ilk derleme sırasında geçici bir ifade oluşturur ve bu nedenle, istenen kaynak değeri gerçekten bir nesne oluşturmak için gerekli olana kadar kaynakları aramayı erteleyin. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfası yüklendikten sonra bu olabilir. Kaynak değeri, geçerli sayfa kapsamından başlayarak etkin olan tüm kaynak sözlüklerine karşı anahtar aramasına göre bulunur ve derlemeden yer tutucu ifadesinin yerine konur.  
  
> [!IMPORTANT]
> Bağımlılık özelliği önceliği açısından, bir `DynamicResource` ifadesi dinamik kaynak başvurusunun uygulandığı konuma eşdeğerdir. Önceden yerel değer olarak `DynamicResource` bir ifadeye sahip olan bir özellik için yerel bir değer ayarlarsanız, `DynamicResource` tamamen kaldırılır. Ayrıntılar için bkz. [bağımlılık özelliği değer önceliği](dependency-property-value-precedence.md).  
  
 Belirli kaynak erişim senaryoları, bir [StaticResource Işaretleme uzantısının](staticresource-markup-extension.md)aksine özellikle `DynamicResource` için uygundur. `DynamicResource` ve `StaticResource`göreli birleşme ve performans etkileri hakkında bir tartışma için bkz. [xaml kaynakları](xaml-resources.md) .  
  
 Belirtilen <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>, sayfa, uygulama, kullanılabilir denetim temaları ve dış kaynaklar ya da sistem kaynakları için [X:Key yönergesi](../../xaml-services/x-key-directive.md) tarafından belirlenen mevcut bir kaynağa karşılık gelmelidir ve kaynak arama şu şekilde olur: Bu sipariş. Statik ve dinamik kaynaklar için kaynak arama hakkında daha fazla bilgi için bkz. [xaml kaynakları](xaml-resources.md).  
  
 Kaynak anahtarı [XamlName dilbilgisinde](../../xaml-services/xamlname-grammar.md)tanımlanmış herhangi bir dize olabilir. Kaynak anahtarı, <xref:System.Type>gibi diğer nesne türleri de olabilir. <xref:System.Type> anahtar, denetimlerin temalar tarafından nasıl Stillenebilir. Daha fazla bilgi için bkz. [Denetim yazma genel bakış](../controls/control-authoring-overview.md).  
  
 <xref:System.Windows.FrameworkElement.FindResource%2A>gibi kaynak değerleri araması için API 'Ler, `DynamicResource`tarafından kullanılan aynı kaynak arama mantığını izler.  
  
 Bir kaynağa başvuruda bulunan alternatif bildirime dayalı bir değer, bir [StaticResource Işaretleme uzantısı](staticresource-markup-extension.md)olarak gelir.  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. `DynamicResource` tanımlayıcı dizeden sonra belirtilen dize belirteci, temel <xref:System.Windows.DynamicResourceExtension> uzantı sınıfının <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> değeri olarak atanır.  
  
 `DynamicResource`, nesne öğesi sözdiziminde kullanılabilir. Bu durumda, <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> özelliğinin değerini belirtmek gereklidir.  
  
 `DynamicResource`, özellik = değer çifti olarak <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> özelliğini belirten ayrıntılı bir öznitelik kullanımında de kullanılabilir:  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır. `DynamicResource`, gereken tek bir ayarlanabilir özelliğe sahip olduğundan, bu ayrıntılı kullanım tipik değildir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci uygulamasında, bu biçimlendirme uzantısının işlenmesi <xref:System.Windows.DynamicResourceExtension> sınıfı tarafından tanımlanır.  
  
 `DynamicResource`, biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tüm biçimlendirme uzantıları öznitelik sözdiziminde {ve} karakterlerini kullanır. Bu, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisinin, bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini tanıdığı bir kuraldır. Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML Kaynakları](xaml-resources.md)
- [Kaynaklar ve Kod](resources-and-code.md)
- [x:Key Yönergesi](../../xaml-services/x-key-directive.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [StaticResource İşaretleme Uzantısı](staticresource-markup-extension.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
