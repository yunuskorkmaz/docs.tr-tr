---
title: 'Nasıl yapılır: Bir Windows Forms düğmesini iptal düğmesi olarak belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: f8eacea0d21159d30d48e48be3093ddf8ca3d7d7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722401"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a><span data-ttu-id="64059-102">Nasıl yapılır: Bir Windows Forms düğmesini iptal düğmesi olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="64059-102">How to: Designate a Windows Forms Button as the Cancel Button</span></span>
<span data-ttu-id="64059-103">Herhangi bir Windows formunda, belirlediğiniz bir <xref:System.Windows.Forms.Button> iptal düğmesi olarak denetimi.</span><span class="sxs-lookup"><span data-stu-id="64059-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="64059-104">Her kullanıcının hangi bağımsız olarak form üzerindeki diğer denetim odağa sahip ESC tuşuna bastığında iptal düğmesine tıklandığında.</span><span class="sxs-lookup"><span data-stu-id="64059-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="64059-105">Böyle bir düğme, kullanıcının herhangi bir işlem taahhüt vermek zorunda kalmadan bir işlemi hızlı bir şekilde çıkmak etkinleştirmek için genellikle programlanır.</span><span class="sxs-lookup"><span data-stu-id="64059-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="64059-106">İptal düğmesi atamak için</span><span class="sxs-lookup"><span data-stu-id="64059-106">To designate the cancel button</span></span>  
  
1.  <span data-ttu-id="64059-107">Formun <xref:System.Windows.Forms.Form.CancelButton%2A> özelliğini uygun <xref:System.Windows.Forms.Button> denetimi.</span><span class="sxs-lookup"><span data-stu-id="64059-107">Set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="64059-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64059-108">See also</span></span>
- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="64059-109">Düğme Kontrolüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="64059-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="64059-110">Windows Forms Düğme Kontrolü Seçme Yolları</span><span class="sxs-lookup"><span data-stu-id="64059-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="64059-111">Nasıl yapılır: Windows Forms düğme tıklamalarına yanıt verme</span><span class="sxs-lookup"><span data-stu-id="64059-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="64059-112">Nasıl yapılır: Bir Windows Forms düğmesini kabul et düğmesi olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="64059-112">How to: Designate a Windows Forms Button as the Accept Button</span></span>](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [<span data-ttu-id="64059-113">Düğme Kontrolü</span><span class="sxs-lookup"><span data-stu-id="64059-113">Button Control</span></span>](button-control-windows-forms.md)
