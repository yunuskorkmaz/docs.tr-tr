---
title: Denetimlerde öznitelikler
ms.date: 03/30/2017
helpviewer_keywords:
- attributes [Windows Forms]
- attributes [Windows Forms], data binding properties
- attributes [Windows Forms], control properties
- attributes [Windows Forms], classes
ms.assetid: 2c5640e9-6c6c-49d7-a5e4-a768f6be7853
ms.openlocfilehash: b32e4f87e953438a3bb11569445a9270e11c7922
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732130"
---
# <a name="attributes-in-windows-forms-controls"></a>Windows Forms Denetimlerindeki Öznitelikler
.NET Framework, özel denetimlerinizin ve bileşenlerinizin üyelerine uygulayabileceğiniz çeşitli öznitelikler sağlar. Bu özniteliklerin bazıları, bir sınıfın çalışma zamanı davranışını etkiler ve diğerleri tasarım zamanı davranışını etkiler.  
  
## <a name="attributes-for-control-and-component-properties"></a>Denetim ve bileşen özellikleri için öznitelikler  
 Aşağıdaki tabloda, özel denetimlerinizin ve bileşenlerinizin özelliklerine veya diğer üyelerine uygulayabileceğiniz öznitelikler gösterilmektedir. Bu özniteliklerin birçoğunu kullanan bir örnek için bkz. [nasıl yapılır: öznitelikleri uygulama Windows Forms denetimleri](how-to-apply-attributes-in-windows-forms-controls.md).  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|Özelliğin değerini başka bir kaynaktan almasını sağlamak için bir özelliğe geçirilecek değeri belirtir. Bu, *Ambience*olarak bilinir.|  
|<xref:System.ComponentModel.BrowsableAttribute>|Bir özellik veya olayın bir **Özellikler** penceresinde görüntülenip görüntülenmeyeceğini belirtir.|  
|<xref:System.ComponentModel.CategoryAttribute>|<xref:System.Windows.Forms.PropertyGrid> denetim <xref:System.Windows.Forms.PropertySort.Categorized> moduna ayarlanmış şekilde görüntülendiğinde özelliğin veya olayın gruplandıralınacağı kategorinin adını belirtir.|  
|<xref:System.ComponentModel.DefaultValueAttribute>|Bir özellik için varsayılan değeri belirtir.|  
|<xref:System.ComponentModel.DescriptionAttribute>|Bir özellik veya olay için bir açıklama belirtir.|  
|<xref:System.ComponentModel.DisplayNameAttribute>|Bağımsız değişken içermeyen bir özellik, olay veya `public void` yöntemi için görünen adı belirtir.|  
|<xref:System.ComponentModel.EditorAttribute>|Bir özelliği değiştirmek için kullanılacak düzenleyiciyi belirtir.|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|Bir özellik veya yöntemin düzenleyicide görüntülenebilir olduğunu belirtir.|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|Bir sınıf veya üyenin bağlam anahtar sözcüğünü belirtir.|  
|<xref:System.ComponentModel.LocalizableAttribute>|Bir özelliğin yerelleştirilmesi gerekip gerekmediğini belirtir.|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|Bir nesnenin metin gösteriminin yıldız gibi karakterlerle gizlendiğini gösterir.|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|Bu özniteliğin bağlantılı özelliğinin, tasarım zamanında salt okunurdur veya okuma/yazma özelliği olup olmadığını belirtir.|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|İlişkili özellik değeri değiştiğinde özellik kılavuzunun yenilenmesi gerektiğini gösterir.|  
|<xref:System.ComponentModel.TypeConverterAttribute>|Bu özniteliğin bağlandığı nesne için dönüştürücü olarak kullanılacak türü belirtir.|  
  
## <a name="attributes-for-data-binding-properties"></a>Veri bağlama özellikleri için öznitelikler  
 Aşağıdaki tabloda, özel denetimlerinizin ve bileşenlerinizin veri bağlama ile nasıl etkileşime gireceğini belirtmek için uygulayabileceğiniz öznitelikler gösterilmektedir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|<xref:System.ComponentModel.BindableAttribute>|Bir özelliğin genellikle bağlama için kullanılıp kullanılmayacağını belirtir.|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Bir bileşenin veri kaynağı ve veri üyesi özelliklerini belirtir.|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Bir bileşen için varsayılan bağlama özelliğini belirtir.|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Bir bileşenin veri kaynağı ve veri üyesi özelliklerini belirtir.|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|Öznitelik yeniden yönlendirmeyi mümkün.|  
  
## <a name="attributes-for-classes"></a>Sınıfların öznitelikleri  
 Aşağıdaki tabloda, tasarım zamanında özel denetimlerinizin ve bileşenlerinizin davranışını belirtmek için uygulayabileceğiniz öznitelikler gösterilmektedir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|Bir bileşen için varsayılan olayı belirtir.|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|Bir bileşen için varsayılan özelliği belirtir.|  
|<xref:System.ComponentModel.DesignerAttribute>|Bir bileşene ait tasarım zamanı hizmetlerini uygulamak için kullanılan sınıfı belirtir.|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|Bir sınıfın tasarımcısının belirli bir kategoriye ait olduğunu belirtir.|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|Bir araç kutusu öğesinin özniteliğini temsil eder.|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|Bir araç kutusu öğesi için kullanılacak filtre dizesini ve filtre türünü belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Attribute>
- [Nasıl yapılır: Windows Forms Denetiminde Öznitelikleri Uygulama](how-to-apply-attributes-in-windows-forms-controls.md)
- [Tasarım zamanı desteğini genişletme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](developing-custom-windows-forms-controls.md)
