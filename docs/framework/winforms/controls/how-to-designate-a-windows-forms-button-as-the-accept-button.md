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
ms.openlocfilehash: 8e608bb2cb4635ef1d29fd7a0aff3ac95fcd9af5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309829"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a><span data-ttu-id="0324b-102">Nasıl yapılır: Bir Windows Forms Düğmesini Kabul Et Düğmesi Olarak Belirtme</span><span class="sxs-lookup"><span data-stu-id="0324b-102">How to: Designate a Windows Forms Button as the Accept Button</span></span>
<span data-ttu-id="0324b-103">Herhangi bir Windows formunda, belirlediğiniz bir <xref:System.Windows.Forms.Button> kabul et düğmesi olarak da bilinen varsayılan düğme olarak denetimi.</span><span class="sxs-lookup"><span data-stu-id="0324b-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="0324b-104">Kullanıcı ENTER tuşuna bastığında olduğunda, bağımsız olarak form üzerindeki diğer denetim odağa sahip varsayılan düğme tıklandığında.</span><span class="sxs-lookup"><span data-stu-id="0324b-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0324b-105">Başka bir düğme denetimi odağa sahip olduğunda bu olan özel durumlar — odağa sahip düğmesine tıklandığında bu durumda, — veya çok satırlı metin kutusu ya da ENTER tuşunu yakalar özel bir denetim.</span><span class="sxs-lookup"><span data-stu-id="0324b-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>  
  
### <a name="to-designate-the-accept-button"></a><span data-ttu-id="0324b-106">Kabul Et düğmesi atamak için</span><span class="sxs-lookup"><span data-stu-id="0324b-106">To designate the accept button</span></span>  
  
1. <span data-ttu-id="0324b-107">Formun <xref:System.Windows.Forms.Form.AcceptButton%2A> özelliğini uygun <xref:System.Windows.Forms.Button> denetimi.</span><span class="sxs-lookup"><span data-stu-id="0324b-107">Set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0324b-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0324b-108">See also</span></span>

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [<span data-ttu-id="0324b-109">Düğme Kontrolüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0324b-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="0324b-110">Windows Forms Düğme Denetimi Seçmenin Yolları</span><span class="sxs-lookup"><span data-stu-id="0324b-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="0324b-111">Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="0324b-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="0324b-112">Nasıl yapılır: Bir Windows Forms Düğmesini İptal Düğmesi Olarak Belirtme</span><span class="sxs-lookup"><span data-stu-id="0324b-112">How to: Designate a Windows Forms Button as the Cancel Button</span></span>](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [<span data-ttu-id="0324b-113">Düğme Kontrolü</span><span class="sxs-lookup"><span data-stu-id="0324b-113">Button Control</span></span>](button-control-windows-forms.md)
