---
title: 'İzlenecek yol: Tasarım Zamanında Özel Windows Formları Denetimleri Hatalarını Ayıklama'
ms.date: 03/30/2017
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
ms.openlocfilehash: 824c1e47cf50dc13a3a986e48a49158b15dbb935
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331804"
---
# <a name="walkthrough-debugging-custom-windows-forms-controls-at-design-time"></a><span data-ttu-id="768d5-102">İzlenecek yol: Tasarım Zamanında Özel Windows Formları Denetimleri Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="768d5-102">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="768d5-103">Özel denetim oluşturduğunuzda, genellikle, tasarım zamanı davranışını hata ayıklamak gerekli bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="768d5-103">When you create a custom control, you will often find it necessary to debug its design-time behavior.</span></span> <span data-ttu-id="768d5-104">Özel denetim için özel bir tasarımcı yazıyorsanız bu özellikle doğrudur.</span><span class="sxs-lookup"><span data-stu-id="768d5-104">This is especially true if you are authoring a custom designer for your custom control.</span></span> <span data-ttu-id="768d5-105">Ayrıntılar için bkz [izlenecek yol: bir Windows Forms denetimi olduğunu alır avantajı, Visual Studio tasarım-zamanı özellikleri oluşturma](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="768d5-105">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span></span>  
  
 <span data-ttu-id="768d5-106">Diğer .NET Framework sınıfları debug gibi özel kontrollerinizi Visual Studio kullanarak hata ayıklama yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="768d5-106">You can debug your custom controls using Visual Studio, just as you would debug any other .NET Framework classes.</span></span> <span data-ttu-id="768d5-107">Visual Studio'ya özel denetiminizin kodu çalıştıran ayrı bir örneğini hata ayıklayacaktır fark</span><span class="sxs-lookup"><span data-stu-id="768d5-107">The difference is that you will debug a separate instance of Visual Studio that is running your custom control's code</span></span>  
  
 <span data-ttu-id="768d5-108">Bu kılavuzda gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="768d5-108">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="768d5-109">Özel denetiminizi barındırmak için bir Windows Forms projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="768d5-109">Creating a Windows Forms project to host your custom control</span></span>  
  
-   <span data-ttu-id="768d5-110">Bir denetim kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="768d5-110">Creating a control library project</span></span>  
  
-   <span data-ttu-id="768d5-111">Bir özellik için özel denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="768d5-111">Adding a property to your custom control</span></span>  
  
-   <span data-ttu-id="768d5-112">Konak formuna özel denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="768d5-112">Adding your custom control to the host form</span></span>  
  
-   <span data-ttu-id="768d5-113">Tasarım zamanı hata ayıklama için projeyi ayarlama</span><span class="sxs-lookup"><span data-stu-id="768d5-113">Setting up the project for design-time debugging</span></span>  
  
-   <span data-ttu-id="768d5-114">Özel denetiminizi tasarım zamanında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="768d5-114">Debugging your custom control at design time</span></span>  
  
 <span data-ttu-id="768d5-115">İşlemi tamamladığınızda, özel denetiminin tasarım zamanı davranışını hata ayıklama için gerekli görevleri bir anlayışa sahip olacaksınız.</span><span class="sxs-lookup"><span data-stu-id="768d5-115">When you are finished, you will have an understanding of the tasks necessary for debugging the design-time behavior of a custom control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="768d5-116">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="768d5-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="768d5-117">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="768d5-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="768d5-118">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="768d5-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="768d5-119">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="768d5-119">Creating the Project</span></span>  
 <span data-ttu-id="768d5-120">İlk adım, uygulama projesi oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="768d5-120">The first step is to create the application project.</span></span> <span data-ttu-id="768d5-121">Bu proje, özel denetimin barındıran uygulaması oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="768d5-121">You will use this project to build the application that hosts the custom control.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="768d5-122">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="768d5-122">To create the project</span></span>  
  
