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
ms.openlocfilehash: 9f290629e50d7d791119298059277ba73d8e73eb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211212"
---
# <a name="walkthrough-creating-a-windows-forms-control-that-takes-advantage-of-visual-studio-design-time-features"></a><span data-ttu-id="e39f5-102">İzlenecek yol: Visual Studio Tasarım-Zamanı Özellikleri'nden Faydalanan Windows Forms Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e39f5-102">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>

<span data-ttu-id="e39f5-103">Özel denetim için tasarım zamanı deneyimi, ilişkili bir özel Tasarımcı yazma tarafından geliştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e39f5-103">The design-time experience for a custom control can be enhanced by authoring an associated custom designer.</span></span>

<span data-ttu-id="e39f5-104">Bu izlenecek yol, özel bir denetim için özel bir tasarımcı oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e39f5-104">This walkthrough illustrates how to create a custom designer for a custom control.</span></span> <span data-ttu-id="e39f5-105">Uygulamadan bir `MarqueeControl` türü ve adlı bir ilişkili bir tasarımcı sınıfını `MarqueeControlRootDesigner`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-105">You will implement a `MarqueeControl` type and an associated designer class, called `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="e39f5-106">`MarqueeControl` Tür tiyatro kayan animasyonlu ışıkları ve yanıp sönen metin ile benzer bir ekran uygular.</span><span class="sxs-lookup"><span data-stu-id="e39f5-106">The `MarqueeControl` type implements a display similar to a theater marquee, with animated lights and flashing text.</span></span>

<span data-ttu-id="e39f5-107">Bu denetim için tasarımcı, bir özel tasarım zamanı deneyimi sağlamak için tasarım ortamı ile etkileşime girer.</span><span class="sxs-lookup"><span data-stu-id="e39f5-107">The designer for this control interacts with the design environment to provide a custom design-time experience.</span></span> <span data-ttu-id="e39f5-108">Özel tasarımcı ile özel bir araya `MarqueeControl` uygulamasıyla animasyonlu ışıkları ve birçok birleşimleri yanıp sönen metni.</span><span class="sxs-lookup"><span data-stu-id="e39f5-108">With the custom designer, you can assemble a custom `MarqueeControl` implementation with animated lights and flashing text in many combinations.</span></span> <span data-ttu-id="e39f5-109">Herhangi bir Windows Forms denetimi gibi bir form üzerinde oluşturulmuş denetimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e39f5-109">You can use the assembled control on a form like any other Windows Forms control.</span></span>

<span data-ttu-id="e39f5-110">Bu kılavuzda gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="e39f5-110">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="e39f5-111">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e39f5-111">Creating the Project</span></span>

- <span data-ttu-id="e39f5-112">Bir denetim kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e39f5-112">Creating a Control Library Project</span></span>

- <span data-ttu-id="e39f5-113">Özel denetim projesine başvurma</span><span class="sxs-lookup"><span data-stu-id="e39f5-113">Referencing the Custom Control Project</span></span>

- <span data-ttu-id="e39f5-114">Özel bir denetim ve özel iş Tasarımcısı tanımlama</span><span class="sxs-lookup"><span data-stu-id="e39f5-114">Defining a Custom Control and Its Custom Designer</span></span>

- <span data-ttu-id="e39f5-115">Özel denetim örneği oluşturma</span><span class="sxs-lookup"><span data-stu-id="e39f5-115">Creating an Instance of Your Custom Control</span></span>

- <span data-ttu-id="e39f5-116">Tasarım zamanı hata ayıklama için projeyi ayarlama</span><span class="sxs-lookup"><span data-stu-id="e39f5-116">Setting Up the Project for Design-Time Debugging</span></span>

- <span data-ttu-id="e39f5-117">Özel denetiminizi uygulama</span><span class="sxs-lookup"><span data-stu-id="e39f5-117">Implementing Your Custom Control</span></span>

- <span data-ttu-id="e39f5-118">Özel denetim için bir alt denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e39f5-118">Creating a Child Control for Your Custom Control</span></span>

- <span data-ttu-id="e39f5-119">MarqueeBorder alt denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e39f5-119">Create the MarqueeBorder Child Control</span></span>

- <span data-ttu-id="e39f5-120">Özel bir tasarımcı gölge ve filtre özellikleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="e39f5-120">Creating a Custom Designer to Shadow and Filter Properties</span></span>

- <span data-ttu-id="e39f5-121">Bileşen değişiklikleri işleme</span><span class="sxs-lookup"><span data-stu-id="e39f5-121">Handling Component Changes</span></span>

- <span data-ttu-id="e39f5-122">Tasarımcı fiilleri özel Tasarımcınıza ekleme</span><span class="sxs-lookup"><span data-stu-id="e39f5-122">Adding Designer Verbs to your Custom Designer</span></span>

- <span data-ttu-id="e39f5-123">Özel UITypeEditor oluşturma</span><span class="sxs-lookup"><span data-stu-id="e39f5-123">Creating a Custom UITypeEditor</span></span>

- <span data-ttu-id="e39f5-124">Özel Denetim Tasarımcısı'nda test etme</span><span class="sxs-lookup"><span data-stu-id="e39f5-124">Testing your Custom Control in the Designer</span></span>

<span data-ttu-id="e39f5-125">İşlemi tamamladığınızda, özel denetiminizi aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="e39f5-125">When you are finished, your custom control will look something like the following:</span></span>

<span data-ttu-id="e39f5-126">![Olası MarqueeControl yerleşimi](./media/demomarqueecontrol.gif "DemoMarqueeControl")</span><span class="sxs-lookup"><span data-stu-id="e39f5-126">![A possible MarqueeControl arrangement](./media/demomarqueecontrol.gif "DemoMarqueeControl")</span></span>

<span data-ttu-id="e39f5-127">Tam kod listesi için bkz: [nasıl yapılır: Tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="e39f5-127">For the complete code listing, see [How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).</span></span>

> [!NOTE]
> <span data-ttu-id="e39f5-128">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="e39f5-128">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e39f5-129">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="e39f5-129">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e39f5-130">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="e39f5-130">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e39f5-131">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="e39f5-131">Prerequisites</span></span>

<span data-ttu-id="e39f5-132">Bu izlenecek yolu tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="e39f5-132">In order to complete this walkthrough, you'll need Visual Studio.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="e39f5-133">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e39f5-133">Creating the Project</span></span>

<span data-ttu-id="e39f5-134">İlk adım, uygulama projesi oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="e39f5-134">The first step is to create the application project.</span></span> <span data-ttu-id="e39f5-135">Bu proje, özel denetimin barındıran uygulaması oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="e39f5-135">You will use this project to build the application that hosts the custom control.</span></span>

<span data-ttu-id="e39f5-136">Visual Studio'yu açın ve "MarqueeControlTest" adlı bir Windows Forms uygulaması projesi oluşturun (**dosya** > **yeni** > **proje**  >  **Visual C#**  veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms uygulamalarındaki**).</span><span class="sxs-lookup"><span data-stu-id="e39f5-136">Open Visual Studio and create a Windows Forms Application project called "MarqueeControlTest" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

## <a name="creating-a-control-library-project"></a><span data-ttu-id="e39f5-137">Bir denetim kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e39f5-137">Creating a Control Library Project</span></span>

<span data-ttu-id="e39f5-138">Sonraki adım, denetim kitaplığı projesi oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="e39f5-138">The next step is to create the control library project.</span></span> <span data-ttu-id="e39f5-139">Yeni özel denetim ve karşılık gelen kendi özel Tasarımcısı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="e39f5-139">You will create a new custom control and its corresponding custom designer.</span></span>

### <a name="to-create-the-control-library-project"></a><span data-ttu-id="e39f5-140">Denetim Kitaplığı projesini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e39f5-140">To create the control library project</span></span>

1. <span data-ttu-id="e39f5-141">Bir Windows Forms Denetim Kitaplığı projesi çözüme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e39f5-141">Add a Windows Forms Control Library project to the solution.</span></span> <span data-ttu-id="e39f5-142">"MarqueeControlLibrary." proje adı</span><span class="sxs-lookup"><span data-stu-id="e39f5-142">Name the project "MarqueeControlLibrary."</span></span>

2. <span data-ttu-id="e39f5-143">Kullanarak **Çözüm Gezgini**, istediğiniz dilde bağlı olarak "UserControl1.cs" veya "UserControl1.vb" adlı kaynak dosyası silerek projenin varsayılan denetimini silin.</span><span class="sxs-lookup"><span data-stu-id="e39f5-143">Using **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span> <span data-ttu-id="e39f5-144">Daha fazla bilgi için [nasıl yapılır: , Silme, kaldırmak ve öğeleri hariç](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e39f5-144">For more information, see [How to: Remove, Delete, and Exclude Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span></span>

3. <span data-ttu-id="e39f5-145">Yeni bir <xref:System.Windows.Forms.UserControl> öğesinin `MarqueeControlLibrary` proje.</span><span class="sxs-lookup"><span data-stu-id="e39f5-145">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="e39f5-146">Yeni kaynak dosyası bir temel "MarqueeControl." adını verin</span><span class="sxs-lookup"><span data-stu-id="e39f5-146">Give the new source file a base name of "MarqueeControl."</span></span>

4. <span data-ttu-id="e39f5-147">Kullanarak **Çözüm Gezgini**, yeni bir klasör oluşturun `MarqueeControlLibrary` proje.</span><span class="sxs-lookup"><span data-stu-id="e39f5-147">Using **Solution Explorer**, create a new folder in the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="e39f5-148">Daha fazla bilgi için [nasıl yapılır: Yeni proje öğeleri ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e39f5-148">For more information, see [How to: Add New Project Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span></span> <span data-ttu-id="e39f5-149">Yeni klasörü "Tasarım" olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="e39f5-149">Name the new folder "Design."</span></span>

5. <span data-ttu-id="e39f5-150">Sağ **tasarım** klasör ve bir yeni sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e39f5-150">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="e39f5-151">Kaynak dosyanın temel adı "MarqueeControlRootDesigner." verin</span><span class="sxs-lookup"><span data-stu-id="e39f5-151">Give the source file a base name of "MarqueeControlRootDesigner."</span></span>

6. <span data-ttu-id="e39f5-152">İhtiyacınız olacak System.Design derlemesinden türleri kullanın, böylece bu referansı eklemek `MarqueeControlLibrary` proje.</span><span class="sxs-lookup"><span data-stu-id="e39f5-152">You will need to use types from the System.Design assembly, so add this reference to the `MarqueeControlLibrary` project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e39f5-153">System.Design derleme kullanmak için projenizi değil .NET Framework istemci profili .NET Framework'ün tam sürümünü hedeflemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e39f5-153">To use the System.Design assembly, your project must target the full version of the .NET Framework, not the .NET Framework Client Profile.</span></span> <span data-ttu-id="e39f5-154">Hedef Framework'ü değiştirmek için bkz: [nasıl yapılır: .NET Framework sürümü hedefleme](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="e39f5-154">To change the target framework, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span>

## <a name="referencing-the-custom-control-project"></a><span data-ttu-id="e39f5-155">Özel denetim projesine başvurma</span><span class="sxs-lookup"><span data-stu-id="e39f5-155">Referencing the Custom Control Project</span></span>

<span data-ttu-id="e39f5-156">Kullanacağınız `MarqueeControlTest` özel denetim test etmek için proje.</span><span class="sxs-lookup"><span data-stu-id="e39f5-156">You will use the `MarqueeControlTest` project to test the custom control.</span></span> <span data-ttu-id="e39f5-157">Bir proje başvurusu eklediğinizde, test projesi özel kontrolünü farkına varır `MarqueeControlLibrary` derleme.</span><span class="sxs-lookup"><span data-stu-id="e39f5-157">The test project will become aware of the custom control when you add a project reference to the `MarqueeControlLibrary` assembly.</span></span>

### <a name="to-reference-the-custom-control-project"></a><span data-ttu-id="e39f5-158">Özel denetim projesine başvuruda bulunmak için</span><span class="sxs-lookup"><span data-stu-id="e39f5-158">To reference the custom control project</span></span>

- <span data-ttu-id="e39f5-159">İçinde `MarqueeControlTest` projesi, bir proje başvurusu Ekle `MarqueeControlLibrary` derleme.</span><span class="sxs-lookup"><span data-stu-id="e39f5-159">In the `MarqueeControlTest` project, add a project reference to the `MarqueeControlLibrary` assembly.</span></span> <span data-ttu-id="e39f5-160">Kullandığınızdan emin olun **projeleri** sekmesinde **Başvuru Ekle** başvuran yerine iletişim kutusu `MarqueeControlLibrary` doğrudan derleme.</span><span class="sxs-lookup"><span data-stu-id="e39f5-160">Be sure to use the **Projects** tab in the **Add Reference** dialog box instead of referencing the `MarqueeControlLibrary` assembly directly.</span></span>

## <a name="defining-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="e39f5-161">Özel bir denetim ve özel iş Tasarımcısı tanımlama</span><span class="sxs-lookup"><span data-stu-id="e39f5-161">Defining a Custom Control and Its Custom Designer</span></span>
 <span data-ttu-id="e39f5-162">Öğesinden türetilen özel denetiminizi <xref:System.Windows.Forms.UserControl> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e39f5-162">Your custom control will derive from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="e39f5-163">Bu diğer denetimleri içeren denetim sağlar ve denetiminizi varsayılan işlevsellik harika bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="e39f5-163">This allows your control to contain other controls, and it gives your control a great deal of default functionality.</span></span>

 <span data-ttu-id="e39f5-164">Özel denetim, ilişkili bir özel Tasarımcı sahip olur.</span><span class="sxs-lookup"><span data-stu-id="e39f5-164">Your custom control will have an associated custom designer.</span></span> <span data-ttu-id="e39f5-165">Bu özel denetim için özel olarak uyarlanmış bir benzersiz tasarım deneyimi oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e39f5-165">This allows you to create a unique design experience tailored specifically for your custom control.</span></span>

 <span data-ttu-id="e39f5-166">Denetim kullanarak kendi Tasarımcısı ile ilişkilendirebileceğiniz <xref:System.ComponentModel.DesignerAttribute> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e39f5-166">You associate the control with its designer by using the <xref:System.ComponentModel.DesignerAttribute> class.</span></span> <span data-ttu-id="e39f5-167">Özel denetiminizi tüm tasarım zamanı davranışını geliştiriyorsunuz çünkü özel Tasarımcı uygulayacak <xref:System.ComponentModel.Design.IRootDesigner> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-167">Because you are developing the entire design-time behavior of your custom control, the custom designer will implement the <xref:System.ComponentModel.Design.IRootDesigner> interface.</span></span>

### <a name="to-define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="e39f5-168">Özel bir denetim ve özel iş Tasarımcısı tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="e39f5-168">To define a custom control and its custom designer</span></span>

1. <span data-ttu-id="e39f5-169">Açık `MarqueeControl` kaynak dosyada **Kod Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="e39f5-169">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="e39f5-170">Dosyasının en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="e39f5-170">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. <span data-ttu-id="e39f5-171">Ekleme <xref:System.ComponentModel.DesignerAttribute> için `MarqueeControl` sınıfının bildirimi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-171">Add the <xref:System.ComponentModel.DesignerAttribute> to the `MarqueeControl` class declaration.</span></span> <span data-ttu-id="e39f5-172">Bu özel denetimi iş Tasarımcısı ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="e39f5-172">This associates the custom control with its designer.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. <span data-ttu-id="e39f5-173">Açık `MarqueeControlRootDesigner` kaynak dosyada **Kod Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="e39f5-173">Open the `MarqueeControlRootDesigner` source file in the **Code Editor**.</span></span> <span data-ttu-id="e39f5-174">Dosyasının en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="e39f5-174">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. <span data-ttu-id="e39f5-175">Bildirimini değiştirmek `MarqueeControlRootDesigner` devralınacak <xref:System.Windows.Forms.Design.DocumentDesigner> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e39f5-175">Change the declaration of `MarqueeControlRootDesigner` to inherit from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="e39f5-176">Uygulama <xref:System.ComponentModel.ToolboxItemFilterAttribute> Tasarımcı etkileşimi belirtmek için **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="e39f5-176">Apply the <xref:System.ComponentModel.ToolboxItemFilterAttribute> to specify the designer interaction with the **Toolbox**.</span></span>

     <span data-ttu-id="e39f5-177">**Not** tanımı `MarqueeControlRootDesigner` sınıfı, "MarqueeControlLibrary.Design." adlı bir ad alanında alınmış</span><span class="sxs-lookup"><span data-stu-id="e39f5-177">**Note** The definition for the `MarqueeControlRootDesigner` class has been enclosed in a namespace called "MarqueeControlLibrary.Design."</span></span> <span data-ttu-id="e39f5-178">Bu bildirim Tasarımcısı tasarım ilgili türler için ayrılmış, özel bir isim uzayında yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="e39f5-178">This declaration places the designer in a special namespace reserved for design-related types.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. <span data-ttu-id="e39f5-179">Tanımlamak için oluşturucu `MarqueeControlRootDesigner` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e39f5-179">Define the constructor for the `MarqueeControlRootDesigner` class.</span></span> <span data-ttu-id="e39f5-180">INSERT bir <xref:System.Diagnostics.Trace.WriteLine%2A> Oluşturucu gövdesinde deyimi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-180">Insert a <xref:System.Diagnostics.Trace.WriteLine%2A> statement in the constructor body.</span></span> <span data-ttu-id="e39f5-181">Bu, hata ayıklama amacıyla yararlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e39f5-181">This will be useful for debugging purposes.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="creating-an-instance-of-your-custom-control"></a><span data-ttu-id="e39f5-182">Özel denetim örneği oluşturma</span><span class="sxs-lookup"><span data-stu-id="e39f5-182">Creating an Instance of Your Custom Control</span></span>
 <span data-ttu-id="e39f5-183">Özel tasarım zamanı davranışını gözlemlemek için denetiminizi biçiminde örneğini yerleştireceğiniz `MarqueeControlTest` proje.</span><span class="sxs-lookup"><span data-stu-id="e39f5-183">To observe the custom design-time behavior of your control, you will place an instance of your control on the form in `MarqueeControlTest` project.</span></span>

### <a name="to-create-an-instance-of-your-custom-control"></a><span data-ttu-id="e39f5-184">Özel denetim örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e39f5-184">To create an instance of your custom control</span></span>

1. <span data-ttu-id="e39f5-185">Yeni bir <xref:System.Windows.Forms.UserControl> öğesinin `MarqueeControlTest` proje.</span><span class="sxs-lookup"><span data-stu-id="e39f5-185">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlTest` project.</span></span> <span data-ttu-id="e39f5-186">Yeni kaynak dosyası bir temel "DemoMarqueeControl." adını verin</span><span class="sxs-lookup"><span data-stu-id="e39f5-186">Give the new source file a base name of "DemoMarqueeControl."</span></span>

