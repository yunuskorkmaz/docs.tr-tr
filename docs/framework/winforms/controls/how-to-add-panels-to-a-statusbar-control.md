---
title: 'Nasıl yapılır: Bir StatusBar Denetimine Panel Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- panels [Windows Forms], status bars
- status bars [Windows Forms], adding panels
- StatusBar control [Windows Forms], adding panels
ms.assetid: 835e3902-288c-4c38-9d69-0696d8695009
ms.openlocfilehash: 386c8cae425c458ddf4c446a454ae4213761e651
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142205"
---
# <a name="how-to-add-panels-to-a-statusbar-control"></a>Nasıl yapılır: Bir StatusBar Denetimine Panel Ekleme
> [!IMPORTANT]
> Ve <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.ToolStripStatusLabel> denetimleri değiştirin ve <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel> işlevsellik ekleyin ve denetimleri; ancak, <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimler, isterseniz, hem geriye dönük uyumluluk hem de gelecekteki kullanım için korunur.  
  
 [StatusBar Denetimi](statusbar-control-windows-forms.md) denetimi içindeki programlanabilir alan <xref:System.Windows.Forms.StatusBarPanel> sınıfın örneklerinden oluşur. Bunlar <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> sınıfa eklemeler yoluyla eklenir.  
  
### <a name="to-add-panels-to-a-status-bar"></a>Durum çubuğuna panel eklemek için  
  
1. Bir yordamda, durum çubuğu panelleri oluşturmak <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>için . Özellikten geçen dizinini kullanarak tek <xref:System.Windows.Forms.StatusBar.Panels%2A> tek paneller için özellik ayarlarını belirtin.  
  
     Aşağıdaki kod örneğinde, simgenin konumu için ayarlanan yol **Belgelerim** klasörüdür. Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu klasörü içereceğini varsayabileceğiniziçin bu konum kullanılır. Bu konumun seçilmesi, en az sistem erişim düzeyine sahip kullanıcıların uygulamayı güvenli bir şekilde çalıştırmasına da olanak tanır. Aşağıdaki örnek, zaten eklenen <xref:System.Windows.Forms.StatusBar> bir denetime sahip bir form gerektirir.  
  
    > [!NOTE]
    > Sıfır <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> tabanlı bir koleksiyondur, bu nedenle kod buna göre hareket etmelidir.  
  
    ```vb  
    Public Sub CreateStatusBarPanels()  
    ' Create panels and set text property.  
       StatusBar1.Panels.Add("One")  
       StatusBar1.Panels.Add("Two")  
       StatusBar1.Panels.Add("Three")  
    ' Set properties of StatusBar panels.  
    ' Set AutoSize property of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(1).AutoSize = StatusBarPanelAutoSize.Contents  
       StatusBar1.Panels(2).AutoSize = StatusBarPanelAutoSize.Contents  
    ' Set BorderStyle property of panels.  
       StatusBar1.Panels(0).BorderStyle = StatusBarPanelBorderStyle.Raised  
       StatusBar1.Panels(1).BorderStyle = StatusBarPanelBorderStyle.Sunken  
       StatusBar1.Panels(2).BorderStyle = StatusBarPanelBorderStyle.Raised  
    ' Set Icon property of third panel. You should replace the bolded  
    ' icon in the sample below with an icon of your own choosing.  
       StatusBar1.Panels(2).Icon = New _
       System.Drawing.Icon(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Icon.ico")  
       StatusBar1.ShowPanels = True  
    End Sub  
    ```  
  
    ```csharp  
    public void CreateStatusBarPanels()  
    {  
       // Create panels and set text property.  
       statusBar1.Panels.Add("One");  
       statusBar1.Panels.Add("Two");  
       statusBar1.Panels.Add("Three");  
       // Set properties of StatusBar panels.  
       // Set AutoSize property of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[1].AutoSize = StatusBarPanelAutoSize.Contents;  
       statusBar1.Panels[2].AutoSize = StatusBarPanelAutoSize.Contents;  
       // Set BorderStyle property of panels.  
       statusBar1.Panels[0].BorderStyle =  
          StatusBarPanelBorderStyle.Raised;  
       statusBar1.Panels[1].BorderStyle = StatusBarPanelBorderStyle.Sunken;  
       statusBar1.Panels[2].BorderStyle = StatusBarPanelBorderStyle.Raised;  
       // Set Icon property of third panel. You should replace the bolded  
       // icon in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       statusBar1.Panels[2].Icon =
          new System.Drawing.Icon (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Icon.ico");  
       statusBar1.ShowPanels = true;  
    }  
    ```  
  
    ```cpp  
    public:  
       void CreateStatusBarPanels()  
       {  
          // Create panels and set text property.  
          statusBar1->Panels->Add("One");  
          statusBar1->Panels->Add("Two");  
          statusBar1->Panels->Add("Three");  
          // Set properties of StatusBar panels.  
          // Set AutoSize property of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[1]->AutoSize =  
             StatusBarPanelAutoSize::Contents;  
          statusBar1->Panels[2]->AutoSize =  
             StatusBarPanelAutoSize::Contents;  
          // Set BorderStyle property of panels.  
          statusBar1->Panels[0]->BorderStyle =  
             StatusBarPanelBorderStyle::Raised;  
          statusBar1->Panels[1]->BorderStyle =  
             StatusBarPanelBorderStyle::Sunken;  
          statusBar1->Panels[2]->BorderStyle =  
             StatusBarPanelBorderStyle::Raised;  
          // Set Icon property of third panel.  
          // You should replace the bolded image
          // in the sample below with an icon of your own choosing.  
          statusBar1->Panels[2]->Icon =  
             gcnew System::Drawing::Icon(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Icon.ico"));  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Koleksiyon Düzenleyicisi İletişim Kutusu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/xc4yyekt(v=vs.100))
- [Nasıl yapılır: Durum Çubuğu Panellerinin Boyutunu Ayarlama](how-to-set-the-size-of-status-bar-panels.md)
- [İzlenecek yol: Çalışma Zamanında Durum Çubuğu Bilgilerini Güncelleştirme](walkthrough-updating-status-bar-information-at-run-time.md)
- [Nasıl yapılır: Windows Forms StatusBar Denetiminde Hangi Panele Tıklandığını Belirleme](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar Denetimine Genel Bakış](statusbar-control-overview-windows-forms.md)
