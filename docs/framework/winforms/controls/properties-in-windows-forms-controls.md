---
title: Windows Forms Denetimlerindeki Özellikler
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: e531b80cffabb94d2589383936a425b740c9cc07
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708918"
---
# <a name="properties-in-windows-forms-controls"></a>Windows Forms Denetimlerindeki Özellikler
Bir Windows Forms denetimi birçok özellikleri formu temel sınıf devralan <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Bu gibi özellikleri içeren <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>ve diğer birçok. Devralınan özellikler hakkında daha fazla ayrıntı için bkz: <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
 Devralınan özellikler geçersiz kılma denetiminizi yapabilir yeni özelliklerini tanımlayın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Özellik Tanımlama](defining-a-property-in-windows-forms-controls.md)  
 Bir özelliği bir özel denetim veya bileşen için uygulama işlemini gösterir ve tasarım ortamına özelliği tümleştirme işlemi açıklanır.  
  
 [ShouldSerialize ile Varsayılan Değerleri Tanımlama ve Yöntemleri Sıfırlama](defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 Özel denetim veya bileşen için varsayılan özellik değerlerini tanımlayabileceğiniz gösterilmektedir.  
  
 [Özellik Değişti Olayları](property-changed-events.md)  
 Özellik değişikliği bildirimleri bir özellik değeri değiştiğinde etkinleştirmeyi açıklar.  
  
 [Nasıl yapılır: Bağlı denetimlerin özelliklerini kullanıma sunma](how-to-expose-properties-of-constituent-controls.md)  
 Bağlı denetimlerin özelliklerini özel bileşik denetim olarak kullanıma sunma işlemi gösterilmektedir.  
  
 [Özel Denetimlerde Yöntem Uygulama](method-implementation-in-custom-controls.md)  
 Özel denetimleri ve bileşenleri yöntemleri uygulamak açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.UserControl>  
 Bileşik denetimler uygulamak için temel sınıf belgeler.  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 Belirten özniteliği belgeleri <xref:System.ComponentModel.TypeConverter> bir özel özellik türü için kullanılacak.  
  
 <xref:System.ComponentModel.EditorAttribute>  
 Belirten özniteliği belgeleri <xref:System.Drawing.Design.UITypeEditor> özel bir özellik için kullanılacak.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Windows Forms Denetimlerindeki Öznitelikler](attributes-in-windows-forms-controls.md)  
 Özellikleri veya diğer üyeleri özel denetimler ve bileşenlerinizi uygulayabilirsiniz öznitelikleri açıklanmaktadır.  
  
 [Bileşenler için tasarım zamanı öznitelikleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))  
 Böylece bunlar görsel tasarımcılar, tasarım zamanında doğru bir şekilde görüntülenir, bileşenleri ve denetimleri uygulamak için meta veri öznitelikleri listeler.  
  
 [Tasarım zamanı desteği sunma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))  
 Sınıflar gibi düzenleyiciler ve tasarımcılar, tasarım zamanı desteği sağlayan uygulama açıklar.
