---
title: RadioButton Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- RadioButton
helpviewer_keywords:
- RadioButton control [Windows Forms], about RadioButton control
- RadioButton control [Windows Forms], determining state
- radio buttons [Windows Forms], determining state
- radio buttons [Windows Forms], about radio buttons
ms.assetid: cd11f0c2-d098-4022-adf9-1455bc166a13
ms.openlocfilehash: bbc93046b69d39caadde4986ff56f067fc206a9e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741140"
---
# <a name="radiobutton-control-overview-windows-forms"></a>RadioButton Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.RadioButton> denetimleri, kullanıcıya birbirini dışlayan iki veya daha fazla seçenek kümesi sunar. Radyo düğmeleri ve onay kutuları benzer şekilde işlev gibi görünebilir ve önemli bir farklılık vardır: bir Kullanıcı radyo düğmesini seçtiğinde, aynı gruptaki diğer radyo düğmeleri de seçilemez. Bunun aksine, herhangi bir sayıda onay kutusu seçilebilir. Radyo düğmesi grubu tanımlamak kullanıcıya "bir tane ve yalnızca bir tane seçebileceğiniz seçimler kümesi" olduğunu söyler.  
  
## <a name="using-the-control"></a>Denetimi kullanma  
 <xref:System.Windows.Forms.RadioButton> denetimine tıklandığında, <xref:System.Windows.Forms.RadioButton.Checked%2A> özelliği `true` olarak ayarlanır ve <xref:System.Windows.Forms.Control.Click> olay işleyicisi çağrılır. <xref:System.Windows.Forms.RadioButton.CheckedChanged> olayı, <xref:System.Windows.Forms.RadioButton.Checked%2A> özelliğinin değeri değiştiğinde tetiklenir. <xref:System.Windows.Forms.RadioButton.AutoCheck%2A> özelliği `true` (varsayılan) olarak ayarlandıysa, radyo düğmesi seçildiğinde gruptaki diğer tüm diğerleri otomatik olarak temizlenir. Bu özellik genellikle, seçilen radyo düğmesinin izin verilen bir seçenek olduğundan emin olmak için doğrulama kodu kullanıldığında `false` olarak ayarlanır. Denetim içinde görünen metin, erişim tuşu kısayolları içerebilen <xref:System.Windows.Forms.Control.Text%2A> özelliği ile ayarlanır. Erişim anahtarı, bir kullanıcının, erişim anahtarıyla ALT tuşuna basarak denetimi "tıklamasına" olanak sağlar. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms denetimleri Için erişim tuşları oluşturma](how-to-create-access-keys-for-windows-forms-controls.md) ve [nasıl yapılır: Windows Forms denetimi tarafından görüntülenecek metni ayarlama](how-to-set-the-text-displayed-by-a-windows-forms-control.md).  
  
 <xref:System.Windows.Forms.RadioButton> denetimi bir komut düğmesi gibi görünebilir ve bu, <xref:System.Windows.Forms.RadioButton.Appearance%2A> özelliği <xref:System.Windows.Forms.Appearance.Button>olarak ayarlandıysa, seçildiği şekilde görünür. Radyo düğmeleri Ayrıca <xref:System.Windows.Forms.ButtonBase.Image%2A> ve <xref:System.Windows.Forms.ButtonBase.ImageList%2A> özelliklerini kullanarak görüntü görüntüleyebilir. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms denetimi tarafından görüntülenecek görüntüyü ayarlama](how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.RadioButton>
- [Panel Denetimine Genel Bakış](panel-control-overview-windows-forms.md)
- [GroupBox Denetimine Genel Bakış](groupbox-control-overview-windows-forms.md)
- [CheckBox Denetimine Genel Bakış](checkbox-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms Denetimleri için Erişim Tuşları Oluşturma](how-to-create-access-keys-for-windows-forms-controls.md)
- [Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Metni Ayarlama](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Nasıl yapılır: Windows Forms RadioButton Denetimlerini Küme İşlevi Görecek Şekilde Gruplama](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)
- [RadioButton Denetimi](radiobutton-control-windows-forms.md)
