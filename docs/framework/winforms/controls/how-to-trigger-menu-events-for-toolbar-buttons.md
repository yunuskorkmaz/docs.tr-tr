---
title: 'Nasıl yapılır: Araç çubuğu düğmeleri için menü olaylarını tetikleme'
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
ms.openlocfilehash: 6459c61e49a49001d490d5213f23ff652d4a1939
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609596"
---
# <a name="how-to-trigger-menu-events-for-toolbar-buttons"></a><span data-ttu-id="d3ba7-102">Nasıl yapılır: Araç çubuğu düğmeleri için menü olaylarını tetikleme</span><span class="sxs-lookup"><span data-stu-id="d3ba7-102">How to: Trigger Menu Events for Toolbar Buttons</span></span>
> [!NOTE]
>  <span data-ttu-id="d3ba7-103"><xref:System.Windows.Forms.ToolStrip> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.ToolBar> denetler; ancak, <xref:System.Windows.Forms.ToolBar> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="d3ba7-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="d3ba7-104">Windows Form özelliklerinizi bir <xref:System.Windows.Forms.ToolBar> denetimi araç çubuğu düğmeleri ile hangi kullanıcı düğmesi bilmek isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="d3ba7-104">If your Windows Form features a <xref:System.Windows.Forms.ToolBar> control with toolbar buttons, you will want to know which button the user clicks.</span></span>  
  
 <span data-ttu-id="d3ba7-105">Üzerinde <xref:System.Windows.Forms.ToolBar.ButtonClick> olayı <xref:System.Windows.Forms.ToolBar> denetimi değerlendirme <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> özelliği <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d3ba7-105">On the <xref:System.Windows.Forms.ToolBar.ButtonClick> event of the <xref:System.Windows.Forms.ToolBar> control, you can evaluate the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> property of the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> class.</span></span> <span data-ttu-id="d3ba7-106">Aşağıdaki örnekte, hangi düğmesine tıklandığını belirten bir ileti kutusu gösterilir.</span><span class="sxs-lookup"><span data-stu-id="d3ba7-106">In the example below, a message box is shown, indicating which button was clicked.</span></span> <span data-ttu-id="d3ba7-107">Ayrıntılar için bkz <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="d3ba7-107">For details, see <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="d3ba7-108">Aşağıdaki örnekte bir <xref:System.Windows.Forms.ToolBar> Windows Form denetimi eklendi.</span><span class="sxs-lookup"><span data-stu-id="d3ba7-108">The example below assumes a <xref:System.Windows.Forms.ToolBar> control has been added to a Windows Form.</span></span>  
  
### <a name="to-handle-the-click-event-on-a-toolbar"></a><span data-ttu-id="d3ba7-109">Araç çubuğundaki Click olayını işlemek için</span><span class="sxs-lookup"><span data-stu-id="d3ba7-109">To handle the Click event on a toolbar</span></span>  
  
1.  <span data-ttu-id="d3ba7-110">Bir yordamda araç çubuğu düğmelerine ekleme <xref:System.Windows.Forms.ToolBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d3ba7-110">In a procedure, add toolbar buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
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
  
2.  <span data-ttu-id="d3ba7-111">İçin bir olay işleyicisi ekleme <xref:System.Windows.Forms.ToolBar> denetimin <xref:System.Windows.Forms.ToolBar.ButtonClick> olay.</span><span class="sxs-lookup"><span data-stu-id="d3ba7-111">Add an event handler for the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ButtonClick> event.</span></span> <span data-ttu-id="d3ba7-112">Kullanım deyimi değiştirme ve <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> tıklandığını araç çubuğu düğmesi belirlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="d3ba7-112">Use a case switching statement and the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> class to determine the toolbar button that was clicked.</span></span> <span data-ttu-id="d3ba7-113">Bunu temel alarak, uygun bir ileti kutusu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d3ba7-113">Based on this, show an appropriate message box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d3ba7-114">Bir ileti kutusu yalnızca, bu örnekte bir yer tutucu olarak kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="d3ba7-114">A message box is being used solely as a placeholder in this example.</span></span> <span data-ttu-id="d3ba7-115">Araç çubuğu düğmeleri tıklatıldığında yürütülecek diğer kod eklemekten çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="d3ba7-115">Feel free to add other code to execute when the toolbar buttons are clicked.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d3ba7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3ba7-116">See also</span></span>
- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="d3ba7-117">Nasıl yapılır: Bir ToolBar denetimine düğme ekleme</span><span class="sxs-lookup"><span data-stu-id="d3ba7-117">How to: Add Buttons to a ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)
- [<span data-ttu-id="d3ba7-118">Nasıl yapılır: ToolBar düğmesi için simge tanımlama</span><span class="sxs-lookup"><span data-stu-id="d3ba7-118">How to: Define an Icon for a ToolBar Button</span></span>](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)
- [<span data-ttu-id="d3ba7-119">ToolBar Denetimi</span><span class="sxs-lookup"><span data-stu-id="d3ba7-119">ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
