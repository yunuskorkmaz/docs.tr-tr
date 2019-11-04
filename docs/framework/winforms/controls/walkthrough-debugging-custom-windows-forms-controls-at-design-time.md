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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a8572c1e70e36faf3a179de7a69e88e9cf1e781b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460618"
---
# <a name="walkthrough-debug-custom-windows-forms-controls-at-design-time"></a><span data-ttu-id="0cb13-102">İzlenecek yol: tasarım zamanında özel Windows Forms Denetimlerinde hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="0cb13-102">Walkthrough: Debug Custom Windows Forms Controls at Design Time</span></span>

<span data-ttu-id="0cb13-103">Özel bir denetim oluşturduğunuzda, genellikle tasarım zamanı davranışından hata ayıklamanın gerekli olduğunu fark edersiniz.</span><span class="sxs-lookup"><span data-stu-id="0cb13-103">When you create a custom control, you will often find it necessary to debug its design-time behavior.</span></span> <span data-ttu-id="0cb13-104">Özel denetiminiz için özel tasarımcı yazıyorsanız bu özellikle doğrudur.</span><span class="sxs-lookup"><span data-stu-id="0cb13-104">This is especially true if you are authoring a custom designer for your custom control.</span></span> <span data-ttu-id="0cb13-105">Ayrıntılar için bkz. [Izlenecek yol: Visual Studio tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma](creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="0cb13-105">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md).</span></span>

<span data-ttu-id="0cb13-106">Visual Studio 'Yu kullanarak özel denetimlerde hata ayıklaması yapabilirsiniz, tıpkı diğer .NET Framework sınıflarında hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cb13-106">You can debug your custom controls using Visual Studio, just as you would debug any other .NET Framework classes.</span></span> <span data-ttu-id="0cb13-107">Fark, Visual Studio 'nun özel denetiminizin kodunu çalıştıran ayrı bir örneğinde hata ayıklamanın farkından oluşur.</span><span class="sxs-lookup"><span data-stu-id="0cb13-107">The difference is that you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="0cb13-108">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="0cb13-108">Create the project</span></span>

<span data-ttu-id="0cb13-109">İlk adım uygulama projesini oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="0cb13-109">The first step is to create the application project.</span></span> <span data-ttu-id="0cb13-110">Bu projeyi, özel denetimi barındıran uygulamayı oluşturmak için kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0cb13-110">You will use this project to build the application that hosts the custom control.</span></span>

<span data-ttu-id="0cb13-111">Visual Studio 'da bir Windows uygulama projesi oluşturun ve **DebuggingExample**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="0cb13-111">In Visual Studio, create a Windows Application project, and name it **DebuggingExample**.</span></span>

## <a name="create-the-control-library-project"></a><span data-ttu-id="0cb13-112">Denetim kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="0cb13-112">Create the control library project</span></span>

1. <span data-ttu-id="0cb13-113">Çözüme bir **Windows Denetim Kitaplığı** projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0cb13-113">Add a **Windows Control Library** project to the solution.</span></span>

2. <span data-ttu-id="0cb13-114">DebugControlLibrary projesine yeni bir **UserControl** öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0cb13-114">Add a new **UserControl** item to the DebugControlLibrary project.</span></span> <span data-ttu-id="0cb13-115">**DebugControl**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="0cb13-115">Name it **DebugControl**.</span></span>

3. <span data-ttu-id="0cb13-116">**Çözüm Gezgini**, kod dosyasını UserControl1 temel adıyla silerek projenin varsayılan denetimini silin.</span><span class="sxs-lookup"><span data-stu-id="0cb13-116">In **Solution Explorer**, delete the project's default control by deleting the code file with a base name of UserControl1.</span></span>

4. <span data-ttu-id="0cb13-117">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0cb13-117">Build the solution.</span></span>

## <a name="checkpoint"></a><span data-ttu-id="0cb13-118">Mak</span><span class="sxs-lookup"><span data-stu-id="0cb13-118">Checkpoint</span></span>

<span data-ttu-id="0cb13-119">Bu noktada, **araç kutusunda**özel denetiminizi görebileceksiniz.</span><span class="sxs-lookup"><span data-stu-id="0cb13-119">At this point, you will be able to see your custom control in the **Toolbox**.</span></span>

