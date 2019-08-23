---
title: 'Nasıl yapılır: Windows Forms StatusBar Denetiminde Hangi Panele Tıklandığını Belirleme'
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
ms.openlocfilehash: 6229d8965949641105cd0e9708474c3249d52d1d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965715"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a><span data-ttu-id="3e50a-102">Nasıl yapılır: Windows Forms StatusBar Denetiminde Hangi Panele Tıklandığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="3e50a-102">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>
> [!IMPORTANT]
> <span data-ttu-id="3e50a-103"><xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel> Ve denetimleri, vedenetimlerine<xref:System.Windows.Forms.StatusBarPanel> işlevsellik ekler ve bunları ekler; ancak, ve denetimleri hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.ToolStripStatusLabel> 'yu.</span><span class="sxs-lookup"><span data-stu-id="3e50a-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="3e50a-104">[Durum denetimi](statusbar-control-windows-forms.md) denetimini Kullanıcı tıklamalarına yanıt verecek şekilde programlamak için <xref:System.Windows.Forms.StatusBar.PanelClick> olay içinde bir Case ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e50a-104">To program the [StatusBar Control](statusbar-control-windows-forms.md) control to respond to user clicks, use a case statement within the <xref:System.Windows.Forms.StatusBar.PanelClick> event.</span></span> <span data-ttu-id="3e50a-105">Olay, tıklanan <xref:System.Windows.Forms.StatusBarPanel>bir başvuruyu içeren bir bağımsız değişken (panel bağımsız değişkeni) içerir.</span><span class="sxs-lookup"><span data-stu-id="3e50a-105">The event contains an argument (the panel argument), which contains a reference to the clicked <xref:System.Windows.Forms.StatusBarPanel>.</span></span> <span data-ttu-id="3e50a-106">Bu başvuruyu kullanarak, tıklanan panelin dizinini ve programla buna uygun olarak bir program belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e50a-106">Using this reference, you can determine the index of the clicked panel, and program accordingly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e50a-107">Denetimin özelliğinin olarak`true`ayarlandığından emin olun. <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> <xref:System.Windows.Forms.StatusBar></span><span class="sxs-lookup"><span data-stu-id="3e50a-107">Ensure that the <xref:System.Windows.Forms.StatusBar> control's <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property is set to `true`.</span></span>  
  
### <a name="to-determine-which-panel-was-clicked"></a><span data-ttu-id="3e50a-108">Hangi panelin tıklandığını belirleme</span><span class="sxs-lookup"><span data-stu-id="3e50a-108">To determine which panel was clicked</span></span>  
  
1. <span data-ttu-id="3e50a-109">`switch case` `Select Case` C# C++Olay işleyicisinde, olay bağımsız değişkenlerinde tıklatılan panelin dizinini inceleyerek hangi panelin tıklandığını belirleyen bir (Visual Basic) veya (görsel veya görsel) ifadesini kullanın. <xref:System.Windows.Forms.StatusBar.PanelClick></span><span class="sxs-lookup"><span data-stu-id="3e50a-109">In the <xref:System.Windows.Forms.StatusBar.PanelClick> event handler, use a `Select Case` (in Visual Basic) or `switch case` (Visual C# or Visual C++) statement to determine which panel was clicked by examining the index of the clicked panel in the event arguments.</span></span>  
  
     <span data-ttu-id="3e50a-110">Aşağıdaki kod örneği <xref:System.Windows.Forms.StatusBar> , bir `StatusBar1`denetim,, ve iki <xref:System.Windows.Forms.StatusBarPanel> nesne `StatusBarPanel1` ve `StatusBarPanel2`için varlık gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3e50a-110">The following code example requires the presence, on the form, of a <xref:System.Windows.Forms.StatusBar> control, `StatusBar1`, and two <xref:System.Windows.Forms.StatusBarPanel> objects, `StatusBarPanel1` and `StatusBarPanel2`.</span></span>  
  
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
  
     <span data-ttu-id="3e50a-111">(Görsel C#, görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="3e50a-111">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3e50a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e50a-112">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="3e50a-113">Nasıl yapılır: Durum çubuğu panellerinin boyutunu ayarlama</span><span class="sxs-lookup"><span data-stu-id="3e50a-113">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)
- [<span data-ttu-id="3e50a-114">İzlenecek yol: Çalışma zamanında durum çubuğu bilgilerini güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="3e50a-114">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)
- [<span data-ttu-id="3e50a-115">StatusBar Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3e50a-115">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
