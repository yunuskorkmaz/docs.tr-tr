---
title: "İzlenecek yol: Visual Studio Tasarım-Zamanı Özellikleri'nden Faydalanan Windows Forms Denetimi Oluşturma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms controls, creating
- design-time functionality [Windows Forms], Windows Forms
- DocumentDesigner class [Windows Forms]
- walkthroughs [Windows Forms], controls
ms.assetid: 6f487c59-cb38-4afa-ad2e-95edacb1d626
ms.openlocfilehash: c8d04725a576c9e24a4b7d4aec1251516a8c544c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666226"
---
# <a name="walkthrough-creating-a-windows-forms-control-that-takes-advantage-of-visual-studio-design-time-features"></a><span data-ttu-id="fecd3-102">İzlenecek yol: Visual Studio Tasarım-Zamanı Özellikleri'nden Faydalanan Windows Forms Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fecd3-102">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>

<span data-ttu-id="fecd3-103">Özel bir denetim için tasarım zamanı deneyimi, ilişkili bir özel tasarımcı Authoring ile geliştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-103">The design-time experience for a custom control can be enhanced by authoring an associated custom designer.</span></span>

<span data-ttu-id="fecd3-104">Bu izlenecek yol, özel bir denetim için özel tasarımcı oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-104">This walkthrough illustrates how to create a custom designer for a custom control.</span></span> <span data-ttu-id="fecd3-105">`MarqueeControl` Adlı`MarqueeControlRootDesigner`bir türü ve ilişkili bir tasarımcı sınıfını uygulayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="fecd3-105">You will implement a `MarqueeControl` type and an associated designer class, called `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="fecd3-106">`MarqueeControl` Türü, animasyonlu ışıklar ve yanıp sönen metinle benzer bir sinemalı yazı tipine benzer bir ekran uygular.</span><span class="sxs-lookup"><span data-stu-id="fecd3-106">The `MarqueeControl` type implements a display similar to a theater marquee, with animated lights and flashing text.</span></span>

<span data-ttu-id="fecd3-107">Bu denetim için tasarımcı, tasarım ortamıyla birlikte etkileşimde bulunur ve özel bir tasarım zamanı deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fecd3-107">The designer for this control interacts with the design environment to provide a custom design-time experience.</span></span> <span data-ttu-id="fecd3-108">Özel tasarımcı sayesinde, bir özel `MarqueeControl` uygulamayı animasyonlu ışıklar ve yanıp sönen metni birçok birleşimde bir araya getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fecd3-108">With the custom designer, you can assemble a custom `MarqueeControl` implementation with animated lights and flashing text in many combinations.</span></span> <span data-ttu-id="fecd3-109">Bir form üzerinde, diğer Windows Forms denetimleri gibi, birleştirilmiş denetimi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fecd3-109">You can use the assembled control on a form like any other Windows Forms control.</span></span>

<span data-ttu-id="fecd3-110">Bu izlenecek yolda gösterilen görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="fecd3-110">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="fecd3-111">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fecd3-111">Creating the Project</span></span>

- <span data-ttu-id="fecd3-112">Denetim kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="fecd3-112">Creating a Control Library Project</span></span>

- <span data-ttu-id="fecd3-113">Özel denetim projesine başvurma</span><span class="sxs-lookup"><span data-stu-id="fecd3-113">Referencing the Custom Control Project</span></span>

- <span data-ttu-id="fecd3-114">Özel bir denetim ve özel tasarımcı tanımlama</span><span class="sxs-lookup"><span data-stu-id="fecd3-114">Defining a Custom Control and Its Custom Designer</span></span>

- <span data-ttu-id="fecd3-115">Özel denetiminizin bir örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="fecd3-115">Creating an Instance of Your Custom Control</span></span>

- <span data-ttu-id="fecd3-116">Projeyi tasarım zamanı hata ayıklama için ayarlama</span><span class="sxs-lookup"><span data-stu-id="fecd3-116">Setting Up the Project for Design-Time Debugging</span></span>

- <span data-ttu-id="fecd3-117">Özel denetiminizi uygulama</span><span class="sxs-lookup"><span data-stu-id="fecd3-117">Implementing Your Custom Control</span></span>

- <span data-ttu-id="fecd3-118">Özel denetiminiz için bir alt denetim oluşturma</span><span class="sxs-lookup"><span data-stu-id="fecd3-118">Creating a Child Control for Your Custom Control</span></span>

- <span data-ttu-id="fecd3-119">MarqueeBorder alt denetimini oluşturma</span><span class="sxs-lookup"><span data-stu-id="fecd3-119">Create the MarqueeBorder Child Control</span></span>

- <span data-ttu-id="fecd3-120">Gölge ve filtre özelliklerine özel tasarımcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="fecd3-120">Creating a Custom Designer to Shadow and Filter Properties</span></span>

- <span data-ttu-id="fecd3-121">Bileşen değişikliklerini işleme</span><span class="sxs-lookup"><span data-stu-id="fecd3-121">Handling Component Changes</span></span>

- <span data-ttu-id="fecd3-122">Özel tasarımcıya tasarımcı fiilleri ekleme</span><span class="sxs-lookup"><span data-stu-id="fecd3-122">Adding Designer Verbs to your Custom Designer</span></span>

- <span data-ttu-id="fecd3-123">Özel Uııtypeınfo Düzenleyicisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="fecd3-123">Creating a Custom UITypeEditor</span></span>

- <span data-ttu-id="fecd3-124">Tasarımcıda özel denetiminizi test etme</span><span class="sxs-lookup"><span data-stu-id="fecd3-124">Testing your Custom Control in the Designer</span></span>

<span data-ttu-id="fecd3-125">İşiniz bittiğinde, özel denetiminiz aşağıdakine benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="fecd3-125">When you are finished, your custom control will look something like the following:</span></span>

![Metin ve Başlat ve Durdur düğmelerini gösteren bir kayan yazıyı gösteren uygulama.](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

<span data-ttu-id="fecd3-127">Tüm kod listesi için bkz [. nasıl yapılır: Tasarım zamanı özelliklerinden](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))faydalanan bir Windows Forms denetimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fecd3-127">For the complete code listing, see [How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fecd3-128">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="fecd3-128">Prerequisites</span></span>

<span data-ttu-id="fecd3-129">Bu izlenecek yolu tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-129">In order to complete this walkthrough, you'll need Visual Studio.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="fecd3-130">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fecd3-130">Creating the Project</span></span>

<span data-ttu-id="fecd3-131">İlk adım uygulama projesini oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="fecd3-131">The first step is to create the application project.</span></span> <span data-ttu-id="fecd3-132">Bu projeyi, özel denetimi barındıran uygulamayı oluşturmak için kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="fecd3-132">You will use this project to build the application that hosts the custom control.</span></span>

<span data-ttu-id="fecd3-133">Visual Studio 'yu açın ve "MarqueeControlTest" adlı bir Windows Forms uygulama projesi oluşturun (**Dosya** > **Yeni** > **Proje** > **görseli C#**  veya **Visual Basic** . >  **Klasik Masaüstü** **Windows Forms uygulama).**  > </span><span class="sxs-lookup"><span data-stu-id="fecd3-133">Open Visual Studio and create a Windows Forms Application project called "MarqueeControlTest" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

## <a name="creating-a-control-library-project"></a><span data-ttu-id="fecd3-134">Denetim kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="fecd3-134">Creating a Control Library Project</span></span>

<span data-ttu-id="fecd3-135">Sonraki adım, denetim kitaplığı projesi oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="fecd3-135">The next step is to create the control library project.</span></span> <span data-ttu-id="fecd3-136">Yeni bir özel denetim ve buna karşılık gelen özel tasarımcı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="fecd3-136">You will create a new custom control and its corresponding custom designer.</span></span>

### <a name="to-create-the-control-library-project"></a><span data-ttu-id="fecd3-137">Denetim kitaplığı projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fecd3-137">To create the control library project</span></span>

1. <span data-ttu-id="fecd3-138">Çözüme bir Windows Forms denetim kitaplığı projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-138">Add a Windows Forms Control Library project to the solution.</span></span> <span data-ttu-id="fecd3-139">Projeyi "MarqueeControlLibrary" olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-139">Name the project "MarqueeControlLibrary."</span></span>

2. <span data-ttu-id="fecd3-140">**Çözüm Gezgini**kullanarak, tercih ettiğiniz dile bağlı olarak, "UserControl1.cs" veya "UserControl1. vb" adlı kaynak dosyayı silerek projenin varsayılan denetimini silin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-140">Using **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span> <span data-ttu-id="fecd3-141">Daha fazla bilgi için [nasıl yapılır: Öğeleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100))kaldırma, silme ve hariç tutma.</span><span class="sxs-lookup"><span data-stu-id="fecd3-141">For more information, see [How to: Remove, Delete, and Exclude Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span></span>

3. <span data-ttu-id="fecd3-142">`MarqueeControlLibrary` Projeye yeni <xref:System.Windows.Forms.UserControl> bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-142">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="fecd3-143">Yeni kaynak dosyasına "MarqueeControl" temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-143">Give the new source file a base name of "MarqueeControl."</span></span>