2. <span data-ttu-id="e39f5-187">Açık `DemoMarqueeControl` dosyası **Kod Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="e39f5-187">Open the `DemoMarqueeControl` file in the **Code Editor**.</span></span> <span data-ttu-id="e39f5-188">İçeri aktarma dosyasının en üstüne `MarqueeControlLibrary` ad alanı:</span><span class="sxs-lookup"><span data-stu-id="e39f5-188">At the top of the file, import the `MarqueeControlLibrary` namespace:</span></span>

```vb
Imports MarqueeControlLibrary
```

```csharp
using MarqueeControlLibrary;
```

1. <span data-ttu-id="e39f5-189">Bildirimini değiştirmek `DemoMarqueeControl` devralınacak `MarqueeControl` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e39f5-189">Change the declaration of `DemoMarqueeControl` to inherit from the `MarqueeControl` class.</span></span>

2. <span data-ttu-id="e39f5-190">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e39f5-190">Build the project.</span></span>

3. <span data-ttu-id="e39f5-191">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="e39f5-191">Open `Form1` in the Windows Forms Designer.</span></span>

4. <span data-ttu-id="e39f5-192">Bulma **MarqueeControlTest bileşenleri** sekmesinde **araç kutusu** ve açın.</span><span class="sxs-lookup"><span data-stu-id="e39f5-192">Find the **MarqueeControlTest Components** tab in the **Toolbox** and open it.</span></span> <span data-ttu-id="e39f5-193">Sürükleme bir `DemoMarqueeControl` gelen **araç kutusu** formunuza.</span><span class="sxs-lookup"><span data-stu-id="e39f5-193">Drag a `DemoMarqueeControl` from the **Toolbox** onto your form.</span></span>

5. <span data-ttu-id="e39f5-194">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e39f5-194">Build the project.</span></span>

## <a name="setting-up-the-project-for-design-time-debugging"></a><span data-ttu-id="e39f5-195">Tasarım zamanı hata ayıklama için projeyi ayarlama</span><span class="sxs-lookup"><span data-stu-id="e39f5-195">Setting Up the Project for Design-Time Debugging</span></span>

<span data-ttu-id="e39f5-196">Özel bir tasarım zamanı deneyimi geliştirirken, denetimleri ve bileşenleri hata ayıklamak gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e39f5-196">When you are developing a custom design-time experience, it will be necessary to debug your controls and components.</span></span> <span data-ttu-id="e39f5-197">Projenizi tasarım zamanında hata ayıklamaya izin verecek şekilde ayarlamak için basit bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="e39f5-197">There is a simple way to set up your project to allow debugging at design time.</span></span> <span data-ttu-id="e39f5-198">Daha fazla bilgi için [izlenecek yol: Tasarım zamanında Forms denetimleri özel Windows hata ayıklama](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="e39f5-198">For more information, see [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>

### <a name="to-set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="e39f5-199">Tasarım zamanı hata ayıklama için projeyi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e39f5-199">To set up the project for design-time debugging</span></span>

1. <span data-ttu-id="e39f5-200">Sağ `MarqueeControlLibrary` seçin ve proje **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="e39f5-200">Right-click the `MarqueeControlLibrary` project and select **Properties**.</span></span>

2. <span data-ttu-id="e39f5-201">"MarqueeControlLibrary özellik sayfaları" iletişim kutusunda **hata ayıklama** sayfası.</span><span class="sxs-lookup"><span data-stu-id="e39f5-201">In the "MarqueeControlLibrary Property Pages" dialog box, select the **Debug** page.</span></span>

3. <span data-ttu-id="e39f5-202">İçinde **başlatma eylemi** bölümünden **harici Program Başlat**.</span><span class="sxs-lookup"><span data-stu-id="e39f5-202">In the **Start Action** section, select **Start External Program**.</span></span> <span data-ttu-id="e39f5-203">Artık Visual Studio, ayrı bir örneğini hata ayıklama şekilde üç nokta simgesine tıklayın (![VisualStudioEllipsesButton ekran](../media/vbellipsesbutton.png "vbEllipsesButton")) Visual Studio IDE için Gözat düğmesini.</span><span class="sxs-lookup"><span data-stu-id="e39f5-203">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="e39f5-204">Devenv.exe yürütülebilir dosya adıdır ve varsayılan bir konuma yüklediyseniz, %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe yoludur.</span><span class="sxs-lookup"><span data-stu-id="e39f5-204">The name of the executable file is devenv.exe, and if you installed to the default location, its path is %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span></span>

4. <span data-ttu-id="e39f5-205">İletişim kutusunu kapatmak için Tamam'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e39f5-205">Click OK to close the dialog box.</span></span>

