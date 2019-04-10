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
ms.openlocfilehash: 9adcbeb29ca7d3d9bad1ad9cdb6279d826af1f6b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227801"
---
# <a name="how-to-add-panels-to-a-statusbar-control"></a><span data-ttu-id="f4cd2-102">Nasıl yapılır: Bir StatusBar Denetimine Panel Ekleme</span><span class="sxs-lookup"><span data-stu-id="f4cd2-102">How to: Add Panels to a StatusBar Control</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="f4cd2-103"><xref:System.Windows.Forms.StatusStrip> Ve <xref:System.Windows.Forms.ToolStripStatusLabel> denetimleri değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetler; ancak, <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimleri korunur geriye dönük uyumluluk ve gelecekte kullanım için varsa, ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="f4cd2-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="f4cd2-104">Programlanabilir alanı içinde bir [StatusBar denetimine](statusbar-control-windows-forms.md) denetimi oluşur örneklerini <xref:System.Windows.Forms.StatusBarPanel> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f4cd2-104">The programmable area within a [StatusBar Control](statusbar-control-windows-forms.md) control consists of instances of the <xref:System.Windows.Forms.StatusBarPanel> class.</span></span> <span data-ttu-id="f4cd2-105">Bu eklemeler aracılığıyla eklenen <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f4cd2-105">These are added through additions to the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> class.</span></span>  
  
### <a name="to-add-panels-to-a-status-bar"></a><span data-ttu-id="f4cd2-106">Durum çubuğu için panel eklemek için</span><span class="sxs-lookup"><span data-stu-id="f4cd2-106">To add panels to a status bar</span></span>  
  
1.  <span data-ttu-id="f4cd2-107">Bir yordamda ekleyerek durum çubuğu panellerinin oluşturma <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span><span class="sxs-lookup"><span data-stu-id="f4cd2-107">In a procedure, create status-bar panels by adding them to the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span> <span data-ttu-id="f4cd2-108">Kendi dizini kullanılarak tek tek bölmeleri geçtiğini özellik ayarları belirtmek <xref:System.Windows.Forms.StatusBar.Panels%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f4cd2-108">Specify property settings for individual panels by using its index passed through the <xref:System.Windows.Forms.StatusBar.Panels%2A> property.</span></span>  
  
     <span data-ttu-id="f4cd2-109">Aşağıdaki kod örneğinde yolunu ayarlamak için simgenin konumunu **Belgelerim** klasör.</span><span class="sxs-lookup"><span data-stu-id="f4cd2-109">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="f4cd2-110">Bu konum, Windows işletim sistemi çalıştırılan bilgisayarların çoğu bu klasör içerdiğini varsayar çünkü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f4cd2-110">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="f4cd2-111">Bu konumu seçme, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeylerine sahip kullanıcılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4cd2-111">Choosing this location also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="f4cd2-112">Aşağıdaki örnek bir formla gerektiren bir <xref:System.Windows.Forms.StatusBar> denetim zaten eklendi.</span><span class="sxs-lookup"><span data-stu-id="f4cd2-112">The following example requires a form with a <xref:System.Windows.Forms.StatusBar> control already added.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f4cd2-113"><xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> Sıfır tabanlı bir koleksiyon olduğundan kod buna göre devam etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="f4cd2-113">The <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> is a zero-based collection, so code should proceed accordingly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f4cd2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4cd2-114">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="f4cd2-115">Koleksiyon Düzenleyicisi iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="f4cd2-115">Collection Editor Dialog Box</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/xc4yyekt(v=vs.100))
- [<span data-ttu-id="f4cd2-116">Nasıl yapılır: Durum Çubuğu Panellerinin Boyutunu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="f4cd2-116">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)
- [<span data-ttu-id="f4cd2-117">İzlenecek yol: Çalışma Zamanında Durum Çubuğu Bilgilerini Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="f4cd2-117">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)
- [<span data-ttu-id="f4cd2-118">Nasıl yapılır: Windows Forms StatusBar Denetiminde Hangi Panele Tıklandığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="f4cd2-118">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [<span data-ttu-id="f4cd2-119">StatusBar Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f4cd2-119">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