4. <span data-ttu-id="fecd3-144">**Çözüm Gezgini**kullanarak `MarqueeControlLibrary` projede yeni bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fecd3-144">Using **Solution Explorer**, create a new folder in the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="fecd3-145">Daha fazla bilgi için [nasıl yapılır: Yeni proje öğeleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100))ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-145">For more information, see [How to: Add New Project Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span></span> <span data-ttu-id="fecd3-146">"Tasarım" adlı yeni klasörü adlandırın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-146">Name the new folder "Design."</span></span>

5. <span data-ttu-id="fecd3-147">**Tasarım** klasörüne sağ tıklayın ve yeni bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-147">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="fecd3-148">Kaynak dosyaya "MarqueeControlRootDesigner" temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-148">Give the source file a base name of "MarqueeControlRootDesigner."</span></span>

6. <span data-ttu-id="fecd3-149">System. Design derlemesinden türler kullanmanız gerekir, bu nedenle bu başvuruyu `MarqueeControlLibrary` projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-149">You will need to use types from the System.Design assembly, so add this reference to the `MarqueeControlLibrary` project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fecd3-150">System. Design derlemesini kullanmak için, projenizin .NET Framework Istemci profilinin değil .NET Framework tam sürümünü hedeflemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-150">To use the System.Design assembly, your project must target the full version of the .NET Framework, not the .NET Framework Client Profile.</span></span> <span data-ttu-id="fecd3-151">Hedef Framework 'ü değiştirmek için bkz [. nasıl yapılır: .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)bir sürümünü hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-151">To change the target framework, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span>

## <a name="referencing-the-custom-control-project"></a><span data-ttu-id="fecd3-152">Özel denetim projesine başvurma</span><span class="sxs-lookup"><span data-stu-id="fecd3-152">Referencing the Custom Control Project</span></span>

<span data-ttu-id="fecd3-153">Bu `MarqueeControlTest` projeyi, özel denetimi test etmek için kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="fecd3-153">You will use the `MarqueeControlTest` project to test the custom control.</span></span> <span data-ttu-id="fecd3-154">`MarqueeControlLibrary` Derlemeye bir proje başvurusu eklediğinizde test projesi özel denetimden haberdar olur.</span><span class="sxs-lookup"><span data-stu-id="fecd3-154">The test project will become aware of the custom control when you add a project reference to the `MarqueeControlLibrary` assembly.</span></span>

### <a name="to-reference-the-custom-control-project"></a><span data-ttu-id="fecd3-155">Özel denetim projesine başvurmak için</span><span class="sxs-lookup"><span data-stu-id="fecd3-155">To reference the custom control project</span></span>

- <span data-ttu-id="fecd3-156">Projede, `MarqueeControlLibrary` derlemeye bir proje başvurusu ekleyin. `MarqueeControlTest`</span><span class="sxs-lookup"><span data-stu-id="fecd3-156">In the `MarqueeControlTest` project, add a project reference to the `MarqueeControlLibrary` assembly.</span></span> <span data-ttu-id="fecd3-157">`MarqueeControlLibrary` Derlemeye doğrudan başvurmak yerine **Başvuru Ekle** iletişim kutusundaki **Projeler** sekmesini kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="fecd3-157">Be sure to use the **Projects** tab in the **Add Reference** dialog box instead of referencing the `MarqueeControlLibrary` assembly directly.</span></span>

## <a name="defining-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="fecd3-158">Özel bir denetim ve özel tasarımcı tanımlama</span><span class="sxs-lookup"><span data-stu-id="fecd3-158">Defining a Custom Control and Its Custom Designer</span></span>
 <span data-ttu-id="fecd3-159">Özel denetiminiz <xref:System.Windows.Forms.UserControl> sınıfından türecektir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-159">Your custom control will derive from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="fecd3-160">Bu, denetiminizin diğer denetimleri içermesini sağlar ve denetimi, varsayılan işlevselliğin harika olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fecd3-160">This allows your control to contain other controls, and it gives your control a great deal of default functionality.</span></span>

 <span data-ttu-id="fecd3-161">Özel denetiminizin ilişkili bir özel Tasarımcısı olacak.</span><span class="sxs-lookup"><span data-stu-id="fecd3-161">Your custom control will have an associated custom designer.</span></span> <span data-ttu-id="fecd3-162">Bu, özel denetiminiz için özel olarak uyarlanmış benzersiz bir tasarım deneyimi oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fecd3-162">This allows you to create a unique design experience tailored specifically for your custom control.</span></span>

 <span data-ttu-id="fecd3-163"><xref:System.ComponentModel.DesignerAttribute> Sınıfını kullanarak denetimi Tasarımcı ile ilişkilendirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fecd3-163">You associate the control with its designer by using the <xref:System.ComponentModel.DesignerAttribute> class.</span></span> <span data-ttu-id="fecd3-164">Özel denetiminizin tüm tasarım zamanı davranışını geliştirmekte olduğunuzdan, özel tasarımcı <xref:System.ComponentModel.Design.IRootDesigner> arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="fecd3-164">Because you are developing the entire design-time behavior of your custom control, the custom designer will implement the <xref:System.ComponentModel.Design.IRootDesigner> interface.</span></span>

### <a name="to-define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="fecd3-165">Özel bir denetim ve özel tasarımcı tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="fecd3-165">To define a custom control and its custom designer</span></span>

1. <span data-ttu-id="fecd3-166">Kaynak dosyasını kod düzenleyicisinde açın. `MarqueeControl`</span><span class="sxs-lookup"><span data-stu-id="fecd3-166">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="fecd3-167">Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="fecd3-167">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. <span data-ttu-id="fecd3-168"><xref:System.ComponentModel.DesignerAttribute> Sınıfını`MarqueeControl` sınıf bildirimine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-168">Add the <xref:System.ComponentModel.DesignerAttribute> to the `MarqueeControl` class declaration.</span></span> <span data-ttu-id="fecd3-169">Bu, özel denetimi Tasarımcı ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-169">This associates the custom control with its designer.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. <span data-ttu-id="fecd3-170">Kaynak dosyasını kod düzenleyicisinde açın. `MarqueeControlRootDesigner`</span><span class="sxs-lookup"><span data-stu-id="fecd3-170">Open the `MarqueeControlRootDesigner` source file in the **Code Editor**.</span></span> <span data-ttu-id="fecd3-171">Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="fecd3-171">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. <span data-ttu-id="fecd3-172">Bildirimini `MarqueeControlRootDesigner` <xref:System.Windows.Forms.Design.DocumentDesigner> sınıfından devralacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-172">Change the declaration of `MarqueeControlRootDesigner` to inherit from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="fecd3-173">**Araç kutusu**ile tasarımcı etkileşimini belirtmek içinöğesiniuygulayın.<xref:System.ComponentModel.ToolboxItemFilterAttribute></span><span class="sxs-lookup"><span data-stu-id="fecd3-173">Apply the <xref:System.ComponentModel.ToolboxItemFilterAttribute> to specify the designer interaction with the **Toolbox**.</span></span>

     <span data-ttu-id="fecd3-174">**Göz önünde** `MarqueeControlRootDesigner` Sınıfının tanımı, "MarqueeControlLibrary. Design" adlı bir ad alanı içine alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="fecd3-174">**Note** The definition for the `MarqueeControlRootDesigner` class has been enclosed in a namespace called "MarqueeControlLibrary.Design."</span></span> <span data-ttu-id="fecd3-175">Bu bildirim, tasarımcıyı tasarımla ilgili türler için ayrılmış özel bir ad alanına koyar.</span><span class="sxs-lookup"><span data-stu-id="fecd3-175">This declaration places the designer in a special namespace reserved for design-related types.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. <span data-ttu-id="fecd3-176">`MarqueeControlRootDesigner` Sınıf için oluşturucuyu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-176">Define the constructor for the `MarqueeControlRootDesigner` class.</span></span> <span data-ttu-id="fecd3-177">Oluşturucu gövdesine <xref:System.Diagnostics.Trace.WriteLine%2A> bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-177">Insert a <xref:System.Diagnostics.Trace.WriteLine%2A> statement in the constructor body.</span></span> <span data-ttu-id="fecd3-178">Bu, hata ayıklama amacıyla yararlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fecd3-178">This will be useful for debugging purposes.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="creating-an-instance-of-your-custom-control"></a><span data-ttu-id="fecd3-179">Özel denetiminizin bir örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="fecd3-179">Creating an Instance of Your Custom Control</span></span>
 <span data-ttu-id="fecd3-180">Denetiminizin özel tasarım zamanı davranışını gözlemlemek için, bir denetimin örneğini Project 'teki `MarqueeControlTest` forma yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fecd3-180">To observe the custom design-time behavior of your control, you will place an instance of your control on the form in `MarqueeControlTest` project.</span></span>

### <a name="to-create-an-instance-of-your-custom-control"></a><span data-ttu-id="fecd3-181">Özel denetiminizin bir örneğini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fecd3-181">To create an instance of your custom control</span></span>

1. <span data-ttu-id="fecd3-182">`MarqueeControlTest` Projeye yeni <xref:System.Windows.Forms.UserControl> bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-182">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlTest` project.</span></span> <span data-ttu-id="fecd3-183">Yeni kaynak dosyasına "DemoMarqueeControl" temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-183">Give the new source file a base name of "DemoMarqueeControl."</span></span>

2. <span data-ttu-id="fecd3-184">Dosyayı kod düzenleyicisinde açın. `DemoMarqueeControl`</span><span class="sxs-lookup"><span data-stu-id="fecd3-184">Open the `DemoMarqueeControl` file in the **Code Editor**.</span></span> <span data-ttu-id="fecd3-185">Dosyanın en üstünde, `MarqueeControlLibrary` ad alanını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="fecd3-185">At the top of the file, import the `MarqueeControlLibrary` namespace:</span></span>

```vb
Imports MarqueeControlLibrary
```

```csharp
using MarqueeControlLibrary;
```

1. <span data-ttu-id="fecd3-186">Bildirimini `DemoMarqueeControl` `MarqueeControl` sınıfından devralacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-186">Change the declaration of `DemoMarqueeControl` to inherit from the `MarqueeControl` class.</span></span>

2. <span data-ttu-id="fecd3-187">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fecd3-187">Build the project.</span></span>

3. <span data-ttu-id="fecd3-188">Windows Form Tasarımcısı `Form1` açın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-188">Open `Form1` in the Windows Forms Designer.</span></span>

4. <span data-ttu-id="fecd3-189">**Araç kutusunda** **MarqueeControlTest Components** sekmesini bulun ve açın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-189">Find the **MarqueeControlTest Components** tab in the **Toolbox** and open it.</span></span> <span data-ttu-id="fecd3-190">`DemoMarqueeControl` **Araç kutusundan** bir öğesini formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-190">Drag a `DemoMarqueeControl` from the **Toolbox** onto your form.</span></span>

5. <span data-ttu-id="fecd3-191">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fecd3-191">Build the project.</span></span>

## <a name="setting-up-the-project-for-design-time-debugging"></a><span data-ttu-id="fecd3-192">Projeyi tasarım zamanı hata ayıklama için ayarlama</span><span class="sxs-lookup"><span data-stu-id="fecd3-192">Setting Up the Project for Design-Time Debugging</span></span>

<span data-ttu-id="fecd3-193">Özel bir tasarım zamanı deneyimi geliştirirken, denetimlerinizin ve bileşenlerinizin hata ayıklaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-193">When you are developing a custom design-time experience, it will be necessary to debug your controls and components.</span></span> <span data-ttu-id="fecd3-194">Projenizi tasarım zamanında hata ayıklamaya izin verecek şekilde kurmak için basit bir yol vardır.</span><span class="sxs-lookup"><span data-stu-id="fecd3-194">There is a simple way to set up your project to allow debugging at design time.</span></span> <span data-ttu-id="fecd3-195">Daha fazla bilgi için bkz [. İzlenecek yol: Tasarım zamanında](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)özel Windows Forms Denetimlerinde hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="fecd3-195">For more information, see [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>

### <a name="to-set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="fecd3-196">Projeyi tasarım zamanı hata ayıklama için ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="fecd3-196">To set up the project for design-time debugging</span></span>

1. <span data-ttu-id="fecd3-197">`MarqueeControlLibrary` Projeye sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-197">Right-click the `MarqueeControlLibrary` project and select **Properties**.</span></span>

2. <span data-ttu-id="fecd3-198">"MarqueeControlLibrary Özellik sayfaları" iletişim kutusunda **hata ayıklama** sayfasını seçin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-198">In the "MarqueeControlLibrary Property Pages" dialog box, select the **Debug** page.</span></span>

3. <span data-ttu-id="fecd3-199">**Başlangıç eylemi** bölümünde **dış program Başlat**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-199">In the **Start Action** section, select **Start External Program**.</span></span> <span data-ttu-id="fecd3-200">Visual Studio 'nun ayrı bir örneğinde hata ayıkladığınızda, Visual Studio IDE 'ye gitmek için![üç nokta (Visual](./media/visual-studio-ellipsis-button.png)Studio 'nun Özellikler penceresi) düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-200">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="fecd3-201">Yürütülebilir dosyanın adı devenv. exe ' dir ve varsayılan konuma yüklediyseniz, yolu%programfiles%\Microsoft Visual Studio 9.0 \ Common7\IDE\devenv.exe. ' dir</span><span class="sxs-lookup"><span data-stu-id="fecd3-201">The name of the executable file is devenv.exe, and if you installed to the default location, its path is %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span></span>

4. <span data-ttu-id="fecd3-202">İletişim kutusunu kapatmak için Tamam ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-202">Click OK to close the dialog box.</span></span>

5. <span data-ttu-id="fecd3-203">`MarqueeControlLibrary` Projeye sağ tıklayın ve "başlangıç projesi olarak ayarla" yı seçerek bu hata ayıklama yapılandırmasını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-203">Right-click the `MarqueeControlLibrary` project and select "Set as StartUp Project" to enable this debugging configuration.</span></span>

## <a name="checkpoint"></a><span data-ttu-id="fecd3-204">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="fecd3-204">Checkpoint</span></span>

<span data-ttu-id="fecd3-205">Artık özel denetiminizin tasarım zamanı davranışını hata ayıklamaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="fecd3-205">You are now ready to debug the design-time behavior of your custom control.</span></span> <span data-ttu-id="fecd3-206">Hata ayıklama ortamının doğru şekilde ayarlandığını belirledikten sonra, özel denetim ve özel tasarımcı arasındaki ilişkilendirmeyi test edersiniz.</span><span class="sxs-lookup"><span data-stu-id="fecd3-206">Once you have determined that the debugging environment is set up correctly, you will test the association between the custom control and the custom designer.</span></span>

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a><span data-ttu-id="fecd3-207">Hata ayıklama ortamını ve tasarımcı ilişkilendirmesini test etmek için</span><span class="sxs-lookup"><span data-stu-id="fecd3-207">To test the debugging environment and the designer association</span></span>

1. <span data-ttu-id="fecd3-208">Kaynak dosyasını **kod düzenleyicisinde** açın ve <xref:System.Diagnostics.Trace.WriteLine%2A> deyime bir kesme noktası yerleştirin. `MarqueeControlRootDesigner`</span><span class="sxs-lookup"><span data-stu-id="fecd3-208">Open the `MarqueeControlRootDesigner` source file in the **Code Editor** and place a breakpoint on the <xref:System.Diagnostics.Trace.WriteLine%2A> statement.</span></span>

2. <span data-ttu-id="fecd3-209">Hata ayıklama oturumu başlatmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-209">Press F5 to start the debugging session.</span></span> <span data-ttu-id="fecd3-210">Visual Studio 'nun yeni bir örneğinin oluşturulduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-210">Note that a new instance of Visual Studio is created.</span></span>

3. <span data-ttu-id="fecd3-211">Visual Studio 'nun yeni örneğinde, "MarqueeControlTest" çözümünü açın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-211">In the new instance of Visual Studio, open the "MarqueeControlTest" solution.</span></span> <span data-ttu-id="fecd3-212">**Dosya** menüsünden **son projeler** ' i seçerek çözümü kolayca bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fecd3-212">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="fecd3-213">"MarqueeControlTest. sln" çözüm dosyası en son kullanılan dosya olarak listelenecektir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-213">The "MarqueeControlTest.sln" solution file will be listed as the most recently used file.</span></span>

4. <span data-ttu-id="fecd3-214">`DemoMarqueeControl` Öğesini tasarımcıda açın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-214">Open the `DemoMarqueeControl` in the designer.</span></span> <span data-ttu-id="fecd3-215">Visual Studio 'nun hata ayıklama örneğinin, kesme noktasına odaklanarak ve yürütmenin durduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-215">Note that the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="fecd3-216">Hata ayıklama oturumuna devam etmek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-216">Press F5 to continue the debugging session.</span></span>

<span data-ttu-id="fecd3-217">Bu noktada, özel denetiminizi ve onunla ilişkili özel tasarımcıyı geliştirip hata ayıklamanızın her şey vardır.</span><span class="sxs-lookup"><span data-stu-id="fecd3-217">At this point, everything is in place for you to develop and debug your custom control and its associated custom designer.</span></span> <span data-ttu-id="fecd3-218">Bu izlenecek yolun geri kalanı, denetimin ve tasarımcının özelliklerini uygulama ayrıntılarına odaklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="fecd3-218">The remainder of this walkthrough will concentrate on the details of implementing features of the control and the designer.</span></span>

## <a name="implementing-your-custom-control"></a><span data-ttu-id="fecd3-219">Özel denetiminizi uygulama</span><span class="sxs-lookup"><span data-stu-id="fecd3-219">Implementing Your Custom Control</span></span>

<span data-ttu-id="fecd3-220">, `MarqueeControl` Bir<xref:System.Windows.Forms.UserControl> özelleştirme biraz daha vardır.</span><span class="sxs-lookup"><span data-stu-id="fecd3-220">The `MarqueeControl` is a <xref:System.Windows.Forms.UserControl> with a little bit of customization.</span></span> <span data-ttu-id="fecd3-221">İki yöntem sunar: `Start`, kayan yazı animasyonunu başlatan ve `Stop`animasyonu durduran.</span><span class="sxs-lookup"><span data-stu-id="fecd3-221">It exposes two methods: `Start`, which starts the marquee animation, and `Stop`, which stops the animation.</span></span> <span data-ttu-id="fecd3-222">, `MarqueeControl` `StopMarquee` `StartMarquee` Arabirimini `IMarqueeWidget` uygulayanaltdenetimleriçerdiğindenveherbiraltdenetimivesırasıylaveyöntemleriniherbiraltdenetimdesırasıylaçağırmak`Start`için `Stop` uygulayan `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="fecd3-222">Because the `MarqueeControl` contains child controls that implement the `IMarqueeWidget` interface, `Start` and `Stop` enumerate each child control and call the `StartMarquee` and `StopMarquee` methods, respectively, on each child control that implements `IMarqueeWidget`.</span></span>

<span data-ttu-id="fecd3-223">`MarqueeBorder` Ve `MarqueeControl` denetimleriningörünümü<xref:System.Windows.Forms.Control.OnLayout%2A> düzene bağlıdır, bu nedenle yöntemi ve bu türün alt denetimlerinde yapılan çağrıları <xref:System.Windows.Forms.Control.PerformLayout%2A> geçersiz kılar. `MarqueeText`</span><span class="sxs-lookup"><span data-stu-id="fecd3-223">The appearance of the `MarqueeBorder` and `MarqueeText` controls is dependent on the layout, so `MarqueeControl` overrides the <xref:System.Windows.Forms.Control.OnLayout%2A> method and calls <xref:System.Windows.Forms.Control.PerformLayout%2A> on child controls of this type.</span></span>

<span data-ttu-id="fecd3-224">Bu, `MarqueeControl` özelleştirmelerin bir kapsamını.</span><span class="sxs-lookup"><span data-stu-id="fecd3-224">This is the extent of the `MarqueeControl` customizations.</span></span> <span data-ttu-id="fecd3-225">Çalışma zamanı özellikleri `MarqueeBorder` ve `MarqueeText` denetimleri tarafından uygulanır ve tasarım zamanı `MarqueeBorderDesigner` özellikleri ve `MarqueeControlRootDesigner` sınıfları tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fecd3-225">The run-time features are implemented by the `MarqueeBorder` and `MarqueeText` controls, and the design-time features are implemented by the `MarqueeBorderDesigner` and `MarqueeControlRootDesigner` classes.</span></span>

### <a name="to-implement-your-custom-control"></a><span data-ttu-id="fecd3-226">Özel denetiminizi uygulamak için</span><span class="sxs-lookup"><span data-stu-id="fecd3-226">To implement your custom control</span></span>

1. <span data-ttu-id="fecd3-227">Kaynak dosyasını kod düzenleyicisinde açın. `MarqueeControl`</span><span class="sxs-lookup"><span data-stu-id="fecd3-227">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="fecd3-228">`Start` Ve`Stop` yöntemlerini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-228">Implement the `Start` and `Stop` methods.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. <span data-ttu-id="fecd3-229">Geçersiz kılma <xref:System.Windows.Forms.Control.OnLayout%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fecd3-229">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="creating-a-child-control-for-your-custom-control"></a><span data-ttu-id="fecd3-230">Özel denetiminiz için bir alt denetim oluşturma</span><span class="sxs-lookup"><span data-stu-id="fecd3-230">Creating a Child Control for Your Custom Control</span></span>

<span data-ttu-id="fecd3-231">İki tür alt denetimi barındırır `MarqueeBorder` : denetim ve `MarqueeText` denetim. `MarqueeControl`</span><span class="sxs-lookup"><span data-stu-id="fecd3-231">The `MarqueeControl` will host two kinds of child control: the `MarqueeBorder` control and the `MarqueeText` control.</span></span>

- <span data-ttu-id="fecd3-232">`MarqueeBorder`: Bu denetim, kenarları etrafında "ışıklar" kenarlığını boyar.</span><span class="sxs-lookup"><span data-stu-id="fecd3-232">`MarqueeBorder`: This control paints a border of "lights" around its edges.</span></span> <span data-ttu-id="fecd3-233">Kenarlıkta bulunan ışıklar, kenarlık etrafında taşınıyor gibi görünürler.</span><span class="sxs-lookup"><span data-stu-id="fecd3-233">The lights flash in sequence, so they appear to be moving around the border.</span></span> <span data-ttu-id="fecd3-234">Işıklarının flaşın, çağrılan `UpdatePeriod`bir özellik tarafından denetlenme hızı.</span><span class="sxs-lookup"><span data-stu-id="fecd3-234">The speed at which the lights flash is controlled by a property called `UpdatePeriod`.</span></span> <span data-ttu-id="fecd3-235">Diğer birçok özel özellik, denetimin görünümünün diğer yönlerini tespit.</span><span class="sxs-lookup"><span data-stu-id="fecd3-235">Several other custom properties determine other aspects of the control's appearance.</span></span> <span data-ttu-id="fecd3-236">Animasyon başladığında ve durdurulduğunda `StartMarquee` denetim `StopMarquee`olarak adlandırılan iki yöntem.</span><span class="sxs-lookup"><span data-stu-id="fecd3-236">Two methods, called `StartMarquee` and `StopMarquee`, control when the animation starts and stops.</span></span>

- <span data-ttu-id="fecd3-237">`MarqueeText`: Bu denetim yanıp sönen bir dizeyi boyar.</span><span class="sxs-lookup"><span data-stu-id="fecd3-237">`MarqueeText`: This control paints a flashing string.</span></span> <span data-ttu-id="fecd3-238">Denetim gibi, metnin yanıp sönebileceği hız, `UpdatePeriod` özelliği tarafından kontrol edilir. `MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="fecd3-238">Like the `MarqueeBorder` control, the speed at which the text flashes is controlled by the `UpdatePeriod` property.</span></span> <span data-ttu-id="fecd3-239">Denetim Ayrıca, `StartMarquee` denetimiyle`MarqueeBorder` ortak olan `StopMarquee` ve yöntemlerine sahiptir. `MarqueeText`</span><span class="sxs-lookup"><span data-stu-id="fecd3-239">The `MarqueeText` control also has the `StartMarquee` and `StopMarquee` methods in common with the `MarqueeBorder` control.</span></span>

<span data-ttu-id="fecd3-240">Tasarım zamanında `MarqueeControlRootDesigner` , bu iki denetim türünün herhangi bir `MarqueeControl` kombinasyonda içine eklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-240">At design time, the `MarqueeControlRootDesigner` allows these two control types to be added to a `MarqueeControl` in any combination.</span></span>

<span data-ttu-id="fecd3-241">İki denetimin ortak özellikleri, adlı `IMarqueeWidget`bir arabirimle birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-241">Common features of the two controls are factored into an interface called `IMarqueeWidget`.</span></span> <span data-ttu-id="fecd3-242">Bu, `MarqueeControl` bir seçim çerçevesinin ilgili alt denetimleri bulmasını ve özel bir işleme vermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fecd3-242">This allows the `MarqueeControl` to discover any Marquee-related child controls and give them special treatment.</span></span>

<span data-ttu-id="fecd3-243">Düzenli animasyon özelliğini uygulamak için, <xref:System.ComponentModel.BackgroundWorker> <xref:System.ComponentModel?displayProperty=nameWithType> ad alanındaki nesneleri kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="fecd3-243">To implement the periodic animation feature, you will use <xref:System.ComponentModel.BackgroundWorker> objects from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="fecd3-244">Nesneleri kullanabilirsiniz <xref:System.Windows.Forms.Timer> , ancak birçok `IMarqueeWidget` nesne mevcut olduğunda, tek UI iş parçacığı animasyonla birlikte tutulamayabilir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-244">You could use <xref:System.Windows.Forms.Timer> objects, but when many `IMarqueeWidget` objects are present, the single UI thread may be unable to keep up with the animation.</span></span>

### <a name="to-create-a-child-control-for-your-custom-control"></a><span data-ttu-id="fecd3-245">Özel denetiminiz için bir alt denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fecd3-245">To create a child control for your custom control</span></span>

1. <span data-ttu-id="fecd3-246">`MarqueeControlLibrary` Projeye yeni bir sınıf öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-246">Add a new class item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="fecd3-247">Yeni kaynak dosyasına "Imarqueepencere öğesi" için temel adı verin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-247">Give the new source file a base name of "IMarqueeWidget."</span></span>

2. <span data-ttu-id="fecd3-248">Kaynak dosyasını **kod düzenleyicisinde** açın ve bildirimi ' den `class` ' e `interface`değiştirin: `IMarqueeWidget`</span><span class="sxs-lookup"><span data-stu-id="fecd3-248">Open the `IMarqueeWidget` source file in the **Code Editor** and change the declaration from `class` to `interface`:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. <span data-ttu-id="fecd3-249">İki yöntemi ve kayan yazı animasyonunu `IMarqueeWidget` işleyen bir özelliği göstermek için aşağıdaki kodu arabirimine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="fecd3-249">Add the following code to the `IMarqueeWidget` interface to expose two methods and a property that manipulate the marquee animation:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. <span data-ttu-id="fecd3-250">`MarqueeControlLibrary` Projeye yeni bir **özel denetim** öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-250">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="fecd3-251">Yeni kaynak dosyasına "MarqueeText" temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-251">Give the new source file a base name of "MarqueeText."</span></span>

5. <span data-ttu-id="fecd3-252">**Araç kutusundan** bir <xref:System.ComponentModel.BackgroundWorker> bileşeni denetimüzerinesürükleyin.`MarqueeText`</span><span class="sxs-lookup"><span data-stu-id="fecd3-252">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeText` control.</span></span> <span data-ttu-id="fecd3-253">Bu bileşen `MarqueeText` denetimin kendisini zaman uyumsuz olarak güncelleştirmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-253">This component will allow the `MarqueeText` control to update itself asynchronously.</span></span>

6. <span data-ttu-id="fecd3-254"><xref:System.ComponentModel.BackgroundWorker> Özellikler penceresi, `WorkerReportsProgress` bileşen ve <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliklerini olarak`true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-254">In the Properties window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to `true`.</span></span> <span data-ttu-id="fecd3-255">Bu ayarlar, <xref:System.ComponentModel.BackgroundWorker> bileşenin düzenli olarak <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayı kullanmasına ve zaman uyumsuz güncelleştirmeleri iptal edebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fecd3-255">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span> <span data-ttu-id="fecd3-256">Daha fazla bilgi için bkz. [BackgroundWorker Component](backgroundworker-component.md).</span><span class="sxs-lookup"><span data-stu-id="fecd3-256">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

7. <span data-ttu-id="fecd3-257">Kaynak dosyasını kod düzenleyicisinde açın. `MarqueeText`</span><span class="sxs-lookup"><span data-stu-id="fecd3-257">Open the `MarqueeText` source file in the **Code Editor**.</span></span> <span data-ttu-id="fecd3-258">Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="fecd3-258">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. <span data-ttu-id="fecd3-259">' Dan `MarqueeText` <xref:System.Windows.Forms.Label> devralması için bildirimini değiştirin ve `IMarqueeWidget` arabirimini uygulayın:</span><span class="sxs-lookup"><span data-stu-id="fecd3-259">Change the declaration of `MarqueeText` to inherit from <xref:System.Windows.Forms.Label> and to implement the `IMarqueeWidget` interface:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. <span data-ttu-id="fecd3-260">Gösterilen özelliklere karşılık gelen örnek değişkenlerini bildirin ve bunları oluşturucuda başlatın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-260">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span> <span data-ttu-id="fecd3-261">Alan, metnin `LightColor` özelliği tarafından verilen renkte boyanmış olup olmayacağını belirler. `isLit`</span><span class="sxs-lookup"><span data-stu-id="fecd3-261">The `isLit` field determines if the text is to be painted in the color given by the `LightColor` property.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. <span data-ttu-id="fecd3-262">`IMarqueeWidget` arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-262">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="fecd3-263">Ve `StartMarquee` yöntemleri,<xref:System.ComponentModel.BackgroundWorker> animasyonu başlatmak ve durdurmak için <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> bileşenin veyöntemleriniçağırır.<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> `StopMarquee`</span><span class="sxs-lookup"><span data-stu-id="fecd3-263">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="fecd3-264"><xref:System.ComponentModel.CategoryAttribute.Category%2A> Ve<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A>öznitelikleri, "kayan yazı" adlı Özellikler penceresi özel bir bölümünde görünmesi için özelliğineuygulanır.`UpdatePeriod`</span><span class="sxs-lookup"><span data-stu-id="fecd3-264">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to the `UpdatePeriod` property so it appears in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. <span data-ttu-id="fecd3-265">Özellik erişimcileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-265">Implement the property accessors.</span></span> <span data-ttu-id="fecd3-266">İstemciler için iki özelliği kullanıma sunacaksınız: `LightColor` ve `DarkColor`.</span><span class="sxs-lookup"><span data-stu-id="fecd3-266">You will expose two properties to clients: `LightColor` and `DarkColor`.</span></span> <span data-ttu-id="fecd3-267"><xref:System.ComponentModel.CategoryAttribute.Category%2A> Ve<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> öznitelikleri bu özelliklere uygulanır, bu nedenle Özellikler "kayan yazı" adlı Özellikler penceresi özel bir bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-267">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to these properties, so the properties appear in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. <span data-ttu-id="fecd3-268"><xref:System.ComponentModel.BackgroundWorker> Bileşen ve Olaylar<xref:System.ComponentModel.BackgroundWorker.ProgressChanged> için işleyicileri uygulayın. <xref:System.ComponentModel.BackgroundWorker.DoWork></span><span class="sxs-lookup"><span data-stu-id="fecd3-268">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="fecd3-269">Olay işleyicisi, tarafından `UpdatePeriod` <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>belirtilenmilisaniye sayısı için uyku moduna geçer. <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> <xref:System.ComponentModel.BackgroundWorker.DoWork></span><span class="sxs-lookup"><span data-stu-id="fecd3-269">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="fecd3-270"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Olay işleyicisi, yanıp sönmeye yönelik görünümü sağlamak için açık ve koyu durumu arasındaki metni değiştirir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-270">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler toggles the text between its light and dark state to give the appearance of flashing.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. <span data-ttu-id="fecd3-271">Animasyonu etkinleştirmek için yöntemini geçersiz kılın. <xref:System.Windows.Forms.Control.OnPaint%2A></span><span class="sxs-lookup"><span data-stu-id="fecd3-271">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method to enable the animation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. <span data-ttu-id="fecd3-272">Çözümü derlemek için F6 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-272">Press F6 to build the solution.</span></span>

## <a name="create-the-marqueeborder-child-control"></a><span data-ttu-id="fecd3-273">MarqueeBorder alt denetimini oluşturma</span><span class="sxs-lookup"><span data-stu-id="fecd3-273">Create the MarqueeBorder Child Control</span></span>

<span data-ttu-id="fecd3-274">Denetim, `MarqueeText` denetimden biraz daha karmaşıktır. `MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="fecd3-274">The `MarqueeBorder` control is slightly more sophisticated than the `MarqueeText` control.</span></span> <span data-ttu-id="fecd3-275">Daha fazla özelliğe sahiptir ve <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemdeki animasyon daha fazla yer alır.</span><span class="sxs-lookup"><span data-stu-id="fecd3-275">It has more properties and the animation in the <xref:System.Windows.Forms.Control.OnPaint%2A> method is more involved.</span></span> <span data-ttu-id="fecd3-276">Prensibi, `MarqueeText` denetime oldukça benzer.</span><span class="sxs-lookup"><span data-stu-id="fecd3-276">In principle, it is quite similar to the `MarqueeText` control.</span></span>

<span data-ttu-id="fecd3-277">Denetimde alt denetimler olabileceğinden, <xref:System.Windows.Forms.Control.Layout> olayların farkında olması gerekir. `MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="fecd3-277">Because the `MarqueeBorder` control can have child controls, it needs to be aware of <xref:System.Windows.Forms.Control.Layout> events.</span></span>

### <a name="to-create-the-marqueeborder-control"></a><span data-ttu-id="fecd3-278">MarqueeBorder denetimini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fecd3-278">To create the MarqueeBorder control</span></span>

1. <span data-ttu-id="fecd3-279">`MarqueeControlLibrary` Projeye yeni bir **özel denetim** öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-279">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="fecd3-280">Yeni kaynak dosyasına "MarqueeBorder" temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-280">Give the new source file a base name of "MarqueeBorder."</span></span>

2. <span data-ttu-id="fecd3-281">**Araç kutusundan** bir <xref:System.ComponentModel.BackgroundWorker> bileşeni denetimüzerinesürükleyin.`MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="fecd3-281">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeBorder` control.</span></span> <span data-ttu-id="fecd3-282">Bu bileşen `MarqueeBorder` denetimin kendisini zaman uyumsuz olarak güncelleştirmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-282">This component will allow the `MarqueeBorder` control to update itself asynchronously.</span></span>

3. <span data-ttu-id="fecd3-283"><xref:System.ComponentModel.BackgroundWorker> Özellikler penceresi, `WorkerReportsProgress` bileşen ve <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliklerini olarak`true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-283">In the Properties window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to `true`.</span></span> <span data-ttu-id="fecd3-284">Bu ayarlar, <xref:System.ComponentModel.BackgroundWorker> bileşenin düzenli olarak <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayı kullanmasına ve zaman uyumsuz güncelleştirmeleri iptal edebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fecd3-284">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span> <span data-ttu-id="fecd3-285">Daha fazla bilgi için bkz. [BackgroundWorker Component](backgroundworker-component.md).</span><span class="sxs-lookup"><span data-stu-id="fecd3-285">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

4. <span data-ttu-id="fecd3-286">Özellikler penceresi, olaylar düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-286">In the Properties window, click the Events button.</span></span> <span data-ttu-id="fecd3-287"><xref:System.ComponentModel.BackgroundWorker.DoWork> Ve<xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayları için işleyiciler iliştirin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-287">Attach handlers for the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

5. <span data-ttu-id="fecd3-288">Kaynak dosyasını kod düzenleyicisinde açın. `MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="fecd3-288">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span> <span data-ttu-id="fecd3-289">Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="fecd3-289">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. <span data-ttu-id="fecd3-290">' Dan `MarqueeBorder` <xref:System.Windows.Forms.Panel> devralması için bildirimini değiştirin ve `IMarqueeWidget` arabirimini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-290">Change the declaration of `MarqueeBorder` to inherit from <xref:System.Windows.Forms.Panel> and to implement the `IMarqueeWidget` interface.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. <span data-ttu-id="fecd3-291">`MarqueeBorder` Denetimin durumunu yönetmek için iki numaralandırma bildirin: `MarqueeSpinDirection`, ışıklarının etrafında "döndürme" ve `MarqueeLightShape`ışıklarının şeklini (kare veya dairesel) belirleyen yönü belirleyen yönü belirler.</span><span class="sxs-lookup"><span data-stu-id="fecd3-291">Declare two enumerations for managing the `MarqueeBorder` control's state: `MarqueeSpinDirection`, which determines the direction in which the lights "spin" around the border, and `MarqueeLightShape`, which determines the shape of the lights (square or circular).</span></span> <span data-ttu-id="fecd3-292">Bu bildirimleri `MarqueeBorder` Sınıf bildiriminden önce yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-292">Place these declarations before the `MarqueeBorder` class declaration.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. <span data-ttu-id="fecd3-293">Gösterilen özelliklere karşılık gelen örnek değişkenlerini bildirin ve bunları oluşturucuda başlatın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-293">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. <span data-ttu-id="fecd3-294">`IMarqueeWidget` arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-294">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="fecd3-295">Ve `StartMarquee` yöntemleri,<xref:System.ComponentModel.BackgroundWorker> animasyonu başlatmak ve durdurmak için <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> bileşenin veyöntemleriniçağırır.<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> `StopMarquee`</span><span class="sxs-lookup"><span data-stu-id="fecd3-295">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="fecd3-296">Denetim alt denetimler içerebildiğinden `StartMarquee` , yöntemi, uygulamalarındaki `IMarqueeWidget`tüm alt denetimleri ve çağrıları `StartMarquee` numaralandırır. `MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="fecd3-296">Because the `MarqueeBorder` control can contain child controls, the `StartMarquee` method enumerates all child controls and calls `StartMarquee` on those that implement `IMarqueeWidget`.</span></span> <span data-ttu-id="fecd3-297">`StopMarquee` Yönteminde benzer bir uygulama vardır.</span><span class="sxs-lookup"><span data-stu-id="fecd3-297">The `StopMarquee` method has a similar implementation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. <span data-ttu-id="fecd3-298">Özellik erişimcileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-298">Implement the property accessors.</span></span> <span data-ttu-id="fecd3-299">`MarqueeBorder` Denetimde, görünümünü denetlemek için çeşitli özellikler vardır.</span><span class="sxs-lookup"><span data-stu-id="fecd3-299">The `MarqueeBorder` control has several properties for controlling its appearance.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. <span data-ttu-id="fecd3-300"><xref:System.ComponentModel.BackgroundWorker> Bileşen ve Olaylar<xref:System.ComponentModel.BackgroundWorker.ProgressChanged> için işleyicileri uygulayın. <xref:System.ComponentModel.BackgroundWorker.DoWork></span><span class="sxs-lookup"><span data-stu-id="fecd3-300">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="fecd3-301">Olay işleyicisi, tarafından `UpdatePeriod` <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>belirtilenmilisaniye sayısı için uyku moduna geçer. <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> <xref:System.ComponentModel.BackgroundWorker.DoWork></span><span class="sxs-lookup"><span data-stu-id="fecd3-301">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="fecd3-302">Olay işleyicisi, diğer ışıklarının açık/koyu durumunun belirlendiği "temel" Işığın konumunu artırır ve denetimin kendisini yeniden çizmeyi sağlamak için <xref:System.Windows.Forms.Control.Refresh%2A> yöntemini çağırır. <xref:System.ComponentModel.BackgroundWorker.ProgressChanged></span><span class="sxs-lookup"><span data-stu-id="fecd3-302">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler increments the position of the "base" light, from which the light/dark state of the other lights is determined, and calls the <xref:System.Windows.Forms.Control.Refresh%2A> method to cause the control to repaint itself.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. <span data-ttu-id="fecd3-303">Yardımcı yöntemleri ve `DrawLight`' yi `IsLit` uygulayın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-303">Implement the helper methods, `IsLit` and `DrawLight`.</span></span>

    <span data-ttu-id="fecd3-304">Yöntemi `IsLit` , belirli bir konumdaki ışığın rengini belirler.</span><span class="sxs-lookup"><span data-stu-id="fecd3-304">The `IsLit` method determines the color of a light at a given position.</span></span> <span data-ttu-id="fecd3-305">"Açık" olan ışıklar `LightColor` özelliği tarafından verilen renkte çizilir ve "koyu" olan ışıklar `DarkColor` özelliği tarafından verilen renkte çizilir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-305">Lights that are "lit" are drawn in the color given by the `LightColor` property, and those that are "dark" are drawn in the color given by the `DarkColor` property.</span></span>

    <span data-ttu-id="fecd3-306">`DrawLight` Yöntemi uygun renk, şekil ve konumu kullanarak bir ışık çizer.</span><span class="sxs-lookup"><span data-stu-id="fecd3-306">The `DrawLight` method draws a light using the appropriate color, shape, and position.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. <span data-ttu-id="fecd3-307"><xref:System.Windows.Forms.Control.OnLayout%2A> Ve<xref:System.Windows.Forms.Control.OnPaint%2A> yöntemlerini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-307">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> and <xref:System.Windows.Forms.Control.OnPaint%2A> methods.</span></span>

    <span data-ttu-id="fecd3-308">Yöntemi, `MarqueeBorder` denetimin kenarları üzerinde ışıkları çizer. <xref:System.Windows.Forms.Control.OnPaint%2A></span><span class="sxs-lookup"><span data-stu-id="fecd3-308">The <xref:System.Windows.Forms.Control.OnPaint%2A> method draws the lights along the edges of the `MarqueeBorder` control.</span></span>

    <span data-ttu-id="fecd3-309"><xref:System.Windows.Forms.Control.OnPaint%2A> Yöntem `MarqueeBorder` denetimin boyutlarına bağlı olduğundan, düzen her değiştiğinde onu çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-309">Because the <xref:System.Windows.Forms.Control.OnPaint%2A> method depends on the dimensions of the `MarqueeBorder` control, you need to call it whenever the layout changes.</span></span> <span data-ttu-id="fecd3-310">Bunu başarmak için, öğesini <xref:System.Windows.Forms.Control.OnLayout%2A> geçersiz kılın <xref:System.Windows.Forms.Control.Refresh%2A>ve çağırın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-310">To achieve this, override <xref:System.Windows.Forms.Control.OnLayout%2A> and call <xref:System.Windows.Forms.Control.Refresh%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="creating-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="fecd3-311">Gölge ve filtre özelliklerine özel tasarımcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="fecd3-311">Creating a Custom Designer to Shadow and Filter Properties</span></span>

<span data-ttu-id="fecd3-312">`MarqueeControlRootDesigner` Sınıfı, kök Tasarımcı için uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="fecd3-312">The `MarqueeControlRootDesigner` class provides the implementation for the root designer.</span></span> <span data-ttu-id="fecd3-313">Üzerinde `MarqueeControl`çalışan bu tasarımcıya ek olarak, özellikle `MarqueeBorder` denetimle ilişkili özel bir tasarımcıya ihtiyacınız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fecd3-313">In addition to this designer, which operates on the `MarqueeControl`, you will need a custom designer that is specifically associated with the `MarqueeBorder` control.</span></span> <span data-ttu-id="fecd3-314">Bu tasarımcı, özel kök tasarlayıcı bağlamında uygun olan özel davranışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="fecd3-314">This designer provides custom behavior that is appropriate in the context of the custom root designer.</span></span>

<span data-ttu-id="fecd3-315">Özellikle, "gölgelendir" ve `MarqueeBorder` denetimdeki belirli özellikleri filtreleyerek tasarım ortamıyla etkileşimini değiştirmiş olacak.`MarqueeBorderDesigner`</span><span class="sxs-lookup"><span data-stu-id="fecd3-315">Specifically, the `MarqueeBorderDesigner` will "shadow" and filter certain properties on the `MarqueeBorder` control, changing their interaction with the design environment.</span></span>

<span data-ttu-id="fecd3-316">Bir bileşenin Özellik erişimcisine yönelik kesintiye uğratan çağrı, "gölgeleme" olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-316">Intercepting calls to a component's property accessor is known as "shadowing."</span></span> <span data-ttu-id="fecd3-317">Bir tasarımcının Kullanıcı tarafından ayarlanan değeri izlemesine ve isteğe bağlı olarak bu değeri tasarlanmakta olan bileşene iletmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fecd3-317">It allows a designer to track the value set by the user and optionally pass that value to the component being designed.</span></span>

<span data-ttu-id="fecd3-318">Bu örnekte <xref:System.Windows.Forms.Control.Visible%2A> , ve <xref:System.Windows.Forms.Control.Enabled%2A> özellikleri, `MarqueeBorderDesigner`kullanıcının tasarım zamanı sırasında `MarqueeBorder` denetimi görünmez veya devre dışı yapmasını önleyen tarafından gölgelenir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-318">For this example, the <xref:System.Windows.Forms.Control.Visible%2A> and <xref:System.Windows.Forms.Control.Enabled%2A> properties will be shadowed by the `MarqueeBorderDesigner`, which prevents the user from making the `MarqueeBorder` control invisible or disabled during design time.</span></span>

<span data-ttu-id="fecd3-319">Tasarımcılar Ayrıca özellikler ekleyebilir ve kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-319">Designers can also add and remove properties.</span></span> <span data-ttu-id="fecd3-320">Bu örnekte, <xref:System.Windows.Forms.Control.Padding%2A> özellik tasarım zamanında kaldırılacak, `MarqueeBorder` çünkü denetim program aracılığıyla, `LightSize` özelliği tarafından belirtilen ışıklarının boyutuna göre doldurma ayarlıyor.</span><span class="sxs-lookup"><span data-stu-id="fecd3-320">For this example, the <xref:System.Windows.Forms.Control.Padding%2A> property will be removed at design time, because the `MarqueeBorder` control programmatically sets the padding based on the size of the lights specified by the `LightSize` property.</span></span>

<span data-ttu-id="fecd3-321">`MarqueeBorderDesigner` İçin<xref:System.ComponentModel.Design.ComponentDesigner>temel sınıf, tasarım zamanında bir denetim tarafından açığa çıkarılan öznitelikleri, özellikleri ve olayları değiştirebilen yöntemler içerir:</span><span class="sxs-lookup"><span data-stu-id="fecd3-321">The base class for `MarqueeBorderDesigner` is <xref:System.ComponentModel.Design.ComponentDesigner>, which has methods that can change the attributes, properties, and events exposed by a control at design time:</span></span>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

<span data-ttu-id="fecd3-322">Bu yöntemleri kullanarak bir bileşenin genel arabirimini değiştirirken bu kuralları izlemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="fecd3-322">When changing the public interface of a component using these methods, you must follow these rules:</span></span>

- <span data-ttu-id="fecd3-323">Yalnızca `PreFilter` metotlarda öğe ekleme veya kaldırma</span><span class="sxs-lookup"><span data-stu-id="fecd3-323">Add or remove items in the `PreFilter` methods only</span></span>

- <span data-ttu-id="fecd3-324">Yalnızca `PostFilter` metotlarda bulunan öğeleri değiştir</span><span class="sxs-lookup"><span data-stu-id="fecd3-324">Modify existing items in the `PostFilter` methods only</span></span>

- <span data-ttu-id="fecd3-325">Her zaman ilk olarak `PreFilter` metotlarda temel uygulamayı çağırın</span><span class="sxs-lookup"><span data-stu-id="fecd3-325">Always call the base implementation first in the `PreFilter` methods</span></span>

- <span data-ttu-id="fecd3-326">Her zaman, `PostFilter` metotlarda en son temel uygulamayı çağırın</span><span class="sxs-lookup"><span data-stu-id="fecd3-326">Always call the base implementation last in the `PostFilter` methods</span></span>

<span data-ttu-id="fecd3-327">Bu kurallara uymak, tasarım zamanı ortamındaki tüm tasarımcılarının tasarlanmakta olan tüm bileşenlerin tutarlı bir görünümüne sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fecd3-327">Adhering to these rules ensures that all designers in the design-time environment have a consistent view of all components being designed.</span></span>

<span data-ttu-id="fecd3-328"><xref:System.ComponentModel.Design.ComponentDesigner> Sınıfı, gölgelendirilmiş özelliklerin değerlerini yönetmek için bir sözlük sağlar, bu da size belirli örnek değişkenleri oluşturma gereksinimini sizi maliyetinden kurtarır.</span><span class="sxs-lookup"><span data-stu-id="fecd3-328">The <xref:System.ComponentModel.Design.ComponentDesigner> class provides a dictionary for managing the values of shadowed properties, which relieves you of the need to create specific instance variables.</span></span>

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="fecd3-329">Gölge ve filtre özelliklerine özel bir tasarımcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fecd3-329">To create a custom designer to shadow and filter properties</span></span>

1. <span data-ttu-id="fecd3-330">**Tasarım** klasörüne sağ tıklayın ve yeni bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-330">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="fecd3-331">Kaynak dosyaya "MarqueeBorderDesigner" temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-331">Give the source file a base name of "MarqueeBorderDesigner."</span></span>

2. <span data-ttu-id="fecd3-332">Kaynak dosyasını kod düzenleyicisinde açın. `MarqueeBorderDesigner`</span><span class="sxs-lookup"><span data-stu-id="fecd3-332">Open the `MarqueeBorderDesigner` source file in the **Code Editor**.</span></span> <span data-ttu-id="fecd3-333">Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="fecd3-333">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. <span data-ttu-id="fecd3-334">Bildirimini `MarqueeBorderDesigner` öğesinden<xref:System.Windows.Forms.Design.ParentControlDesigner>devralacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-334">Change the declaration of `MarqueeBorderDesigner` to inherit from <xref:System.Windows.Forms.Design.ParentControlDesigner>.</span></span>

    <span data-ttu-id="fecd3-335">Denetim alt denetimler içerebildiğinden, üst-alt etkileşimini <xref:System.Windows.Forms.Design.ParentControlDesigner>işleyen öğesinden devralır.`MarqueeBorderDesigner` `MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="fecd3-335">Because the `MarqueeBorder` control can contain child controls, `MarqueeBorderDesigner` inherits from <xref:System.Windows.Forms.Design.ParentControlDesigner>, which handles the parent-child interaction.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. <span data-ttu-id="fecd3-336">Temel uygulamasını <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-336">Override the base implementation of <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. <span data-ttu-id="fecd3-337"><xref:System.Windows.Forms.Control.Enabled%2A> Ve<xref:System.Windows.Forms.Control.Visible%2A> özelliklerini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-337">Implement the <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A> properties.</span></span> <span data-ttu-id="fecd3-338">Bu uygulamalar, denetimin özelliklerini gölgelendir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-338">These implementations shadow the control's properties.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handling-component-changes"></a><span data-ttu-id="fecd3-339">Bileşen değişikliklerini işleme</span><span class="sxs-lookup"><span data-stu-id="fecd3-339">Handling Component Changes</span></span>
 <span data-ttu-id="fecd3-340">Sınıfı, örneklerinizin `MarqueeControl` özel tasarım zamanı deneyimini sağlar. `MarqueeControlRootDesigner`</span><span class="sxs-lookup"><span data-stu-id="fecd3-340">The `MarqueeControlRootDesigner` class provides the custom design-time experience for your `MarqueeControl` instances.</span></span> <span data-ttu-id="fecd3-341">Tasarım zamanı işlevlerinin çoğu <xref:System.Windows.Forms.Design.DocumentDesigner> sınıftan devralınır; kodunuz iki özel özelleştirme uygular: bileşen değişikliklerini işleme ve tasarımcı fiilleri ekleme.</span><span class="sxs-lookup"><span data-stu-id="fecd3-341">Most of the design-time functionality is inherited from the <xref:System.Windows.Forms.Design.DocumentDesigner> class; your code will implement two specific customizations: handling component changes, and adding designer verbs.</span></span>

 <span data-ttu-id="fecd3-342">Kullanıcılar `MarqueeControl` örneklerini tasarlarsa, kök tasarlayıcı, `MarqueeControl` ve alt denetimlerinde yapılan değişiklikleri izler.</span><span class="sxs-lookup"><span data-stu-id="fecd3-342">As users design their `MarqueeControl` instances, your root designer will track changes to the `MarqueeControl` and its child controls.</span></span> <span data-ttu-id="fecd3-343">Tasarım zamanı ortamı, bileşen durumundaki değişiklikleri izlemek için uygun <xref:System.ComponentModel.Design.IComponentChangeService>bir hizmet sunar.</span><span class="sxs-lookup"><span data-stu-id="fecd3-343">The design-time environment offers a convenient service, <xref:System.ComponentModel.Design.IComponentChangeService>, for tracking changes to component state.</span></span>

 <span data-ttu-id="fecd3-344">Ortamı <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> yöntemiyle sorgulayarak bu hizmete bir başvuru elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="fecd3-344">You acquire a reference to this service by querying the environment with the <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> method.</span></span> <span data-ttu-id="fecd3-345">Sorgu başarılı olursa, tasarımcı <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> olay için bir işleyici iliştirebilir ve tasarım zamanında tutarlı bir durumu korumak için gereken görevleri gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-345">If the query is successful, your designer can attach a handler for the <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> event and perform whatever tasks are required to maintain a consistent state at design time.</span></span>

 <span data-ttu-id="fecd3-346">`MarqueeControlRootDesigner` Sınıfı söz konusu olduğunda, <xref:System.Windows.Forms.Control.Refresh%2A> yöntemi tarafından içerilen `MarqueeControl`her `IMarqueeWidget` bir nesne üzerinde çağıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="fecd3-346">In the case of the `MarqueeControlRootDesigner` class, you will call the <xref:System.Windows.Forms.Control.Refresh%2A> method on each `IMarqueeWidget` object contained by the `MarqueeControl`.</span></span> <span data-ttu-id="fecd3-347">Bu, `IMarqueeWidget` <xref:System.Windows.Forms.Control.Size%2A> üst öğesi gibi özellikler değiştirildiğinde nesnenin kendisini uygun şekilde yeniden görüntülemesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="fecd3-347">This will cause the `IMarqueeWidget` object to repaint itself appropriately when properties like its parent's <xref:System.Windows.Forms.Control.Size%2A> are changed.</span></span>

### <a name="to-handle-component-changes"></a><span data-ttu-id="fecd3-348">Bileşen değişikliklerini işlemek için</span><span class="sxs-lookup"><span data-stu-id="fecd3-348">To handle component changes</span></span>

1. <span data-ttu-id="fecd3-349">Kaynak dosyasını **kod düzenleyicisinde** açın ve <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> metodunu geçersiz kılın. `MarqueeControlRootDesigner`</span><span class="sxs-lookup"><span data-stu-id="fecd3-349">Open the `MarqueeControlRootDesigner` source file in the **Code Editor** and override the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span> <span data-ttu-id="fecd3-350">İçin temel uygulamasını <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> çağırın ve için sorgulayın. <xref:System.ComponentModel.Design.IComponentChangeService></span><span class="sxs-lookup"><span data-stu-id="fecd3-350">Call the base implementation of <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> and query for the <xref:System.ComponentModel.Design.IComponentChangeService>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. <span data-ttu-id="fecd3-351"><xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> Olay işleyicisini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-351">Implement the <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> event handler.</span></span> <span data-ttu-id="fecd3-352">Gönderen bileşenin türünü test edin ve bir `IMarqueeWidget`ise <xref:System.Windows.Forms.Control.Refresh%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-352">Test the sending component's type, and if it is an `IMarqueeWidget`, call its <xref:System.Windows.Forms.Control.Refresh%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="adding-designer-verbs-to-your-custom-designer"></a><span data-ttu-id="fecd3-353">Özel tasarımcıya tasarımcı fiilleri ekleme</span><span class="sxs-lookup"><span data-stu-id="fecd3-353">Adding Designer Verbs to your Custom Designer</span></span>

<span data-ttu-id="fecd3-354">Tasarımcı fiili, olay işleyicisine bağlı bir menü komutu olur.</span><span class="sxs-lookup"><span data-stu-id="fecd3-354">A designer verb is a menu command linked to an event handler.</span></span> <span data-ttu-id="fecd3-355">Tasarımcı fiilleri, tasarım zamanında bir bileşenin kısayol menüsüne eklenir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-355">Designer verbs are added to a component's shortcut menu at design time.</span></span> <span data-ttu-id="fecd3-356">Daha fazla bilgi için bkz. <xref:System.ComponentModel.Design.DesignerVerb>.</span><span class="sxs-lookup"><span data-stu-id="fecd3-356">For more information, see <xref:System.ComponentModel.Design.DesignerVerb>.</span></span>

<span data-ttu-id="fecd3-357">Tasarımcılara iki tasarımcı fiilleri ekleyeceksiniz: **Testi Çalıştır** ve **testi durdur**.</span><span class="sxs-lookup"><span data-stu-id="fecd3-357">You will add two designer verbs to your designers: **Run Test** and **Stop Test**.</span></span> <span data-ttu-id="fecd3-358">Bu fiiller, `MarqueeControl` tasarım zamanının çalışma zamanı davranışını görüntülemenize olanak sağlayacak.</span><span class="sxs-lookup"><span data-stu-id="fecd3-358">These verbs will allow you to view the run-time behavior of the `MarqueeControl` at design time.</span></span> <span data-ttu-id="fecd3-359">Bu fiiller öğesine `MarqueeControlRootDesigner`eklenecektir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-359">These verbs will be added to the `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="fecd3-360">**Çalıştırma testi** çağrıldığında, fiil olay işleyicisi üzerinde `StartMarquee` `MarqueeControl`yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="fecd3-360">When **Run Test** is invoked, the verb event handler will call the `StartMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="fecd3-361">**Testi durdur** çağrıldığında, fiil olay işleyicisi üzerinde `StopMarquee` `MarqueeControl`yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="fecd3-361">When **Stop Test** is invoked, the verb event handler will call the `StopMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="fecd3-362">`StartMarquee` Ve `IMarqueeWidget` `IMarqueeWidget` yöntemlerinin uygulaması, uygulayan içerilen denetimler üzerinde bu yöntemleri çağırır, bu nedenle içerilen denetimlerin de teste katılması gerekir. `StopMarquee`</span><span class="sxs-lookup"><span data-stu-id="fecd3-362">The implementation of the `StartMarquee` and `StopMarquee` methods call these methods on contained controls that implement `IMarqueeWidget`, so any contained `IMarqueeWidget` controls will also participate in the test.</span></span>

### <a name="to-add-designer-verbs-to-your-custom-designers"></a><span data-ttu-id="fecd3-363">Özel tasarımcılara tasarımcı fiilleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="fecd3-363">To add designer verbs to your custom designers</span></span>

1. <span data-ttu-id="fecd3-364">Sınıfında, `OnVerbRunTest` ve`OnVerbStopTest`adlı olay işleyicileri ekleyin. `MarqueeControlRootDesigner`</span><span class="sxs-lookup"><span data-stu-id="fecd3-364">In the `MarqueeControlRootDesigner` class, add event handlers named `OnVerbRunTest` and `OnVerbStopTest`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. <span data-ttu-id="fecd3-365">Bu olay işleyicilerini ilgili tasarımcı fiillerine bağlayın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-365">Connect these event handlers to their corresponding designer verbs.</span></span> <span data-ttu-id="fecd3-366">`MarqueeControlRootDesigner`kendi temel <xref:System.ComponentModel.Design.DesignerVerbCollection> sınıfından bir devralır.</span><span class="sxs-lookup"><span data-stu-id="fecd3-366">`MarqueeControlRootDesigner` inherits a <xref:System.ComponentModel.Design.DesignerVerbCollection> from its base class.</span></span> <span data-ttu-id="fecd3-367">İki yeni <xref:System.ComponentModel.Design.DesignerVerb> nesne oluşturacak ve bu koleksiyona, <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> yöntemi içinde ekleyecek.</span><span class="sxs-lookup"><span data-stu-id="fecd3-367">You will create two new <xref:System.ComponentModel.Design.DesignerVerb> objects and add them to this collection in the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="creating-a-custom-uitypeeditor"></a><span data-ttu-id="fecd3-368">Özel Uııtypeınfo Düzenleyicisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="fecd3-368">Creating a Custom UITypeEditor</span></span>

<span data-ttu-id="fecd3-369">Kullanıcılar için özel bir tasarım zamanı deneyimi oluşturduğunuzda, genellikle Özellikler penceresi özel bir etkileşim oluşturmak tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-369">When you create a custom design-time experience for users, it is often desirable to create a custom interaction with the Properties window.</span></span> <span data-ttu-id="fecd3-370">Bunu oluşturarak <xref:System.Drawing.Design.UITypeEditor>yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fecd3-370">You can accomplish this by creating a <xref:System.Drawing.Design.UITypeEditor>.</span></span> <span data-ttu-id="fecd3-371">Daha fazla bilgi için [nasıl yapılır: UI türü Düzenleyici](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fd3kt7d5(v=vs.120))oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fecd3-371">For more information, see [How to: Create a UI Type Editor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fd3kt7d5(v=vs.120)).</span></span>

<span data-ttu-id="fecd3-372">`MarqueeBorder` Denetim Özellikler penceresi çeşitli özellikleri kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="fecd3-372">The `MarqueeBorder` control exposes several properties in the Properties window.</span></span> <span data-ttu-id="fecd3-373">Bu özelliklerden `MarqueeSpinDirection` ikisi ve `MarqueeLightShape` numaralandırmalar tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-373">Two of these properties, `MarqueeSpinDirection` and `MarqueeLightShape` are represented by enumerations.</span></span> <span data-ttu-id="fecd3-374">Kullanıcı arabirimi türü düzenleyicisinin kullanımını göstermek için, `MarqueeLightShape` özelliği ilişkili <xref:System.Drawing.Design.UITypeEditor> bir sınıfa sahip olur.</span><span class="sxs-lookup"><span data-stu-id="fecd3-374">To illustrate the use of a UI type editor, the `MarqueeLightShape` property will have an associated <xref:System.Drawing.Design.UITypeEditor> class.</span></span>

### <a name="to-create-a-custom-ui-type-editor"></a><span data-ttu-id="fecd3-375">Özel bir kullanıcı arabirimi tür Düzenleyicisi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fecd3-375">To create a custom UI type editor</span></span>

1. <span data-ttu-id="fecd3-376">Kaynak dosyasını kod düzenleyicisinde açın. `MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="fecd3-376">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span>

2. <span data-ttu-id="fecd3-377">`MarqueeBorder` Sınıfının tanımında, öğesinden `LightShapeEditor` <xref:System.Drawing.Design.UITypeEditor>türetilen adlı bir sınıf bildirin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-377">In the definition of the `MarqueeBorder` class, declare a class called `LightShapeEditor` that derives from <xref:System.Drawing.Design.UITypeEditor>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. <span data-ttu-id="fecd3-378"><xref:System.Windows.Forms.Design.IWindowsFormsEditorService> Adlı`editorService`bir örnek değişkeni bildirin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-378">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. <span data-ttu-id="fecd3-379">Geçersiz kılma <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fecd3-379">Override the <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> method.</span></span> <span data-ttu-id="fecd3-380">Bu uygulama, <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>tasarım ortamına nasıl `LightShapeEditor`görüntüleneceğini bildiren, öğesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="fecd3-380">This implementation returns <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, which tells the design environment how to display the `LightShapeEditor`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. <span data-ttu-id="fecd3-381">Geçersiz kılma <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fecd3-381">Override the <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> method.</span></span> <span data-ttu-id="fecd3-382">Bu uygulama, bir <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> nesnenin tasarım ortamını sorgular.</span><span class="sxs-lookup"><span data-stu-id="fecd3-382">This implementation queries the design environment for an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> object.</span></span> <span data-ttu-id="fecd3-383">Başarılı olursa, bir `LightShapeSelectionControl`oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fecd3-383">If successful, it creates a `LightShapeSelectionControl`.</span></span> <span data-ttu-id="fecd3-384">Yöntemi başlatmak için çağrılır. `LightShapeEditor` <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A></span><span class="sxs-lookup"><span data-stu-id="fecd3-384">The <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> method is invoked to start the `LightShapeEditor`.</span></span> <span data-ttu-id="fecd3-385">Bu çağrıdan gelen dönüş değeri tasarım ortamına döndürülür.</span><span class="sxs-lookup"><span data-stu-id="fecd3-385">The return value from this invocation is returned to the design environment.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="creating-a-view-control-for-your-custom-uitypeeditor"></a><span data-ttu-id="fecd3-386">Özel Uııtypeınfo Düzenleyicisi için bir görünüm denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="fecd3-386">Creating a View Control for your Custom UITypeEditor</span></span>

1. <span data-ttu-id="fecd3-387">Özelliği iki tür açık şekli destekler: `Square` ve `Circle`. `MarqueeLightShape`</span><span class="sxs-lookup"><span data-stu-id="fecd3-387">The `MarqueeLightShape` property supports two types of light shapes: `Square` and `Circle`.</span></span> <span data-ttu-id="fecd3-388">Yalnızca bu değerleri Özellikler penceresi grafik olarak görüntülemek için kullanılan özel bir denetim oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="fecd3-388">You will create a custom control used solely for the purpose of graphically displaying these values in the Properties window.</span></span> <span data-ttu-id="fecd3-389">Bu özel denetim, Özellikler penceresi etkileşimde bulunmak için <xref:System.Drawing.Design.UITypeEditor> sizin tarafınızdan kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="fecd3-389">This custom control will be used by your <xref:System.Drawing.Design.UITypeEditor> to interact with the Properties window.</span></span>

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a><span data-ttu-id="fecd3-390">Özel UI türü düzenleyiciniz için bir görünüm denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fecd3-390">To create a view control for your custom UI type editor</span></span>

1. <span data-ttu-id="fecd3-391">`MarqueeControlLibrary` Projeye yeni <xref:System.Windows.Forms.UserControl> bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-391">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="fecd3-392">Yeni kaynak dosyasına "LightShapeSelectionControl" temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-392">Give the new source file a base name of "LightShapeSelectionControl."</span></span>

2. <span data-ttu-id="fecd3-393">Araç kutusundan <xref:System.Windows.Forms.Panel> iki denetimi üzerine sürükleyin. `LightShapeSelectionControl`</span><span class="sxs-lookup"><span data-stu-id="fecd3-393">Drag two <xref:System.Windows.Forms.Panel> controls from the **Toolbox** onto the `LightShapeSelectionControl`.</span></span> <span data-ttu-id="fecd3-394">Onları `squarePanel` ve`circlePanel`olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-394">Name them `squarePanel` and `circlePanel`.</span></span> <span data-ttu-id="fecd3-395">Yan yana düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-395">Arrange them side by side.</span></span> <span data-ttu-id="fecd3-396">Her iki<xref:System.Windows.Forms.Panel> denetimin özelliğini (60, 60) olarak ayarlayın. <xref:System.Windows.Forms.Control.Size%2A></span><span class="sxs-lookup"><span data-stu-id="fecd3-396">Set the <xref:System.Windows.Forms.Control.Size%2A> property of both <xref:System.Windows.Forms.Panel> controls to (60, 60).</span></span> <span data-ttu-id="fecd3-397">`squarePanel` Denetimin özelliğini (8, 10) olarak ayarlayın. <xref:System.Windows.Forms.Control.Location%2A></span><span class="sxs-lookup"><span data-stu-id="fecd3-397">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `squarePanel` control to (8, 10).</span></span> <span data-ttu-id="fecd3-398">`circlePanel` Denetimin özelliğini (80, 10) olarak ayarlayın. <xref:System.Windows.Forms.Control.Location%2A></span><span class="sxs-lookup"><span data-stu-id="fecd3-398">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `circlePanel` control to (80, 10).</span></span> <span data-ttu-id="fecd3-399">Son olarak, `LightShapeSelectionControl` öğesinin <xref:System.Windows.Forms.Control.Size%2A> özelliğini olarak ayarlayın (150, 80).</span><span class="sxs-lookup"><span data-stu-id="fecd3-399">Finally, set the <xref:System.Windows.Forms.Control.Size%2A> property of the `LightShapeSelectionControl` to (150, 80).</span></span>

3. <span data-ttu-id="fecd3-400">Kaynak dosyasını kod düzenleyicisinde açın. `LightShapeSelectionControl`</span><span class="sxs-lookup"><span data-stu-id="fecd3-400">Open the `LightShapeSelectionControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="fecd3-401">Dosyanın en üstünde, <xref:System.Windows.Forms.Design?displayProperty=nameWithType> ad alanını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="fecd3-401">At the top of the file, import the <xref:System.Windows.Forms.Design?displayProperty=nameWithType> namespace:</span></span>

```vb
Imports System.Windows.Forms.Design
```

```csharp
using System.Windows.Forms.Design;
```

1. <span data-ttu-id="fecd3-402">Ve`squarePanel` <xref:System.Windows.Forms.Control.Click> denetimleriiçin`circlePanel` olay işleyicileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-402">Implement <xref:System.Windows.Forms.Control.Click> event handlers for the `squarePanel` and `circlePanel` controls.</span></span> <span data-ttu-id="fecd3-403">Bu yöntemler, <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> özel <xref:System.Drawing.Design.UITypeEditor> Düzenle oturumunu sona erdirmek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="fecd3-403">These methods invoke <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> to end the custom <xref:System.Drawing.Design.UITypeEditor> editing session.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

2. <span data-ttu-id="fecd3-404"><xref:System.Windows.Forms.Design.IWindowsFormsEditorService> Adlı`editorService`bir örnek değişkeni bildirin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-404">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

```vb
Private editorService As IWindowsFormsEditorService
```

```csharp
private IWindowsFormsEditorService editorService;
```

1. <span data-ttu-id="fecd3-405">`MarqueeLightShape` Adlı`lightShapeValue`bir örnek değişkeni bildirin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-405">Declare a `MarqueeLightShape` instance variable called `lightShapeValue`.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

2. <span data-ttu-id="fecd3-406">`LightShapeSelectionControl` Oluşturucuda, <xref:System.Windows.Forms.Control.Click> olay işleyicilerini `squarePanel` ve `circlePanel` denetimlerin olaylarınaekleyin.<xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="fecd3-406">In the `LightShapeSelectionControl` constructor, attach the <xref:System.Windows.Forms.Control.Click> event handlers to the `squarePanel` and `circlePanel` controls' <xref:System.Windows.Forms.Control.Click> events.</span></span> <span data-ttu-id="fecd3-407">Ayrıca, tasarım ortamından `MarqueeLightShape` `lightShapeValue` alana değeri atayan bir Oluşturucu aşırı yüklemesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-407">Also, define a constructor overload that assigns the `MarqueeLightShape` value from the design environment to the `lightShapeValue` field.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

3. <span data-ttu-id="fecd3-408"><xref:System.ComponentModel.Component.Dispose%2A> Yönteminde <xref:System.Windows.Forms.Control.Click> olay işleyicilerini ayırın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-408">In the <xref:System.ComponentModel.Component.Dispose%2A> method, detach the <xref:System.Windows.Forms.Control.Click> event handlers.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

4. <span data-ttu-id="fecd3-409">**Çözüm Gezgini**, **tüm dosyaları göster** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-409">In **Solution Explorer**, click the **Show All Files** button.</span></span> <span data-ttu-id="fecd3-410">LightShapeSelectionControl.Designer.cs veya LightShapeSelectionControl. Designer. vb dosyasını açın ve <xref:System.ComponentModel.Component.Dispose%2A> yönteminin varsayılan tanımını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-410">Open the LightShapeSelectionControl.Designer.cs or LightShapeSelectionControl.Designer.vb file, and remove the default definition of the <xref:System.ComponentModel.Component.Dispose%2A> method.</span></span>

5. <span data-ttu-id="fecd3-411">`LightShape` Özelliğini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-411">Implement the `LightShape` property.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

6. <span data-ttu-id="fecd3-412">Geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fecd3-412">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="fecd3-413">Bu uygulama doldurulmuş bir kare ve daire çizecek.</span><span class="sxs-lookup"><span data-stu-id="fecd3-413">This implementation will draw a filled square and circle.</span></span> <span data-ttu-id="fecd3-414">Ayrıca, bir şekil ya da diğeri etrafında kenarlık çizerek seçili değeri vurgulayacaktır.</span><span class="sxs-lookup"><span data-stu-id="fecd3-414">It will also highlight the selected value by drawing a border around one shape or the other.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="testing-your-custom-control-in-the-designer"></a><span data-ttu-id="fecd3-415">Tasarımcıda özel denetiminizi test etme</span><span class="sxs-lookup"><span data-stu-id="fecd3-415">Testing your Custom Control in the Designer</span></span>

<span data-ttu-id="fecd3-416">Bu noktada, `MarqueeControlLibrary` projeyi derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fecd3-416">At this point, you can build the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="fecd3-417">`MarqueeControl` Sınıfından devralan bir denetim oluşturarak ve onu bir formda kullanarak uygulamanızı test edin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-417">Test your implementation by creating a control that inherits from the `MarqueeControl` class and using it on a form.</span></span>

### <a name="to-create-a-custom-marqueecontrol-implementation"></a><span data-ttu-id="fecd3-418">Özel bir MarqueeControl uygulamasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fecd3-418">To create a custom MarqueeControl implementation</span></span>

1. <span data-ttu-id="fecd3-419">Windows Form Tasarımcısı `DemoMarqueeControl` açın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-419">Open `DemoMarqueeControl` in the Windows Forms Designer.</span></span> <span data-ttu-id="fecd3-420">Bu, `DemoMarqueeControl` türün bir örneğini oluşturur ve `MarqueeControlRootDesigner` türün bir örneğinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fecd3-420">This creates an instance of the `DemoMarqueeControl` type and displays it in an instance of the `MarqueeControlRootDesigner` type.</span></span>

2. <span data-ttu-id="fecd3-421">**Araç kutusunda** **MarqueeControlLibrary Components** sekmesini açın. Seçim için kullanılabilir `MarqueeBorder` ve `MarqueeText` denetimleri görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="fecd3-421">In the **Toolbox**, open the **MarqueeControlLibrary Components** tab. You will see the `MarqueeBorder` and `MarqueeText` controls available for selection.</span></span>

3. <span data-ttu-id="fecd3-422">`MarqueeBorder` Denetimin`DemoMarqueeControl` bir örneğini tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-422">Drag an instance of the `MarqueeBorder` control onto the `DemoMarqueeControl` design surface.</span></span> <span data-ttu-id="fecd3-423">Bu `MarqueeBorder` denetimi üst denetime yerleştir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-423">Dock this `MarqueeBorder` control to the parent control.</span></span>

4. <span data-ttu-id="fecd3-424">`MarqueeText` Denetimin`DemoMarqueeControl` bir örneğini tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-424">Drag an instance of the `MarqueeText` control onto the `DemoMarqueeControl` design surface.</span></span>

5. <span data-ttu-id="fecd3-425">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fecd3-425">Build the solution.</span></span>

6. <span data-ttu-id="fecd3-426">Sağ tıklayıp kısayol menüsünden `DemoMarqueeControl` , animasyonu başlatmak için **Test Çalıştır** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-426">Right-click the `DemoMarqueeControl` and from the shortcut menu select the **Run Test** option to start the animation.</span></span> <span data-ttu-id="fecd3-427">Animasyonu durdurmak için **Sınamayı Durdur** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-427">Click **Stop Test** to stop the animation.</span></span>

7. <span data-ttu-id="fecd3-428">Tasarım görünümü 'da **Form1** ' i açın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-428">Open **Form1** in Design view.</span></span>

8. <span data-ttu-id="fecd3-429">Forma iki <xref:System.Windows.Forms.Button> denetim koyun.</span><span class="sxs-lookup"><span data-stu-id="fecd3-429">Place two <xref:System.Windows.Forms.Button> controls on the form.</span></span> <span data-ttu-id="fecd3-430">Onları `startButton` ve <xref:System.Windows.Forms.Control.Text%2A>olarak adlandırın ve sırasıyla başlangıç ve durdurma özelliği değerlerini değiştirin. `stopButton`</span><span class="sxs-lookup"><span data-stu-id="fecd3-430">Name them `startButton` and `stopButton`, and change the <xref:System.Windows.Forms.Control.Text%2A> property values to **Start** and **Stop**, respectively.</span></span>

9. <span data-ttu-id="fecd3-431">Her <xref:System.Windows.Forms.Control.Click> iki denetim için de <xref:System.Windows.Forms.Button> olay işleyicileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-431">Implement <xref:System.Windows.Forms.Control.Click> event handlers for both <xref:System.Windows.Forms.Button> controls.</span></span>

10. <span data-ttu-id="fecd3-432">**Araç kutusunda** **MarqueeControlTest Components** sekmesini açın. Seçim için `DemoMarqueeControl` kullanılabilir seçeneğini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="fecd3-432">In the **Toolbox**, open the **MarqueeControlTest Components** tab. You will see the `DemoMarqueeControl` available for selection.</span></span>

11. <span data-ttu-id="fecd3-433">Bir örneğini `DemoMarqueeControl` **Form1** tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-433">Drag an instance of `DemoMarqueeControl` onto the **Form1** design surface.</span></span>

12. <span data-ttu-id="fecd3-434">Olay işleyicilerinde, `Start` ve `Stop` üzerindeki `DemoMarqueeControl`yöntemlerini çağırın. <xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="fecd3-434">In the <xref:System.Windows.Forms.Control.Click> event handlers, invoke the `Start` and `Stop` methods on the `DemoMarqueeControl`.</span></span>

```vb
Private Sub startButton_Click(sender As Object, e As System.EventArgs)
    Me.demoMarqueeControl1.Start()
End Sub 'startButton_Click

Private Sub stopButton_Click(sender As Object, e As System.EventArgs)
Me.demoMarqueeControl1.Stop()
End Sub 'stopButton_Click
```

```csharp
private void startButton_Click(object sender, System.EventArgs e)
{
    this.demoMarqueeControl1.Start();
}

private void stopButton_Click(object sender, System.EventArgs e)
{
    this.demoMarqueeControl1.Stop();
}
```

1. <span data-ttu-id="fecd3-435">`MarqueeControlTest` Projeyi başlangıç projesi olarak ayarlayın ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-435">Set the `MarqueeControlTest` project as the startup project and run it.</span></span> <span data-ttu-id="fecd3-436">Formunu görüntüleyen `DemoMarqueeControl`formu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="fecd3-436">You will see the form displaying your `DemoMarqueeControl`.</span></span> <span data-ttu-id="fecd3-437">Animasyonu başlatmak için **Başlat** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-437">Click the **Start** button to start the animation.</span></span> <span data-ttu-id="fecd3-438">Metnin yanıp sönmesi ve kenarlığın etrafında hareket eden ışıklar görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-438">You should see the text flashing and the lights moving around the border.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fecd3-439">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="fecd3-439">Next Steps</span></span>

<span data-ttu-id="fecd3-440">, `MarqueeControlLibrary` Özel denetimlerin ve ilişkili tasarımcılarının basit bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fecd3-440">The `MarqueeControlLibrary` demonstrates a simple implementation of custom controls and associated designers.</span></span> <span data-ttu-id="fecd3-441">Bu örneği çeşitli yollarla daha karmaşık hale getirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fecd3-441">You can make this sample more sophisticated in several ways:</span></span>

- <span data-ttu-id="fecd3-442">Tasarımcı `DemoMarqueeControl` içindeki için özellik değerlerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-442">Change the property values for the `DemoMarqueeControl` in the designer.</span></span> <span data-ttu-id="fecd3-443">Daha fazla `MarqueBorder` denetim ekleyin ve iç içe geçmiş bir efekt oluşturmak için bunları üst örnekleri içine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-443">Add more `MarqueBorder` controls and dock them within their parent instances to create a nested effect.</span></span> <span data-ttu-id="fecd3-444">`UpdatePeriod` Ve ışığıyla ilgili özellikler için farklı ayarlarla denemeler yapın.</span><span class="sxs-lookup"><span data-stu-id="fecd3-444">Experiment with different settings for the `UpdatePeriod` and the light-related properties.</span></span>

- <span data-ttu-id="fecd3-445">Kendi uygulamalarınızı yazar `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="fecd3-445">Author your own implementations of `IMarqueeWidget`.</span></span> <span data-ttu-id="fecd3-446">Örneğin, yanıp sönen bir "Neon Sign" veya birden çok görüntüde animasyonlu bir işaret oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fecd3-446">You could, for example, create a flashing "neon sign" or an animated sign with multiple images.</span></span>

- <span data-ttu-id="fecd3-447">Tasarım zamanı deneyimini daha da özelleştirin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-447">Further customize the design-time experience.</span></span> <span data-ttu-id="fecd3-448"><xref:System.Windows.Forms.Control.Enabled%2A> Ve<xref:System.Windows.Forms.Control.Visible%2A>' den daha fazla özelliği gölgelendirmeyi deneyebilirsiniz ve yeni özellikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fecd3-448">You could try shadowing more properties than <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A>, and you could add new properties.</span></span> <span data-ttu-id="fecd3-449">Alt öğe denetimleri yerleştirme gibi yaygın görevleri basitleştirmek için yeni tasarımcı fiilleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-449">Add new designer verbs to simplify common tasks like docking child controls.</span></span>

- <span data-ttu-id="fecd3-450">Lisansına sahip `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="fecd3-450">License the `MarqueeControl`.</span></span> <span data-ttu-id="fecd3-451">Daha fazla bilgi için [nasıl yapılır: Lisans bileşenleri ve denetimleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="fecd3-451">For more information, see [How to: License Components and Controls](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120)).</span></span>

- <span data-ttu-id="fecd3-452">Denetimlerinizin serileştirilme şeklini ve kodun onlar için nasıl oluşturulduğunu denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fecd3-452">Control how your controls are serialized and how code is generated for them.</span></span> <span data-ttu-id="fecd3-453">Daha fazla bilgi için bkz. [dinamik kaynak kodu oluşturma ve derleme](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="fecd3-453">For more information, see [Dynamic Source Code Generation and Compilation](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fecd3-454">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fecd3-454">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
- <span data-ttu-id="fecd3-455">[Nasıl yapılır: Tasarım zamanı özelliklerinden faydalanan bir Windows Forms denetimi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="fecd3-455">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span></span>
- <span data-ttu-id="fecd3-456">[Tasarım zamanı desteğini genişletme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="fecd3-456">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>
- <span data-ttu-id="fecd3-457">[Özel tasarımcılar](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h51z5c0x(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="fecd3-457">[Custom Designers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h51z5c0x(v=vs.120))</span></span>
