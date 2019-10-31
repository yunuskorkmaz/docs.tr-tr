---
title: 'İzlenecek yol: Çalışma Zamanında Durum Çubuğu Bilgilerini Güncelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], updating at run time
- status bars [Windows Forms], refreshing panels
- StatusBar control [Windows Forms], refreshing panels
- panels [Windows Forms], refreshing status bar
ms.assetid: cc2abb06-c082-49f7-a5a3-2fd1bbcb58d1
ms.openlocfilehash: f1d22079dfa3a6452efb74ef57530bb43e059a4a
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197106"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a><span data-ttu-id="cd0d6-102">İzlenecek yol: Çalışma Zamanında Durum Çubuğu Bilgilerini Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="cd0d6-102">Walkthrough: Updating Status Bar Information at Run Time</span></span>
> [!IMPORTANT]
> <span data-ttu-id="cd0d6-103"><xref:System.Windows.Forms.StatusStrip> ve <xref:System.Windows.Forms.ToolStripStatusLabel> denetimleri yerini alır ve <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimlerine işlevsellik ekler; Ancak, <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimleri hem geri uyumluluk hem de gelecekteki kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="cd0d6-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="cd0d6-104">Genellikle, bir program, uygulama durumu veya diğer kullanıcı etkileşimlerine bağlı olarak durum çubuğu panellerinin içeriğini çalışma zamanında dinamik olarak güncelleştirmeniz için çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="cd0d6-104">Often, a program will call for you to update the contents of status bar panels dynamically at run time, based on changes to application state or other user interaction.</span></span> <span data-ttu-id="cd0d6-105">Bu, Caps Lock, NUM LOCK veya SCROLL LOCK gibi anahtarların etkinleştirildiğini veya tarih ya da saatin uygun bir başvuru olarak sağlanması için kullanıcılara işaret etmenin yaygın bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="cd0d6-105">This is a common way to signal users that keys such as the CAPS LOCK, NUM LOCK, or SCROLL LOCK are enabled, or to provide the date or a clock as a convenient reference.</span></span>  
  
 <span data-ttu-id="cd0d6-106">Aşağıdaki örnekte, bir saati barındırmak için <xref:System.Windows.Forms.StatusBarPanel> sınıfının bir örneğini kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="cd0d6-106">In the following example, you will use an instance of the <xref:System.Windows.Forms.StatusBarPanel> class to host a clock.</span></span>  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a><span data-ttu-id="cd0d6-107">Durum çubuğunu güncelleştirmeye hazırlanıyor</span><span class="sxs-lookup"><span data-stu-id="cd0d6-107">To get the status bar ready for updating</span></span>  
  
1. <span data-ttu-id="cd0d6-108">Yeni bir Windows formu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd0d6-108">Create a new Windows form.</span></span>  
  
2. <span data-ttu-id="cd0d6-109">Formunuza <xref:System.Windows.Forms.StatusBar> denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0d6-109">Add a <xref:System.Windows.Forms.StatusBar> control to your form.</span></span> <span data-ttu-id="cd0d6-110">Ayrıntılar için bkz. [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="cd0d6-110">For details, see [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
3. <span data-ttu-id="cd0d6-111"><xref:System.Windows.Forms.StatusBar> denetimine bir durum çubuğu paneli ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0d6-111">Add a status bar panel to your <xref:System.Windows.Forms.StatusBar> control.</span></span> <span data-ttu-id="cd0d6-112">Ayrıntılar için bkz. [nasıl yapılır: bir StatusBar Denetimine Panel ekleme](how-to-add-panels-to-a-statusbar-control.md).</span><span class="sxs-lookup"><span data-stu-id="cd0d6-112">For details, see [How to: Add Panels to a StatusBar Control](how-to-add-panels-to-a-statusbar-control.md).</span></span>  
  
4. <span data-ttu-id="cd0d6-113">Formunuza eklediğiniz <xref:System.Windows.Forms.StatusBar> denetimi için <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cd0d6-113">For the <xref:System.Windows.Forms.StatusBar> control you added to your form, set the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true`.</span></span>  
  
5. <span data-ttu-id="cd0d6-114">Forma bir Windows Forms <xref:System.Windows.Forms.Timer> bileşeni ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0d6-114">Add a Windows Forms <xref:System.Windows.Forms.Timer> component to the form.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cd0d6-115">Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> bileşeni bir Windows Forms ortamı için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cd0d6-115">The Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="cd0d6-116">Sunucu ortamı için uygun bir zamanlayıcıya ihtiyacınız varsa bkz. [sunucu tabanlı zamanlayıcılara giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="cd0d6-116">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
6. <span data-ttu-id="cd0d6-117"><xref:System.Windows.Forms.Timer.Enabled%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cd0d6-117">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>  
  
