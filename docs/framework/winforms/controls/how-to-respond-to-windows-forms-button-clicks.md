---
title: Düğme Tıklamalarına Yanıt Verme
description: Windows Forms düğme tıklamalarına nasıl yanıt verileceğini öğrenin. Windows Forms düğme denetiminin en temel kullanımı, düğme tıklandığında bazı kodları çalıştırkullanmaktır.
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
ms.openlocfilehash: 5c458d56dbd6f1cab8e88bdbb86ede958367e5c4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619734"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a><span data-ttu-id="7311e-104">Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="7311e-104">How to: Respond to Windows Forms Button Clicks</span></span>
<span data-ttu-id="7311e-105">Windows Forms denetiminin en temel kullanımı, <xref:System.Windows.Forms.Button> düğme tıklandığında bazı kodları çalıştırkullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="7311e-105">The most basic use of a Windows Forms <xref:System.Windows.Forms.Button> control is to run some code when the button is clicked.</span></span>  
  
 <span data-ttu-id="7311e-106">Bir <xref:System.Windows.Forms.Button> denetime tıkladığınızda <xref:System.Windows.Forms.Control.MouseEnter> ,, ve olayları gibi birçok farklı olay da oluşturulur <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.MouseUp> .</span><span class="sxs-lookup"><span data-stu-id="7311e-106">Clicking a <xref:System.Windows.Forms.Button> control also generates a number of other events, such as the <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, and <xref:System.Windows.Forms.Control.MouseUp> events.</span></span> <span data-ttu-id="7311e-107">Bu ilgili olaylar için olay işleyicileri eklemek istiyorsanız, eylemlerinin çakışmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="7311e-107">If you intend to attach event handlers for these related events, be sure that their actions do not conflict.</span></span> <span data-ttu-id="7311e-108">Örneğin, düğmeye tıkladığınızda kullanıcının bir metin kutusuna girdiği bilgiler temizlenir, fare işaretçisini düğme üzerinde duraklatmak, bu, varolmayan bilgilerin bulunduğu bir araç ipucunu göstermemelidir.</span><span class="sxs-lookup"><span data-stu-id="7311e-108">For example, if clicking the button clears information that the user has typed in a text box, pausing the mouse pointer over the button should not display a tool tip with that now-nonexistent information.</span></span>  
  
 <span data-ttu-id="7311e-109">Kullanıcı denetime çift tıkladenerse <xref:System.Windows.Forms.Button> , her tıklama ayrı olarak işlenir; diğer bir deyişle, denetim çift tıklama olayını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7311e-109">If the user attempts to double-click the <xref:System.Windows.Forms.Button> control, each click will be processed separately; that is, the control does not support the double-click event.</span></span>  
  
### <a name="to-respond-to-a-button-click"></a><span data-ttu-id="7311e-110">Düğme tıklamasına yanıt vermek için</span><span class="sxs-lookup"><span data-stu-id="7311e-110">To respond to a button click</span></span>  
  
- <span data-ttu-id="7311e-111">Düğme, `Click` <xref:System.EventHandler> çalıştırılacak kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="7311e-111">In the button's `Click` <xref:System.EventHandler> write the code to run.</span></span> <span data-ttu-id="7311e-112">`Button1_Click`denetime bağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7311e-112">`Button1_Click` must be bound to the control.</span></span> <span data-ttu-id="7311e-113">Daha fazla bilgi için bkz. [nasıl yapılır: çalışma zamanında olay Işleyicileri oluşturma Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7311e-113">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7311e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7311e-114">See also</span></span>

- [<span data-ttu-id="7311e-115">Düğme Kontrolüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7311e-115">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="7311e-116">Windows Forms Düğme Denetimi Seçmenin Yolları</span><span class="sxs-lookup"><span data-stu-id="7311e-116">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="7311e-117">Düğme Denetimi</span><span class="sxs-lookup"><span data-stu-id="7311e-117">Button Control</span></span>](button-control-windows-forms.md)
