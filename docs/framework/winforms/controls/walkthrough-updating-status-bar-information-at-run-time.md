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
ms.openlocfilehash: 670746a1b964a85bc5136d976d831c6848466797
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930979"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a><span data-ttu-id="7e0a8-102">İzlenecek yol: Çalışma Zamanında Durum Çubuğu Bilgilerini Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="7e0a8-102">Walkthrough: Updating Status Bar Information at Run Time</span></span>
> [!IMPORTANT]
> <span data-ttu-id="7e0a8-103"><xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel> Ve denetimleri, vedenetimlerine<xref:System.Windows.Forms.StatusBarPanel> işlevsellik ekler ve bunları ekler; ancak, ve denetimleri hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.ToolStripStatusLabel> 'yu.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="7e0a8-104">Genellikle, bir program, uygulama durumu veya diğer kullanıcı etkileşimlerine bağlı olarak durum çubuğu panellerinin içeriğini çalışma zamanında dinamik olarak güncelleştirmeniz için çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-104">Often, a program will call for you to update the contents of status bar panels dynamically at run time, based on changes to application state or other user interaction.</span></span> <span data-ttu-id="7e0a8-105">Bu, Caps Lock, NUM LOCK veya SCROLL LOCK gibi anahtarların etkinleştirildiğini veya tarih ya da saatin uygun bir başvuru olarak sağlanması için kullanıcılara işaret etmenin yaygın bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-105">This is a common way to signal users that keys such as the CAPS LOCK, NUM LOCK, or SCROLL LOCK are enabled, or to provide the date or a clock as a convenient reference.</span></span>  
  
 <span data-ttu-id="7e0a8-106">Aşağıdaki örnekte, bir saati barındırmak için <xref:System.Windows.Forms.StatusBarPanel> sınıfının bir örneğini kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-106">In the following example, you will use an instance of the <xref:System.Windows.Forms.StatusBarPanel> class to host a clock.</span></span>  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a><span data-ttu-id="7e0a8-107">Durum çubuğunu güncelleştirmeye hazırlanıyor</span><span class="sxs-lookup"><span data-stu-id="7e0a8-107">To get the status bar ready for updating</span></span>  
  
1. <span data-ttu-id="7e0a8-108">Yeni bir Windows formu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-108">Create a new Windows form.</span></span>  
  
