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
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a><span data-ttu-id="b3931-102">Nasıl yapılır: Bir Windows Forms Düğmesini Kabul Et Düğmesi Olarak Belirtme</span><span class="sxs-lookup"><span data-stu-id="b3931-102">How to: Designate a Windows Forms Button as the Accept Button</span></span>
<span data-ttu-id="b3931-103">Herhangi bir Windows formunda, bir <xref:System.Windows.Forms.Button> denetimi varsayılan düğme olarak da bilinen kabul et düğmesi olacak şekilde belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3931-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="b3931-104">Kullanıcı ENTER tuşuna bastığında, form üzerindeki diğer denetimin odağa sahip olduğu bağımsız olarak varsayılan düğme tıklanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b3931-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3931-105">Bunun özel durumları, odağa sahip olan denetimin başka bir düğme olduğu durumdur. Bu durumda, odağa sahip düğme veya çok satırlı bir metin kutusu ya da ENTER tuşunu yakaladığı özel bir denetim olur.</span><span class="sxs-lookup"><span data-stu-id="b3931-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>  
  
### <a name="to-designate-the-accept-button"></a><span data-ttu-id="b3931-106">Kabul et düğmesini belirlemek için</span><span class="sxs-lookup"><span data-stu-id="b3931-106">To designate the accept button</span></span>  
  
1. <span data-ttu-id="b3931-107">Formun <xref:System.Windows.Forms.Form.AcceptButton%2A> özelliğini uygun <xref:System.Windows.Forms.Button> denetim olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b3931-107">Set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b3931-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3931-108">See also</span></span>

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [<span data-ttu-id="b3931-109">Düğme Kontrolüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b3931-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="b3931-110">Windows Forms Düğme Kontrolü Seçme Yolları</span><span class="sxs-lookup"><span data-stu-id="b3931-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="b3931-111">Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt verme</span><span class="sxs-lookup"><span data-stu-id="b3931-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="b3931-112">Nasıl yapılır: Iptal düğmesi olarak bir Windows Forms düğmesi belirleyin</span><span class="sxs-lookup"><span data-stu-id="b3931-112">How to: Designate a Windows Forms Button as the Cancel Button</span></span>](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [<span data-ttu-id="b3931-113">Düğme Kontrolü</span><span class="sxs-lookup"><span data-stu-id="b3931-113">Button Control</span></span>](button-control-windows-forms.md)
