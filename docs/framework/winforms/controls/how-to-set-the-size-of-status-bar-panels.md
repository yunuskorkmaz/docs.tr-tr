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
ms.openlocfilehash: c6c9d6570e9b5c2f6d4eee0262c3d90e29e4b493
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131068"
---
# <a name="how-to-set-the-size-of-status-bar-panels"></a>Nasıl yapılır: Durum Çubuğu Panellerinin Boyutunu Ayarlama
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripStatusLabel> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.StatusBar> denetler; ancak, <xref:System.Windows.Forms.StatusBar> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.  
  
 Her bir örneği <xref:System.Windows.Forms.StatusBarPanel> içinde sınıf bir [StatusBar denetimine](statusbar-control-windows-forms.md) birkaç genişliğini belirleyin ve çalışma zamanında yeniden boyutlandırma davranışı dinamik özellikleri denetime sahiptir.  
  
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
- [İzlenecek yol: Çalışma Zamanında Durum Çubuğu Bilgilerini Güncelleştirme](walkthrough-updating-status-bar-information-at-run-time.md)
- [Nasıl yapılır: Windows Forms StatusBar Denetiminde Hangi Panele Tıklandığını Belirleme](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar Denetimine Genel Bakış](statusbar-control-overview-windows-forms.md)
