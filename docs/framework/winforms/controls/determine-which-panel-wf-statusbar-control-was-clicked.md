---
title: StatusBar denetiminde hangi panelin tıklandığını belirleme
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
ms.openlocfilehash: 94619f8bd426a42e5dafa0db99880e20d24f9963
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746016"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>Nasıl yapılır: Windows Forms StatusBar Denetiminde Hangi Panele Tıklandığını Belirleme
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusStrip> ve <xref:System.Windows.Forms.ToolStripStatusLabel> denetimleri yerini alır ve <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimlerine işlevsellik ekler; Ancak, <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimleri hem geri uyumluluk hem de gelecekteki kullanım için korunur.  
  
 [Durum denetimi](statusbar-control-windows-forms.md) denetimini Kullanıcı tıklamalarına yanıt verecek şekilde programlamak için <xref:System.Windows.Forms.StatusBar.PanelClick> olayı içinde bir Case ifadesini kullanın. Olay, tıklanan <xref:System.Windows.Forms.StatusBarPanel>bir başvuru içeren bir bağımsız değişken (panel bağımsız değişkeni) içerir. Bu başvuruyu kullanarak, tıklanan panelin dizinini ve programla buna uygun olarak bir program belirleyebilirsiniz.  
  
> [!NOTE]
> <xref:System.Windows.Forms.StatusBar> denetiminin <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğinin `true`olarak ayarlandığından emin olun.  
  
### <a name="to-determine-which-panel-was-clicked"></a>Hangi panelin tıklandığını belirleme  
  
1. <xref:System.Windows.Forms.StatusBar.PanelClick> olay işleyicisinde, olay bağımsız değişkenlerinde tıklatılan panelin dizinini inceleyerek hangi panelin tıklandığını belirleyen bir C# `Select Case` ( C++Visual Basic) veya `switch case` (Visual veya görsel) ifadesini kullanın.  
  
     Aşağıdaki kod örneği, bir <xref:System.Windows.Forms.StatusBar> denetimi, `StatusBar1`ve iki <xref:System.Windows.Forms.StatusBarPanel> nesne, `StatusBarPanel1` ve `StatusBarPanel2`için varlık gerektirir.  
  
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
  
     (Görsel C#, görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Nasıl yapılır: Durum Çubuğu Panellerinin Boyutunu Ayarlama](how-to-set-the-size-of-status-bar-panels.md)
- [İzlenecek yol: Çalışma Zamanında Durum Çubuğu Bilgilerini Güncelleştirme](walkthrough-updating-status-bar-information-at-run-time.md)
- [StatusBar Denetimine Genel Bakış](statusbar-control-overview-windows-forms.md)
