---
title: 'İzlenecek yol: Tasarım Zamanında Özel Windows Forms Denetimleri Hatalarını Ayıklama'
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
ms.openlocfilehash: 39adcbd6d915f8b086df7e425efbe08ae8680a45
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882458"
---
# <a name="walkthrough-debugging-custom-windows-forms-controls-at-design-time"></a><span data-ttu-id="234b7-102">İzlenecek yol: Tasarım Zamanında Özel Windows Forms Denetimleri Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="234b7-102">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>

<span data-ttu-id="234b7-103">Özel denetim oluşturduğunuzda, genellikle, tasarım zamanı davranışını hata ayıklamak gerekli bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="234b7-103">When you create a custom control, you will often find it necessary to debug its design-time behavior.</span></span> <span data-ttu-id="234b7-104">Özel denetim için özel bir tasarımcı yazıyorsanız bu özellikle doğrudur.</span><span class="sxs-lookup"><span data-stu-id="234b7-104">This is especially true if you are authoring a custom designer for your custom control.</span></span> <span data-ttu-id="234b7-105">Ayrıntılar için bkz [izlenecek yol: Oluşturma bir Windows Forms Visual Studio tasarım zamanı özelliklerinden yararlanır denetimin](creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="234b7-105">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md).</span></span>

<span data-ttu-id="234b7-106">Diğer .NET Framework sınıfları debug gibi özel kontrollerinizi Visual Studio kullanarak hata ayıklama yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="234b7-106">You can debug your custom controls using Visual Studio, just as you would debug any other .NET Framework classes.</span></span> <span data-ttu-id="234b7-107">Visual Studio'ya özel denetiminizin kodu çalıştıran ayrı bir örneğini hata ayıklayacaktır fark</span><span class="sxs-lookup"><span data-stu-id="234b7-107">The difference is that you will debug a separate instance of Visual Studio that is running your custom control's code</span></span>

<span data-ttu-id="234b7-108">Bu kılavuzda gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="234b7-108">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="234b7-109">Özel denetiminizi barındırmak için bir Windows Forms projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="234b7-109">Creating a Windows Forms project to host your custom control</span></span>

- <span data-ttu-id="234b7-110">Bir denetim kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="234b7-110">Creating a control library project</span></span>

- <span data-ttu-id="234b7-111">Bir özellik için özel denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="234b7-111">Adding a property to your custom control</span></span>

- <span data-ttu-id="234b7-112">Konak formuna özel denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="234b7-112">Adding your custom control to the host form</span></span>

- <span data-ttu-id="234b7-113">Tasarım zamanı hata ayıklama için projeyi ayarlama</span><span class="sxs-lookup"><span data-stu-id="234b7-113">Setting up the project for design-time debugging</span></span>

- <span data-ttu-id="234b7-114">Özel denetiminizi tasarım zamanında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="234b7-114">Debugging your custom control at design time</span></span>

<span data-ttu-id="234b7-115">İşlemi tamamladığınızda, özel denetiminin tasarım zamanı davranışını hata ayıklama için gerekli görevleri bir anlayışa sahip olacaksınız.</span><span class="sxs-lookup"><span data-stu-id="234b7-115">When you are finished, you will have an understanding of the tasks necessary for debugging the design-time behavior of a custom control.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="234b7-116">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="234b7-116">Create the project</span></span>

<span data-ttu-id="234b7-117">İlk adım, uygulama projesi oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="234b7-117">The first step is to create the application project.</span></span> <span data-ttu-id="234b7-118">Bu proje, özel denetimin barındıran uygulaması oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="234b7-118">You will use this project to build the application that hosts the custom control.</span></span>

<span data-ttu-id="234b7-119">Visual Studio'da "DebuggingExample" adlı bir Windows uygulaması projesi oluşturun (**dosya** > **yeni** > **proje**  >  **Visual C#**  veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms uygulamalarındaki**).</span><span class="sxs-lookup"><span data-stu-id="234b7-119">In Visual Studio, create a Windows Application project called "DebuggingExample" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

