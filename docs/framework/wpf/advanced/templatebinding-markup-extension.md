---
title: "TemplateBinding Biçimlendirme Uzantısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TemplateBinding
- TemplateBindingExtension
helpviewer_keywords:
- XAML [WPF], TemplateBinding markup extension
- TemplateBinding markup extensions [WPF]
ms.assetid: 1d25bbfc-dbc2-499d-9f12-419d23d4ac6a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 959cad0d53b12c3093b95b19ff56ed55eec7eb4f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
|`propertyName`|<xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>ayarlayıcı sözdiziminde ayarlanan özelliği.|  
|`sourceProperty`|Belirtilen şablonu, oluşturulan türünde bulunan başka bir bağımlılık özelliği tarafından kendi <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.<br /><br /> - veya -<br /><br /> Şablonu oluşturulan hedef türünden farklı bir tür tarafından tanımlanan "aşağı noktalanmış" özellik adı. Bu gerçekten olan bir <xref:System.Windows.PropertyPath>. Bkz: [PropertyPath XAML sözdizimi](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 A `TemplateBinding` en iyi duruma getirilmiş bir biçimidir bir [bağlama](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) alınmak üzere benzer şablon senaryoları için bir `Binding` ile oluşturulan `{Binding RelativeSource={RelativeSource TemplatedParent}}`. A `TemplateBinding` iki yönlü bağlama için varsayılan özellikler dahil her zaman bir tek yönlü bağlama, olsa dahi. İlgili iki özellik de bağımlılık özellikleri olmalıdır.  
  
 [RelativeSource](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md) bazen yerine veya ile birlikte kullanılan başka bir işaretleme uzantısı `TemplateBinding` şablon içinde göreli özellik bağlamasını gerçekleştirmek için.  
  
 Kavram olarak denetim şablonları açıklayan burada kapsanmayan; Daha fazla bilgi için bkz: [denetim stilleri ve şablonları](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. Sonra sağlanan dize belirteci `TemplateBinding` kimlik dizesi olarak atandığı <xref:System.Windows.TemplateBindingExtension.Property%2A> temel değer <xref:System.Windows.TemplateBindingExtension> uzantısı sınıfı.  
  
 Nesne öğesi sözdizimi mümkündür, ancak gerçekçi uygulamaya sahip olmadığından gösterilmez. `TemplateBinding`kullanarak, ayarlayıcılar içinde değerleri değerlendirilmiş ifadeler doldurmak için kullanılır ve nesne öğesi sözdizimini kullanarak `TemplateBinding` doldurmak için `<Setter.Property>` özellik öğesi sözdizimini gereksiz yere ayrıntılıdır.  
  
 `TemplateBinding`belirten bir ayrıntılı öznitelik kullanımı da kullanılabilir <xref:System.Windows.TemplateBindingExtension.Property%2A> özelliği bir özellik olarak değer çifti =:  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 Ayrıntılı kullanım, genellikle birden fazla ayarlanabilir özelliğe sahip uzantılar için veya bazı özellikler isteğe bağlıysa yararlıdır. Çünkü `TemplateBinding` yalnızca gerekli olan bir ayarlanabilir özelliği, bu ayrıntılı kullanım tipik sahiptir.  
  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemci uygulamasında, bu biçimlendirme uzantısı işlenmesi tarafından tanımlanan <xref:System.Windows.TemplateBindingExtension> sınıfı.  
  
 `TemplateBinding`bir biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. XAML Kullanımdaki tüm biçimlendirme uzantıları `{` ve `}` olarak XAML işlemci tanıdığı biçimlendirme uzantısı öznitelik işlemelidir kuralı kendi öznitelik sözdiziminde karakterler. Daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Style>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [İşaretleme Uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [RelativeSource İşaretleme Uzantısı](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md)  
 [İşaretleme Uzantısı Bağlama](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)