2. <span data-ttu-id="7e0a8-109">Formunuza bir <xref:System.Windows.Forms.StatusBar> denetim ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-109">Add a <xref:System.Windows.Forms.StatusBar> control to your form.</span></span> <span data-ttu-id="7e0a8-110">Ayrıntılar için bkz [. nasıl yapılır: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-110">For details, see [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
3. <span data-ttu-id="7e0a8-111"><xref:System.Windows.Forms.StatusBar> Denetimi bir durum çubuğu paneli ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-111">Add a status bar panel to your <xref:System.Windows.Forms.StatusBar> control.</span></span> <span data-ttu-id="7e0a8-112">Ayrıntılar için bkz [. nasıl yapılır: Bir StatusBar denetimine](how-to-add-panels-to-a-statusbar-control.md)panel ekleme.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-112">For details, see [How to: Add Panels to a StatusBar Control](how-to-add-panels-to-a-statusbar-control.md).</span></span>  
  
4. <span data-ttu-id="7e0a8-113">Formunuza eklediğiniz <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> `true`denetim için özelliğini olarak ayarlayın. <xref:System.Windows.Forms.StatusBar></span><span class="sxs-lookup"><span data-stu-id="7e0a8-113">For the <xref:System.Windows.Forms.StatusBar> control you added to your form, set the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true`.</span></span>  
  
5. <span data-ttu-id="7e0a8-114">Forma bir Windows Forms <xref:System.Windows.Forms.Timer> bileşeni ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-114">Add a Windows Forms <xref:System.Windows.Forms.Timer> component to the form.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7e0a8-115">Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> bileşeni, bir Windows Forms ortamı için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-115">The Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="7e0a8-116">Sunucu ortamı için uygun bir zamanlayıcıya ihtiyacınız varsa bkz. [sunucu tabanlı zamanlayıcılara giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="7e0a8-116">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
6. <span data-ttu-id="7e0a8-117">Ayarlama <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-117">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>  
  
7. <span data-ttu-id="7e0a8-118">Öğesinin özelliğini 30000 olarak ayarlayın. <xref:System.Windows.Forms.Timer> <xref:System.Windows.Forms.Timer.Interval%2A></span><span class="sxs-lookup"><span data-stu-id="7e0a8-118">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> to 30000.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7e0a8-119"><xref:System.Windows.Forms.Timer> Bileşenin özelliği, görüntülenen sürede doğru bir saatin yansıtıldığından emin olmak için 30 saniye (30.000 milisaniye) olarak ayarlanır. <xref:System.Windows.Forms.Timer.Interval%2A></span><span class="sxs-lookup"><span data-stu-id="7e0a8-119">The <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> component is set to 30 seconds (30,000 milliseconds) to ensure that an accurate time is reflected in the time displayed.</span></span>  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a><span data-ttu-id="7e0a8-120">Durum çubuğunu güncelleştirmek üzere zamanlayıcıyı uygulamak için</span><span class="sxs-lookup"><span data-stu-id="7e0a8-120">To implement the timer to update the status bar</span></span>  
  
1. <span data-ttu-id="7e0a8-121">Denetim<xref:System.Windows.Forms.StatusBar> masasını güncelleştirmek için <xref:System.Windows.Forms.Timer> bileşenin olay işleyicisine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-121">Insert the following code into the event handler of the <xref:System.Windows.Forms.Timer> component to update the panel of the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
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
  
     <span data-ttu-id="7e0a8-122">Bu noktada, uygulamayı çalıştırmaya ve durum çubuğu panelinde çalışan saati gözlemlemeye hazırız.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-122">At this point, you are ready to run the application and observe the clock running in the status bar panel.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="7e0a8-123">Uygulamayı test etmek için</span><span class="sxs-lookup"><span data-stu-id="7e0a8-123">To test the application</span></span>  
  
1. <span data-ttu-id="7e0a8-124">Uygulamada hata ayıklayın ve F5 tuşuna basarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-124">Debug the application and press F5 to run it.</span></span> <span data-ttu-id="7e0a8-125">Hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio 'Da hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="7e0a8-125">For details about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7e0a8-126">Durum çubuğunda saatin görünmesi yaklaşık olarak 30 saniye sürer.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-126">It will take approximately 30 seconds for the clock to appear in the status bar.</span></span> <span data-ttu-id="7e0a8-127">Bu, mümkün olan en doğru zamanı almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-127">This is to get the most accurate time possible.</span></span> <span data-ttu-id="7e0a8-128">Tersine, saatin daha erken görünmesini sağlamak için, önceki yordamda 7. adımda ayarladığınız <xref:System.Windows.Forms.Timer.Interval%2A> özelliğin değerini azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-128">Conversely, to make the clock appear sooner, you can reduce the value of the <xref:System.Windows.Forms.Timer.Interval%2A> property you set in step 7 in the previous procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e0a8-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-129">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="7e0a8-130">Nasıl yapılır: Bir StatusBar Denetimine Panel ekleme</span><span class="sxs-lookup"><span data-stu-id="7e0a8-130">How to: Add Panels to a StatusBar Control</span></span>](how-to-add-panels-to-a-statusbar-control.md)
- [<span data-ttu-id="7e0a8-131">Nasıl yapılır: Windows Forms StatusBar denetimindeki panelin tıklandığını belirleme</span><span class="sxs-lookup"><span data-stu-id="7e0a8-131">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [<span data-ttu-id="7e0a8-132">StatusBar Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7e0a8-132">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
