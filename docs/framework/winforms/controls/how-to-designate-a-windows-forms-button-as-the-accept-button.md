---
title: Bir Düğmeyi Kabul Et Düğmesi Olarak Belirleyin
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: 22cc9da6-b913-4e04-9554-dee443ac5c3a
ms.openlocfilehash: ca5f691fb26db5c4adcb48405c9600b54827104c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142153"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>Nasıl yapılır: Bir Windows Forms Düğmesini Kabul Et Düğmesi Olarak Belirtme
Herhangi bir Windows Formu'nda, varsayılan düğme olarak da bilinen kabul düğmesi olarak bir <xref:System.Windows.Forms.Button> denetim belirleyebilirsiniz. Kullanıcı ENTER tuşuna bastığında, formdaki diğer denetimin odak noktası ne olursa olsun varsayılan düğme tıklanır.  
  
> [!NOTE]
> Bunun istisnaları, odaklı denetimbaşka bir düğme olduğunda -bu durumda, odak lı düğme tıklatılır- veya çok satırlı bir metin kutusu veya ENTER tuşunu hapseden özel bir denetimdir.  
  
### <a name="to-designate-the-accept-button"></a>Kabul düğmesini belirlemek için  
  
1. Formun <xref:System.Windows.Forms.Form.AcceptButton%2A> özelliğini uygun <xref:System.Windows.Forms.Button> denetime ayarlayın.  
  
    ```vb  
    Private Sub SetDefault(ByVal myDefaultBtn As Button)  
      Me.AcceptButton = myDefaultBtn
    End Sub  
    ```  
  
    ```csharp  
    private void SetDefault(Button myDefaultBtn)  
    {  
       this.AcceptButton = myDefaultBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetDefault(Button ^ myDefaultBtn)  
       {  
          this->AcceptButton = myDefaultBtn;  
       }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Düğme Kontrolüne Genel Bakış](button-control-overview-windows-forms.md)
- [Windows Forms Düğme Denetimi Seçmenin Yolları](ways-to-select-a-windows-forms-button-control.md)
- [Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme](how-to-respond-to-windows-forms-button-clicks.md)
- [Nasıl yapılır: Bir Windows Forms Düğmesini İptal Düğmesi Olarak Belirtme](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [Düğme Denetimi](button-control-windows-forms.md)