5. <span data-ttu-id="e39f5-206">Sağ `MarqueeControlLibrary` proje ve "Başlangıç projesi olarak ayarla bu hata ayıklama yapılandırmasını etkinleştirmek için"'i seçin.</span><span class="sxs-lookup"><span data-stu-id="e39f5-206">Right-click the `MarqueeControlLibrary` project and select "Set as StartUp Project" to enable this debugging configuration.</span></span>

## <a name="checkpoint"></a><span data-ttu-id="e39f5-207">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="e39f5-207">Checkpoint</span></span>

<span data-ttu-id="e39f5-208">Özel denetiminizi tasarım zamanı davranışını hata ayıklamak artık hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="e39f5-208">You are now ready to debug the design-time behavior of your custom control.</span></span> <span data-ttu-id="e39f5-209">Hata ayıklama ortamında doğru şekilde ayarlandığını belirledikten sonra özel denetimin özel Tasarımcı arasındaki ilişkiyi test eder.</span><span class="sxs-lookup"><span data-stu-id="e39f5-209">Once you have determined that the debugging environment is set up correctly, you will test the association between the custom control and the custom designer.</span></span>

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a><span data-ttu-id="e39f5-210">Hata ayıklama ortamını ve tasarımcı ilişkilendirme test etmek için</span><span class="sxs-lookup"><span data-stu-id="e39f5-210">To test the debugging environment and the designer association</span></span>

1. <span data-ttu-id="e39f5-211">Açık `MarqueeControlRootDesigner` kaynak dosyada **Kod Düzenleyicisi** ve bir kesme noktası yerleştirmek <xref:System.Diagnostics.Trace.WriteLine%2A> deyimi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-211">Open the `MarqueeControlRootDesigner` source file in the **Code Editor** and place a breakpoint on the <xref:System.Diagnostics.Trace.WriteLine%2A> statement.</span></span>

2. <span data-ttu-id="e39f5-212">Hata ayıklama oturumu başlatmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e39f5-212">Press F5 to start the debugging session.</span></span> <span data-ttu-id="e39f5-213">Visual Studio'nun yeni bir örneğini oluşturulduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e39f5-213">Note that a new instance of Visual Studio is created.</span></span>

3. <span data-ttu-id="e39f5-214">Visual Studio'nun yeni örneğini "MarqueeControlTest" çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="e39f5-214">In the new instance of Visual Studio, open the "MarqueeControlTest" solution.</span></span> <span data-ttu-id="e39f5-215">Çözüm seçerek kolayca bulabilirsiniz **son projeler** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="e39f5-215">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="e39f5-216">En son dosya kullanılan "MarqueeControlTest.sln" Çözüm dosyası listelenir.</span><span class="sxs-lookup"><span data-stu-id="e39f5-216">The "MarqueeControlTest.sln" solution file will be listed as the most recently used file.</span></span>

4. <span data-ttu-id="e39f5-217">Açık `DemoMarqueeControl` Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="e39f5-217">Open the `DemoMarqueeControl` in the designer.</span></span> <span data-ttu-id="e39f5-218">Visual Studio hata ayıklama örneğindeki odağı alır ve yürütmeyi, kesme noktasında durur unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e39f5-218">Note that the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="e39f5-219">Hata ayıklama oturumu devam etmek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e39f5-219">Press F5 to continue the debugging session.</span></span>

<span data-ttu-id="e39f5-220">Bu noktada, gereken her şey, geliştirme ve özel denetiminizi ve onun ilişkili özel Tasarımcı hata ayıklama vardır.</span><span class="sxs-lookup"><span data-stu-id="e39f5-220">At this point, everything is in place for you to develop and debug your custom control and its associated custom designer.</span></span> <span data-ttu-id="e39f5-221">Bu kılavuzda kalan denetim ve tasarımcı özelliklerini uygulama konusunda ayrıntılı bilgi odaklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="e39f5-221">The remainder of this walkthrough will concentrate on the details of implementing features of the control and the designer.</span></span>

## <a name="implementing-your-custom-control"></a><span data-ttu-id="e39f5-222">Özel denetiminizi uygulama</span><span class="sxs-lookup"><span data-stu-id="e39f5-222">Implementing Your Custom Control</span></span>

<span data-ttu-id="e39f5-223">`MarqueeControl` Olduğu bir <xref:System.Windows.Forms.UserControl> ufak bir özelleştirme.</span><span class="sxs-lookup"><span data-stu-id="e39f5-223">The `MarqueeControl` is a <xref:System.Windows.Forms.UserControl> with a little bit of customization.</span></span> <span data-ttu-id="e39f5-224">İki yöntem sunar: `Start`, kayan animasyon başlar ve `Stop`, animasyon durdurur.</span><span class="sxs-lookup"><span data-stu-id="e39f5-224">It exposes two methods: `Start`, which starts the marquee animation, and `Stop`, which stops the animation.</span></span> <span data-ttu-id="e39f5-225">Çünkü `MarqueeControl` uygulayan alt denetimler de içerir `IMarqueeWidget` arabirimi `Start` ve `Stop` her bir alt denetimin ve çağrı listeleme `StartMarquee` ve `StopMarquee` yöntemleri, sırasıyla her alt denetimi hakkında uygulayan `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-225">Because the `MarqueeControl` contains child controls that implement the `IMarqueeWidget` interface, `Start` and `Stop` enumerate each child control and call the `StartMarquee` and `StopMarquee` methods, respectively, on each child control that implements `IMarqueeWidget`.</span></span>

<span data-ttu-id="e39f5-226">Görünümünü `MarqueeBorder` ve `MarqueeText` denetimleri düzen, bağımlı şekilde `MarqueeControl` geçersiz kılmalar <xref:System.Windows.Forms.Control.OnLayout%2A> yöntemi ve çağrıları <xref:System.Windows.Forms.Control.PerformLayout%2A> alt denetimleri bu tür.</span><span class="sxs-lookup"><span data-stu-id="e39f5-226">The appearance of the `MarqueeBorder` and `MarqueeText` controls is dependent on the layout, so `MarqueeControl` overrides the <xref:System.Windows.Forms.Control.OnLayout%2A> method and calls <xref:System.Windows.Forms.Control.PerformLayout%2A> on child controls of this type.</span></span>

<span data-ttu-id="e39f5-227">Bu kapsamı, `MarqueeControl` özelleştirmeler.</span><span class="sxs-lookup"><span data-stu-id="e39f5-227">This is the extent of the `MarqueeControl` customizations.</span></span> <span data-ttu-id="e39f5-228">Çalışma zamanı özellikleri tarafından uygulanan `MarqueeBorder` ve `MarqueeText` denetimleri ve tasarım-zamanı özellikleri tarafından uygulanır `MarqueeBorderDesigner` ve `MarqueeControlRootDesigner` sınıfları.</span><span class="sxs-lookup"><span data-stu-id="e39f5-228">The run-time features are implemented by the `MarqueeBorder` and `MarqueeText` controls, and the design-time features are implemented by the `MarqueeBorderDesigner` and `MarqueeControlRootDesigner` classes.</span></span>

### <a name="to-implement-your-custom-control"></a><span data-ttu-id="e39f5-229">Özel denetim uygulamak için</span><span class="sxs-lookup"><span data-stu-id="e39f5-229">To implement your custom control</span></span>

1. <span data-ttu-id="e39f5-230">Açık `MarqueeControl` kaynak dosyada **Kod Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="e39f5-230">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="e39f5-231">Uygulama `Start` ve `Stop` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="e39f5-231">Implement the `Start` and `Stop` methods.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. <span data-ttu-id="e39f5-232">Geçersiz kılma <xref:System.Windows.Forms.Control.OnLayout%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-232">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="creating-a-child-control-for-your-custom-control"></a><span data-ttu-id="e39f5-233">Özel denetim için bir alt denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e39f5-233">Creating a Child Control for Your Custom Control</span></span>

<span data-ttu-id="e39f5-234">`MarqueeControl` İki tür alt denetimin barındıracak: `MarqueeBorder` denetimi ve `MarqueeText` denetimi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-234">The `MarqueeControl` will host two kinds of child control: the `MarqueeBorder` control and the `MarqueeText` control.</span></span>

- <span data-ttu-id="e39f5-235">`MarqueeBorder`: Bu denetimi "ışıkları" kendi köşelerindeki kenarlığın boyar.</span><span class="sxs-lookup"><span data-stu-id="e39f5-235">`MarqueeBorder`: This control paints a border of "lights" around its edges.</span></span> <span data-ttu-id="e39f5-236">Kenarlık taşıma olması görünmesini ışıkları sırayla flash.</span><span class="sxs-lookup"><span data-stu-id="e39f5-236">The lights flash in sequence, so they appear to be moving around the border.</span></span> <span data-ttu-id="e39f5-237">Başlangıçtan ışıkları flash hızlı adlı bir özellik tarafından denetlenir `UpdatePeriod`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-237">The speed at which the lights flash is controlled by a property called `UpdatePeriod`.</span></span> <span data-ttu-id="e39f5-238">Diğer özel bazı özellikleri denetimin görünümünü diğer yönlerini belirler.</span><span class="sxs-lookup"><span data-stu-id="e39f5-238">Several other custom properties determine other aspects of the control's appearance.</span></span> <span data-ttu-id="e39f5-239">Adlı iki yöntem `StartMarquee` ve `StopMarquee`, animasyon zaman başlatır ve durdurur denetim.</span><span class="sxs-lookup"><span data-stu-id="e39f5-239">Two methods, called `StartMarquee` and `StopMarquee`, control when the animation starts and stops.</span></span>

- <span data-ttu-id="e39f5-240">`MarqueeText`: Bu denetim, yanıp sönen bir dize boyar.</span><span class="sxs-lookup"><span data-stu-id="e39f5-240">`MarqueeText`: This control paints a flashing string.</span></span> <span data-ttu-id="e39f5-241">Gibi `MarqueeBorder` denetimi, metin yanıp hızı tarafından denetlenir `UpdatePeriod` özelliği.</span><span class="sxs-lookup"><span data-stu-id="e39f5-241">Like the `MarqueeBorder` control, the speed at which the text flashes is controlled by the `UpdatePeriod` property.</span></span> <span data-ttu-id="e39f5-242">`MarqueeText` Denetimi de sahip `StartMarquee` ve `StopMarquee` yöntemleri common ile `MarqueeBorder` denetimi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-242">The `MarqueeText` control also has the `StartMarquee` and `StopMarquee` methods in common with the `MarqueeBorder` control.</span></span>

<span data-ttu-id="e39f5-243">Tasarım zamanında `MarqueeControlRootDesigner` eklenmesi bu iki denetim türlerini sağlar bir `MarqueeControl` herhangi bir birleşimini.</span><span class="sxs-lookup"><span data-stu-id="e39f5-243">At design time, the `MarqueeControlRootDesigner` allows these two control types to be added to a `MarqueeControl` in any combination.</span></span>

<span data-ttu-id="e39f5-244">İki denetimin ortak özelliklerini adlı bir arabirim factored `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-244">Common features of the two controls are factored into an interface called `IMarqueeWidget`.</span></span> <span data-ttu-id="e39f5-245">Böylece `MarqueeControl` tüm kayan ilgili alt denetimler bulmak ve onlara özel olarak değerlendirilmesi için.</span><span class="sxs-lookup"><span data-stu-id="e39f5-245">This allows the `MarqueeControl` to discover any Marquee-related child controls and give them special treatment.</span></span>

<span data-ttu-id="e39f5-246">Dönemsel animasyon özelliği uygulamak için kullanacağınız <xref:System.ComponentModel.BackgroundWorker> nesnelerin <xref:System.ComponentModel?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e39f5-246">To implement the periodic animation feature, you will use <xref:System.ComponentModel.BackgroundWorker> objects from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="e39f5-247">Kullanabileceğinizi <xref:System.Windows.Forms.Timer> nesneleri, ne zaman ancak birçok `IMarqueeWidget` nesneleri, tek kullanıcı Arabirimi iş parçacığı ile animasyon yetişemiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="e39f5-247">You could use <xref:System.Windows.Forms.Timer> objects, but when many `IMarqueeWidget` objects are present, the single UI thread may be unable to keep up with the animation.</span></span>