<span data-ttu-id="0cb13-120">İlerleme durumunu denetlemek için **DebugControlLibrary bileşenleri** adlı yeni sekmeyi bulun ve seçmek için tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0cb13-120">To check your progress, find the new tab called **DebugControlLibrary Components** and click to select it.</span></span> <span data-ttu-id="0cb13-121">Açıldığında, denetimizin, simgenin yanında **DebugControl** olarak listelendiğini göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="0cb13-121">When it opens, you will see your control listed as **DebugControl** with the default icon beside it.</span></span>

## <a name="add-a-property-to-your-custom-control"></a><span data-ttu-id="0cb13-122">Özel denetimi bir özellik ekleyin</span><span class="sxs-lookup"><span data-stu-id="0cb13-122">Add a property to your custom control</span></span>

<span data-ttu-id="0cb13-123">Özel denetimizin kodunun tasarım zamanında çalıştığını göstermek için, özelliği uygulayan kodda bir özellik ekleyeceksiniz ve bir kesme noktası ayarlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0cb13-123">To demonstrate that your custom control's code is running at design-time, you will add a property and set a breakpoint in the code that implements the property.</span></span>

1. <span data-ttu-id="0cb13-124">**Kod düzenleyicisinde** **DebugControl** ' i açın.</span><span class="sxs-lookup"><span data-stu-id="0cb13-124">Open **DebugControl** in the **Code Editor**.</span></span> <span data-ttu-id="0cb13-125">Aşağıdaki kodu sınıf tanımına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0cb13-125">Add the following code to the class definition:</span></span>

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

2. <span data-ttu-id="0cb13-126">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0cb13-126">Build the solution.</span></span>

## <a name="add-your-custom-control-to-the-host-form"></a><span data-ttu-id="0cb13-127">Özel denetiminizi ana bilgisayar formuna ekleme</span><span class="sxs-lookup"><span data-stu-id="0cb13-127">Add your custom control to the host form</span></span>

<span data-ttu-id="0cb13-128">Özel denetiminizin tasarım zamanı davranışının hatalarını ayıklamak için, bir ana bilgisayar formuna özel denetim sınıfının bir örneğini yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cb13-128">To debug the design-time behavior of your custom control, you will place an instance of the custom control class on a host form.</span></span>

1. <span data-ttu-id="0cb13-129">"DebuggingExample" projesinde, **Windows Form Tasarımcısı**Form1 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="0cb13-129">In the "DebuggingExample" project, open Form1 in the **Windows Forms Designer**.</span></span>

2. <span data-ttu-id="0cb13-130">**Araç kutusunda** **DebugControlLibrary bileşenleri** sekmesini açın ve bir **DebugControl** örneğini form üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="0cb13-130">In the **Toolbox**, open the **DebugControlLibrary Components** tab and drag a **DebugControl** instance onto the form.</span></span>

3. <span data-ttu-id="0cb13-131">**Özellikler** penceresinde `DemoString` özel özelliğini bulun.</span><span class="sxs-lookup"><span data-stu-id="0cb13-131">Find the `DemoString` custom property in the **Properties** window.</span></span> <span data-ttu-id="0cb13-132">Değerini diğer tüm özellikler gibi değiştirebileceğinizi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0cb13-132">Note that you can change its value as you would any other property.</span></span> <span data-ttu-id="0cb13-133">Ayrıca, `DemoString` özelliği seçildiğinde özelliğin açıklama dizesinin **Özellikler** penceresinin altında göründüğünü unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0cb13-133">Also note that when the `DemoString` property is selected, the property's description string appears at the bottom of the **Properties** window.</span></span>

## <a name="set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="0cb13-134">Projeyi tasarım zamanı hata ayıklama için ayarlama</span><span class="sxs-lookup"><span data-stu-id="0cb13-134">Set up the project for design-time debugging</span></span>

<span data-ttu-id="0cb13-135">Özel denetiminizin tasarım zamanı davranışınızda hata ayıklamak için, özel denetiminizin kodunu çalıştıran ayrı bir Visual Studio örneğinden hata ayıklayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0cb13-135">To debug your custom control's design-time behavior, you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>

1. <span data-ttu-id="0cb13-136">**Çözüm Gezgini** **DebugControlLibrary** projesine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="0cb13-136">Right-click on the **DebugControlLibrary** project in the **Solution Explorer** and select **Properties**.</span></span>

