---
title: 'Nasıl yapılır: Durum çubuğu panellerinin boyutunu ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- StatusBar control [Windows Forms], panel size
- status bars [Windows Forms], setting panel size
- panels [Windows Forms], setting size in status bars
ms.assetid: a01bee43-d9eb-4954-84e6-45a93532d08d
ms.openlocfilehash: be1f216af61c1e7b77e84c584dc9d965a97c56b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539668"
---
# <a name="how-to-set-the-size-of-status-bar-panels"></a>Nasıl yapılır: Durum çubuğu panellerinin boyutunu ayarlama
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripStatusLabel> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.StatusBar> denetler; ancak, <xref:System.Windows.Forms.StatusBar> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.  
  
 Her bir örneği <xref:System.Windows.Forms.StatusBarPanel> içinde sınıf bir [StatusBar denetimine](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) birkaç genişliğini belirleyin ve çalışma zamanında yeniden boyutlandırma davranışı dinamik özellikleri denetime sahiptir.  
  
### <a name="to-set-the-size-of-a-panel"></a>Bir panel boyutunu ayarlamak için  
  
1.  Bir yordamda <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>, <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>, ve <xref:System.Windows.Forms.StatusBarPanel.Width%2A> özellikleri (veya herhangi bir alt sıralamadaki) için durum çubuğu kendi dizini kullanılarak panelleri geçtiğini <xref:System.Windows.Forms.StatusBar.Panels%2A> özelliği <xref:System.Windows.Forms.StatusBarPanel> koleksiyonu.  
  
    ```vb  
    Public Sub SetStatusBarPanelSize()  
    ' Create panel and set text property.  
       StatusBar1.Panels.Add("One")  
    ' Set properties of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(0).Width = 200  
    ' Enable the StatusBar control to display panels.  
       StatusBar1.ShowPanels = True  
        End Sub  
    ```  
  
    ```csharp  
    public void SetStatusBarPanelSize()  
    {  
       // Create panel and set text property.  
       statusBar1.Panels.Add("One");  
       // Set properties of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[0].Width = 200;  
       statusBar1.ShowPanels = true;  
    }  
    ```  
  
    ```cpp  
    public:  
       void SetStatusBarPanelSize()  
       {  
          // Create panel and set text property.  
          statusBar1->Panels->Add("One");  
          // Set properties of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[0]->Width = 200;  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [İzlenecek yol: Çalışma zamanında durum çubuğu bilgilerini güncelleştirme](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)
- [Nasıl yapılır: Windows Forms StatusBar denetiminde hangi panele tıklandığını belirleme](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