### <a name="to-create-a-child-control-for-your-custom-control"></a><span data-ttu-id="e39f5-248">Özel denetim için bir alt denetimin oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e39f5-248">To create a child control for your custom control</span></span>

1. <span data-ttu-id="e39f5-249">Yeni bir sınıf öğe ekleme `MarqueeControlLibrary` proje.</span><span class="sxs-lookup"><span data-stu-id="e39f5-249">Add a new class item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="e39f5-250">Yeni kaynak dosyası bir temel "IMarqueeWidget." adını verin</span><span class="sxs-lookup"><span data-stu-id="e39f5-250">Give the new source file a base name of "IMarqueeWidget."</span></span>

2. <span data-ttu-id="e39f5-251">Açık `IMarqueeWidget` kaynak dosyada **Kod Düzenleyicisi** bildirimden değiştirip `class` için `interface`:</span><span class="sxs-lookup"><span data-stu-id="e39f5-251">Open the `IMarqueeWidget` source file in the **Code Editor** and change the declaration from `class` to `interface`:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. <span data-ttu-id="e39f5-252">Aşağıdaki kodu ekleyin `IMarqueeWidget` arabirimi iki yöntem ve kayan animasyon işleme bir özelliği göstermek için:</span><span class="sxs-lookup"><span data-stu-id="e39f5-252">Add the following code to the `IMarqueeWidget` interface to expose two methods and a property that manipulate the marquee animation:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. <span data-ttu-id="e39f5-253">Yeni bir **özel denetim** öğesinin `MarqueeControlLibrary` proje.</span><span class="sxs-lookup"><span data-stu-id="e39f5-253">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="e39f5-254">Yeni kaynak dosyası bir temel "MarqueeText." adını verin</span><span class="sxs-lookup"><span data-stu-id="e39f5-254">Give the new source file a base name of "MarqueeText."</span></span>

5. <span data-ttu-id="e39f5-255">Sürükleme bir <xref:System.ComponentModel.BackgroundWorker> bileşenini **araç kutusu** üzerine, `MarqueeText` denetimi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-255">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeText` control.</span></span> <span data-ttu-id="e39f5-256">Bu bileşen sağlayacak `MarqueeText` kendisini zaman uyumsuz olarak güncelleştirmek için denetimi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-256">This component will allow the `MarqueeText` control to update itself asynchronously.</span></span>

6. <span data-ttu-id="e39f5-257">Özellikler penceresinde ayarlayın <xref:System.ComponentModel.BackgroundWorker> bileşenin `WorkerReportsProgress` ve <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliklerine `true`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-257">In the Properties window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to `true`.</span></span> <span data-ttu-id="e39f5-258">Bu ayarlar sağlar. <xref:System.ComponentModel.BackgroundWorker> düzenli aralıklarla yükseltmek için bileşen <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olay ve zaman uyumsuz güncelleştirmeleri iptal etmek için.</span><span class="sxs-lookup"><span data-stu-id="e39f5-258">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span> <span data-ttu-id="e39f5-259">Daha fazla bilgi için [BackgroundWorker bileşeni](backgroundworker-component.md).</span><span class="sxs-lookup"><span data-stu-id="e39f5-259">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

7. <span data-ttu-id="e39f5-260">Açık `MarqueeText` kaynak dosyada **Kod Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="e39f5-260">Open the `MarqueeText` source file in the **Code Editor**.</span></span> <span data-ttu-id="e39f5-261">Dosyasının en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="e39f5-261">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. <span data-ttu-id="e39f5-262">Bildirimini değiştirmek `MarqueeText` devralınacak <xref:System.Windows.Forms.Label> ve uygulamak için `IMarqueeWidget` arabirimi:</span><span class="sxs-lookup"><span data-stu-id="e39f5-262">Change the declaration of `MarqueeText` to inherit from <xref:System.Windows.Forms.Label> and to implement the `IMarqueeWidget` interface:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. <span data-ttu-id="e39f5-263">Kullanıma sunulan özelliklere karşılık gelen örnek değişkenleri tanımlayın ve bunları oluşturucuda başlatmak.</span><span class="sxs-lookup"><span data-stu-id="e39f5-263">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span> <span data-ttu-id="e39f5-264">`isLit` Alanı, metin rengi tarafından verilen boyanacak olup olmadığını belirler `LightColor` özelliği.</span><span class="sxs-lookup"><span data-stu-id="e39f5-264">The `isLit` field determines if the text is to be painted in the color given by the `LightColor` property.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. <span data-ttu-id="e39f5-265">`IMarqueeWidget` arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="e39f5-265">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="e39f5-266">`StartMarquee` Ve `StopMarquee` yöntemleri çağırma <xref:System.ComponentModel.BackgroundWorker> bileşenin <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> ve <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> yöntemleri animasyon durdurmak ve başlatmak.</span><span class="sxs-lookup"><span data-stu-id="e39f5-266">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="e39f5-267"><xref:System.ComponentModel.CategoryAttribute.Category%2A> Ve <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> öznitelikler uygulanır `UpdatePeriod` Özellikler penceresinin "Çerçevesi." adlı özel bir bölümde görüntülenecek şekilde özelliği</span><span class="sxs-lookup"><span data-stu-id="e39f5-267">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to the `UpdatePeriod` property so it appears in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. <span data-ttu-id="e39f5-268">Özellik erişimcisi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e39f5-268">Implement the property accessors.</span></span> <span data-ttu-id="e39f5-269">İstemciler için iki özellik açığa çıkarır: `LightColor` ve `DarkColor`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-269">You will expose two properties to clients: `LightColor` and `DarkColor`.</span></span> <span data-ttu-id="e39f5-270"><xref:System.ComponentModel.CategoryAttribute.Category%2A> Ve <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> özelliklerini Özellikler penceresinde "Çerçevesi." adlı özel bir kısmında görünmesini öznitelikler bu özellikler için uygulanır</span><span class="sxs-lookup"><span data-stu-id="e39f5-270">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to these properties, so the properties appear in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. <span data-ttu-id="e39f5-271">İşleyicileri uygulamak <xref:System.ComponentModel.BackgroundWorker> bileşenin <xref:System.ComponentModel.BackgroundWorker.DoWork> ve <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayları.</span><span class="sxs-lookup"><span data-stu-id="e39f5-271">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="e39f5-272"><xref:System.ComponentModel.BackgroundWorker.DoWork> Olay işleyicisi uyku tarafından belirtilen milisaniye sayısı `UpdatePeriod` ardından başlatır <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> çağırarak animasyon kodunuzu durdurur kadar olay <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="e39f5-272">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="e39f5-273"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Olay işleyicisi yanıp görünümünü sağlamak için açık ve koyu durumuna arasındaki metni değiştirir.</span><span class="sxs-lookup"><span data-stu-id="e39f5-273">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler toggles the text between its light and dark state to give the appearance of flashing.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. <span data-ttu-id="e39f5-274">Geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> animasyon etkinleştirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-274">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method to enable the animation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. <span data-ttu-id="e39f5-275">Çözümü derlemek için F6 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e39f5-275">Press F6 to build the solution.</span></span>

## <a name="create-the-marqueeborder-child-control"></a><span data-ttu-id="e39f5-276">MarqueeBorder alt denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e39f5-276">Create the MarqueeBorder Child Control</span></span>

<span data-ttu-id="e39f5-277">`MarqueeBorder` Denetimidir biraz daha karmaşık `MarqueeText` denetimi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-277">The `MarqueeBorder` control is slightly more sophisticated than the `MarqueeText` control.</span></span> <span data-ttu-id="e39f5-278">Daha fazla özellik ve animasyon sahip <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemdir daha karmaşık.</span><span class="sxs-lookup"><span data-stu-id="e39f5-278">It has more properties and the animation in the <xref:System.Windows.Forms.Control.OnPaint%2A> method is more involved.</span></span> <span data-ttu-id="e39f5-279">İlkesi, oldukça benzer `MarqueeText` denetimi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-279">In principle, it is quite similar to the `MarqueeText` control.</span></span>

<span data-ttu-id="e39f5-280">Çünkü `MarqueeBorder` denetimi alt denetimler sahip olabilir, farkında olmanız gereken <xref:System.Windows.Forms.Control.Layout> olayları.</span><span class="sxs-lookup"><span data-stu-id="e39f5-280">Because the `MarqueeBorder` control can have child controls, it needs to be aware of <xref:System.Windows.Forms.Control.Layout> events.</span></span>

### <a name="to-create-the-marqueeborder-control"></a><span data-ttu-id="e39f5-281">MarqueeBorder denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e39f5-281">To create the MarqueeBorder control</span></span>

1. <span data-ttu-id="e39f5-282">Yeni bir **özel denetim** öğesinin `MarqueeControlLibrary` proje.</span><span class="sxs-lookup"><span data-stu-id="e39f5-282">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="e39f5-283">Yeni kaynak dosyası bir temel "MarqueeBorder." adını verin</span><span class="sxs-lookup"><span data-stu-id="e39f5-283">Give the new source file a base name of "MarqueeBorder."</span></span>

2. <span data-ttu-id="e39f5-284">Sürükleme bir <xref:System.ComponentModel.BackgroundWorker> bileşenini **araç kutusu** üzerine, `MarqueeBorder` denetimi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-284">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeBorder` control.</span></span> <span data-ttu-id="e39f5-285">Bu bileşen sağlayacak `MarqueeBorder` kendisini zaman uyumsuz olarak güncelleştirmek için denetimi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-285">This component will allow the `MarqueeBorder` control to update itself asynchronously.</span></span>

3. <span data-ttu-id="e39f5-286">Özellikler penceresinde ayarlayın <xref:System.ComponentModel.BackgroundWorker> bileşenin `WorkerReportsProgress` ve <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliklerine `true`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-286">In the Properties window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to `true`.</span></span> <span data-ttu-id="e39f5-287">Bu ayarlar sağlar. <xref:System.ComponentModel.BackgroundWorker> düzenli aralıklarla yükseltmek için bileşen <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olay ve zaman uyumsuz güncelleştirmeleri iptal etmek için.</span><span class="sxs-lookup"><span data-stu-id="e39f5-287">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span> <span data-ttu-id="e39f5-288">Daha fazla bilgi için [BackgroundWorker bileşeni](backgroundworker-component.md).</span><span class="sxs-lookup"><span data-stu-id="e39f5-288">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

4. <span data-ttu-id="e39f5-289">Özellikler penceresinde olayları düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e39f5-289">In the Properties window, click the Events button.</span></span> <span data-ttu-id="e39f5-290">İşleyicileri eklemek <xref:System.ComponentModel.BackgroundWorker.DoWork> ve <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayları.</span><span class="sxs-lookup"><span data-stu-id="e39f5-290">Attach handlers for the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

