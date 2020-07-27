---
title: StaticResource Biçimlendirme Uzantısı
description: Önceden tanımlanmış bir kaynağa bir başvuru arayarak herhangi bir XAML özellik özniteliği için bir değer sağlar.
ms.date: 03/30/2017
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
ms.openlocfilehash: 77396c1867dcbe279d7ba158ed9e6f5f833f17b5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164673"
---
# <a name="staticresource-markup-extension"></a>StaticResource Biçimlendirme Uzantısı
[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]Önceden tanımlanmış bir kaynağa başvuru arayarak herhangi bir özellik özniteliği için bir değer sağlar. Bu kaynak için arama davranışı, daha önce geçerli sayfanın ve diğer uygulama kaynaklarının biçimlendirmesine göre yüklenen kaynakları arayan yükleme zamanı aramasına benzer [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve çalışma zamanı nesnelerinde Özellik değeri olarak bu kaynak değerini oluşturacaktır.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xml  
<object property="{StaticResource key}" ... />  
```  
  
## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" ... />  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`key`|İstenen kaynak için anahtar. Bu anahtar başlangıçta, biçimlendirme içinde bir [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) kaynak oluşturulduysa veya `key` <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> kaynak kodda oluşturulduysa çağrılırken parametre olarak sağlanmışsa, x:Key yönergesi tarafından atanır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
> `StaticResource`, Dosya içinde Sözcüksel olarak tanımlanmış bir kaynağa ileri bir başvuru yapmayı denememelidir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Bunun denenmemesi desteklenmez, ancak böyle bir başvurunun başarısız olmasına rağmen, ileri başvurunun denenmemesi, bir yükü temsil eden iç karma tabloları arandığı zaman bir yükleme süresi performans cezası olur <xref:System.Windows.ResourceDictionary> . En iyi sonuçları elde etmek için, kaynak sözlüklerinizin, ileri başvuruların önlenebilir şekilde ayarlanmasını sağlayabilirsiniz. İleri başvuruyu önlememeniz durumunda, bunun yerine [DynamicResource Biçimlendirme Uzantısı](dynamicresource-markup-extension.md) kullanın.  
  
 Belirtilen <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> var olan bir kaynağa karşılık gelmelidir; sayfanızda, uygulamanızda, kullanılabilir denetim temalarından ve dış kaynaklarda veya Sistem kaynaklarında bir [X:Key yönergesi](../../../desktop-wpf/xaml-services/xkey-directive.md) ile tanımlanır. Kaynak arama bu sırada oluşur. Statik ve dinamik kaynaklar için kaynak arama davranışı hakkında daha fazla bilgi için bkz. [xaml kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 Kaynak anahtarı [XamlName dilbilgisinde](../../../desktop-wpf/xaml-services/xamlname-grammar.md)tanımlanmış herhangi bir dize olabilir. Kaynak anahtarı, gibi diğer nesne türleri de olabilir <xref:System.Type> . Bir <xref:System.Type> anahtar, bir örtülü stil anahtarı aracılığıyla denetimlerin temalar tarafından nasıl Stillenebilir. Daha fazla bilgi için bkz. [Denetim yazma genel bakış](../controls/control-authoring-overview.md).  
  
 Bir kaynağa başvuran alternatif bildirime dayalı yol, [DynamicResource Biçimlendirme Uzantısı](dynamicresource-markup-extension.md)olarak belirlenir.  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. Tanımlayıcı dizeden sonra belirtilen dize belirteci, `StaticResource` <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> temel uzantı sınıfının değeri olarak atanır <xref:System.Windows.StaticResourceExtension> .  
  
 `StaticResource`nesne öğesi söz dizimi içinde kullanılabilir. Bu durumda, özelliğinin değerini belirtmek <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> gereklidir.  
  
 `StaticResource`, özelliği <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> özellik = değer çifti olarak belirten ayrıntılı bir öznitelik kullanımında de kullanılabilir:  
  
```xml  
<object property="{StaticResource ResourceKey=key}" ... />  
```  
  
 Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır. , `StaticResource` Gereken tek bir ayarlanabilir özelliğe sahip olduğundan, bu ayrıntılı kullanım tipik değildir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] İşlemci uygulamasında, bu biçimlendirme uzantısının işlenmesi sınıfı tarafından tanımlanır <xref:System.Windows.StaticResourceExtension> .  
  
 `StaticResource`bir biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. İçindeki tüm biçimlendirme uzantıları [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelik sözdiziminde {ve} karakteri kullanır. Bu, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini tanıdığı bir kuraldır. Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Biçimlendirme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [XAML Kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Kaynaklar ve Kod](resources-and-code.md)
