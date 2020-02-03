---
title: Bir düğmeyi Iptal düğmesi olarak belirleyin
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: 123b3e275065efadd24815320ea7d855808e60b9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743253"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a><span data-ttu-id="3c12c-102">Nasıl yapılır: Bir Windows Forms Düğmesini İptal Düğmesi Olarak Belirtme</span><span class="sxs-lookup"><span data-stu-id="3c12c-102">How to: Designate a Windows Forms Button as the Cancel Button</span></span>
<span data-ttu-id="3c12c-103">Herhangi bir Windows formunda, bir <xref:System.Windows.Forms.Button> denetimini iptal düğmesi olacak şekilde belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c12c-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="3c12c-104">Kullanıcı, form üzerindeki diğer denetimin odağa sahip olduğu bağımsız olarak ESC tuşuna bastığında bir iptal düğmesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3c12c-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="3c12c-105">Bu tür bir düğme, genellikle kullanıcının herhangi bir eylemde bulunmadan bir işlemden hızlı bir şekilde çıkmasına olanak tanımak üzere programlanır.</span><span class="sxs-lookup"><span data-stu-id="3c12c-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="3c12c-106">İptal düğmesini belirlemek için</span><span class="sxs-lookup"><span data-stu-id="3c12c-106">To designate the cancel button</span></span>  
  
1. <span data-ttu-id="3c12c-107">Formun <xref:System.Windows.Forms.Form.CancelButton%2A> özelliğini uygun <xref:System.Windows.Forms.Button> denetimine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3c12c-107">Set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3c12c-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c12c-108">See also</span></span>

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="3c12c-109">Düğme Kontrolüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3c12c-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="3c12c-110">Windows Forms Düğme Kontrolü Seçme Yolları</span><span class="sxs-lookup"><span data-stu-id="3c12c-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="3c12c-111">Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="3c12c-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="3c12c-112">Nasıl yapılır: Bir Windows Forms Düğmesini Kabul Et Düğmesi Olarak Belirtme</span><span class="sxs-lookup"><span data-stu-id="3c12c-112">How to: Designate a Windows Forms Button as the Accept Button</span></span>](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [<span data-ttu-id="3c12c-113">Düğme Kontrolü</span><span class="sxs-lookup"><span data-stu-id="3c12c-113">Button Control</span></span>](button-control-windows-forms.md)