5. <span data-ttu-id="e39f5-291">Açık `MarqueeBorder` kaynak dosyada **Kod Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="e39f5-291">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span> <span data-ttu-id="e39f5-292">Dosyasının en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="e39f5-292">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. <span data-ttu-id="e39f5-293">Bildirimini değiştirmek `MarqueeBorder` devralınacak <xref:System.Windows.Forms.Panel> ve uygulamak için `IMarqueeWidget` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-293">Change the declaration of `MarqueeBorder` to inherit from <xref:System.Windows.Forms.Panel> and to implement the `IMarqueeWidget` interface.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. <span data-ttu-id="e39f5-294">Yönetmek için iki sabit listesi bildirme `MarqueeBorder` denetimin durumunu: `MarqueeSpinDirection`, hangi ışıkları "döndürme" kenarlık yönü belirler ve `MarqueeLightShape`, ışıkları (kare veya döngüsel) şeklini belirler.</span><span class="sxs-lookup"><span data-stu-id="e39f5-294">Declare two enumerations for managing the `MarqueeBorder` control's state: `MarqueeSpinDirection`, which determines the direction in which the lights "spin" around the border, and `MarqueeLightShape`, which determines the shape of the lights (square or circular).</span></span> <span data-ttu-id="e39f5-295">Bu bildirimler önce yerleştirin `MarqueeBorder` sınıfının bildirimi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-295">Place these declarations before the `MarqueeBorder` class declaration.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. <span data-ttu-id="e39f5-296">Kullanıma sunulan özelliklere karşılık gelen örnek değişkenleri tanımlayın ve bunları oluşturucuda başlatmak.</span><span class="sxs-lookup"><span data-stu-id="e39f5-296">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. <span data-ttu-id="e39f5-297">`IMarqueeWidget` arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="e39f5-297">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="e39f5-298">`StartMarquee` Ve `StopMarquee` yöntemleri çağırma <xref:System.ComponentModel.BackgroundWorker> bileşenin <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> ve <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> yöntemleri animasyon durdurmak ve başlatmak.</span><span class="sxs-lookup"><span data-stu-id="e39f5-298">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="e39f5-299">Çünkü `MarqueeBorder` denetimi alt denetimler içerebilir `StartMarquee` yöntemi, tüm alt denetimleri ve çağrıları numaralandırır `StartMarquee` uygulayan bu `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-299">Because the `MarqueeBorder` control can contain child controls, the `StartMarquee` method enumerates all child controls and calls `StartMarquee` on those that implement `IMarqueeWidget`.</span></span> <span data-ttu-id="e39f5-300">`StopMarquee` Yöntemi benzer bir uygulaması vardır.</span><span class="sxs-lookup"><span data-stu-id="e39f5-300">The `StopMarquee` method has a similar implementation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. <span data-ttu-id="e39f5-301">Özellik erişimcisi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e39f5-301">Implement the property accessors.</span></span> <span data-ttu-id="e39f5-302">`MarqueeBorder` Denetiminin görünümünü denetlemek için çeşitli özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e39f5-302">The `MarqueeBorder` control has several properties for controlling its appearance.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. <span data-ttu-id="e39f5-303">İşleyicileri uygulamak <xref:System.ComponentModel.BackgroundWorker> bileşenin <xref:System.ComponentModel.BackgroundWorker.DoWork> ve <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayları.</span><span class="sxs-lookup"><span data-stu-id="e39f5-303">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="e39f5-304"><xref:System.ComponentModel.BackgroundWorker.DoWork> Olay işleyicisi uyku tarafından belirtilen milisaniye sayısı `UpdatePeriod` ardından başlatır <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> çağırarak animasyon kodunuzu durdurur kadar olay <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="e39f5-304">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="e39f5-305"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Olay işleyicisi, diğer ışıkları açık/koyu durumu belirlenir, "temel" ışık ve çağrıları konumunu artırır <xref:System.Windows.Forms.Control.Refresh%2A> kendisini çizilecek denetimi neden için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-305">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler increments the position of the "base" light, from which the light/dark state of the other lights is determined, and calls the <xref:System.Windows.Forms.Control.Refresh%2A> method to cause the control to repaint itself.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. <span data-ttu-id="e39f5-306">Yardımcı yöntemler uygulamak `IsLit` ve `DrawLight`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-306">Implement the helper methods, `IsLit` and `DrawLight`.</span></span>

    <span data-ttu-id="e39f5-307">`IsLit` Yöntemi, belirtilen konumda bir ışığın rengini belirler.</span><span class="sxs-lookup"><span data-stu-id="e39f5-307">The `IsLit` method determines the color of a light at a given position.</span></span> <span data-ttu-id="e39f5-308">"Aydınlatma" ışık rengi tarafından verilen çizilmiştir `LightColor` özellik ve "koyu" olanlar tarafından verilen renkli çizilmiştir `DarkColor` özelliği.</span><span class="sxs-lookup"><span data-stu-id="e39f5-308">Lights that are "lit" are drawn in the color given by the `LightColor` property, and those that are "dark" are drawn in the color given by the `DarkColor` property.</span></span>

    <span data-ttu-id="e39f5-309">`DrawLight` Yöntemi bir ışık uygun rengini, Şekil ve konumu kullanarak çizer.</span><span class="sxs-lookup"><span data-stu-id="e39f5-309">The `DrawLight` method draws a light using the appropriate color, shape, and position.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. <span data-ttu-id="e39f5-310">Geçersiz kılma <xref:System.Windows.Forms.Control.OnLayout%2A> ve <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="e39f5-310">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> and <xref:System.Windows.Forms.Control.OnPaint%2A> methods.</span></span>

    <span data-ttu-id="e39f5-311"><xref:System.Windows.Forms.Control.OnPaint%2A> Yöntemi çizer kenarlarında ışıkları `MarqueeBorder` denetimi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-311">The <xref:System.Windows.Forms.Control.OnPaint%2A> method draws the lights along the edges of the `MarqueeBorder` control.</span></span>

    <span data-ttu-id="e39f5-312">Çünkü <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi bağlıdır boyutlarını üzerinde `MarqueeBorder` denetime ihtiyacınız düzeni değiştiğinde çağırmak.</span><span class="sxs-lookup"><span data-stu-id="e39f5-312">Because the <xref:System.Windows.Forms.Control.OnPaint%2A> method depends on the dimensions of the `MarqueeBorder` control, you need to call it whenever the layout changes.</span></span> <span data-ttu-id="e39f5-313">Bunu başarmak için geçersiz kılma <xref:System.Windows.Forms.Control.OnLayout%2A> ve çağrı <xref:System.Windows.Forms.Control.Refresh%2A>.</span><span class="sxs-lookup"><span data-stu-id="e39f5-313">To achieve this, override <xref:System.Windows.Forms.Control.OnLayout%2A> and call <xref:System.Windows.Forms.Control.Refresh%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="creating-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="e39f5-314">Özel bir tasarımcı gölge ve filtre özellikleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="e39f5-314">Creating a Custom Designer to Shadow and Filter Properties</span></span>

<span data-ttu-id="e39f5-315">`MarqueeControlRootDesigner` Sınıfı kök Tasarımcısı uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e39f5-315">The `MarqueeControlRootDesigner` class provides the implementation for the root designer.</span></span> <span data-ttu-id="e39f5-316">Bu tasarımcı yanı sıra çalıştığı üzerinde `MarqueeControl`, özellikle ile ilişkili özel bir tasarımcı ihtiyacınız olacak `MarqueeBorder` denetimi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-316">In addition to this designer, which operates on the `MarqueeControl`, you will need a custom designer that is specifically associated with the `MarqueeBorder` control.</span></span> <span data-ttu-id="e39f5-317">Bu tasarımcı özel kök Tasarımcı bağlamında uygun özel davranış sağlar.</span><span class="sxs-lookup"><span data-stu-id="e39f5-317">This designer provides custom behavior that is appropriate in the context of the custom root designer.</span></span>

<span data-ttu-id="e39f5-318">Özellikle, `MarqueeBorderDesigner` "gölge" ve belirli özellikleri üzerinde filtre `MarqueeBorder` denetimi tasarım ortamı ile kendi etkileşimi değiştirme.</span><span class="sxs-lookup"><span data-stu-id="e39f5-318">Specifically, the `MarqueeBorderDesigner` will "shadow" and filter certain properties on the `MarqueeBorder` control, changing their interaction with the design environment.</span></span>

<span data-ttu-id="e39f5-319">Bir bileşenin özellik erişimcisi çağrıları kesintiye "gölgeleme olarak." adı verilir</span><span class="sxs-lookup"><span data-stu-id="e39f5-319">Intercepting calls to a component's property accessor is known as "shadowing."</span></span> <span data-ttu-id="e39f5-320">Bu kullanıcı tarafından ayarlanan değer izlemek bir tasarımcı sağlar ve isteğe bağlı olarak bu değeri tasarlanmakta bileşenine geçirin.</span><span class="sxs-lookup"><span data-stu-id="e39f5-320">It allows a designer to track the value set by the user and optionally pass that value to the component being designed.</span></span>

<span data-ttu-id="e39f5-321">Bu örnekte, <xref:System.Windows.Forms.Control.Visible%2A> ve <xref:System.Windows.Forms.Control.Enabled%2A> özellikleri gölgeli tarafından `MarqueeBorderDesigner`, gelen yapma kullanıcı engeller `MarqueeBorder` görünmez ya da devre dışı tasarım zamanında denetimi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-321">For this example, the <xref:System.Windows.Forms.Control.Visible%2A> and <xref:System.Windows.Forms.Control.Enabled%2A> properties will be shadowed by the `MarqueeBorderDesigner`, which prevents the user from making the `MarqueeBorder` control invisible or disabled during design time.</span></span>

<span data-ttu-id="e39f5-322">Tasarımcılar, ayrıca ekleyebilir ve özellikleri Kaldır.</span><span class="sxs-lookup"><span data-stu-id="e39f5-322">Designers can also add and remove properties.</span></span> <span data-ttu-id="e39f5-323">Bu örnekte, <xref:System.Windows.Forms.Control.Padding%2A> özelliği için tasarım zamanında kaldırılacak `MarqueeBorder` denetimi program aracılığıyla doldurma tarafından belirtilen ışıkları boyutuna göre ayarlar `LightSize` özelliği.</span><span class="sxs-lookup"><span data-stu-id="e39f5-323">For this example, the <xref:System.Windows.Forms.Control.Padding%2A> property will be removed at design time, because the `MarqueeBorder` control programmatically sets the padding based on the size of the lights specified by the `LightSize` property.</span></span>

<span data-ttu-id="e39f5-324">Temel sınıfı `MarqueeBorderDesigner` olduğu <xref:System.ComponentModel.Design.ComponentDesigner>, öznitelikler, özellikleri ve olayları tasarım zamanında denetimi tarafından kullanıma sunulan değiştirebilirsiniz yöntemleri vardır:</span><span class="sxs-lookup"><span data-stu-id="e39f5-324">The base class for `MarqueeBorderDesigner` is <xref:System.ComponentModel.Design.ComponentDesigner>, which has methods that can change the attributes, properties, and events exposed by a control at design time:</span></span>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

<span data-ttu-id="e39f5-325">Bu yöntemleri kullanarak bir bileşenin genel arabirimi değiştirilirken şu kurallara uymalıdır:</span><span class="sxs-lookup"><span data-stu-id="e39f5-325">When changing the public interface of a component using these methods, you must follow these rules:</span></span>

- <span data-ttu-id="e39f5-326">Ekleme veya öğeleri kaldırma `PreFilter` yalnızca yöntemleri</span><span class="sxs-lookup"><span data-stu-id="e39f5-326">Add or remove items in the `PreFilter` methods only</span></span>

- <span data-ttu-id="e39f5-327">Mevcut öğelerini `PostFilter` yalnızca yöntemleri</span><span class="sxs-lookup"><span data-stu-id="e39f5-327">Modify existing items in the `PostFilter` methods only</span></span>

- <span data-ttu-id="e39f5-328">Her zaman temel uygulamayı ilk kez çağırmak `PreFilter` yöntemleri</span><span class="sxs-lookup"><span data-stu-id="e39f5-328">Always call the base implementation first in the `PreFilter` methods</span></span>

- <span data-ttu-id="e39f5-329">Her zaman temel uygulamayı son çağırması `PostFilter` yöntemleri</span><span class="sxs-lookup"><span data-stu-id="e39f5-329">Always call the base implementation last in the `PostFilter` methods</span></span>

<span data-ttu-id="e39f5-330">Bu kurallarına uymak için tasarım zamanı ortamında tüm tasarımcıları tasarlanmakta olan tüm bileşenlerin tutarlı bir görünüm sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e39f5-330">Adhering to these rules ensures that all designers in the design-time environment have a consistent view of all components being designed.</span></span>

<span data-ttu-id="e39f5-331"><xref:System.ComponentModel.Design.ComponentDesigner> Sınıfı gölgeli özelliklerinin değerleri, belirli bir örneği değişkenleri oluşturmak üzere gerek kalmamasını yönetmek için bir sözlüğünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="e39f5-331">The <xref:System.ComponentModel.Design.ComponentDesigner> class provides a dictionary for managing the values of shadowed properties, which relieves you of the need to create specific instance variables.</span></span>

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="e39f5-332">Gölge ve filtre özellikleri için özel bir tasarımcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e39f5-332">To create a custom designer to shadow and filter properties</span></span>

1. <span data-ttu-id="e39f5-333">Sağ **tasarım** klasör ve bir yeni sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e39f5-333">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="e39f5-334">Kaynak dosyanın temel adı "MarqueeBorderDesigner." verin</span><span class="sxs-lookup"><span data-stu-id="e39f5-334">Give the source file a base name of "MarqueeBorderDesigner."</span></span>

2. <span data-ttu-id="e39f5-335">Açık `MarqueeBorderDesigner` kaynak dosyada **Kod Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="e39f5-335">Open the `MarqueeBorderDesigner` source file in the **Code Editor**.</span></span> <span data-ttu-id="e39f5-336">Dosyasının en üstüne aşağıdaki ad alanlarını içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="e39f5-336">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. <span data-ttu-id="e39f5-337">Bildirimini değiştirmek `MarqueeBorderDesigner` devralınacak <xref:System.Windows.Forms.Design.ParentControlDesigner>.</span><span class="sxs-lookup"><span data-stu-id="e39f5-337">Change the declaration of `MarqueeBorderDesigner` to inherit from <xref:System.Windows.Forms.Design.ParentControlDesigner>.</span></span>

    <span data-ttu-id="e39f5-338">Çünkü `MarqueeBorder` denetimi alt denetimler içerebilir `MarqueeBorderDesigner` devraldığı <xref:System.Windows.Forms.Design.ParentControlDesigner>, üst-alt etkileşimini işler.</span><span class="sxs-lookup"><span data-stu-id="e39f5-338">Because the `MarqueeBorder` control can contain child controls, `MarqueeBorderDesigner` inherits from <xref:System.Windows.Forms.Design.ParentControlDesigner>, which handles the parent-child interaction.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. <span data-ttu-id="e39f5-339">Taban uygulamasını geçersiz kılma <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.</span><span class="sxs-lookup"><span data-stu-id="e39f5-339">Override the base implementation of <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. <span data-ttu-id="e39f5-340">Uygulama <xref:System.Windows.Forms.Control.Enabled%2A> ve <xref:System.Windows.Forms.Control.Visible%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="e39f5-340">Implement the <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A> properties.</span></span> <span data-ttu-id="e39f5-341">Bu uygulamalar, denetimin özelliklerini gölge.</span><span class="sxs-lookup"><span data-stu-id="e39f5-341">These implementations shadow the control's properties.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handling-component-changes"></a><span data-ttu-id="e39f5-342">Bileşen değişiklikleri işleme</span><span class="sxs-lookup"><span data-stu-id="e39f5-342">Handling Component Changes</span></span>
 <span data-ttu-id="e39f5-343">`MarqueeControlRootDesigner` Sınıfı için özel tasarım zamanı deneyimi sağlar, `MarqueeControl` örnekleri.</span><span class="sxs-lookup"><span data-stu-id="e39f5-343">The `MarqueeControlRootDesigner` class provides the custom design-time experience for your `MarqueeControl` instances.</span></span> <span data-ttu-id="e39f5-344">Tasarım zamanı işlevselliği çoğunu devralınır <xref:System.Windows.Forms.Design.DocumentDesigner> sınıfı; iki belirli özelleştirmeleri uygulamak, kod olacaktır: bileşen değişiklikleri işleme ve tasarımcı fiilleri ekleme.</span><span class="sxs-lookup"><span data-stu-id="e39f5-344">Most of the design-time functionality is inherited from the <xref:System.Windows.Forms.Design.DocumentDesigner> class; your code will implement two specific customizations: handling component changes, and adding designer verbs.</span></span>

 <span data-ttu-id="e39f5-345">Kullanıcıların tasarım olarak kendi `MarqueeControl` örnekleri, kök tasarımcınıza değişiklikleri izleyecek `MarqueeControl` ve onun alt denetimler.</span><span class="sxs-lookup"><span data-stu-id="e39f5-345">As users design their `MarqueeControl` instances, your root designer will track changes to the `MarqueeControl` and its child controls.</span></span> <span data-ttu-id="e39f5-346">Tasarım zamanı ortamında uygun bir hizmet sunar <xref:System.ComponentModel.Design.IComponentChangeService>, bileşen durumu için izleme dönüşür.</span><span class="sxs-lookup"><span data-stu-id="e39f5-346">The design-time environment offers a convenient service, <xref:System.ComponentModel.Design.IComponentChangeService>, for tracking changes to component state.</span></span>

 <span data-ttu-id="e39f5-347">Ortamıyla sorgulayarak bu hizmet için bir başvuru alma <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-347">You acquire a reference to this service by querying the environment with the <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> method.</span></span> <span data-ttu-id="e39f5-348">Sorgu başarılı olursa, tasarımcınıza bir işleyici ekleyebilirsiniz <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> olay ve tutarlı bir duruma tasarım zamanında korumak için gerekli tüm görevleri gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="e39f5-348">If the query is successful, your designer can attach a handler for the <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> event and perform whatever tasks are required to maintain a consistent state at design time.</span></span>

 <span data-ttu-id="e39f5-349">Durumunda, `MarqueeControlRootDesigner` sınıfı çağıracaktır <xref:System.Windows.Forms.Control.Refresh%2A> yöntemi her `IMarqueeWidget` nesnesi tarafından içerilen `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-349">In the case of the `MarqueeControlRootDesigner` class, you will call the <xref:System.Windows.Forms.Control.Refresh%2A> method on each `IMarqueeWidget` object contained by the `MarqueeControl`.</span></span> <span data-ttu-id="e39f5-350">Bu neden `IMarqueeWidget` nesnenin kendisini uygun özellikler, üst beğendiğinizde repaint <xref:System.Windows.Forms.Control.Size%2A> değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="e39f5-350">This will cause the `IMarqueeWidget` object to repaint itself appropriately when properties like its parent's <xref:System.Windows.Forms.Control.Size%2A> are changed.</span></span>

