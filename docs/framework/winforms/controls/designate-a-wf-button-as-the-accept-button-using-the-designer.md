---
title: 'Nasıl yapılır: Tasarımcı kullanarak kabul düğmesi olarak bir Windows Formları düğmesi atama'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: 477094b88c99bbe9193a6eaedb5c16d0c0e679d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709552"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a>Nasıl yapılır: Tasarımcı kullanarak kabul düğmesi olarak bir Windows Formları düğmesi atama
Herhangi bir Windows formunda, belirlediğiniz bir <xref:System.Windows.Forms.Button> kabul et düğmesi olarak da bilinen varsayılan düğme olarak denetimi. Kullanıcı ENTER tuşuna bastığında olduğunda, bağımsız olarak form üzerindeki diğer denetim odağa sahip varsayılan düğme tıklandığında. Başka bir düğme denetimi odağa sahip olduğunda bu olan özel durumlar — odağa sahip düğmesine tıklandığında bu durumda, — veya çok satırlı metin kutusu ya da ENTER tuşunu yakalar özel bir denetim.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-designate-the-accept-button"></a>Kabul Et düğmesi atamak için  
  
1.  Düğme yer aldığı formu seçin.  
  
2.  İçinde **özellikleri** penceresinde, formun ayarlayın <xref:System.Windows.Forms.Form.AcceptButton%2A> özelliğini <xref:System.Windows.Forms.Button> denetimin adı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Düğme Kontrolüne Genel Bakış](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)
- [Windows Forms Düğme Kontrolü Seçme Yolları](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)
- [Nasıl yapılır: Windows Forms düğme tıklamalarına yanıt verme](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)
- [Nasıl yapılır: Tasarımcı kullanarak iptal düğmesi olarak bir Windows Formları düğmesi atama](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Düğme Kontrolü](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
