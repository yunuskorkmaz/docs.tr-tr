---
title: "Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28b0467c8b589882fe5afd7e884d0de55d8ca564
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a><span data-ttu-id="8d64c-102">Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="8d64c-102">How to: Respond to Windows Forms Button Clicks</span></span>
<span data-ttu-id="8d64c-103">Windows Forms en temel kullanımını <xref:System.Windows.Forms.Button> denetimidir düğmesine tıklandığında bazı kodlar çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="8d64c-103">The most basic use of a Windows Forms <xref:System.Windows.Forms.Button> control is to run some code when the button is clicked.</span></span>  
  
 <span data-ttu-id="8d64c-104">Tıklatarak bir <xref:System.Windows.Forms.Button> denetimi de oluşturur diğer olayların sayısı gibi <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, ve <xref:System.Windows.Forms.Control.MouseUp> olaylar.</span><span class="sxs-lookup"><span data-stu-id="8d64c-104">Clicking a <xref:System.Windows.Forms.Button> control also generates a number of other events, such as the <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, and <xref:System.Windows.Forms.Control.MouseUp> events.</span></span> <span data-ttu-id="8d64c-105">Bu ilgili olayları için olay işleyicileri eklemek istiyorsanız, eylemlerini çakışmasını emin olun.</span><span class="sxs-lookup"><span data-stu-id="8d64c-105">If you intend to attach event handlers for these related events, be sure that their actions do not conflict.</span></span> <span data-ttu-id="8d64c-106">Düğmesini tıklatarak bir metin kutusunda kullanıcının girdiği bilgileri temizler, örneğin, fare işaretçisini düğmenin üzerinde duraklatma şimdi varolmayan bilgileri olan bir araç ipucu görüntülemelidir değil.</span><span class="sxs-lookup"><span data-stu-id="8d64c-106">For example, if clicking the button clears information that the user has typed in a text box, pausing the mouse pointer over the button should not display a tool tip with that now-nonexistent information.</span></span>  
  
 <span data-ttu-id="8d64c-107">Kullanıcı çift çalışırsa <xref:System.Windows.Forms.Button> denetim, her tıklatma ayrı ayrı işlenir; diğer bir deyişle, denetim çift olay desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="8d64c-107">If the user attempts to double-click the <xref:System.Windows.Forms.Button> control, each click will be processed separately; that is, the control does not support the double-click event.</span></span>  
  
### <a name="to-respond-to-a-button-click"></a><span data-ttu-id="8d64c-108">Yanıt için bir düğmeye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="8d64c-108">To respond to a button click</span></span>  
  
-   <span data-ttu-id="8d64c-109">Düğmenin içinde `Click` <xref:System.EventHandler> çalıştırmak için kod yazma.</span><span class="sxs-lookup"><span data-stu-id="8d64c-109">In the button's `Click` <xref:System.EventHandler> write the code to run.</span></span> <span data-ttu-id="8d64c-110">`Button1_Click`denetime bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d64c-110">`Button1_Click` must be bound to the control.</span></span> <span data-ttu-id="8d64c-111">Daha fazla bilgi için bkz: [nasıl yapılır: olay işleyicileri oluşturma çalıştırma süresi için Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8d64c-111">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8d64c-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8d64c-112">See Also</span></span>  
 [<span data-ttu-id="8d64c-113">Düğme Kontrolüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8d64c-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="8d64c-114">Windows Forms Düğme Kontrolü Seçme Yolları</span><span class="sxs-lookup"><span data-stu-id="8d64c-114">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="8d64c-115">Düğme Kontrolü</span><span class="sxs-lookup"><span data-stu-id="8d64c-115">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