### <a name="to-handle-component-changes"></a><span data-ttu-id="e39f5-351">Bileşen değişiklikleri işlemek için</span><span class="sxs-lookup"><span data-stu-id="e39f5-351">To handle component changes</span></span>

1. <span data-ttu-id="e39f5-352">Açık `MarqueeControlRootDesigner` kaynak dosyada **Kod Düzenleyicisi** ve geçersiz kılma <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-352">Open the `MarqueeControlRootDesigner` source file in the **Code Editor** and override the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span> <span data-ttu-id="e39f5-353">' In temel uygulamayı çağırması <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> ve sorgu <xref:System.ComponentModel.Design.IComponentChangeService>.</span><span class="sxs-lookup"><span data-stu-id="e39f5-353">Call the base implementation of <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> and query for the <xref:System.ComponentModel.Design.IComponentChangeService>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. <span data-ttu-id="e39f5-354">Uygulama <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-354">Implement the <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> event handler.</span></span> <span data-ttu-id="e39f5-355">Test gönderen bileşenin türü ve ise bir `IMarqueeWidget`, arama, <xref:System.Windows.Forms.Control.Refresh%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-355">Test the sending component's type, and if it is an `IMarqueeWidget`, call its <xref:System.Windows.Forms.Control.Refresh%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="adding-designer-verbs-to-your-custom-designer"></a><span data-ttu-id="e39f5-356">Tasarımcı fiilleri özel Tasarımcınıza ekleme</span><span class="sxs-lookup"><span data-stu-id="e39f5-356">Adding Designer Verbs to your Custom Designer</span></span>

<span data-ttu-id="e39f5-357">Tasarımcı fiil bir olay işleyicisi için bağlı bir menü komutu ' dir.</span><span class="sxs-lookup"><span data-stu-id="e39f5-357">A designer verb is a menu command linked to an event handler.</span></span> <span data-ttu-id="e39f5-358">Tasarımcı fiilleri tasarım zamanında bir bileşenin kısayol menüsüne eklenir.</span><span class="sxs-lookup"><span data-stu-id="e39f5-358">Designer verbs are added to a component's shortcut menu at design time.</span></span> <span data-ttu-id="e39f5-359">Daha fazla bilgi için bkz. <xref:System.ComponentModel.Design.DesignerVerb>.</span><span class="sxs-lookup"><span data-stu-id="e39f5-359">For more information, see <xref:System.ComponentModel.Design.DesignerVerb>.</span></span>

<span data-ttu-id="e39f5-360">Tasarımcılar, iki Tasarımcı fiilleri ekler: **Test çalıştırması** ve **durdurma Test**.</span><span class="sxs-lookup"><span data-stu-id="e39f5-360">You will add two designer verbs to your designers: **Run Test** and **Stop Test**.</span></span> <span data-ttu-id="e39f5-361">Bu Eylemler, çalışma zamanı davranışını görüntülemenize olanak sağlayacak `MarqueeControl` tasarım zamanında.</span><span class="sxs-lookup"><span data-stu-id="e39f5-361">These verbs will allow you to view the run-time behavior of the `MarqueeControl` at design time.</span></span> <span data-ttu-id="e39f5-362">Bu eylemler eklenecek `MarqueeControlRootDesigner`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-362">These verbs will be added to the `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="e39f5-363">Zaman **Test çalıştırması** olan çağrılır, fiil olay işleyiciyi çağırır `StartMarquee` metodunda `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-363">When **Run Test** is invoked, the verb event handler will call the `StartMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="e39f5-364">Zaman **durdurma Test** olan çağrılır, fiil olay işleyiciyi çağırır `StopMarquee` metodunda `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-364">When **Stop Test** is invoked, the verb event handler will call the `StopMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="e39f5-365">Uygulamasını `StartMarquee` ve `StopMarquee` uygulayan içerdiği denetimlerle üzerinde yöntemleri çağırmak bu yöntemleri `IMarqueeWidget`, bu nedenle tüm kapsanan `IMarqueeWidget` denetimleri de test katılın.</span><span class="sxs-lookup"><span data-stu-id="e39f5-365">The implementation of the `StartMarquee` and `StopMarquee` methods call these methods on contained controls that implement `IMarqueeWidget`, so any contained `IMarqueeWidget` controls will also participate in the test.</span></span>

### <a name="to-add-designer-verbs-to-your-custom-designers"></a><span data-ttu-id="e39f5-366">Özel, tasarımcılar için tasarımcı fiilleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="e39f5-366">To add designer verbs to your custom designers</span></span>

