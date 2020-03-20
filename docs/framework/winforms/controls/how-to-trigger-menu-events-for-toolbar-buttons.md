---
title: 'Nasıl yapılır: Araç Çubuğu Düğmeleri için Menü Olaylarını Tetikleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], click event handlers
- ToolBar control [Windows Forms], coding button click events
- toolbars [Windows Forms], click event handlers
ms.assetid: 98374f70-993d-4ca4-89fb-48fea6ce5b45
ms.openlocfilehash: 99db077b41a59fe9263f7283b58b8c31959c7c79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182071"
---
# <a name="how-to-trigger-menu-events-for-toolbar-buttons"></a><span data-ttu-id="d1c36-102">Nasıl yapılır: Araç Çubuğu Düğmeleri için Menü Olaylarını Tetikleme</span><span class="sxs-lookup"><span data-stu-id="d1c36-102">How to: Trigger Menu Events for Toolbar Buttons</span></span>
> [!NOTE]
> <span data-ttu-id="d1c36-103">Denetim, <xref:System.Windows.Forms.ToolStrip> denetimin <xref:System.Windows.Forms.ToolBar> yerini alır ve işlevsellik ekler; ancak, <xref:System.Windows.Forms.ToolBar> isterseniz, denetim hem geriye dönük uyumluluk hem de gelecekteki kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="d1c36-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="d1c36-104">Windows Form'unuzda <xref:System.Windows.Forms.ToolBar> araç çubuğu düğmeleriyle bir denetim varsa, kullanıcının hangi düğmeyi tıklattıklarını bilmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="d1c36-104">If your Windows Form features a <xref:System.Windows.Forms.ToolBar> control with toolbar buttons, you will want to know which button the user clicks.</span></span>  
  
 <span data-ttu-id="d1c36-105">Denetim <xref:System.Windows.Forms.ToolBar.ButtonClick> durumunda, sınıfın özelliğini <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> değerlendirebilirsiniz. <xref:System.Windows.Forms.ToolBar></span><span class="sxs-lookup"><span data-stu-id="d1c36-105">On the <xref:System.Windows.Forms.ToolBar.ButtonClick> event of the <xref:System.Windows.Forms.ToolBar> control, you can evaluate the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> property of the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> class.</span></span> <span data-ttu-id="d1c36-106">Aşağıdaki örnekte, hangi düğmenin tıklandığını belirten bir ileti kutusu gösterilir.</span><span class="sxs-lookup"><span data-stu-id="d1c36-106">In the example below, a message box is shown, indicating which button was clicked.</span></span> <span data-ttu-id="d1c36-107">Ayrıntılar için bkz. <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="d1c36-107">For details, see <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="d1c36-108">Aşağıdaki örnekte, <xref:System.Windows.Forms.ToolBar> windows formuna bir denetim eklendiğini varsayar.</span><span class="sxs-lookup"><span data-stu-id="d1c36-108">The example below assumes a <xref:System.Windows.Forms.ToolBar> control has been added to a Windows Form.</span></span>  
  
### <a name="to-handle-the-click-event-on-a-toolbar"></a><span data-ttu-id="d1c36-109">Araç çubuğundaki Click olayını işlemek için</span><span class="sxs-lookup"><span data-stu-id="d1c36-109">To handle the Click event on a toolbar</span></span>  
  
1. <span data-ttu-id="d1c36-110">Bir yordamda, <xref:System.Windows.Forms.ToolBar> denetime araç çubuğu düğmeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d1c36-110">In a procedure, add toolbar buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
    ```vb  
    Public Sub ToolBarConfig()  
    ' Instantiate the toolbar buttons, set their Text properties  
    ' and add them to the ToolBar control.  
       ToolBar1.Buttons.Add(New ToolBarButton("One"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Two"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Three"))  
    ' Add the event handler delegate.  
       AddHandler ToolBar1.ButtonClick, AddressOf Me.ToolBar1_ButtonClick  
    End Sub  
    ```  
  
    ```csharp  
    public void ToolBarConfig()
    {  
       toolBar1.Buttons.Add(new ToolBarButton("One"));  
       toolBar1.Buttons.Add(new ToolBarButton("Two"));  
       toolBar1.Buttons.Add(new ToolBarButton("Three"));  
  
       toolBar1.ButtonClick +=
          new ToolBarButtonClickEventHandler(this.toolBar1_ButtonClick);  
    }  
    ```  
  
    ```cpp  
    public:  
       void ToolBarConfig()  
       {  
          toolBar1->Buttons->Add(gcnew ToolBarButton("One"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Two"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Three"));  
  
          toolBar1->ButtonClick +=
             gcnew ToolBarButtonClickEventHandler(this,  
             &Form1::toolBar1_ButtonClick);  
       }  
    ```  
  
