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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b72c449ab68c9bb2ceea6f8ee78abe6771b9a8bd
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016004"
---
# <a name="walkthrough-create-a-control-that-takes-advantage-of-design-time-features"></a><span data-ttu-id="20926-102">İzlenecek yol: Tasarım zamanı özelliklerinden faydalanan bir denetim oluşturma</span><span class="sxs-lookup"><span data-stu-id="20926-102">Walkthrough: Create a control that takes advantage of design-time features</span></span>

<span data-ttu-id="20926-103">Özel bir denetim için tasarım zamanı deneyimi, ilişkili bir özel tasarımcı Authoring ile geliştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="20926-103">The design-time experience for a custom control can be enhanced by authoring an associated custom designer.</span></span>

<span data-ttu-id="20926-104">Bu makalede özel bir denetim için nasıl özel tasarımcı oluşturacağınız açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="20926-104">This article illustrates how to create a custom designer for a custom control.</span></span> <span data-ttu-id="20926-105">`MarqueeControl` Adlı`MarqueeControlRootDesigner`bir tür ve ilişkili tasarımcı sınıfını uygulayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="20926-105">You'll implement a `MarqueeControl` type and an associated designer class called `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="20926-106">Türü `MarqueeControl` , animasyonlu ışıklar ve yanıp sönen metinle benzer bir tiyatro çerçevesine benzer bir ekran uygular.</span><span class="sxs-lookup"><span data-stu-id="20926-106">The `MarqueeControl` type implements a display similar to a theater marquee with animated lights and flashing text.</span></span>

<span data-ttu-id="20926-107">Bu denetim için tasarımcı, tasarım ortamıyla birlikte etkileşimde bulunur ve özel bir tasarım zamanı deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="20926-107">The designer for this control interacts with the design environment to provide a custom design-time experience.</span></span> <span data-ttu-id="20926-108">Özel tasarımcı sayesinde, bir özel `MarqueeControl` uygulamayı animasyonlu ışıklar ve yanıp sönen metni birçok birleşimde bir araya getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20926-108">With the custom designer, you can assemble a custom `MarqueeControl` implementation with animated lights and flashing text in many combinations.</span></span> <span data-ttu-id="20926-109">Bir form üzerinde, diğer Windows Forms denetimleri gibi, birleştirilmiş denetimi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20926-109">You can use the assembled control on a form like any other Windows Forms control.</span></span>

<span data-ttu-id="20926-110">Bu yönergeyi tamamladığınızda, özel denetiminiz aşağıdakine benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="20926-110">When you're finished with this walkthrough, your custom control will look something like the following:</span></span>