1. <span data-ttu-id="e39f5-367">İçinde `MarqueeControlRootDesigner` sınıf, olay işleyicileri adlı ekleme `OnVerbRunTest` ve `OnVerbStopTest`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-367">In the `MarqueeControlRootDesigner` class, add event handlers named `OnVerbRunTest` and `OnVerbStopTest`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. <span data-ttu-id="e39f5-368">Bu olay işleyicileri için karşılık gelen, Tasarımcı fiilleri bağlanın.</span><span class="sxs-lookup"><span data-stu-id="e39f5-368">Connect these event handlers to their corresponding designer verbs.</span></span> <span data-ttu-id="e39f5-369">`MarqueeControlRootDesigner` devralınan bir <xref:System.ComponentModel.Design.DesignerVerbCollection> taban sınıfından.</span><span class="sxs-lookup"><span data-stu-id="e39f5-369">`MarqueeControlRootDesigner` inherits a <xref:System.ComponentModel.Design.DesignerVerbCollection> from its base class.</span></span> <span data-ttu-id="e39f5-370">İki yeni oluşturacak <xref:System.ComponentModel.Design.DesignerVerb> nesneleri ve bu koleksiyonda ekleme <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-370">You will create two new <xref:System.ComponentModel.Design.DesignerVerb> objects and add them to this collection in the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="creating-a-custom-uitypeeditor"></a><span data-ttu-id="e39f5-371">Özel UITypeEditor oluşturma</span><span class="sxs-lookup"><span data-stu-id="e39f5-371">Creating a Custom UITypeEditor</span></span>

