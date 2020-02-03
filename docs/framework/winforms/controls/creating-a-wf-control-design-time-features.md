---
title: Visual Studio tasarım zamanı özelliklerinden faydalanan bir denetim oluşturma
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
ms.openlocfilehash: 7166b4203c54ab31f1d929c85cf1e6481ff120f8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744083"
---
# <a name="walkthrough-create-a-control-that-takes-advantage-of-design-time-features"></a><span data-ttu-id="c3035-102">İzlenecek yol: tasarım zamanı özelliklerinden faydalanan bir denetim oluşturma</span><span class="sxs-lookup"><span data-stu-id="c3035-102">Walkthrough: Create a control that takes advantage of design-time features</span></span>

<span data-ttu-id="c3035-103">Özel bir denetim için tasarım zamanı deneyimi, ilişkili bir özel tasarımcı Authoring ile geliştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c3035-103">The design-time experience for a custom control can be enhanced by authoring an associated custom designer.</span></span>

<span data-ttu-id="c3035-104">Bu makalede özel bir denetim için nasıl özel tasarımcı oluşturacağınız açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c3035-104">This article illustrates how to create a custom designer for a custom control.</span></span> <span data-ttu-id="c3035-105">`MarqueeControl` bir türü ve `MarqueeControlRootDesigner`adlı ilişkili tasarımcı sınıfını uygulayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c3035-105">You'll implement a `MarqueeControl` type and an associated designer class called `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="c3035-106">`MarqueeControl` türü, animasyonlu ışıklar ve yanıp sönen metinle benzer bir tiyatro çerçevesine benzer bir ekran uygular.</span><span class="sxs-lookup"><span data-stu-id="c3035-106">The `MarqueeControl` type implements a display similar to a theater marquee with animated lights and flashing text.</span></span>

<span data-ttu-id="c3035-107">Bu denetim için tasarımcı, tasarım ortamıyla birlikte etkileşimde bulunur ve özel bir tasarım zamanı deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3035-107">The designer for this control interacts with the design environment to provide a custom design-time experience.</span></span> <span data-ttu-id="c3035-108">Özel tasarımcı sayesinde, bir özel `MarqueeControl` uygulamasını animasyonlu ışıklar ve yanıp sönen metni birçok birleşimde bir araya getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3035-108">With the custom designer, you can assemble a custom `MarqueeControl` implementation with animated lights and flashing text in many combinations.</span></span> <span data-ttu-id="c3035-109">Bir form üzerinde, diğer Windows Forms denetimleri gibi, birleştirilmiş denetimi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3035-109">You can use the assembled control on a form like any other Windows Forms control.</span></span>

<span data-ttu-id="c3035-110">Bu yönergeyi tamamladığınızda, özel denetiminiz aşağıdakine benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="c3035-110">When you're finished with this walkthrough, your custom control will look something like the following:</span></span>