![Metin ve Başlat ve Durdur düğmelerini gösteren bir kayan yazıyı gösteren uygulama.](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

<span data-ttu-id="20926-112">Tüm kod listesi için bkz [. nasıl yapılır: Tasarım zamanı özelliklerinden](/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))faydalanan bir Windows Forms denetimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="20926-112">For the complete code listing, see [How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="20926-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="20926-113">Prerequisites</span></span>

<span data-ttu-id="20926-114">Bu izlenecek yolu tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="20926-114">In order to complete this walkthrough, you'll need Visual Studio.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="20926-115">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="20926-115">Create the project</span></span>

<span data-ttu-id="20926-116">İlk adım uygulama projesini oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="20926-116">The first step is to create the application project.</span></span> <span data-ttu-id="20926-117">Bu projeyi, özel denetimi barındıran uygulamayı oluşturmak için kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="20926-117">You will use this project to build the application that hosts the custom control.</span></span>

<span data-ttu-id="20926-118">Visual Studio 'da yeni bir Windows Forms uygulama projesi oluşturun ve **MarqueeControlTest**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="20926-118">In Visual Studio, create a new Windows Forms Application project, and name it **MarqueeControlTest**.</span></span>

## <a name="create-the-control-library-project"></a><span data-ttu-id="20926-119">Denetim kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="20926-119">Create the control library project</span></span>

1. <span data-ttu-id="20926-120">Çözüme bir Windows Forms denetim kitaplığı projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20926-120">Add a Windows Forms Control Library project to the solution.</span></span> <span data-ttu-id="20926-121">Projeyi **MarqueeControlLibrary**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="20926-121">Name the project **MarqueeControlLibrary**.</span></span>

2. <span data-ttu-id="20926-122">**Çözüm Gezgini**kullanarak, tercih ettiğiniz dile bağlı olarak, "UserControl1.cs" veya "UserControl1. vb" adlı kaynak dosyayı silerek projenin varsayılan denetimini silin.</span><span class="sxs-lookup"><span data-stu-id="20926-122">Using **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span>

3. <span data-ttu-id="20926-123">`MarqueeControlLibrary` Projeye yeni <xref:System.Windows.Forms.UserControl> bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20926-123">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="20926-124">Yeni kaynak dosyasına **MarqueeControl**temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="20926-124">Give the new source file a base name of **MarqueeControl**.</span></span>

4. <span data-ttu-id="20926-125">**Çözüm Gezgini**kullanarak `MarqueeControlLibrary` projede yeni bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="20926-125">Using **Solution Explorer**, create a new folder in the `MarqueeControlLibrary` project.</span></span>

5. <span data-ttu-id="20926-126">**Tasarım** klasörüne sağ tıklayın ve yeni bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20926-126">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="20926-127">**MarqueeControlRootDesigner**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="20926-127">Name it **MarqueeControlRootDesigner**.</span></span>

6. <span data-ttu-id="20926-128">System. Design derlemesinden türler kullanmanız gerekir, bu nedenle bu başvuruyu `MarqueeControlLibrary` projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20926-128">You'll need to use types from the System.Design assembly, so add this reference to the `MarqueeControlLibrary` project.</span></span>

## <a name="reference-the-custom-control-project"></a><span data-ttu-id="20926-129">Özel denetim projesine başvur</span><span class="sxs-lookup"><span data-stu-id="20926-129">Reference the Custom Control Project</span></span>

<span data-ttu-id="20926-130">Bu `MarqueeControlTest` projeyi, özel denetimi test etmek için kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="20926-130">You will use the `MarqueeControlTest` project to test the custom control.</span></span> <span data-ttu-id="20926-131">`MarqueeControlLibrary` Derlemeye bir proje başvurusu eklediğinizde test projesi özel denetimden haberdar olur.</span><span class="sxs-lookup"><span data-stu-id="20926-131">The test project will become aware of the custom control when you add a project reference to the `MarqueeControlLibrary` assembly.</span></span>

<span data-ttu-id="20926-132">Projede, `MarqueeControlLibrary` derlemeye bir proje başvurusu ekleyin. `MarqueeControlTest`</span><span class="sxs-lookup"><span data-stu-id="20926-132">In the `MarqueeControlTest` project, add a project reference to the `MarqueeControlLibrary` assembly.</span></span> <span data-ttu-id="20926-133">`MarqueeControlLibrary` Derlemeye doğrudan başvurmak yerine **Başvuru Ekle** iletişim kutusundaki **Projeler** sekmesini kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="20926-133">Be sure to use the **Projects** tab in the **Add Reference** dialog box instead of referencing the `MarqueeControlLibrary` assembly directly.</span></span>

## <a name="define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="20926-134">Özel bir denetim ve kendi özel tasarımcısını tanımlama</span><span class="sxs-lookup"><span data-stu-id="20926-134">Define a Custom Control and Its Custom Designer</span></span>

<span data-ttu-id="20926-135">Özel denetiminiz <xref:System.Windows.Forms.UserControl> sınıfından türecektir.</span><span class="sxs-lookup"><span data-stu-id="20926-135">Your custom control will derive from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="20926-136">Bu, denetiminizin diğer denetimleri içermesini sağlar ve denetimi, varsayılan işlevselliğin harika olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="20926-136">This allows your control to contain other controls, and it gives your control a great deal of default functionality.</span></span>

<span data-ttu-id="20926-137">Özel denetiminizin ilişkili bir özel Tasarımcısı olacak.</span><span class="sxs-lookup"><span data-stu-id="20926-137">Your custom control will have an associated custom designer.</span></span> <span data-ttu-id="20926-138">Bu, özel denetiminiz için özel olarak uyarlanmış benzersiz bir tasarım deneyimi oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="20926-138">This allows you to create a unique design experience tailored specifically for your custom control.</span></span>

<span data-ttu-id="20926-139"><xref:System.ComponentModel.DesignerAttribute> Sınıfını kullanarak denetimi Tasarımcı ile ilişkilendirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20926-139">You associate the control with its designer by using the <xref:System.ComponentModel.DesignerAttribute> class.</span></span> <span data-ttu-id="20926-140">Özel denetiminizin tüm tasarım zamanı davranışını geliştirmekte olduğunuzdan, özel tasarımcı <xref:System.ComponentModel.Design.IRootDesigner> arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="20926-140">Because you are developing the entire design-time behavior of your custom control, the custom designer will implement the <xref:System.ComponentModel.Design.IRootDesigner> interface.</span></span>

### <a name="to-define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="20926-141">Özel bir denetim ve özel tasarımcı tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="20926-141">To define a custom control and its custom designer</span></span>

1. <span data-ttu-id="20926-142">Kaynak dosyasını kod düzenleyicisinde açın. `MarqueeControl`</span><span class="sxs-lookup"><span data-stu-id="20926-142">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="20926-143">Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="20926-143">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. <span data-ttu-id="20926-144"><xref:System.ComponentModel.DesignerAttribute> Sınıfını`MarqueeControl` sınıf bildirimine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20926-144">Add the <xref:System.ComponentModel.DesignerAttribute> to the `MarqueeControl` class declaration.</span></span> <span data-ttu-id="20926-145">Bu, özel denetimi Tasarımcı ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="20926-145">This associates the custom control with its designer.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. <span data-ttu-id="20926-146">Kaynak dosyasını kod düzenleyicisinde açın. `MarqueeControlRootDesigner`</span><span class="sxs-lookup"><span data-stu-id="20926-146">Open the `MarqueeControlRootDesigner` source file in the **Code Editor**.</span></span> <span data-ttu-id="20926-147">Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="20926-147">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. <span data-ttu-id="20926-148">Bildirimini `MarqueeControlRootDesigner` <xref:System.Windows.Forms.Design.DocumentDesigner> sınıfından devralacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="20926-148">Change the declaration of `MarqueeControlRootDesigner` to inherit from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="20926-149">**Araç kutusu**ile tasarımcı etkileşimini belirtmek içinöğesiniuygulayın.<xref:System.ComponentModel.ToolboxItemFilterAttribute></span><span class="sxs-lookup"><span data-stu-id="20926-149">Apply the <xref:System.ComponentModel.ToolboxItemFilterAttribute> to specify the designer interaction with the **Toolbox**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="20926-150">`MarqueeControlRootDesigner` Sınıfının tanımı, MarqueeControlLibrary. Design adlı bir ad alanı içine alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="20926-150">The definition for the `MarqueeControlRootDesigner` class has been enclosed in a namespace called MarqueeControlLibrary.Design.</span></span> <span data-ttu-id="20926-151">Bu bildirim, tasarımcıyı tasarımla ilgili türler için ayrılmış özel bir ad alanına koyar.</span><span class="sxs-lookup"><span data-stu-id="20926-151">This declaration places the designer in a special namespace reserved for design-related types.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. <span data-ttu-id="20926-152">`MarqueeControlRootDesigner` Sınıf için oluşturucuyu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="20926-152">Define the constructor for the `MarqueeControlRootDesigner` class.</span></span> <span data-ttu-id="20926-153">Oluşturucu gövdesine <xref:System.Diagnostics.Trace.WriteLine%2A> bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20926-153">Insert a <xref:System.Diagnostics.Trace.WriteLine%2A> statement in the constructor body.</span></span> <span data-ttu-id="20926-154">Bu, hata ayıklama için yararlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="20926-154">This will be useful for debugging.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="create-an-instance-of-your-custom-control"></a><span data-ttu-id="20926-155">Özel denetiminizin bir örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="20926-155">Create an instance of your custom control</span></span>

1. <span data-ttu-id="20926-156">`MarqueeControlTest` Projeye yeni <xref:System.Windows.Forms.UserControl> bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20926-156">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlTest` project.</span></span> <span data-ttu-id="20926-157">Yeni kaynak dosyasına **DemoMarqueeControl**temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="20926-157">Give the new source file a base name of **DemoMarqueeControl**.</span></span>

2. <span data-ttu-id="20926-158">Dosyayı kod düzenleyicisinde açın. `DemoMarqueeControl`</span><span class="sxs-lookup"><span data-stu-id="20926-158">Open the `DemoMarqueeControl` file in the **Code Editor**.</span></span> <span data-ttu-id="20926-159">Dosyanın en üstünde, `MarqueeControlLibrary` ad alanını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="20926-159">At the top of the file, import the `MarqueeControlLibrary` namespace:</span></span>

   ```vb
   Imports MarqueeControlLibrary
   ```

   ```csharp
   using MarqueeControlLibrary;
   ```

3. <span data-ttu-id="20926-160">Bildirimini `DemoMarqueeControl` `MarqueeControl` sınıfından devralacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="20926-160">Change the declaration of `DemoMarqueeControl` to inherit from the `MarqueeControl` class.</span></span>

4. <span data-ttu-id="20926-161">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="20926-161">Build the project.</span></span>

5. <span data-ttu-id="20926-162">Windows Form Tasarımcısı Form1 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="20926-162">Open Form1 in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="20926-163">**Araç kutusunda** **MarqueeControlTest Components** sekmesini bulun ve açın.</span><span class="sxs-lookup"><span data-stu-id="20926-163">Find the **MarqueeControlTest Components** tab in the **Toolbox** and open it.</span></span> <span data-ttu-id="20926-164">`DemoMarqueeControl` **Araç kutusundan** bir öğesini formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="20926-164">Drag a `DemoMarqueeControl` from the **Toolbox** onto your form.</span></span>

7. <span data-ttu-id="20926-165">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="20926-165">Build the project.</span></span>

## <a name="set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="20926-166">Projeyi tasarım zamanı hata ayıklama için ayarlama</span><span class="sxs-lookup"><span data-stu-id="20926-166">Set Up the Project for Design-Time Debugging</span></span>

<span data-ttu-id="20926-167">Özel bir tasarım zamanı deneyimi geliştirirken, denetimlerinizin ve bileşenlerinizin hata ayıklaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="20926-167">When you're developing a custom design-time experience, it will be necessary to debug your controls and components.</span></span> <span data-ttu-id="20926-168">Projenizi tasarım zamanında hata ayıklamaya izin verecek şekilde kurmak için basit bir yol vardır.</span><span class="sxs-lookup"><span data-stu-id="20926-168">There is a simple way to set up your project to allow debugging at design time.</span></span> <span data-ttu-id="20926-169">Daha fazla bilgi için bkz [. İzlenecek yol: Tasarım zamanında](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)özel Windows Forms Denetimlerinde hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="20926-169">For more information, see [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>

1. <span data-ttu-id="20926-170">`MarqueeControlLibrary` Projeye sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="20926-170">Right-click the `MarqueeControlLibrary` project and select **Properties**.</span></span>

2. <span data-ttu-id="20926-171">**MarqueeControlLibrary Özellik sayfaları** Iletişim kutusunda **hata ayıklama** sayfasını seçin.</span><span class="sxs-lookup"><span data-stu-id="20926-171">In the **MarqueeControlLibrary Property Pages** dialog box, select the **Debug** page.</span></span>

3. <span data-ttu-id="20926-172">**Başlangıç eylemi** bölümünde **dış program Başlat**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="20926-172">In the **Start Action** section, select **Start External Program**.</span></span> <span data-ttu-id="20926-173">Visual Studio 'nun ayrı bir örneğinde hata ayıkladığınızda, Visual Studio IDE 'ye gitmek için![üç nokta (Visual Studio](./media/visual-studio-ellipsis-button.png)'nun Özellikler penceresi) düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="20926-173">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="20926-174">Yürütülebilir dosyanın adı devenv. exe ' dir ve varsayılan konuma yüklediyseniz, yolu *% ProgramFiles (x86)% \ Microsoft Visual studio\2019\\\<Edition > \Common7\IDE\devenv.exe*olur.</span><span class="sxs-lookup"><span data-stu-id="20926-174">The name of the executable file is devenv.exe, and if you installed to the default location, its path is *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\\\<edition>\Common7\IDE\devenv.exe*.</span></span>

4. <span data-ttu-id="20926-175">İletişim kutusunu kapatmak için **Tamam ' ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="20926-175">Select **OK** to close the dialog box.</span></span>

5. <span data-ttu-id="20926-176">Bu hata ayıklama yapılandırmasını etkinleştirmek için MarqueeControlLibrary projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="20926-176">Right-click the MarqueeControlLibrary project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>

## <a name="checkpoint"></a><span data-ttu-id="20926-177">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="20926-177">Checkpoint</span></span>

<span data-ttu-id="20926-178">Artık özel denetiminizin tasarım zamanı davranışını hata ayıklamaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="20926-178">You are now ready to debug the design-time behavior of your custom control.</span></span> <span data-ttu-id="20926-179">Hata ayıklama ortamının doğru şekilde ayarlandığını belirledikten sonra, özel denetim ve özel tasarımcı arasındaki ilişkilendirmeyi test edersiniz.</span><span class="sxs-lookup"><span data-stu-id="20926-179">Once you've determined that the debugging environment is set up correctly, you'll test the association between the custom control and the custom designer.</span></span>

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a><span data-ttu-id="20926-180">Hata ayıklama ortamını ve tasarımcı ilişkilendirmesini test etmek için</span><span class="sxs-lookup"><span data-stu-id="20926-180">To test the debugging environment and the designer association</span></span>

1. <span data-ttu-id="20926-181">**Kod düzenleyicisinde** MarqueeControlRootDesigner kaynak dosyasını açın ve <xref:System.Diagnostics.Trace.WriteLine%2A> deyime bir kesme noktası yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="20926-181">Open the MarqueeControlRootDesigner source file in the **Code Editor** and place a breakpoint on the <xref:System.Diagnostics.Trace.WriteLine%2A> statement.</span></span>

2. <span data-ttu-id="20926-182">Hata ayıklama oturumu başlatmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="20926-182">Press **F5** to start the debugging session.</span></span>

   <span data-ttu-id="20926-183">Visual Studio 'nun yeni bir örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="20926-183">A new instance of Visual Studio is created.</span></span>

3. <span data-ttu-id="20926-184">Visual Studio 'nun yeni örneğinde, MarqueeControlTest çözümünü açın.</span><span class="sxs-lookup"><span data-stu-id="20926-184">In the new instance of Visual Studio, open the MarqueeControlTest solution.</span></span> <span data-ttu-id="20926-185">**Dosya** menüsünden **son projeler** ' i seçerek çözümü kolayca bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20926-185">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="20926-186">MarqueeControlTest. sln çözüm dosyası en son kullanılan dosya olarak listelenecektir.</span><span class="sxs-lookup"><span data-stu-id="20926-186">The MarqueeControlTest.sln solution file will be listed as the most recently used file.</span></span>

4. <span data-ttu-id="20926-187">`DemoMarqueeControl` Öğesini tasarımcıda açın.</span><span class="sxs-lookup"><span data-stu-id="20926-187">Open the `DemoMarqueeControl` in the designer.</span></span>

   <span data-ttu-id="20926-188">Visual Studio 'nun hata ayıklama örneği, kesme noktasında odak ve yürütme işlemini alır.</span><span class="sxs-lookup"><span data-stu-id="20926-188">The debugging instance of Visual Studio obtains focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="20926-189">Hata ayıklama oturumuna devam etmek için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="20926-189">Press **F5** to continue the debugging session.</span></span>

<span data-ttu-id="20926-190">Bu noktada, özel denetiminizi ve onunla ilişkili özel tasarımcıyı geliştirip hata ayıklamanızın her şey vardır.</span><span class="sxs-lookup"><span data-stu-id="20926-190">At this point, everything is in place for you to develop and debug your custom control and its associated custom designer.</span></span> <span data-ttu-id="20926-191">Bu makalenin geri kalanında, denetimin ve tasarımcının özelliklerini uygulama ayrıntılarına yoğunlaşmaktadır.</span><span class="sxs-lookup"><span data-stu-id="20926-191">The remainder of this article concentrates on the details of implementing features of the control and the designer.</span></span>

## <a name="implement-the-custom-control"></a><span data-ttu-id="20926-192">Özel denetimi uygulama</span><span class="sxs-lookup"><span data-stu-id="20926-192">Implement the Custom Control</span></span>

<span data-ttu-id="20926-193">, `MarqueeControl` Bir<xref:System.Windows.Forms.UserControl> özelleştirme biraz daha vardır.</span><span class="sxs-lookup"><span data-stu-id="20926-193">The `MarqueeControl` is a <xref:System.Windows.Forms.UserControl> with a little bit of customization.</span></span> <span data-ttu-id="20926-194">İki yöntem sunar: `Start`, kayan yazı animasyonunu başlatan ve `Stop`animasyonu durduran.</span><span class="sxs-lookup"><span data-stu-id="20926-194">It exposes two methods: `Start`, which starts the marquee animation, and `Stop`, which stops the animation.</span></span> <span data-ttu-id="20926-195">, `MarqueeControl` `StopMarquee` `StartMarquee` Arabirimini `IMarqueeWidget` uygulayanaltdenetimleriçerdiğindenveherbiraltdenetimivesırasıylaveyöntemleriniherbiraltdenetimdesırasıylaçağırmak`Start`için `Stop` uygulayan `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="20926-195">Because the `MarqueeControl` contains child controls that implement the `IMarqueeWidget` interface, `Start` and `Stop` enumerate each child control and call the `StartMarquee` and `StopMarquee` methods, respectively, on each child control that implements `IMarqueeWidget`.</span></span>

<span data-ttu-id="20926-196">`MarqueeBorder` Ve `MarqueeControl` denetimleriningörünümü<xref:System.Windows.Forms.Control.OnLayout%2A> düzene bağlıdır, bu nedenle yöntemi ve bu türün alt denetimlerinde yapılan çağrıları <xref:System.Windows.Forms.Control.PerformLayout%2A> geçersiz kılar. `MarqueeText`</span><span class="sxs-lookup"><span data-stu-id="20926-196">The appearance of the `MarqueeBorder` and `MarqueeText` controls is dependent on the layout, so `MarqueeControl` overrides the <xref:System.Windows.Forms.Control.OnLayout%2A> method and calls <xref:System.Windows.Forms.Control.PerformLayout%2A> on child controls of this type.</span></span>

<span data-ttu-id="20926-197">Bu, `MarqueeControl` özelleştirmelerin bir kapsamını.</span><span class="sxs-lookup"><span data-stu-id="20926-197">This is the extent of the `MarqueeControl` customizations.</span></span> <span data-ttu-id="20926-198">Çalışma zamanı özellikleri `MarqueeBorder` ve `MarqueeText` denetimleri tarafından uygulanır ve tasarım zamanı `MarqueeBorderDesigner` özellikleri ve `MarqueeControlRootDesigner` sınıfları tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="20926-198">The run-time features are implemented by the `MarqueeBorder` and `MarqueeText` controls, and the design-time features are implemented by the `MarqueeBorderDesigner` and `MarqueeControlRootDesigner` classes.</span></span>

### <a name="to-implement-your-custom-control"></a><span data-ttu-id="20926-199">Özel denetiminizi uygulamak için</span><span class="sxs-lookup"><span data-stu-id="20926-199">To implement your custom control</span></span>

1. <span data-ttu-id="20926-200">Kaynak dosyasını kod düzenleyicisinde açın. `MarqueeControl`</span><span class="sxs-lookup"><span data-stu-id="20926-200">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="20926-201">`Start` Ve`Stop` yöntemlerini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="20926-201">Implement the `Start` and `Stop` methods.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. <span data-ttu-id="20926-202">Geçersiz kılma <xref:System.Windows.Forms.Control.OnLayout%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="20926-202">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="create-a-child-control-for-your-custom-control"></a><span data-ttu-id="20926-203">Özel denetiminiz için bir alt denetim oluşturma</span><span class="sxs-lookup"><span data-stu-id="20926-203">Create a Child Control for Your Custom Control</span></span>

<span data-ttu-id="20926-204">İki tür alt denetimi barındırır `MarqueeBorder` : denetim ve `MarqueeText` denetim. `MarqueeControl`</span><span class="sxs-lookup"><span data-stu-id="20926-204">The `MarqueeControl` will host two kinds of child control: the `MarqueeBorder` control and the `MarqueeText` control.</span></span>

- <span data-ttu-id="20926-205">`MarqueeBorder`: Bu denetim, kenarları etrafında "ışıklar" kenarlığını boyar.</span><span class="sxs-lookup"><span data-stu-id="20926-205">`MarqueeBorder`: This control paints a border of "lights" around its edges.</span></span> <span data-ttu-id="20926-206">Kenarlıkta bulunan ışıklar, kenarlık etrafında taşınıyor gibi görünürler.</span><span class="sxs-lookup"><span data-stu-id="20926-206">The lights flash in sequence, so they appear to be moving around the border.</span></span> <span data-ttu-id="20926-207">Işıklarının flaşın, çağrılan `UpdatePeriod`bir özellik tarafından denetlenme hızı.</span><span class="sxs-lookup"><span data-stu-id="20926-207">The speed at which the lights flash is controlled by a property called `UpdatePeriod`.</span></span> <span data-ttu-id="20926-208">Diğer birçok özel özellik, denetimin görünümünün diğer yönlerini tespit.</span><span class="sxs-lookup"><span data-stu-id="20926-208">Several other custom properties determine other aspects of the control's appearance.</span></span> <span data-ttu-id="20926-209">Animasyon başladığında ve durdurulduğunda `StartMarquee` denetim `StopMarquee`olarak adlandırılan iki yöntem.</span><span class="sxs-lookup"><span data-stu-id="20926-209">Two methods, called `StartMarquee` and `StopMarquee`, control when the animation starts and stops.</span></span>

- <span data-ttu-id="20926-210">`MarqueeText`: Bu denetim yanıp sönen bir dizeyi boyar.</span><span class="sxs-lookup"><span data-stu-id="20926-210">`MarqueeText`: This control paints a flashing string.</span></span> <span data-ttu-id="20926-211">Denetim gibi, metnin yanıp sönebileceği hız, `UpdatePeriod` özelliği tarafından kontrol edilir. `MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="20926-211">Like the `MarqueeBorder` control, the speed at which the text flashes is controlled by the `UpdatePeriod` property.</span></span> <span data-ttu-id="20926-212">Denetim Ayrıca, `StartMarquee` denetimiyle`MarqueeBorder` ortak olan `StopMarquee` ve yöntemlerine sahiptir. `MarqueeText`</span><span class="sxs-lookup"><span data-stu-id="20926-212">The `MarqueeText` control also has the `StartMarquee` and `StopMarquee` methods in common with the `MarqueeBorder` control.</span></span>

<span data-ttu-id="20926-213">Tasarım zamanında `MarqueeControlRootDesigner` , bu iki denetim türünün herhangi bir `MarqueeControl` kombinasyonda içine eklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="20926-213">At design time, the `MarqueeControlRootDesigner` allows these two control types to be added to a `MarqueeControl` in any combination.</span></span>

<span data-ttu-id="20926-214">İki denetimin ortak özellikleri, adlı `IMarqueeWidget`bir arabirimle birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="20926-214">Common features of the two controls are factored into an interface called `IMarqueeWidget`.</span></span> <span data-ttu-id="20926-215">Bu, `MarqueeControl` bir seçim çerçevesinin ilgili alt denetimleri bulmasını ve özel bir işleme vermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="20926-215">This allows the `MarqueeControl` to discover any Marquee-related child controls and give them special treatment.</span></span>

<span data-ttu-id="20926-216">Düzenli animasyon özelliğini uygulamak için, <xref:System.ComponentModel.BackgroundWorker> <xref:System.ComponentModel?displayProperty=nameWithType> ad alanındaki nesneleri kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="20926-216">To implement the periodic animation feature, you will use <xref:System.ComponentModel.BackgroundWorker> objects from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="20926-217">Nesneleri kullanabilirsiniz <xref:System.Windows.Forms.Timer> , ancak birçok `IMarqueeWidget` nesne mevcut olduğunda, tek UI iş parçacığı animasyonla birlikte tutulamayabilir.</span><span class="sxs-lookup"><span data-stu-id="20926-217">You could use <xref:System.Windows.Forms.Timer> objects, but when many `IMarqueeWidget` objects are present, the single UI thread may be unable to keep up with the animation.</span></span>

### <a name="to-create-a-child-control-for-your-custom-control"></a><span data-ttu-id="20926-218">Özel denetiminiz için bir alt denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="20926-218">To create a child control for your custom control</span></span>

1. <span data-ttu-id="20926-219">`MarqueeControlLibrary` Projeye yeni bir sınıf öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20926-219">Add a new class item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="20926-220">Yeni kaynak dosyasına "Imarqueepencere öğesi" için temel adı verin.</span><span class="sxs-lookup"><span data-stu-id="20926-220">Give the new source file a base name of "IMarqueeWidget."</span></span>

2. <span data-ttu-id="20926-221">Kaynak dosyasını **kod düzenleyicisinde** açın ve bildirimi ' den `class` ' e `interface`değiştirin: `IMarqueeWidget`</span><span class="sxs-lookup"><span data-stu-id="20926-221">Open the `IMarqueeWidget` source file in the **Code Editor** and change the declaration from `class` to `interface`:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. <span data-ttu-id="20926-222">İki yöntemi ve kayan yazı animasyonunu `IMarqueeWidget` işleyen bir özelliği göstermek için aşağıdaki kodu arabirimine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="20926-222">Add the following code to the `IMarqueeWidget` interface to expose two methods and a property that manipulate the marquee animation:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. <span data-ttu-id="20926-223">`MarqueeControlLibrary` Projeye yeni bir **özel denetim** öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20926-223">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="20926-224">Yeni kaynak dosyasına "MarqueeText" temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="20926-224">Give the new source file a base name of "MarqueeText."</span></span>

5. <span data-ttu-id="20926-225">**Araç kutusundan** bir <xref:System.ComponentModel.BackgroundWorker> bileşeni denetimüzerinesürükleyin.`MarqueeText`</span><span class="sxs-lookup"><span data-stu-id="20926-225">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeText` control.</span></span> <span data-ttu-id="20926-226">Bu bileşen `MarqueeText` denetimin kendisini zaman uyumsuz olarak güncelleştirmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="20926-226">This component will allow the `MarqueeText` control to update itself asynchronously.</span></span>

6. <span data-ttu-id="20926-227">**Özellikler** penceresinde <xref:System.ComponentModel.BackgroundWorker> , bileşen `WorkerReportsProgress` ve <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliklerini **doğru**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="20926-227">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to **true**.</span></span> <span data-ttu-id="20926-228">Bu ayarlar, <xref:System.ComponentModel.BackgroundWorker> bileşenin düzenli olarak <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayı kullanmasına ve zaman uyumsuz güncelleştirmeleri iptal edebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="20926-228">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span>

   <span data-ttu-id="20926-229">Daha fazla bilgi için bkz. [BackgroundWorker Component](backgroundworker-component.md).</span><span class="sxs-lookup"><span data-stu-id="20926-229">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

7. <span data-ttu-id="20926-230">Kaynak dosyasını kod düzenleyicisinde açın. `MarqueeText`</span><span class="sxs-lookup"><span data-stu-id="20926-230">Open the `MarqueeText` source file in the **Code Editor**.</span></span> <span data-ttu-id="20926-231">Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="20926-231">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. <span data-ttu-id="20926-232">' Dan `MarqueeText` <xref:System.Windows.Forms.Label> devralması için bildirimini değiştirin ve `IMarqueeWidget` arabirimini uygulayın:</span><span class="sxs-lookup"><span data-stu-id="20926-232">Change the declaration of `MarqueeText` to inherit from <xref:System.Windows.Forms.Label> and to implement the `IMarqueeWidget` interface:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. <span data-ttu-id="20926-233">Gösterilen özelliklere karşılık gelen örnek değişkenlerini bildirin ve bunları oluşturucuda başlatın.</span><span class="sxs-lookup"><span data-stu-id="20926-233">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span> <span data-ttu-id="20926-234">Alan, metnin `LightColor` özelliği tarafından verilen renkte boyanmış olup olmayacağını belirler. `isLit`</span><span class="sxs-lookup"><span data-stu-id="20926-234">The `isLit` field determines if the text is to be painted in the color given by the `LightColor` property.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. <span data-ttu-id="20926-235">`IMarqueeWidget` arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="20926-235">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="20926-236">Ve `StartMarquee` yöntemleri,<xref:System.ComponentModel.BackgroundWorker> animasyonu başlatmak ve durdurmak için <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> bileşenin veyöntemleriniçağırır.<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> `StopMarquee`</span><span class="sxs-lookup"><span data-stu-id="20926-236">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="20926-237"><xref:System.ComponentModel.CategoryAttribute.Category%2A> Ve<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A>öznitelikleri, "kayan yazı" adlı Özellikler penceresi özel bir bölümünde görünmesi için özelliğineuygulanır.`UpdatePeriod`</span><span class="sxs-lookup"><span data-stu-id="20926-237">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to the `UpdatePeriod` property so it appears in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. <span data-ttu-id="20926-238">Özellik erişimcileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="20926-238">Implement the property accessors.</span></span> <span data-ttu-id="20926-239">İstemciler için iki özelliği kullanıma sunacaksınız: `LightColor` ve `DarkColor`.</span><span class="sxs-lookup"><span data-stu-id="20926-239">You'll expose two properties to clients: `LightColor` and `DarkColor`.</span></span> <span data-ttu-id="20926-240"><xref:System.ComponentModel.CategoryAttribute.Category%2A> Ve<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> öznitelikleri bu özelliklere uygulanır, bu nedenle Özellikler "kayan yazı" adlı Özellikler penceresi özel bir bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="20926-240">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to these properties, so the properties appear in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. <span data-ttu-id="20926-241"><xref:System.ComponentModel.BackgroundWorker> Bileşen ve Olaylar<xref:System.ComponentModel.BackgroundWorker.ProgressChanged> için işleyicileri uygulayın. <xref:System.ComponentModel.BackgroundWorker.DoWork></span><span class="sxs-lookup"><span data-stu-id="20926-241">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="20926-242">Olay işleyicisi, tarafından `UpdatePeriod` <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>belirtilenmilisaniye sayısı için uyku moduna geçer. <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> <xref:System.ComponentModel.BackgroundWorker.DoWork></span><span class="sxs-lookup"><span data-stu-id="20926-242">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="20926-243"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Olay işleyicisi, yanıp sönmeye yönelik görünümü sağlamak için açık ve koyu durumu arasındaki metni değiştirir.</span><span class="sxs-lookup"><span data-stu-id="20926-243">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler toggles the text between its light and dark state to give the appearance of flashing.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. <span data-ttu-id="20926-244">Animasyonu etkinleştirmek için yöntemini geçersiz kılın. <xref:System.Windows.Forms.Control.OnPaint%2A></span><span class="sxs-lookup"><span data-stu-id="20926-244">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method to enable the animation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. <span data-ttu-id="20926-245">Çözümü derlemek için **F6** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="20926-245">Press **F6** to build the solution.</span></span>

## <a name="create-the-marqueeborder-child-control"></a><span data-ttu-id="20926-246">MarqueeBorder alt denetimini oluşturma</span><span class="sxs-lookup"><span data-stu-id="20926-246">Create the MarqueeBorder Child Control</span></span>

<span data-ttu-id="20926-247">Denetim, `MarqueeText` denetimden biraz daha karmaşıktır. `MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="20926-247">The `MarqueeBorder` control is slightly more sophisticated than the `MarqueeText` control.</span></span> <span data-ttu-id="20926-248">Daha fazla özelliğe sahiptir ve <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemdeki animasyon daha fazla yer alır.</span><span class="sxs-lookup"><span data-stu-id="20926-248">It has more properties and the animation in the <xref:System.Windows.Forms.Control.OnPaint%2A> method is more involved.</span></span> <span data-ttu-id="20926-249">Prensibi, `MarqueeText` denetime oldukça benzer.</span><span class="sxs-lookup"><span data-stu-id="20926-249">In principle, it is quite similar to the `MarqueeText` control.</span></span>

<span data-ttu-id="20926-250">Denetimde alt denetimler olabileceğinden, <xref:System.Windows.Forms.Control.Layout> olayların farkında olması gerekir. `MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="20926-250">Because the `MarqueeBorder` control can have child controls, it needs to be aware of <xref:System.Windows.Forms.Control.Layout> events.</span></span>

### <a name="to-create-the-marqueeborder-control"></a><span data-ttu-id="20926-251">MarqueeBorder denetimini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="20926-251">To create the MarqueeBorder control</span></span>

1. <span data-ttu-id="20926-252">`MarqueeControlLibrary` Projeye yeni bir **özel denetim** öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20926-252">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="20926-253">Yeni kaynak dosyasına "MarqueeBorder" temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="20926-253">Give the new source file a base name of "MarqueeBorder."</span></span>

2. <span data-ttu-id="20926-254">**Araç kutusundan** bir <xref:System.ComponentModel.BackgroundWorker> bileşeni denetimüzerinesürükleyin.`MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="20926-254">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeBorder` control.</span></span> <span data-ttu-id="20926-255">Bu bileşen `MarqueeBorder` denetimin kendisini zaman uyumsuz olarak güncelleştirmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="20926-255">This component will allow the `MarqueeBorder` control to update itself asynchronously.</span></span>

3. <span data-ttu-id="20926-256">**Özellikler** penceresinde <xref:System.ComponentModel.BackgroundWorker> , bileşen `WorkerReportsProgress` ve <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliklerini **doğru**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="20926-256">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to **true**.</span></span> <span data-ttu-id="20926-257">Bu ayarlar, <xref:System.ComponentModel.BackgroundWorker> bileşenin düzenli olarak <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayı kullanmasına ve zaman uyumsuz güncelleştirmeleri iptal edebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="20926-257">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span> <span data-ttu-id="20926-258">Daha fazla bilgi için bkz. [BackgroundWorker Component](backgroundworker-component.md).</span><span class="sxs-lookup"><span data-stu-id="20926-258">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

4. <span data-ttu-id="20926-259">**Özellikler** penceresinde, **Olaylar** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="20926-259">In the **Properties** window, select the **Events** button.</span></span> <span data-ttu-id="20926-260"><xref:System.ComponentModel.BackgroundWorker.DoWork> Ve<xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayları için işleyiciler iliştirin.</span><span class="sxs-lookup"><span data-stu-id="20926-260">Attach handlers for the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

5. <span data-ttu-id="20926-261">Kaynak dosyasını kod düzenleyicisinde açın. `MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="20926-261">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span> <span data-ttu-id="20926-262">Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="20926-262">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. <span data-ttu-id="20926-263">' Dan `MarqueeBorder` <xref:System.Windows.Forms.Panel> devralması için bildirimini değiştirin ve `IMarqueeWidget` arabirimini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="20926-263">Change the declaration of `MarqueeBorder` to inherit from <xref:System.Windows.Forms.Panel> and to implement the `IMarqueeWidget` interface.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. <span data-ttu-id="20926-264">`MarqueeBorder` Denetimin durumunu yönetmek için iki numaralandırma bildirin: `MarqueeSpinDirection`, ışıklarının etrafında "döndürme" ve `MarqueeLightShape`ışıklarının şeklini (kare veya dairesel) belirleyen yönü belirleyen yönü belirler.</span><span class="sxs-lookup"><span data-stu-id="20926-264">Declare two enumerations for managing the `MarqueeBorder` control's state: `MarqueeSpinDirection`, which determines the direction in which the lights "spin" around the border, and `MarqueeLightShape`, which determines the shape of the lights (square or circular).</span></span> <span data-ttu-id="20926-265">Bu bildirimleri `MarqueeBorder` Sınıf bildiriminden önce yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="20926-265">Place these declarations before the `MarqueeBorder` class declaration.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. <span data-ttu-id="20926-266">Gösterilen özelliklere karşılık gelen örnek değişkenlerini bildirin ve bunları oluşturucuda başlatın.</span><span class="sxs-lookup"><span data-stu-id="20926-266">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. <span data-ttu-id="20926-267">`IMarqueeWidget` arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="20926-267">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="20926-268">Ve `StartMarquee` yöntemleri,<xref:System.ComponentModel.BackgroundWorker> animasyonu başlatmak ve durdurmak için <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> bileşenin veyöntemleriniçağırır.<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> `StopMarquee`</span><span class="sxs-lookup"><span data-stu-id="20926-268">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="20926-269">Denetim alt denetimler içerebildiğinden `StartMarquee` , yöntemi, uygulamalarındaki `IMarqueeWidget`tüm alt denetimleri ve çağrıları `StartMarquee` numaralandırır. `MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="20926-269">Because the `MarqueeBorder` control can contain child controls, the `StartMarquee` method enumerates all child controls and calls `StartMarquee` on those that implement `IMarqueeWidget`.</span></span> <span data-ttu-id="20926-270">`StopMarquee` Yönteminde benzer bir uygulama vardır.</span><span class="sxs-lookup"><span data-stu-id="20926-270">The `StopMarquee` method has a similar implementation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. <span data-ttu-id="20926-271">Özellik erişimcileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="20926-271">Implement the property accessors.</span></span> <span data-ttu-id="20926-272">`MarqueeBorder` Denetimde, görünümünü denetlemek için çeşitli özellikler vardır.</span><span class="sxs-lookup"><span data-stu-id="20926-272">The `MarqueeBorder` control has several properties for controlling its appearance.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. <span data-ttu-id="20926-273"><xref:System.ComponentModel.BackgroundWorker> Bileşen ve Olaylar<xref:System.ComponentModel.BackgroundWorker.ProgressChanged> için işleyicileri uygulayın. <xref:System.ComponentModel.BackgroundWorker.DoWork></span><span class="sxs-lookup"><span data-stu-id="20926-273">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="20926-274">Olay işleyicisi, tarafından `UpdatePeriod` <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>belirtilenmilisaniye sayısı için uyku moduna geçer. <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> <xref:System.ComponentModel.BackgroundWorker.DoWork></span><span class="sxs-lookup"><span data-stu-id="20926-274">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="20926-275">Olay işleyicisi, diğer ışıklarının açık/koyu durumunun belirlendiği "temel" Işığın konumunu artırır ve denetimin kendisini yeniden çizmeyi sağlamak için <xref:System.Windows.Forms.Control.Refresh%2A> yöntemini çağırır. <xref:System.ComponentModel.BackgroundWorker.ProgressChanged></span><span class="sxs-lookup"><span data-stu-id="20926-275">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler increments the position of the "base" light, from which the light/dark state of the other lights is determined, and calls the <xref:System.Windows.Forms.Control.Refresh%2A> method to cause the control to repaint itself.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. <span data-ttu-id="20926-276">Yardımcı yöntemleri ve `DrawLight`' yi `IsLit` uygulayın.</span><span class="sxs-lookup"><span data-stu-id="20926-276">Implement the helper methods, `IsLit` and `DrawLight`.</span></span>

    <span data-ttu-id="20926-277">Yöntemi `IsLit` , belirli bir konumdaki ışığın rengini belirler.</span><span class="sxs-lookup"><span data-stu-id="20926-277">The `IsLit` method determines the color of a light at a given position.</span></span> <span data-ttu-id="20926-278">"Açık" olan ışıklar `LightColor` özelliği tarafından verilen renkte çizilir ve "koyu" olan ışıklar `DarkColor` özelliği tarafından verilen renkte çizilir.</span><span class="sxs-lookup"><span data-stu-id="20926-278">Lights that are "lit" are drawn in the color given by the `LightColor` property, and those that are "dark" are drawn in the color given by the `DarkColor` property.</span></span>

    <span data-ttu-id="20926-279">`DrawLight` Yöntemi uygun renk, şekil ve konumu kullanarak bir ışık çizer.</span><span class="sxs-lookup"><span data-stu-id="20926-279">The `DrawLight` method draws a light using the appropriate color, shape, and position.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. <span data-ttu-id="20926-280"><xref:System.Windows.Forms.Control.OnLayout%2A> Ve<xref:System.Windows.Forms.Control.OnPaint%2A> yöntemlerini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="20926-280">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> and <xref:System.Windows.Forms.Control.OnPaint%2A> methods.</span></span>

    <span data-ttu-id="20926-281">Yöntemi, `MarqueeBorder` denetimin kenarları üzerinde ışıkları çizer. <xref:System.Windows.Forms.Control.OnPaint%2A></span><span class="sxs-lookup"><span data-stu-id="20926-281">The <xref:System.Windows.Forms.Control.OnPaint%2A> method draws the lights along the edges of the `MarqueeBorder` control.</span></span>

    <span data-ttu-id="20926-282"><xref:System.Windows.Forms.Control.OnPaint%2A> Yöntem `MarqueeBorder` denetimin boyutlarına bağlı olduğundan, düzen her değiştiğinde onu çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="20926-282">Because the <xref:System.Windows.Forms.Control.OnPaint%2A> method depends on the dimensions of the `MarqueeBorder` control, you need to call it whenever the layout changes.</span></span> <span data-ttu-id="20926-283">Bunu başarmak için, öğesini <xref:System.Windows.Forms.Control.OnLayout%2A> geçersiz kılın <xref:System.Windows.Forms.Control.Refresh%2A>ve çağırın.</span><span class="sxs-lookup"><span data-stu-id="20926-283">To achieve this, override <xref:System.Windows.Forms.Control.OnLayout%2A> and call <xref:System.Windows.Forms.Control.Refresh%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="20926-284">Gölge ve filtre özelliklerine özel tasarımcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="20926-284">Create a Custom Designer to Shadow and Filter Properties</span></span>

<span data-ttu-id="20926-285">`MarqueeControlRootDesigner` Sınıfı, kök Tasarımcı için uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="20926-285">The `MarqueeControlRootDesigner` class provides the implementation for the root designer.</span></span> <span data-ttu-id="20926-286">Üzerinde `MarqueeControl`çalışan bu tasarımcıya ek olarak, özellikle `MarqueeBorder` denetimle ilişkili özel bir tasarımcı gerekir.</span><span class="sxs-lookup"><span data-stu-id="20926-286">In addition to this designer, which operates on the `MarqueeControl`, you'll need a custom designer that is specifically associated with the `MarqueeBorder` control.</span></span> <span data-ttu-id="20926-287">Bu tasarımcı, özel kök tasarlayıcı bağlamında uygun olan özel davranışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="20926-287">This designer provides custom behavior that is appropriate in the context of the custom root designer.</span></span>

<span data-ttu-id="20926-288">Özellikle, "gölgelendir" ve `MarqueeBorder` denetimdeki belirli özellikleri filtreleyerek tasarım ortamıyla etkileşimini değiştirmiş olacak.`MarqueeBorderDesigner`</span><span class="sxs-lookup"><span data-stu-id="20926-288">Specifically, the `MarqueeBorderDesigner` will "shadow" and filter certain properties on the `MarqueeBorder` control, changing their interaction with the design environment.</span></span>

<span data-ttu-id="20926-289">Bir bileşenin Özellik erişimcisine yönelik kesintiye uğratan çağrı, "gölgeleme" olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="20926-289">Intercepting calls to a component's property accessor is known as "shadowing."</span></span> <span data-ttu-id="20926-290">Bir tasarımcının Kullanıcı tarafından ayarlanan değeri izlemesine ve isteğe bağlı olarak bu değeri tasarlanmakta olan bileşene iletmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="20926-290">It allows a designer to track the value set by the user and optionally pass that value to the component being designed.</span></span>

<span data-ttu-id="20926-291">Bu örnekte <xref:System.Windows.Forms.Control.Visible%2A> , ve <xref:System.Windows.Forms.Control.Enabled%2A> özellikleri, `MarqueeBorderDesigner`kullanıcının tasarım zamanı sırasında `MarqueeBorder` denetimi görünmez veya devre dışı yapmasını önleyen tarafından gölgelenir.</span><span class="sxs-lookup"><span data-stu-id="20926-291">For this example, the <xref:System.Windows.Forms.Control.Visible%2A> and <xref:System.Windows.Forms.Control.Enabled%2A> properties will be shadowed by the `MarqueeBorderDesigner`, which prevents the user from making the `MarqueeBorder` control invisible or disabled during design time.</span></span>

<span data-ttu-id="20926-292">Tasarımcılar Ayrıca özellikler ekleyebilir ve kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="20926-292">Designers can also add and remove properties.</span></span> <span data-ttu-id="20926-293">Bu örnekte, <xref:System.Windows.Forms.Control.Padding%2A> özellik tasarım zamanında kaldırılacak, `MarqueeBorder` çünkü denetim program aracılığıyla, `LightSize` özelliği tarafından belirtilen ışıklarının boyutuna göre doldurma ayarlıyor.</span><span class="sxs-lookup"><span data-stu-id="20926-293">For this example, the <xref:System.Windows.Forms.Control.Padding%2A> property will be removed at design time, because the `MarqueeBorder` control programmatically sets the padding based on the size of the lights specified by the `LightSize` property.</span></span>

<span data-ttu-id="20926-294">`MarqueeBorderDesigner` İçin<xref:System.ComponentModel.Design.ComponentDesigner>temel sınıf, tasarım zamanında bir denetim tarafından açığa çıkarılan öznitelikleri, özellikleri ve olayları değiştirebilen yöntemler içerir:</span><span class="sxs-lookup"><span data-stu-id="20926-294">The base class for `MarqueeBorderDesigner` is <xref:System.ComponentModel.Design.ComponentDesigner>, which has methods that can change the attributes, properties, and events exposed by a control at design time:</span></span>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

<span data-ttu-id="20926-295">Bu yöntemleri kullanarak bir bileşenin genel arabirimini değiştirirken bu kuralları izleyin:</span><span class="sxs-lookup"><span data-stu-id="20926-295">When changing the public interface of a component using these methods, follow these rules:</span></span>

- <span data-ttu-id="20926-296">Yalnızca `PreFilter` metotlarda öğe ekleme veya kaldırma</span><span class="sxs-lookup"><span data-stu-id="20926-296">Add or remove items in the `PreFilter` methods only</span></span>

- <span data-ttu-id="20926-297">Yalnızca `PostFilter` metotlarda bulunan öğeleri değiştir</span><span class="sxs-lookup"><span data-stu-id="20926-297">Modify existing items in the `PostFilter` methods only</span></span>

- <span data-ttu-id="20926-298">Her zaman ilk olarak `PreFilter` metotlarda temel uygulamayı çağırın</span><span class="sxs-lookup"><span data-stu-id="20926-298">Always call the base implementation first in the `PreFilter` methods</span></span>

- <span data-ttu-id="20926-299">Her zaman, `PostFilter` metotlarda en son temel uygulamayı çağırın</span><span class="sxs-lookup"><span data-stu-id="20926-299">Always call the base implementation last in the `PostFilter` methods</span></span>

<span data-ttu-id="20926-300">Bu kurallara uymak, tasarım zamanı ortamındaki tüm tasarımcılarının tasarlanmakta olan tüm bileşenlerin tutarlı bir görünümüne sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="20926-300">Adhering to these rules ensures that all designers in the design-time environment have a consistent view of all components being designed.</span></span>

<span data-ttu-id="20926-301"><xref:System.ComponentModel.Design.ComponentDesigner> Sınıfı, gölgelendirilmiş özelliklerin değerlerini yönetmek için bir sözlük sağlar, bu da size belirli örnek değişkenleri oluşturma gereksinimini sizi maliyetinden kurtarır.</span><span class="sxs-lookup"><span data-stu-id="20926-301">The <xref:System.ComponentModel.Design.ComponentDesigner> class provides a dictionary for managing the values of shadowed properties, which relieves you of the need to create specific instance variables.</span></span>

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="20926-302">Gölge ve filtre özelliklerine özel bir tasarımcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="20926-302">To create a custom designer to shadow and filter properties</span></span>

1. <span data-ttu-id="20926-303">**Tasarım** klasörüne sağ tıklayın ve yeni bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20926-303">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="20926-304">Kaynak dosyaya **MarqueeBorderDesigner**temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="20926-304">Give the source file a base name of **MarqueeBorderDesigner**.</span></span>

2. <span data-ttu-id="20926-305">MarqueeBorderDesigner kaynak dosyasını **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="20926-305">Open the MarqueeBorderDesigner source file in the **Code Editor**.</span></span> <span data-ttu-id="20926-306">Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="20926-306">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. <span data-ttu-id="20926-307">Bildirimini `MarqueeBorderDesigner` öğesinden<xref:System.Windows.Forms.Design.ParentControlDesigner>devralacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="20926-307">Change the declaration of `MarqueeBorderDesigner` to inherit from <xref:System.Windows.Forms.Design.ParentControlDesigner>.</span></span>

    <span data-ttu-id="20926-308">Denetim alt denetimler içerebildiğinden, üst-alt etkileşimini <xref:System.Windows.Forms.Design.ParentControlDesigner>işleyen öğesinden devralır.`MarqueeBorderDesigner` `MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="20926-308">Because the `MarqueeBorder` control can contain child controls, `MarqueeBorderDesigner` inherits from <xref:System.Windows.Forms.Design.ParentControlDesigner>, which handles the parent-child interaction.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. <span data-ttu-id="20926-309">Temel uygulamasını <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="20926-309">Override the base implementation of <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. <span data-ttu-id="20926-310"><xref:System.Windows.Forms.Control.Enabled%2A> Ve<xref:System.Windows.Forms.Control.Visible%2A> özelliklerini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="20926-310">Implement the <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A> properties.</span></span> <span data-ttu-id="20926-311">Bu uygulamalar, denetimin özelliklerini gölgelendir.</span><span class="sxs-lookup"><span data-stu-id="20926-311">These implementations shadow the control's properties.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handle-component-changes"></a><span data-ttu-id="20926-312">Bileşen değişikliklerini işle</span><span class="sxs-lookup"><span data-stu-id="20926-312">Handle Component Changes</span></span>

<span data-ttu-id="20926-313">Sınıfı, örneklerinizin `MarqueeControl` özel tasarım zamanı deneyimini sağlar. `MarqueeControlRootDesigner`</span><span class="sxs-lookup"><span data-stu-id="20926-313">The `MarqueeControlRootDesigner` class provides the custom design-time experience for your `MarqueeControl` instances.</span></span> <span data-ttu-id="20926-314">Tasarım zamanı işlevlerinin çoğu <xref:System.Windows.Forms.Design.DocumentDesigner> sınıfından devralınır.</span><span class="sxs-lookup"><span data-stu-id="20926-314">Most of the design-time functionality is inherited from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="20926-315">Kodunuz iki özel özelleştirme uygular: bileşen değişikliklerini işleme ve tasarımcı fiilleri ekleme.</span><span class="sxs-lookup"><span data-stu-id="20926-315">Your code will implement two specific customizations: handling component changes, and adding designer verbs.</span></span>

<span data-ttu-id="20926-316">Kullanıcılar `MarqueeControl` örneklerini tasarlarsa, kök tasarlayıcı, `MarqueeControl` ve alt denetimlerinde yapılan değişiklikleri izler.</span><span class="sxs-lookup"><span data-stu-id="20926-316">As users design their `MarqueeControl` instances, your root designer will track changes to the `MarqueeControl` and its child controls.</span></span> <span data-ttu-id="20926-317">Tasarım zamanı ortamı, bileşen durumundaki değişiklikleri izlemek için uygun <xref:System.ComponentModel.Design.IComponentChangeService>bir hizmet sunar.</span><span class="sxs-lookup"><span data-stu-id="20926-317">The design-time environment offers a convenient service, <xref:System.ComponentModel.Design.IComponentChangeService>, for tracking changes to component state.</span></span>

<span data-ttu-id="20926-318">Ortamı <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> yöntemiyle sorgulayarak bu hizmete bir başvuru elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="20926-318">You acquire a reference to this service by querying the environment with the <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> method.</span></span> <span data-ttu-id="20926-319">Sorgu başarılı olursa, tasarımcı <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> olay için bir işleyici iliştirebilir ve tasarım zamanında tutarlı bir durumu korumak için gereken görevleri gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="20926-319">If the query is successful, your designer can attach a handler for the <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> event and perform whatever tasks are required to maintain a consistent state at design time.</span></span>

<span data-ttu-id="20926-320">`MarqueeControlRootDesigner` Sınıfı söz konusu olduğunda, <xref:System.Windows.Forms.Control.Refresh%2A> yöntemi tarafından içerilen `MarqueeControl`her `IMarqueeWidget` bir nesne üzerinde çağıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="20926-320">In the case of the `MarqueeControlRootDesigner` class, you will call the <xref:System.Windows.Forms.Control.Refresh%2A> method on each `IMarqueeWidget` object contained by the `MarqueeControl`.</span></span> <span data-ttu-id="20926-321">Bu, `IMarqueeWidget` <xref:System.Windows.Forms.Control.Size%2A> üst öğesi gibi özellikler değiştirildiğinde nesnenin kendisini uygun şekilde yeniden görüntülemesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="20926-321">This will cause the `IMarqueeWidget` object to repaint itself appropriately when properties like its parent's <xref:System.Windows.Forms.Control.Size%2A> are changed.</span></span>

### <a name="to-handle-component-changes"></a><span data-ttu-id="20926-322">Bileşen değişikliklerini işlemek için</span><span class="sxs-lookup"><span data-stu-id="20926-322">To handle component changes</span></span>

1. <span data-ttu-id="20926-323">Kaynak dosyasını **kod düzenleyicisinde** açın ve <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> metodunu geçersiz kılın. `MarqueeControlRootDesigner`</span><span class="sxs-lookup"><span data-stu-id="20926-323">Open the `MarqueeControlRootDesigner` source file in the **Code Editor** and override the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span> <span data-ttu-id="20926-324">İçin temel uygulamasını <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> çağırın ve için sorgulayın. <xref:System.ComponentModel.Design.IComponentChangeService></span><span class="sxs-lookup"><span data-stu-id="20926-324">Call the base implementation of <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> and query for the <xref:System.ComponentModel.Design.IComponentChangeService>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. <span data-ttu-id="20926-325"><xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> Olay işleyicisini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="20926-325">Implement the <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> event handler.</span></span> <span data-ttu-id="20926-326">Gönderen bileşenin türünü test edin ve bir `IMarqueeWidget`ise <xref:System.Windows.Forms.Control.Refresh%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="20926-326">Test the sending component's type, and if it is an `IMarqueeWidget`, call its <xref:System.Windows.Forms.Control.Refresh%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="add-designer-verbs-to-your-custom-designer"></a><span data-ttu-id="20926-327">Özel tasarımcıya tasarımcı fiilleri ekleme</span><span class="sxs-lookup"><span data-stu-id="20926-327">Add Designer Verbs to your Custom Designer</span></span>

<span data-ttu-id="20926-328">Tasarımcı fiili, olay işleyicisine bağlı bir menü komutu olur.</span><span class="sxs-lookup"><span data-stu-id="20926-328">A designer verb is a menu command linked to an event handler.</span></span> <span data-ttu-id="20926-329">Tasarımcı fiilleri, tasarım zamanında bir bileşenin kısayol menüsüne eklenir.</span><span class="sxs-lookup"><span data-stu-id="20926-329">Designer verbs are added to a component's shortcut menu at design time.</span></span> <span data-ttu-id="20926-330">Daha fazla bilgi için bkz. <xref:System.ComponentModel.Design.DesignerVerb>.</span><span class="sxs-lookup"><span data-stu-id="20926-330">For more information, see <xref:System.ComponentModel.Design.DesignerVerb>.</span></span>

<span data-ttu-id="20926-331">Tasarımcılara iki tasarımcı fiilleri ekleyeceksiniz: **Testi Çalıştır** ve **testi durdur**.</span><span class="sxs-lookup"><span data-stu-id="20926-331">You will add two designer verbs to your designers: **Run Test** and **Stop Test**.</span></span> <span data-ttu-id="20926-332">Bu fiiller, `MarqueeControl` tasarım zamanının çalışma zamanı davranışını görüntülemenize olanak sağlayacak.</span><span class="sxs-lookup"><span data-stu-id="20926-332">These verbs will allow you to view the run-time behavior of the `MarqueeControl` at design time.</span></span> <span data-ttu-id="20926-333">Bu fiiller öğesine `MarqueeControlRootDesigner`eklenecektir.</span><span class="sxs-lookup"><span data-stu-id="20926-333">These verbs will be added to `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="20926-334">**Çalıştırma testi** çağrıldığında, fiil olay işleyicisi üzerinde `StartMarquee` `MarqueeControl`yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="20926-334">When **Run Test** is invoked, the verb event handler will call the `StartMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="20926-335">**Testi durdur** çağrıldığında, fiil olay işleyicisi üzerinde `StopMarquee` `MarqueeControl`yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="20926-335">When **Stop Test** is invoked, the verb event handler will call the `StopMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="20926-336">`StartMarquee` Ve `IMarqueeWidget` `IMarqueeWidget` yöntemlerinin uygulaması, uygulayan içerilen denetimler üzerinde bu yöntemleri çağırır, bu nedenle içerilen denetimlerin de teste katılması gerekir. `StopMarquee`</span><span class="sxs-lookup"><span data-stu-id="20926-336">The implementation of the `StartMarquee` and `StopMarquee` methods call these methods on contained controls that implement `IMarqueeWidget`, so any contained `IMarqueeWidget` controls will also participate in the test.</span></span>

### <a name="to-add-designer-verbs-to-your-custom-designers"></a><span data-ttu-id="20926-337">Özel tasarımcılara tasarımcı fiilleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="20926-337">To add designer verbs to your custom designers</span></span>

1. <span data-ttu-id="20926-338">Sınıfında, `OnVerbRunTest` ve`OnVerbStopTest`adlı olay işleyicileri ekleyin. `MarqueeControlRootDesigner`</span><span class="sxs-lookup"><span data-stu-id="20926-338">In the `MarqueeControlRootDesigner` class, add event handlers named `OnVerbRunTest` and `OnVerbStopTest`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. <span data-ttu-id="20926-339">Bu olay işleyicilerini ilgili tasarımcı fiillerine bağlayın.</span><span class="sxs-lookup"><span data-stu-id="20926-339">Connect these event handlers to their corresponding designer verbs.</span></span> <span data-ttu-id="20926-340">`MarqueeControlRootDesigner`kendi temel <xref:System.ComponentModel.Design.DesignerVerbCollection> sınıfından bir devralır.</span><span class="sxs-lookup"><span data-stu-id="20926-340">`MarqueeControlRootDesigner` inherits a <xref:System.ComponentModel.Design.DesignerVerbCollection> from its base class.</span></span> <span data-ttu-id="20926-341">İki yeni <xref:System.ComponentModel.Design.DesignerVerb> nesne oluşturacak ve bu koleksiyona, <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> yöntemi içinde ekleyecek.</span><span class="sxs-lookup"><span data-stu-id="20926-341">You will create two new <xref:System.ComponentModel.Design.DesignerVerb> objects and add them to this collection in the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="create-a-custom-uitypeeditor"></a><span data-ttu-id="20926-342">Özel bir Uııtypeınfo Düzenleyicisi oluşturun</span><span class="sxs-lookup"><span data-stu-id="20926-342">Create a Custom UITypeEditor</span></span>

<span data-ttu-id="20926-343">Kullanıcılar için özel bir tasarım zamanı deneyimi oluşturduğunuzda, genellikle Özellikler penceresi özel bir etkileşim oluşturmak tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="20926-343">When you create a custom design-time experience for users, it is often desirable to create a custom interaction with the Properties window.</span></span> <span data-ttu-id="20926-344">Bunu oluşturarak <xref:System.Drawing.Design.UITypeEditor>yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20926-344">You can accomplish this by creating a <xref:System.Drawing.Design.UITypeEditor>.</span></span>

<span data-ttu-id="20926-345">`MarqueeBorder` Denetim Özellikler penceresi çeşitli özellikleri kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="20926-345">The `MarqueeBorder` control exposes several properties in the Properties window.</span></span> <span data-ttu-id="20926-346">Bu özelliklerden `MarqueeSpinDirection` ikisi ve `MarqueeLightShape` numaralandırmalar tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="20926-346">Two of these properties, `MarqueeSpinDirection` and `MarqueeLightShape` are represented by enumerations.</span></span> <span data-ttu-id="20926-347">Kullanıcı arabirimi türü düzenleyicisinin kullanımını göstermek için, `MarqueeLightShape` özelliği ilişkili <xref:System.Drawing.Design.UITypeEditor> bir sınıfa sahip olur.</span><span class="sxs-lookup"><span data-stu-id="20926-347">To illustrate the use of a UI type editor, the `MarqueeLightShape` property will have an associated <xref:System.Drawing.Design.UITypeEditor> class.</span></span>

### <a name="to-create-a-custom-ui-type-editor"></a><span data-ttu-id="20926-348">Özel bir kullanıcı arabirimi tür Düzenleyicisi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="20926-348">To create a custom UI type editor</span></span>

1. <span data-ttu-id="20926-349">Kaynak dosyasını kod düzenleyicisinde açın. `MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="20926-349">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span>

2. <span data-ttu-id="20926-350">`MarqueeBorder` Sınıfının tanımında, öğesinden `LightShapeEditor` <xref:System.Drawing.Design.UITypeEditor>türetilen adlı bir sınıf bildirin.</span><span class="sxs-lookup"><span data-stu-id="20926-350">In the definition of the `MarqueeBorder` class, declare a class called `LightShapeEditor` that derives from <xref:System.Drawing.Design.UITypeEditor>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. <span data-ttu-id="20926-351"><xref:System.Windows.Forms.Design.IWindowsFormsEditorService> Adlı`editorService`bir örnek değişkeni bildirin.</span><span class="sxs-lookup"><span data-stu-id="20926-351">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. <span data-ttu-id="20926-352">Geçersiz kılma <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="20926-352">Override the <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> method.</span></span> <span data-ttu-id="20926-353">Bu uygulama, <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>tasarım ortamına nasıl `LightShapeEditor`görüntüleneceğini bildiren, öğesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="20926-353">This implementation returns <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, which tells the design environment how to display the `LightShapeEditor`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. <span data-ttu-id="20926-354">Geçersiz kılma <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="20926-354">Override the <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> method.</span></span> <span data-ttu-id="20926-355">Bu uygulama, bir <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> nesnenin tasarım ortamını sorgular.</span><span class="sxs-lookup"><span data-stu-id="20926-355">This implementation queries the design environment for an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> object.</span></span> <span data-ttu-id="20926-356">Başarılı olursa, bir `LightShapeSelectionControl`oluşturur.</span><span class="sxs-lookup"><span data-stu-id="20926-356">If successful, it creates a `LightShapeSelectionControl`.</span></span> <span data-ttu-id="20926-357">Yöntemi başlatmak için çağrılır. `LightShapeEditor` <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A></span><span class="sxs-lookup"><span data-stu-id="20926-357">The <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> method is invoked to start the `LightShapeEditor`.</span></span> <span data-ttu-id="20926-358">Bu çağrıdan gelen dönüş değeri tasarım ortamına döndürülür.</span><span class="sxs-lookup"><span data-stu-id="20926-358">The return value from this invocation is returned to the design environment.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="create-a-view-control-for-your-custom-uitypeeditor"></a><span data-ttu-id="20926-359">Özel Uııtypeınfo Düzenleyicisi için bir görünüm denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="20926-359">Create a View Control for your Custom UITypeEditor</span></span>

<span data-ttu-id="20926-360">Özelliği iki tür açık şekli destekler: `Square` ve `Circle`. `MarqueeLightShape`</span><span class="sxs-lookup"><span data-stu-id="20926-360">The `MarqueeLightShape` property supports two types of light shapes: `Square` and `Circle`.</span></span> <span data-ttu-id="20926-361">Yalnızca bu değerleri Özellikler penceresi grafik olarak görüntülemek için kullanılan özel bir denetim oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="20926-361">You will create a custom control used solely for the purpose of graphically displaying these values in the Properties window.</span></span> <span data-ttu-id="20926-362">Bu özel denetim, Özellikler penceresi etkileşimde bulunmak için <xref:System.Drawing.Design.UITypeEditor> sizin tarafınızdan kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="20926-362">This custom control will be used by your <xref:System.Drawing.Design.UITypeEditor> to interact with the Properties window.</span></span>

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a><span data-ttu-id="20926-363">Özel UI türü düzenleyiciniz için bir görünüm denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="20926-363">To create a view control for your custom UI type editor</span></span>

1. <span data-ttu-id="20926-364">`MarqueeControlLibrary` Projeye yeni <xref:System.Windows.Forms.UserControl> bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20926-364">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="20926-365">Yeni kaynak dosyasına, **Açık Shapeselectioncontrol**temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="20926-365">Give the new source file a base name of **LightShapeSelectionControl**.</span></span>

2. <span data-ttu-id="20926-366">Araç kutusundan <xref:System.Windows.Forms.Panel> iki denetimi üzerine sürükleyin. `LightShapeSelectionControl`</span><span class="sxs-lookup"><span data-stu-id="20926-366">Drag two <xref:System.Windows.Forms.Panel> controls from the **Toolbox** onto the `LightShapeSelectionControl`.</span></span> <span data-ttu-id="20926-367">Onları `squarePanel` ve`circlePanel`olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="20926-367">Name them `squarePanel` and `circlePanel`.</span></span> <span data-ttu-id="20926-368">Yan yana düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="20926-368">Arrange them side by side.</span></span> <span data-ttu-id="20926-369">Her iki <xref:System.Windows.Forms.Control.Size%2A> <xref:System.Windows.Forms.Panel> denetimin özelliğini **(60, 60)** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="20926-369">Set the <xref:System.Windows.Forms.Control.Size%2A> property of both <xref:System.Windows.Forms.Panel> controls to **(60, 60)**.</span></span> <span data-ttu-id="20926-370">Denetimin özelliğini **(8, 10)** olarak ayarlayın. <xref:System.Windows.Forms.Control.Location%2A> `squarePanel`</span><span class="sxs-lookup"><span data-stu-id="20926-370">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `squarePanel` control to **(8, 10)**.</span></span> <span data-ttu-id="20926-371">Denetimin özelliğini **(80, 10)** olarak ayarlayın. <xref:System.Windows.Forms.Control.Location%2A> `circlePanel`</span><span class="sxs-lookup"><span data-stu-id="20926-371">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `circlePanel` control to **(80, 10)**.</span></span> <span data-ttu-id="20926-372">Son olarak, `LightShapeSelectionControl` öğesinin <xref:System.Windows.Forms.Control.Size%2A> özelliğini olarak ayarlayın **(150, 80)** .</span><span class="sxs-lookup"><span data-stu-id="20926-372">Finally, set the <xref:System.Windows.Forms.Control.Size%2A> property of the `LightShapeSelectionControl` to **(150, 80)**.</span></span>

3. <span data-ttu-id="20926-373">Kaynak dosyasını kod düzenleyicisinde açın. `LightShapeSelectionControl`</span><span class="sxs-lookup"><span data-stu-id="20926-373">Open the `LightShapeSelectionControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="20926-374">Dosyanın en üstünde, <xref:System.Windows.Forms.Design?displayProperty=nameWithType> ad alanını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="20926-374">At the top of the file, import the <xref:System.Windows.Forms.Design?displayProperty=nameWithType> namespace:</span></span>

   ```vb
   Imports System.Windows.Forms.Design
   ```

   ```csharp
   using System.Windows.Forms.Design;
   ```

4. <span data-ttu-id="20926-375">Ve`squarePanel` <xref:System.Windows.Forms.Control.Click> denetimleriiçin`circlePanel` olay işleyicileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="20926-375">Implement <xref:System.Windows.Forms.Control.Click> event handlers for the `squarePanel` and `circlePanel` controls.</span></span> <span data-ttu-id="20926-376">Bu yöntemler, <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> özel <xref:System.Drawing.Design.UITypeEditor> Düzenle oturumunu sona erdirmek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="20926-376">These methods invoke <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> to end the custom <xref:System.Drawing.Design.UITypeEditor> editing session.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

5. <span data-ttu-id="20926-377"><xref:System.Windows.Forms.Design.IWindowsFormsEditorService> Adlı`editorService`bir örnek değişkeni bildirin.</span><span class="sxs-lookup"><span data-stu-id="20926-377">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

   ```vb
   Private editorService As IWindowsFormsEditorService
   ```

   ```csharp
   private IWindowsFormsEditorService editorService;
   ```

6. <span data-ttu-id="20926-378">`MarqueeLightShape` Adlı`lightShapeValue`bir örnek değişkeni bildirin.</span><span class="sxs-lookup"><span data-stu-id="20926-378">Declare a `MarqueeLightShape` instance variable called `lightShapeValue`.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

7. <span data-ttu-id="20926-379">`LightShapeSelectionControl` Oluşturucuda, <xref:System.Windows.Forms.Control.Click> olay işleyicilerini `squarePanel` ve `circlePanel` denetimlerin olaylarınaekleyin.<xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="20926-379">In the `LightShapeSelectionControl` constructor, attach the <xref:System.Windows.Forms.Control.Click> event handlers to the `squarePanel` and `circlePanel` controls' <xref:System.Windows.Forms.Control.Click> events.</span></span> <span data-ttu-id="20926-380">Ayrıca, tasarım ortamından `MarqueeLightShape` `lightShapeValue` alana değeri atayan bir Oluşturucu aşırı yüklemesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="20926-380">Also, define a constructor overload that assigns the `MarqueeLightShape` value from the design environment to the `lightShapeValue` field.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

8. <span data-ttu-id="20926-381"><xref:System.ComponentModel.Component.Dispose%2A> Yönteminde <xref:System.Windows.Forms.Control.Click> olay işleyicilerini ayırın.</span><span class="sxs-lookup"><span data-stu-id="20926-381">In the <xref:System.ComponentModel.Component.Dispose%2A> method, detach the <xref:System.Windows.Forms.Control.Click> event handlers.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

9. <span data-ttu-id="20926-382">**Çözüm Gezgini**, **tüm dosyaları göster** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="20926-382">In **Solution Explorer**, click the **Show All Files** button.</span></span> <span data-ttu-id="20926-383">LightShapeSelectionControl.Designer.cs veya LightShapeSelectionControl. Designer. vb dosyasını açın ve <xref:System.ComponentModel.Component.Dispose%2A> yönteminin varsayılan tanımını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="20926-383">Open the LightShapeSelectionControl.Designer.cs or LightShapeSelectionControl.Designer.vb file, and remove the default definition of the <xref:System.ComponentModel.Component.Dispose%2A> method.</span></span>

10. <span data-ttu-id="20926-384">`LightShape` Özelliğini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="20926-384">Implement the `LightShape` property.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

11. <span data-ttu-id="20926-385">Geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="20926-385">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="20926-386">Bu uygulama doldurulmuş bir kare ve daire çizecek.</span><span class="sxs-lookup"><span data-stu-id="20926-386">This implementation will draw a filled square and circle.</span></span> <span data-ttu-id="20926-387">Ayrıca, bir şekil ya da diğeri etrafında kenarlık çizerek seçili değeri vurgulayacaktır.</span><span class="sxs-lookup"><span data-stu-id="20926-387">It will also highlight the selected value by drawing a border around one shape or the other.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="test-your-custom-control-in-the-designer"></a><span data-ttu-id="20926-388">Tasarımcıda özel denetiminizi test etme</span><span class="sxs-lookup"><span data-stu-id="20926-388">Test your Custom Control in the Designer</span></span>

<span data-ttu-id="20926-389">Bu noktada, `MarqueeControlLibrary` projeyi derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20926-389">At this point, you can build the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="20926-390">`MarqueeControl` Sınıfından devralan bir denetim oluşturarak ve onu bir formda kullanarak uygulamanızı test edin.</span><span class="sxs-lookup"><span data-stu-id="20926-390">Test your implementation by creating a control that inherits from the `MarqueeControl` class and using it on a form.</span></span>

### <a name="to-create-a-custom-marqueecontrol-implementation"></a><span data-ttu-id="20926-391">Özel bir MarqueeControl uygulamasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="20926-391">To create a custom MarqueeControl implementation</span></span>

1. <span data-ttu-id="20926-392">Windows Form Tasarımcısı `DemoMarqueeControl` açın.</span><span class="sxs-lookup"><span data-stu-id="20926-392">Open `DemoMarqueeControl` in the Windows Forms Designer.</span></span> <span data-ttu-id="20926-393">Bu, `DemoMarqueeControl` türün bir örneğini oluşturur ve `MarqueeControlRootDesigner` türün bir örneğinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="20926-393">This creates an instance of the `DemoMarqueeControl` type and displays it in an instance of the `MarqueeControlRootDesigner` type.</span></span>

2. <span data-ttu-id="20926-394">**Araç kutusunda** **MarqueeControlLibrary Components** sekmesini açın. Seçim için kullanılabilir `MarqueeBorder` ve `MarqueeText` denetimleri görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="20926-394">In the **Toolbox**, open the **MarqueeControlLibrary Components** tab. You will see the `MarqueeBorder` and `MarqueeText` controls available for selection.</span></span>

3. <span data-ttu-id="20926-395">`MarqueeBorder` Denetimin`DemoMarqueeControl` bir örneğini tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="20926-395">Drag an instance of the `MarqueeBorder` control onto the `DemoMarqueeControl` design surface.</span></span> <span data-ttu-id="20926-396">Bu `MarqueeBorder` denetimi üst denetime yerleştir.</span><span class="sxs-lookup"><span data-stu-id="20926-396">Dock this `MarqueeBorder` control to the parent control.</span></span>

4. <span data-ttu-id="20926-397">`MarqueeText` Denetimin`DemoMarqueeControl` bir örneğini tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="20926-397">Drag an instance of the `MarqueeText` control onto the `DemoMarqueeControl` design surface.</span></span>

5. <span data-ttu-id="20926-398">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="20926-398">Build the solution.</span></span>

6. <span data-ttu-id="20926-399">Sağ tıklayıp kısayol menüsünden `DemoMarqueeControl` , animasyonu başlatmak için **Test Çalıştır** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="20926-399">Right-click the `DemoMarqueeControl` and from the shortcut menu select the **Run Test** option to start the animation.</span></span> <span data-ttu-id="20926-400">Animasyonu durdurmak için **Sınamayı Durdur** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="20926-400">Click **Stop Test** to stop the animation.</span></span>

7. <span data-ttu-id="20926-401">Tasarım görünümü 'da **Form1** ' i açın.</span><span class="sxs-lookup"><span data-stu-id="20926-401">Open **Form1** in Design view.</span></span>

8. <span data-ttu-id="20926-402">Forma iki <xref:System.Windows.Forms.Button> denetim koyun.</span><span class="sxs-lookup"><span data-stu-id="20926-402">Place two <xref:System.Windows.Forms.Button> controls on the form.</span></span> <span data-ttu-id="20926-403">Onları `startButton` ve <xref:System.Windows.Forms.Control.Text%2A>olarak adlandırın ve sırasıyla başlangıç ve durdurma özelliği değerlerini değiştirin. `stopButton`</span><span class="sxs-lookup"><span data-stu-id="20926-403">Name them `startButton` and `stopButton`, and change the <xref:System.Windows.Forms.Control.Text%2A> property values to **Start** and **Stop**, respectively.</span></span>

9. <span data-ttu-id="20926-404">Her <xref:System.Windows.Forms.Control.Click> iki denetim için de <xref:System.Windows.Forms.Button> olay işleyicileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="20926-404">Implement <xref:System.Windows.Forms.Control.Click> event handlers for both <xref:System.Windows.Forms.Button> controls.</span></span>

10. <span data-ttu-id="20926-405">**Araç kutusunda** **MarqueeControlTest Components** sekmesini açın. Seçim için `DemoMarqueeControl` kullanılabilir seçeneğini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="20926-405">In the **Toolbox**, open the **MarqueeControlTest Components** tab. You will see the `DemoMarqueeControl` available for selection.</span></span>

11. <span data-ttu-id="20926-406">Bir örneğini `DemoMarqueeControl` **Form1** tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="20926-406">Drag an instance of `DemoMarqueeControl` onto the **Form1** design surface.</span></span>

12. <span data-ttu-id="20926-407">Olay işleyicilerinde, `Start` ve `Stop` üzerindeki `DemoMarqueeControl`yöntemlerini çağırın. <xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="20926-407">In the <xref:System.Windows.Forms.Control.Click> event handlers, invoke the `Start` and `Stop` methods on the `DemoMarqueeControl`.</span></span>

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

13. <span data-ttu-id="20926-408">`MarqueeControlTest` Projeyi başlangıç projesi olarak ayarlayın ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="20926-408">Set the `MarqueeControlTest` project as the startup project and run it.</span></span> <span data-ttu-id="20926-409">Formunu görüntüleyen `DemoMarqueeControl`formu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="20926-409">You will see the form displaying your `DemoMarqueeControl`.</span></span> <span data-ttu-id="20926-410">Animasyonu başlatmak için **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="20926-410">Select the **Start** button to start the animation.</span></span> <span data-ttu-id="20926-411">Metnin yanıp sönmesi ve kenarlığın etrafında hareket eden ışıklar görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="20926-411">You should see the text flashing and the lights moving around the border.</span></span>

## <a name="next-steps"></a><span data-ttu-id="20926-412">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="20926-412">Next steps</span></span>

<span data-ttu-id="20926-413">, `MarqueeControlLibrary` Özel denetimlerin ve ilişkili tasarımcılarının basit bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="20926-413">The `MarqueeControlLibrary` demonstrates a simple implementation of custom controls and associated designers.</span></span> <span data-ttu-id="20926-414">Bu örneği çeşitli yollarla daha karmaşık hale getirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="20926-414">You can make this sample more sophisticated in several ways:</span></span>

- <span data-ttu-id="20926-415">Tasarımcı `DemoMarqueeControl` içindeki için özellik değerlerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="20926-415">Change the property values for the `DemoMarqueeControl` in the designer.</span></span> <span data-ttu-id="20926-416">Daha fazla `MarqueBorder` denetim ekleyin ve iç içe geçmiş bir efekt oluşturmak için bunları üst örnekleri içine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="20926-416">Add more `MarqueBorder` controls and dock them within their parent instances to create a nested effect.</span></span> <span data-ttu-id="20926-417">`UpdatePeriod` Ve ışığıyla ilgili özellikler için farklı ayarlarla denemeler yapın.</span><span class="sxs-lookup"><span data-stu-id="20926-417">Experiment with different settings for the `UpdatePeriod` and the light-related properties.</span></span>

- <span data-ttu-id="20926-418">Kendi uygulamalarınızı yazar `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="20926-418">Author your own implementations of `IMarqueeWidget`.</span></span> <span data-ttu-id="20926-419">Örneğin, yanıp sönen bir "Neon Sign" veya birden çok görüntüde animasyonlu bir işaret oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20926-419">You could, for example, create a flashing "neon sign" or an animated sign with multiple images.</span></span>

- <span data-ttu-id="20926-420">Tasarım zamanı deneyimini daha da özelleştirin.</span><span class="sxs-lookup"><span data-stu-id="20926-420">Further customize the design-time experience.</span></span> <span data-ttu-id="20926-421"><xref:System.Windows.Forms.Control.Enabled%2A> Ve<xref:System.Windows.Forms.Control.Visible%2A>' den daha fazla özelliği gölgelendirmeyi deneyebilirsiniz ve yeni özellikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20926-421">You could try shadowing more properties than <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A>, and you could add new properties.</span></span> <span data-ttu-id="20926-422">Alt öğe denetimleri yerleştirme gibi yaygın görevleri basitleştirmek için yeni tasarımcı fiilleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20926-422">Add new designer verbs to simplify common tasks like docking child controls.</span></span>

- <span data-ttu-id="20926-423">Lisansına sahip `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="20926-423">License the `MarqueeControl`.</span></span>

- <span data-ttu-id="20926-424">Denetimlerinizin serileştirilme şeklini ve kodun onlar için nasıl oluşturulduğunu denetleyin.</span><span class="sxs-lookup"><span data-stu-id="20926-424">Control how your controls are serialized and how code is generated for them.</span></span> <span data-ttu-id="20926-425">Daha fazla bilgi için bkz. [dinamik kaynak kodu oluşturma ve derleme](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="20926-425">For more information, see [Dynamic Source Code Generation and Compilation](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="20926-426">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20926-426">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