7. <span data-ttu-id="cd0d6-118"><xref:System.Windows.Forms.Timer> <xref:System.Windows.Forms.Timer.Interval%2A> özelliğini 30000 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cd0d6-118">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> to 30000.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cd0d6-119"><xref:System.Windows.Forms.Timer> bileşenin <xref:System.Windows.Forms.Timer.Interval%2A> özelliği, görüntülenen sürede doğru saatin yansıtıldığından emin olmak için 30 saniye (30.000 milisaniye) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cd0d6-119">The <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> component is set to 30 seconds (30,000 milliseconds) to ensure that an accurate time is reflected in the time displayed.</span></span>  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a><span data-ttu-id="cd0d6-120">Durum çubuğunu güncelleştirmek üzere zamanlayıcıyı uygulamak için</span><span class="sxs-lookup"><span data-stu-id="cd0d6-120">To implement the timer to update the status bar</span></span>  
  
1. <span data-ttu-id="cd0d6-121"><xref:System.Windows.Forms.StatusBar> denetiminin panelini güncelleştirmek için <xref:System.Windows.Forms.Timer> bileşenin olay işleyicisine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0d6-121">Insert the following code into the event handler of the <xref:System.Windows.Forms.Timer> component to update the panel of the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
    ```vb  
    Private Sub Timer1_Tick(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
       StatusBar1.Panels(0).Text = Now.ToShortTimeString  
    End Sub  
    ```  
  
    ```csharp  
    private void timer1_Tick(object sender, System.EventArgs e)  
    {  
       statusBar1.Panels[0].Text = DateTime.Now.ToShortTimeString();  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void timer1_Tick(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        statusBar1->Panels[0]->Text =  
          DateTime::Now.ToShortTimeString();  
      }  
    ```  
  
     <span data-ttu-id="cd0d6-122">Bu noktada, uygulamayı çalıştırmaya ve durum çubuğu panelinde çalışan saati gözlemlemeye hazırız.</span><span class="sxs-lookup"><span data-stu-id="cd0d6-122">At this point, you are ready to run the application and observe the clock running in the status bar panel.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="cd0d6-123">Uygulamayı test etmek için</span><span class="sxs-lookup"><span data-stu-id="cd0d6-123">To test the application</span></span>  
  
1. <span data-ttu-id="cd0d6-124">Uygulamada hata ayıklayın ve F5 tuşuna basarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cd0d6-124">Debug the application and press F5 to run it.</span></span> <span data-ttu-id="cd0d6-125">Hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio 'Da hata ayıklama](/visualstudio/debugger/debugger-feature-tour).</span><span class="sxs-lookup"><span data-stu-id="cd0d6-125">For details about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugger-feature-tour).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cd0d6-126">Durum çubuğunda saatin görünmesi yaklaşık olarak 30 saniye sürer.</span><span class="sxs-lookup"><span data-stu-id="cd0d6-126">It will take approximately 30 seconds for the clock to appear in the status bar.</span></span> <span data-ttu-id="cd0d6-127">Bu, mümkün olan en doğru zamanı almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cd0d6-127">This is to get the most accurate time possible.</span></span> <span data-ttu-id="cd0d6-128">Tersine, saatin daha önce görünmesi için, önceki yordamda 7. adımda ayarladığınız <xref:System.Windows.Forms.Timer.Interval%2A> özelliğinin değerini azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd0d6-128">Conversely, to make the clock appear sooner, you can reduce the value of the <xref:System.Windows.Forms.Timer.Interval%2A> property you set in step 7 in the previous procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd0d6-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd0d6-129">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="cd0d6-130">Nasıl yapılır: Bir StatusBar Denetimine Panel Ekleme</span><span class="sxs-lookup"><span data-stu-id="cd0d6-130">How to: Add Panels to a StatusBar Control</span></span>](how-to-add-panels-to-a-statusbar-control.md)
- [<span data-ttu-id="cd0d6-131">Nasıl yapılır: Windows Forms StatusBar Denetiminde Hangi Panele Tıklandığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="cd0d6-131">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [<span data-ttu-id="cd0d6-132">StatusBar Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cd0d6-132">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
