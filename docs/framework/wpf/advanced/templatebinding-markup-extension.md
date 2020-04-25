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
ms.openlocfilehash: 69698db8b51e3872d5941d4fba67271b1e61226e
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140454"
---
# <a name="templatebinding-markup-extension"></a>TemplateBinding Biçimlendirme Uzantısı
Denetim şablonunda bir özelliğin değerini, şablonlu denetim üzerinde açıkça gösterilen başka bir özelliğin değerine bağlar.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xml  
<object property="{TemplateBinding sourceProperty}" ... />
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a>XAML Öznitelik Kullanımı (şablon veya stilde Ayarlayıcı özelliği için)  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" ... />  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`propertyName`|<xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>ayarlayıcı sözdiziminde ayarlanan özelliğin.|  
|`sourceProperty`|Şablonlu tür üzerinde bulunan ve tarafından belirtilen başka bir bağımlılık özelliği <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.<br /><br /> - veya -<br /><br /> Şablonu oluşturulan hedef türünden farklı bir tür tarafından tanımlanan "aşağı noktalanmış" özellik adı. Bu aslında bir <xref:System.Windows.PropertyPath>' dır. Bkz. [PROPERTYPATH XAML sözdizimi](propertypath-xaml-syntax.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 , İle `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=OneWay}`oluşturulmuş bir `Binding` şablon senaryosu için bir [bağlama](binding-markup-extension.md) için iyileştirilmiş bir formdur. `TemplateBinding` Özellikler `TemplateBinding` iki yönlü bağlamaya varsayılan olarak dahil olsa bile, her zaman tek yönlü bir bağlamadır. İlgili iki özellik de bağımlılık özellikleri olmalıdır. Şablonlu bir üst öğeye iki yönlü bağlama ulaşmak için bunun yerine `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`aşağıdaki bağlama ifadesini kullanın.
  
 [RelativeSource](relativesource-markupextension.md) , bazen bir şablon içinde göreli Özellik bağlamayı gerçekleştirmek için veya yerine `TemplateBinding` ile birlikte kullanılan başka bir biçimlendirme uzantısıdır.  
  
 Bir kavram olarak denetim şablonlarının açıklaması burada ele alınmıyor; daha fazla bilgi için bkz. [denetim stilleri ve şablonları](../controls/control-styles-and-templates.md).  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. `TemplateBinding` Tanımlayıcı dizeden sonra belirtilen dize belirteci, temel <xref:System.Windows.TemplateBindingExtension.Property%2A> <xref:System.Windows.TemplateBindingExtension> uzantı sınıfının değeri olarak atanır.  
  
 Nesne öğesi sözdizimi mümkündür, ancak gerçekçi uygulamaya sahip olmadığından gösterilmez. `TemplateBinding`, değerlendirilmiş ifadeleri kullanarak, ayarlayıcıları içindeki değerleri doldurmek için kullanılır ve özellik öğesi söz dizimini `TemplateBinding` dolduracak `<Setter.Property>` şekilde nesne öğesi sözdizimini kullanmak gereksiz şekilde ayrıntılıdır.  
  
 `TemplateBinding`, <xref:System.Windows.TemplateBindingExtension.Property%2A> özelliği özellik = değer çifti olarak belirten ayrıntılı bir öznitelik kullanımında de kullanılabilir:  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" ... />
```  
  
 Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır. , `TemplateBinding` Gereken tek bir ayarlanabilir özelliğe sahip olduğundan, bu ayrıntılı kullanım tipik değildir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Xaml işlemci uygulamasında, bu biçimlendirme uzantısının işlenmesi <xref:System.Windows.TemplateBindingExtension> sınıfı tarafından tanımlanır.  
  
 `TemplateBinding`bir biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. XAML 'deki tüm biçimlendirme uzantıları, `{` öznitelik sözdiziminde `}` ve karakterlerini KULLANıR. Bu, XAML işlemcisinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini tanıdığı kuraldır. Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Biçimlendirme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [RelativeSource MarkupExtension](relativesource-markupextension.md)
- [Biçimlendirme Uzantısı Bağlama](binding-markup-extension.md)
