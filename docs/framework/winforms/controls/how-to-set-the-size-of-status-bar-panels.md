---
title: 'Nasıl yapılır: Durum Çubuğu Panellerinin Boyutunu Ayarlama'
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
ms.openlocfilehash: 4ba0f7f02b548a5d9ea1a99605a668f449b3e4a9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923623"
---
# <a name="how-to-set-the-size-of-status-bar-panels"></a>Nasıl yapılır: Durum Çubuğu Panellerinin Boyutunu Ayarlama
> [!NOTE]
> Denetim yerini alır ve <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBar> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.ToolStripStatusLabel>  
  
 Bir [StatusBar denetim](statusbar-control-windows-forms.md) denetimindeki <xref:System.Windows.Forms.StatusBarPanel> sınıfın her örneği, çalışma zamanında genişliğini ve yeniden boyutlandırma davranışını tespit eden bazı dinamik özelliklere sahiptir.  
  
### <a name="to-set-the-size-of-a-panel"></a>Bölmenin boyutunu ayarlamak için  
  
1. Bir yordamda <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>,, <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>, ve <xref:System.Windows.Forms.StatusBarPanel.Width%2A> özelliklerini (veya herhangi bir alt kümeyi) <xref:System.Windows.Forms.StatusBarPanel> koleksiyonun <xref:System.Windows.Forms.StatusBar.Panels%2A> özelliği aracılığıyla geçirilen dizinini kullanarak durum çubuğu panelleri için ayarlayın.  
  
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
- [İzlenecek yol: Çalışma zamanında durum çubuğu bilgilerini güncelleştirme](walkthrough-updating-status-bar-information-at-run-time.md)
- [Nasıl yapılır: Windows Forms StatusBar denetimindeki panelin tıklandığını belirleme](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar Denetimine Genel Bakış](statusbar-control-overview-windows-forms.md)
