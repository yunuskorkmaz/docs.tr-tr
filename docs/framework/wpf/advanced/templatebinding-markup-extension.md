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
ms.openlocfilehash: 399e4ac223d2fcb728ece2c92d25a087990992f2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458663"
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
|`propertyName`|ayarlayıcı sözdiziminde ayarlanan özelliğin <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.|  
|`sourceProperty`|Şablonlu tür üzerinde bulunan ve <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>tarafından belirtilen başka bir bağımlılık özelliği.<br /><br /> veya<br /><br /> Şablonu oluşturulan hedef türünden farklı bir tür tarafından tanımlanan "aşağı noktalanmış" özellik adı. Bu aslında bir <xref:System.Windows.PropertyPath>. Bkz. [PROPERTYPATH XAML sözdizimi](propertypath-xaml-syntax.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 `TemplateBinding`, `{Binding RelativeSource={RelativeSource TemplatedParent}}`ile oluşturulmuş bir `Binding` benzer şablon senaryoları için en iyileştirilmiş bir [bağlama](binding-markup-extension.md) biçimidir. Bir `TemplateBinding` her zaman tek yönlü bir bağlamadır ve özellikler varsayılan olarak iki yönlü bağlamaya dahil olur. İlgili iki özellik de bağımlılık özellikleri olmalıdır. Şablonlu bir üst öğeye iki yönlü bağlama ulaşmak için `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`yerine aşağıdaki bağlama ifadesini kullanın. 
  
 [RelativeSource](relativesource-markupextension.md) , bir şablon içinde göreli Özellik bağlamayı gerçekleştirmek için bazen `TemplateBinding` veya yerine ile birlikte kullanılan başka bir işaretleme uzantısıdır.  
  
 Bir kavram olarak denetim şablonlarının açıklaması burada ele alınmıyor; daha fazla bilgi için bkz. [denetim stilleri ve şablonları](../controls/control-styles-and-templates.md).  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. `TemplateBinding` tanımlayıcı dizeden sonra belirtilen dize belirteci, temel <xref:System.Windows.TemplateBindingExtension> uzantı sınıfının <xref:System.Windows.TemplateBindingExtension.Property%2A> değeri olarak atanır.  
  
 Nesne öğesi sözdizimi mümkündür, ancak gerçekçi uygulamaya sahip olmadığından gösterilmez. `TemplateBinding`, değerlendirilmiş ifadeler kullanılarak ayarlayıcıdaki değerleri ve `TemplateBinding` için nesne öğesi söz dizimini `<Setter.Property>` Özellik öğesi söz dizimini kullanarak doldurmanız için kullanılır.  
  
 `TemplateBinding`, özellik = değer çifti olarak <xref:System.Windows.TemplateBindingExtension.Property%2A> özelliğini belirten ayrıntılı bir öznitelik kullanımında de kullanılabilir:  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır. `TemplateBinding`, gereken tek bir ayarlanabilir özelliğe sahip olduğundan, bu ayrıntılı kullanım tipik değildir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemci uygulamasında, bu biçimlendirme uzantısının işlenmesi <xref:System.Windows.TemplateBindingExtension> sınıfı tarafından tanımlanır.  
  
 `TemplateBinding`, biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. XAML 'deki tüm biçimlendirme uzantıları, `{` ve `}` karakterlerini öznitelik sözdiziminde kullanır. Bu, XAML işlemcisinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini tanıdığı bir kuraldır. Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [Stil ve Şablon Oluşturma](../controls/styling-and-templating.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [RelativeSource İşaretleme Uzantısı](relativesource-markupextension.md)
- [İşaretleme Uzantısı Bağlama](binding-markup-extension.md)
