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
ms.openlocfilehash: 27d65c07f0a6ec4a25d057e2c16a8b59933bb8fd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925107"
---
# <a name="how-to-add-panels-to-a-statusbar-control"></a>Nasıl yapılır: Bir StatusBar Denetimine Panel Ekleme
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel> Ve denetimleri, vedenetimlerine<xref:System.Windows.Forms.StatusBarPanel> işlevsellik ekler ve bunları ekler; ancak, ve denetimleri hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.ToolStripStatusLabel> 'yu.  
  
 Bir [StatusBar denetim](statusbar-control-windows-forms.md) denetimindeki programlanabilir alan, <xref:System.Windows.Forms.StatusBarPanel> sınıfının örneklerinden oluşur. Bunlar, <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> sınıfa eklemeler aracılığıyla eklenir.  
  
### <a name="to-add-panels-to-a-status-bar"></a>Bir durum çubuğuna panel eklemek için  
  
1. Bir yordamda, ' ye <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>ekleyerek durum çubuğu bölmeleri oluşturun. <xref:System.Windows.Forms.StatusBar.Panels%2A> Özelliği aracılığıyla geçirilen dizinini kullanarak ayrı panellerin özellik ayarlarını belirtin.  
  
     Aşağıdaki kod örneğinde, simgenin konumu için ayarlanan yol Belgelerim klasörüdür. Bu konum, Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu klasörü içerdiğini varsaydığı için kullanılır. Bu konumun seçilmesi, en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenle çalıştırmasına olanak tanır. Aşağıdaki örnek, bir <xref:System.Windows.Forms.StatusBar> denetimin zaten eklenmiş olduğu bir form gerektirir.  
  
    > [!NOTE]
    > , <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> Sıfır tabanlı bir koleksiyondur, bu nedenle kod buna uygun şekilde devam etmelidir.  
  
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
- [Koleksiyon Düzenleyicisi Iletişim kutusu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/xc4yyekt(v=vs.100))
- [Nasıl yapılır: Durum çubuğu panellerinin boyutunu ayarlama](how-to-set-the-size-of-status-bar-panels.md)
- [İzlenecek yol: Çalışma zamanında durum çubuğu bilgilerini güncelleştirme](walkthrough-updating-status-bar-information-at-run-time.md)
- [Nasıl yapılır: Windows Forms StatusBar denetimindeki panelin tıklandığını belirleme](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar Denetimine Genel Bakış](statusbar-control-overview-windows-forms.md)
