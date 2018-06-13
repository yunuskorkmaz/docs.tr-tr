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
ms.openlocfilehash: 397808c055fd5ba5e8a73d47dfc7fee6c0cf2975
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540088"
---
# <a name="radiobutton-control-overview-windows-forms"></a>RadioButton Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.RadioButton> denetimleri iki veya daha fazla dışlayan bir dizi kullanıcıya sunar. Radyo düğmeleri ve onay kutuları benzer şekilde çalışması için görünebilir, ancak önemli bir fark yoktur: kullanıcı radyo düğmesini seçtiğinde aynı gruptaki diğer radyo düğmeleri de seçilemez. Buna karşılık, herhangi bir sayıda onay kutularını seçilebilir. Radyo düğmesi grubunda tanımlama kullanıcı söyler, ", yalnızca tek seçim yapabileceğiniz bir seçenek kümesi İşte."  
  
## <a name="using-the-control"></a>Denetimi kullanma  
 Zaman bir <xref:System.Windows.Forms.RadioButton> denetim tıklandığında, kendi <xref:System.Windows.Forms.RadioButton.Checked%2A> özelliği ayarlanmış `true` ve <xref:System.Windows.Forms.Control.Click> olay işleyicisi çağrılır. <xref:System.Windows.Forms.RadioButton.CheckedChanged> Olayı zaman değerini <xref:System.Windows.Forms.RadioButton.Checked%2A> özellik değişikliği. Varsa <xref:System.Windows.Forms.RadioButton.AutoCheck%2A> özelliği ayarlanmış `true` (varsayılan), radyo düğmesinin seçildiğinde diğer tüm kullanıcılar grubunda otomatik olarak temizlenir. Bu özellik genellikle olduğundan yalnızca kümesine `false` seçili radyo düğmesi emin olmak için doğrulama kodu kullanıldığında izin verilen bir seçenektir. Denetim içinde görüntülenen metni ile ayarlama <xref:System.Windows.Forms.Control.Text%2A> erişim anahtar kısayollar içerebilir özelliği. Erişim tuşu "Denetim erişim anahtarı ile ALT tuşuna basarak tıklayın" görüntülemesini sağlar. Daha fazla bilgi için bkz: [nasıl yapılır: oluşturmak erişim anahtarları için Windows Forms denetimleri](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md) ve [nasıl yapılır: Windows Forms denetimi tarafından görüntülenen metni ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).  
  
 <xref:System.Windows.Forms.RadioButton> Denetim varsa seçtiyseniz, basılı göründüğünden ve komut düğmesi gibi görünebilir <xref:System.Windows.Forms.RadioButton.Appearance%2A> özelliği ayarlanmış <xref:System.Windows.Forms.Appearance.Button>. Radyo düğmelerini kullanarak görüntüleri de görüntüleyebilir <xref:System.Windows.Forms.ButtonBase.Image%2A> ve <xref:System.Windows.Forms.ButtonBase.ImageList%2A> özellikleri. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms denetimi tarafından görüntülenen resmi ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.RadioButton>  
 [Panel Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [GroupBox Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)  
 [CheckBox Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms Denetimleri için Erişim Tuşları Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 [Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Metni Ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [Nasıl yapılır: Windows Forms RadioButton Denetimlerini Küme İşlevi Görecek Şekilde Gruplama](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)  
 [RadioButton Denetimi](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)
