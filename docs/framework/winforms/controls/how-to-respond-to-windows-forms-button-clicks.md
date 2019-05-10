---
title: 'Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], responding to Click events
- events [Windows Forms], Click events
- Click event [Windows Forms], Button control
- MouseDown event
- Button control [Windows Forms], click response
- double-clicks
- examples [Windows Forms], controls
- Click event [Windows Forms], responding to
ms.assetid: 7a4951bd-369c-4662-b246-28ad83eda484
ms.openlocfilehash: ebcde2b5e749c5a3621c623a864578b2a654ce63
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638369"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a><span data-ttu-id="91760-102">Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="91760-102">How to: Respond to Windows Forms Button Clicks</span></span>
<span data-ttu-id="91760-103">Bir Windows Forms en temel kullanımını <xref:System.Windows.Forms.Button> düğmesine tıklandığında, bazı kodlar çalıştırmak için denetimidir.</span><span class="sxs-lookup"><span data-stu-id="91760-103">The most basic use of a Windows Forms <xref:System.Windows.Forms.Button> control is to run some code when the button is clicked.</span></span>  
  
 <span data-ttu-id="91760-104">Tıklayarak bir <xref:System.Windows.Forms.Button> denetimi aynı zamanda oluşturur birkaç diğer olaylar gibi <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, ve <xref:System.Windows.Forms.Control.MouseUp> olayları.</span><span class="sxs-lookup"><span data-stu-id="91760-104">Clicking a <xref:System.Windows.Forms.Button> control also generates a number of other events, such as the <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, and <xref:System.Windows.Forms.Control.MouseUp> events.</span></span> <span data-ttu-id="91760-105">Bu ilgili olayları için olay işleyicileri eklemek istiyorsanız, eylemlerini çakışmasını emin olun.</span><span class="sxs-lookup"><span data-stu-id="91760-105">If you intend to attach event handlers for these related events, be sure that their actions do not conflict.</span></span> <span data-ttu-id="91760-106">Düğmeye tıklandığında, metin kutusuna kullanıcının girdiği bilgileri temizler, örneğin, fare işaretçisi düğmenin üzerine duraklatma bir araç ipucu artık var olmayan bu bilgilerle görüntülemelidir değil.</span><span class="sxs-lookup"><span data-stu-id="91760-106">For example, if clicking the button clears information that the user has typed in a text box, pausing the mouse pointer over the button should not display a tool tip with that now-nonexistent information.</span></span>  
  
 <span data-ttu-id="91760-107">Kullanıcının çift çalışırsa <xref:System.Windows.Forms.Button> denetimi her tıklatma ayrı ayrı işlenir; diğer bir deyişle, denetime çift tıklama olay desteklemez.</span><span class="sxs-lookup"><span data-stu-id="91760-107">If the user attempts to double-click the <xref:System.Windows.Forms.Button> control, each click will be processed separately; that is, the control does not support the double-click event.</span></span>  
  
### <a name="to-respond-to-a-button-click"></a><span data-ttu-id="91760-108">Yanıt vermek için bir düğmeye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91760-108">To respond to a button click</span></span>  
  
- <span data-ttu-id="91760-109">Düğmenin içinde `Click` <xref:System.EventHandler> çalıştırmak için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="91760-109">In the button's `Click` <xref:System.EventHandler> write the code to run.</span></span> <span data-ttu-id="91760-110">`Button1_Click` denetime bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91760-110">`Button1_Click` must be bound to the control.</span></span> <span data-ttu-id="91760-111">Daha fazla bilgi için [nasıl yapılır: Windows Forms için çalışma zamanında olay işleyicileri oluşturma](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="91760-111">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       MessageBox.Show("Button1 was clicked")  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       MessageBox.Show("button1 was clicked");  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          MessageBox::Show("button1 was clicked");  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="91760-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91760-112">See also</span></span>

- [<span data-ttu-id="91760-113">Düğme Kontrolüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="91760-113">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="91760-114">Windows Forms Düğme Kontrolü Seçme Yolları</span><span class="sxs-lookup"><span data-stu-id="91760-114">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="91760-115">Düğme Kontrolü</span><span class="sxs-lookup"><span data-stu-id="91760-115">Button Control</span></span>](button-control-windows-forms.md)
