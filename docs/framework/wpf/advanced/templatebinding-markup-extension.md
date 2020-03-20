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
ms.openlocfilehash: 8cebbf717f66b072bc84b2068193ff2fe76ea87b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187288"
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
|`propertyName`|<xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>ayarlayıcı sözdiziminde ayarlanan özelliğin.|  
|`sourceProperty`|Şablonlanan türde bulunan başka bir bağımlılık özelliği, <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>onun .<br /><br /> - veya -<br /><br /> Şablonu oluşturulan hedef türünden farklı bir tür tarafından tanımlanan "aşağı noktalanmış" özellik adı. Bu aslında <xref:System.Windows.PropertyPath>bir. Bkz. [PropertyPath XAML Sözdizimi.](propertypath-xaml-syntax.md)|  
  
## <a name="remarks"></a>Açıklamalar  
 A, `TemplateBinding` şablon senaryoları [için](binding-markup-extension.md) bağlayıcılık için en iyi `Binding` duruma `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=OneWay}`getirilmiş bir biçimidir, bu da bir 'ile oluşturulmuşbir . A, `TemplateBinding` özellikler varsayılan olarak iki yönlü bağlamayı gerektirse bile, her zaman tek yönlü bir bağlamadır. İlgili iki özellik de bağımlılık özellikleri olmalıdır. Şablonlu bir üst öğeye iki yönlü bağlama elde etmek `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`için aşağıdaki bağlayıcı ifadeyi kullanın.
  
 [RelativeSource](relativesource-markupextension.md) bazen bir şablon içinde göreceli özellik bağlama `TemplateBinding` gerçekleştirmek için birlikte veya yerine kullanılan başka bir biçimlendirme uzantısıdır.  
  
 Denetim şablonlarını bir kavram olarak tanımlamak burada ele alınmaz; daha fazla bilgi için denetim [stilleri ve Şablonlar'a](../controls/control-styles-and-templates.md)bakın.  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. Tanımlayıcı dizesonra sağlanan `TemplateBinding` dize belirteci alttaki <xref:System.Windows.TemplateBindingExtension.Property%2A> <xref:System.Windows.TemplateBindingExtension> uzantı sınıfının değeri olarak atanır.  
  
 Nesne öğesi sözdizimi mümkündür, ancak gerçekçi uygulamaya sahip olmadığından gösterilmez. `TemplateBinding`ayarlayıcılar içindeki değerleri doldurmak için, değerlendirilen ifadeleri kullanarak ve `TemplateBinding` özellik `<Setter.Property>` öğesi sözdizimini doldurmak için nesne öğesi sözdizimini kullanmak gereksiz yere ayrıntılıdır.  
  
 `TemplateBinding`<xref:System.Windows.TemplateBindingExtension.Property%2A> özelliği özellik=değer çifti olarak belirten ayrıntılı bir öznitelik kullanımında da kullanılabilir:  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır. Yalnızca `TemplateBinding` bir ayarlanabilen özelliği olduğundan, bu ayrıntılı kullanım tipik değildir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemci uygulamasında, bu biçimlendirme uzantısı için işleme <xref:System.Windows.TemplateBindingExtension> sınıf tarafından tanımlanır.  
  
 `TemplateBinding`biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. XAML'deki tüm biçimlendirme `{` uzantıları, bir XAML işlemcinin bir biçimlendirme uzantısıözözelliği ni işlemesi gerektiğini kabul ettiği kural olan öznitelik sözdiziminde karakterleri ve `}` karakterleri kullanır. Daha fazla bilgi için [bkz: Biçimlendirme Uzantıları ve WPF XAML.](markup-extensions-and-wpf-xaml.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [Stil ve Şablon Oluşturma](../controls/styling-and-templating.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [RelativeSource İşaretleme Uzantısı](relativesource-markupextension.md)
- [İşaretleme Uzantısı Bağlama](binding-markup-extension.md)
