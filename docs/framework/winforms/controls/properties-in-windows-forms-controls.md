---
title: Windows Forms Denetimlerindeki Özellikler
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: 37db3f16a17acc7f3a6e594bd284ba368801e70a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47192277"
---
# <a name="properties-in-windows-forms-controls"></a>Windows Forms Denetimlerindeki Özellikler
Bir Windows Forms denetimi birçok özellikleri formu temel sınıf devralan <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Bu gibi özellikleri içeren <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>ve diğer birçok. Devralınan özellikler hakkında daha fazla ayrıntı için bkz: <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
 Devralınan özellikler geçersiz kılma denetiminizi yapabilir yeni özelliklerini tanımlayın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Özellik Tanımlama](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 Bir özelliği bir özel denetim veya bileşen için uygulama işlemini gösterir ve tasarım ortamına özelliği tümleştirme işlemi açıklanır.  
  
 [ShouldSerialize ile Varsayılan Değerleri Tanımlama ve Yöntemleri Sıfırlama](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 Özel denetim veya bileşen için varsayılan özellik değerlerini tanımlayabileceğiniz gösterilmektedir.  
  
 [Özellik Değişti Olayları](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 Özellik değişikliği bildirimleri bir özellik değeri değiştiğinde etkinleştirmeyi açıklar.  
  
 [Nasıl yapılır: Bağlı Denetimlerin Özelliklerini Açma](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)  
 Bağlı denetimlerin özelliklerini özel bileşik denetim olarak kullanıma sunma işlemi gösterilmektedir.  
  
 [Özel Denetimlerde Yöntem Uygulama](../../../../docs/framework/winforms/controls/method-implementation-in-custom-controls.md)  
 Özel denetimleri ve bileşenleri yöntemleri uygulamak açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.UserControl>  
 Bileşik denetimler uygulamak için temel sınıf belgeler.  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 Belirten özniteliği belgeleri <xref:System.ComponentModel.TypeConverter> bir özel özellik türü için kullanılacak.  
  
 <xref:System.ComponentModel.EditorAttribute>  
 Belirten özniteliği belgeleri <xref:System.Drawing.Design.UITypeEditor> özel bir özellik için kullanılacak.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Windows Forms Denetimlerindeki Öznitelikler](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 Özellikleri veya diğer üyeleri özel denetimler ve bileşenlerinizi uygulayabilirsiniz öznitelikleri açıklanmaktadır.  
  
 [Bileşenler için tasarım zamanı öznitelikleri](https://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 Böylece bunlar görsel tasarımcılar, tasarım zamanında doğru bir şekilde görüntülenir, bileşenleri ve denetimleri uygulamak için meta veri öznitelikleri listeler.  
  
 [Tasarım zamanı desteği sunma](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 Sınıflar gibi düzenleyiciler ve tasarımcılar, tasarım zamanı desteği sağlayan uygulama açıklar.
