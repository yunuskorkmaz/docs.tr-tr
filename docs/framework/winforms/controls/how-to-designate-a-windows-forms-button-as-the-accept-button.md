---
title: 'Nasıl yapılır: Bir Windows Forms Düğmesini Kabul Et Düğmesi Olarak Belirtme'
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
ms.openlocfilehash: 1e24e410681b03a92c8c48b187dde569eccdc1c1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222152"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>Nasıl yapılır: Bir Windows Forms Düğmesini Kabul Et Düğmesi Olarak Belirtme
Herhangi bir Windows formunda, belirlediğiniz bir <xref:System.Windows.Forms.Button> kabul et düğmesi olarak da bilinen varsayılan düğme olarak denetimi. Kullanıcı ENTER tuşuna bastığında olduğunda, bağımsız olarak form üzerindeki diğer denetim odağa sahip varsayılan düğme tıklandığında.  
  
> [!NOTE]
>  Başka bir düğme denetimi odağa sahip olduğunda bu olan özel durumlar — odağa sahip düğmesine tıklandığında bu durumda, — veya çok satırlı metin kutusu ya da ENTER tuşunu yakalar özel bir denetim.  
  
### <a name="to-designate-the-accept-button"></a>Kabul Et düğmesi atamak için  
  
1.  Formun <xref:System.Windows.Forms.Form.AcceptButton%2A> özelliğini uygun <xref:System.Windows.Forms.Button> denetimi.  
  
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
- [Düğme Kontrolü](button-control-windows-forms.md)