-   <span data-ttu-id="768d5-123">"DebuggingExample" adlı bir Windows uygulaması projesi oluşturun (**dosya** > **yeni** > **proje**  >  **Visual C#** veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms uygulamalarındaki**).</span><span class="sxs-lookup"><span data-stu-id="768d5-123">Create a Windows Application project called "DebuggingExample" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
## <a name="creating-a-control-library-project"></a><span data-ttu-id="768d5-124">Bir denetim kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="768d5-124">Creating a Control Library Project</span></span>  
 <span data-ttu-id="768d5-125">Sonraki adım, denetim kitaplığı projesi oluşturun ve özel denetimi ayarlamaktır.</span><span class="sxs-lookup"><span data-stu-id="768d5-125">The next step is to create the control library project and set up the custom control.</span></span>  
  
#### <a name="to-create-the-control-library-project"></a><span data-ttu-id="768d5-126">Denetim Kitaplığı projesini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="768d5-126">To create the control library project</span></span>  
  
1.  <span data-ttu-id="768d5-127">Ekleme bir **Windows Denetim Kitaplığı** çözüme bir proje.</span><span class="sxs-lookup"><span data-stu-id="768d5-127">Add a **Windows Control Library** project to the solution.</span></span>  
  
2.  <span data-ttu-id="768d5-128">Yeni bir **UserControl** DebugControlLibrary projeye öğe.</span><span class="sxs-lookup"><span data-stu-id="768d5-128">Add a new **UserControl** item to the DebugControlLibrary project.</span></span> <span data-ttu-id="768d5-129">Ayrıntılar için bkz [NIB: nasıl yapılır: Yeni proje öğeleri ekleme](https://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span><span class="sxs-lookup"><span data-stu-id="768d5-129">For details, see [NIB:How to: Add New Project Items](https://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span></span> <span data-ttu-id="768d5-130">Yeni kaynak dosyanın temel "DebugControl" adını verin.</span><span class="sxs-lookup"><span data-stu-id="768d5-130">Give the new source file a base name of "DebugControl".</span></span>  
  
3.  <span data-ttu-id="768d5-131">Kullanarak **Çözüm Gezgini**, projenin varsayılan denetimi kod dosyası taban adı ile silerek Sil "`UserControl1`".</span><span class="sxs-lookup"><span data-stu-id="768d5-131">Using the **Solution Explorer**, delete the project's default control by deleting the code file with a base name of "`UserControl1`".</span></span> <span data-ttu-id="768d5-132">Ayrıntılar için bkz [NIB: nasıl yapılır: kaldırma, silme ve öğeleri hariç](https://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span><span class="sxs-lookup"><span data-stu-id="768d5-132">For details, see [NIB:How to: Remove, Delete, and Exclude Items](https://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span></span>  
  
4.  <span data-ttu-id="768d5-133">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="768d5-133">Build the solution.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="768d5-134">Denetim noktası</span><span class="sxs-lookup"><span data-stu-id="768d5-134">Checkpoint</span></span>  
 <span data-ttu-id="768d5-135">Bu noktada, özel denetiminizi görmeye olacaktır **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="768d5-135">At this point, you will be able to see your custom control in the **Toolbox**.</span></span>  
  
#### <a name="to-check-your-progress"></a><span data-ttu-id="768d5-136">İlerleme durumunuzu kontrol etmek için</span><span class="sxs-lookup"><span data-stu-id="768d5-136">To check your progress</span></span>  
  
-   <span data-ttu-id="768d5-137">Adlı yeni sekmeyi bulun **DebugControlLibrary bileşenleri** ve seçmek için tıklayın.</span><span class="sxs-lookup"><span data-stu-id="768d5-137">Find the new tab called **DebugControlLibrary Components** and click to select it.</span></span> <span data-ttu-id="768d5-138">Açıldığında, denetiminiz olarak listelenen göreceğiniz **DebugControl** varsayılan simgesinin yanında.</span><span class="sxs-lookup"><span data-stu-id="768d5-138">When it opens, you will see your control listed as **DebugControl** with the default icon beside it.</span></span>  
  
## <a name="adding-a-property-to-your-custom-control"></a><span data-ttu-id="768d5-139">Bir özellik için özel denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="768d5-139">Adding a Property to Your Custom Control</span></span>  
 <span data-ttu-id="768d5-140">Tasarım zamanında özel denetiminizin kodu çalıştığını göstermek için özellik ekleme ve özelliği uygulayan kod içinde bir kesme noktası ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="768d5-140">To demonstrate that your custom control's code is running at design-time, you will add a property and set a breakpoint in the code that implements the property.</span></span>  
  
#### <a name="to-add-a-property-to-your-custom-control"></a><span data-ttu-id="768d5-141">Bir özellik için özel denetim eklemek için</span><span class="sxs-lookup"><span data-stu-id="768d5-141">To add a property to your custom control</span></span>  
  
1.  <span data-ttu-id="768d5-142">Açık **DebugControl** içinde **Kod Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="768d5-142">Open **DebugControl** in the **Code Editor**.</span></span> <span data-ttu-id="768d5-143">Aşağıdaki kodu sınıf tanımına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="768d5-143">Add the following code to the class definition:</span></span>  
  
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
  
2.  <span data-ttu-id="768d5-144">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="768d5-144">Build the solution.</span></span>  
  
## <a name="adding-your-custom-control-to-the-host-form"></a><span data-ttu-id="768d5-145">Konak formuna özel denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="768d5-145">Adding Your Custom Control to the Host Form</span></span>  
 <span data-ttu-id="768d5-146">Özel denetiminizi tasarım zamanı davranışını hata ayıklamak için bir konak formda özel denetim sınıfının bir örneğini yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="768d5-146">To debug the design-time behavior of your custom control, you will place an instance of the custom control class on a host form.</span></span>  
  
#### <a name="to-add-your-custom-control-to-the-host-form"></a><span data-ttu-id="768d5-147">Konak formuna özel denetim eklemek için</span><span class="sxs-lookup"><span data-stu-id="768d5-147">To add your custom control to the host form</span></span>  
  
1.  <span data-ttu-id="768d5-148">Form1 içinde "DebuggingExample" projesinde açın **Windows Form Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="768d5-148">In the "DebuggingExample" project, open Form1 in the **Windows Forms Designer**.</span></span>  
  
2.  <span data-ttu-id="768d5-149">İçinde **araç kutusu**açın **DebugControlLibrary bileşenleri** sürükleyin ve sekme bir **DebugControl** forma örneği.</span><span class="sxs-lookup"><span data-stu-id="768d5-149">In the **Toolbox**, open the **DebugControlLibrary Components** tab and drag a **DebugControl** instance onto the form.</span></span>  
  
3.  <span data-ttu-id="768d5-150">Bulma `DemoString` özel özelliğinde **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="768d5-150">Find the `DemoString` custom property in the **Properties** window.</span></span> <span data-ttu-id="768d5-151">Herhangi bir özellik gibi değerini değiştirebileceğinize dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="768d5-151">Note that you can change its value as you would any other property.</span></span> <span data-ttu-id="768d5-152">Gerektiğini de unutmayın `DemoString` özelliği seçildiğinde, özellik açıklama dizesi sonunda görünür **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="768d5-152">Also note that when the `DemoString` property is selected, the property's description string appears at the bottom of the **Properties** window.</span></span>  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a><span data-ttu-id="768d5-153">Tasarım zamanı hata ayıklama için projeyi ayarlama</span><span class="sxs-lookup"><span data-stu-id="768d5-153">Setting Up the Project for Design-Time Debugging</span></span>  
 <span data-ttu-id="768d5-154">Özel denetiminizin tasarım zamanı davranışını hata ayıklamak için Visual Studio'ya özel denetiminizin kodu çalıştıran ayrı bir örneğini hata ayıklayacaktır.</span><span class="sxs-lookup"><span data-stu-id="768d5-154">To debug your custom control's design-time behavior, you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="768d5-155">Tasarım zamanı hata ayıklama için projeyi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="768d5-155">To set up the project for design-time debugging</span></span>  
  
1.  <span data-ttu-id="768d5-156">Sağ **DebugControlLibrary** projesi **Çözüm Gezgini** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="768d5-156">Right-click on the **DebugControlLibrary** project in the **Solution Explorer** and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="768d5-157">İçinde **DebugControlLibrary** özellik sayfasını, select **hata ayıklama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="768d5-157">In the **DebugControlLibrary** property sheet, select the **Debug** tab.</span></span>  
  
     <span data-ttu-id="768d5-158">İçinde **başlatma eylemi** bölümünden **harici program Başlat**.</span><span class="sxs-lookup"><span data-stu-id="768d5-158">In the **Start Action** section, select **Start external program**.</span></span> <span data-ttu-id="768d5-159">Artık Visual Studio, ayrı bir örneğini hata ayıklama şekilde üç nokta simgesine tıklayın (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) Visual Studio IDE için Gözat düğmesini.</span><span class="sxs-lookup"><span data-stu-id="768d5-159">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="768d5-160">Yürütülebilir dosyanın adı **devenv.exe**, ve varsayılan bir konuma yüklediyseniz, %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe yoludur.</span><span class="sxs-lookup"><span data-stu-id="768d5-160">The name of the executable file is **devenv.exe**, and if you installed to the default location, its path is %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span></span>  
  
3.  <span data-ttu-id="768d5-161">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="768d5-161">Click **OK** to close the dialog box.</span></span>  
  
4.  <span data-ttu-id="768d5-162">Sağ **DebugControlLibrary** seçin ve proje **başlangıç projesi olarak ayarla** bu hata ayıklama yapılandırmasını etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="768d5-162">Right-click the **DebugControlLibrary** project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>  
  
## <a name="debugging-your-custom-control-at-design-time"></a><span data-ttu-id="768d5-163">Özel denetiminizi tasarım zamanında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="768d5-163">Debugging Your Custom Control at Design Time</span></span>  
 <span data-ttu-id="768d5-164">Özel denetiminizi Tasarım modunda çalışırken hata ayıklamak hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="768d5-164">Now you are ready to debug your custom control as it runs in design mode.</span></span> <span data-ttu-id="768d5-165">Hata ayıklama oturumu başlattığınızda, Visual Studio'nun yeni bir örneği oluşturulur ve "DebuggingExample" çözümü yüklemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="768d5-165">When you start the debugging session, a new instance of Visual Studio will be created, and you will use it to load the "DebuggingExample" solution.</span></span> <span data-ttu-id="768d5-166">Form1 içinde açtığınızda **Form Tasarımcısı**, özel denetiminizi örneği oluşturulur ve çalıştırmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="768d5-166">When you open Form1 in the **Forms Designer**, an instance of your custom control will be created and will start running.</span></span>  
  
#### <a name="to-debug-your-custom-control-at-design-time"></a><span data-ttu-id="768d5-167">Özel denetiminizi tasarım zamanında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="768d5-167">To debug your custom control at design time</span></span>  
  
1.  <span data-ttu-id="768d5-168">Açık **DebugControl** kaynak dosyada **Kod Düzenleyicisi** ve bir kesme noktası yerleştirmek `Set` erişimcisine `DemoString` özelliği.</span><span class="sxs-lookup"><span data-stu-id="768d5-168">Open the **DebugControl** source file in the **Code Editor** and place a breakpoint on the `Set` accessor of the `DemoString` property.</span></span>  
  
2.  <span data-ttu-id="768d5-169">Hata ayıklama oturumu başlatmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="768d5-169">Press F5 to start the debugging session.</span></span> <span data-ttu-id="768d5-170">Visual Studio'nun yeni bir örneğini oluşturulduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="768d5-170">Note that a new instance of Visual Studio is created.</span></span> <span data-ttu-id="768d5-171">İki yolla örnekleri ayırt edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="768d5-171">You can distinguish between the instances in two ways:</span></span>  
  
    -   <span data-ttu-id="768d5-172">Hata ayıklama örneğindeki ifadesi **çalıştıran** başlık çubuğunda</span><span class="sxs-lookup"><span data-stu-id="768d5-172">The debugging instance has the word **Running** in its title bar</span></span>  
  
    -   <span data-ttu-id="768d5-173">Hata ayıklama örneğindeki sahip **Başlat** düğmesini kendi **hata ayıklama** araç çubuğunda devre dışı</span><span class="sxs-lookup"><span data-stu-id="768d5-173">The debugging instance has the **Start** button on its **Debug** toolbar disabled</span></span>  
  
     <span data-ttu-id="768d5-174">Kesme noktasına içinde hata ayıklama örneğindeki ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="768d5-174">Your breakpoint is set in the debugging instance.</span></span>  
  
3.  <span data-ttu-id="768d5-175">Visual Studio'nun yeni örneğini "DebuggingExample" çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="768d5-175">In the new instance of Visual Studio, open the "DebuggingExample" solution.</span></span> <span data-ttu-id="768d5-176">Çözüm seçerek kolayca bulabilirsiniz **son projeler** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="768d5-176">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="768d5-177">En son dosya kullanılan "DebuggingExample.sln" Çözüm dosyası listelenir.</span><span class="sxs-lookup"><span data-stu-id="768d5-177">The "DebuggingExample.sln" solution file will be listed as the most recently used file.</span></span>  
  
4.  <span data-ttu-id="768d5-178">Açık olarak Form1 **Form Tasarımcısı** seçip **DebugControl** denetimi.</span><span class="sxs-lookup"><span data-stu-id="768d5-178">Open Form1 in the **Forms Designer** and select the **DebugControl** control.</span></span>  
  
5.  <span data-ttu-id="768d5-179">Değiştirin `DemoString` özelliği.</span><span class="sxs-lookup"><span data-stu-id="768d5-179">Change the value of the `DemoString` property.</span></span> <span data-ttu-id="768d5-180">Değişiklik yaparsanız, hata ayıklama örneğindeki Visual Studio'nun odağı alır ve yürütmeyi, kesme noktasında durur unutmayın.</span><span class="sxs-lookup"><span data-stu-id="768d5-180">Note that when you commit the change, the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="768d5-181">Özellik erişimcisi aracılığıyla tek adımlı yapabilecekleriniz gibi herhangi bir kod gerekir.</span><span class="sxs-lookup"><span data-stu-id="768d5-181">You can single-step through the property accessor just as your would any other code.</span></span>  
  
6.  <span data-ttu-id="768d5-182">Hata ayıklama oturumunuzu ile işiniz bittiğinde, barındırılan bir Visual Studio örneğini kapatma veya tıklayarak çıkabilirsiniz **hata ayıklamayı Durdur** hata ayıklama örneğindeki düğmesi.</span><span class="sxs-lookup"><span data-stu-id="768d5-182">When you are finished with your debugging session, you can exit by dismissing the hosted instance of Visual Studio or by clicking the **Stop Debugging** button in the debugging instance.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="768d5-183">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="768d5-183">Next Steps</span></span>  
 <span data-ttu-id="768d5-184">Tasarım zamanında özel kontrollerinizi ayıklayabilirsiniz, Visual Studio IDE denetiminizin etkileşim genişletme için çok sayıda olasılık vardır.</span><span class="sxs-lookup"><span data-stu-id="768d5-184">Now that you can debug your custom controls at design time, there are many possibilities for expanding your control's interaction with the Visual Studio IDE.</span></span>  
  
-   <span data-ttu-id="768d5-185">Kullanabileceğiniz <xref:System.ComponentModel.Component.DesignMode%2A> özelliği <xref:System.ComponentModel.Component> yalnızca tasarım zamanında yürütülür kod yazmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="768d5-185">You can use the <xref:System.ComponentModel.Component.DesignMode%2A> property of the <xref:System.ComponentModel.Component> class to write code that will only execute at design time.</span></span> <span data-ttu-id="768d5-186">Ayrıntılar için bkz <xref:System.ComponentModel.Component.DesignMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="768d5-186">For details, see <xref:System.ComponentModel.Component.DesignMode%2A>.</span></span>  
  
-   <span data-ttu-id="768d5-187">Birkaç öznitelik özel denetiminizin etkileşim Tasarımcısı ile düzenlemek için denetimin özelliklerini uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="768d5-187">There are several attributes you can apply to your control's properties to manipulate your custom control's interaction with the designer.</span></span> <span data-ttu-id="768d5-188">İçinde bu özniteliklerin bulabilirsiniz <xref:System.ComponentModel?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="768d5-188">You can find these attributes in the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span>  
  
-   <span data-ttu-id="768d5-189">Özel denetim için özel bir tasarımcı yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="768d5-189">You can write a custom designer for your custom control.</span></span> <span data-ttu-id="768d5-190">Bu, Visual Studio tarafından kullanıma sunulan Genişletilebilir Tasarımcı altyapısını kullanarak tasarım deneyimi üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="768d5-190">This gives you complete control over the design experience using the extensible designer infrastructure exposed by Visual Studio.</span></span> <span data-ttu-id="768d5-191">Ayrıntılar için bkz [izlenecek yol: bir Windows Forms denetimi olduğunu alır avantajı, Visual Studio tasarım-zamanı özellikleri oluşturma](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="768d5-191">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="768d5-192">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="768d5-192">See Also</span></span>  
 [<span data-ttu-id="768d5-193">İzlenecek yol: Visual Studio Tasarım-Zamanı Özellikleri'nden Faydalanan Windows Forms Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="768d5-193">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 [<span data-ttu-id="768d5-194">Nasıl yapılır: tasarım zamanı hizmetlere erişme</span><span class="sxs-lookup"><span data-stu-id="768d5-194">How to: Access Design-Time Services</span></span>](https://msdn.microsoft.com/library/c186c4b6-076c-438d-9ed3-f13da29c8c1f)  
 [<span data-ttu-id="768d5-195">Nasıl yapılır: Windows Forms tasarım zamanı desteğine erişim</span><span class="sxs-lookup"><span data-stu-id="768d5-195">How to: Access Design-Time Support in Windows Forms</span></span>](https://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09)
