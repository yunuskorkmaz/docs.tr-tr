---
title: Visual Studio tasarım zamanı özelliklerinden faydalanan bir denetim oluşturma
description: Tasarım zamanı özelliklerinden faydalanan Windows Forms özel bir denetim için özel tasarımcı oluşturmayı öğrenin.
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 03c04578ecb01b689f58d41a46eef5793fb1182c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613916"
---
# <a name="walkthrough-create-a-control-that-takes-advantage-of-design-time-features"></a><span data-ttu-id="88f9a-103">İzlenecek yol: tasarım zamanı özelliklerinden faydalanan bir denetim oluşturma</span><span class="sxs-lookup"><span data-stu-id="88f9a-103">Walkthrough: Create a control that takes advantage of design-time features</span></span>

<span data-ttu-id="88f9a-104">Özel bir denetim için tasarım zamanı deneyimi, ilişkili bir özel tasarımcı Authoring ile geliştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-104">The design-time experience for a custom control can be enhanced by authoring an associated custom designer.</span></span>

<span data-ttu-id="88f9a-105">Bu makalede özel bir denetim için nasıl özel tasarımcı oluşturacağınız açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-105">This article illustrates how to create a custom designer for a custom control.</span></span> <span data-ttu-id="88f9a-106">`MarqueeControl`Adlı bir tür ve ilişkili tasarımcı sınıfını uygulayacaksınız `MarqueeControlRootDesigner` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-106">You'll implement a `MarqueeControl` type and an associated designer class called `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="88f9a-107">`MarqueeControl`Türü, animasyonlu ışıklar ve yanıp sönen metinle benzer bir tiyatro çerçevesine benzer bir ekran uygular.</span><span class="sxs-lookup"><span data-stu-id="88f9a-107">The `MarqueeControl` type implements a display similar to a theater marquee with animated lights and flashing text.</span></span>

<span data-ttu-id="88f9a-108">Bu denetim için tasarımcı, tasarım ortamıyla birlikte etkileşimde bulunur ve özel bir tasarım zamanı deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="88f9a-108">The designer for this control interacts with the design environment to provide a custom design-time experience.</span></span> <span data-ttu-id="88f9a-109">Özel tasarımcı sayesinde, bir özel `MarqueeControl` uygulamayı animasyonlu ışıklar ve yanıp sönen metni birçok birleşimde bir araya getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88f9a-109">With the custom designer, you can assemble a custom `MarqueeControl` implementation with animated lights and flashing text in many combinations.</span></span> <span data-ttu-id="88f9a-110">Bir form üzerinde, diğer Windows Forms denetimleri gibi, birleştirilmiş denetimi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88f9a-110">You can use the assembled control on a form like any other Windows Forms control.</span></span>

<span data-ttu-id="88f9a-111">Bu yönergeyi tamamladığınızda, özel denetiminiz aşağıdakine benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="88f9a-111">When you're finished with this walkthrough, your custom control will look something like the following:</span></span>

