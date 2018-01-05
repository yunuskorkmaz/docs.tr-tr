---
title: "İzlenecek yol: Tasarım Zamanında Özel Windows Formları Denetimleri Hatalarını Ayıklama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- custom controls [Windows Forms], walkthroughs
- visual editors
- debugging [Visual Studio], Windows Forms
- custom controls [Windows Forms], debugging
- designers
- controls [Windows Forms], debugging
- walkthroughs [Windows Forms], debugging
- design-time debugging
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fd38f6246d44bd24753d9c86a5b0b08819d3db7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-debugging-custom-windows-forms-controls-at-design-time"></a><span data-ttu-id="a2a80-102">İzlenecek yol: Tasarım Zamanında Özel Windows Formları Denetimleri Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a2a80-102">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="a2a80-103">Özel bir denetim oluşturduğunuzda, genellikle bu tasarım zamanı davranışını hata ayıklamak gerekli bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="a2a80-103">When you create a custom control, you will often find it necessary to debug its design-time behavior.</span></span> <span data-ttu-id="a2a80-104">Özel denetim için özel bir tasarımcı yazıyorsanız bu özellikle doğrudur.</span><span class="sxs-lookup"><span data-stu-id="a2a80-104">This is especially true if you are authoring a custom designer for your custom control.</span></span> <span data-ttu-id="a2a80-105">Ayrıntılar için bkz [izlenecek yol: bir Windows Forms denetimi, geçen avantajı, Visual Studio tasarım-zamanı özellikleri oluşturma](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="a2a80-105">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span></span>  
  
 <span data-ttu-id="a2a80-106">Diğer .NET Framework sınıfları debug gibi özel denetimler Visual Studio kullanarak ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2a80-106">You can debug your custom controls using Visual Studio, just as you would debug any other .NET Framework classes.</span></span> <span data-ttu-id="a2a80-107">Özel denetimin kodunu çalıştıran Visual Studio ayrı bir örneğini hata ayıklama farktır</span><span class="sxs-lookup"><span data-stu-id="a2a80-107">The difference is that you will debug a separate instance of Visual Studio that is running your custom control's code</span></span>  
  
 <span data-ttu-id="a2a80-108">Bu örneklerde gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="a2a80-108">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="a2a80-109">Özel denetim barındırmak için bir Windows Forms projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="a2a80-109">Creating a Windows Forms project to host your custom control</span></span>  
  
-   <span data-ttu-id="a2a80-110">Bir denetim kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="a2a80-110">Creating a control library project</span></span>  
  
-   <span data-ttu-id="a2a80-111">Bir özellik için özel denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="a2a80-111">Adding a property to your custom control</span></span>  
  
-   <span data-ttu-id="a2a80-112">Ana bilgisayar formuna özel denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="a2a80-112">Adding your custom control to the host form</span></span>  
  
-   <span data-ttu-id="a2a80-113">Tasarım zamanı hata ayıklama için proje ayarlama</span><span class="sxs-lookup"><span data-stu-id="a2a80-113">Setting up the project for design-time debugging</span></span>  
  
-   <span data-ttu-id="a2a80-114">Özel Denetim tasarım zamanında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="a2a80-114">Debugging your custom control at design time</span></span>  
  
 <span data-ttu-id="a2a80-115">İşiniz bittiğinde, özel bir denetim tasarım zamanı davranışını hata ayıklama için gereken görevleri anlaşılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a2a80-115">When you are finished, you will have an understanding of the tasks necessary for debugging the design-time behavior of a custom control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2a80-116">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="a2a80-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a2a80-117">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="a2a80-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a2a80-118">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="a2a80-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="a2a80-119">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a2a80-119">Creating the Project</span></span>  
 <span data-ttu-id="a2a80-120">İlk adım, uygulama projesi oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="a2a80-120">The first step is to create the application project.</span></span> <span data-ttu-id="a2a80-121">Özel denetim barındıran uygulama oluşturmak için bu proje kullanır.</span><span class="sxs-lookup"><span data-stu-id="a2a80-121">You will use this project to build the application that hosts the custom control.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="a2a80-122">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a2a80-122">To create the project</span></span>  
  
-   <span data-ttu-id="a2a80-123">"DebuggingExample" adlı bir Windows uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a2a80-123">Create a Windows Application project called "DebuggingExample".</span></span> <span data-ttu-id="a2a80-124">Ayrıntılar için bkz [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="a2a80-124">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
## <a name="creating-a-control-library-project"></a><span data-ttu-id="a2a80-125">Bir denetim kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="a2a80-125">Creating a Control Library Project</span></span>  
 <span data-ttu-id="a2a80-126">Sonraki adım, denetim kitaplığı projesi oluşturun ve özel denetimin ayarlamaktır.</span><span class="sxs-lookup"><span data-stu-id="a2a80-126">The next step is to create the control library project and set up the custom control.</span></span>  
  
#### <a name="to-create-the-control-library-project"></a><span data-ttu-id="a2a80-127">Denetim Kitaplığı projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a2a80-127">To create the control library project</span></span>  
  
1.  <span data-ttu-id="a2a80-128">Ekleme bir **Windows Denetim Kitaplığı** çözüme proje.</span><span class="sxs-lookup"><span data-stu-id="a2a80-128">Add a **Windows Control Library** project to the solution.</span></span>  
  
2.  <span data-ttu-id="a2a80-129">Yeni bir ekleme **UserControl** DebugControlLibrary proje öğesi.</span><span class="sxs-lookup"><span data-stu-id="a2a80-129">Add a new **UserControl** item to the DebugControlLibrary project.</span></span> <span data-ttu-id="a2a80-130">Ayrıntılar için bkz [NIB: nasıl yapılır: Yeni proje öğeleri Ekle](http://msdn.microsoft.com/en-us/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span><span class="sxs-lookup"><span data-stu-id="a2a80-130">For details, see [NIB:How to: Add New Project Items](http://msdn.microsoft.com/en-us/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span></span> <span data-ttu-id="a2a80-131">Yeni kaynak dosyası "DebugControl", temel bir ad verin.</span><span class="sxs-lookup"><span data-stu-id="a2a80-131">Give the new source file a base name of "DebugControl".</span></span>  
  
3.  <span data-ttu-id="a2a80-132">Kullanarak **Çözüm Gezgini**, bir taban adı ile kod dosyası tarafından projenin varsayılan denetim silindiğinde "`UserControl1`".</span><span class="sxs-lookup"><span data-stu-id="a2a80-132">Using the **Solution Explorer**, delete the project's default control by deleting the code file with a base name of "`UserControl1`".</span></span> <span data-ttu-id="a2a80-133">Ayrıntılar için bkz [NIB: nasıl yapılır: Kaldır, silme ve dışlama öğeleri](http://msdn.microsoft.com/en-us/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span><span class="sxs-lookup"><span data-stu-id="a2a80-133">For details, see [NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/en-us/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span></span>  
  
4.  <span data-ttu-id="a2a80-134">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a2a80-134">Build the solution.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="a2a80-135">Denetim noktası</span><span class="sxs-lookup"><span data-stu-id="a2a80-135">Checkpoint</span></span>  
 <span data-ttu-id="a2a80-136">Bu noktada, içinde özel denetim görmeye olacaktır **araç**.</span><span class="sxs-lookup"><span data-stu-id="a2a80-136">At this point, you will be able to see your custom control in the **Toolbox**.</span></span>  
  
#### <a name="to-check-your-progress"></a><span data-ttu-id="a2a80-137">İlerleme durumunuzu denetlemek için</span><span class="sxs-lookup"><span data-stu-id="a2a80-137">To check your progress</span></span>  
  
-   <span data-ttu-id="a2a80-138">Adlı yeni sekmede Bul **DebugControlLibrary bileşenleri** ve seçmek için tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a2a80-138">Find the new tab called **DebugControlLibrary Components** and click to select it.</span></span> <span data-ttu-id="a2a80-139">Açıldığında, olarak listelenen denetiminizi görürsünüz **DebugControl** yanında varsayılan simgesiyle.</span><span class="sxs-lookup"><span data-stu-id="a2a80-139">When it opens, you will see your control listed as **DebugControl** with the default icon beside it.</span></span>  
  
## <a name="adding-a-property-to-your-custom-control"></a><span data-ttu-id="a2a80-140">Bir özellik için özel denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="a2a80-140">Adding a Property to Your Custom Control</span></span>  
 <span data-ttu-id="a2a80-141">Tasarım zamanında özel denetiminizin kodu çalıştığını göstermek için bir özellik ekleyin ve özellik uygulayan kodda bir kesme noktası ayarlama.</span><span class="sxs-lookup"><span data-stu-id="a2a80-141">To demonstrate that your custom control's code is running at design-time, you will add a property and set a breakpoint in the code that implements the property.</span></span>  
  
#### <a name="to-add-a-property-to-your-custom-control"></a><span data-ttu-id="a2a80-142">Bir özellik için özel denetim eklemek için</span><span class="sxs-lookup"><span data-stu-id="a2a80-142">To add a property to your custom control</span></span>  
  
1.  <span data-ttu-id="a2a80-143">Açık **DebugControl** içinde **Kod düzenleyicisinde**.</span><span class="sxs-lookup"><span data-stu-id="a2a80-143">Open **DebugControl** in the **Code Editor**.</span></span> <span data-ttu-id="a2a80-144">Aşağıdaki kodu sınıf tanımına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a2a80-144">Add the following code to the class definition:</span></span>  
  
    ```vb  
    Private demoStringValue As String = Nothing  
    <BrowsableAttribute(true)>  
    Public Property DemoString() As String  
  
        Get  
            Return Me.demoStringValue  
        End Get  
  
        Set(ByVal value As String)  
            Me.demoStringValue = value  
        End Set  
  
    End Property  
    ```  
  
    ```csharp  
    private string demoStringValue = null;  
    [Browsable(true)]  
    public string DemoString  
    {  
        get  
        {  
            return this.demoStringValue;  
        }  
        set  
        {  
            demoStringValue = value;  
        }  
    }  
    ```  
  
2.  <span data-ttu-id="a2a80-145">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a2a80-145">Build the solution.</span></span>  
  
## <a name="adding-your-custom-control-to-the-host-form"></a><span data-ttu-id="a2a80-146">Ana bilgisayar formuna özel denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="a2a80-146">Adding Your Custom Control to the Host Form</span></span>  
 <span data-ttu-id="a2a80-147">Özel Denetim tasarım zamanı davranışını hata ayıklamak için özel denetim sınıfının bir örneği bir ana bilgisayar formunda yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="a2a80-147">To debug the design-time behavior of your custom control, you will place an instance of the custom control class on a host form.</span></span>  
  
#### <a name="to-add-your-custom-control-to-the-host-form"></a><span data-ttu-id="a2a80-148">Ana bilgisayar formun özel denetim eklemek için</span><span class="sxs-lookup"><span data-stu-id="a2a80-148">To add your custom control to the host form</span></span>  
  
1.  <span data-ttu-id="a2a80-149">İçinde Form1 "DebuggingExample" projeyi açın **Windows Form Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="a2a80-149">In the "DebuggingExample" project, open Form1 in the **Windows Forms Designer**.</span></span>  
  
2.  <span data-ttu-id="a2a80-150">İçinde **araç**, açık **DebugControlLibrary bileşenleri** sekmesinde ve sürükleyin bir **DebugControl** forma örneği.</span><span class="sxs-lookup"><span data-stu-id="a2a80-150">In the **Toolbox**, open the **DebugControlLibrary Components** tab and drag a **DebugControl** instance onto the form.</span></span>  
  
3.  <span data-ttu-id="a2a80-151">Bul `DemoString` özel bir özellik **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="a2a80-151">Find the `DemoString` custom property in the **Properties** window.</span></span> <span data-ttu-id="a2a80-152">Herhangi bir özellik gibi değerini değiştirebileceğinizi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a2a80-152">Note that you can change its value as you would any other property.</span></span> <span data-ttu-id="a2a80-153">Ayrıca gerektiğini unutmayın `DemoString` özelliği seçildiğinde, özelliğin açıklama dizesi en altında görüntülenen **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="a2a80-153">Also note that when the `DemoString` property is selected, the property's description string appears at the bottom of the **Properties** window.</span></span>  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a><span data-ttu-id="a2a80-154">Tasarım zamanı hata ayıklama için proje ayarlama</span><span class="sxs-lookup"><span data-stu-id="a2a80-154">Setting Up the Project for Design-Time Debugging</span></span>  
 <span data-ttu-id="a2a80-155">Özel denetimin tasarım zamanı davranışını hata ayıklamak için özel denetimin kodunu çalıştıran Visual Studio ayrı bir örneğini hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="a2a80-155">To debug your custom control's design-time behavior, you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="a2a80-156">Tasarım zamanı hata ayıklama için proje ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a2a80-156">To set up the project for design-time debugging</span></span>  
  
1.  <span data-ttu-id="a2a80-157">Sağ **DebugControlLibrary** proje **Çözüm Gezgini** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="a2a80-157">Right-click on the **DebugControlLibrary** project in the **Solution Explorer** and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="a2a80-158">İçinde **DebugControlLibrary** özellik sayfasını, select **hata ayıklama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="a2a80-158">In the **DebugControlLibrary** property sheet, select the **Debug** tab.</span></span>  
  
     <span data-ttu-id="a2a80-159">İçinde **eylemi Başlat** bölümünde, select **başlangıç dış program**.</span><span class="sxs-lookup"><span data-stu-id="a2a80-159">In the **Start Action** section, select **Start external program**.</span></span> <span data-ttu-id="a2a80-160">Size Visual Studio, ayrı bir örneğini hata ayıklama böylece tıklatın üç nokta (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) için Visual Studio IDE gözatmak için düğmeyi.</span><span class="sxs-lookup"><span data-stu-id="a2a80-160">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="a2a80-161">Yürütülebilir dosya adı **devenv.exe**, ve varsayılan konuma geri yüklediyseniz, %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe yoludur.</span><span class="sxs-lookup"><span data-stu-id="a2a80-161">The name of the executable file is **devenv.exe**, and if you installed to the default location, its path is %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span></span>  
  
3.  <span data-ttu-id="a2a80-162">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a2a80-162">Click **OK** to close the dialog box.</span></span>  
  
4.  <span data-ttu-id="a2a80-163">Sağ **DebugControlLibrary** proje ve seçin **başlangıç projesi olarak ayarla** bu hata ayıklama yapılandırmasını etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="a2a80-163">Right-click the **DebugControlLibrary** project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>  
  
## <a name="debugging-your-custom-control-at-design-time"></a><span data-ttu-id="a2a80-164">Özel Denetim tasarım zamanında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="a2a80-164">Debugging Your Custom Control at Design Time</span></span>  
 <span data-ttu-id="a2a80-165">Şimdi Tasarım modunda çalışırken özel denetim hata ayıklamak hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="a2a80-165">Now you are ready to debug your custom control as it runs in design mode.</span></span> <span data-ttu-id="a2a80-166">Hata ayıklama oturumu başlattığınızda, Visual Studio yeni bir örneğini oluşturulur ve "DebuggingExample" Çözüm yüklemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="a2a80-166">When you start the debugging session, a new instance of Visual Studio will be created, and you will use it to load the "DebuggingExample" solution.</span></span> <span data-ttu-id="a2a80-167">İçinde Form1 açtığınızda **Forms Tasarımcısı**, özel denetim örneği oluşturulur ve çalışmaya başlar.</span><span class="sxs-lookup"><span data-stu-id="a2a80-167">When you open Form1 in the **Forms Designer**, an instance of your custom control will be created and will start running.</span></span>  
  
#### <a name="to-debug-your-custom-control-at-design-time"></a><span data-ttu-id="a2a80-168">Özel Denetim tasarım zamanında hata ayıklamak için</span><span class="sxs-lookup"><span data-stu-id="a2a80-168">To debug your custom control at design time</span></span>  
  
1.  <span data-ttu-id="a2a80-169">Açık **DebugControl** kaynak dosyasında **Kod düzenleyicisinde** ve bir kesme noktası yerleştirmek `Set` erişimcisine `DemoString` özelliği.</span><span class="sxs-lookup"><span data-stu-id="a2a80-169">Open the **DebugControl** source file in the **Code Editor** and place a breakpoint on the `Set` accessor of the `DemoString` property.</span></span>  
  
2.  <span data-ttu-id="a2a80-170">Hata ayıklama oturumu başlatmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a2a80-170">Press F5 to start the debugging session.</span></span> <span data-ttu-id="a2a80-171">Visual Studio yeni bir örneğini oluşturulduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a2a80-171">Note that a new instance of Visual Studio is created.</span></span> <span data-ttu-id="a2a80-172">İki yolla örnekleri arasında ayırt edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a2a80-172">You can distinguish between the instances in two ways:</span></span>  
  
    -   <span data-ttu-id="a2a80-173">Hata ayıklama örneği sözcüğü bulunan **çalıştıran** kendi başlık çubuğunda</span><span class="sxs-lookup"><span data-stu-id="a2a80-173">The debugging instance has the word **Running** in its title bar</span></span>  
  
    -   <span data-ttu-id="a2a80-174">Hata ayıklama örneğinin **Başlat** düğmesini kendi **hata ayıklama** devre dışı araç çubuğu</span><span class="sxs-lookup"><span data-stu-id="a2a80-174">The debugging instance has the **Start** button on its **Debug** toolbar disabled</span></span>  
  
     <span data-ttu-id="a2a80-175">Hata ayıklama örneğinde isabetini ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a2a80-175">Your breakpoint is set in the debugging instance.</span></span>  
  
3.  <span data-ttu-id="a2a80-176">Visual Studio yeni örneğini "DebuggingExample" çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="a2a80-176">In the new instance of Visual Studio, open the "DebuggingExample" solution.</span></span> <span data-ttu-id="a2a80-177">Seçerek kolayca çözüm bulabilirsiniz **son projeler** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="a2a80-177">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="a2a80-178">En son kullanılan dosya "DebuggingExample.sln" çözüm dosyasını listelenir.</span><span class="sxs-lookup"><span data-stu-id="a2a80-178">The "DebuggingExample.sln" solution file will be listed as the most recently used file.</span></span>  
  
4.  <span data-ttu-id="a2a80-179">Açık olarak Form1 **Forms Tasarımcısı** seçip **DebugControl** denetim.</span><span class="sxs-lookup"><span data-stu-id="a2a80-179">Open Form1 in the **Forms Designer** and select the **DebugControl** control.</span></span>  
  
5.  <span data-ttu-id="a2a80-180">Değerini değiştirme `DemoString` özelliği.</span><span class="sxs-lookup"><span data-stu-id="a2a80-180">Change the value of the `DemoString` property.</span></span> <span data-ttu-id="a2a80-181">Değişiklik yaparsanız, Visual Studio hata ayıklama örneğini odağı alması ve yürütme, kesme noktasında durur unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a2a80-181">Note that when you commit the change, the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="a2a80-182">Tek adımlı özelliği erişimcisi ile yapabileceğiniz gibi başka bir kod gerekir.</span><span class="sxs-lookup"><span data-stu-id="a2a80-182">You can single-step through the property accessor just as your would any other code.</span></span>  
  
6.  <span data-ttu-id="a2a80-183">Hata ayıklama oturumunuz ile işiniz bittiğinde, Visual Studio'nun barındırılan örneği kapatılıyor veya tıklatarak çıkabilirsiniz **durdurma hata ayıklama** hata ayıklama örneğinde düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a2a80-183">When you are finished with your debugging session, you can exit by dismissing the hosted instance of Visual Studio or by clicking the **Stop Debugging** button in the debugging instance.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a2a80-184">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="a2a80-184">Next Steps</span></span>  
 <span data-ttu-id="a2a80-185">Tasarım zamanında özel denetimler ayıklayabilirsiniz, Visual Studio IDE denetiminizin etkileşim genişletmek için çok sayıda olasılık vardır.</span><span class="sxs-lookup"><span data-stu-id="a2a80-185">Now that you can debug your custom controls at design time, there are many possibilities for expanding your control's interaction with the Visual Studio IDE.</span></span>  
  
-   <span data-ttu-id="a2a80-186">Kullanabileceğiniz <xref:System.ComponentModel.Component.DesignMode%2A> özelliği <xref:System.ComponentModel.Component> yalnızca tasarım zamanında yürütülür yazma koduna sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a2a80-186">You can use the <xref:System.ComponentModel.Component.DesignMode%2A> property of the <xref:System.ComponentModel.Component> class to write code that will only execute at design time.</span></span> <span data-ttu-id="a2a80-187">Ayrıntılar için bkz <xref:System.ComponentModel.Component.DesignMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2a80-187">For details, see <xref:System.ComponentModel.Component.DesignMode%2A>.</span></span>  
  
-   <span data-ttu-id="a2a80-188">Birkaç öznitelik Tasarımcı özel denetiminizin etkileşim işlemek üzere denetiminizin özellikleri uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2a80-188">There are several attributes you can apply to your control's properties to manipulate your custom control's interaction with the designer.</span></span> <span data-ttu-id="a2a80-189">İçinde bu özniteliklerin bulabilirsiniz <xref:System.ComponentModel?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="a2a80-189">You can find these attributes in the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span>  
  
-   <span data-ttu-id="a2a80-190">Özel denetim için özel bir tasarımcı yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2a80-190">You can write a custom designer for your custom control.</span></span> <span data-ttu-id="a2a80-191">Bu size Visual Studio tarafından kullanıma sunulan Genişletilebilir Tasarımcı altyapısını kullanarak tasarım deneyimi üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2a80-191">This gives you complete control over the design experience using the extensible designer infrastructure exposed by Visual Studio.</span></span> <span data-ttu-id="a2a80-192">Ayrıntılar için bkz [izlenecek yol: bir Windows Forms denetimi, geçen avantajı, Visual Studio tasarım-zamanı özellikleri oluşturma](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="a2a80-192">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2a80-193">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2a80-193">See Also</span></span>  
 [<span data-ttu-id="a2a80-194">İzlenecek yol: Visual Studio Tasarım-Zamanı Özellikleri'nden Faydalanan Windows Forms Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a2a80-194">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 [<span data-ttu-id="a2a80-195">Nasıl yapılır: tasarım zamanında hizmetlere erişme</span><span class="sxs-lookup"><span data-stu-id="a2a80-195">How to: Access Design-Time Services</span></span>](http://msdn.microsoft.com/library/c186c4b6-076c-438d-9ed3-f13da29c8c1f)  
 [<span data-ttu-id="a2a80-196">Nasıl yapılır: Windows Forms'ta tasarım zamanı desteği erişim</span><span class="sxs-lookup"><span data-stu-id="a2a80-196">How to: Access Design-Time Support in Windows Forms</span></span>](http://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09)
