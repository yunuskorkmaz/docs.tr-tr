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
ms.openlocfilehash: 5b21ee7da7a666a391be3bc5be57855eaa7ec8b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967363"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>Nasıl yapılır: Bir Windows Forms Düğmesini Kabul Et Düğmesi Olarak Belirtme
Herhangi bir Windows formunda, bir <xref:System.Windows.Forms.Button> denetimi varsayılan düğme olarak da bilinen kabul et düğmesi olacak şekilde belirleyebilirsiniz. Kullanıcı ENTER tuşuna bastığında, form üzerindeki diğer denetimin odağa sahip olduğu bağımsız olarak varsayılan düğme tıklanmalıdır.  
  
> [!NOTE]
> Bunun özel durumları, odağa sahip olan denetimin başka bir düğme olduğu durumdur. Bu durumda, odağa sahip düğme veya çok satırlı bir metin kutusu ya da ENTER tuşunu yakaladığı özel bir denetim olur.  
  
### <a name="to-designate-the-accept-button"></a>Kabul et düğmesini belirlemek için  
  
1. Formun <xref:System.Windows.Forms.Form.AcceptButton%2A> özelliğini uygun <xref:System.Windows.Forms.Button> denetim olarak ayarlayın.  
  
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
- [Windows Forms Düğme Kontrolü Seçme Yolları](ways-to-select-a-windows-forms-button-control.md)
- [Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt verme](how-to-respond-to-windows-forms-button-clicks.md)
- [Nasıl yapılır: Iptal düğmesi olarak bir Windows Forms düğmesi belirleyin](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [Düğme Kontrolü](button-control-windows-forms.md)
