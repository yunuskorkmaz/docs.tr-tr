---
title: TemplateBinding Biçimlendirme Uzantısı
ms.date: 03/30/2017
f1_keywords:
- TemplateBinding
- TemplateBindingExtension
helpviewer_keywords:
- XAML [WPF], TemplateBinding markup extension
- TemplateBinding markup extensions [WPF]
ms.assetid: 1d25bbfc-dbc2-499d-9f12-419d23d4ac6a
ms.openlocfilehash: c004560a0b7ab367fbf4fbb48b0e8d8b63f3d8f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59156006"
---
# <a name="templatebinding-markup-extension"></a>TemplateBinding Biçimlendirme Uzantısı
Denetim şablonunda bir özelliğin değerini, şablonlu denetim üzerinde açıkça gösterilen başka bir özelliğin değerine bağlar.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xml  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a>XAML Öznitelik Kullanımı (şablon veya stilde Ayarlayıcı özelliği için)  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`propertyName`|<xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> ayarlayıcı sözdiziminde ayarlanan özelliği.|  
|`sourceProperty`|Tarafından belirtilen şablonu, oluşturulan türde bulunan başka bir bağımlılık özelliği, <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.<br /><br /> - veya -<br /><br /> Şablonu oluşturulan hedef türünden farklı bir tür tarafından tanımlanan "aşağı noktalanmış" özellik adı. Bu, aslında bir <xref:System.Windows.PropertyPath>. Bkz: [PropertyPath XAML söz dizimi](propertypath-xaml-syntax.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 A `TemplateBinding` en iyi duruma getirilmiş formudur bir [bağlama](binding-markup-extension.md) , şablon senaryoları için benzer bir `Binding` ile oluşturulan `{Binding RelativeSource={RelativeSource TemplatedParent}}`. A `TemplateBinding` özellikler iki yönlü bağlamaya varsayılan yapsa bile her zaman bir bağlamadır. İlgili iki özellik de bağımlılık özellikleri olmalıdır. Elde etmek için bir şablonlu üst öğeye iki yönlü bir bağlama kullanın şu bağlama ifadesi `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`. 
  
 [RelativeSource](relativesource-markupextension.md) bazen yerine veya ile birlikte kullanılan başka bir işaretleme uzantısı `TemplateBinding` şablon içinde göreli özellik bağlamasını gerçekleştirmek için.  
  
 Kavram olarak denetim şablonları açıklayan burada kapsanmıyor; Daha fazla bilgi için [denetim stilleri ve şablonları](../controls/control-styles-and-templates.md).  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. Sonra sağlanan dize belirteci `TemplateBinding` tanımlayıcı dizesi olarak atandığı <xref:System.Windows.TemplateBindingExtension.Property%2A> temel değer <xref:System.Windows.TemplateBindingExtension> uzantısı sınıfı.  
  
 Nesne öğesi sözdizimi mümkündür, ancak gerçekçi uygulamaya sahip olmadığından gösterilmez. `TemplateBinding` kullanarak, ayarlayıcılar içinde değerleri değerlendirilmiş ifadeler doldurmak için kullanılır ve nesne öğesi sözdizimi `TemplateBinding` doldurmak için `<Setter.Property>` özellik öğesi sözdizimine gereksiz yere ayrıntılıdır.  
  
 `TemplateBinding` belirten ayrıntılı öznitelik kullanımında da ayrıca kullanılabilir <xref:System.Windows.TemplateBindingExtension.Property%2A> bir özellik olarak özellik değer eşleştirmesi:  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır. Çünkü `TemplateBinding` yalnızca gerekli olan bir ayarlanabilir özelliği, bu ayrıntılı kullanım tipik değildir.  
  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemci uygulamasında, bu işaretleme uzantısının işlenmesi tarafından tanımlanır <xref:System.Windows.TemplateBindingExtension> sınıfı.  
  
 `TemplateBinding` bir işaretleme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. XAML kullanım içindeki tüm biçimlendirme uzantıları `{` ve `}` karakter olarak bir XAML işlemcisinin bir işaretleme uzantısı özniteliği işlenmesi gerektiğini, kuralına göre kendi öznitelik sözdizimi. Daha fazla bilgi için [biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [Stil ve Şablon Oluşturma](../controls/styling-and-templating.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [RelativeSource İşaretleme Uzantısı](relativesource-markupextension.md)
- [İşaretleme Uzantısı Bağlama](binding-markup-extension.md)
