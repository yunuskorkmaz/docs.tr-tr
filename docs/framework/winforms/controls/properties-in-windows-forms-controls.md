---
title: Windows Forms Denetimlerindeki Özellikler
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: aa7d8be158f4e0a7b2b95bf02cb0d1e173041f59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="properties-in-windows-forms-controls"></a>Windows Forms Denetimlerindeki Özellikler
Bir Windows Forms denetimi birçok özellikler form temel sınıfı devralır <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Bunlar gibi özellikler içeren <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>ve diğer birçok. Devralınan özellikler hakkında daha fazla ayrıntı için bkz: <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
 , Denetiminde devralınan özelliklerini geçersiz kılmak yanı sıra yeni özellikleri tanımlayın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Özellik Tanımlama](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 Özellik tasarım ortamına tümleştirme nasıl gösterir ve özel denetimi veya bileşeni için bir özellik uygulamak gösterir.  
  
 [ShouldSerialize ile Varsayılan Değerleri Tanımlama ve Yöntemleri Sıfırlama](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 Özel denetimi veya bileşeni için varsayılan özellik değerlerini tanımlayabileceğiniz gösterilmektedir.  
  
 [Özellik Değişti Olayları](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 Özellik değişikliği bildirimlerini özellik değeri değiştiğinde etkinleştirmeyi açıklar.  
  
 [Nasıl yapılır: Bağlı Denetimlerin Özelliklerini Açma](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)  
 Özel bir bileşik denetim bağlı denetimlerin özelliklerini ortaya gösterilmektedir.  
  
 [Özel Denetimlerde Yöntem Uygulama](../../../../docs/framework/winforms/controls/method-implementation-in-custom-controls.md)  
 Özel denetimler ve bileşenler yöntemleri uygulamak açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.UserControl>  
 Bileşik denetimler uygulamak için temel sınıf belgeler.  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 Belirten özniteliği belgeleri <xref:System.ComponentModel.TypeConverter> bir özel özellik türü için kullanılacak.  
  
 <xref:System.ComponentModel.EditorAttribute>  
 Belirten özniteliği belgeleri <xref:System.Drawing.Design.UITypeEditor> bir özel özellik için kullanılacak.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Windows Forms Denetimlerindeki Öznitelikler](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 Özellikleri veya diğer özel denetimleri ve bileşenleri üyeleri uygulayabilirsiniz öznitelikleri açıklanmaktadır.  
  
 [Bileşenleri için tasarım zamanı öznitelikleri](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 Böylece doğru görsel tasarımcılar tasarım zamanında görüntülendikleri bileşenleri ve denetimler uygulamak için meta veri öznitelikleri listeler.  
  
 [Tasarım zamanı desteği genişletme](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 Sınıfları düzenleyicileri ve tasarım zamanı desteği tasarımcıları gibi uygulamak açıklar.
