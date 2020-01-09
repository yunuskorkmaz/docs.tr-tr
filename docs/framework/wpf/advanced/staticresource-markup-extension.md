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
ms.openlocfilehash: aa7f69e8871295006c3c5a9c7d0a70d0ecbd6d7e
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559826"
---
# <a name="staticresource-markup-extension"></a>StaticResource Biçimlendirme Uzantısı
Önceden tanımlanmış bir kaynağa başvuru arayarak herhangi bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Özellik özniteliği için bir değer sağlar. Bu kaynağın arama davranışı, daha önce geçerli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfasının ve diğer uygulama kaynaklarının biçimlendirmesine göre yüklenen kaynakları ve çalışma zamanı nesnelerinde Özellik değeri olarak bu kaynak değerini oluşturacak olan yükleme zamanı aramasına benzer.  
  
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
|`key`|İstenen kaynak için anahtar. Bu anahtar başlangıçta [X:Key yönergesi](../../../desktop-wpf/xaml-services/xkey-directive.md) tarafından, bir kaynak biçimlendirme içinde oluşturulduysa veya kaynak kodda oluşturulduysa <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> çağrılırken `key` parametresi olarak sağlanmışsa.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
> `StaticResource`, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyasında sözcüksel olarak tanımlanmış bir kaynağa ileri bir başvuru yapmayı denememelidir. Bunun denenmemesi desteklenmez, ancak böyle bir başvuru başarısız olmasa bile, bir <xref:System.Windows.ResourceDictionary> temsil eden iç karma tabloları arandığı zaman, ileri başvurunun denenmesine yönelik bir yükleme süresi performans cezası olur. En iyi sonuçları elde etmek için, kaynak sözlüklerinizin, ileri başvuruların önlenebilir şekilde ayarlanmasını sağlayabilirsiniz. İleri başvuruyu önlememeniz durumunda, bunun yerine [DynamicResource Biçimlendirme Uzantısı](dynamicresource-markup-extension.md) kullanın.  
  
 Belirtilen <xref:System.Windows.StaticResourceExtension.ResourceKey%2A>, sayfa, uygulama, kullanılabilir denetim temaları ve dış kaynaklar ya da sistem kaynakları için bir [X:Key yönergesi](../../../desktop-wpf/xaml-services/xkey-directive.md) ile tanımlanmış mevcut bir kaynağa karşılık gelmelidir. Kaynak arama bu sırada oluşur. Statik ve dinamik kaynaklar için kaynak arama davranışı hakkında daha fazla bilgi için bkz. [xaml kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 Kaynak anahtarı [XamlName dilbilgisinde](../../../desktop-wpf/xaml-services/xamlname-grammar.md)tanımlanmış herhangi bir dize olabilir. Kaynak anahtarı, <xref:System.Type>gibi diğer nesne türleri de olabilir. <xref:System.Type> anahtar, denetimlerin temalar tarafından nasıl Stillenebilir ve örtülü bir stil anahtarıyla bir temel değer. Daha fazla bilgi için bkz. [Denetim yazma genel bakış](../controls/control-authoring-overview.md).  
  
 Bir kaynağa başvuran alternatif bildirime dayalı yol, [DynamicResource Biçimlendirme Uzantısı](dynamicresource-markup-extension.md)olarak belirlenir.  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. `StaticResource` tanımlayıcı dizeden sonra belirtilen dize belirteci, temel <xref:System.Windows.StaticResourceExtension> uzantı sınıfının <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> değeri olarak atanır.  
  
 `StaticResource`, nesne öğesi sözdiziminde kullanılabilir. Bu durumda, <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> özelliğinin değerini belirtmek gereklidir.  
  
 `StaticResource`, özellik = değer çifti olarak <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> özelliğini belirten ayrıntılı bir öznitelik kullanımında de kullanılabilir:  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır. `StaticResource`, gereken tek bir ayarlanabilir özelliğe sahip olduğundan, bu ayrıntılı kullanım tipik değildir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci uygulamasında, bu biçimlendirme uzantısının işlenmesi <xref:System.Windows.StaticResourceExtension> sınıfı tarafından tanımlanır.  
  
 `StaticResource`, biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tüm biçimlendirme uzantıları öznitelik sözdiziminde {ve} karakterlerini kullanır. Bu, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisinin, bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini tanıdığı bir kuraldır. Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Stil ve Şablon Oluşturma](../controls/styling-and-templating.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [XAML Kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Kaynaklar ve Kod](resources-and-code.md)
