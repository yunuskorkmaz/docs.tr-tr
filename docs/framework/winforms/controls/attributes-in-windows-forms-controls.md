---
title: "Windows Forms Denetimlerindeki Öznitelikler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [Windows Forms]
- attributes [Windows Forms], data binding properties
- attributes [Windows Forms], control properties
- attributes [Windows Forms], classes
ms.assetid: 2c5640e9-6c6c-49d7-a5e4-a768f6be7853
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13aad22dca249147e3037bcef6da755c264021db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="attributes-in-windows-forms-controls"></a>Windows Forms Denetimlerindeki Öznitelikler
.NET Framework öznitelikleri özel denetimleri ve bileşenleri üyelerine uygulayabilirsiniz çeşitli sağlar. Bazı bu öznitelikler bir sınıfın çalışma zamanı davranışını etkilemek ve diğer tasarım zamanı davranışını etkiler.  
  
## <a name="attributes-for-control-and-component-properties"></a>Denetim ve bileşen özellikleri için öznitelikler  
 Aşağıdaki tabloda, özellikleri veya diğer özel denetimleri ve bileşenleri üyeleri uygulayabilirsiniz öznitelikleri gösterir. Bu öznitelikler çoğunu kullanan bir örnek için bkz: [nasıl yapılır: Windows Forms denetimlerindeki öznitelikler uygulamak](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|Bir özellik değerini başka bir kaynaktan alınacağı özellik neden geçirilecek değeri belirtir. Bu olarak bilinir *çevre*.|  
|<xref:System.ComponentModel.BrowsableAttribute>|Bir özellik veya olay içinde görüntülenmesi gerekip gerekmediğini belirten bir **özellikleri** penceresi.|  
|<xref:System.ComponentModel.CategoryAttribute>|Grup özelliği veya görüntülenen olay kategorisi adını belirtir. bir <xref:System.Windows.Forms.PropertyGrid> denetim kümesine <xref:System.Windows.Forms.PropertySort.Categorized> modu.|  
|<xref:System.ComponentModel.DefaultValueAttribute>|Bir özellik için varsayılan değer belirtir.|  
|<xref:System.ComponentModel.DescriptionAttribute>|Bir özellik veya olay için bir açıklama belirtir.|  
|<xref:System.ComponentModel.DisplayNameAttribute>|Bir özellik için görünen ad belirtir, olayı veya `public``void` bağımsız değişken almayan yöntemi.|  
|<xref:System.ComponentModel.EditorAttribute>|Bir özelliği değiştirmek için kullanılacak Düzenleyicisi'ni belirtir.|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|Bir özellik veya yöntem bir düzenleyicide görüntülenebilir olduğunu belirtir.|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|Bir sınıf veya üye bağlam anahtar sözcüğü belirtir.|  
|<xref:System.ComponentModel.LocalizableAttribute>|Bir özellik yerelleştirilmiş olup olmadığını belirtir.|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|Bir nesnenin metin gösterimi yıldızlar gibi karakterler tarafından getirilmemeli olduğunu gösterir.|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|Bu öznitelik bağlı özelliği salt okunur veya okuma/yazma tasarım zamanında olup olmadığını belirtir.|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|İlişkili özelliğin değeri değiştiğinde özellik Kılavuzu yenilemelisiniz gösterir.|  
|<xref:System.ComponentModel.TypeConverterAttribute>|Bu öznitelik nesne için bir dönüştürücü kullanılacak türüne bağlı belirtir.|  
  
## <a name="attributes-for-data-binding-properties"></a>Veri bağlama özellikleri için öznitelikler  
 Aşağıdaki tabloda özel denetimleri ve bileşenleri veri bağlama ile nasıl etkileşim belirtmek için uygulayabileceğiniz öznitelikleri gösterir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|<xref:System.ComponentModel.BindableAttribute>|Bir özelliği için bağlama genellikle kullanılıp kullanılmayacağını belirtir.|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Bir bileşenin veri üye özellikleri ve veri kaynağını belirtir.|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Bir bileşenin varsayılan bağlama özelliği belirtir.|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Bir bileşenin veri üye özellikleri ve veri kaynağını belirtir.|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|Yeniden yönlendirme etkinleştirir öznitelik.|  
  
## <a name="attributes-for-classes"></a>Sınıfları için öznitelikler  
 Aşağıdaki tabloda tasarım zamanında özel denetimleri ve bileşenleri davranışını belirtmek için uygulayabileceğiniz öznitelikleri gösterir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|Bir bileşen için varsayılan olayı belirtir.|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|Bir bileşen için varsayılan özellik belirtir.|  
|<xref:System.ComponentModel.DesignerAttribute>|Tasarım zamanı hizmetleri bileşeni için uygulamak için kullanılan sınıfı belirtir.|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|Tasarımcı bir sınıf için belirli bir kategoriye ait olduğunu belirtir.|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|Araç kutusu öğesi bir özniteliği temsil eder.|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|Araç kutusu öğesi için kullanmak üzere filtre türü ve filtre dizesini belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Attribute>  
 [Nasıl yapılır: Windows Forms Denetiminde Öznitelikleri Uygulama](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)  
 [Tasarım zamanı desteği genişletme](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
