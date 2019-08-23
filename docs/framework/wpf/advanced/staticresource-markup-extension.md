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
ms.openlocfilehash: 7392be182aedeeebe6b7092f9868c1fabfaafcb7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963457"
---
# <a name="staticresource-markup-extension"></a>StaticResource Biçimlendirme Uzantısı
Önceden tanımlanmış bir kaynağa başvuru [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arayarak herhangi bir özellik özniteliği için bir değer sağlar. Bu kaynak için arama davranışı, daha önce geçerli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfanın ve diğer uygulama kaynaklarının biçimlendirmesine göre yüklenen kaynakları arayan yükleme zamanı aramasına benzer ve bu kaynak değeri şu şekilde oluşturur çalışma zamanı nesnelerinde Özellik değeri.  
  
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
|`key`|İstenen kaynak için anahtar. Bu anahtar başlangıçta, biçimlendirme içinde bir kaynak oluşturulduysa veya kaynak kodda oluşturulduysa çağrılırken `key` <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> parametre olarak sağlanmışsa, [x:Key yönergesi](../../xaml-services/x-key-directive.md) tarafından atanır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
> `StaticResource` ,[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Dosya içinde Sözcüksel olarak tanımlanmış bir kaynağa ileri bir başvuru yapmayı denememelidir. Bunun denenmemesi desteklenmez, ancak böyle bir başvurunun başarısız olmasına rağmen, ileri başvurunun denenmemesi, bir <xref:System.Windows.ResourceDictionary> yükü temsil eden iç karma tabloları arandığı zaman bir yükleme süresi performans cezası olur. En iyi sonuçları elde etmek için, kaynak sözlüklerinizin, ileri başvuruların önlenebilir şekilde ayarlanmasını sağlayabilirsiniz. İleri başvuruyu önlememeniz durumunda, bunun yerine [DynamicResource Biçimlendirme Uzantısı](dynamicresource-markup-extension.md) kullanın.  
  
 Belirtilen <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> var olan bir kaynağa karşılık gelmelidir; sayfanızda, uygulamanızda, kullanılabilir denetim temalarından ve dış kaynaklarda veya Sistem kaynaklarında bir [x:Key yönergesi](../../xaml-services/x-key-directive.md) ile tanımlanır. Kaynak arama bu sırada oluşur. Statik ve dinamik kaynaklar için kaynak arama davranışı hakkında daha fazla bilgi için bkz. [xaml kaynakları](xaml-resources.md).  
  
 Kaynak anahtarı [XamlName dilbilgisinde](../../xaml-services/xamlname-grammar.md)tanımlanmış herhangi bir dize olabilir. Kaynak anahtarı, <xref:System.Type>gibi diğer nesne türleri de olabilir. Bir <xref:System.Type> anahtar, bir örtülü stil anahtarı aracılığıyla denetimlerin temalar tarafından nasıl Stillenebilir. Daha fazla bilgi için bkz. [Denetim yazma genel bakış](../controls/control-authoring-overview.md).  
  
 Bir kaynağa başvuran alternatif bildirime dayalı yol, [DynamicResource Biçimlendirme Uzantısı](dynamicresource-markup-extension.md)olarak belirlenir.  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. `StaticResource` Tanımlayıcı dizeden sonra belirtilen dize belirteci, temel <xref:System.Windows.StaticResourceExtension> uzantı sınıfının <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> değeri olarak atanır.  
  
 `StaticResource`nesne öğesi söz dizimi içinde kullanılabilir. Bu durumda, <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> özelliğinin değerini belirtmek gereklidir.  
  
 `StaticResource`, <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> özelliği özellik = değer çifti olarak belirten ayrıntılı bir öznitelik kullanımında de kullanılabilir:  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır. , `StaticResource` Gereken tek bir ayarlanabilir özelliğe sahip olduğundan, bu ayrıntılı kullanım tipik değildir.  
  
 İşlemci uygulamasında, bu biçimlendirme <xref:System.Windows.StaticResourceExtension> uzantısının işlenmesi sınıfı tarafından tanımlanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `StaticResource`bir biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. İçindeki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tüm biçimlendirme uzantıları öznitelik sözdiziminde {ve} karakteri kullanır. Bu, bir işlemcinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tanıdığı bir kuraldır. Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Stil ve Şablon Oluşturma](../controls/styling-and-templating.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [XAML Kaynakları](xaml-resources.md)
- [Kaynaklar ve Kod](resources-and-code.md)
