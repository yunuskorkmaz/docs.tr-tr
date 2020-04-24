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
ms.openlocfilehash: 5c0bb247bae525658d89d53f1672e57b87aba7bc
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646206"
---
# <a name="staticresource-markup-extension"></a>StaticResource Biçimlendirme Uzantısı
Zaten tanımlanmış bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kaynağa başvuruda bulunarak herhangi bir özellik özniteliği için bir değer sağlar. Bu kaynağın arama davranışı, daha önce geçerli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfanın biçimlendirmesinden yüklenen kaynakları ve diğer uygulama kaynaklarını arayacak ve bu kaynak değerini çalışma zamanı nesnelerindeki özellik değeri olarak oluşturacak yükleme zamanı aramaya benzer.  
  
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
|`key`|İstenen kaynağın anahtarı. Bu anahtar başlangıçta [x:Key Yönergesi](../../../desktop-wpf/xaml-services/xkey-directive.md) tarafından bir kaynak biçimlendirme de `key` oluşturulduysa <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> veya kaynak kod olarak oluşturulduysa parametre olarak sağlanmışsa atanmıştır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] A, `StaticResource` dosya içinde sözlü olarak tanımlanan bir kaynağa ileri başvuru yapmaya çalışmamalıdır. Bunu yapmaya çalışmak desteklenmez ve böyle bir başvuru başarısız olmasa bile, ileri başvuruyu denemek, bir <xref:System.Windows.ResourceDictionary> başvuruyu temsil eden iç karma tablolar arandığında bir yükleme süresi performans cezasına neden olur. En iyi sonuçlar için, kaynak sözlüklerinizin kompozisyonunu, ileriye dönük başvuruların önlenebileceği şekilde ayarlayın. İleri ye dönük bir başvurudan kaçınamıyorsanız, bunun yerine [DynamicResource Biçimlendirme Uzantısı'nı](dynamicresource-markup-extension.md) kullanın.  
  
 Belirtilen, <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> sayfanızda, uygulamanızda, kullanılabilir denetim temalarında ve dış kaynaklarda veya sistem kaynaklarında bir [düzeyde x:Key Yönergesi](../../../desktop-wpf/xaml-services/xkey-directive.md) ile tanımlanan varolan bir kaynağa karşılık gelmelidir. Kaynak araması bu sırada gerçekleşir. Statik ve dinamik kaynaklar için kaynak arama davranışı hakkında daha fazla bilgi için [Bkz. XAML Kaynakları.](../../../desktop-wpf/fundamentals/xaml-resources-define.md)  
  
 Kaynak anahtarı [XamlName Grammar'da](../../../desktop-wpf/xaml-services/xamlname-grammar.md)tanımlanan herhangi bir dize olabilir. Kaynak anahtarı, <xref:System.Type>başka nesne türleri de olabilir. Anahtar, <xref:System.Type> denetimlerin örtülü bir stil anahtarı aracılığıyla temalar tarafından nasıl biçimlandırılabildiğini temel denedir. Daha fazla bilgi için [bkz.](../controls/control-authoring-overview.md)  
  
 Bir kaynağa başvurmanın alternatif bildirimsel yolu [Dinamik Kaynak Biçimlendirme Uzantısı](dynamicresource-markup-extension.md)olarakdır.  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. Tanımlayıcı dizesonra sağlanan `StaticResource` dize belirteci alttaki <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> <xref:System.Windows.StaticResourceExtension> uzantı sınıfının değeri olarak atanır.  
  
 `StaticResource`nesne öğesi sözdiziminde kullanılabilir. Bu durumda, <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> özelliğin değerini belirterek gereklidir.  
  
 `StaticResource`<xref:System.Windows.StaticResourceExtension.ResourceKey%2A> özelliği özellik=değer çifti olarak belirten ayrıntılı bir öznitelik kullanımında da kullanılabilir:  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır. Yalnızca `StaticResource` bir ayarlanabilen özelliği olduğundan, bu ayrıntılı kullanım tipik değildir.  
  
 İşlemci uygulamasında, bu biçimlendirme uzantısı için işleme <xref:System.Windows.StaticResourceExtension> sınıf tarafından tanımlanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `StaticResource`biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. Öznitelik sözdiziminde { ve } karakterlerini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanan tüm biçimlendirme uzantıları, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini kabul ettiği kuraldır. Daha fazla bilgi için [bkz: Biçimlendirme Uzantıları ve WPF XAML.](markup-extensions-and-wpf-xaml.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Biçimlendirme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [XAML Kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Kaynaklar ve Kod](resources-and-code.md)
