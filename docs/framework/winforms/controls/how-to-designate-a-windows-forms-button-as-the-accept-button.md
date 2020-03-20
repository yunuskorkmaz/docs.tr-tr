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
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a><span data-ttu-id="58605-102">Nasıl yapılır: Bir Windows Forms Düğmesini Kabul Et Düğmesi Olarak Belirtme</span><span class="sxs-lookup"><span data-stu-id="58605-102">How to: Designate a Windows Forms Button as the Accept Button</span></span>
<span data-ttu-id="58605-103">Herhangi bir Windows Formu'nda, varsayılan düğme olarak da bilinen kabul düğmesi olarak bir <xref:System.Windows.Forms.Button> denetim belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58605-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="58605-104">Kullanıcı ENTER tuşuna bastığında, formdaki diğer denetimin odak noktası ne olursa olsun varsayılan düğme tıklanır.</span><span class="sxs-lookup"><span data-stu-id="58605-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="58605-105">Bunun istisnaları, odaklı denetimbaşka bir düğme olduğunda -bu durumda, odak lı düğme tıklatılır- veya çok satırlı bir metin kutusu veya ENTER tuşunu hapseden özel bir denetimdir.</span><span class="sxs-lookup"><span data-stu-id="58605-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>  
  
### <a name="to-designate-the-accept-button"></a><span data-ttu-id="58605-106">Kabul düğmesini belirlemek için</span><span class="sxs-lookup"><span data-stu-id="58605-106">To designate the accept button</span></span>  
  
1. <span data-ttu-id="58605-107">Formun <xref:System.Windows.Forms.Form.AcceptButton%2A> özelliğini uygun <xref:System.Windows.Forms.Button> denetime ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="58605-107">Set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="58605-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58605-108">See also</span></span>

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [<span data-ttu-id="58605-109">Düğme Kontrolüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="58605-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="58605-110">Windows Forms Düğme Denetimi Seçmenin Yolları</span><span class="sxs-lookup"><span data-stu-id="58605-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="58605-111">Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="58605-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="58605-112">Nasıl yapılır: Bir Windows Forms Düğmesini İptal Düğmesi Olarak Belirtme</span><span class="sxs-lookup"><span data-stu-id="58605-112">How to: Designate a Windows Forms Button as the Cancel Button</span></span>](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [<span data-ttu-id="58605-113">Düğme Denetimi</span><span class="sxs-lookup"><span data-stu-id="58605-113">Button Control</span></span>](button-control-windows-forms.md)
