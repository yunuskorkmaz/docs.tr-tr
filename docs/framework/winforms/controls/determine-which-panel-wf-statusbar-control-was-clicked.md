---
title: StatusBar Denetiminde Hangi Panelin Tıklandığını Belirleyin
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], determining panel clicked
- panels [Windows Forms], determining clicked
- StatusBar control [Windows Forms], coding panel click events
- StatusBar control [Windows Forms], determining panel clicked
- PanelClick event [Windows Forms], determining panel clicked
- Panel control [Windows Forms], determining click
ms.assetid: d14c6092-04b2-4a07-8ddf-0dd11277ff5f
ms.openlocfilehash: eb3b10d515ba5b62236594e063ca7f060b34b73e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182358"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a><span data-ttu-id="8cc0e-102">Nasıl yapılır: Windows Forms StatusBar Denetiminde Hangi Panele Tıklandığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="8cc0e-102">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>
> [!IMPORTANT]
> <span data-ttu-id="8cc0e-103">Ve <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.ToolStripStatusLabel> denetimleri değiştirin ve <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel> işlevsellik ekleyin ve denetimleri; ancak, <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimler, isterseniz, hem geriye dönük uyumluluk hem de gelecekteki kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="8cc0e-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="8cc0e-104">Kullanıcı tıklamalarına yanıt vermek için [StatusBar Control](statusbar-control-windows-forms.md) denetimini <xref:System.Windows.Forms.StatusBar.PanelClick> programlamak için olay içinde bir servis talebi bildirimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="8cc0e-104">To program the [StatusBar Control](statusbar-control-windows-forms.md) control to respond to user clicks, use a case statement within the <xref:System.Windows.Forms.StatusBar.PanelClick> event.</span></span> <span data-ttu-id="8cc0e-105">Olay, tıklatılana <xref:System.Windows.Forms.StatusBarPanel>bir başvuru içeren bir bağımsız değişken (panel bağımsız değişkeni) içerir.</span><span class="sxs-lookup"><span data-stu-id="8cc0e-105">The event contains an argument (the panel argument), which contains a reference to the clicked <xref:System.Windows.Forms.StatusBarPanel>.</span></span> <span data-ttu-id="8cc0e-106">Bu başvuruyu kullanarak, tıklanan panelin dizinini belirleyebilir ve buna göre programlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8cc0e-106">Using this reference, you can determine the index of the clicked panel, and program accordingly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8cc0e-107">Denetimin <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğinin '' olarak `true`ayarlandığından emin olun</span><span class="sxs-lookup"><span data-stu-id="8cc0e-107">Ensure that the <xref:System.Windows.Forms.StatusBar> control's <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property is set to `true`.</span></span>  
  
### <a name="to-determine-which-panel-was-clicked"></a><span data-ttu-id="8cc0e-108">Hangi panelin tıklandığını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="8cc0e-108">To determine which panel was clicked</span></span>  
  
1. <span data-ttu-id="8cc0e-109">Olay <xref:System.Windows.Forms.StatusBar.PanelClick> işleyicisinde, olay `Select Case` bağımsız değişkenlerinde `switch case` tıklanan panelin dizinini inceleyerek hangi panelin tıklandığını belirlemek için (Visual Basic'te) veya (Visual C# veya Visual C++) deyimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8cc0e-109">In the <xref:System.Windows.Forms.StatusBar.PanelClick> event handler, use a `Select Case` (in Visual Basic) or `switch case` (Visual C# or Visual C++) statement to determine which panel was clicked by examining the index of the clicked panel in the event arguments.</span></span>  
  
     <span data-ttu-id="8cc0e-110">Aşağıdaki kod örneği, <xref:System.Windows.Forms.StatusBar> bir denetimin `StatusBar1`ve iki <xref:System.Windows.Forms.StatusBarPanel> nesnenin formdaki `StatusBarPanel1` varlığını `StatusBarPanel2`ve .</span><span class="sxs-lookup"><span data-stu-id="8cc0e-110">The following code example requires the presence, on the form, of a <xref:System.Windows.Forms.StatusBar> control, `StatusBar1`, and two <xref:System.Windows.Forms.StatusBarPanel> objects, `StatusBarPanel1` and `StatusBarPanel2`.</span></span>  
  
    ```vb  
    Private Sub StatusBar1_PanelClick(ByVal sender As System.Object, ByVal e As System.Windows.Forms.StatusBarPanelClickEventArgs) Handles StatusBar1.PanelClick  
       Select Case StatusBar1.Panels.IndexOf(e.StatusBarPanel)  
         Case 0  
           MessageBox.Show("You have clicked Panel One.")  
         Case 1  
           MessageBox.Show("You have clicked Panel Two.")  
       End Select  
    End Sub  
    ```  
  
    ```csharp  
    private void statusBar1_PanelClick(object sender,
    System.Windows.Forms.StatusBarPanelClickEventArgs e)  
    {  
       switch (statusBar1.Panels.IndexOf(e.StatusBarPanel))  
       {  
          case 0 :  
             MessageBox.Show("You have clicked Panel One.");  
             break;  
          case 1 :  
             MessageBox.Show("You have clicked Panel Two.");  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void statusBar1_PanelClick(System::Object ^  sender,  
          System::Windows::Forms::StatusBarPanelClickEventArgs ^  e)  
       {  
          switch (statusBar1->Panels->IndexOf(e->StatusBarPanel))  
          {  
             case 0 :  
                MessageBox::Show("You have clicked Panel One.");  
                break;  
             case 1 :  
                MessageBox::Show("You have clicked Panel Two.");  
                break;  
          }  
       }  
    ```  
  
     <span data-ttu-id="8cc0e-111">(Görsel C#, Görsel C++) Olay işleyicisini kaydetmek için aşağıdaki kodu formun oluşturucusuna yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="8cc0e-111">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.statusBar1.PanelClick += new
       System.Windows.Forms.StatusBarPanelClickEventHandler
       (this.statusBar1_PanelClick);  
    ```  
  
    ```cpp  
    this->statusBar1->PanelClick += gcnew  
       System::Windows::Forms::StatusBarPanelClickEventHandler  
       (this, &Form1::statusBar1_PanelClick);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8cc0e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8cc0e-112">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="8cc0e-113">Nasıl yapılır: Durum Çubuğu Panellerinin Boyutunu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="8cc0e-113">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)
- [<span data-ttu-id="8cc0e-114">İzlenecek yol: Çalışma Zamanında Durum Çubuğu Bilgilerini Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="8cc0e-114">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)
- [<span data-ttu-id="8cc0e-115">StatusBar Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8cc0e-115">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
