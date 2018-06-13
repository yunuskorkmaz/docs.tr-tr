---
title: 'Nasıl yapılır: Bir Windows Forms Düğmesini İptal Düğmesi Olarak Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: efe68ec8e5c34607bb8f865b5d0c7919a0377ab8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530877"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a><span data-ttu-id="bc151-102">Nasıl yapılır: Bir Windows Forms Düğmesini İptal Düğmesi Olarak Belirtme</span><span class="sxs-lookup"><span data-stu-id="bc151-102">How to: Designate a Windows Forms Button as the Cancel Button</span></span>
<span data-ttu-id="bc151-103">Herhangi bir Windows formunda tanımladığınız bir <xref:System.Windows.Forms.Button> iptal düğmesi olarak denetim.</span><span class="sxs-lookup"><span data-stu-id="bc151-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="bc151-104">Her kullanıcının hangi bağımsız olarak formunda diğer denetimi odağa sahip ESC tuşuna bastığında iptal düğmesine tıklandığında.</span><span class="sxs-lookup"><span data-stu-id="bc151-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="bc151-105">Bu tür bir düğme genellikle hızlı bir şekilde bir işlem için herhangi bir eylem kaydetmeden çıkmak kullanıcının etkinleştirmek için programlanmış.</span><span class="sxs-lookup"><span data-stu-id="bc151-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="bc151-106">İptal düğmesi atamak için</span><span class="sxs-lookup"><span data-stu-id="bc151-106">To designate the cancel button</span></span>  
  
1.  <span data-ttu-id="bc151-107">Formun <xref:System.Windows.Forms.Form.CancelButton%2A> özelliğine uygun <xref:System.Windows.Forms.Button> denetim.</span><span class="sxs-lookup"><span data-stu-id="bc151-107">Set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub SetCancelButton(ByVal myCancelBtn As Button)  
       Me.CancelButton = myCancelBtn  
    End Sub  
    ```  
  
    ```csharp  
    private void SetCancelButton(Button myCancelBtn)  
    {  
       this.CancelButton = myCancelBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetCancelButton(Button ^ myCancelBtn)  
       {  
          this->CancelButton = myCancelBtn;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bc151-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bc151-108">See Also</span></span>  
 <xref:System.Windows.Forms.Form.CancelButton%2A>  
 [<span data-ttu-id="bc151-109">Düğme Kontrolüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bc151-109">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="bc151-110">Windows Forms Düğme Kontrolü Seçme Yolları</span><span class="sxs-lookup"><span data-stu-id="bc151-110">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="bc151-111">Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="bc151-111">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="bc151-112">Nasıl yapılır: Bir Windows Forms Düğmesini Kabul Et Düğmesi Olarak Belirtme</span><span class="sxs-lookup"><span data-stu-id="bc151-112">How to: Designate a Windows Forms Button as the Accept Button</span></span>](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-accept-button.md)  
 [<span data-ttu-id="bc151-113">Düğme Kontrolü</span><span class="sxs-lookup"><span data-stu-id="bc151-113">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
