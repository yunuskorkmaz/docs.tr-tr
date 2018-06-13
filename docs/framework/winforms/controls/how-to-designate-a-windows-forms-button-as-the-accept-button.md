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
ms.openlocfilehash: a69964b83e9948a844483725616a150234a38c97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531946"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a><span data-ttu-id="42c3a-102">Nasıl yapılır: Bir Windows Forms Düğmesini Kabul Et Düğmesi Olarak Belirtme</span><span class="sxs-lookup"><span data-stu-id="42c3a-102">How to: Designate a Windows Forms Button as the Accept Button</span></span>
<span data-ttu-id="42c3a-103">Herhangi bir Windows formunda tanımladığınız bir <xref:System.Windows.Forms.Button> kabul et düğmesi olarak da bilinen varsayılan düğme olarak denetim.</span><span class="sxs-lookup"><span data-stu-id="42c3a-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="42c3a-104">Her kullanıcı ENTER tuşuna bastığında, bağımsız olarak form üzerindeki diğer denetim odağı olan varsayılan düğme tıklatıldığında.</span><span class="sxs-lookup"><span data-stu-id="42c3a-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42c3a-105">Başka bir düğme denetimi odağa sahip olduğunda bu öğeler için özel durumlar — odaklanılan düğmesine tıklandığında bu durumda, — veya çok satırlı metin kutusu veya ENTER tuşuna yakalar özel bir denetim.</span><span class="sxs-lookup"><span data-stu-id="42c3a-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>  
  
### <a name="to-designate-the-accept-button"></a><span data-ttu-id="42c3a-106">Kabul Et düğmesi atamak için</span><span class="sxs-lookup"><span data-stu-id="42c3a-106">To designate the accept button</span></span>  
  
1.  <span data-ttu-id="42c3a-107">Formun <xref:System.Windows.Forms.Form.AcceptButton%2A> özelliğine uygun <xref:System.Windows.Forms.Button> denetim.</span><span class="sxs-lookup"><span data-stu-id="42c3a-107">Set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="42c3a-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="42c3a-108">See Also</span></span>  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>  
 [<span data-ttu-id="42c3a-109">Düğme Kontrolüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="42c3a-109">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="42c3a-110">Windows Forms Düğme Kontrolü Seçme Yolları</span><span class="sxs-lookup"><span data-stu-id="42c3a-110">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="42c3a-111">Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="42c3a-111">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="42c3a-112">Nasıl yapılır: Bir Windows Forms Düğmesini İptal Düğmesi Olarak Belirtme</span><span class="sxs-lookup"><span data-stu-id="42c3a-112">How to: Designate a Windows Forms Button as the Cancel Button</span></span>](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-cancel-button.md)  
 [<span data-ttu-id="42c3a-113">Düğme Kontrolü</span><span class="sxs-lookup"><span data-stu-id="42c3a-113">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
