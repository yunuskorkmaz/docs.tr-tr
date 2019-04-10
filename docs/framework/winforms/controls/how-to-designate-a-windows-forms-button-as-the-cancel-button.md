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
ms.openlocfilehash: ad95a527ea72858cc106c87d8712110e018e97b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231441"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a><span data-ttu-id="d6fbc-102">Nasıl yapılır: Bir Windows Forms Düğmesini İptal Düğmesi Olarak Belirtme</span><span class="sxs-lookup"><span data-stu-id="d6fbc-102">How to: Designate a Windows Forms Button as the Cancel Button</span></span>
<span data-ttu-id="d6fbc-103">Herhangi bir Windows formunda, belirlediğiniz bir <xref:System.Windows.Forms.Button> iptal düğmesi olarak denetimi.</span><span class="sxs-lookup"><span data-stu-id="d6fbc-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="d6fbc-104">Her kullanıcının hangi bağımsız olarak form üzerindeki diğer denetim odağa sahip ESC tuşuna bastığında iptal düğmesine tıklandığında.</span><span class="sxs-lookup"><span data-stu-id="d6fbc-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="d6fbc-105">Böyle bir düğme, kullanıcının herhangi bir işlem taahhüt vermek zorunda kalmadan bir işlemi hızlı bir şekilde çıkmak etkinleştirmek için genellikle programlanır.</span><span class="sxs-lookup"><span data-stu-id="d6fbc-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="d6fbc-106">İptal düğmesi atamak için</span><span class="sxs-lookup"><span data-stu-id="d6fbc-106">To designate the cancel button</span></span>  
  
1.  <span data-ttu-id="d6fbc-107">Formun <xref:System.Windows.Forms.Form.CancelButton%2A> özelliğini uygun <xref:System.Windows.Forms.Button> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d6fbc-107">Set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d6fbc-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6fbc-108">See also</span></span>

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="d6fbc-109">Düğme Kontrolüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d6fbc-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="d6fbc-110">Windows Forms Düğme Denetimi Seçmenin Yolları</span><span class="sxs-lookup"><span data-stu-id="d6fbc-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="d6fbc-111">Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="d6fbc-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="d6fbc-112">Nasıl yapılır: Bir Windows Forms Düğmesini Kabul Et Düğmesi Olarak Belirtme</span><span class="sxs-lookup"><span data-stu-id="d6fbc-112">How to: Designate a Windows Forms Button as the Accept Button</span></span>](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [<span data-ttu-id="d6fbc-113">Düğme Kontrolü</span><span class="sxs-lookup"><span data-stu-id="d6fbc-113">Button Control</span></span>](button-control-windows-forms.md)
