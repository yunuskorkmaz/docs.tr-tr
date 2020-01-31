---
title: Denetimlerin özellikleri
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: 82bfab15cef4946661a37d2d88fbe1b797f3d816
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741172"
---
# <a name="properties-in-windows-forms-controls"></a>Windows Forms Denetimlerindeki Özellikler
Windows Forms denetim, temel sınıf <xref:System.Windows.Forms.Control?displayProperty=nameWithType>birçok özellik formunu devralır. Bunlar <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>ve diğer birçok özellik içerir. Devralınan özellikler hakkında daha fazla bilgi için bkz. <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
 Denetiminizin devralınan özelliklerini geçersiz kılabilir ve yeni özellikler tanımlayabilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Özellik Tanımlama](defining-a-property-in-windows-forms-controls.md)  
 Özel denetim veya bileşen için bir özelliğin nasıl uygulanacağını gösterir ve özelliğin tasarım ortamıyla nasıl tümleştirileceğini gösterir.  
  
 [ShouldSerialize ile Varsayılan Değerleri Tanımlama ve Yöntemleri Sıfırlama](defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 Özel bir denetim veya bileşen için varsayılan özellik değerlerinin nasıl tanımlanacağını gösterir.  
  
 [Özellik Değişti Olayları](property-changed-events.md)  
 Özellik değeri değiştiğinde özellik değişikliği bildirimlerinin nasıl etkinleştirileceğini açıklar.  
  
 [Nasıl yapılır: Bağlı Denetimlerin Özelliklerini Açma](how-to-expose-properties-of-constituent-controls.md)  
 Özel bir bileşik denetimde bileşen denetimlerinin özelliklerinin nasıl gösterileceğini gösterir.  
  
 [Özel Denetimlerde Yöntem Uygulama](method-implementation-in-custom-controls.md)  
 Özel denetimlerde ve bileşenlerde yöntemlerin nasıl uygulanacağını açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.UserControl>  
 Bileşik denetimlerin uygulanması için temel sınıfı belgeler.  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 Özel özellik türü için kullanılacak <xref:System.ComponentModel.TypeConverter> belirten özniteliği belgeler.  
  
 <xref:System.ComponentModel.EditorAttribute>  
 Özel bir özellik için kullanılacak <xref:System.Drawing.Design.UITypeEditor> belirten özniteliği belgeler.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Windows Forms Denetimlerindeki Öznitelikler](attributes-in-windows-forms-controls.md)  
 Özel denetimlerinizin ve bileşenlerinizin özelliklerine veya diğer üyelerine uygulayabileceğiniz öznitelikleri açıklar.  
  
 [Bileşenler için tasarım zamanı öznitelikleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))  
 Görsel tasarımcılarda tasarım zamanında doğru görüntülenebilmesi için bileşenlere ve denetimlere uygulanacak meta veri özniteliklerini listeler.  
  
 [Tasarım zamanı desteğini genişletme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))  
 Tasarım zamanı desteği sağlayan düzenleyiciler ve tasarımcılar gibi sınıfların nasıl uygulanacağını açıklar.