<span data-ttu-id="e39f5-372">Kullanıcılar için özel bir tasarım zamanı deneyimi oluşturduğunuzda, genellikle bir özel özellikler penceresini etkileşim oluşturmak için tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="e39f5-372">When you create a custom design-time experience for users, it is often desirable to create a custom interaction with the Properties window.</span></span> <span data-ttu-id="e39f5-373">Oluşturarak bunu gerçekleştirebilirsiniz bir <xref:System.Drawing.Design.UITypeEditor>.</span><span class="sxs-lookup"><span data-stu-id="e39f5-373">You can accomplish this by creating a <xref:System.Drawing.Design.UITypeEditor>.</span></span> <span data-ttu-id="e39f5-374">Daha fazla bilgi için [nasıl yapılır: UI türü düzenleyici oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fd3kt7d5(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="e39f5-374">For more information, see [How to: Create a UI Type Editor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fd3kt7d5(v=vs.120)).</span></span>

<span data-ttu-id="e39f5-375">`MarqueeBorder` Denetimi Özellikler penceresindeki çeşitli özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="e39f5-375">The `MarqueeBorder` control exposes several properties in the Properties window.</span></span> <span data-ttu-id="e39f5-376">Bu özelliklerin iki `MarqueeSpinDirection` ve `MarqueeLightShape` numaralandırmalar tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="e39f5-376">Two of these properties, `MarqueeSpinDirection` and `MarqueeLightShape` are represented by enumerations.</span></span> <span data-ttu-id="e39f5-377">UI türü Düzenleyici kullanımını göstermek için `MarqueeLightShape` özellik ilişkili bir olacaktır <xref:System.Drawing.Design.UITypeEditor> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e39f5-377">To illustrate the use of a UI type editor, the `MarqueeLightShape` property will have an associated <xref:System.Drawing.Design.UITypeEditor> class.</span></span>

### <a name="to-create-a-custom-ui-type-editor"></a><span data-ttu-id="e39f5-378">Özel bir UI türü düzenleyici oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e39f5-378">To create a custom UI type editor</span></span>

1. <span data-ttu-id="e39f5-379">Açık `MarqueeBorder` kaynak dosyada **Kod Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="e39f5-379">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span>

2. <span data-ttu-id="e39f5-380">Tanımındaki `MarqueeBorder` sınıfı, adında bir sınıf bildirme `LightShapeEditor` türetilen <xref:System.Drawing.Design.UITypeEditor>.</span><span class="sxs-lookup"><span data-stu-id="e39f5-380">In the definition of the `MarqueeBorder` class, declare a class called `LightShapeEditor` that derives from <xref:System.Drawing.Design.UITypeEditor>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. <span data-ttu-id="e39f5-381">Bildirme bir <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> adlı örnek değişkeni `editorService`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-381">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. <span data-ttu-id="e39f5-382">Geçersiz kılma <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-382">Override the <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> method.</span></span> <span data-ttu-id="e39f5-383">Bu uygulama döndürür <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, nasıl görüntüleneceğini tasarım ortamı söyler `LightShapeEditor`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-383">This implementation returns <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, which tells the design environment how to display the `LightShapeEditor`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. <span data-ttu-id="e39f5-384">Geçersiz kılma <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-384">Override the <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> method.</span></span> <span data-ttu-id="e39f5-385">Bu uygulama için tasarım ortamı sorgular bir <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> nesne.</span><span class="sxs-lookup"><span data-stu-id="e39f5-385">This implementation queries the design environment for an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> object.</span></span> <span data-ttu-id="e39f5-386">Başarılı oluşturur, bir `LightShapeSelectionControl`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-386">If successful, it creates a `LightShapeSelectionControl`.</span></span> <span data-ttu-id="e39f5-387"><xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> Metodunu çağırmak başlatmak için `LightShapeEditor`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-387">The <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> method is invoked to start the `LightShapeEditor`.</span></span> <span data-ttu-id="e39f5-388">Bu çağrıyı dönüş değeri, tasarım ortama döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e39f5-388">The return value from this invocation is returned to the design environment.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="creating-a-view-control-for-your-custom-uitypeeditor"></a><span data-ttu-id="e39f5-389">Bir View denetimi için özel UITypeEditor oluşturma</span><span class="sxs-lookup"><span data-stu-id="e39f5-389">Creating a View Control for your Custom UITypeEditor</span></span>

1. <span data-ttu-id="e39f5-390">`MarqueeLightShape` Özelliğini destekleyen iki tür açık şekiller: `Square` ve `Circle`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-390">The `MarqueeLightShape` property supports two types of light shapes: `Square` and `Circle`.</span></span> <span data-ttu-id="e39f5-391">Bu değerleri Özellikler penceresinde görüntüleme grafik ile amacıyla yalnızca kullanılan özel bir denetim oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="e39f5-391">You will create a custom control used solely for the purpose of graphically displaying these values in the Properties window.</span></span> <span data-ttu-id="e39f5-392">Bu özel denetimi tarafından kullanılan, <xref:System.Drawing.Design.UITypeEditor> Özellikler penceresi ile etkileşim kurmak için.</span><span class="sxs-lookup"><span data-stu-id="e39f5-392">This custom control will be used by your <xref:System.Drawing.Design.UITypeEditor> to interact with the Properties window.</span></span>

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a><span data-ttu-id="e39f5-393">Bir görünüm denetimi türü düzenleyici için özel kullanıcı Arabirimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e39f5-393">To create a view control for your custom UI type editor</span></span>

1. <span data-ttu-id="e39f5-394">Yeni bir <xref:System.Windows.Forms.UserControl> öğesinin `MarqueeControlLibrary` proje.</span><span class="sxs-lookup"><span data-stu-id="e39f5-394">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="e39f5-395">Yeni kaynak dosyası bir temel "LightShapeSelectionControl." adını verin</span><span class="sxs-lookup"><span data-stu-id="e39f5-395">Give the new source file a base name of "LightShapeSelectionControl."</span></span>

2. <span data-ttu-id="e39f5-396">İki <xref:System.Windows.Forms.Panel> denetimler **araç kutusu** üzerine `LightShapeSelectionControl`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-396">Drag two <xref:System.Windows.Forms.Panel> controls from the **Toolbox** onto the `LightShapeSelectionControl`.</span></span> <span data-ttu-id="e39f5-397">Bunları `squarePanel` ve `circlePanel`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-397">Name them `squarePanel` and `circlePanel`.</span></span> <span data-ttu-id="e39f5-398">Yan yana düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="e39f5-398">Arrange them side by side.</span></span> <span data-ttu-id="e39f5-399">Ayarlama <xref:System.Windows.Forms.Control.Size%2A> her iki özellik <xref:System.Windows.Forms.Panel> için denetimler (60, 60).</span><span class="sxs-lookup"><span data-stu-id="e39f5-399">Set the <xref:System.Windows.Forms.Control.Size%2A> property of both <xref:System.Windows.Forms.Panel> controls to (60, 60).</span></span> <span data-ttu-id="e39f5-400">Ayarlama <xref:System.Windows.Forms.Control.Location%2A> özelliği `squarePanel` denetimi (8, 10).</span><span class="sxs-lookup"><span data-stu-id="e39f5-400">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `squarePanel` control to (8, 10).</span></span> <span data-ttu-id="e39f5-401">Ayarlama <xref:System.Windows.Forms.Control.Location%2A> özelliği `circlePanel` denetimi (80, 10).</span><span class="sxs-lookup"><span data-stu-id="e39f5-401">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `circlePanel` control to (80, 10).</span></span> <span data-ttu-id="e39f5-402">Son olarak, ayarlama <xref:System.Windows.Forms.Control.Size%2A> özelliği `LightShapeSelectionControl` için (150, 80).</span><span class="sxs-lookup"><span data-stu-id="e39f5-402">Finally, set the <xref:System.Windows.Forms.Control.Size%2A> property of the `LightShapeSelectionControl` to (150, 80).</span></span>

3. <span data-ttu-id="e39f5-403">Açık `LightShapeSelectionControl` kaynak dosyada **Kod Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="e39f5-403">Open the `LightShapeSelectionControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="e39f5-404">İçeri aktarma dosyasının en üstüne <xref:System.Windows.Forms.Design?displayProperty=nameWithType> ad alanı:</span><span class="sxs-lookup"><span data-stu-id="e39f5-404">At the top of the file, import the <xref:System.Windows.Forms.Design?displayProperty=nameWithType> namespace:</span></span>

```vb
Imports System.Windows.Forms.Design
```

```csharp
using System.Windows.Forms.Design;
```

1. <span data-ttu-id="e39f5-405">Uygulama <xref:System.Windows.Forms.Control.Click> için olay işleyicileri `squarePanel` ve `circlePanel` kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="e39f5-405">Implement <xref:System.Windows.Forms.Control.Click> event handlers for the `squarePanel` and `circlePanel` controls.</span></span> <span data-ttu-id="e39f5-406">Bu yöntemleri çağırmak <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> özel sonuna <xref:System.Drawing.Design.UITypeEditor> oturumu düzenleme.</span><span class="sxs-lookup"><span data-stu-id="e39f5-406">These methods invoke <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> to end the custom <xref:System.Drawing.Design.UITypeEditor> editing session.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

2. <span data-ttu-id="e39f5-407">Bildirme bir <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> adlı örnek değişkeni `editorService`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-407">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

```vb
Private editorService As IWindowsFormsEditorService
```

```csharp
private IWindowsFormsEditorService editorService;
```

1. <span data-ttu-id="e39f5-408">Bildirme bir `MarqueeLightShape` adlı örnek değişkeni `lightShapeValue`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-408">Declare a `MarqueeLightShape` instance variable called `lightShapeValue`.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

2. <span data-ttu-id="e39f5-409">İçinde `LightShapeSelectionControl` oluşturucusu, ekleme <xref:System.Windows.Forms.Control.Click> olay işleyicilerine `squarePanel` ve `circlePanel` denetimleri <xref:System.Windows.Forms.Control.Click> olayları.</span><span class="sxs-lookup"><span data-stu-id="e39f5-409">In the `LightShapeSelectionControl` constructor, attach the <xref:System.Windows.Forms.Control.Click> event handlers to the `squarePanel` and `circlePanel` controls' <xref:System.Windows.Forms.Control.Click> events.</span></span> <span data-ttu-id="e39f5-410">Ayrıca atayan bir yapıcı yeniden yüklemesi tanımlayan `MarqueeLightShape` tasarım ortamı değerinden `lightShapeValue` alan.</span><span class="sxs-lookup"><span data-stu-id="e39f5-410">Also, define a constructor overload that assigns the `MarqueeLightShape` value from the design environment to the `lightShapeValue` field.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

3. <span data-ttu-id="e39f5-411">İçinde <xref:System.ComponentModel.Component.Dispose%2A> yöntemi ayırma <xref:System.Windows.Forms.Control.Click> olay işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="e39f5-411">In the <xref:System.ComponentModel.Component.Dispose%2A> method, detach the <xref:System.Windows.Forms.Control.Click> event handlers.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

4. <span data-ttu-id="e39f5-412">İçinde **Çözüm Gezgini**, tıklayın **tüm dosyaları göster** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-412">In **Solution Explorer**, click the **Show All Files** button.</span></span> <span data-ttu-id="e39f5-413">LightShapeSelectionControl.Designer.cs veya LightShapeSelectionControl.Designer.vb dosyasını açın ve öğenin varsayılan tanımını Kaldır <xref:System.ComponentModel.Component.Dispose%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-413">Open the LightShapeSelectionControl.Designer.cs or LightShapeSelectionControl.Designer.vb file, and remove the default definition of the <xref:System.ComponentModel.Component.Dispose%2A> method.</span></span>

5. <span data-ttu-id="e39f5-414">Uygulama `LightShape` özelliği.</span><span class="sxs-lookup"><span data-stu-id="e39f5-414">Implement the `LightShape` property.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

6. <span data-ttu-id="e39f5-415">Geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-415">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="e39f5-416">Bu uygulama bir dolu bir kare ve daire çizer.</span><span class="sxs-lookup"><span data-stu-id="e39f5-416">This implementation will draw a filled square and circle.</span></span> <span data-ttu-id="e39f5-417">Bir şekil veya diğer çevresine bir kenarlık çizerek, seçili değer ayrıca vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="e39f5-417">It will also highlight the selected value by drawing a border around one shape or the other.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="testing-your-custom-control-in-the-designer"></a><span data-ttu-id="e39f5-418">Özel Denetim Tasarımcısı'nda test etme</span><span class="sxs-lookup"><span data-stu-id="e39f5-418">Testing your Custom Control in the Designer</span></span>

<span data-ttu-id="e39f5-419">Bu noktada, yapı `MarqueeControlLibrary` proje.</span><span class="sxs-lookup"><span data-stu-id="e39f5-419">At this point, you can build the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="e39f5-420">Devralınan bir denetim oluşturarak uygulamanızı test `MarqueeControl` sınıf ve form üzerinde kullanarak.</span><span class="sxs-lookup"><span data-stu-id="e39f5-420">Test your implementation by creating a control that inherits from the `MarqueeControl` class and using it on a form.</span></span>

### <a name="to-create-a-custom-marqueecontrol-implementation"></a><span data-ttu-id="e39f5-421">Özel bir MarqueeControl uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e39f5-421">To create a custom MarqueeControl implementation</span></span>

1. <span data-ttu-id="e39f5-422">Açık `DemoMarqueeControl` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="e39f5-422">Open `DemoMarqueeControl` in the Windows Forms Designer.</span></span> <span data-ttu-id="e39f5-423">Bu örneği oluşturur `DemoMarqueeControl` yazın ve örneğinde görüntüler `MarqueeControlRootDesigner` türü.</span><span class="sxs-lookup"><span data-stu-id="e39f5-423">This creates an instance of the `DemoMarqueeControl` type and displays it in an instance of the `MarqueeControlRootDesigner` type.</span></span>

2. <span data-ttu-id="e39f5-424">İçinde **araç kutusu**açın **MarqueeControlLibrary bileşenleri** sekmesi. Göreceğiniz `MarqueeBorder` ve `MarqueeText` denetimleri seçilebilir.</span><span class="sxs-lookup"><span data-stu-id="e39f5-424">In the **Toolbox**, open the **MarqueeControlLibrary Components** tab. You will see the `MarqueeBorder` and `MarqueeText` controls available for selection.</span></span>

3. <span data-ttu-id="e39f5-425">Örneği sürükleyin `MarqueeBorder` denetimi `DemoMarqueeControl` tasarım yüzeyi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-425">Drag an instance of the `MarqueeBorder` control onto the `DemoMarqueeControl` design surface.</span></span> <span data-ttu-id="e39f5-426">Bu dock `MarqueeBorder` denetimin üst denetimine.</span><span class="sxs-lookup"><span data-stu-id="e39f5-426">Dock this `MarqueeBorder` control to the parent control.</span></span>

4. <span data-ttu-id="e39f5-427">Örneği sürükleyin `MarqueeText` denetimi `DemoMarqueeControl` tasarım yüzeyi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-427">Drag an instance of the `MarqueeText` control onto the `DemoMarqueeControl` design surface.</span></span>

5. <span data-ttu-id="e39f5-428">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e39f5-428">Build the solution.</span></span>

6. <span data-ttu-id="e39f5-429">Sağ `DemoMarqueeControl` kısayol menüsünü seçin ve **Test çalıştırması** animasyonu başlatmak için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e39f5-429">Right-click the `DemoMarqueeControl` and from the shortcut menu select the **Run Test** option to start the animation.</span></span> <span data-ttu-id="e39f5-430">Tıklayın **durdurma Test** animasyonu durdurmak için.</span><span class="sxs-lookup"><span data-stu-id="e39f5-430">Click **Stop Test** to stop the animation.</span></span>

7. <span data-ttu-id="e39f5-431">Açık **Form1** Tasarım görünümünde.</span><span class="sxs-lookup"><span data-stu-id="e39f5-431">Open **Form1** in Design view.</span></span>

8. <span data-ttu-id="e39f5-432">İki <xref:System.Windows.Forms.Button> form üzerinde denetimleri.</span><span class="sxs-lookup"><span data-stu-id="e39f5-432">Place two <xref:System.Windows.Forms.Button> controls on the form.</span></span> <span data-ttu-id="e39f5-433">Bunları `startButton` ve `stopButton`, değiştirip <xref:System.Windows.Forms.Control.Text%2A> değerlerini özellik **Başlat** ve **Durdur**sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="e39f5-433">Name them `startButton` and `stopButton`, and change the <xref:System.Windows.Forms.Control.Text%2A> property values to **Start** and **Stop**, respectively.</span></span>

9. <span data-ttu-id="e39f5-434">Uygulama <xref:System.Windows.Forms.Control.Click> her ikisi için olay işleyicileri <xref:System.Windows.Forms.Button> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="e39f5-434">Implement <xref:System.Windows.Forms.Control.Click> event handlers for both <xref:System.Windows.Forms.Button> controls.</span></span>

10. <span data-ttu-id="e39f5-435">İçinde **araç kutusu**açın **MarqueeControlTest bileşenleri** sekmesi. Göreceğiniz `DemoMarqueeControl` seçim için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e39f5-435">In the **Toolbox**, open the **MarqueeControlTest Components** tab. You will see the `DemoMarqueeControl` available for selection.</span></span>

11. <span data-ttu-id="e39f5-436">Örneği sürükleyin `DemoMarqueeControl` üzerine **Form1** tasarım yüzeyi.</span><span class="sxs-lookup"><span data-stu-id="e39f5-436">Drag an instance of `DemoMarqueeControl` onto the **Form1** design surface.</span></span>

12. <span data-ttu-id="e39f5-437">İçinde <xref:System.Windows.Forms.Control.Click> olay işleyicilerini çağırma `Start` ve `Stop` yöntemlerde `DemoMarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-437">In the <xref:System.Windows.Forms.Control.Click> event handlers, invoke the `Start` and `Stop` methods on the `DemoMarqueeControl`.</span></span>

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

1. <span data-ttu-id="e39f5-438">Ayarlama `MarqueeControlTest` projesini başlangıç projesi olarak ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e39f5-438">Set the `MarqueeControlTest` project as the startup project and run it.</span></span> <span data-ttu-id="e39f5-439">Görüntüleme formu görürsünüz, `DemoMarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-439">You will see the form displaying your `DemoMarqueeControl`.</span></span> <span data-ttu-id="e39f5-440">Tıklayın **Başlat** animasyonu başlatmak için düğme.</span><span class="sxs-lookup"><span data-stu-id="e39f5-440">Click the **Start** button to start the animation.</span></span> <span data-ttu-id="e39f5-441">Yanıp metin ve kenarlık taşıma ışıkları görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e39f5-441">You should see the text flashing and the lights moving around the border.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e39f5-442">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="e39f5-442">Next Steps</span></span>

<span data-ttu-id="e39f5-443">`MarqueeControlLibrary` Özel denetimler ve ilişkili tasarımcıları basit bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e39f5-443">The `MarqueeControlLibrary` demonstrates a simple implementation of custom controls and associated designers.</span></span> <span data-ttu-id="e39f5-444">Bu örnek daha karmaşık çeşitli şekillerde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e39f5-444">You can make this sample more sophisticated in several ways:</span></span>

- <span data-ttu-id="e39f5-445">Özellik değerlerini değiştirmek `DemoMarqueeControl` Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="e39f5-445">Change the property values for the `DemoMarqueeControl` in the designer.</span></span> <span data-ttu-id="e39f5-446">Daha fazla Ekle `MarqueBorder` denetler ve bunları bir iç içe geçmiş etkisi oluşturmak için üst örneklerinden yerleştir.</span><span class="sxs-lookup"><span data-stu-id="e39f5-446">Add more `MarqueBorder` controls and dock them within their parent instances to create a nested effect.</span></span> <span data-ttu-id="e39f5-447">Deneme için farklı ayarlarla `UpdatePeriod` ve ışık güvenlikle ilgili özellikler.</span><span class="sxs-lookup"><span data-stu-id="e39f5-447">Experiment with different settings for the `UpdatePeriod` and the light-related properties.</span></span>

- <span data-ttu-id="e39f5-448">Kendi uygulamalarını Yazar `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-448">Author your own implementations of `IMarqueeWidget`.</span></span> <span data-ttu-id="e39f5-449">Örneğin, bir yanıp sönen "neon işareti" veya bir animasyonlu işareti ile birden çok görüntü oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e39f5-449">You could, for example, create a flashing "neon sign" or an animated sign with multiple images.</span></span>

- <span data-ttu-id="e39f5-450">Tasarım zamanı deneyimi özelleştirin.</span><span class="sxs-lookup"><span data-stu-id="e39f5-450">Further customize the design-time experience.</span></span> <span data-ttu-id="e39f5-451">Daha fazla özellik gölgeleme deneyebilirsiniz <xref:System.Windows.Forms.Control.Enabled%2A> ve <xref:System.Windows.Forms.Control.Visible%2A>, ve yeni özellikleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e39f5-451">You could try shadowing more properties than <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A>, and you could add new properties.</span></span> <span data-ttu-id="e39f5-452">Alt denetimler yerleştirme gibi genel görevleri basitleştirmek için yeni Tasarımcı fiilleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e39f5-452">Add new designer verbs to simplify common tasks like docking child controls.</span></span>

- <span data-ttu-id="e39f5-453">Lisans `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="e39f5-453">License the `MarqueeControl`.</span></span> <span data-ttu-id="e39f5-454">Daha fazla bilgi için [nasıl yapılır: Lisans bileşenleri ve denetimleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="e39f5-454">For more information, see [How to: License Components and Controls](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120)).</span></span>

- <span data-ttu-id="e39f5-455">Denetimlerinizi nasıl sıralanır ve kod için bunları nasıl oluşturulacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="e39f5-455">Control how your controls are serialized and how code is generated for them.</span></span> <span data-ttu-id="e39f5-456">Daha fazla bilgi için [dinamik kaynak kodu oluşturma ve derleme](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="e39f5-456">For more information, see [Dynamic Source Code Generation and Compilation](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e39f5-457">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e39f5-457">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
- <span data-ttu-id="e39f5-458">[Nasıl yapılır: Tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="e39f5-458">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span></span>
- <span data-ttu-id="e39f5-459">[Tasarım zamanı desteği sunma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="e39f5-459">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>
- <span data-ttu-id="e39f5-460">[Özel tasarımcılar](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h51z5c0x(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="e39f5-460">[Custom Designers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h51z5c0x(v=vs.120))</span></span>