![Metin ve Başlat ve Durdur düğmelerini gösteren bir kayan yazıyı gösteren uygulama.](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

<span data-ttu-id="88f9a-113">Tam kod listesi için, bkz. [nasıl yapılır: tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="88f9a-113">For the complete code listing, see [How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="88f9a-114">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="88f9a-114">Prerequisites</span></span>

<span data-ttu-id="88f9a-115">Bu izlenecek yolu tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-115">In order to complete this walkthrough, you'll need Visual Studio.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="88f9a-116">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="88f9a-116">Create the project</span></span>

<span data-ttu-id="88f9a-117">İlk adım uygulama projesini oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-117">The first step is to create the application project.</span></span> <span data-ttu-id="88f9a-118">Bu projeyi, özel denetimi barındıran uygulamayı oluşturmak için kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="88f9a-118">You will use this project to build the application that hosts the custom control.</span></span>

<span data-ttu-id="88f9a-119">Visual Studio 'da yeni bir Windows Forms uygulama projesi oluşturun ve **MarqueeControlTest**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-119">In Visual Studio, create a new Windows Forms Application project, and name it **MarqueeControlTest**.</span></span>

## <a name="create-the-control-library-project"></a><span data-ttu-id="88f9a-120">Denetim kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="88f9a-120">Create the control library project</span></span>

1. <span data-ttu-id="88f9a-121">Çözüme bir Windows Forms denetim kitaplığı projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-121">Add a Windows Forms Control Library project to the solution.</span></span> <span data-ttu-id="88f9a-122">Projeyi **MarqueeControlLibrary**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-122">Name the project **MarqueeControlLibrary**.</span></span>

2. <span data-ttu-id="88f9a-123">**Çözüm Gezgini**kullanarak, tercih ettiğiniz dile bağlı olarak, "UserControl1.cs" veya "UserControl1. vb" adlı kaynak dosyayı silerek projenin varsayılan denetimini silin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-123">Using **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span>

3. <span data-ttu-id="88f9a-124">Projeye yeni bir <xref:System.Windows.Forms.UserControl> öğe ekleyin `MarqueeControlLibrary` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-124">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="88f9a-125">Yeni kaynak dosyasına **MarqueeControl**temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-125">Give the new source file a base name of **MarqueeControl**.</span></span>

4. <span data-ttu-id="88f9a-126">**Çözüm Gezgini**kullanarak projede yeni bir klasör oluşturun `MarqueeControlLibrary` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-126">Using **Solution Explorer**, create a new folder in the `MarqueeControlLibrary` project.</span></span>

5. <span data-ttu-id="88f9a-127">**Tasarım** klasörüne sağ tıklayın ve yeni bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-127">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="88f9a-128">**MarqueeControlRootDesigner**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-128">Name it **MarqueeControlRootDesigner**.</span></span>

6. <span data-ttu-id="88f9a-129">System. Design derlemesinden türler kullanmanız gerekir, bu nedenle bu başvuruyu `MarqueeControlLibrary` projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-129">You'll need to use types from the System.Design assembly, so add this reference to the `MarqueeControlLibrary` project.</span></span>

## <a name="reference-the-custom-control-project"></a><span data-ttu-id="88f9a-130">Özel denetim projesine başvur</span><span class="sxs-lookup"><span data-stu-id="88f9a-130">Reference the Custom Control Project</span></span>

<span data-ttu-id="88f9a-131">Bu `MarqueeControlTest` projeyi, özel denetimi test etmek için kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="88f9a-131">You will use the `MarqueeControlTest` project to test the custom control.</span></span> <span data-ttu-id="88f9a-132">Derlemeye bir proje başvurusu eklediğinizde test projesi özel denetimden haberdar olur `MarqueeControlLibrary` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-132">The test project will become aware of the custom control when you add a project reference to the `MarqueeControlLibrary` assembly.</span></span>

<span data-ttu-id="88f9a-133">`MarqueeControlTest`Projede, derlemeye bir proje başvurusu ekleyin `MarqueeControlLibrary` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-133">In the `MarqueeControlTest` project, add a project reference to the `MarqueeControlLibrary` assembly.</span></span> <span data-ttu-id="88f9a-134">Derlemeye doğrudan başvurmak yerine **Başvuru Ekle** Iletişim kutusundaki **Projeler** sekmesini kullandığınızdan emin olun `MarqueeControlLibrary` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-134">Be sure to use the **Projects** tab in the **Add Reference** dialog box instead of referencing the `MarqueeControlLibrary` assembly directly.</span></span>

## <a name="define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="88f9a-135">Özel bir denetim ve kendi özel tasarımcısını tanımlama</span><span class="sxs-lookup"><span data-stu-id="88f9a-135">Define a Custom Control and Its Custom Designer</span></span>

<span data-ttu-id="88f9a-136">Özel denetiminiz sınıfından türecektir <xref:System.Windows.Forms.UserControl> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-136">Your custom control will derive from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="88f9a-137">Bu, denetiminizin diğer denetimleri içermesini sağlar ve denetimi, varsayılan işlevselliğin harika olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="88f9a-137">This allows your control to contain other controls, and it gives your control a great deal of default functionality.</span></span>

<span data-ttu-id="88f9a-138">Özel denetiminizin ilişkili bir özel Tasarımcısı olacak.</span><span class="sxs-lookup"><span data-stu-id="88f9a-138">Your custom control will have an associated custom designer.</span></span> <span data-ttu-id="88f9a-139">Bu, özel denetiminiz için özel olarak uyarlanmış benzersiz bir tasarım deneyimi oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="88f9a-139">This allows you to create a unique design experience tailored specifically for your custom control.</span></span>

<span data-ttu-id="88f9a-140">Sınıfını kullanarak denetimi Tasarımcı ile ilişkilendirirsiniz <xref:System.ComponentModel.DesignerAttribute> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-140">You associate the control with its designer by using the <xref:System.ComponentModel.DesignerAttribute> class.</span></span> <span data-ttu-id="88f9a-141">Özel denetiminizin tüm tasarım zamanı davranışını geliştirmekte olduğunuzdan, özel tasarımcı <xref:System.ComponentModel.Design.IRootDesigner> arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="88f9a-141">Because you are developing the entire design-time behavior of your custom control, the custom designer will implement the <xref:System.ComponentModel.Design.IRootDesigner> interface.</span></span>

### <a name="to-define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="88f9a-142">Özel bir denetim ve özel tasarımcı tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="88f9a-142">To define a custom control and its custom designer</span></span>

1. <span data-ttu-id="88f9a-143">`MarqueeControl`Kaynak dosyasını **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-143">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="88f9a-144">Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="88f9a-144">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. <span data-ttu-id="88f9a-145"><xref:System.ComponentModel.DesignerAttribute> `MarqueeControl` Sınıfını sınıf bildirimine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-145">Add the <xref:System.ComponentModel.DesignerAttribute> to the `MarqueeControl` class declaration.</span></span> <span data-ttu-id="88f9a-146">Bu, özel denetimi Tasarımcı ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-146">This associates the custom control with its designer.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. <span data-ttu-id="88f9a-147">`MarqueeControlRootDesigner`Kaynak dosyasını **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-147">Open the `MarqueeControlRootDesigner` source file in the **Code Editor**.</span></span> <span data-ttu-id="88f9a-148">Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="88f9a-148">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. <span data-ttu-id="88f9a-149">Bildirimini `MarqueeControlRootDesigner` sınıfından devralacak şekilde değiştirin <xref:System.Windows.Forms.Design.DocumentDesigner> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-149">Change the declaration of `MarqueeControlRootDesigner` to inherit from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="88f9a-150"><xref:System.ComponentModel.ToolboxItemFilterAttribute> **Araç kutusu**ile tasarımcı etkileşimini belirtmek için öğesini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-150">Apply the <xref:System.ComponentModel.ToolboxItemFilterAttribute> to specify the designer interaction with the **Toolbox**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="88f9a-151">Sınıfının tanımı, `MarqueeControlRootDesigner` MarqueeControlLibrary. Design adlı bir ad alanı içine alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-151">The definition for the `MarqueeControlRootDesigner` class has been enclosed in a namespace called MarqueeControlLibrary.Design.</span></span> <span data-ttu-id="88f9a-152">Bu bildirim, tasarımcıyı tasarımla ilgili türler için ayrılmış özel bir ad alanına koyar.</span><span class="sxs-lookup"><span data-stu-id="88f9a-152">This declaration places the designer in a special namespace reserved for design-related types.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. <span data-ttu-id="88f9a-153">Sınıf için oluşturucuyu tanımlayın `MarqueeControlRootDesigner` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-153">Define the constructor for the `MarqueeControlRootDesigner` class.</span></span> <span data-ttu-id="88f9a-154"><xref:System.Diagnostics.Trace.WriteLine%2A>Oluşturucu gövdesine bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-154">Insert a <xref:System.Diagnostics.Trace.WriteLine%2A> statement in the constructor body.</span></span> <span data-ttu-id="88f9a-155">Bu, hata ayıklama için yararlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-155">This will be useful for debugging.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="create-an-instance-of-your-custom-control"></a><span data-ttu-id="88f9a-156">Özel denetiminizin bir örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="88f9a-156">Create an instance of your custom control</span></span>

1. <span data-ttu-id="88f9a-157">Projeye yeni bir <xref:System.Windows.Forms.UserControl> öğe ekleyin `MarqueeControlTest` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-157">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlTest` project.</span></span> <span data-ttu-id="88f9a-158">Yeni kaynak dosyasına **DemoMarqueeControl**temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-158">Give the new source file a base name of **DemoMarqueeControl**.</span></span>

2. <span data-ttu-id="88f9a-159">`DemoMarqueeControl`Dosyayı **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-159">Open the `DemoMarqueeControl` file in the **Code Editor**.</span></span> <span data-ttu-id="88f9a-160">Dosyanın en üstünde, `MarqueeControlLibrary` ad alanını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="88f9a-160">At the top of the file, import the `MarqueeControlLibrary` namespace:</span></span>

   ```vb
   Imports MarqueeControlLibrary
   ```

   ```csharp
   using MarqueeControlLibrary;
   ```

3. <span data-ttu-id="88f9a-161">Bildirimini `DemoMarqueeControl` sınıfından devralacak şekilde değiştirin `MarqueeControl` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-161">Change the declaration of `DemoMarqueeControl` to inherit from the `MarqueeControl` class.</span></span>

4. <span data-ttu-id="88f9a-162">Projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-162">Build the project.</span></span>

5. <span data-ttu-id="88f9a-163">Windows Form Tasarımcısı Form1 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-163">Open Form1 in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="88f9a-164">**Araç kutusunda** **MarqueeControlTest Components** sekmesini bulun ve açın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-164">Find the **MarqueeControlTest Components** tab in the **Toolbox** and open it.</span></span> <span data-ttu-id="88f9a-165">`DemoMarqueeControl` **Araç kutusundan** bir öğesini formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-165">Drag a `DemoMarqueeControl` from the **Toolbox** onto your form.</span></span>

7. <span data-ttu-id="88f9a-166">Projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-166">Build the project.</span></span>

## <a name="set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="88f9a-167">Projeyi tasarım zamanı hata ayıklama için ayarlama</span><span class="sxs-lookup"><span data-stu-id="88f9a-167">Set Up the Project for Design-Time Debugging</span></span>

<span data-ttu-id="88f9a-168">Özel bir tasarım zamanı deneyimi geliştirirken, denetimlerinizin ve bileşenlerinizin hata ayıklaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-168">When you're developing a custom design-time experience, it will be necessary to debug your controls and components.</span></span> <span data-ttu-id="88f9a-169">Projenizi tasarım zamanında hata ayıklamaya izin verecek şekilde kurmak için basit bir yol vardır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-169">There is a simple way to set up your project to allow debugging at design time.</span></span> <span data-ttu-id="88f9a-170">Daha fazla bilgi için bkz. [Izlenecek yol: tasarım zamanında özel Windows Forms Denetimlerinde hata ayıklama](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="88f9a-170">For more information, see [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>

1. <span data-ttu-id="88f9a-171">Projeye sağ tıklayın `MarqueeControlLibrary` ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-171">Right-click the `MarqueeControlLibrary` project and select **Properties**.</span></span>

2. <span data-ttu-id="88f9a-172">**MarqueeControlLibrary Özellik sayfaları** Iletişim kutusunda **hata ayıklama** sayfasını seçin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-172">In the **MarqueeControlLibrary Property Pages** dialog box, select the **Debug** page.</span></span>

3. <span data-ttu-id="88f9a-173">**Başlangıç eylemi** bölümünde **dış program Başlat**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-173">In the **Start Action** section, select **Start External Program**.</span></span> <span data-ttu-id="88f9a-174">Visual Studio 'nun ayrı bir örneğinde hata ayıkladığınızda, ![ ](./media/visual-studio-ellipsis-button.png) VISUAL Studio IDE 'ye gitmek için üç nokta (Visual studio 'nun Özellikler penceresi) düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-174">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="88f9a-175">Yürütülebilir dosyanın adı devenv.exe ve varsayılan konuma yüklediyseniz, yolu *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019 \\ \<edition>\Common7\IDE\devenv.exe*.</span><span class="sxs-lookup"><span data-stu-id="88f9a-175">The name of the executable file is devenv.exe, and if you installed to the default location, its path is *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\\\<edition>\Common7\IDE\devenv.exe*.</span></span>

4. <span data-ttu-id="88f9a-176">İletişim kutusunu kapatmak için **Tamam ' ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-176">Select **OK** to close the dialog box.</span></span>

5. <span data-ttu-id="88f9a-177">Bu hata ayıklama yapılandırmasını etkinleştirmek için MarqueeControlLibrary projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-177">Right-click the MarqueeControlLibrary project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>

## <a name="checkpoint"></a><span data-ttu-id="88f9a-178">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="88f9a-178">Checkpoint</span></span>

<span data-ttu-id="88f9a-179">Artık özel denetiminizin tasarım zamanı davranışını hata ayıklamaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="88f9a-179">You are now ready to debug the design-time behavior of your custom control.</span></span> <span data-ttu-id="88f9a-180">Hata ayıklama ortamının doğru şekilde ayarlandığını belirledikten sonra, özel denetim ve özel tasarımcı arasındaki ilişkilendirmeyi test edersiniz.</span><span class="sxs-lookup"><span data-stu-id="88f9a-180">Once you've determined that the debugging environment is set up correctly, you'll test the association between the custom control and the custom designer.</span></span>

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a><span data-ttu-id="88f9a-181">Hata ayıklama ortamını ve tasarımcı ilişkilendirmesini test etmek için</span><span class="sxs-lookup"><span data-stu-id="88f9a-181">To test the debugging environment and the designer association</span></span>

1. <span data-ttu-id="88f9a-182">**Kod düzenleyicisinde** MarqueeControlRootDesigner kaynak dosyasını açın ve deyime bir kesme noktası yerleştirin <xref:System.Diagnostics.Trace.WriteLine%2A> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-182">Open the MarqueeControlRootDesigner source file in the **Code Editor** and place a breakpoint on the <xref:System.Diagnostics.Trace.WriteLine%2A> statement.</span></span>

2. <span data-ttu-id="88f9a-183">Hata ayıklama oturumu başlatmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-183">Press **F5** to start the debugging session.</span></span>

   <span data-ttu-id="88f9a-184">Visual Studio 'nun yeni bir örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="88f9a-184">A new instance of Visual Studio is created.</span></span>

3. <span data-ttu-id="88f9a-185">Visual Studio 'nun yeni örneğinde, MarqueeControlTest çözümünü açın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-185">In the new instance of Visual Studio, open the MarqueeControlTest solution.</span></span> <span data-ttu-id="88f9a-186">**Dosya** menüsünden **son projeler** ' i seçerek çözümü kolayca bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88f9a-186">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="88f9a-187">MarqueeControlTest. sln çözüm dosyası en son kullanılan dosya olarak listelenecektir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-187">The MarqueeControlTest.sln solution file will be listed as the most recently used file.</span></span>

4. <span data-ttu-id="88f9a-188">Öğesini `DemoMarqueeControl` tasarımcıda açın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-188">Open the `DemoMarqueeControl` in the designer.</span></span>

   <span data-ttu-id="88f9a-189">Visual Studio 'nun hata ayıklama örneği, kesme noktasında odak ve yürütme işlemini alır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-189">The debugging instance of Visual Studio obtains focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="88f9a-190">Hata ayıklama oturumuna devam etmek için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-190">Press **F5** to continue the debugging session.</span></span>

<span data-ttu-id="88f9a-191">Bu noktada, özel denetiminizi ve onunla ilişkili özel tasarımcıyı geliştirip hata ayıklamanızın her şey vardır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-191">At this point, everything is in place for you to develop and debug your custom control and its associated custom designer.</span></span> <span data-ttu-id="88f9a-192">Bu makalenin geri kalanında, denetimin ve tasarımcının özelliklerini uygulama ayrıntılarına yoğunlaşmaktadır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-192">The remainder of this article concentrates on the details of implementing features of the control and the designer.</span></span>

## <a name="implement-the-custom-control"></a><span data-ttu-id="88f9a-193">Özel denetimi uygulama</span><span class="sxs-lookup"><span data-stu-id="88f9a-193">Implement the Custom Control</span></span>

<span data-ttu-id="88f9a-194">, `MarqueeControl` Bir <xref:System.Windows.Forms.UserControl> Özelleştirme biraz daha vardır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-194">The `MarqueeControl` is a <xref:System.Windows.Forms.UserControl> with a little bit of customization.</span></span> <span data-ttu-id="88f9a-195">İki yöntem sunar: `Start` , kayan yazı animasyonunu başlatan ve `Stop` animasyonu durduran.</span><span class="sxs-lookup"><span data-stu-id="88f9a-195">It exposes two methods: `Start`, which starts the marquee animation, and `Stop`, which stops the animation.</span></span> <span data-ttu-id="88f9a-196">, `MarqueeControl` Arabirimini uygulayan alt denetimler içerdiğinden ve `IMarqueeWidget` `Start` `Stop` her bir alt denetimi numaralandırın ve öğesini `StartMarquee` `StopMarquee` uygulayan her alt denetimde sırasıyla ve yöntemlerini çağırdığından `IMarqueeWidget` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-196">Because the `MarqueeControl` contains child controls that implement the `IMarqueeWidget` interface, `Start` and `Stop` enumerate each child control and call the `StartMarquee` and `StopMarquee` methods, respectively, on each child control that implements `IMarqueeWidget`.</span></span>

<span data-ttu-id="88f9a-197">`MarqueeBorder`Ve `MarqueeText` denetimlerinin görünümü düzene bağlıdır, `MarqueeControl` Bu nedenle <xref:System.Windows.Forms.Control.OnLayout%2A> yöntemi ve <xref:System.Windows.Forms.Control.PerformLayout%2A> Bu türün alt denetimlerinde yapılan çağrıları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="88f9a-197">The appearance of the `MarqueeBorder` and `MarqueeText` controls is dependent on the layout, so `MarqueeControl` overrides the <xref:System.Windows.Forms.Control.OnLayout%2A> method and calls <xref:System.Windows.Forms.Control.PerformLayout%2A> on child controls of this type.</span></span>

<span data-ttu-id="88f9a-198">Bu, özelleştirmelerin bir kapsamını `MarqueeControl` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-198">This is the extent of the `MarqueeControl` customizations.</span></span> <span data-ttu-id="88f9a-199">Çalışma zamanı özellikleri `MarqueeBorder` ve denetimleri tarafından uygulanır `MarqueeText` ve tasarım zamanı özellikleri `MarqueeBorderDesigner` ve sınıfları tarafından uygulanır `MarqueeControlRootDesigner` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-199">The run-time features are implemented by the `MarqueeBorder` and `MarqueeText` controls, and the design-time features are implemented by the `MarqueeBorderDesigner` and `MarqueeControlRootDesigner` classes.</span></span>

### <a name="to-implement-your-custom-control"></a><span data-ttu-id="88f9a-200">Özel denetiminizi uygulamak için</span><span class="sxs-lookup"><span data-stu-id="88f9a-200">To implement your custom control</span></span>

1. <span data-ttu-id="88f9a-201">`MarqueeControl`Kaynak dosyasını **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-201">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="88f9a-202">`Start`Ve yöntemlerini uygulayın `Stop` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-202">Implement the `Start` and `Stop` methods.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. <span data-ttu-id="88f9a-203">Yöntemini geçersiz kılın <xref:System.Windows.Forms.Control.OnLayout%2A> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-203">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="create-a-child-control-for-your-custom-control"></a><span data-ttu-id="88f9a-204">Özel denetiminiz için bir alt denetim oluşturma</span><span class="sxs-lookup"><span data-stu-id="88f9a-204">Create a Child Control for Your Custom Control</span></span>

<span data-ttu-id="88f9a-205">`MarqueeControl`İki tür alt denetimi barındırır: `MarqueeBorder` Denetim ve `MarqueeText` Denetim.</span><span class="sxs-lookup"><span data-stu-id="88f9a-205">The `MarqueeControl` will host two kinds of child control: the `MarqueeBorder` control and the `MarqueeText` control.</span></span>

- <span data-ttu-id="88f9a-206">`MarqueeBorder`: Bu denetim, kenarları etrafında "ışıklar" kenarlığını boyar.</span><span class="sxs-lookup"><span data-stu-id="88f9a-206">`MarqueeBorder`: This control paints a border of "lights" around its edges.</span></span> <span data-ttu-id="88f9a-207">Kenarlıkta bulunan ışıklar, kenarlık etrafında taşınıyor gibi görünürler.</span><span class="sxs-lookup"><span data-stu-id="88f9a-207">The lights flash in sequence, so they appear to be moving around the border.</span></span> <span data-ttu-id="88f9a-208">Işıklarının flaşın, çağrılan bir özellik tarafından denetlenme hızı `UpdatePeriod` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-208">The speed at which the lights flash is controlled by a property called `UpdatePeriod`.</span></span> <span data-ttu-id="88f9a-209">Diğer birçok özel özellik, denetimin görünümünün diğer yönlerini tespit.</span><span class="sxs-lookup"><span data-stu-id="88f9a-209">Several other custom properties determine other aspects of the control's appearance.</span></span> <span data-ttu-id="88f9a-210">`StartMarquee` `StopMarquee` Animasyon başladığında ve durdurulduğunda denetim olarak adlandırılan iki yöntem.</span><span class="sxs-lookup"><span data-stu-id="88f9a-210">Two methods, called `StartMarquee` and `StopMarquee`, control when the animation starts and stops.</span></span>

- <span data-ttu-id="88f9a-211">`MarqueeText`: Bu denetim yanıp sönen bir dizeyi boyar.</span><span class="sxs-lookup"><span data-stu-id="88f9a-211">`MarqueeText`: This control paints a flashing string.</span></span> <span data-ttu-id="88f9a-212">Denetim gibi `MarqueeBorder` , metnin yanıp sönebileceği hız, özelliği tarafından kontrol edilir `UpdatePeriod` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-212">Like the `MarqueeBorder` control, the speed at which the text flashes is controlled by the `UpdatePeriod` property.</span></span> <span data-ttu-id="88f9a-213">`MarqueeText`Denetim Ayrıca, `StartMarquee` `StopMarquee` denetimiyle ortak olan ve yöntemlerine sahiptir `MarqueeBorder` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-213">The `MarqueeText` control also has the `StartMarquee` and `StopMarquee` methods in common with the `MarqueeBorder` control.</span></span>

<span data-ttu-id="88f9a-214">Tasarım zamanında, `MarqueeControlRootDesigner` Bu iki denetim türünün herhangi bir kombinasyonda içine eklenmesine izin verir `MarqueeControl` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-214">At design time, the `MarqueeControlRootDesigner` allows these two control types to be added to a `MarqueeControl` in any combination.</span></span>

<span data-ttu-id="88f9a-215">İki denetimin ortak özellikleri, adlı bir arabirimle birleştirilir `IMarqueeWidget` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-215">Common features of the two controls are factored into an interface called `IMarqueeWidget`.</span></span> <span data-ttu-id="88f9a-216">Bu, `MarqueeControl` bir seçim çerçevesinin ilgili alt denetimleri bulmasını ve özel bir işleme vermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="88f9a-216">This allows the `MarqueeControl` to discover any Marquee-related child controls and give them special treatment.</span></span>

<span data-ttu-id="88f9a-217">Düzenli animasyon özelliğini uygulamak için, <xref:System.ComponentModel.BackgroundWorker> <xref:System.ComponentModel?displayProperty=nameWithType> ad alanındaki nesneleri kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="88f9a-217">To implement the periodic animation feature, you will use <xref:System.ComponentModel.BackgroundWorker> objects from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="88f9a-218"><xref:System.Windows.Forms.Timer>Nesneleri kullanabilirsiniz, ancak birçok `IMarqueeWidget` nesne mevcut olduğunda, tek UI iş parçacığı animasyonla birlikte tutulamayabilir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-218">You could use <xref:System.Windows.Forms.Timer> objects, but when many `IMarqueeWidget` objects are present, the single UI thread may be unable to keep up with the animation.</span></span>

### <a name="to-create-a-child-control-for-your-custom-control"></a><span data-ttu-id="88f9a-219">Özel denetiminiz için bir alt denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="88f9a-219">To create a child control for your custom control</span></span>

1. <span data-ttu-id="88f9a-220">Projeye yeni bir sınıf öğesi ekleyin `MarqueeControlLibrary` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-220">Add a new class item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="88f9a-221">Yeni kaynak dosyasına "Imarqueepencere öğesi" için temel adı verin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-221">Give the new source file a base name of "IMarqueeWidget."</span></span>

2. <span data-ttu-id="88f9a-222">`IMarqueeWidget`Kaynak dosyasını **kod düzenleyicisinde** açın ve bildirimi ' den ' `class` e değiştirin `interface` :</span><span class="sxs-lookup"><span data-stu-id="88f9a-222">Open the `IMarqueeWidget` source file in the **Code Editor** and change the declaration from `class` to `interface`:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. <span data-ttu-id="88f9a-223">`IMarqueeWidget`İki yöntemi ve kayan yazı animasyonunu işleyen bir özelliği göstermek için aşağıdaki kodu arabirimine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="88f9a-223">Add the following code to the `IMarqueeWidget` interface to expose two methods and a property that manipulate the marquee animation:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. <span data-ttu-id="88f9a-224">Projeye yeni bir **özel denetim** öğesi ekleyin `MarqueeControlLibrary` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-224">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="88f9a-225">Yeni kaynak dosyasına "MarqueeText" temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-225">Give the new source file a base name of "MarqueeText."</span></span>

5. <span data-ttu-id="88f9a-226"><xref:System.ComponentModel.BackgroundWorker> **Araç kutusundan** bir bileşeni denetim üzerine sürükleyin `MarqueeText` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-226">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeText` control.</span></span> <span data-ttu-id="88f9a-227">Bu bileşen `MarqueeText` denetimin kendisini zaman uyumsuz olarak güncelleştirmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-227">This component will allow the `MarqueeText` control to update itself asynchronously.</span></span>

6. <span data-ttu-id="88f9a-228">**Özellikler** penceresinde, <xref:System.ComponentModel.BackgroundWorker> bileşen `WorkerReportsProgress` ve <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliklerini **doğru**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-228">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to **true**.</span></span> <span data-ttu-id="88f9a-229">Bu ayarlar, <xref:System.ComponentModel.BackgroundWorker> bileşenin düzenli olarak <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayı kullanmasına ve zaman uyumsuz güncelleştirmeleri iptal edebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="88f9a-229">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span>

   <span data-ttu-id="88f9a-230">Daha fazla bilgi için bkz. [BackgroundWorker Component](backgroundworker-component.md).</span><span class="sxs-lookup"><span data-stu-id="88f9a-230">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

7. <span data-ttu-id="88f9a-231">`MarqueeText`Kaynak dosyasını **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-231">Open the `MarqueeText` source file in the **Code Editor**.</span></span> <span data-ttu-id="88f9a-232">Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="88f9a-232">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. <span data-ttu-id="88f9a-233">`MarqueeText`' Dan devralması için bildirimini değiştirin <xref:System.Windows.Forms.Label> ve `IMarqueeWidget` arabirimini uygulayın:</span><span class="sxs-lookup"><span data-stu-id="88f9a-233">Change the declaration of `MarqueeText` to inherit from <xref:System.Windows.Forms.Label> and to implement the `IMarqueeWidget` interface:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. <span data-ttu-id="88f9a-234">Gösterilen özelliklere karşılık gelen örnek değişkenlerini bildirin ve bunları oluşturucuda başlatın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-234">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span> <span data-ttu-id="88f9a-235">`isLit`Alan, metnin özelliği tarafından verilen renkte boyanmış olup olmayacağını belirler `LightColor` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-235">The `isLit` field determines if the text is to be painted in the color given by the `LightColor` property.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. <span data-ttu-id="88f9a-236">`IMarqueeWidget` arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-236">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="88f9a-237">`StartMarquee`Ve `StopMarquee` yöntemleri, <xref:System.ComponentModel.BackgroundWorker> <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> animasyonu başlatmak ve durdurmak için bileşenin ve yöntemlerini çağırır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-237">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="88f9a-238"><xref:System.ComponentModel.CategoryAttribute.Category%2A>Ve <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> öznitelikleri, `UpdatePeriod` "kayan yazı" adlı Özellikler penceresi özel bir bölümünde görünmesi için özelliğine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-238">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to the `UpdatePeriod` property so it appears in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. <span data-ttu-id="88f9a-239">Özellik erişimcileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-239">Implement the property accessors.</span></span> <span data-ttu-id="88f9a-240">İstemciler için iki özelliği kullanıma sunacaksınız: `LightColor` ve `DarkColor` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-240">You'll expose two properties to clients: `LightColor` and `DarkColor`.</span></span> <span data-ttu-id="88f9a-241"><xref:System.ComponentModel.CategoryAttribute.Category%2A>Ve <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> öznitelikleri bu özelliklere uygulanır, bu nedenle Özellikler "kayan yazı" adlı Özellikler penceresi özel bir bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-241">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to these properties, so the properties appear in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. <span data-ttu-id="88f9a-242"><xref:System.ComponentModel.BackgroundWorker>Bileşen ve olaylar için işleyicileri uygulayın <xref:System.ComponentModel.BackgroundWorker.DoWork> <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-242">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="88f9a-243"><xref:System.ComponentModel.BackgroundWorker.DoWork>Olay işleyicisi, tarafından belirtilen milisaniye sayısı için uyku moduna geçer `UpdatePeriod` <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-243">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="88f9a-244"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged>Olay işleyicisi, yanıp sönmeye yönelik görünümü sağlamak için açık ve koyu durumu arasındaki metni değiştirir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-244">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler toggles the text between its light and dark state to give the appearance of flashing.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. <span data-ttu-id="88f9a-245"><xref:System.Windows.Forms.Control.OnPaint%2A>Animasyonu etkinleştirmek için yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-245">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method to enable the animation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. <span data-ttu-id="88f9a-246">Çözümü derlemek için **F6** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-246">Press **F6** to build the solution.</span></span>

## <a name="create-the-marqueeborder-child-control"></a><span data-ttu-id="88f9a-247">MarqueeBorder alt denetimini oluşturma</span><span class="sxs-lookup"><span data-stu-id="88f9a-247">Create the MarqueeBorder Child Control</span></span>

<span data-ttu-id="88f9a-248">`MarqueeBorder`Denetim, denetimden biraz daha karmaşıktır `MarqueeText` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-248">The `MarqueeBorder` control is slightly more sophisticated than the `MarqueeText` control.</span></span> <span data-ttu-id="88f9a-249">Daha fazla özelliğe sahiptir ve <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemdeki animasyon daha fazla yer alır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-249">It has more properties and the animation in the <xref:System.Windows.Forms.Control.OnPaint%2A> method is more involved.</span></span> <span data-ttu-id="88f9a-250">Prensibi, denetime oldukça benzer `MarqueeText` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-250">In principle, it is quite similar to the `MarqueeText` control.</span></span>

<span data-ttu-id="88f9a-251">`MarqueeBorder`Denetimde alt denetimler olabileceğinden, olayların farkında olması gerekir <xref:System.Windows.Forms.Control.Layout> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-251">Because the `MarqueeBorder` control can have child controls, it needs to be aware of <xref:System.Windows.Forms.Control.Layout> events.</span></span>

### <a name="to-create-the-marqueeborder-control"></a><span data-ttu-id="88f9a-252">MarqueeBorder denetimini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="88f9a-252">To create the MarqueeBorder control</span></span>

1. <span data-ttu-id="88f9a-253">Projeye yeni bir **özel denetim** öğesi ekleyin `MarqueeControlLibrary` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-253">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="88f9a-254">Yeni kaynak dosyasına "MarqueeBorder" temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-254">Give the new source file a base name of "MarqueeBorder."</span></span>

2. <span data-ttu-id="88f9a-255"><xref:System.ComponentModel.BackgroundWorker> **Araç kutusundan** bir bileşeni denetim üzerine sürükleyin `MarqueeBorder` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-255">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeBorder` control.</span></span> <span data-ttu-id="88f9a-256">Bu bileşen `MarqueeBorder` denetimin kendisini zaman uyumsuz olarak güncelleştirmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-256">This component will allow the `MarqueeBorder` control to update itself asynchronously.</span></span>

3. <span data-ttu-id="88f9a-257">**Özellikler** penceresinde, <xref:System.ComponentModel.BackgroundWorker> bileşen `WorkerReportsProgress` ve <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliklerini **doğru**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-257">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to **true**.</span></span> <span data-ttu-id="88f9a-258">Bu ayarlar, <xref:System.ComponentModel.BackgroundWorker> bileşenin düzenli olarak <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayı kullanmasına ve zaman uyumsuz güncelleştirmeleri iptal edebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="88f9a-258">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span> <span data-ttu-id="88f9a-259">Daha fazla bilgi için bkz. [BackgroundWorker Component](backgroundworker-component.md).</span><span class="sxs-lookup"><span data-stu-id="88f9a-259">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

4. <span data-ttu-id="88f9a-260">**Özellikler** penceresinde, **Olaylar** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-260">In the **Properties** window, select the **Events** button.</span></span> <span data-ttu-id="88f9a-261">Ve olayları için işleyiciler <xref:System.ComponentModel.BackgroundWorker.DoWork> iliştirin <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-261">Attach handlers for the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

5. <span data-ttu-id="88f9a-262">`MarqueeBorder`Kaynak dosyasını **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-262">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span> <span data-ttu-id="88f9a-263">Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="88f9a-263">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. <span data-ttu-id="88f9a-264">`MarqueeBorder`' Dan devralması için bildirimini değiştirin <xref:System.Windows.Forms.Panel> ve `IMarqueeWidget` arabirimini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-264">Change the declaration of `MarqueeBorder` to inherit from <xref:System.Windows.Forms.Panel> and to implement the `IMarqueeWidget` interface.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. <span data-ttu-id="88f9a-265">Denetimin durumunu yönetmek için iki numaralandırma bildirin `MarqueeBorder` : `MarqueeSpinDirection` , ışıklarının etrafında "döndürme" ve `MarqueeLightShape` ışıklarının şeklini (kare veya dairesel) belirleyen yönü belirleyen yönü belirler.</span><span class="sxs-lookup"><span data-stu-id="88f9a-265">Declare two enumerations for managing the `MarqueeBorder` control's state: `MarqueeSpinDirection`, which determines the direction in which the lights "spin" around the border, and `MarqueeLightShape`, which determines the shape of the lights (square or circular).</span></span> <span data-ttu-id="88f9a-266">Bu bildirimleri `MarqueeBorder` Sınıf bildiriminden önce yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-266">Place these declarations before the `MarqueeBorder` class declaration.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. <span data-ttu-id="88f9a-267">Gösterilen özelliklere karşılık gelen örnek değişkenlerini bildirin ve bunları oluşturucuda başlatın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-267">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. <span data-ttu-id="88f9a-268">`IMarqueeWidget` arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-268">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="88f9a-269">`StartMarquee`Ve `StopMarquee` yöntemleri, <xref:System.ComponentModel.BackgroundWorker> <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> animasyonu başlatmak ve durdurmak için bileşenin ve yöntemlerini çağırır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-269">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="88f9a-270">`MarqueeBorder`Denetim alt denetimler içerebildiğinden, `StartMarquee` yöntemi, uygulamalarındaki tüm alt denetimleri ve çağrıları numaralandırır `StartMarquee` `IMarqueeWidget` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-270">Because the `MarqueeBorder` control can contain child controls, the `StartMarquee` method enumerates all child controls and calls `StartMarquee` on those that implement `IMarqueeWidget`.</span></span> <span data-ttu-id="88f9a-271">`StopMarquee`Yönteminde benzer bir uygulama vardır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-271">The `StopMarquee` method has a similar implementation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. <span data-ttu-id="88f9a-272">Özellik erişimcileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-272">Implement the property accessors.</span></span> <span data-ttu-id="88f9a-273">`MarqueeBorder`Denetimde, görünümünü denetlemek için çeşitli özellikler vardır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-273">The `MarqueeBorder` control has several properties for controlling its appearance.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. <span data-ttu-id="88f9a-274"><xref:System.ComponentModel.BackgroundWorker>Bileşen ve olaylar için işleyicileri uygulayın <xref:System.ComponentModel.BackgroundWorker.DoWork> <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-274">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="88f9a-275"><xref:System.ComponentModel.BackgroundWorker.DoWork>Olay işleyicisi, tarafından belirtilen milisaniye sayısı için uyku moduna geçer `UpdatePeriod` <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-275">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="88f9a-276"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged>Olay işleyicisi, diğer ışıklarının açık/koyu durumunun belirlendiği "temel" Işığın konumunu artırır ve <xref:System.Windows.Forms.Control.Refresh%2A> denetimin kendisini yeniden çizmeyi sağlamak için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-276">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler increments the position of the "base" light, from which the light/dark state of the other lights is determined, and calls the <xref:System.Windows.Forms.Control.Refresh%2A> method to cause the control to repaint itself.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. <span data-ttu-id="88f9a-277">Yardımcı yöntemleri ve ' yi `IsLit` uygulayın `DrawLight` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-277">Implement the helper methods, `IsLit` and `DrawLight`.</span></span>

    <span data-ttu-id="88f9a-278">`IsLit`Yöntemi, belirli bir konumdaki ışığın rengini belirler.</span><span class="sxs-lookup"><span data-stu-id="88f9a-278">The `IsLit` method determines the color of a light at a given position.</span></span> <span data-ttu-id="88f9a-279">"Açık" olan ışıklar özelliği tarafından verilen renkte çizilir `LightColor` ve "koyu" olan ışıklar özelliği tarafından verilen renkte çizilir `DarkColor` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-279">Lights that are "lit" are drawn in the color given by the `LightColor` property, and those that are "dark" are drawn in the color given by the `DarkColor` property.</span></span>

    <span data-ttu-id="88f9a-280">`DrawLight`Yöntemi uygun renk, şekil ve konumu kullanarak bir ışık çizer.</span><span class="sxs-lookup"><span data-stu-id="88f9a-280">The `DrawLight` method draws a light using the appropriate color, shape, and position.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. <span data-ttu-id="88f9a-281"><xref:System.Windows.Forms.Control.OnLayout%2A>Ve yöntemlerini geçersiz kılın <xref:System.Windows.Forms.Control.OnPaint%2A> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-281">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> and <xref:System.Windows.Forms.Control.OnPaint%2A> methods.</span></span>

    <span data-ttu-id="88f9a-282"><xref:System.Windows.Forms.Control.OnPaint%2A>Yöntemi, denetimin kenarları üzerinde ışıkları çizer `MarqueeBorder` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-282">The <xref:System.Windows.Forms.Control.OnPaint%2A> method draws the lights along the edges of the `MarqueeBorder` control.</span></span>

    <span data-ttu-id="88f9a-283"><xref:System.Windows.Forms.Control.OnPaint%2A>Yöntem denetimin boyutlarına bağlı olduğundan `MarqueeBorder` , düzen her değiştiğinde onu çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-283">Because the <xref:System.Windows.Forms.Control.OnPaint%2A> method depends on the dimensions of the `MarqueeBorder` control, you need to call it whenever the layout changes.</span></span> <span data-ttu-id="88f9a-284">Bunu başarmak için, öğesini geçersiz kılın <xref:System.Windows.Forms.Control.OnLayout%2A> ve çağırın <xref:System.Windows.Forms.Control.Refresh%2A> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-284">To achieve this, override <xref:System.Windows.Forms.Control.OnLayout%2A> and call <xref:System.Windows.Forms.Control.Refresh%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="88f9a-285">Gölge ve filtre özelliklerine özel tasarımcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="88f9a-285">Create a Custom Designer to Shadow and Filter Properties</span></span>

<span data-ttu-id="88f9a-286">`MarqueeControlRootDesigner`Sınıfı, kök Tasarımcı için uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="88f9a-286">The `MarqueeControlRootDesigner` class provides the implementation for the root designer.</span></span> <span data-ttu-id="88f9a-287">Üzerinde çalışan bu tasarımcıya ek olarak, `MarqueeControl` özellikle denetimle ilişkili özel bir tasarımcı gerekir `MarqueeBorder` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-287">In addition to this designer, which operates on the `MarqueeControl`, you'll need a custom designer that is specifically associated with the `MarqueeBorder` control.</span></span> <span data-ttu-id="88f9a-288">Bu tasarımcı, özel kök tasarlayıcı bağlamında uygun olan özel davranışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="88f9a-288">This designer provides custom behavior that is appropriate in the context of the custom root designer.</span></span>

<span data-ttu-id="88f9a-289">Özellikle, `MarqueeBorderDesigner` "gölgelendir" ve denetimdeki belirli özellikleri filtreleyerek `MarqueeBorder` tasarım ortamıyla etkileşimini değiştirmiş olacak.</span><span class="sxs-lookup"><span data-stu-id="88f9a-289">Specifically, the `MarqueeBorderDesigner` will "shadow" and filter certain properties on the `MarqueeBorder` control, changing their interaction with the design environment.</span></span>

<span data-ttu-id="88f9a-290">Bir bileşenin Özellik erişimcisine yönelik kesintiye uğratan çağrı, "gölgeleme" olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-290">Intercepting calls to a component's property accessor is known as "shadowing."</span></span> <span data-ttu-id="88f9a-291">Bir tasarımcının Kullanıcı tarafından ayarlanan değeri izlemesine ve isteğe bağlı olarak bu değeri tasarlanmakta olan bileşene iletmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-291">It allows a designer to track the value set by the user and optionally pass that value to the component being designed.</span></span>

<span data-ttu-id="88f9a-292">Bu örnekte, <xref:System.Windows.Forms.Control.Visible%2A> ve <xref:System.Windows.Forms.Control.Enabled%2A> Özellikleri, `MarqueeBorderDesigner` kullanıcının `MarqueeBorder` Tasarım zamanı sırasında denetimi görünmez veya devre dışı yapmasını önleyen tarafından gölgelenir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-292">For this example, the <xref:System.Windows.Forms.Control.Visible%2A> and <xref:System.Windows.Forms.Control.Enabled%2A> properties will be shadowed by the `MarqueeBorderDesigner`, which prevents the user from making the `MarqueeBorder` control invisible or disabled during design time.</span></span>

<span data-ttu-id="88f9a-293">Tasarımcılar Ayrıca özellikler ekleyebilir ve kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-293">Designers can also add and remove properties.</span></span> <span data-ttu-id="88f9a-294">Bu örnekte, <xref:System.Windows.Forms.Control.Padding%2A> özellik tasarım zamanında kaldırılacak, çünkü `MarqueeBorder` Denetim program aracılığıyla, özelliği tarafından belirtilen ışıklarının boyutuna göre doldurma ayarlıyor `LightSize` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-294">For this example, the <xref:System.Windows.Forms.Control.Padding%2A> property will be removed at design time, because the `MarqueeBorder` control programmatically sets the padding based on the size of the lights specified by the `LightSize` property.</span></span>

<span data-ttu-id="88f9a-295">İçin temel sınıf `MarqueeBorderDesigner` <xref:System.ComponentModel.Design.ComponentDesigner> , tasarım zamanında bir denetim tarafından açığa çıkarılan öznitelikleri, özellikleri ve olayları değiştirebilen yöntemler içerir:</span><span class="sxs-lookup"><span data-stu-id="88f9a-295">The base class for `MarqueeBorderDesigner` is <xref:System.ComponentModel.Design.ComponentDesigner>, which has methods that can change the attributes, properties, and events exposed by a control at design time:</span></span>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

<span data-ttu-id="88f9a-296">Bu yöntemleri kullanarak bir bileşenin genel arabirimini değiştirirken bu kuralları izleyin:</span><span class="sxs-lookup"><span data-stu-id="88f9a-296">When changing the public interface of a component using these methods, follow these rules:</span></span>

- <span data-ttu-id="88f9a-297">Yalnızca metotlarda öğe ekleme veya kaldırma `PreFilter`</span><span class="sxs-lookup"><span data-stu-id="88f9a-297">Add or remove items in the `PreFilter` methods only</span></span>

- <span data-ttu-id="88f9a-298">`PostFilter`Yalnızca metotlarda bulunan öğeleri değiştir</span><span class="sxs-lookup"><span data-stu-id="88f9a-298">Modify existing items in the `PostFilter` methods only</span></span>

- <span data-ttu-id="88f9a-299">Her zaman ilk olarak metotlarda temel uygulamayı çağırın `PreFilter`</span><span class="sxs-lookup"><span data-stu-id="88f9a-299">Always call the base implementation first in the `PreFilter` methods</span></span>

- <span data-ttu-id="88f9a-300">Her zaman, metotlarda en son temel uygulamayı çağırın `PostFilter`</span><span class="sxs-lookup"><span data-stu-id="88f9a-300">Always call the base implementation last in the `PostFilter` methods</span></span>

<span data-ttu-id="88f9a-301">Bu kurallara uymak, tasarım zamanı ortamındaki tüm tasarımcılarının tasarlanmakta olan tüm bileşenlerin tutarlı bir görünümüne sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="88f9a-301">Adhering to these rules ensures that all designers in the design-time environment have a consistent view of all components being designed.</span></span>

<span data-ttu-id="88f9a-302"><xref:System.ComponentModel.Design.ComponentDesigner>Sınıfı, gölgelendirilmiş özelliklerin değerlerini yönetmek için bir sözlük sağlar, bu da size belirli örnek değişkenleri oluşturma gereksinimini sizi maliyetinden kurtarır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-302">The <xref:System.ComponentModel.Design.ComponentDesigner> class provides a dictionary for managing the values of shadowed properties, which relieves you of the need to create specific instance variables.</span></span>

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="88f9a-303">Gölge ve filtre özelliklerine özel bir tasarımcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="88f9a-303">To create a custom designer to shadow and filter properties</span></span>

1. <span data-ttu-id="88f9a-304">**Tasarım** klasörüne sağ tıklayın ve yeni bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-304">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="88f9a-305">Kaynak dosyaya **MarqueeBorderDesigner**temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-305">Give the source file a base name of **MarqueeBorderDesigner**.</span></span>

2. <span data-ttu-id="88f9a-306">MarqueeBorderDesigner kaynak dosyasını **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-306">Open the MarqueeBorderDesigner source file in the **Code Editor**.</span></span> <span data-ttu-id="88f9a-307">Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="88f9a-307">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. <span data-ttu-id="88f9a-308">Bildirimini `MarqueeBorderDesigner` öğesinden devralacak şekilde değiştirin <xref:System.Windows.Forms.Design.ParentControlDesigner> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-308">Change the declaration of `MarqueeBorderDesigner` to inherit from <xref:System.Windows.Forms.Design.ParentControlDesigner>.</span></span>

    <span data-ttu-id="88f9a-309">`MarqueeBorder`Denetim alt denetimler içerebildiğinden, `MarqueeBorderDesigner` <xref:System.Windows.Forms.Design.ParentControlDesigner> üst-alt etkileşimini işleyen öğesinden devralır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-309">Because the `MarqueeBorder` control can contain child controls, `MarqueeBorderDesigner` inherits from <xref:System.Windows.Forms.Design.ParentControlDesigner>, which handles the parent-child interaction.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. <span data-ttu-id="88f9a-310">Temel uygulamasını geçersiz kılın <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-310">Override the base implementation of <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. <span data-ttu-id="88f9a-311"><xref:System.Windows.Forms.Control.Enabled%2A>Ve özelliklerini uygulayın <xref:System.Windows.Forms.Control.Visible%2A> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-311">Implement the <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A> properties.</span></span> <span data-ttu-id="88f9a-312">Bu uygulamalar, denetimin özelliklerini gölgelendir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-312">These implementations shadow the control's properties.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handle-component-changes"></a><span data-ttu-id="88f9a-313">Bileşen değişikliklerini işle</span><span class="sxs-lookup"><span data-stu-id="88f9a-313">Handle Component Changes</span></span>

<span data-ttu-id="88f9a-314">`MarqueeControlRootDesigner`Sınıfı, örneklerinizin özel tasarım zamanı deneyimini sağlar `MarqueeControl` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-314">The `MarqueeControlRootDesigner` class provides the custom design-time experience for your `MarqueeControl` instances.</span></span> <span data-ttu-id="88f9a-315">Tasarım zamanı işlevlerinin çoğu <xref:System.Windows.Forms.Design.DocumentDesigner> sınıfından devralınır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-315">Most of the design-time functionality is inherited from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="88f9a-316">Kodunuz iki özel özelleştirme uygular: bileşen değişikliklerini işleme ve tasarımcı fiilleri ekleme.</span><span class="sxs-lookup"><span data-stu-id="88f9a-316">Your code will implement two specific customizations: handling component changes, and adding designer verbs.</span></span>

<span data-ttu-id="88f9a-317">Kullanıcılar `MarqueeControl` örneklerini tasarlarsa, kök tasarlayıcı, `MarqueeControl` ve alt denetimlerinde yapılan değişiklikleri izler.</span><span class="sxs-lookup"><span data-stu-id="88f9a-317">As users design their `MarqueeControl` instances, your root designer will track changes to the `MarqueeControl` and its child controls.</span></span> <span data-ttu-id="88f9a-318">Tasarım zamanı ortamı, <xref:System.ComponentModel.Design.IComponentChangeService> bileşen durumundaki değişiklikleri izlemek için uygun bir hizmet sunar.</span><span class="sxs-lookup"><span data-stu-id="88f9a-318">The design-time environment offers a convenient service, <xref:System.ComponentModel.Design.IComponentChangeService>, for tracking changes to component state.</span></span>

<span data-ttu-id="88f9a-319">Ortamı yöntemiyle sorgulayarak bu hizmete bir başvuru elde edersiniz <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-319">You acquire a reference to this service by querying the environment with the <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> method.</span></span> <span data-ttu-id="88f9a-320">Sorgu başarılı olursa, tasarımcı olay için bir işleyici iliştirebilir <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> ve tasarım zamanında tutarlı bir durumu korumak için gereken görevleri gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-320">If the query is successful, your designer can attach a handler for the <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> event and perform whatever tasks are required to maintain a consistent state at design time.</span></span>

<span data-ttu-id="88f9a-321">Sınıfı söz konusu olduğunda, `MarqueeControlRootDesigner` <xref:System.Windows.Forms.Control.Refresh%2A> yöntemi tarafından içerilen her bir nesne üzerinde çağıracaksınız `IMarqueeWidget` `MarqueeControl` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-321">In the case of the `MarqueeControlRootDesigner` class, you will call the <xref:System.Windows.Forms.Control.Refresh%2A> method on each `IMarqueeWidget` object contained by the `MarqueeControl`.</span></span> <span data-ttu-id="88f9a-322">Bu, `IMarqueeWidget` üst öğesi gibi özellikler değiştirildiğinde nesnenin kendisini uygun şekilde yeniden görüntülemesine neden olur <xref:System.Windows.Forms.Control.Size%2A> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-322">This will cause the `IMarqueeWidget` object to repaint itself appropriately when properties like its parent's <xref:System.Windows.Forms.Control.Size%2A> are changed.</span></span>

### <a name="to-handle-component-changes"></a><span data-ttu-id="88f9a-323">Bileşen değişikliklerini işlemek için</span><span class="sxs-lookup"><span data-stu-id="88f9a-323">To handle component changes</span></span>

1. <span data-ttu-id="88f9a-324">`MarqueeControlRootDesigner`Kaynak dosyasını **kod düzenleyicisinde** açın ve metodunu geçersiz kılın <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-324">Open the `MarqueeControlRootDesigner` source file in the **Code Editor** and override the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span> <span data-ttu-id="88f9a-325">İçin temel uygulamasını çağırın <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> ve için sorgulayın <xref:System.ComponentModel.Design.IComponentChangeService> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-325">Call the base implementation of <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> and query for the <xref:System.ComponentModel.Design.IComponentChangeService>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. <span data-ttu-id="88f9a-326"><xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A>Olay işleyicisini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-326">Implement the <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> event handler.</span></span> <span data-ttu-id="88f9a-327">Gönderen bileşenin türünü test edin ve bir ise `IMarqueeWidget` <xref:System.Windows.Forms.Control.Refresh%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-327">Test the sending component's type, and if it is an `IMarqueeWidget`, call its <xref:System.Windows.Forms.Control.Refresh%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="add-designer-verbs-to-your-custom-designer"></a><span data-ttu-id="88f9a-328">Özel tasarımcıya tasarımcı fiilleri ekleme</span><span class="sxs-lookup"><span data-stu-id="88f9a-328">Add Designer Verbs to your Custom Designer</span></span>

<span data-ttu-id="88f9a-329">Tasarımcı fiili, olay işleyicisine bağlı bir menü komutu olur.</span><span class="sxs-lookup"><span data-stu-id="88f9a-329">A designer verb is a menu command linked to an event handler.</span></span> <span data-ttu-id="88f9a-330">Tasarımcı fiilleri, tasarım zamanında bir bileşenin kısayol menüsüne eklenir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-330">Designer verbs are added to a component's shortcut menu at design time.</span></span> <span data-ttu-id="88f9a-331">Daha fazla bilgi için bkz. <xref:System.ComponentModel.Design.DesignerVerb>.</span><span class="sxs-lookup"><span data-stu-id="88f9a-331">For more information, see <xref:System.ComponentModel.Design.DesignerVerb>.</span></span>

<span data-ttu-id="88f9a-332">Tasarımcılara iki tasarımcı fiilleri ekleyeceksiniz: **Testi Çalıştır** ve **testi durdur**.</span><span class="sxs-lookup"><span data-stu-id="88f9a-332">You will add two designer verbs to your designers: **Run Test** and **Stop Test**.</span></span> <span data-ttu-id="88f9a-333">Bu fiiller, tasarım zamanının çalışma zamanı davranışını görüntülemenize olanak sağlayacak `MarqueeControl` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-333">These verbs will allow you to view the run-time behavior of the `MarqueeControl` at design time.</span></span> <span data-ttu-id="88f9a-334">Bu fiiller öğesine eklenecektir `MarqueeControlRootDesigner` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-334">These verbs will be added to `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="88f9a-335">**Çalıştırma testi** çağrıldığında, fiil olay işleyicisi `StartMarquee` üzerinde yöntemini çağırır `MarqueeControl` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-335">When **Run Test** is invoked, the verb event handler will call the `StartMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="88f9a-336">**Testi durdur** çağrıldığında, fiil olay işleyicisi `StopMarquee` üzerinde yöntemini çağırır `MarqueeControl` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-336">When **Stop Test** is invoked, the verb event handler will call the `StopMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="88f9a-337">Ve yöntemlerinin uygulaması, `StartMarquee` `StopMarquee` uygulayan içerilen denetimler üzerinde bu yöntemleri çağırır `IMarqueeWidget` , bu nedenle içerilen `IMarqueeWidget` denetimlerin de teste katılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-337">The implementation of the `StartMarquee` and `StopMarquee` methods call these methods on contained controls that implement `IMarqueeWidget`, so any contained `IMarqueeWidget` controls will also participate in the test.</span></span>

### <a name="to-add-designer-verbs-to-your-custom-designers"></a><span data-ttu-id="88f9a-338">Özel tasarımcılara tasarımcı fiilleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="88f9a-338">To add designer verbs to your custom designers</span></span>

1. <span data-ttu-id="88f9a-339">`MarqueeControlRootDesigner`Sınıfında, ve adlı olay işleyicileri ekleyin `OnVerbRunTest` `OnVerbStopTest` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-339">In the `MarqueeControlRootDesigner` class, add event handlers named `OnVerbRunTest` and `OnVerbStopTest`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. <span data-ttu-id="88f9a-340">Bu olay işleyicilerini ilgili tasarımcı fiillerine bağlayın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-340">Connect these event handlers to their corresponding designer verbs.</span></span> <span data-ttu-id="88f9a-341">`MarqueeControlRootDesigner`<xref:System.ComponentModel.Design.DesignerVerbCollection>kendi temel sınıfından bir devralır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-341">`MarqueeControlRootDesigner` inherits a <xref:System.ComponentModel.Design.DesignerVerbCollection> from its base class.</span></span> <span data-ttu-id="88f9a-342">İki yeni <xref:System.ComponentModel.Design.DesignerVerb> nesne oluşturacak ve bu koleksiyona, yöntemi içinde ekleyecek <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-342">You will create two new <xref:System.ComponentModel.Design.DesignerVerb> objects and add them to this collection in the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="create-a-custom-uitypeeditor"></a><span data-ttu-id="88f9a-343">Özel bir Uııtypeınfo Düzenleyicisi oluşturun</span><span class="sxs-lookup"><span data-stu-id="88f9a-343">Create a Custom UITypeEditor</span></span>

<span data-ttu-id="88f9a-344">Kullanıcılar için özel bir tasarım zamanı deneyimi oluşturduğunuzda, genellikle Özellikler penceresi özel bir etkileşim oluşturmak tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-344">When you create a custom design-time experience for users, it is often desirable to create a custom interaction with the Properties window.</span></span> <span data-ttu-id="88f9a-345">Bunu oluşturarak yapabilirsiniz <xref:System.Drawing.Design.UITypeEditor> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-345">You can accomplish this by creating a <xref:System.Drawing.Design.UITypeEditor>.</span></span>

<span data-ttu-id="88f9a-346">`MarqueeBorder`Denetim Özellikler penceresi çeşitli özellikleri kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="88f9a-346">The `MarqueeBorder` control exposes several properties in the Properties window.</span></span> <span data-ttu-id="88f9a-347">Bu özelliklerden ikisi `MarqueeSpinDirection` ve `MarqueeLightShape` numaralandırmalar tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-347">Two of these properties, `MarqueeSpinDirection` and `MarqueeLightShape` are represented by enumerations.</span></span> <span data-ttu-id="88f9a-348">Kullanıcı arabirimi türü düzenleyicisinin kullanımını göstermek için, `MarqueeLightShape` özelliği ilişkili bir sınıfa sahip olur <xref:System.Drawing.Design.UITypeEditor> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-348">To illustrate the use of a UI type editor, the `MarqueeLightShape` property will have an associated <xref:System.Drawing.Design.UITypeEditor> class.</span></span>

### <a name="to-create-a-custom-ui-type-editor"></a><span data-ttu-id="88f9a-349">Özel bir kullanıcı arabirimi tür Düzenleyicisi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="88f9a-349">To create a custom UI type editor</span></span>

1. <span data-ttu-id="88f9a-350">`MarqueeBorder`Kaynak dosyasını **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-350">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span>

2. <span data-ttu-id="88f9a-351">`MarqueeBorder`Sınıfının tanımında, öğesinden türetilen adlı bir sınıf bildirin `LightShapeEditor` <xref:System.Drawing.Design.UITypeEditor> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-351">In the definition of the `MarqueeBorder` class, declare a class called `LightShapeEditor` that derives from <xref:System.Drawing.Design.UITypeEditor>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. <span data-ttu-id="88f9a-352">Adlı bir <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> örnek değişkeni bildirin `editorService` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-352">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. <span data-ttu-id="88f9a-353">Yöntemini geçersiz kılın <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-353">Override the <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> method.</span></span> <span data-ttu-id="88f9a-354">Bu uygulama, <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown> tasarım ortamına nasıl görüntüleneceğini bildiren, öğesini döndürür `LightShapeEditor` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-354">This implementation returns <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, which tells the design environment how to display the `LightShapeEditor`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. <span data-ttu-id="88f9a-355">Yöntemini geçersiz kılın <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-355">Override the <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> method.</span></span> <span data-ttu-id="88f9a-356">Bu uygulama, bir nesnenin tasarım ortamını sorgular <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-356">This implementation queries the design environment for an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> object.</span></span> <span data-ttu-id="88f9a-357">Başarılı olursa, bir oluşturur `LightShapeSelectionControl` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-357">If successful, it creates a `LightShapeSelectionControl`.</span></span> <span data-ttu-id="88f9a-358"><xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A>Yöntemi başlatmak için çağrılır `LightShapeEditor` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-358">The <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> method is invoked to start the `LightShapeEditor`.</span></span> <span data-ttu-id="88f9a-359">Bu çağrıdan gelen dönüş değeri tasarım ortamına döndürülür.</span><span class="sxs-lookup"><span data-stu-id="88f9a-359">The return value from this invocation is returned to the design environment.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="create-a-view-control-for-your-custom-uitypeeditor"></a><span data-ttu-id="88f9a-360">Özel Uııtypeınfo Düzenleyicisi için bir görünüm denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="88f9a-360">Create a View Control for your Custom UITypeEditor</span></span>

<span data-ttu-id="88f9a-361">`MarqueeLightShape`Özelliği iki tür açık şekli destekler: `Square` ve `Circle` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-361">The `MarqueeLightShape` property supports two types of light shapes: `Square` and `Circle`.</span></span> <span data-ttu-id="88f9a-362">Yalnızca bu değerleri Özellikler penceresi grafik olarak görüntülemek için kullanılan özel bir denetim oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="88f9a-362">You will create a custom control used solely for the purpose of graphically displaying these values in the Properties window.</span></span> <span data-ttu-id="88f9a-363">Bu özel denetim <xref:System.Drawing.Design.UITypeEditor> , Özellikler penceresi etkileşimde bulunmak için sizin tarafınızdan kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-363">This custom control will be used by your <xref:System.Drawing.Design.UITypeEditor> to interact with the Properties window.</span></span>

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a><span data-ttu-id="88f9a-364">Özel UI türü düzenleyiciniz için bir görünüm denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="88f9a-364">To create a view control for your custom UI type editor</span></span>

1. <span data-ttu-id="88f9a-365">Projeye yeni bir <xref:System.Windows.Forms.UserControl> öğe ekleyin `MarqueeControlLibrary` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-365">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="88f9a-366">Yeni kaynak dosyasına, **Açık Shapeselectioncontrol**temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-366">Give the new source file a base name of **LightShapeSelectionControl**.</span></span>

2. <span data-ttu-id="88f9a-367"><xref:System.Windows.Forms.Panel> **Araç kutusundan** iki denetimi üzerine sürükleyin `LightShapeSelectionControl` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-367">Drag two <xref:System.Windows.Forms.Panel> controls from the **Toolbox** onto the `LightShapeSelectionControl`.</span></span> <span data-ttu-id="88f9a-368">Onları ve olarak adlandırın `squarePanel` `circlePanel` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-368">Name them `squarePanel` and `circlePanel`.</span></span> <span data-ttu-id="88f9a-369">Yan yana düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-369">Arrange them side by side.</span></span> <span data-ttu-id="88f9a-370"><xref:System.Windows.Forms.Control.Size%2A>Her iki <xref:System.Windows.Forms.Panel> denetimin özelliğini **(60, 60)** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-370">Set the <xref:System.Windows.Forms.Control.Size%2A> property of both <xref:System.Windows.Forms.Panel> controls to **(60, 60)**.</span></span> <span data-ttu-id="88f9a-371"><xref:System.Windows.Forms.Control.Location%2A> `squarePanel` Denetimin özelliğini **(8, 10)** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-371">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `squarePanel` control to **(8, 10)**.</span></span> <span data-ttu-id="88f9a-372"><xref:System.Windows.Forms.Control.Location%2A> `circlePanel` Denetimin özelliğini **(80, 10)** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-372">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `circlePanel` control to **(80, 10)**.</span></span> <span data-ttu-id="88f9a-373">Son olarak, <xref:System.Windows.Forms.Control.Size%2A> öğesinin özelliğini olarak ayarlayın `LightShapeSelectionControl` **(150, 80)**.</span><span class="sxs-lookup"><span data-stu-id="88f9a-373">Finally, set the <xref:System.Windows.Forms.Control.Size%2A> property of the `LightShapeSelectionControl` to **(150, 80)**.</span></span>

3. <span data-ttu-id="88f9a-374">`LightShapeSelectionControl`Kaynak dosyasını **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-374">Open the `LightShapeSelectionControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="88f9a-375">Dosyanın en üstünde, <xref:System.Windows.Forms.Design?displayProperty=nameWithType> ad alanını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="88f9a-375">At the top of the file, import the <xref:System.Windows.Forms.Design?displayProperty=nameWithType> namespace:</span></span>

   ```vb
   Imports System.Windows.Forms.Design
   ```

   ```csharp
   using System.Windows.Forms.Design;
   ```

4. <span data-ttu-id="88f9a-376"><xref:System.Windows.Forms.Control.Click>Ve denetimleri için olay işleyicileri `squarePanel` uygulayın `circlePanel` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-376">Implement <xref:System.Windows.Forms.Control.Click> event handlers for the `squarePanel` and `circlePanel` controls.</span></span> <span data-ttu-id="88f9a-377">Bu yöntemler <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> , özel Düzenle oturumunu sona erdirmek için çağırır <xref:System.Drawing.Design.UITypeEditor> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-377">These methods invoke <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> to end the custom <xref:System.Drawing.Design.UITypeEditor> editing session.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

5. <span data-ttu-id="88f9a-378">Adlı bir <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> örnek değişkeni bildirin `editorService` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-378">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

   ```vb
   Private editorService As IWindowsFormsEditorService
   ```

   ```csharp
   private IWindowsFormsEditorService editorService;
   ```

6. <span data-ttu-id="88f9a-379">Adlı bir `MarqueeLightShape` örnek değişkeni bildirin `lightShapeValue` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-379">Declare a `MarqueeLightShape` instance variable called `lightShapeValue`.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

7. <span data-ttu-id="88f9a-380">`LightShapeSelectionControl`Oluşturucuda, <xref:System.Windows.Forms.Control.Click> olay işleyicilerini `squarePanel` ve `circlePanel` denetimlerin <xref:System.Windows.Forms.Control.Click> olaylarına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-380">In the `LightShapeSelectionControl` constructor, attach the <xref:System.Windows.Forms.Control.Click> event handlers to the `squarePanel` and `circlePanel` controls' <xref:System.Windows.Forms.Control.Click> events.</span></span> <span data-ttu-id="88f9a-381">Ayrıca, `MarqueeLightShape` Tasarım ortamından alana değeri atayan bir Oluşturucu aşırı yüklemesi tanımlayın `lightShapeValue` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-381">Also, define a constructor overload that assigns the `MarqueeLightShape` value from the design environment to the `lightShapeValue` field.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

8. <span data-ttu-id="88f9a-382"><xref:System.ComponentModel.Component.Dispose%2A>Yönteminde <xref:System.Windows.Forms.Control.Click> olay işleyicilerini ayırın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-382">In the <xref:System.ComponentModel.Component.Dispose%2A> method, detach the <xref:System.Windows.Forms.Control.Click> event handlers.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

9. <span data-ttu-id="88f9a-383">**Çözüm Gezgini**, **tüm dosyaları göster** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-383">In **Solution Explorer**, click the **Show All Files** button.</span></span> <span data-ttu-id="88f9a-384">LightShapeSelectionControl.Designer.cs veya LightShapeSelectionControl. Designer. vb dosyasını açın ve yönteminin varsayılan tanımını kaldırın <xref:System.ComponentModel.Component.Dispose%2A> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-384">Open the LightShapeSelectionControl.Designer.cs or LightShapeSelectionControl.Designer.vb file, and remove the default definition of the <xref:System.ComponentModel.Component.Dispose%2A> method.</span></span>

10. <span data-ttu-id="88f9a-385">Özelliğini uygulayın `LightShape` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-385">Implement the `LightShape` property.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

11. <span data-ttu-id="88f9a-386">Yöntemini geçersiz kılın <xref:System.Windows.Forms.Control.OnPaint%2A> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-386">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="88f9a-387">Bu uygulama doldurulmuş bir kare ve daire çizecek.</span><span class="sxs-lookup"><span data-stu-id="88f9a-387">This implementation will draw a filled square and circle.</span></span> <span data-ttu-id="88f9a-388">Ayrıca, bir şekil ya da diğeri etrafında kenarlık çizerek seçili değeri vurgulayacaktır.</span><span class="sxs-lookup"><span data-stu-id="88f9a-388">It will also highlight the selected value by drawing a border around one shape or the other.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="test-your-custom-control-in-the-designer"></a><span data-ttu-id="88f9a-389">Tasarımcıda özel denetiminizi test etme</span><span class="sxs-lookup"><span data-stu-id="88f9a-389">Test your Custom Control in the Designer</span></span>

<span data-ttu-id="88f9a-390">Bu noktada, projeyi derleyebilirsiniz `MarqueeControlLibrary` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-390">At this point, you can build the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="88f9a-391">Sınıfından devralan bir denetim oluşturarak `MarqueeControl` ve onu bir formda kullanarak uygulamanızı test edin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-391">Test your implementation by creating a control that inherits from the `MarqueeControl` class and using it on a form.</span></span>

### <a name="to-create-a-custom-marqueecontrol-implementation"></a><span data-ttu-id="88f9a-392">Özel bir MarqueeControl uygulamasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="88f9a-392">To create a custom MarqueeControl implementation</span></span>

1. <span data-ttu-id="88f9a-393">`DemoMarqueeControl`Windows Form Tasarımcısı açın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-393">Open `DemoMarqueeControl` in the Windows Forms Designer.</span></span> <span data-ttu-id="88f9a-394">Bu, türün bir örneğini oluşturur `DemoMarqueeControl` ve türün bir örneğinde görüntüler `MarqueeControlRootDesigner` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-394">This creates an instance of the `DemoMarqueeControl` type and displays it in an instance of the `MarqueeControlRootDesigner` type.</span></span>

2. <span data-ttu-id="88f9a-395">**Araç kutusunda** **MarqueeControlLibrary Components** sekmesini açın. `MarqueeBorder` `MarqueeText` Seçim için kullanılabilir ve denetimleri görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="88f9a-395">In the **Toolbox**, open the **MarqueeControlLibrary Components** tab. You will see the `MarqueeBorder` and `MarqueeText` controls available for selection.</span></span>

3. <span data-ttu-id="88f9a-396">Denetimin bir örneğini `MarqueeBorder` `DemoMarqueeControl` tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-396">Drag an instance of the `MarqueeBorder` control onto the `DemoMarqueeControl` design surface.</span></span> <span data-ttu-id="88f9a-397">Bu `MarqueeBorder` denetimi üst denetime yerleştir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-397">Dock this `MarqueeBorder` control to the parent control.</span></span>

4. <span data-ttu-id="88f9a-398">Denetimin bir örneğini `MarqueeText` `DemoMarqueeControl` tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-398">Drag an instance of the `MarqueeText` control onto the `DemoMarqueeControl` design surface.</span></span>

5. <span data-ttu-id="88f9a-399">Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-399">Build the solution.</span></span>

6. <span data-ttu-id="88f9a-400">Sağ tıklayıp `DemoMarqueeControl` kısayol menüsünden, animasyonu başlatmak Için **Test Çalıştır** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-400">Right-click the `DemoMarqueeControl` and from the shortcut menu select the **Run Test** option to start the animation.</span></span> <span data-ttu-id="88f9a-401">Animasyonu durdurmak için **Sınamayı Durdur** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-401">Click **Stop Test** to stop the animation.</span></span>

7. <span data-ttu-id="88f9a-402">Tasarım görünümü 'da **Form1** ' i açın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-402">Open **Form1** in Design view.</span></span>

8. <span data-ttu-id="88f9a-403">Forma iki <xref:System.Windows.Forms.Button> Denetim koyun.</span><span class="sxs-lookup"><span data-stu-id="88f9a-403">Place two <xref:System.Windows.Forms.Button> controls on the form.</span></span> <span data-ttu-id="88f9a-404">Onları `startButton` ve `stopButton` olarak adlandırın ve <xref:System.Windows.Forms.Control.Text%2A> sırasıyla **Başlangıç** ve **durdurma**özelliği değerlerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-404">Name them `startButton` and `stopButton`, and change the <xref:System.Windows.Forms.Control.Text%2A> property values to **Start** and **Stop**, respectively.</span></span>

9. <span data-ttu-id="88f9a-405"><xref:System.Windows.Forms.Control.Click>Her iki denetim için de olay işleyicileri uygulayın <xref:System.Windows.Forms.Button> .</span><span class="sxs-lookup"><span data-stu-id="88f9a-405">Implement <xref:System.Windows.Forms.Control.Click> event handlers for both <xref:System.Windows.Forms.Button> controls.</span></span>

10. <span data-ttu-id="88f9a-406">**Araç kutusunda** **MarqueeControlTest Components** sekmesini açın. `DemoMarqueeControl`Seçim için kullanılabilir seçeneğini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="88f9a-406">In the **Toolbox**, open the **MarqueeControlTest Components** tab. You will see the `DemoMarqueeControl` available for selection.</span></span>

11. <span data-ttu-id="88f9a-407">Bir örneğini `DemoMarqueeControl` **Form1** tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-407">Drag an instance of `DemoMarqueeControl` onto the **Form1** design surface.</span></span>

12. <span data-ttu-id="88f9a-408"><xref:System.Windows.Forms.Control.Click>Olay işleyicilerinde, `Start` ve `Stop` üzerindeki yöntemlerini çağırın `DemoMarqueeControl` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-408">In the <xref:System.Windows.Forms.Control.Click> event handlers, invoke the `Start` and `Stop` methods on the `DemoMarqueeControl`.</span></span>

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

13. <span data-ttu-id="88f9a-409">`MarqueeControlTest`Projeyi başlangıç projesi olarak ayarlayın ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="88f9a-409">Set the `MarqueeControlTest` project as the startup project and run it.</span></span> <span data-ttu-id="88f9a-410">Formunu görüntüleyen formu görürsünüz `DemoMarqueeControl` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-410">You will see the form displaying your `DemoMarqueeControl`.</span></span> <span data-ttu-id="88f9a-411">Animasyonu başlatmak için **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-411">Select the **Start** button to start the animation.</span></span> <span data-ttu-id="88f9a-412">Metnin yanıp sönmesi ve kenarlığın etrafında hareket eden ışıklar görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-412">You should see the text flashing and the lights moving around the border.</span></span>

## <a name="next-steps"></a><span data-ttu-id="88f9a-413">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="88f9a-413">Next steps</span></span>

<span data-ttu-id="88f9a-414">, `MarqueeControlLibrary` Özel denetimlerin ve ilişkili tasarımcılarının basit bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="88f9a-414">The `MarqueeControlLibrary` demonstrates a simple implementation of custom controls and associated designers.</span></span> <span data-ttu-id="88f9a-415">Bu örneği çeşitli yollarla daha karmaşık hale getirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="88f9a-415">You can make this sample more sophisticated in several ways:</span></span>

- <span data-ttu-id="88f9a-416">Tasarımcı içindeki için özellik değerlerini değiştirin `DemoMarqueeControl` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-416">Change the property values for the `DemoMarqueeControl` in the designer.</span></span> <span data-ttu-id="88f9a-417">Daha fazla `MarqueBorder` denetim ekleyin ve iç içe geçmiş bir efekt oluşturmak için bunları üst örnekleri içine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-417">Add more `MarqueBorder` controls and dock them within their parent instances to create a nested effect.</span></span> <span data-ttu-id="88f9a-418">Ve ışığıyla ilgili özellikler için farklı ayarlarla denemeler yapın `UpdatePeriod` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-418">Experiment with different settings for the `UpdatePeriod` and the light-related properties.</span></span>

- <span data-ttu-id="88f9a-419">Kendi uygulamalarınızı yazar `IMarqueeWidget` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-419">Author your own implementations of `IMarqueeWidget`.</span></span> <span data-ttu-id="88f9a-420">Örneğin, yanıp sönen bir "Neon Sign" veya birden çok görüntüde animasyonlu bir işaret oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88f9a-420">You could, for example, create a flashing "neon sign" or an animated sign with multiple images.</span></span>

- <span data-ttu-id="88f9a-421">Tasarım zamanı deneyimini daha da özelleştirin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-421">Further customize the design-time experience.</span></span> <span data-ttu-id="88f9a-422">Ve ' den daha fazla özelliği gölgelendirmeyi <xref:System.Windows.Forms.Control.Enabled%2A> deneyebilirsiniz <xref:System.Windows.Forms.Control.Visible%2A> ve yeni özellikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88f9a-422">You could try shadowing more properties than <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A>, and you could add new properties.</span></span> <span data-ttu-id="88f9a-423">Alt öğe denetimleri yerleştirme gibi yaygın görevleri basitleştirmek için yeni tasarımcı fiilleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-423">Add new designer verbs to simplify common tasks like docking child controls.</span></span>

- <span data-ttu-id="88f9a-424">Lisansına sahip `MarqueeControl` .</span><span class="sxs-lookup"><span data-stu-id="88f9a-424">License the `MarqueeControl`.</span></span>

- <span data-ttu-id="88f9a-425">Denetimlerinizin serileştirilme şeklini ve kodun onlar için nasıl oluşturulduğunu denetleyin.</span><span class="sxs-lookup"><span data-stu-id="88f9a-425">Control how your controls are serialized and how code is generated for them.</span></span> <span data-ttu-id="88f9a-426">Daha fazla bilgi için bkz. [dinamik kaynak kodu oluşturma ve derleme](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="88f9a-426">For more information, see [Dynamic Source Code Generation and Compilation](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="88f9a-427">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88f9a-427">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