![Metin ve Başlat ve Durdur düğmelerini gösteren bir kayan yazıyı gösteren uygulama.](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

<span data-ttu-id="c3035-112">Tam kod listesi için, bkz. [nasıl yapılır: tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="c3035-112">For the complete code listing, see [How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c3035-113">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="c3035-113">Prerequisites</span></span>

<span data-ttu-id="c3035-114">Bu izlenecek yolu tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3035-114">In order to complete this walkthrough, you'll need Visual Studio.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="c3035-115">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c3035-115">Create the project</span></span>

<span data-ttu-id="c3035-116">İlk adım uygulama projesini oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="c3035-116">The first step is to create the application project.</span></span> <span data-ttu-id="c3035-117">Bu projeyi, özel denetimi barındıran uygulamayı oluşturmak için kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c3035-117">You will use this project to build the application that hosts the custom control.</span></span>

<span data-ttu-id="c3035-118">Visual Studio 'da yeni bir Windows Forms uygulama projesi oluşturun ve **MarqueeControlTest**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="c3035-118">In Visual Studio, create a new Windows Forms Application project, and name it **MarqueeControlTest**.</span></span>

## <a name="create-the-control-library-project"></a><span data-ttu-id="c3035-119">Denetim kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c3035-119">Create the control library project</span></span>

1. <span data-ttu-id="c3035-120">Çözüme bir Windows Forms denetim kitaplığı projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-120">Add a Windows Forms Control Library project to the solution.</span></span> <span data-ttu-id="c3035-121">Projeyi **MarqueeControlLibrary**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="c3035-121">Name the project **MarqueeControlLibrary**.</span></span>

2. <span data-ttu-id="c3035-122">**Çözüm Gezgini**kullanarak, tercih ettiğiniz dile bağlı olarak, "UserControl1.cs" veya "UserControl1. vb" adlı kaynak dosyayı silerek projenin varsayılan denetimini silin.</span><span class="sxs-lookup"><span data-stu-id="c3035-122">Using **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span>

3. <span data-ttu-id="c3035-123">`MarqueeControlLibrary` projesine yeni bir <xref:System.Windows.Forms.UserControl> öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-123">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="c3035-124">Yeni kaynak dosyasına **MarqueeControl**temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="c3035-124">Give the new source file a base name of **MarqueeControl**.</span></span>

4. <span data-ttu-id="c3035-125">**Çözüm Gezgini**kullanarak, `MarqueeControlLibrary` projesinde yeni bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c3035-125">Using **Solution Explorer**, create a new folder in the `MarqueeControlLibrary` project.</span></span>

5. <span data-ttu-id="c3035-126">**Tasarım** klasörüne sağ tıklayın ve yeni bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-126">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="c3035-127">**MarqueeControlRootDesigner**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="c3035-127">Name it **MarqueeControlRootDesigner**.</span></span>

6. <span data-ttu-id="c3035-128">System. Design derlemesinden türler kullanmanız gerekir, bu nedenle bu başvuruyu `MarqueeControlLibrary` projesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-128">You'll need to use types from the System.Design assembly, so add this reference to the `MarqueeControlLibrary` project.</span></span>

## <a name="reference-the-custom-control-project"></a><span data-ttu-id="c3035-129">Özel denetim projesine başvur</span><span class="sxs-lookup"><span data-stu-id="c3035-129">Reference the Custom Control Project</span></span>

<span data-ttu-id="c3035-130">Özel denetimi test etmek için `MarqueeControlTest` projesi kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c3035-130">You will use the `MarqueeControlTest` project to test the custom control.</span></span> <span data-ttu-id="c3035-131">`MarqueeControlLibrary` derlemesine bir proje başvurusu eklediğinizde test projesi özel denetimden haberdar olur.</span><span class="sxs-lookup"><span data-stu-id="c3035-131">The test project will become aware of the custom control when you add a project reference to the `MarqueeControlLibrary` assembly.</span></span>

<span data-ttu-id="c3035-132">`MarqueeControlTest` projesinde, `MarqueeControlLibrary` derlemesine bir proje başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-132">In the `MarqueeControlTest` project, add a project reference to the `MarqueeControlLibrary` assembly.</span></span> <span data-ttu-id="c3035-133">`MarqueeControlLibrary` derlemesine doğrudan başvurmak yerine **Başvuru Ekle** Iletişim kutusundaki **Projeler** sekmesini kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c3035-133">Be sure to use the **Projects** tab in the **Add Reference** dialog box instead of referencing the `MarqueeControlLibrary` assembly directly.</span></span>

## <a name="define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="c3035-134">Özel bir denetim ve kendi özel tasarımcısını tanımlama</span><span class="sxs-lookup"><span data-stu-id="c3035-134">Define a Custom Control and Its Custom Designer</span></span>

<span data-ttu-id="c3035-135">Özel denetiminiz <xref:System.Windows.Forms.UserControl> sınıfından türecektir.</span><span class="sxs-lookup"><span data-stu-id="c3035-135">Your custom control will derive from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="c3035-136">Bu, denetiminizin diğer denetimleri içermesini sağlar ve denetimi, varsayılan işlevselliğin harika olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3035-136">This allows your control to contain other controls, and it gives your control a great deal of default functionality.</span></span>

<span data-ttu-id="c3035-137">Özel denetiminizin ilişkili bir özel Tasarımcısı olacak.</span><span class="sxs-lookup"><span data-stu-id="c3035-137">Your custom control will have an associated custom designer.</span></span> <span data-ttu-id="c3035-138">Bu, özel denetiminiz için özel olarak uyarlanmış benzersiz bir tasarım deneyimi oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3035-138">This allows you to create a unique design experience tailored specifically for your custom control.</span></span>

<span data-ttu-id="c3035-139"><xref:System.ComponentModel.DesignerAttribute> sınıfını kullanarak denetimi Tasarımcı ile ilişkilendirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3035-139">You associate the control with its designer by using the <xref:System.ComponentModel.DesignerAttribute> class.</span></span> <span data-ttu-id="c3035-140">Özel denetiminizin tüm tasarım zamanı davranışını geliştirmekte olduğunuzdan, özel tasarımcı <xref:System.ComponentModel.Design.IRootDesigner> arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="c3035-140">Because you are developing the entire design-time behavior of your custom control, the custom designer will implement the <xref:System.ComponentModel.Design.IRootDesigner> interface.</span></span>

### <a name="to-define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="c3035-141">Özel bir denetim ve özel tasarımcı tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="c3035-141">To define a custom control and its custom designer</span></span>

1. <span data-ttu-id="c3035-142">`MarqueeControl` kaynak dosyasını **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="c3035-142">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="c3035-143">Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="c3035-143">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. <span data-ttu-id="c3035-144">`MarqueeControl` sınıfı bildirimine <xref:System.ComponentModel.DesignerAttribute> ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-144">Add the <xref:System.ComponentModel.DesignerAttribute> to the `MarqueeControl` class declaration.</span></span> <span data-ttu-id="c3035-145">Bu, özel denetimi Tasarımcı ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="c3035-145">This associates the custom control with its designer.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. <span data-ttu-id="c3035-146">`MarqueeControlRootDesigner` kaynak dosyasını **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="c3035-146">Open the `MarqueeControlRootDesigner` source file in the **Code Editor**.</span></span> <span data-ttu-id="c3035-147">Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="c3035-147">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. <span data-ttu-id="c3035-148">`MarqueeControlRootDesigner` bildirimini <xref:System.Windows.Forms.Design.DocumentDesigner> sınıfından devralacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c3035-148">Change the declaration of `MarqueeControlRootDesigner` to inherit from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="c3035-149">**Araç kutusu**ile tasarımcı etkileşimini belirtmek için <xref:System.ComponentModel.ToolboxItemFilterAttribute> uygulayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-149">Apply the <xref:System.ComponentModel.ToolboxItemFilterAttribute> to specify the designer interaction with the **Toolbox**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="c3035-150">`MarqueeControlRootDesigner` sınıfının tanımı, MarqueeControlLibrary. Design adlı bir ad alanı içine alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="c3035-150">The definition for the `MarqueeControlRootDesigner` class has been enclosed in a namespace called MarqueeControlLibrary.Design.</span></span> <span data-ttu-id="c3035-151">Bu bildirim, tasarımcıyı tasarımla ilgili türler için ayrılmış özel bir ad alanına koyar.</span><span class="sxs-lookup"><span data-stu-id="c3035-151">This declaration places the designer in a special namespace reserved for design-related types.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. <span data-ttu-id="c3035-152">`MarqueeControlRootDesigner` sınıfı için oluşturucuyu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-152">Define the constructor for the `MarqueeControlRootDesigner` class.</span></span> <span data-ttu-id="c3035-153">Oluşturucu gövdesine <xref:System.Diagnostics.Trace.WriteLine%2A> bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-153">Insert a <xref:System.Diagnostics.Trace.WriteLine%2A> statement in the constructor body.</span></span> <span data-ttu-id="c3035-154">Bu, hata ayıklama için yararlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c3035-154">This will be useful for debugging.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="create-an-instance-of-your-custom-control"></a><span data-ttu-id="c3035-155">Özel denetiminizin bir örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="c3035-155">Create an instance of your custom control</span></span>

1. <span data-ttu-id="c3035-156">`MarqueeControlTest` projesine yeni bir <xref:System.Windows.Forms.UserControl> öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-156">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlTest` project.</span></span> <span data-ttu-id="c3035-157">Yeni kaynak dosyasına **DemoMarqueeControl**temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="c3035-157">Give the new source file a base name of **DemoMarqueeControl**.</span></span>

2. <span data-ttu-id="c3035-158">**Kod düzenleyicisinde**`DemoMarqueeControl` dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="c3035-158">Open the `DemoMarqueeControl` file in the **Code Editor**.</span></span> <span data-ttu-id="c3035-159">Dosyanın en üstüne `MarqueeControlLibrary` ad alanını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="c3035-159">At the top of the file, import the `MarqueeControlLibrary` namespace:</span></span>

   ```vb
   Imports MarqueeControlLibrary
   ```

   ```csharp
   using MarqueeControlLibrary;
   ```

3. <span data-ttu-id="c3035-160">`DemoMarqueeControl` bildirimini `MarqueeControl` sınıfından devralacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c3035-160">Change the declaration of `DemoMarqueeControl` to inherit from the `MarqueeControl` class.</span></span>

4. <span data-ttu-id="c3035-161">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c3035-161">Build the project.</span></span>

5. <span data-ttu-id="c3035-162">Windows Form Tasarımcısı Form1 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="c3035-162">Open Form1 in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="c3035-163">**Araç kutusunda** **MarqueeControlTest Components** sekmesini bulun ve açın.</span><span class="sxs-lookup"><span data-stu-id="c3035-163">Find the **MarqueeControlTest Components** tab in the **Toolbox** and open it.</span></span> <span data-ttu-id="c3035-164">**Araç kutusundan** bir `DemoMarqueeControl` form üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-164">Drag a `DemoMarqueeControl` from the **Toolbox** onto your form.</span></span>

7. <span data-ttu-id="c3035-165">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c3035-165">Build the project.</span></span>

## <a name="set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="c3035-166">Projeyi tasarım zamanı hata ayıklama için ayarlama</span><span class="sxs-lookup"><span data-stu-id="c3035-166">Set Up the Project for Design-Time Debugging</span></span>

<span data-ttu-id="c3035-167">Özel bir tasarım zamanı deneyimi geliştirirken, denetimlerinizin ve bileşenlerinizin hata ayıklaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3035-167">When you're developing a custom design-time experience, it will be necessary to debug your controls and components.</span></span> <span data-ttu-id="c3035-168">Projenizi tasarım zamanında hata ayıklamaya izin verecek şekilde kurmak için basit bir yol vardır.</span><span class="sxs-lookup"><span data-stu-id="c3035-168">There is a simple way to set up your project to allow debugging at design time.</span></span> <span data-ttu-id="c3035-169">Daha fazla bilgi için bkz. [Izlenecek yol: tasarım zamanında özel Windows Forms Denetimlerinde hata ayıklama](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="c3035-169">For more information, see [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>

1. <span data-ttu-id="c3035-170">`MarqueeControlLibrary` projesine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="c3035-170">Right-click the `MarqueeControlLibrary` project and select **Properties**.</span></span>

2. <span data-ttu-id="c3035-171">**MarqueeControlLibrary Özellik sayfaları** Iletişim kutusunda **hata ayıklama** sayfasını seçin.</span><span class="sxs-lookup"><span data-stu-id="c3035-171">In the **MarqueeControlLibrary Property Pages** dialog box, select the **Debug** page.</span></span>

3. <span data-ttu-id="c3035-172">**Başlangıç eylemi** bölümünde **dış program Başlat**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="c3035-172">In the **Start Action** section, select **Start External Program**.</span></span> <span data-ttu-id="c3035-173">Visual Studio 'nun ayrı bir örneğinde hata ayıkladığınızda, Visual Studio IDE 'ye gözatabilmek için üç nokta (Visual](./media/visual-studio-ellipsis-button.png)Studio 'nun Özellikler penceresi![) düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="c3035-173">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="c3035-174">Yürütülebilir dosyanın adı devenv. exe ' dir ve varsayılan konuma yüklediyseniz, yolu *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\\\<edition > \Common7\IDE\devenv.exe*olur.</span><span class="sxs-lookup"><span data-stu-id="c3035-174">The name of the executable file is devenv.exe, and if you installed to the default location, its path is *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\\\<edition>\Common7\IDE\devenv.exe*.</span></span>

4. <span data-ttu-id="c3035-175">İletişim kutusunu kapatmak için **Tamam ' ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="c3035-175">Select **OK** to close the dialog box.</span></span>

5. <span data-ttu-id="c3035-176">Bu hata ayıklama yapılandırmasını etkinleştirmek için MarqueeControlLibrary projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="c3035-176">Right-click the MarqueeControlLibrary project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>

## <a name="checkpoint"></a><span data-ttu-id="c3035-177">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="c3035-177">Checkpoint</span></span>

<span data-ttu-id="c3035-178">Artık özel denetiminizin tasarım zamanı davranışını hata ayıklamaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="c3035-178">You are now ready to debug the design-time behavior of your custom control.</span></span> <span data-ttu-id="c3035-179">Hata ayıklama ortamının doğru şekilde ayarlandığını belirledikten sonra, özel denetim ve özel tasarımcı arasındaki ilişkilendirmeyi test edersiniz.</span><span class="sxs-lookup"><span data-stu-id="c3035-179">Once you've determined that the debugging environment is set up correctly, you'll test the association between the custom control and the custom designer.</span></span>

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a><span data-ttu-id="c3035-180">Hata ayıklama ortamını ve tasarımcı ilişkilendirmesini test etmek için</span><span class="sxs-lookup"><span data-stu-id="c3035-180">To test the debugging environment and the designer association</span></span>

1. <span data-ttu-id="c3035-181">**Kod düzenleyicisinde** MarqueeControlRootDesigner kaynak dosyasını açın ve <xref:System.Diagnostics.Trace.WriteLine%2A> ifadesine bir kesme noktası yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c3035-181">Open the MarqueeControlRootDesigner source file in the **Code Editor** and place a breakpoint on the <xref:System.Diagnostics.Trace.WriteLine%2A> statement.</span></span>

2. <span data-ttu-id="c3035-182">Hata ayıklama oturumu başlatmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c3035-182">Press **F5** to start the debugging session.</span></span>

   <span data-ttu-id="c3035-183">Visual Studio 'nun yeni bir örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c3035-183">A new instance of Visual Studio is created.</span></span>

3. <span data-ttu-id="c3035-184">Visual Studio 'nun yeni örneğinde, MarqueeControlTest çözümünü açın.</span><span class="sxs-lookup"><span data-stu-id="c3035-184">In the new instance of Visual Studio, open the MarqueeControlTest solution.</span></span> <span data-ttu-id="c3035-185">**Dosya** menüsünden **son projeler** ' i seçerek çözümü kolayca bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3035-185">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="c3035-186">MarqueeControlTest. sln çözüm dosyası en son kullanılan dosya olarak listelenecektir.</span><span class="sxs-lookup"><span data-stu-id="c3035-186">The MarqueeControlTest.sln solution file will be listed as the most recently used file.</span></span>

4. <span data-ttu-id="c3035-187">Tasarımcıda `DemoMarqueeControl` açın.</span><span class="sxs-lookup"><span data-stu-id="c3035-187">Open the `DemoMarqueeControl` in the designer.</span></span>

   <span data-ttu-id="c3035-188">Visual Studio 'nun hata ayıklama örneği, kesme noktasında odak ve yürütme işlemini alır.</span><span class="sxs-lookup"><span data-stu-id="c3035-188">The debugging instance of Visual Studio obtains focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="c3035-189">Hata ayıklama oturumuna devam etmek için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c3035-189">Press **F5** to continue the debugging session.</span></span>

<span data-ttu-id="c3035-190">Bu noktada, özel denetiminizi ve onunla ilişkili özel tasarımcıyı geliştirip hata ayıklamanızın her şey vardır.</span><span class="sxs-lookup"><span data-stu-id="c3035-190">At this point, everything is in place for you to develop and debug your custom control and its associated custom designer.</span></span> <span data-ttu-id="c3035-191">Bu makalenin geri kalanında, denetimin ve tasarımcının özelliklerini uygulama ayrıntılarına yoğunlaşmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c3035-191">The remainder of this article concentrates on the details of implementing features of the control and the designer.</span></span>

## <a name="implement-the-custom-control"></a><span data-ttu-id="c3035-192">Özel denetimi uygulama</span><span class="sxs-lookup"><span data-stu-id="c3035-192">Implement the Custom Control</span></span>

<span data-ttu-id="c3035-193">`MarqueeControl`, çok sayıda özelleştirmeye sahip bir <xref:System.Windows.Forms.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="c3035-193">The `MarqueeControl` is a <xref:System.Windows.Forms.UserControl> with a little bit of customization.</span></span> <span data-ttu-id="c3035-194">İki yöntem sunar: kayan yazı animasyonunu Başlatan `Start`ve animasyonu durduran `Stop`.</span><span class="sxs-lookup"><span data-stu-id="c3035-194">It exposes two methods: `Start`, which starts the marquee animation, and `Stop`, which stops the animation.</span></span> <span data-ttu-id="c3035-195">`MarqueeControl`, `IMarqueeWidget` arabirimini uygulayan alt denetimler içerdiğinden, her bir alt denetimi `Start` ve `StartMarquee` uygulayan her bir alt denetimde sırasıyla `StopMarquee` ve `IMarqueeWidget`yöntemlerini çağıran `Stop`.</span><span class="sxs-lookup"><span data-stu-id="c3035-195">Because the `MarqueeControl` contains child controls that implement the `IMarqueeWidget` interface, `Start` and `Stop` enumerate each child control and call the `StartMarquee` and `StopMarquee` methods, respectively, on each child control that implements `IMarqueeWidget`.</span></span>

<span data-ttu-id="c3035-196">`MarqueeBorder` ve `MarqueeText` denetimlerinin görünümü düzene bağlıdır, bu nedenle `MarqueeControl` <xref:System.Windows.Forms.Control.OnLayout%2A> yöntemini geçersiz kılar ve bu türün alt denetimlerinde <xref:System.Windows.Forms.Control.PerformLayout%2A> çağırır.</span><span class="sxs-lookup"><span data-stu-id="c3035-196">The appearance of the `MarqueeBorder` and `MarqueeText` controls is dependent on the layout, so `MarqueeControl` overrides the <xref:System.Windows.Forms.Control.OnLayout%2A> method and calls <xref:System.Windows.Forms.Control.PerformLayout%2A> on child controls of this type.</span></span>

<span data-ttu-id="c3035-197">Bu, `MarqueeControl` özelleştirmelerin bir kapsamını.</span><span class="sxs-lookup"><span data-stu-id="c3035-197">This is the extent of the `MarqueeControl` customizations.</span></span> <span data-ttu-id="c3035-198">Çalışma zamanı özellikleri `MarqueeBorder` ve `MarqueeText` denetimleri tarafından uygulanır ve tasarım zamanı özellikleri `MarqueeBorderDesigner` ve `MarqueeControlRootDesigner` sınıfları tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c3035-198">The run-time features are implemented by the `MarqueeBorder` and `MarqueeText` controls, and the design-time features are implemented by the `MarqueeBorderDesigner` and `MarqueeControlRootDesigner` classes.</span></span>

### <a name="to-implement-your-custom-control"></a><span data-ttu-id="c3035-199">Özel denetiminizi uygulamak için</span><span class="sxs-lookup"><span data-stu-id="c3035-199">To implement your custom control</span></span>

1. <span data-ttu-id="c3035-200">`MarqueeControl` kaynak dosyasını **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="c3035-200">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="c3035-201">`Start` ve `Stop` yöntemlerini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-201">Implement the `Start` and `Stop` methods.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. <span data-ttu-id="c3035-202"><xref:System.Windows.Forms.Control.OnLayout%2A> yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="c3035-202">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="create-a-child-control-for-your-custom-control"></a><span data-ttu-id="c3035-203">Özel denetiminiz için bir alt denetim oluşturma</span><span class="sxs-lookup"><span data-stu-id="c3035-203">Create a Child Control for Your Custom Control</span></span>

<span data-ttu-id="c3035-204">`MarqueeControl` iki tür alt denetimi barındırır: `MarqueeBorder` denetimi ve `MarqueeText` denetimi.</span><span class="sxs-lookup"><span data-stu-id="c3035-204">The `MarqueeControl` will host two kinds of child control: the `MarqueeBorder` control and the `MarqueeText` control.</span></span>

- <span data-ttu-id="c3035-205">`MarqueeBorder`: Bu denetim, kenarları etrafında "ışıklar" kenarlığını boyar.</span><span class="sxs-lookup"><span data-stu-id="c3035-205">`MarqueeBorder`: This control paints a border of "lights" around its edges.</span></span> <span data-ttu-id="c3035-206">Kenarlıkta bulunan ışıklar, kenarlık etrafında taşınıyor gibi görünürler.</span><span class="sxs-lookup"><span data-stu-id="c3035-206">The lights flash in sequence, so they appear to be moving around the border.</span></span> <span data-ttu-id="c3035-207">Işıklarının flaşın `UpdatePeriod`adlı bir özellik tarafından denetlenme hızı.</span><span class="sxs-lookup"><span data-stu-id="c3035-207">The speed at which the lights flash is controlled by a property called `UpdatePeriod`.</span></span> <span data-ttu-id="c3035-208">Diğer birçok özel özellik, denetimin görünümünün diğer yönlerini tespit.</span><span class="sxs-lookup"><span data-stu-id="c3035-208">Several other custom properties determine other aspects of the control's appearance.</span></span> <span data-ttu-id="c3035-209">`StartMarquee` ve `StopMarquee`olarak adlandırılan iki yöntem animasyonun ne zaman başlayacağını ve durdurduğunu denetler.</span><span class="sxs-lookup"><span data-stu-id="c3035-209">Two methods, called `StartMarquee` and `StopMarquee`, control when the animation starts and stops.</span></span>

- <span data-ttu-id="c3035-210">`MarqueeText`: Bu denetim yanıp sönen bir dizeyi boyar.</span><span class="sxs-lookup"><span data-stu-id="c3035-210">`MarqueeText`: This control paints a flashing string.</span></span> <span data-ttu-id="c3035-211">`MarqueeBorder` denetimi gibi, metnin yanıp sönebileceği hız, `UpdatePeriod` özelliği tarafından kontrol edilir.</span><span class="sxs-lookup"><span data-stu-id="c3035-211">Like the `MarqueeBorder` control, the speed at which the text flashes is controlled by the `UpdatePeriod` property.</span></span> <span data-ttu-id="c3035-212">`MarqueeText` denetimde Ayrıca, `MarqueeBorder` denetimiyle ortak olan `StartMarquee` ve `StopMarquee` yöntemleri de vardır.</span><span class="sxs-lookup"><span data-stu-id="c3035-212">The `MarqueeText` control also has the `StartMarquee` and `StopMarquee` methods in common with the `MarqueeBorder` control.</span></span>

<span data-ttu-id="c3035-213">Tasarım zamanında `MarqueeControlRootDesigner`, bu iki denetim türünün herhangi bir kombinasyondaki bir `MarqueeControl` eklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="c3035-213">At design time, the `MarqueeControlRootDesigner` allows these two control types to be added to a `MarqueeControl` in any combination.</span></span>

<span data-ttu-id="c3035-214">İki denetimin ortak özellikleri, `IMarqueeWidget`adlı bir arabirimle birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c3035-214">Common features of the two controls are factored into an interface called `IMarqueeWidget`.</span></span> <span data-ttu-id="c3035-215">Bu, `MarqueeControl` tüm seçim çerçevesine ilişkin alt denetimleri bulmasını ve özel bir işleme sunmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3035-215">This allows the `MarqueeControl` to discover any Marquee-related child controls and give them special treatment.</span></span>

<span data-ttu-id="c3035-216">Düzenli animasyon özelliğini uygulamak için, <xref:System.ComponentModel?displayProperty=nameWithType> ad alanındaki <xref:System.ComponentModel.BackgroundWorker> nesneleri kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c3035-216">To implement the periodic animation feature, you will use <xref:System.ComponentModel.BackgroundWorker> objects from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c3035-217"><xref:System.Windows.Forms.Timer> nesneleri kullanabilirsiniz, ancak birçok `IMarqueeWidget` nesnesi mevcut olduğunda, tek kullanıcı arabirimi iş parçacığı animasyonla devam edemiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="c3035-217">You could use <xref:System.Windows.Forms.Timer> objects, but when many `IMarqueeWidget` objects are present, the single UI thread may be unable to keep up with the animation.</span></span>

### <a name="to-create-a-child-control-for-your-custom-control"></a><span data-ttu-id="c3035-218">Özel denetiminiz için bir alt denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c3035-218">To create a child control for your custom control</span></span>

1. <span data-ttu-id="c3035-219">`MarqueeControlLibrary` projesine yeni bir sınıf öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-219">Add a new class item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="c3035-220">Yeni kaynak dosyasına "Imarqueepencere öğesi" için temel adı verin.</span><span class="sxs-lookup"><span data-stu-id="c3035-220">Give the new source file a base name of "IMarqueeWidget."</span></span>

2. <span data-ttu-id="c3035-221">**Kod düzenleyicisinde** `IMarqueeWidget` kaynak dosyasını açın ve `class` bildirimi `interface`olarak değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c3035-221">Open the `IMarqueeWidget` source file in the **Code Editor** and change the declaration from `class` to `interface`:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. <span data-ttu-id="c3035-222">İki yöntemi ve kayan yazı animasyonunu işleyen bir özelliği göstermek için `IMarqueeWidget` arabirimine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c3035-222">Add the following code to the `IMarqueeWidget` interface to expose two methods and a property that manipulate the marquee animation:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. <span data-ttu-id="c3035-223">`MarqueeControlLibrary` projesine yeni bir **özel denetim** öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-223">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="c3035-224">Yeni kaynak dosyasına "MarqueeText" temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="c3035-224">Give the new source file a base name of "MarqueeText."</span></span>

5. <span data-ttu-id="c3035-225">**Araç kutusundan** bir <xref:System.ComponentModel.BackgroundWorker> bileşenini `MarqueeText` denetimine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-225">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeText` control.</span></span> <span data-ttu-id="c3035-226">Bu bileşen `MarqueeText` denetiminin kendisini zaman uyumsuz olarak güncelleştirmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="c3035-226">This component will allow the `MarqueeText` control to update itself asynchronously.</span></span>

6. <span data-ttu-id="c3035-227">**Özellikler** penceresinde, <xref:System.ComponentModel.BackgroundWorker> bileşenin `WorkerReportsProgress` ve <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliklerini **doğru**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-227">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to **true**.</span></span> <span data-ttu-id="c3035-228">Bu ayarlar <xref:System.ComponentModel.BackgroundWorker> bileşeninin düzenli olarak <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayını kullanmasına ve zaman uyumsuz güncelleştirmeleri iptal edebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3035-228">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span>

   <span data-ttu-id="c3035-229">Daha fazla bilgi için bkz. [BackgroundWorker Component](backgroundworker-component.md).</span><span class="sxs-lookup"><span data-stu-id="c3035-229">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

7. <span data-ttu-id="c3035-230">`MarqueeText` kaynak dosyasını **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="c3035-230">Open the `MarqueeText` source file in the **Code Editor**.</span></span> <span data-ttu-id="c3035-231">Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="c3035-231">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. <span data-ttu-id="c3035-232"><xref:System.Windows.Forms.Label> devralması ve `IMarqueeWidget` arabirimini uygulamak için `MarqueeText` bildirimini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c3035-232">Change the declaration of `MarqueeText` to inherit from <xref:System.Windows.Forms.Label> and to implement the `IMarqueeWidget` interface:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. <span data-ttu-id="c3035-233">Gösterilen özelliklere karşılık gelen örnek değişkenlerini bildirin ve bunları oluşturucuda başlatın.</span><span class="sxs-lookup"><span data-stu-id="c3035-233">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span> <span data-ttu-id="c3035-234">`isLit` alanı, metnin `LightColor` özelliği tarafından verilen renkte boyanmış olup olmayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="c3035-234">The `isLit` field determines if the text is to be painted in the color given by the `LightColor` property.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. <span data-ttu-id="c3035-235">`IMarqueeWidget` arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="c3035-235">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="c3035-236">`StartMarquee` ve `StopMarquee` yöntemleri, animasyonu başlatmak ve durdurmak için <xref:System.ComponentModel.BackgroundWorker> bileşenin <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> ve <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> yöntemlerini çağırır.</span><span class="sxs-lookup"><span data-stu-id="c3035-236">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="c3035-237"><xref:System.ComponentModel.CategoryAttribute.Category%2A> ve <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> öznitelikleri `UpdatePeriod` özelliğine uygulanır, bu nedenle "kayan yazı" adlı Özellikler penceresi özel bir bölümünde görünür.</span><span class="sxs-lookup"><span data-stu-id="c3035-237">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to the `UpdatePeriod` property so it appears in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. <span data-ttu-id="c3035-238">Özellik erişimcileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-238">Implement the property accessors.</span></span> <span data-ttu-id="c3035-239">İstemciler için iki özelliği kullanıma sunacaksınız: `LightColor` ve `DarkColor`.</span><span class="sxs-lookup"><span data-stu-id="c3035-239">You'll expose two properties to clients: `LightColor` and `DarkColor`.</span></span> <span data-ttu-id="c3035-240"><xref:System.ComponentModel.CategoryAttribute.Category%2A> ve <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> öznitelikleri bu özelliklere uygulanır, bu nedenle Özellikler "kayan yazı" adlı Özellikler penceresi özel bir bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c3035-240">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to these properties, so the properties appear in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. <span data-ttu-id="c3035-241"><xref:System.ComponentModel.BackgroundWorker> bileşenin <xref:System.ComponentModel.BackgroundWorker.DoWork> ve <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayları için işleyicileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-241">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="c3035-242"><xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi, `UpdatePeriod` tarafından belirtilen milisaniye sayısı için uyku moduna geçer, kodunuz <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>çağırarak animasyonu durdurana kadar <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c3035-242">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="c3035-243"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olay işleyicisi, yanıp sönünün görünümünü sağlamak için ışığın ve koyu durumunun arasındaki metni değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c3035-243">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler toggles the text between its light and dark state to give the appearance of flashing.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. <span data-ttu-id="c3035-244">Animasyonu etkinleştirmek için <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="c3035-244">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method to enable the animation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. <span data-ttu-id="c3035-245">Çözümü derlemek için **F6** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c3035-245">Press **F6** to build the solution.</span></span>

## <a name="create-the-marqueeborder-child-control"></a><span data-ttu-id="c3035-246">MarqueeBorder alt denetimini oluşturma</span><span class="sxs-lookup"><span data-stu-id="c3035-246">Create the MarqueeBorder Child Control</span></span>

<span data-ttu-id="c3035-247">`MarqueeBorder` denetimi `MarqueeText` denetiminden biraz daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="c3035-247">The `MarqueeBorder` control is slightly more sophisticated than the `MarqueeText` control.</span></span> <span data-ttu-id="c3035-248">Daha fazla özelliğe sahiptir ve <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemindeki animasyon daha fazla yer alır.</span><span class="sxs-lookup"><span data-stu-id="c3035-248">It has more properties and the animation in the <xref:System.Windows.Forms.Control.OnPaint%2A> method is more involved.</span></span> <span data-ttu-id="c3035-249">Prensibi, `MarqueeText` denetimine oldukça benzerdir.</span><span class="sxs-lookup"><span data-stu-id="c3035-249">In principle, it is quite similar to the `MarqueeText` control.</span></span>

<span data-ttu-id="c3035-250">`MarqueeBorder` denetimin alt denetimleri olabileceğinden, bu, <xref:System.Windows.Forms.Control.Layout> olaylarının farkında olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3035-250">Because the `MarqueeBorder` control can have child controls, it needs to be aware of <xref:System.Windows.Forms.Control.Layout> events.</span></span>

### <a name="to-create-the-marqueeborder-control"></a><span data-ttu-id="c3035-251">MarqueeBorder denetimini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c3035-251">To create the MarqueeBorder control</span></span>

1. <span data-ttu-id="c3035-252">`MarqueeControlLibrary` projesine yeni bir **özel denetim** öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-252">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="c3035-253">Yeni kaynak dosyasına "MarqueeBorder" temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="c3035-253">Give the new source file a base name of "MarqueeBorder."</span></span>

2. <span data-ttu-id="c3035-254">**Araç kutusundan** bir <xref:System.ComponentModel.BackgroundWorker> bileşenini `MarqueeBorder` denetimine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-254">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeBorder` control.</span></span> <span data-ttu-id="c3035-255">Bu bileşen `MarqueeBorder` denetiminin kendisini zaman uyumsuz olarak güncelleştirmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="c3035-255">This component will allow the `MarqueeBorder` control to update itself asynchronously.</span></span>

3. <span data-ttu-id="c3035-256">**Özellikler** penceresinde, <xref:System.ComponentModel.BackgroundWorker> bileşenin `WorkerReportsProgress` ve <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliklerini **doğru**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-256">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to **true**.</span></span> <span data-ttu-id="c3035-257">Bu ayarlar <xref:System.ComponentModel.BackgroundWorker> bileşeninin düzenli olarak <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayını kullanmasına ve zaman uyumsuz güncelleştirmeleri iptal edebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3035-257">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span> <span data-ttu-id="c3035-258">Daha fazla bilgi için bkz. [BackgroundWorker Component](backgroundworker-component.md).</span><span class="sxs-lookup"><span data-stu-id="c3035-258">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

4. <span data-ttu-id="c3035-259">**Özellikler** penceresinde, **Olaylar** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c3035-259">In the **Properties** window, select the **Events** button.</span></span> <span data-ttu-id="c3035-260"><xref:System.ComponentModel.BackgroundWorker.DoWork> ve <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayları için işleyiciler iliştirin.</span><span class="sxs-lookup"><span data-stu-id="c3035-260">Attach handlers for the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

5. <span data-ttu-id="c3035-261">`MarqueeBorder` kaynak dosyasını **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="c3035-261">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span> <span data-ttu-id="c3035-262">Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="c3035-262">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. <span data-ttu-id="c3035-263">`MarqueeBorder` bildirimini <xref:System.Windows.Forms.Panel> ve `IMarqueeWidget` arabirimini uygulayacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c3035-263">Change the declaration of `MarqueeBorder` to inherit from <xref:System.Windows.Forms.Panel> and to implement the `IMarqueeWidget` interface.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. <span data-ttu-id="c3035-264">`MarqueeBorder` denetiminin durumunu yönetmek için iki sabit listesi bildirin: `MarqueeSpinDirection`, ışıklarının etrafında "döndürme" ve ışıklarının şeklini belirleyen `MarqueeLightShape`(kare veya dairesel) belirleyen yönü belirler.</span><span class="sxs-lookup"><span data-stu-id="c3035-264">Declare two enumerations for managing the `MarqueeBorder` control's state: `MarqueeSpinDirection`, which determines the direction in which the lights "spin" around the border, and `MarqueeLightShape`, which determines the shape of the lights (square or circular).</span></span> <span data-ttu-id="c3035-265">Bu bildirimleri `MarqueeBorder` Sınıf bildiriminden önce yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c3035-265">Place these declarations before the `MarqueeBorder` class declaration.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. <span data-ttu-id="c3035-266">Gösterilen özelliklere karşılık gelen örnek değişkenlerini bildirin ve bunları oluşturucuda başlatın.</span><span class="sxs-lookup"><span data-stu-id="c3035-266">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. <span data-ttu-id="c3035-267">`IMarqueeWidget` arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="c3035-267">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="c3035-268">`StartMarquee` ve `StopMarquee` yöntemleri, animasyonu başlatmak ve durdurmak için <xref:System.ComponentModel.BackgroundWorker> bileşenin <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> ve <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> yöntemlerini çağırır.</span><span class="sxs-lookup"><span data-stu-id="c3035-268">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="c3035-269">`MarqueeBorder` denetimi alt denetimler içerebildiğinden, `StartMarquee` yöntemi tüm alt denetimleri numaralandırır ve `IMarqueeWidget`uygulamalarındaki `StartMarquee` çağırır.</span><span class="sxs-lookup"><span data-stu-id="c3035-269">Because the `MarqueeBorder` control can contain child controls, the `StartMarquee` method enumerates all child controls and calls `StartMarquee` on those that implement `IMarqueeWidget`.</span></span> <span data-ttu-id="c3035-270">`StopMarquee` yöntemi benzer bir uygulamaya sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c3035-270">The `StopMarquee` method has a similar implementation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. <span data-ttu-id="c3035-271">Özellik erişimcileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-271">Implement the property accessors.</span></span> <span data-ttu-id="c3035-272">`MarqueeBorder` denetiminin görünümünü denetlemek için birkaç özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="c3035-272">The `MarqueeBorder` control has several properties for controlling its appearance.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. <span data-ttu-id="c3035-273"><xref:System.ComponentModel.BackgroundWorker> bileşenin <xref:System.ComponentModel.BackgroundWorker.DoWork> ve <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayları için işleyicileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-273">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="c3035-274"><xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi, `UpdatePeriod` tarafından belirtilen milisaniye sayısı için uyku moduna geçer, kodunuz <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>çağırarak animasyonu durdurana kadar <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c3035-274">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="c3035-275"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olay işleyicisi, diğer ışıklarının açık/koyu durumunun belirlendiği "temel" Işığın konumunu arttırır ve denetimin kendisini yeniden çizmeyi sağlamak için <xref:System.Windows.Forms.Control.Refresh%2A> yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="c3035-275">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler increments the position of the "base" light, from which the light/dark state of the other lights is determined, and calls the <xref:System.Windows.Forms.Control.Refresh%2A> method to cause the control to repaint itself.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. <span data-ttu-id="c3035-276">Yardımcı yöntemleri `IsLit` ve `DrawLight`uygulayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-276">Implement the helper methods, `IsLit` and `DrawLight`.</span></span>

    <span data-ttu-id="c3035-277">`IsLit` yöntemi, belirli bir konumdaki ışığın rengini belirler.</span><span class="sxs-lookup"><span data-stu-id="c3035-277">The `IsLit` method determines the color of a light at a given position.</span></span> <span data-ttu-id="c3035-278">"Aydınlatmalı" olan ışıklar `LightColor` özelliği tarafından verilen renkte çizilir ve "koyu" olanlar `DarkColor` özelliği tarafından verilen renkte çizilir.</span><span class="sxs-lookup"><span data-stu-id="c3035-278">Lights that are "lit" are drawn in the color given by the `LightColor` property, and those that are "dark" are drawn in the color given by the `DarkColor` property.</span></span>

    <span data-ttu-id="c3035-279">`DrawLight` yöntemi uygun renk, şekil ve konumu kullanarak bir ışık çizer.</span><span class="sxs-lookup"><span data-stu-id="c3035-279">The `DrawLight` method draws a light using the appropriate color, shape, and position.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. <span data-ttu-id="c3035-280"><xref:System.Windows.Forms.Control.OnLayout%2A> ve <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemlerini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="c3035-280">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> and <xref:System.Windows.Forms.Control.OnPaint%2A> methods.</span></span>

    <span data-ttu-id="c3035-281"><xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi, ışıkları `MarqueeBorder` denetiminin kenarları üzerinde çizer.</span><span class="sxs-lookup"><span data-stu-id="c3035-281">The <xref:System.Windows.Forms.Control.OnPaint%2A> method draws the lights along the edges of the `MarqueeBorder` control.</span></span>

    <span data-ttu-id="c3035-282"><xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi `MarqueeBorder` denetiminin boyutlarına bağlı olduğundan, düzen her değiştiğinde onu çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3035-282">Because the <xref:System.Windows.Forms.Control.OnPaint%2A> method depends on the dimensions of the `MarqueeBorder` control, you need to call it whenever the layout changes.</span></span> <span data-ttu-id="c3035-283">Bunu başarmak için <xref:System.Windows.Forms.Control.OnLayout%2A> geçersiz kılın ve <xref:System.Windows.Forms.Control.Refresh%2A>çağırın.</span><span class="sxs-lookup"><span data-stu-id="c3035-283">To achieve this, override <xref:System.Windows.Forms.Control.OnLayout%2A> and call <xref:System.Windows.Forms.Control.Refresh%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="c3035-284">Gölge ve filtre özelliklerine özel tasarımcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="c3035-284">Create a Custom Designer to Shadow and Filter Properties</span></span>

<span data-ttu-id="c3035-285">`MarqueeControlRootDesigner` sınıfı kök Tasarımcı için uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3035-285">The `MarqueeControlRootDesigner` class provides the implementation for the root designer.</span></span> <span data-ttu-id="c3035-286">`MarqueeControl`üzerinde çalışan bu tasarımcıya ek olarak, `MarqueeBorder` denetimiyle özellikle ilişkilendirilmiş özel bir tasarımcı gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3035-286">In addition to this designer, which operates on the `MarqueeControl`, you'll need a custom designer that is specifically associated with the `MarqueeBorder` control.</span></span> <span data-ttu-id="c3035-287">Bu tasarımcı, özel kök tasarlayıcı bağlamında uygun olan özel davranışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3035-287">This designer provides custom behavior that is appropriate in the context of the custom root designer.</span></span>

<span data-ttu-id="c3035-288">Özellikle, `MarqueeBorderDesigner`, `MarqueeBorder` denetimindeki belirli özellikleri "gölgeleyip" filtreleyecek ve tasarım ortamıyla etkileşimini değiştirmiş.</span><span class="sxs-lookup"><span data-stu-id="c3035-288">Specifically, the `MarqueeBorderDesigner` will "shadow" and filter certain properties on the `MarqueeBorder` control, changing their interaction with the design environment.</span></span>

<span data-ttu-id="c3035-289">Bir bileşenin Özellik erişimcisine yönelik kesintiye uğratan çağrı, "gölgeleme" olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="c3035-289">Intercepting calls to a component's property accessor is known as "shadowing."</span></span> <span data-ttu-id="c3035-290">Bir tasarımcının Kullanıcı tarafından ayarlanan değeri izlemesine ve isteğe bağlı olarak bu değeri tasarlanmakta olan bileşene iletmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c3035-290">It allows a designer to track the value set by the user and optionally pass that value to the component being designed.</span></span>

<span data-ttu-id="c3035-291">Bu örnekte, <xref:System.Windows.Forms.Control.Visible%2A> ve <xref:System.Windows.Forms.Control.Enabled%2A> özellikleri `MarqueeBorderDesigner`tarafından gölgelendirilecektir. Bu, kullanıcının tasarım zamanı sırasında `MarqueeBorder` denetimini görünmez veya devre dışı yapmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="c3035-291">For this example, the <xref:System.Windows.Forms.Control.Visible%2A> and <xref:System.Windows.Forms.Control.Enabled%2A> properties will be shadowed by the `MarqueeBorderDesigner`, which prevents the user from making the `MarqueeBorder` control invisible or disabled during design time.</span></span>

<span data-ttu-id="c3035-292">Tasarımcılar Ayrıca özellikler ekleyebilir ve kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="c3035-292">Designers can also add and remove properties.</span></span> <span data-ttu-id="c3035-293">Bu örnekte, <xref:System.Windows.Forms.Control.Padding%2A> özelliği tasarım zamanında kaldırılacak, çünkü `MarqueeBorder` denetimi program aracılığıyla `LightSize` özelliği tarafından belirtilen ışıklarının boyutuna göre doldurma ayarlıyor.</span><span class="sxs-lookup"><span data-stu-id="c3035-293">For this example, the <xref:System.Windows.Forms.Control.Padding%2A> property will be removed at design time, because the `MarqueeBorder` control programmatically sets the padding based on the size of the lights specified by the `LightSize` property.</span></span>

<span data-ttu-id="c3035-294">`MarqueeBorderDesigner` için temel sınıf, tasarım zamanında bir denetim tarafından açığa çıkarılan öznitelikleri, özellikleri ve olayları değiştirebilen Yöntemler içeren <xref:System.ComponentModel.Design.ComponentDesigner>.</span><span class="sxs-lookup"><span data-stu-id="c3035-294">The base class for `MarqueeBorderDesigner` is <xref:System.ComponentModel.Design.ComponentDesigner>, which has methods that can change the attributes, properties, and events exposed by a control at design time:</span></span>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

<span data-ttu-id="c3035-295">Bu yöntemleri kullanarak bir bileşenin genel arabirimini değiştirirken bu kuralları izleyin:</span><span class="sxs-lookup"><span data-stu-id="c3035-295">When changing the public interface of a component using these methods, follow these rules:</span></span>

- <span data-ttu-id="c3035-296">Yalnızca `PreFilter` metotlarda öğe ekleme veya kaldırma</span><span class="sxs-lookup"><span data-stu-id="c3035-296">Add or remove items in the `PreFilter` methods only</span></span>

- <span data-ttu-id="c3035-297">Yalnızca `PostFilter` metotlarda bulunan öğeleri değiştir</span><span class="sxs-lookup"><span data-stu-id="c3035-297">Modify existing items in the `PostFilter` methods only</span></span>

- <span data-ttu-id="c3035-298">`PreFilter` metotlarında her zaman temel uygulamayı çağır</span><span class="sxs-lookup"><span data-stu-id="c3035-298">Always call the base implementation first in the `PreFilter` methods</span></span>

- <span data-ttu-id="c3035-299">`PostFilter` metotlarında her zaman temel uygulamayı çağırın</span><span class="sxs-lookup"><span data-stu-id="c3035-299">Always call the base implementation last in the `PostFilter` methods</span></span>

<span data-ttu-id="c3035-300">Bu kurallara uymak, tasarım zamanı ortamındaki tüm tasarımcılarının tasarlanmakta olan tüm bileşenlerin tutarlı bir görünümüne sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3035-300">Adhering to these rules ensures that all designers in the design-time environment have a consistent view of all components being designed.</span></span>

<span data-ttu-id="c3035-301"><xref:System.ComponentModel.Design.ComponentDesigner> sınıfı, gölgelendirilmiş özelliklerin değerlerini yönetmeye yönelik bir sözlük sağlar, bu da size belirli örnek değişkenleri oluşturma gereksinimini sizi maliyetinden kurtarır.</span><span class="sxs-lookup"><span data-stu-id="c3035-301">The <xref:System.ComponentModel.Design.ComponentDesigner> class provides a dictionary for managing the values of shadowed properties, which relieves you of the need to create specific instance variables.</span></span>

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="c3035-302">Gölge ve filtre özelliklerine özel bir tasarımcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c3035-302">To create a custom designer to shadow and filter properties</span></span>

1. <span data-ttu-id="c3035-303">**Tasarım** klasörüne sağ tıklayın ve yeni bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-303">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="c3035-304">Kaynak dosyaya **MarqueeBorderDesigner**temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="c3035-304">Give the source file a base name of **MarqueeBorderDesigner**.</span></span>

2. <span data-ttu-id="c3035-305">MarqueeBorderDesigner kaynak dosyasını **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="c3035-305">Open the MarqueeBorderDesigner source file in the **Code Editor**.</span></span> <span data-ttu-id="c3035-306">Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="c3035-306">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. <span data-ttu-id="c3035-307">`MarqueeBorderDesigner` bildirimi <xref:System.Windows.Forms.Design.ParentControlDesigner>' dan devralacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c3035-307">Change the declaration of `MarqueeBorderDesigner` to inherit from <xref:System.Windows.Forms.Design.ParentControlDesigner>.</span></span>

    <span data-ttu-id="c3035-308">`MarqueeBorder` denetim alt denetimler içerebildiğinden, `MarqueeBorderDesigner` üst-alt etkileşimi işleyen <xref:System.Windows.Forms.Design.ParentControlDesigner>devralır.</span><span class="sxs-lookup"><span data-stu-id="c3035-308">Because the `MarqueeBorder` control can contain child controls, `MarqueeBorderDesigner` inherits from <xref:System.Windows.Forms.Design.ParentControlDesigner>, which handles the parent-child interaction.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. <span data-ttu-id="c3035-309"><xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>temel uygulamasını geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="c3035-309">Override the base implementation of <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. <span data-ttu-id="c3035-310"><xref:System.Windows.Forms.Control.Enabled%2A> ve <xref:System.Windows.Forms.Control.Visible%2A> özelliklerini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-310">Implement the <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A> properties.</span></span> <span data-ttu-id="c3035-311">Bu uygulamalar, denetimin özelliklerini gölgelendir.</span><span class="sxs-lookup"><span data-stu-id="c3035-311">These implementations shadow the control's properties.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handle-component-changes"></a><span data-ttu-id="c3035-312">Bileşen değişikliklerini işle</span><span class="sxs-lookup"><span data-stu-id="c3035-312">Handle Component Changes</span></span>

<span data-ttu-id="c3035-313">`MarqueeControlRootDesigner` sınıfı, `MarqueeControl` örneklerinizin özel tasarım zamanı deneyimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3035-313">The `MarqueeControlRootDesigner` class provides the custom design-time experience for your `MarqueeControl` instances.</span></span> <span data-ttu-id="c3035-314">Tasarım zamanı işlevlerinin çoğu <xref:System.Windows.Forms.Design.DocumentDesigner> sınıfından devralınır.</span><span class="sxs-lookup"><span data-stu-id="c3035-314">Most of the design-time functionality is inherited from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="c3035-315">Kodunuz iki özel özelleştirme uygular: bileşen değişikliklerini işleme ve tasarımcı fiilleri ekleme.</span><span class="sxs-lookup"><span data-stu-id="c3035-315">Your code will implement two specific customizations: handling component changes, and adding designer verbs.</span></span>

<span data-ttu-id="c3035-316">Kullanıcılar `MarqueeControl` örneklerini tasarlarsa, kök tasarlayıcı `MarqueeControl` ve onun alt denetimlerinde yapılan değişiklikleri izler.</span><span class="sxs-lookup"><span data-stu-id="c3035-316">As users design their `MarqueeControl` instances, your root designer will track changes to the `MarqueeControl` and its child controls.</span></span> <span data-ttu-id="c3035-317">Tasarım zamanı ortamı, bileşen durumundaki değişiklikleri izlemek için <xref:System.ComponentModel.Design.IComponentChangeService>uygun bir hizmet sunar.</span><span class="sxs-lookup"><span data-stu-id="c3035-317">The design-time environment offers a convenient service, <xref:System.ComponentModel.Design.IComponentChangeService>, for tracking changes to component state.</span></span>

<span data-ttu-id="c3035-318"><xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> yöntemiyle ortamı sorgulayarak bu hizmete bir başvuru elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="c3035-318">You acquire a reference to this service by querying the environment with the <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> method.</span></span> <span data-ttu-id="c3035-319">Sorgu başarılı olursa, tasarımcı <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> olayı için bir işleyici iliştirebilir ve tasarım zamanında tutarlı bir durumu korumak için gereken görevleri gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="c3035-319">If the query is successful, your designer can attach a handler for the <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> event and perform whatever tasks are required to maintain a consistent state at design time.</span></span>

<span data-ttu-id="c3035-320">`MarqueeControlRootDesigner` sınıfı söz konusu olduğunda, `MarqueeControl`bulunan her bir `IMarqueeWidget` nesnesi üzerinde <xref:System.Windows.Forms.Control.Refresh%2A> yöntemini çağıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="c3035-320">In the case of the `MarqueeControlRootDesigner` class, you will call the <xref:System.Windows.Forms.Control.Refresh%2A> method on each `IMarqueeWidget` object contained by the `MarqueeControl`.</span></span> <span data-ttu-id="c3035-321">Bu, üst öğesi <xref:System.Windows.Forms.Control.Size%2A> gibi özellikler değiştirildiğinde `IMarqueeWidget` nesnenin kendisini uygun şekilde yeniden görüntülemesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="c3035-321">This will cause the `IMarqueeWidget` object to repaint itself appropriately when properties like its parent's <xref:System.Windows.Forms.Control.Size%2A> are changed.</span></span>

### <a name="to-handle-component-changes"></a><span data-ttu-id="c3035-322">Bileşen değişikliklerini işlemek için</span><span class="sxs-lookup"><span data-stu-id="c3035-322">To handle component changes</span></span>

1. <span data-ttu-id="c3035-323">`MarqueeControlRootDesigner` kaynak dosyasını **kod düzenleyicisinde** açın ve <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> metodunu geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="c3035-323">Open the `MarqueeControlRootDesigner` source file in the **Code Editor** and override the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span> <span data-ttu-id="c3035-324"><xref:System.ComponentModel.Design.IComponentChangeService><xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> ve sorgusunun temel uygulamasını çağırın.</span><span class="sxs-lookup"><span data-stu-id="c3035-324">Call the base implementation of <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> and query for the <xref:System.ComponentModel.Design.IComponentChangeService>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. <span data-ttu-id="c3035-325"><xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> olay işleyicisini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-325">Implement the <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> event handler.</span></span> <span data-ttu-id="c3035-326">Gönderen bileşenin türünü test edin ve bir `IMarqueeWidget`, <xref:System.Windows.Forms.Control.Refresh%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="c3035-326">Test the sending component's type, and if it is an `IMarqueeWidget`, call its <xref:System.Windows.Forms.Control.Refresh%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="add-designer-verbs-to-your-custom-designer"></a><span data-ttu-id="c3035-327">Özel tasarımcıya tasarımcı fiilleri ekleme</span><span class="sxs-lookup"><span data-stu-id="c3035-327">Add Designer Verbs to your Custom Designer</span></span>

<span data-ttu-id="c3035-328">Tasarımcı fiili, olay işleyicisine bağlı bir menü komutu olur.</span><span class="sxs-lookup"><span data-stu-id="c3035-328">A designer verb is a menu command linked to an event handler.</span></span> <span data-ttu-id="c3035-329">Tasarımcı fiilleri, tasarım zamanında bir bileşenin kısayol menüsüne eklenir.</span><span class="sxs-lookup"><span data-stu-id="c3035-329">Designer verbs are added to a component's shortcut menu at design time.</span></span> <span data-ttu-id="c3035-330">Daha fazla bilgi için bkz. <xref:System.ComponentModel.Design.DesignerVerb>.</span><span class="sxs-lookup"><span data-stu-id="c3035-330">For more information, see <xref:System.ComponentModel.Design.DesignerVerb>.</span></span>

<span data-ttu-id="c3035-331">Tasarımcılara iki tasarımcı fiilleri ekleyeceksiniz: **Testi Çalıştır** ve **testi durdur**.</span><span class="sxs-lookup"><span data-stu-id="c3035-331">You will add two designer verbs to your designers: **Run Test** and **Stop Test**.</span></span> <span data-ttu-id="c3035-332">Bu fiiller, tasarım zamanında `MarqueeControl` çalışma zamanı davranışını görüntülemenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="c3035-332">These verbs will allow you to view the run-time behavior of the `MarqueeControl` at design time.</span></span> <span data-ttu-id="c3035-333">Bu fiiller `MarqueeControlRootDesigner`eklenecektir.</span><span class="sxs-lookup"><span data-stu-id="c3035-333">These verbs will be added to `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="c3035-334">**Çalıştırma testi** çağrıldığında, fiil olay işleyicisi `MarqueeControl``StartMarquee` yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="c3035-334">When **Run Test** is invoked, the verb event handler will call the `StartMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="c3035-335">**Test durdurma** çağrıldığında, fiil olay işleyicisi `MarqueeControl``StopMarquee` yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="c3035-335">When **Stop Test** is invoked, the verb event handler will call the `StopMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="c3035-336">`StartMarquee` ve `StopMarquee` yöntemlerinin uygulanması, `IMarqueeWidget`uygulayan içerilen denetimlerde bu yöntemleri çağırır, bu nedenle içerilen `IMarqueeWidget` denetimlerinin de teste katılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3035-336">The implementation of the `StartMarquee` and `StopMarquee` methods call these methods on contained controls that implement `IMarqueeWidget`, so any contained `IMarqueeWidget` controls will also participate in the test.</span></span>

### <a name="to-add-designer-verbs-to-your-custom-designers"></a><span data-ttu-id="c3035-337">Özel tasarımcılara tasarımcı fiilleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="c3035-337">To add designer verbs to your custom designers</span></span>

1. <span data-ttu-id="c3035-338">`MarqueeControlRootDesigner` sınıfında, `OnVerbRunTest` ve `OnVerbStopTest`adlı olay işleyicileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-338">In the `MarqueeControlRootDesigner` class, add event handlers named `OnVerbRunTest` and `OnVerbStopTest`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. <span data-ttu-id="c3035-339">Bu olay işleyicilerini ilgili tasarımcı fiillerine bağlayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-339">Connect these event handlers to their corresponding designer verbs.</span></span> <span data-ttu-id="c3035-340">`MarqueeControlRootDesigner`, temel sınıfından bir <xref:System.ComponentModel.Design.DesignerVerbCollection> devralır.</span><span class="sxs-lookup"><span data-stu-id="c3035-340">`MarqueeControlRootDesigner` inherits a <xref:System.ComponentModel.Design.DesignerVerbCollection> from its base class.</span></span> <span data-ttu-id="c3035-341">İki yeni <xref:System.ComponentModel.Design.DesignerVerb> nesnesi oluşturacak ve bunları <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> yönteminde bu koleksiyona ekleyecek.</span><span class="sxs-lookup"><span data-stu-id="c3035-341">You will create two new <xref:System.ComponentModel.Design.DesignerVerb> objects and add them to this collection in the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="create-a-custom-uitypeeditor"></a><span data-ttu-id="c3035-342">Özel bir Uııtypeınfo Düzenleyicisi oluşturun</span><span class="sxs-lookup"><span data-stu-id="c3035-342">Create a Custom UITypeEditor</span></span>

<span data-ttu-id="c3035-343">Kullanıcılar için özel bir tasarım zamanı deneyimi oluşturduğunuzda, genellikle Özellikler penceresi özel bir etkileşim oluşturmak tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="c3035-343">When you create a custom design-time experience for users, it is often desirable to create a custom interaction with the Properties window.</span></span> <span data-ttu-id="c3035-344">Bunu, bir <xref:System.Drawing.Design.UITypeEditor>oluşturarak gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3035-344">You can accomplish this by creating a <xref:System.Drawing.Design.UITypeEditor>.</span></span>

<span data-ttu-id="c3035-345">`MarqueeBorder` denetimi Özellikler penceresi çeşitli özellikleri kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="c3035-345">The `MarqueeBorder` control exposes several properties in the Properties window.</span></span> <span data-ttu-id="c3035-346">Bu özelliklerden ikisi, `MarqueeSpinDirection` ve `MarqueeLightShape` numaralandırmalar tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="c3035-346">Two of these properties, `MarqueeSpinDirection` and `MarqueeLightShape` are represented by enumerations.</span></span> <span data-ttu-id="c3035-347">Kullanıcı arabirimi türü düzenleyicisinin kullanımını göstermek için `MarqueeLightShape` özelliği ilişkili bir <xref:System.Drawing.Design.UITypeEditor> sınıfına sahip olur.</span><span class="sxs-lookup"><span data-stu-id="c3035-347">To illustrate the use of a UI type editor, the `MarqueeLightShape` property will have an associated <xref:System.Drawing.Design.UITypeEditor> class.</span></span>

### <a name="to-create-a-custom-ui-type-editor"></a><span data-ttu-id="c3035-348">Özel bir kullanıcı arabirimi tür Düzenleyicisi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c3035-348">To create a custom UI type editor</span></span>

1. <span data-ttu-id="c3035-349">`MarqueeBorder` kaynak dosyasını **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="c3035-349">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span>

2. <span data-ttu-id="c3035-350">`MarqueeBorder` sınıfının tanımında, <xref:System.Drawing.Design.UITypeEditor>türetilen `LightShapeEditor` adlı bir sınıf bildirin.</span><span class="sxs-lookup"><span data-stu-id="c3035-350">In the definition of the `MarqueeBorder` class, declare a class called `LightShapeEditor` that derives from <xref:System.Drawing.Design.UITypeEditor>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. <span data-ttu-id="c3035-351">`editorService`adlı bir <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> örnek değişkeni bildirin.</span><span class="sxs-lookup"><span data-stu-id="c3035-351">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. <span data-ttu-id="c3035-352"><xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="c3035-352">Override the <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> method.</span></span> <span data-ttu-id="c3035-353">Bu uygulama, tasarım ortamına `LightShapeEditor`nasıl görüntüleneceğini bildiren <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3035-353">This implementation returns <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, which tells the design environment how to display the `LightShapeEditor`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. <span data-ttu-id="c3035-354"><xref:System.Drawing.Design.UITypeEditor.EditValue%2A> yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="c3035-354">Override the <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> method.</span></span> <span data-ttu-id="c3035-355">Bu uygulama, <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> nesnesi için tasarım ortamını sorgular.</span><span class="sxs-lookup"><span data-stu-id="c3035-355">This implementation queries the design environment for an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> object.</span></span> <span data-ttu-id="c3035-356">Başarılı olursa, bir `LightShapeSelectionControl`oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c3035-356">If successful, it creates a `LightShapeSelectionControl`.</span></span> <span data-ttu-id="c3035-357"><xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> yöntemi `LightShapeEditor`başlatılacak şekilde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c3035-357">The <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> method is invoked to start the `LightShapeEditor`.</span></span> <span data-ttu-id="c3035-358">Bu çağrıdan gelen dönüş değeri tasarım ortamına döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c3035-358">The return value from this invocation is returned to the design environment.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="create-a-view-control-for-your-custom-uitypeeditor"></a><span data-ttu-id="c3035-359">Özel Uııtypeınfo Düzenleyicisi için bir görünüm denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c3035-359">Create a View Control for your Custom UITypeEditor</span></span>

<span data-ttu-id="c3035-360">`MarqueeLightShape` özelliği iki tür ışık şeklini destekler: `Square` ve `Circle`.</span><span class="sxs-lookup"><span data-stu-id="c3035-360">The `MarqueeLightShape` property supports two types of light shapes: `Square` and `Circle`.</span></span> <span data-ttu-id="c3035-361">Yalnızca bu değerleri Özellikler penceresi grafik olarak görüntülemek için kullanılan özel bir denetim oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c3035-361">You will create a custom control used solely for the purpose of graphically displaying these values in the Properties window.</span></span> <span data-ttu-id="c3035-362">Bu özel denetim, Özellikler penceresi etkileşimde bulunmak için <xref:System.Drawing.Design.UITypeEditor> tarafından kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="c3035-362">This custom control will be used by your <xref:System.Drawing.Design.UITypeEditor> to interact with the Properties window.</span></span>

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a><span data-ttu-id="c3035-363">Özel UI türü düzenleyiciniz için bir görünüm denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c3035-363">To create a view control for your custom UI type editor</span></span>

1. <span data-ttu-id="c3035-364">`MarqueeControlLibrary` projesine yeni bir <xref:System.Windows.Forms.UserControl> öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-364">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="c3035-365">Yeni kaynak dosyasına, **Açık Shapeselectioncontrol**temel adını verin.</span><span class="sxs-lookup"><span data-stu-id="c3035-365">Give the new source file a base name of **LightShapeSelectionControl**.</span></span>

2. <span data-ttu-id="c3035-366">**Araç kutusundan** iki <xref:System.Windows.Forms.Panel> denetimini `LightShapeSelectionControl`üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-366">Drag two <xref:System.Windows.Forms.Panel> controls from the **Toolbox** onto the `LightShapeSelectionControl`.</span></span> <span data-ttu-id="c3035-367">`squarePanel` ve `circlePanel`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="c3035-367">Name them `squarePanel` and `circlePanel`.</span></span> <span data-ttu-id="c3035-368">Yan yana düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-368">Arrange them side by side.</span></span> <span data-ttu-id="c3035-369">Her iki <xref:System.Windows.Forms.Panel> denetiminin <xref:System.Windows.Forms.Control.Size%2A> özelliğini **(60, 60)** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-369">Set the <xref:System.Windows.Forms.Control.Size%2A> property of both <xref:System.Windows.Forms.Panel> controls to **(60, 60)**.</span></span> <span data-ttu-id="c3035-370">`squarePanel` denetiminin <xref:System.Windows.Forms.Control.Location%2A> özelliğini **(8, 10)** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-370">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `squarePanel` control to **(8, 10)**.</span></span> <span data-ttu-id="c3035-371">`circlePanel` denetiminin <xref:System.Windows.Forms.Control.Location%2A> özelliğini **(80, 10)** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-371">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `circlePanel` control to **(80, 10)**.</span></span> <span data-ttu-id="c3035-372">Son olarak, `LightShapeSelectionControl` <xref:System.Windows.Forms.Control.Size%2A> özelliğini **(150, 80)** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-372">Finally, set the <xref:System.Windows.Forms.Control.Size%2A> property of the `LightShapeSelectionControl` to **(150, 80)**.</span></span>

3. <span data-ttu-id="c3035-373">`LightShapeSelectionControl` kaynak dosyasını **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="c3035-373">Open the `LightShapeSelectionControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="c3035-374">Dosyanın en üstüne <xref:System.Windows.Forms.Design?displayProperty=nameWithType> ad alanını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="c3035-374">At the top of the file, import the <xref:System.Windows.Forms.Design?displayProperty=nameWithType> namespace:</span></span>

   ```vb
   Imports System.Windows.Forms.Design
   ```

   ```csharp
   using System.Windows.Forms.Design;
   ```

4. <span data-ttu-id="c3035-375">`squarePanel` ve `circlePanel` denetimleri için <xref:System.Windows.Forms.Control.Click> olay işleyicileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-375">Implement <xref:System.Windows.Forms.Control.Click> event handlers for the `squarePanel` and `circlePanel` controls.</span></span> <span data-ttu-id="c3035-376">Bu yöntemler, özel <xref:System.Drawing.Design.UITypeEditor> Düzenle oturumunun sona erdirmek için <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> çağırır.</span><span class="sxs-lookup"><span data-stu-id="c3035-376">These methods invoke <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> to end the custom <xref:System.Drawing.Design.UITypeEditor> editing session.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

5. <span data-ttu-id="c3035-377">`editorService`adlı bir <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> örnek değişkeni bildirin.</span><span class="sxs-lookup"><span data-stu-id="c3035-377">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

   ```vb
   Private editorService As IWindowsFormsEditorService
   ```

   ```csharp
   private IWindowsFormsEditorService editorService;
   ```

6. <span data-ttu-id="c3035-378">`lightShapeValue`adlı bir `MarqueeLightShape` örnek değişkeni bildirin.</span><span class="sxs-lookup"><span data-stu-id="c3035-378">Declare a `MarqueeLightShape` instance variable called `lightShapeValue`.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

7. <span data-ttu-id="c3035-379">`LightShapeSelectionControl` oluşturucuda, <xref:System.Windows.Forms.Control.Click> olay işleyicilerini `squarePanel` ve `circlePanel` denetimlerin ' <xref:System.Windows.Forms.Control.Click> olaylarını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-379">In the `LightShapeSelectionControl` constructor, attach the <xref:System.Windows.Forms.Control.Click> event handlers to the `squarePanel` and `circlePanel` controls' <xref:System.Windows.Forms.Control.Click> events.</span></span> <span data-ttu-id="c3035-380">Ayrıca, tasarım ortamından `lightShapeValue` alanına `MarqueeLightShape` değerini atayan bir Oluşturucu aşırı yüklemesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-380">Also, define a constructor overload that assigns the `MarqueeLightShape` value from the design environment to the `lightShapeValue` field.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

8. <span data-ttu-id="c3035-381"><xref:System.ComponentModel.Component.Dispose%2A> yönteminde, <xref:System.Windows.Forms.Control.Click> olay işleyicilerini ayırın.</span><span class="sxs-lookup"><span data-stu-id="c3035-381">In the <xref:System.ComponentModel.Component.Dispose%2A> method, detach the <xref:System.Windows.Forms.Control.Click> event handlers.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

9. <span data-ttu-id="c3035-382">**Çözüm Gezgini**, **tüm dosyaları göster** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-382">In **Solution Explorer**, click the **Show All Files** button.</span></span> <span data-ttu-id="c3035-383">LightShapeSelectionControl.Designer.cs veya LightShapeSelectionControl. Designer. vb dosyasını açın ve <xref:System.ComponentModel.Component.Dispose%2A> yönteminin varsayılan tanımını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="c3035-383">Open the LightShapeSelectionControl.Designer.cs or LightShapeSelectionControl.Designer.vb file, and remove the default definition of the <xref:System.ComponentModel.Component.Dispose%2A> method.</span></span>

10. <span data-ttu-id="c3035-384">`LightShape` özelliğini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-384">Implement the `LightShape` property.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

11. <span data-ttu-id="c3035-385"><xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="c3035-385">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="c3035-386">Bu uygulama doldurulmuş bir kare ve daire çizecek.</span><span class="sxs-lookup"><span data-stu-id="c3035-386">This implementation will draw a filled square and circle.</span></span> <span data-ttu-id="c3035-387">Ayrıca, bir şekil ya da diğeri etrafında kenarlık çizerek seçili değeri vurgulayacaktır.</span><span class="sxs-lookup"><span data-stu-id="c3035-387">It will also highlight the selected value by drawing a border around one shape or the other.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="test-your-custom-control-in-the-designer"></a><span data-ttu-id="c3035-388">Tasarımcıda özel denetiminizi test etme</span><span class="sxs-lookup"><span data-stu-id="c3035-388">Test your Custom Control in the Designer</span></span>

<span data-ttu-id="c3035-389">Bu noktada, `MarqueeControlLibrary` projesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3035-389">At this point, you can build the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="c3035-390">`MarqueeControl` sınıfından devralan bir denetim oluşturarak ve bunu bir formda kullanarak uygulamanızı test edin.</span><span class="sxs-lookup"><span data-stu-id="c3035-390">Test your implementation by creating a control that inherits from the `MarqueeControl` class and using it on a form.</span></span>

### <a name="to-create-a-custom-marqueecontrol-implementation"></a><span data-ttu-id="c3035-391">Özel bir MarqueeControl uygulamasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c3035-391">To create a custom MarqueeControl implementation</span></span>

1. <span data-ttu-id="c3035-392">Windows Form Tasarımcısı `DemoMarqueeControl` açın.</span><span class="sxs-lookup"><span data-stu-id="c3035-392">Open `DemoMarqueeControl` in the Windows Forms Designer.</span></span> <span data-ttu-id="c3035-393">Bu, `DemoMarqueeControl` türünün bir örneğini oluşturur ve `MarqueeControlRootDesigner` türünün bir örneğinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c3035-393">This creates an instance of the `DemoMarqueeControl` type and displays it in an instance of the `MarqueeControlRootDesigner` type.</span></span>

2. <span data-ttu-id="c3035-394">**Araç kutusunda** **MarqueeControlLibrary Components** sekmesini açın. `MarqueeBorder` ve `MarqueeText` denetimlerini seçilebilir olarak görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="c3035-394">In the **Toolbox**, open the **MarqueeControlLibrary Components** tab. You will see the `MarqueeBorder` and `MarqueeText` controls available for selection.</span></span>

3. <span data-ttu-id="c3035-395">`MarqueeBorder` denetiminin bir örneğini `DemoMarqueeControl` tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-395">Drag an instance of the `MarqueeBorder` control onto the `DemoMarqueeControl` design surface.</span></span> <span data-ttu-id="c3035-396">Bu `MarqueeBorder` denetimini üst denetime yerleştir.</span><span class="sxs-lookup"><span data-stu-id="c3035-396">Dock this `MarqueeBorder` control to the parent control.</span></span>

4. <span data-ttu-id="c3035-397">`MarqueeText` denetiminin bir örneğini `DemoMarqueeControl` tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-397">Drag an instance of the `MarqueeText` control onto the `DemoMarqueeControl` design surface.</span></span>

5. <span data-ttu-id="c3035-398">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c3035-398">Build the solution.</span></span>

6. <span data-ttu-id="c3035-399">`DemoMarqueeControl` sağ tıklayın ve kısayol menüsünde, animasyonu başlatmak için **Test Çalıştır** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-399">Right-click the `DemoMarqueeControl` and from the shortcut menu select the **Run Test** option to start the animation.</span></span> <span data-ttu-id="c3035-400">Animasyonu durdurmak için **Sınamayı Durdur** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-400">Click **Stop Test** to stop the animation.</span></span>

7. <span data-ttu-id="c3035-401">Tasarım görünümü 'da **Form1** ' i açın.</span><span class="sxs-lookup"><span data-stu-id="c3035-401">Open **Form1** in Design view.</span></span>

8. <span data-ttu-id="c3035-402">Forma iki <xref:System.Windows.Forms.Button> denetimi yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c3035-402">Place two <xref:System.Windows.Forms.Button> controls on the form.</span></span> <span data-ttu-id="c3035-403">`startButton` ve `stopButton`adlandırın ve <xref:System.Windows.Forms.Control.Text%2A> özellik değerlerini sırasıyla **Başlat** ve **Durdur**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c3035-403">Name them `startButton` and `stopButton`, and change the <xref:System.Windows.Forms.Control.Text%2A> property values to **Start** and **Stop**, respectively.</span></span>

9. <span data-ttu-id="c3035-404"><xref:System.Windows.Forms.Button> denetimleri için <xref:System.Windows.Forms.Control.Click> olay işleyicileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-404">Implement <xref:System.Windows.Forms.Control.Click> event handlers for both <xref:System.Windows.Forms.Button> controls.</span></span>

10. <span data-ttu-id="c3035-405">**Araç kutusunda** **MarqueeControlTest Components** sekmesini açın. `DemoMarqueeControl` seçime uygun olarak görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="c3035-405">In the **Toolbox**, open the **MarqueeControlTest Components** tab. You will see the `DemoMarqueeControl` available for selection.</span></span>

11. <span data-ttu-id="c3035-406">Bir `DemoMarqueeControl` örneğini **Form1** tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-406">Drag an instance of `DemoMarqueeControl` onto the **Form1** design surface.</span></span>

12. <span data-ttu-id="c3035-407"><xref:System.Windows.Forms.Control.Click> olay işleyicilerinde, `DemoMarqueeControl`üzerinde `Start` ve `Stop` yöntemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="c3035-407">In the <xref:System.Windows.Forms.Control.Click> event handlers, invoke the `Start` and `Stop` methods on the `DemoMarqueeControl`.</span></span>

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

13. <span data-ttu-id="c3035-408">`MarqueeControlTest` projesini başlangıç projesi olarak ayarlayın ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c3035-408">Set the `MarqueeControlTest` project as the startup project and run it.</span></span> <span data-ttu-id="c3035-409">`DemoMarqueeControl`görüntüleyen formu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="c3035-409">You will see the form displaying your `DemoMarqueeControl`.</span></span> <span data-ttu-id="c3035-410">Animasyonu başlatmak için **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c3035-410">Select the **Start** button to start the animation.</span></span> <span data-ttu-id="c3035-411">Metnin yanıp sönmesi ve kenarlığın etrafında hareket eden ışıklar görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3035-411">You should see the text flashing and the lights moving around the border.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c3035-412">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="c3035-412">Next steps</span></span>

<span data-ttu-id="c3035-413">`MarqueeControlLibrary`, Özel denetimlerin ve ilişkili tasarımcılarının basit bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c3035-413">The `MarqueeControlLibrary` demonstrates a simple implementation of custom controls and associated designers.</span></span> <span data-ttu-id="c3035-414">Bu örneği çeşitli yollarla daha karmaşık hale getirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c3035-414">You can make this sample more sophisticated in several ways:</span></span>

- <span data-ttu-id="c3035-415">Tasarımcıda `DemoMarqueeControl` özellik değerlerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c3035-415">Change the property values for the `DemoMarqueeControl` in the designer.</span></span> <span data-ttu-id="c3035-416">Daha fazla `MarqueBorder` denetim ekleyin ve iç içe bir efekt oluşturmak için bunları üst örneklerine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c3035-416">Add more `MarqueBorder` controls and dock them within their parent instances to create a nested effect.</span></span> <span data-ttu-id="c3035-417">`UpdatePeriod` ve hafif ilgili özellikler için farklı ayarlarla denemeler yapın.</span><span class="sxs-lookup"><span data-stu-id="c3035-417">Experiment with different settings for the `UpdatePeriod` and the light-related properties.</span></span>

- <span data-ttu-id="c3035-418">Kendi `IMarqueeWidget`uygulamalarınızı yazın.</span><span class="sxs-lookup"><span data-stu-id="c3035-418">Author your own implementations of `IMarqueeWidget`.</span></span> <span data-ttu-id="c3035-419">Örneğin, yanıp sönen bir "Neon Sign" veya birden çok görüntüde animasyonlu bir işaret oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3035-419">You could, for example, create a flashing "neon sign" or an animated sign with multiple images.</span></span>

- <span data-ttu-id="c3035-420">Tasarım zamanı deneyimini daha da özelleştirin.</span><span class="sxs-lookup"><span data-stu-id="c3035-420">Further customize the design-time experience.</span></span> <span data-ttu-id="c3035-421"><xref:System.Windows.Forms.Control.Enabled%2A> ve <xref:System.Windows.Forms.Control.Visible%2A>daha fazla özelliği gölgelendirmeyi deneyebilirsiniz ve yeni özellikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3035-421">You could try shadowing more properties than <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A>, and you could add new properties.</span></span> <span data-ttu-id="c3035-422">Alt öğe denetimleri yerleştirme gibi yaygın görevleri basitleştirmek için yeni tasarımcı fiilleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-422">Add new designer verbs to simplify common tasks like docking child controls.</span></span>

- <span data-ttu-id="c3035-423">`MarqueeControl`lisanslayın.</span><span class="sxs-lookup"><span data-stu-id="c3035-423">License the `MarqueeControl`.</span></span>

- <span data-ttu-id="c3035-424">Denetimlerinizin serileştirilme şeklini ve kodun onlar için nasıl oluşturulduğunu denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c3035-424">Control how your controls are serialized and how code is generated for them.</span></span> <span data-ttu-id="c3035-425">Daha fazla bilgi için bkz. [dinamik kaynak kodu oluşturma ve derleme](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="c3035-425">For more information, see [Dynamic Source Code Generation and Compilation](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c3035-426">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3035-426">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