2. <span data-ttu-id="0cb13-137">**DebugControlLibrary** Özellik sayfasında, **Hata Ayıkla** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0cb13-137">In the **DebugControlLibrary** property sheet, select the **Debug** tab.</span></span>

     <span data-ttu-id="0cb13-138">**Başlangıç eylemi** bölümünde **dış program Başlat**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="0cb13-138">In the **Start Action** section, select **Start external program**.</span></span> <span data-ttu-id="0cb13-139">Visual Studio 'nun ayrı bir örneğinde hata ayıkladığınızda, Visual Studio IDE 'ye gözatabilmek için üç nokta (Visual](./media/visual-studio-ellipsis-button.png)Studio 'nun Özellikler penceresi![) düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="0cb13-139">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="0cb13-140">Yürütülebilir dosyanın adı **devenv. exe**' dir ve varsayılan konuma yüklediyseniz, yolu *% ProgramFiles (x86)% \ Microsoft Visual studio\2019\\\<Edition > \Common7\IDE*olur.</span><span class="sxs-lookup"><span data-stu-id="0cb13-140">The name of the executable file is **devenv.exe**, and if you installed to the default location, its path is *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\\\<edition>\Common7\IDE*.</span></span>

3. <span data-ttu-id="0cb13-141">İletişim kutusunu kapatmak için **Tamam ' ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="0cb13-141">Select **OK** to close the dialog box.</span></span>

4. <span data-ttu-id="0cb13-142">**DebugControlLibrary** projesine sağ tıklayın ve bu hata ayıklama yapılandırmasını etkinleştirmek Için **Başlangıç projesi olarak ayarla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="0cb13-142">Right-click the **DebugControlLibrary** project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>

## <a name="debug-your-custom-control-at-design-time"></a><span data-ttu-id="0cb13-143">Tasarım zamanında özel denetimi hata ayıklaması yapın</span><span class="sxs-lookup"><span data-stu-id="0cb13-143">Debug your custom control at design time</span></span>

<span data-ttu-id="0cb13-144">Artık tasarım modunda çalışırken özel denetimi hata ayıklamaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="0cb13-144">Now you are ready to debug your custom control as it runs in design mode.</span></span> <span data-ttu-id="0cb13-145">Hata ayıklama oturumunu başlattığınızda, Visual Studio 'nun yeni bir örneği oluşturulur ve bunu "DebuggingExample" çözümünü yüklemek için kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0cb13-145">When you start the debugging session, a new instance of Visual Studio will be created, and you will use it to load the "DebuggingExample" solution.</span></span> <span data-ttu-id="0cb13-146">**Form tasarımcısında**Form1 ' i açtığınızda, özel denetiminizin bir örneği oluşturulur ve çalışmaya başlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="0cb13-146">When you open Form1 in the **Forms Designer**, an instance of your custom control will be created and will start running.</span></span>

1. <span data-ttu-id="0cb13-147">**Kod düzenleyicisinde** **DebugControl** kaynak dosyasını açın ve `DemoString` özelliğinin `Set` erişimcisine bir kesme noktası yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="0cb13-147">Open the **DebugControl** source file in the **Code Editor** and place a breakpoint on the `Set` accessor of the `DemoString` property.</span></span>

2. <span data-ttu-id="0cb13-148">Hata ayıklama oturumu başlatmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0cb13-148">Press **F5** to start the debugging session.</span></span> <span data-ttu-id="0cb13-149">Visual Studio 'nun yeni bir örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0cb13-149">A new instance of Visual Studio is created.</span></span> <span data-ttu-id="0cb13-150">Örnekler arasında iki şekilde ayrım yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0cb13-150">You can distinguish between the instances in two ways:</span></span>

    - <span data-ttu-id="0cb13-151">Hata ayıklama örneği, başlık çubuğunda **çalışan** sözcüğe sahiptir</span><span class="sxs-lookup"><span data-stu-id="0cb13-151">The debugging instance has the word **Running** in its title bar</span></span>

    - <span data-ttu-id="0cb13-152">Hata ayıklama örneğinde **hata ayıklama** araç çubuğundaki **Başlat** düğmesi devre dışıdır</span><span class="sxs-lookup"><span data-stu-id="0cb13-152">The debugging instance has the **Start** button on its **Debug** toolbar disabled</span></span>

   <span data-ttu-id="0cb13-153">Kesme noktası hata ayıklama örneğinde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0cb13-153">Your breakpoint is set in the debugging instance.</span></span>

