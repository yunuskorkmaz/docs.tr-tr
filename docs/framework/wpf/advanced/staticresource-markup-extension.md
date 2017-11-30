---
title: "StaticResource Biçimlendirme Uzantısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 821cd152ccb7a02dda5338d6a3ec44d6625c0097
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="staticresource-markup-extension"></a>StaticResource Biçimlendirme Uzantısı
İçin herhangi bir değer sağlar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] önceden tanımlanan bir kaynağa başvuru bakarak özellik özniteliği. Bu kaynak için arama davranışı önceden geçerli yüklenen kaynakları arar yükleme zamanı aramasına benzer [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfasında yanı sıra diğer uygulama kaynakları ve kaynak değeri olarak oluşturur çalışma zamanı nesnelerindeki özellik değeri.  
  
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
|`key`|İstenen kaynak için anahtar. Bu anahtar tarafından başlangıçta atandığı [x: Key yönergesi](../../../../docs/framework/xaml-services/x-key-directive.md) bir kaynak biçimlendirme içinde oluşturulduğu veya olarak sağlanan `key` çağırırken parametre <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> kaynak kodunda oluşturduysanız.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
>  A `StaticResource` tanımlanan bir kaynağa ileriye doğru bir başvuru yapmak çalışmamalısınız içinde sözcüksel [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya. Bunu yapmak çalışırken desteklenmiyor ve bu tür bir başvuru başarısız olsa bile, ileri başvuru girişimi yükleme zamanı performans cezasına sebep olabilir zaman temsil eden iç karma tabloları bir <xref:System.Windows.ResourceDictionary> aranır. En iyi sonuçlar için İleri başvuruları önlenebilir gibi kaynak sözlüklerindeki oluşumunu ayarlayın. İleriye doğru bir başvuru yoksayılamaz kullanırsanız [DynamicResource Biçimlendirme Uzantısı](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) yerine.  
  
 Belirtilen <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> ile tanımlanan, varolan bir kaynağa karşılık gelmelidir bir [x: Key yönergesi](../../../../docs/framework/xaml-services/x-key-directive.md) sayfanızı, uygulama, kullanılabilir denetim temalar ve dış kaynaklara veya sistem kaynakları düzeyde. Kaynak arama, o sırada oluşur. Statik ve dinamik kaynaklara kaynak arama davranışı hakkında daha fazla bilgi için bkz: [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Kaynak anahtarı içinde tanımlanan herhangi bir dize olabilir [XamlName Dilbilgisi](../../../../docs/framework/xaml-services/xamlname-grammar.md). Kaynak anahtarı da diğer nesne türleri gibi olabilir bir <xref:System.Type>. A <xref:System.Type> anahtarıdır nasıl denetimleri temalar tarafından örtülü stil anahtarı biçimlendirilebilir için temel. Daha fazla bilgi için bkz: [denetimine genel bakış yazma](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Alternatif bildirime dayanan bir kaynağa başvuran olduğundan bir [DynamicResource Biçimlendirme Uzantısı](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md).  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. Sonra sağlanan dize belirteci `StaticResource` kimlik dizesi olarak atandığı <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> temel değer <xref:System.Windows.StaticResourceExtension> uzantısı sınıfı.  
  
 `StaticResource`nesne öğesi sözdiziminde kullanılabilir. Bu durumda, değerini belirten <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> özelliği gereklidir.  
  
 `StaticResource`belirten bir ayrıntılı öznitelik kullanımı da kullanılabilir <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> özelliği bir özellik olarak değer çifti =:  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır. Çünkü `StaticResource` yalnızca gerekli olan bir ayarlanabilir özelliği, bu ayrıntılı kullanım tipik sahiptir.  
  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci uygulamasında, bu biçimlendirme uzantısı işlenmesi tarafından tanımlanan <xref:System.Windows.StaticResourceExtension> sınıfı.  
  
 `StaticResource`bir biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. İçindeki tüm biçimlendirme uzantıları [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanmak {ve} kurala göre kendi öznitelik sözdiziminde karakterler bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci tanıdığı biçimlendirme uzantısı öznitelik işlemelidir. Daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Stil ve şablon oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Kaynaklar ve kod](../../../../docs/framework/wpf/advanced/resources-and-code.md)
