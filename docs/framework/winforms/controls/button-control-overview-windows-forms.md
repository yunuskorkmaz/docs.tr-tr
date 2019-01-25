---
title: Düğme Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
ms.openlocfilehash: 042ff7cb868b62778691348cb6c1ba464b794993
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656446"
---
# <a name="button-control-overview-windows-forms"></a>Düğme Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.Button> denetim bir eylemi gerçekleştirmek üzere kullanıcının sağlar. Düğme tıklandığında, gönderilen yokmuş gibi görünüyor ve yayımlandı. Kullanıcı bir düğmeyi tıkladığında <xref:System.Windows.Forms.Control.Click> olay işleyicisi çağrılır. Kodda yerleştirdiğiniz <xref:System.Windows.Forms.Control.Click> seçtiğiniz herhangi bir eylemi gerçekleştirmek için olay işleyicisi.  
  
 Düğmede görüntülenen metni bulunan <xref:System.Windows.Forms.Control.Text%2A> özelliği. Metni düğme genişliğini aşarsa, bir sonraki satıra kaydırılır. Bununla birlikte, Denetim genel yükseklik sağlayamazsa kırpılır. Daha fazla bilgi için [nasıl yapılır: Tarafından görüntülenen metni ayarlama bir Windows Forms denetimi](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md). <xref:System.Windows.Forms.Control.Text%2A> Özelliği, "Denetim erişim anahtarı ile ALT tuşuna basarak tıklayın" açmasına izin veren bir erişim anahtarı içerebilir. Ayrıntılar için bkz [nasıl yapılır: Windows Forms denetimleri için erişim tuşları oluşturma](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md). Metin görünümünü tarafından denetlenir <xref:System.Windows.Forms.Control.Font%2A> özelliği ve <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> özelliği.  
  
 <xref:System.Windows.Forms.Button> Denetimi kullanarak görüntüleri de görüntüleyebilir <xref:System.Windows.Forms.ButtonBase.Image%2A> ve <xref:System.Windows.Forms.ButtonBase.ImageList%2A> özellikleri. Daha fazla bilgi için [nasıl yapılır: Tarafından görüntülenen resmi ayarlama bir Windows Forms denetimi](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.Button>
- [Nasıl yapılır: Windows Forms düğme tıklamalarına yanıt verme](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)
- [Windows Forms Düğme Kontrolü Seçme Yolları](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)
- [Nasıl yapılır: Tasarımcı kullanarak kabul düğmesi olarak bir Windows Formları düğmesi atama](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Nasıl yapılır: Tasarımcı kullanarak iptal düğmesi olarak bir Windows Formları düğmesi atama](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Düğme Kontrolü](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