## <a name="create-the-control-library-project"></a><span data-ttu-id="234b7-120">Denetim Kitaplığı projesi oluşturun</span><span class="sxs-lookup"><span data-stu-id="234b7-120">Create the control library project</span></span>

1. <span data-ttu-id="234b7-121">Ekleme bir **Windows Denetim Kitaplığı** çözüme bir proje.</span><span class="sxs-lookup"><span data-stu-id="234b7-121">Add a **Windows Control Library** project to the solution.</span></span>

2. <span data-ttu-id="234b7-122">Yeni bir **UserControl** DebugControlLibrary projeye öğe.</span><span class="sxs-lookup"><span data-stu-id="234b7-122">Add a new **UserControl** item to the DebugControlLibrary project.</span></span> <span data-ttu-id="234b7-123">Ayrıntılar için bkz [nasıl yapılır: Yeni proje öğeleri ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="234b7-123">For details, see [How to: Add New Project Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span></span> <span data-ttu-id="234b7-124">Yeni kaynak dosyanın temel "DebugControl" adını verin.</span><span class="sxs-lookup"><span data-stu-id="234b7-124">Give the new source file a base name of "DebugControl".</span></span>

3. <span data-ttu-id="234b7-125">Kullanarak **Çözüm Gezgini**, projenin varsayılan denetimi kod dosyası taban adı ile silerek Sil "`UserControl1`".</span><span class="sxs-lookup"><span data-stu-id="234b7-125">Using the **Solution Explorer**, delete the project's default control by deleting the code file with a base name of "`UserControl1`".</span></span> <span data-ttu-id="234b7-126">Ayrıntılar için bkz [nasıl yapılır: , Silme, kaldırmak ve öğeleri hariç](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="234b7-126">For details, see [How to: Remove, Delete, and Exclude Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span></span>

4. <span data-ttu-id="234b7-127">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="234b7-127">Build the solution.</span></span>

## <a name="checkpoint"></a><span data-ttu-id="234b7-128">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="234b7-128">Checkpoint</span></span>

<span data-ttu-id="234b7-129">Bu noktada, özel denetiminizi görmeye olacaktır **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="234b7-129">At this point, you will be able to see your custom control in the **Toolbox**.</span></span>

<span data-ttu-id="234b7-130">İlerleme durumunuzu kontrol etmek için adlı yeni sekmeyi bulun **DebugControlLibrary bileşenleri** ve seçmek için tıklayın.</span><span class="sxs-lookup"><span data-stu-id="234b7-130">To check your progress, find the new tab called **DebugControlLibrary Components** and click to select it.</span></span> <span data-ttu-id="234b7-131">Açıldığında, denetiminiz olarak listelenen göreceğiniz **DebugControl** varsayılan simgesinin yanında.</span><span class="sxs-lookup"><span data-stu-id="234b7-131">When it opens, you will see your control listed as **DebugControl** with the default icon beside it.</span></span>

## <a name="add-a-property-to-your-custom-control"></a><span data-ttu-id="234b7-132">Bir özellik için özel denetim Ekle</span><span class="sxs-lookup"><span data-stu-id="234b7-132">Add a property to your custom control</span></span>

<span data-ttu-id="234b7-133">Tasarım zamanında özel denetiminizin kodu çalıştığını göstermek için özellik ekleme ve özelliği uygulayan kod içinde bir kesme noktası ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="234b7-133">To demonstrate that your custom control's code is running at design-time, you will add a property and set a breakpoint in the code that implements the property.</span></span>

1. <span data-ttu-id="234b7-134">Açık **DebugControl** içinde **Kod Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="234b7-134">Open **DebugControl** in the **Code Editor**.</span></span> <span data-ttu-id="234b7-135">Aşağıdaki kodu sınıf tanımına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="234b7-135">Add the following code to the class definition:</span></span>

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

2. <span data-ttu-id="234b7-136">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="234b7-136">Build the solution.</span></span>

## <a name="add-your-custom-control-to-the-host-form"></a><span data-ttu-id="234b7-137">Konak formuna özel denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="234b7-137">Add your custom control to the host form</span></span>

<span data-ttu-id="234b7-138">Özel denetiminizi tasarım zamanı davranışını hata ayıklamak için bir konak formda özel denetim sınıfının bir örneğini yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="234b7-138">To debug the design-time behavior of your custom control, you will place an instance of the custom control class on a host form.</span></span>

1. <span data-ttu-id="234b7-139">Form1 içinde "DebuggingExample" projesinde açın **Windows Form Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="234b7-139">In the "DebuggingExample" project, open Form1 in the **Windows Forms Designer**.</span></span>

2. <span data-ttu-id="234b7-140">İçinde **araç kutusu**açın **DebugControlLibrary bileşenleri** sürükleyin ve sekme bir **DebugControl** forma örneği.</span><span class="sxs-lookup"><span data-stu-id="234b7-140">In the **Toolbox**, open the **DebugControlLibrary Components** tab and drag a **DebugControl** instance onto the form.</span></span>

3. <span data-ttu-id="234b7-141">Bulma `DemoString` özel özelliğinde **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="234b7-141">Find the `DemoString` custom property in the **Properties** window.</span></span> <span data-ttu-id="234b7-142">Herhangi bir özellik gibi değerini değiştirebileceğinize dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="234b7-142">Note that you can change its value as you would any other property.</span></span> <span data-ttu-id="234b7-143">Gerektiğini de unutmayın `DemoString` özelliği seçildiğinde, özellik açıklama dizesi sonunda görünür **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="234b7-143">Also note that when the `DemoString` property is selected, the property's description string appears at the bottom of the **Properties** window.</span></span>

## <a name="set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="234b7-144">Tasarım zamanı hata ayıklama için projeyi ayarlama</span><span class="sxs-lookup"><span data-stu-id="234b7-144">Set up the project for design-time debugging</span></span>

<span data-ttu-id="234b7-145">Özel denetiminizin tasarım zamanı davranışını hata ayıklamak için Visual Studio'ya özel denetiminizin kodu çalıştıran ayrı bir örneğini hata ayıklayacaktır.</span><span class="sxs-lookup"><span data-stu-id="234b7-145">To debug your custom control's design-time behavior, you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>

1. <span data-ttu-id="234b7-146">Sağ **DebugControlLibrary** projesi **Çözüm Gezgini** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="234b7-146">Right-click on the **DebugControlLibrary** project in the **Solution Explorer** and select **Properties**.</span></span>

2. <span data-ttu-id="234b7-147">İçinde **DebugControlLibrary** özellik sayfasını, select **hata ayıklama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="234b7-147">In the **DebugControlLibrary** property sheet, select the **Debug** tab.</span></span>

     <span data-ttu-id="234b7-148">İçinde **başlatma eylemi** bölümünden **harici program Başlat**.</span><span class="sxs-lookup"><span data-stu-id="234b7-148">In the **Start Action** section, select **Start external program**.</span></span> <span data-ttu-id="234b7-149">Artık Visual Studio, ayrı bir örneğini hata ayıklama şekilde üç nokta simgesine tıklayın (![Visual Studio Özellikler penceresinde üç nokta düğmesini (…)](./media/visual-studio-ellipsis-button.png)) Visual Studio IDE için Gözat düğmesini.</span><span class="sxs-lookup"><span data-stu-id="234b7-149">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="234b7-150">Yürütülebilir dosyanın adı **devenv.exe**, ve varsayılan bir konuma yüklediyseniz, %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe yoludur.</span><span class="sxs-lookup"><span data-stu-id="234b7-150">The name of the executable file is **devenv.exe**, and if you installed to the default location, its path is %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span></span>

3. <span data-ttu-id="234b7-151">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="234b7-151">Click **OK** to close the dialog box.</span></span>

4. <span data-ttu-id="234b7-152">Sağ **DebugControlLibrary** seçin ve proje **başlangıç projesi olarak ayarla** bu hata ayıklama yapılandırmasını etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="234b7-152">Right-click the **DebugControlLibrary** project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>

## <a name="debug-your-custom-control-at-design-time"></a><span data-ttu-id="234b7-153">Özel denetiminizi tasarım zamanında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="234b7-153">Debug your custom control at design time</span></span>

<span data-ttu-id="234b7-154">Özel denetiminizi Tasarım modunda çalışırken hata ayıklamak hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="234b7-154">Now you are ready to debug your custom control as it runs in design mode.</span></span> <span data-ttu-id="234b7-155">Hata ayıklama oturumu başlattığınızda, Visual Studio'nun yeni bir örneği oluşturulur ve "DebuggingExample" çözümü yüklemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="234b7-155">When you start the debugging session, a new instance of Visual Studio will be created, and you will use it to load the "DebuggingExample" solution.</span></span> <span data-ttu-id="234b7-156">Form1 içinde açtığınızda **Form Tasarımcısı**, özel denetiminizi örneği oluşturulur ve çalıştırmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="234b7-156">When you open Form1 in the **Forms Designer**, an instance of your custom control will be created and will start running.</span></span>

1. <span data-ttu-id="234b7-157">Açık **DebugControl** kaynak dosyada **Kod Düzenleyicisi** ve bir kesme noktası yerleştirmek `Set` erişimcisine `DemoString` özelliği.</span><span class="sxs-lookup"><span data-stu-id="234b7-157">Open the **DebugControl** source file in the **Code Editor** and place a breakpoint on the `Set` accessor of the `DemoString` property.</span></span>

2. <span data-ttu-id="234b7-158">Hata ayıklama oturumu başlatmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="234b7-158">Press F5 to start the debugging session.</span></span> <span data-ttu-id="234b7-159">Visual Studio'nun yeni bir örneğini oluşturulduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="234b7-159">Note that a new instance of Visual Studio is created.</span></span> <span data-ttu-id="234b7-160">İki yolla örnekleri ayırt edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="234b7-160">You can distinguish between the instances in two ways:</span></span>

    - <span data-ttu-id="234b7-161">Hata ayıklama örneğindeki ifadesi **çalıştıran** başlık çubuğunda</span><span class="sxs-lookup"><span data-stu-id="234b7-161">The debugging instance has the word **Running** in its title bar</span></span>

    - <span data-ttu-id="234b7-162">Hata ayıklama örneğindeki sahip **Başlat** düğmesini kendi **hata ayıklama** araç çubuğunda devre dışı</span><span class="sxs-lookup"><span data-stu-id="234b7-162">The debugging instance has the **Start** button on its **Debug** toolbar disabled</span></span>

     <span data-ttu-id="234b7-163">Kesme noktasına içinde hata ayıklama örneğindeki ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="234b7-163">Your breakpoint is set in the debugging instance.</span></span>

3. <span data-ttu-id="234b7-164">Visual Studio'nun yeni örneğini "DebuggingExample" çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="234b7-164">In the new instance of Visual Studio, open the "DebuggingExample" solution.</span></span> <span data-ttu-id="234b7-165">Çözüm seçerek kolayca bulabilirsiniz **son projeler** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="234b7-165">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="234b7-166">En son dosya kullanılan "DebuggingExample.sln" Çözüm dosyası listelenir.</span><span class="sxs-lookup"><span data-stu-id="234b7-166">The "DebuggingExample.sln" solution file will be listed as the most recently used file.</span></span>

4. <span data-ttu-id="234b7-167">Açık olarak Form1 **Form Tasarımcısı** seçip **DebugControl** denetimi.</span><span class="sxs-lookup"><span data-stu-id="234b7-167">Open Form1 in the **Forms Designer** and select the **DebugControl** control.</span></span>

5. <span data-ttu-id="234b7-168">Değiştirin `DemoString` özelliği.</span><span class="sxs-lookup"><span data-stu-id="234b7-168">Change the value of the `DemoString` property.</span></span> <span data-ttu-id="234b7-169">Değişiklik yaparsanız, hata ayıklama örneğindeki Visual Studio'nun odağı alır ve yürütmeyi, kesme noktasında durur unutmayın.</span><span class="sxs-lookup"><span data-stu-id="234b7-169">Note that when you commit the change, the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="234b7-170">Özellik erişimcisi aracılığıyla tek adımlı yapabilecekleriniz gibi herhangi bir kod gerekir.</span><span class="sxs-lookup"><span data-stu-id="234b7-170">You can single-step through the property accessor just as your would any other code.</span></span>

6. <span data-ttu-id="234b7-171">Hata ayıklama oturumunuzu ile işiniz bittiğinde, barındırılan bir Visual Studio örneğini kapatma veya tıklayarak çıkabilirsiniz **hata ayıklamayı Durdur** hata ayıklama örneğindeki düğmesi.</span><span class="sxs-lookup"><span data-stu-id="234b7-171">When you are finished with your debugging session, you can exit by dismissing the hosted instance of Visual Studio or by clicking the **Stop Debugging** button in the debugging instance.</span></span>

## <a name="next-steps"></a><span data-ttu-id="234b7-172">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="234b7-172">Next steps</span></span>

<span data-ttu-id="234b7-173">Tasarım zamanında özel kontrollerinizi ayıklayabilirsiniz, Visual Studio IDE denetiminizin etkileşim genişletme için çok sayıda olasılık vardır.</span><span class="sxs-lookup"><span data-stu-id="234b7-173">Now that you can debug your custom controls at design time, there are many possibilities for expanding your control's interaction with the Visual Studio IDE.</span></span>

- <span data-ttu-id="234b7-174">Kullanabileceğiniz <xref:System.ComponentModel.Component.DesignMode%2A> özelliği <xref:System.ComponentModel.Component> yalnızca tasarım zamanında yürütülür kod yazmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="234b7-174">You can use the <xref:System.ComponentModel.Component.DesignMode%2A> property of the <xref:System.ComponentModel.Component> class to write code that will only execute at design time.</span></span> <span data-ttu-id="234b7-175">Ayrıntılar için bkz <xref:System.ComponentModel.Component.DesignMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="234b7-175">For details, see <xref:System.ComponentModel.Component.DesignMode%2A>.</span></span>

- <span data-ttu-id="234b7-176">Birkaç öznitelik özel denetiminizin etkileşim Tasarımcısı ile düzenlemek için denetimin özelliklerini uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="234b7-176">There are several attributes you can apply to your control's properties to manipulate your custom control's interaction with the designer.</span></span> <span data-ttu-id="234b7-177">İçinde bu özniteliklerin bulabilirsiniz <xref:System.ComponentModel?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="234b7-177">You can find these attributes in the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span>

- <span data-ttu-id="234b7-178">Özel denetim için özel bir tasarımcı yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="234b7-178">You can write a custom designer for your custom control.</span></span> <span data-ttu-id="234b7-179">Bu, Visual Studio tarafından kullanıma sunulan Genişletilebilir Tasarımcı altyapısını kullanarak tasarım deneyimi üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="234b7-179">This gives you complete control over the design experience using the extensible designer infrastructure exposed by Visual Studio.</span></span> <span data-ttu-id="234b7-180">Ayrıntılar için bkz [izlenecek yol: Oluşturma bir Windows Forms Visual Studio tasarım zamanı özelliklerinden yararlanır denetimin](creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="234b7-180">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="234b7-181">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="234b7-181">See also</span></span>

- [<span data-ttu-id="234b7-182">İzlenecek yol: Visual Studio tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="234b7-182">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)
- <span data-ttu-id="234b7-183">[Nasıl yapılır: Erişim tasarım zamanı Hizmetleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171822(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="234b7-183">[How to: Access Design-Time Services](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171822(v=vs.120))</span></span>
- <span data-ttu-id="234b7-184">[Nasıl yapılır: Windows Forms'ta erişim tasarım zamanı desteği](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171827(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="234b7-184">[How to: Access Design-Time Support in Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171827(v=vs.120))</span></span>
