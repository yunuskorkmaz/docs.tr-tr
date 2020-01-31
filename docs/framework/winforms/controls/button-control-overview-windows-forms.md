---
title: Düğme Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
ms.openlocfilehash: 4ba7b333e5414efb4814d64ce50c55e08b27f859
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747085"
---
# <a name="button-control-overview-windows-forms"></a>Düğme Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.Button> denetimi kullanıcının bir eylem gerçekleştirmek için tıkladığından izin verir. Düğmeye tıklandığında, gönderildiği ve serbest bırakılmakta olduğu anlaşılıyor. Kullanıcı bir düğmeye tıkladığında <xref:System.Windows.Forms.Control.Click> olay işleyicisi çağrılır. Seçtiğiniz herhangi bir eylemi gerçekleştirmek için kodu <xref:System.Windows.Forms.Control.Click> olay işleyicisine yerleştirebilirsiniz.  
  
 Düğme üzerinde görünen metin <xref:System.Windows.Forms.Control.Text%2A> özelliğinde bulunur. Metniniz düğme genişliğini aşarsa, sonraki satıra kaydırılır. Ancak, denetim genel yüksekliğini barındıramazsa kırpılacak. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms denetimi tarafından görüntülenecek metni ayarlama](how-to-set-the-text-displayed-by-a-windows-forms-control.md). <xref:System.Windows.Forms.Control.Text%2A> özelliği bir erişim anahtarı içerebilir ve bu, kullanıcının denetime "tıklamasına" izin veren, erişim anahtarı ile ALT tuşuna basarak. Ayrıntılar için bkz. [nasıl yapılır: Windows Forms denetimleri Için erişim tuşları oluşturma](how-to-create-access-keys-for-windows-forms-controls.md). Metnin görünümü <xref:System.Windows.Forms.Control.Font%2A> özelliği ve <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> özelliği tarafından denetlenir.  
  
 <xref:System.Windows.Forms.Button> denetim, <xref:System.Windows.Forms.ButtonBase.Image%2A> ve <xref:System.Windows.Forms.ButtonBase.ImageList%2A> özelliklerini kullanarak da görüntüler görüntüleyebilir. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms denetimi tarafından görüntülenecek görüntüyü ayarlama](how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Button>
- [Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme](how-to-respond-to-windows-forms-button-clicks.md)
- [Windows Forms Düğme Kontrolü Seçme Yolları](ways-to-select-a-windows-forms-button-control.md)
- [Nasıl yapılır: Tasarımcı Kullanarak Bir Windows Forms Düğmesini Kabul Et Düğmesi Olarak Belirtme](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Nasıl yapılır: Tasarımcı Kullanarak Bir Windows Forms Düğmesini İptal Düğmesi Olarak Belirtme](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Düğme Kontrolü](button-control-windows-forms.md)
