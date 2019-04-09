---
title: 'Nasıl yapılır: Tasarımcı Kullanarak İptal Düğmesi olarak bir Windows Forms Düğmesi Atama'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: be0847d1837ec85ed9d82dc7cc879d0cffa19cd6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156227"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak İptal Düğmesi olarak bir Windows Forms Düğmesi Atama
Herhangi bir Windows formunda, belirlediğiniz bir <xref:System.Windows.Forms.Button> iptal düğmesi olarak denetimi. Her kullanıcının hangi bağımsız olarak form üzerindeki diğer denetim odağa sahip ESC tuşuna bastığında iptal düğmesine tıklandığında. Böyle bir düğme, kullanıcının herhangi bir işlem taahhüt vermek zorunda kalmadan bir işlemi hızlı bir şekilde çıkmak etkinleştirmek için genellikle programlanır.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-designate-the-cancel-button"></a>İptal düğmesi atamak için  
  
1.  Düğme yer aldığı formu seçin.  
  
2.  İçinde **özellikleri** penceresinde, formun ayarlayın <xref:System.Windows.Forms.Form.CancelButton%2A> özelliğini <xref:System.Windows.Forms.Button> denetimin adı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Düğme Kontrolüne Genel Bakış](button-control-overview-windows-forms.md)
- [Windows Forms Düğme Denetimi Seçmenin Yolları](ways-to-select-a-windows-forms-button-control.md)
- [Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme](how-to-respond-to-windows-forms-button-clicks.md)
- [Nasıl yapılır: Tasarımcı Kullanarak Kabul Düğmesi olarak bir Windows Forms Düğmesi Atama](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Düğme Kontrolü](button-control-windows-forms.md)