2. <span data-ttu-id="d1c36-111">Denetimolayı için bir <xref:System.Windows.Forms.ToolBar> olay işleyicisi <xref:System.Windows.Forms.ToolBar.ButtonClick> ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d1c36-111">Add an event handler for the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ButtonClick> event.</span></span> <span data-ttu-id="d1c36-112">Tıklanan araç çubuğu <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> düğmesini belirlemek için büyük/küçük harf anahtarlama deyimini ve sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1c36-112">Use a case switching statement and the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> class to determine the toolbar button that was clicked.</span></span> <span data-ttu-id="d1c36-113">Buna dayanarak, uygun bir ileti kutusu gösterin.</span><span class="sxs-lookup"><span data-stu-id="d1c36-113">Based on this, show an appropriate message box.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d1c36-114">İleti kutusu bu örnekte yalnızca yer tutucu olarak kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="d1c36-114">A message box is being used solely as a placeholder in this example.</span></span> <span data-ttu-id="d1c36-115">Araç çubuğu düğmeleri tıklandığında yürütmek için başka kod eklemekten çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="d1c36-115">Feel free to add other code to execute when the toolbar buttons are clicked.</span></span>  
  
    ```vb  
    Protected Sub ToolBar1_ButtonClick(ByVal sender As Object, _  
    ByVal e As ToolBarButtonClickEventArgs)  
    ' Evaluate the Button property of the ToolBarButtonClickEventArgs  
    ' to determine which button was clicked.  
       Select Case ToolBar1.Buttons.IndexOf(e.Button)  
         Case 0  
           MessageBox.Show("First toolbar button clicked")  
         Case 1  
           MessageBox.Show("Second toolbar button clicked")  
         Case 2  
           MessageBox.Show("Third toolbar button clicked")  
       End Select  
    End Sub  
    ```  
  
    ```csharp  
    protected void toolBar1_ButtonClick(object sender,  
    ToolBarButtonClickEventArgs e)  
    {  
       // Evaluate the Button property of the ToolBarButtonClickEventArgs  
       // to determine which button was clicked.  
       switch (toolBar1.Buttons.IndexOf(e.Button))  
       {  
          case 0 :  
             MessageBox.Show("First toolbar button clicked");  
             break;  
          case 1 :  
             MessageBox.Show("Second toolbar button clicked");  
             break;  
          case 2 :  
             MessageBox.Show("Third toolbar button clicked");  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    protected:  
       void toolBar1_ButtonClick(System::Object ^ sender,  
          ToolBarButtonClickEventArgs ^ e)  
       {  
         // Evaluate the Button property of the ToolBarButtonClickEventArgs  
         // to determine which button was clicked.  
          switch (toolBar1->Buttons->IndexOf(e->Button))  
          {  
             case 0 :  
                MessageBox::Show("First toolbar button clicked");  
                break;  
             case 1 :  
                MessageBox::Show("Second toolbar button clicked");  
                break;  
             case 2 :  
                MessageBox::Show("Third toolbar button clicked");  
                break;  
          }  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d1c36-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1c36-116">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="d1c36-117">Nasıl yapılır: Bir ToolBar Denetimine Düğme Ekleme</span><span class="sxs-lookup"><span data-stu-id="d1c36-117">How to: Add Buttons to a ToolBar Control</span></span>](how-to-add-buttons-to-a-toolbar-control.md)
- [<span data-ttu-id="d1c36-118">Nasıl yapılır: ToolBar Düğmesi için Simge Tanımlama</span><span class="sxs-lookup"><span data-stu-id="d1c36-118">How to: Define an Icon for a ToolBar Button</span></span>](how-to-define-an-icon-for-a-toolbar-button.md)
- [<span data-ttu-id="d1c36-119">ToolBar Denetimi</span><span class="sxs-lookup"><span data-stu-id="d1c36-119">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
