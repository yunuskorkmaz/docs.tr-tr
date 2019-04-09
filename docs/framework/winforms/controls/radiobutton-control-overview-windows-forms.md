---
title: RadioButton Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- RadioButton
helpviewer_keywords:
- RadioButton control [Windows Forms], about RadioButton control
- RadioButton control [Windows Forms], determining state
- radio buttons [Windows Forms], determining state
- radio buttons [Windows Forms], about radio buttons
ms.assetid: cd11f0c2-d098-4022-adf9-1455bc166a13
ms.openlocfilehash: 1210658226d9bcacbf4904fdc90a9908c34f5b73
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129122"
---
# <a name="radiobutton-control-overview-windows-forms"></a>RadioButton Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.RadioButton> denetimleri kullanıcıya iki veya daha fazla birbirini dışlayan seçenekleri kümesi sunar. Radyo düğmeleri ve onay kutularını benzer şekilde çalışması için görünebilse de önemli bir fark yoktur: kullanıcı bir radyo düğmesini seçtiğinde, aynı gruptaki diğer radyo düğmeleri de seçilemez. Buna karşılık, herhangi bir sayıda onay kutularını seçilebilir. Kullanıcı bir radyo düğmesi grubunda tanımlama söyler, ", yalnızca tek seçim yapabileceğiniz bir seçenek kümesi aşağıdadır."  
  
## <a name="using-the-control"></a>Denetimi kullanma  
 Olduğunda bir <xref:System.Windows.Forms.RadioButton> denetim tıklandığında, kendi <xref:System.Windows.Forms.RadioButton.Checked%2A> özelliği `true` ve <xref:System.Windows.Forms.Control.Click> olay işleyicisi çağrılır. <xref:System.Windows.Forms.RadioButton.CheckedChanged> Olayı zaman değerini <xref:System.Windows.Forms.RadioButton.Checked%2A> özellik değişiklikleri. Varsa <xref:System.Windows.Forms.RadioButton.AutoCheck%2A> özelliği `true` (varsayılan), radyo düğmesi seçildiğinde gruptaki diğer tüm otomatik olarak temizlenir. Bu özellik genellikle, yalnızca kümesine `false` radyo düğmesini seçili emin olmak için bir doğrulama kodu kullanıldığında izin verilen bir seçenektir. Denetimde görüntülenen metnin ile ayarlanır <xref:System.Windows.Forms.Control.Text%2A> özelliğe erişim tuş kısayollarını içerebilir. Bir erişim anahtarı "Denetim erişim anahtarı ile ALT tuşuna basarak tıklayın" sağlar. Daha fazla bilgi için [nasıl yapılır: Windows Forms denetimleri için erişim tuşları oluşturma](how-to-create-access-keys-for-windows-forms-controls.md) ve [nasıl yapılır: Tarafından görüntülenen metni ayarlama bir Windows Forms denetimi](how-to-set-the-text-displayed-by-a-windows-forms-control.md).  
  
 <xref:System.Windows.Forms.RadioButton> Denetim, varsa seçtiyseniz, basılı göründüğünden ve komut düğmesi gibi görünebilir <xref:System.Windows.Forms.RadioButton.Appearance%2A> özelliği <xref:System.Windows.Forms.Appearance.Button>. Radyo düğmeleri kullanarak görüntüleri de görüntüleyebilir <xref:System.Windows.Forms.ButtonBase.Image%2A> ve <xref:System.Windows.Forms.ButtonBase.ImageList%2A> özellikleri. Daha fazla bilgi için [nasıl yapılır: Tarafından görüntülenen resmi ayarlama bir Windows Forms denetimi](how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.RadioButton>
- [Panel Denetimine Genel Bakış](panel-control-overview-windows-forms.md)
- [GroupBox Denetimine Genel Bakış](groupbox-control-overview-windows-forms.md)
- [CheckBox Denetimine Genel Bakış](checkbox-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms Denetimleri için Erişim Tuşları Oluşturma](how-to-create-access-keys-for-windows-forms-controls.md)
- [Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Metni Ayarlama](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Nasıl yapılır: Windows Forms RadioButton Denetimlerini Küme İşlevi Görecek Şekilde Gruplama](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)
- [RadioButton Denetimi](radiobutton-control-windows-forms.md)
