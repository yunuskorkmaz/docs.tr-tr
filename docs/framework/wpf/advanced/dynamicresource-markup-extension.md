---
title: "DynamicResource Biçimlendirme Uzantısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DynamicResource
- DynamicResourceExtension
helpviewer_keywords:
- XAML [WPF], DynamicResource markup extension
- DynamicResource markup extensions [WPF]
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f6c8500f9b9cd6d617789a2da3444519971ae81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource Biçimlendirme Uzantısı
İçin herhangi bir değer sağlar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] özellik özniteliği tarafından tanımlanan bir kaynağa başvuru olması için bu değeri erteleniyor. Bu kaynak için arama davranışı çalışma zamanı aramasına benzer.  
  
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
|`key`|İstenen kaynak için anahtar. Bu anahtar tarafından başlangıçta atandığı [x: Key yönergesi](../../../../docs/framework/xaml-services/x-key-directive.md) bir kaynak biçimlendirme içinde oluşturulduğu veya olarak sağlanan `key` çağırırken parametre <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> kaynak kodunda oluşturduysanız.|  
  
## <a name="remarks"></a>Açıklamalar  
 A `DynamicResource` ilk derleme sırasında geçici bir ifade oluşturur ve bu nedenle istenen kaynak değeri bir nesne oluşturmak için gerçekten gerekli olana kadar kaynaklara arama erteleneceği. Bu büyük olasılıkla sonra olabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfa yüklenir. Kaynak değeri geçerli sayfanın kapsamdan başlayarak tüm etkin kaynak sözlüklerindeki karşı anahtar arama göre bulundu ve derleme yer tutucu ifade için değiştirdi.  
  
> [!IMPORTANT]
>  Bağımlılık özelliği önceliği açısından bir `DynamicResource` ifadesi dinamik kaynak başvurusu uygulanan burada konuma eşdeğerdir. Daha önce sahip bir özellik için yerel bir değer ayarlarsanız bir `DynamicResource` ifade yerel değerin olarak `DynamicResource` tamamen kaldırılır. Ayrıntılar için bkz [bağımlılık özelliği değeri önceliği](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).  
  
 Belirli kaynak erişim senaryoları için özellikle uygun `DynamicResource` tersine bir [StaticResource biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md). Bkz: [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md) göreli değeri ve performans etkileri hakkında tartışma için `DynamicResource` ve `StaticResource`.  
  
 Belirtilen <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> tarafından belirlenen varolan bir kaynağa karşılık gelmelidir [x: Key yönergesi](../../../../docs/framework/xaml-services/x-key-directive.md) sayfanızı, uygulama, kullanılabilir denetim temalar ve dış kaynaklara veya sistem kaynaklarının düzeyde ve Kaynak arama, o sırada gerçekleşir. Statik ve dinamik kaynaklara kaynak arama hakkında daha fazla bilgi için bkz: [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Kaynak anahtarı içinde tanımlanan herhangi bir dize olabilir [XamlName Dilbilgisi](../../../../docs/framework/xaml-services/xamlname-grammar.md). Kaynak anahtarı da diğer nesne türleri gibi olabilir bir <xref:System.Type>. A <xref:System.Type> anahtarıdır denetimleri temalar tarafından nasıl biçimlendirilebilir için temel. Daha fazla bilgi için bkz: [denetimine genel bakış yazma](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]Kaynak değerleri araması için gibi <xref:System.Windows.FrameworkElement.FindResource%2A>, tarafından kullanılan aynı kaynak arama mantığını izleyin `DynamicResource`.  
  
 Alternatif bildirime dayanan bir kaynağa başvuran olduğundan bir [StaticResource biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. Sonra sağlanan dize belirteci `DynamicResource` kimlik dizesi olarak atandığı <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> temel değer <xref:System.Windows.DynamicResourceExtension> uzantısı sınıfı.  
  
 `DynamicResource`nesne öğesi sözdiziminde kullanılabilir. Bu durumda, değerini belirten <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> özelliği gereklidir.  
  
 `DynamicResource`belirten bir ayrıntılı öznitelik kullanımı da kullanılabilir <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> özelliği bir özellik olarak değer çifti =:  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır. Çünkü `DynamicResource` yalnızca gerekli olan bir ayarlanabilir özelliği, bu ayrıntılı kullanım tipik sahiptir.  
  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci uygulamasında, bu biçimlendirme uzantısı işlenmesi tarafından tanımlanan <xref:System.Windows.DynamicResourceExtension> sınıfı.  
  
 `DynamicResource`bir biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. İçindeki tüm biçimlendirme uzantıları [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanmak {ve} kurala göre kendi öznitelik sözdiziminde karakterler bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci tanıdığı biçimlendirme uzantısı öznitelik işlemelidir. Daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML Kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Kaynaklar ve Kod](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [x:Key Yönergesi](../../../../docs/framework/xaml-services/x-key-directive.md)  
 [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [İşaretleme Uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [StaticResource İşaretleme Uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)  
 [İşaretleme Uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