3. <span data-ttu-id="0cb13-154">Visual Studio 'nun yeni örneğinde, "DebuggingExample" çözümünü açın.</span><span class="sxs-lookup"><span data-stu-id="0cb13-154">In the new instance of Visual Studio, open the "DebuggingExample" solution.</span></span> <span data-ttu-id="0cb13-155">**Dosya** menüsünden **son projeler** ' i seçerek çözümü kolayca bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cb13-155">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="0cb13-156">"DebuggingExample. sln" çözüm dosyası en son kullanılan dosya olarak listelenecektir.</span><span class="sxs-lookup"><span data-stu-id="0cb13-156">The "DebuggingExample.sln" solution file will be listed as the most recently used file.</span></span>

4. <span data-ttu-id="0cb13-157">**Form tasarımcısında** Form1 ' i açın ve **DebugControl** denetimini seçin.</span><span class="sxs-lookup"><span data-stu-id="0cb13-157">Open Form1 in the **Forms Designer** and select the **DebugControl** control.</span></span>

5. <span data-ttu-id="0cb13-158">`DemoString` özelliğinin değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0cb13-158">Change the value of the `DemoString` property.</span></span> <span data-ttu-id="0cb13-159">Değişikliği kaydettiğinizde, Visual Studio 'daki hata ayıklama örneği odak ve yürütme, kesme noktasında duraklar.</span><span class="sxs-lookup"><span data-stu-id="0cb13-159">When you commit the change, the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="0cb13-160">Özellik erişimcisinde, tıpkı diğer kodlar gibi tek adım izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cb13-160">You can single-step through the property accessor just as your would any other code.</span></span>

6. <span data-ttu-id="0cb13-161">Hata ayıklamayı durdurmak için, Visual Studio 'nun barındırılan örneğinden çıkın veya hata ayıklama örneğindeki **hata ayıklamayı Durdur** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0cb13-161">To stop debugging, exit the hosted instance of Visual Studio or select the **Stop Debugging** button in the debugging instance.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0cb13-162">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="0cb13-162">Next steps</span></span>

<span data-ttu-id="0cb13-163">Tasarım zamanında özel denetimlerde hata ayıklayabildiğinize göre, Visual Studio IDE ile denetiminizin etkileşimini genişletmeye yönelik birçok olasılık vardır.</span><span class="sxs-lookup"><span data-stu-id="0cb13-163">Now that you can debug your custom controls at design time, there are many possibilities for expanding your control's interaction with the Visual Studio IDE.</span></span>

- <span data-ttu-id="0cb13-164">Yalnızca tasarım zamanında yürütülecek kodu yazmak için <xref:System.ComponentModel.Component> sınıfının <xref:System.ComponentModel.Component.DesignMode%2A> özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cb13-164">You can use the <xref:System.ComponentModel.Component.DesignMode%2A> property of the <xref:System.ComponentModel.Component> class to write code that will only execute at design time.</span></span> <span data-ttu-id="0cb13-165">Ayrıntılar için bkz. <xref:System.ComponentModel.Component.DesignMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cb13-165">For details, see <xref:System.ComponentModel.Component.DesignMode%2A>.</span></span>

- <span data-ttu-id="0cb13-166">Özel denetiminizin, tasarımcı ile etkileşimini işlemek için denetiminizin özelliklerine uygulayabileceğiniz birkaç öznitelik vardır.</span><span class="sxs-lookup"><span data-stu-id="0cb13-166">There are several attributes you can apply to your control's properties to manipulate your custom control's interaction with the designer.</span></span> <span data-ttu-id="0cb13-167">Bu öznitelikleri <xref:System.ComponentModel?displayProperty=nameWithType> ad alanında bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cb13-167">You can find these attributes in the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span>

- <span data-ttu-id="0cb13-168">Özel denetiminiz için özel tasarımcı yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cb13-168">You can write a custom designer for your custom control.</span></span> <span data-ttu-id="0cb13-169">Bu sayede, Visual Studio tarafından sunulan Genişletilebilir tasarımcı altyapısını kullanarak tasarım deneyimi üzerinde tüm denetim elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="0cb13-169">This gives you complete control over the design experience using the extensible designer infrastructure exposed by Visual Studio.</span></span> <span data-ttu-id="0cb13-170">Ayrıntılar için bkz. [Izlenecek yol: Visual Studio tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma](creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="0cb13-170">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0cb13-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cb13-171">See also</span></span>

- [<span data-ttu-id="0cb13-172">İzlenecek yol: Visual Studio Tasarım-Zamanı Özellikleri'nden Faydalanan Windows Forms Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0cb13-172">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)
