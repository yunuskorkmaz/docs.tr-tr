---
title: StaticResource Biçimlendirme Uzantısı
ms.date: 03/30/2017
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
ms.openlocfilehash: 8319e451268152e95326c02027157db72df631b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61981909"
---
# <a name="staticresource-markup-extension"></a>StaticResource Biçimlendirme Uzantısı
İçin herhangi bir değer sağlar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] önceden tanımlanan bir kaynağa başvuru bakarak özelliği özniteliği. Bu kaynak için arama davranışı önceden geçerli yüklenen kaynakları arar yükleme zamanı arama, benzer [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfasında yanı sıra diğer uygulama kaynakları ve kaynak değeri olarak oluşturur çalışma zamanı nesneleri özellik değeri.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`key`|İstenen kaynak anahtarı. Bu anahtar tarafından başlangıçta atandığı [x: Key yönergesi](../../xaml-services/x-key-directive.md) kaynak biçimlendirme içinde oluşturulduysa veya olarak sağlanan `key` çağırırken parametre <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> kaynak kodunda oluşturulduysa.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
>  A `StaticResource` tanımlanmış bir kaynağa bir ileri başvuru yapmak kullanmamanız gerekir içinde sözcüksel [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya. Bunu yapma girişimi desteklenmiyor ve bu tür bir başvuru başarısız olsa bile, ileri başvuru girişimi yük zaman performans cezasına sebep olabilir, iç karma tabloları temsil eden bir <xref:System.Windows.ResourceDictionary> aranır. İleri başvurulara önlenebilir gibi en iyi sonuçlar için kaynak sözlükleri, oluşumunu ayarlayın. İleri başvuru yoksayılamaz kullanırsanız [DynamicResource işaretleme uzantısı](dynamicresource-markup-extension.md) yerine.  
  
 Belirtilen <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> ile tanımlanan, var olan bir kaynağa karşılık gelmelidir bir [x: Key yönergesi](../../xaml-services/x-key-directive.md) düzeyde sayfanız, uygulama, kullanılabilir denetim temalar ve dış kaynaklar veya sistem kaynakları. Kaynak arama, o sırada gerçekleşir. Statik ve dinamik kaynaklar için kaynak arama davranışı hakkında daha fazla bilgi için bkz. [XAML kaynakları](xaml-resources.md).  
  
 Bir kaynak anahtarı içinde tanımlanan herhangi bir dize olabilir [XamlName Dilbilgisi](../../xaml-services/xamlname-grammar.md). Kaynak anahtarı da diğer nesne türleri gibi olabilir bir <xref:System.Type>. A <xref:System.Type> anahtardır nasıl denetimleri, temalar tarafından örtülü stil anahtarı biçimlendirilebilir için temel. Daha fazla bilgi için [denetim yazmaya genel bakış](../controls/control-authoring-overview.md).  
  
 Alternatif bildirime dayanan bir kaynağa başvuran gibidir bir [DynamicResource işaretleme uzantısı](dynamicresource-markup-extension.md).  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. Sonra sağlanan dize belirteci `StaticResource` tanımlayıcı dizesi olarak atandığı <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> temel değer <xref:System.Windows.StaticResourceExtension> uzantısı sınıfı.  
  
 `StaticResource` nesne öğesi sözdiziminde kullanılabilir. Bu durumda, değerini belirterek <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> özelliği gereklidir.  
  
 `StaticResource` belirten ayrıntılı öznitelik kullanımında da ayrıca kullanılabilir <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> bir özellik olarak özellik değer eşleştirmesi:  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır. Çünkü `StaticResource` yalnızca gerekli olan bir ayarlanabilir özelliği, bu ayrıntılı kullanım tipik değildir.  
  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci uygulamasında, bu işaretleme uzantısının işlenmesi tarafından tanımlanır <xref:System.Windows.StaticResourceExtension> sınıfı.  
  
 `StaticResource` bir işaretleme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. İçindeki tüm biçimlendirme uzantıları [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanmak {ve} kuralına göre kendi öznitelik sözdizimi içinde karakterler bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisinin bir işaretleme uzantısı özniteliği işlemesi gerekir. Daha fazla bilgi için [biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Stil ve Şablon Oluşturma](../controls/styling-and-templating.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [XAML Kaynakları](xaml-resources.md)
- [Kaynaklar ve Kod](resources-and-code.md)
