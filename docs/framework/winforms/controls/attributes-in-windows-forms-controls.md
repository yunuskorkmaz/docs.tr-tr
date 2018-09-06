---
title: Windows Forms Denetimlerindeki Öznitelikler
ms.date: 03/30/2017
helpviewer_keywords:
- attributes [Windows Forms]
- attributes [Windows Forms], data binding properties
- attributes [Windows Forms], control properties
- attributes [Windows Forms], classes
ms.assetid: 2c5640e9-6c6c-49d7-a5e4-a768f6be7853
ms.openlocfilehash: 5bb7a28e314d6c0b007c1579f371a26d0a714fce
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785397"
---
# <a name="attributes-in-windows-forms-controls"></a>Windows Forms Denetimlerindeki Öznitelikler
.NET Framework özel denetimleri ve bileşenleri üyelerine uygulayabilirsiniz özniteliklerin çeşitli sağlar. Bazı bu öznitelikler bir sınıfın çalışma zamanı davranışını etkiler ve diğer tasarım zamanı davranışını etkiler.  
  
## <a name="attributes-for-control-and-component-properties"></a>Denetim ve bileşen özellikleri için öznitelikler  
 Aşağıdaki tablo, özellikler veya diğer üyeleri özel denetimler ve bileşenlerinizi uygulayabilirsiniz öznitelikleri gösterir. Bu özniteliklerin çoğu kullanan bir örnek için bkz: [nasıl yapılır: Windows Forms denetiminde öznitelikleri uygulama](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|Bir özellik değeri başka bir kaynaktan almak özellik neden geçirmek için bir değer belirtir. Bu olarak bilinir *çevre*.|  
|<xref:System.ComponentModel.BrowsableAttribute>|Bir özellik veya olay içinde görüntülenmesi gerekip gerekmediğini belirten bir **özellikleri** penceresi.|  
|<xref:System.ComponentModel.CategoryAttribute>|Özellik veya olay görüntülenen grubuna kategorisinin adını belirtir bir <xref:System.Windows.Forms.PropertyGrid> denetim kümesine <xref:System.Windows.Forms.PropertySort.Categorized> modu.|  
|<xref:System.ComponentModel.DefaultValueAttribute>|Bir özellik için varsayılan değeri belirtir.|  
|<xref:System.ComponentModel.DescriptionAttribute>|Bir özellik veya olay için bir açıklama belirtir.|  
|<xref:System.ComponentModel.DisplayNameAttribute>|Bir özellik için görünen adları belirtir, olay veya `public void` hiçbir bağımsız değişken alan yöntemi.|  
|<xref:System.ComponentModel.EditorAttribute>|Bir özelliği değiştirmek için kullanmak için düzenleyiciyi belirtir.|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|Bir özellik veya yöntem bir düzenleyicide görüntülenebilir olduğunu belirtir.|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|Bağlam anahtar sözcüğü bir sınıf veya üye belirtir.|  
|<xref:System.ComponentModel.LocalizableAttribute>|Bir özellik yerelleştirilmiş olup olmadığını belirtir.|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|Bir nesnenin metin temsili olarak yıldız işareti gibi karakterler engellenmesidir gösterir.|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|Bu öznitelik için bağlı olduğu özelliğin salt okunur veya okuma/yazma tasarım zamanında olup olmadığını belirtir.|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|İlişkili özelliğin değeri değiştiğinde özellik kılavuzunda yenilemelisiniz gösterir.|  
|<xref:System.ComponentModel.TypeConverterAttribute>|Bağlı bir dönüştürücü nesnesi için bu öznitelik kullanmak için ne tür belirtir.|  
  
## <a name="attributes-for-data-binding-properties"></a>Veri bağlama özellikleri için öznitelikler  
 Aşağıdaki tabloda, özel denetimleri ve bileşenleri veri bağlama ile nasıl etkileşime belirtmek için uygulayabileceğiniz öznitelikleri gösterir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|<xref:System.ComponentModel.BindableAttribute>|Bir özelliği için bağlama genellikle kullanılıp kullanılmayacağını belirtir.|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Bir bileşenin veri üyesi özellikleri ve veri kaynağını belirtir.|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Bir bileşen için varsayılan bağlama özelliği belirtir.|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Bir bileşenin veri üyesi özellikleri ve veri kaynağını belirtir.|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|Yeniden yönlendirme etkinleştirir özniteliği.|  
  
## <a name="attributes-for-classes"></a>Öznitelikleri için sınıflar  
 Aşağıdaki tabloda, tasarım zamanında özel denetimleri ve bileşenleri davranışını belirtmek için uygulayabileceğiniz öznitelikleri gösterir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|Bir bileşen için varsayılan olayı belirtir.|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|Bir bileşen için varsayılan alan özelliği belirtir.|  
|<xref:System.ComponentModel.DesignerAttribute>|Bir bileşen için tasarım zamanı Hizmetleri uygulamak için kullanılan sınıfı belirtir.|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|Bir sınıfı için tasarımcı, belirli bir kategoriye ait olduğunu belirtir.|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|Araç kutusu öğesi bir özniteliği temsil eder.|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|Araç kutusu öğesi için kullanılacak filtre türü ve filtre dizesi belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Attribute>  
 [Nasıl yapılır: Windows Forms Denetiminde Öznitelikleri Uygulama](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)  
 [Tasarım zamanı desteği sunma](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
