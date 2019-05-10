---
title: 'İzlenecek yol: Profesyonel Stilde ToolStrip Denetimi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- toolbars [Windows Forms], walkthroughs
- ToolStrip control [Windows Forms], creating professionally styled controls
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
ms.openlocfilehash: 226e805d0240236899ee0cc290f1060a3b0aa391
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211764"
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="a0d44-102">İzlenecek yol: Profesyonel Stilde ToolStrip Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a0d44-102">Walkthrough: Creating a Professionally Styled ToolStrip Control</span></span>

<span data-ttu-id="a0d44-103">Uygulamanızın verebilirsiniz <xref:System.Windows.Forms.ToolStrip> kendi sınıfından türetilen yazarak bir profesyonel görünümünü ve davranışını denetleyen <xref:System.Windows.Forms.ToolStripProfessionalRenderer> türü.</span><span class="sxs-lookup"><span data-stu-id="a0d44-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>

<span data-ttu-id="a0d44-104">Bu izlenecek yolda nasıl kullanılacağını gösterir <xref:System.Windows.Forms.ToolStrip> benzeyen bileşik denetim oluşturmak için denetimleri **Gezinti bölmesinde** Microsoft Outlook® tarafından sağlanan.</span><span class="sxs-lookup"><span data-stu-id="a0d44-104">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that resembles the **Navigation Pane** provided by Microsoft® Outlook®.</span></span> <span data-ttu-id="a0d44-105">Aşağıdaki görevler bu kılavuzda gösterilen:</span><span class="sxs-lookup"><span data-stu-id="a0d44-105">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="a0d44-106">Bir Windows Denetim Kitaplığı projesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="a0d44-106">Creating a Windows Control Library project.</span></span>

- <span data-ttu-id="a0d44-107">StackView denetimi tasarlama.</span><span class="sxs-lookup"><span data-stu-id="a0d44-107">Designing the StackView Control.</span></span>

- <span data-ttu-id="a0d44-108">Özel oluşturucu oluşturma.</span><span class="sxs-lookup"><span data-stu-id="a0d44-108">Implementing a Custom Renderer.</span></span>

<span data-ttu-id="a0d44-109">İşlemi tamamladığınızda, profesyonel bir Microsoft Office® XP denetiminin görünümünü ile bir yeniden kullanılabilir bir özel istemci denetime sahip olur.</span><span class="sxs-lookup"><span data-stu-id="a0d44-109">When you are finished, you will have a reusable custom client control with the professional appearance of a Microsoft Office® XP control.</span></span>

<span data-ttu-id="a0d44-110">Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: Profesyonel stilde ToolStrip denetimi oluşturma](how-to-create-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="a0d44-110">To copy the code in this topic as a single listing, see [How to: Create a Professionally Styled ToolStrip Control](how-to-create-a-professionally-styled-toolstrip-control.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a0d44-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="a0d44-111">Prerequisites</span></span>

<span data-ttu-id="a0d44-112">Bu izlenecek yolu tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0d44-112">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-control-library-project"></a><span data-ttu-id="a0d44-113">Denetim Kitaplığı projesi oluşturun</span><span class="sxs-lookup"><span data-stu-id="a0d44-113">Create the control library project</span></span>

1. <span data-ttu-id="a0d44-114">Visual Studio'da adlı yeni bir Windows Denetim Kitaplığı projesi oluşturma `StackViewLibrary`.</span><span class="sxs-lookup"><span data-stu-id="a0d44-114">In Visual Studio, create a new Windows Control Library project named `StackViewLibrary`.</span></span>

2. <span data-ttu-id="a0d44-115">İçinde **Çözüm Gezgini**, istediğiniz dilde bağlı olarak "UserControl1.cs" veya "UserControl1.vb" adlı kaynak dosyası silerek projenin varsayılan denetimini silin.</span><span class="sxs-lookup"><span data-stu-id="a0d44-115">In **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span>

     <span data-ttu-id="a0d44-116">Daha fazla bilgi için [nasıl yapılır: , Silme, kaldırmak ve öğeleri hariç](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a0d44-116">For more information, see [How to: Remove, Delete, and Exclude Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span></span>

3. <span data-ttu-id="a0d44-117">Yeni bir <xref:System.Windows.Forms.UserControl> öğesinin **StackViewLibrary** proje.</span><span class="sxs-lookup"><span data-stu-id="a0d44-117">Add a new <xref:System.Windows.Forms.UserControl> item to the **StackViewLibrary** project.</span></span> <span data-ttu-id="a0d44-118">Yeni kaynak dosyanın temel adı verin `StackView`.</span><span class="sxs-lookup"><span data-stu-id="a0d44-118">Give the new source file a base name of `StackView`.</span></span>

## <a name="design-the-stackview-control"></a><span data-ttu-id="a0d44-119">Tasarım StackView denetimi</span><span class="sxs-lookup"><span data-stu-id="a0d44-119">Design the StackView control</span></span>

<span data-ttu-id="a0d44-120">`StackView` Denetimdir: bir alt öğesi ile bileşik denetim <xref:System.Windows.Forms.ToolStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="a0d44-120">The `StackView` control is a composite control with one child <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="a0d44-121">Bileşik denetimler hakkında daha fazla bilgi için bkz: [özel denetim çeşitleri](varieties-of-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="a0d44-121">For more information about composite controls, see [Varieties of Custom Controls](varieties-of-custom-controls.md).</span></span>

1. <span data-ttu-id="a0d44-122">Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.ToolStrip> denetimi tasarım yüzeyine bırakın.</span><span class="sxs-lookup"><span data-stu-id="a0d44-122">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStrip> control to the design surface.</span></span>

2. <span data-ttu-id="a0d44-123">İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.ToolStrip> denetimin özellikleri aşağıdaki tabloya göre.</span><span class="sxs-lookup"><span data-stu-id="a0d44-123">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStrip> control's properties according to the following table.</span></span>

    |<span data-ttu-id="a0d44-124">Özellik</span><span class="sxs-lookup"><span data-stu-id="a0d44-124">Property</span></span>|<span data-ttu-id="a0d44-125">Değer</span><span class="sxs-lookup"><span data-stu-id="a0d44-125">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="a0d44-126">Ad</span><span class="sxs-lookup"><span data-stu-id="a0d44-126">Name</span></span>|`stackStrip`|
    |<span data-ttu-id="a0d44-127">CanOverflow</span><span class="sxs-lookup"><span data-stu-id="a0d44-127">CanOverflow</span></span>|`false`|
    |<span data-ttu-id="a0d44-128">Dock</span><span class="sxs-lookup"><span data-stu-id="a0d44-128">Dock</span></span>|<xref:System.Windows.Forms.DockStyle.Bottom>|
    |<span data-ttu-id="a0d44-129">Yazı tipi</span><span class="sxs-lookup"><span data-stu-id="a0d44-129">Font</span></span>|`Tahoma, 10pt, style=Bold`|
    |<span data-ttu-id="a0d44-130">GripStyle</span><span class="sxs-lookup"><span data-stu-id="a0d44-130">GripStyle</span></span>|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|
    |<span data-ttu-id="a0d44-131">LayoutStyle</span><span class="sxs-lookup"><span data-stu-id="a0d44-131">LayoutStyle</span></span>|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|
    |<span data-ttu-id="a0d44-132">Doldurma</span><span class="sxs-lookup"><span data-stu-id="a0d44-132">Padding</span></span>|`0, 7, 0, 0`|
    |<span data-ttu-id="a0d44-133">RenderMode</span><span class="sxs-lookup"><span data-stu-id="a0d44-133">RenderMode</span></span>|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|

3. <span data-ttu-id="a0d44-134">Windows Form Tasarımcısı'nda tıklatın <xref:System.Windows.Forms.ToolStrip> denetimin **Ekle** düğmesine tıklayın ve Ekle bir <xref:System.Windows.Forms.ToolStripButton> için `stackStrip` denetimi.</span><span class="sxs-lookup"><span data-stu-id="a0d44-134">In the Windows Forms Designer, click the <xref:System.Windows.Forms.ToolStrip> control's **Add** button and add a <xref:System.Windows.Forms.ToolStripButton> to the `stackStrip` control.</span></span>

4. <span data-ttu-id="a0d44-135">İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.ToolStripButton> denetimin özellikleri aşağıdaki tabloya göre.</span><span class="sxs-lookup"><span data-stu-id="a0d44-135">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStripButton> control's properties according to the following table.</span></span>

    |<span data-ttu-id="a0d44-136">Özellik</span><span class="sxs-lookup"><span data-stu-id="a0d44-136">Property</span></span>|<span data-ttu-id="a0d44-137">Değer</span><span class="sxs-lookup"><span data-stu-id="a0d44-137">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="a0d44-138">Ad</span><span class="sxs-lookup"><span data-stu-id="a0d44-138">Name</span></span>|`mailStackButton`|
    |<span data-ttu-id="a0d44-139">CheckOnClick</span><span class="sxs-lookup"><span data-stu-id="a0d44-139">CheckOnClick</span></span>|<span data-ttu-id="a0d44-140">true</span><span class="sxs-lookup"><span data-stu-id="a0d44-140">true</span></span>|
    |<span data-ttu-id="a0d44-141">CheckState</span><span class="sxs-lookup"><span data-stu-id="a0d44-141">CheckState</span></span>|<xref:System.Windows.Forms.CheckState.Checked>|
    |<span data-ttu-id="a0d44-142">DisplayStyle</span><span class="sxs-lookup"><span data-stu-id="a0d44-142">DisplayStyle</span></span>|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|
    |<span data-ttu-id="a0d44-143">ImageAlign</span><span class="sxs-lookup"><span data-stu-id="a0d44-143">ImageAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|
    |<span data-ttu-id="a0d44-144">ImageScaling</span><span class="sxs-lookup"><span data-stu-id="a0d44-144">ImageScaling</span></span>|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|
    |<span data-ttu-id="a0d44-145">ImageTransparentColor</span><span class="sxs-lookup"><span data-stu-id="a0d44-145">ImageTransparentColor</span></span>|`238, 238, 238`|
    |<span data-ttu-id="a0d44-146">Kenar boşluğu</span><span class="sxs-lookup"><span data-stu-id="a0d44-146">Margin</span></span>|`0, 0, 0, 0`|
    |<span data-ttu-id="a0d44-147">Doldurma</span><span class="sxs-lookup"><span data-stu-id="a0d44-147">Padding</span></span>|`3, 3, 3, 3`|
    |<span data-ttu-id="a0d44-148">Metin</span><span class="sxs-lookup"><span data-stu-id="a0d44-148">Text</span></span>|<span data-ttu-id="a0d44-149">**posta**</span><span class="sxs-lookup"><span data-stu-id="a0d44-149">**Mail**</span></span>|
    |<span data-ttu-id="a0d44-150">TextAlign</span><span class="sxs-lookup"><span data-stu-id="a0d44-150">TextAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|

5. <span data-ttu-id="a0d44-151">Daha fazla üç için yineleme adım 7 <xref:System.Windows.Forms.ToolStripButton> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="a0d44-151">Repeat step 7 for three more <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>

     <span data-ttu-id="a0d44-152">Denetimlere `calendarStackButton`, `contactsStackButton`, ve `tasksStackButton`.</span><span class="sxs-lookup"><span data-stu-id="a0d44-152">Name the controls `calendarStackButton`, `contactsStackButton`, and `tasksStackButton`.</span></span> <span data-ttu-id="a0d44-153">Değerini <xref:System.Windows.Forms.Control.Text%2A> özelliğini **Takvim**, **kişiler**, ve **görevleri**sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="a0d44-153">Set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to **Calendar**, **Contacts**, and **Tasks**, respectively.</span></span>

## <a name="handle-events"></a><span data-ttu-id="a0d44-154">Olayları işleme</span><span class="sxs-lookup"><span data-stu-id="a0d44-154">Handle events</span></span>

<span data-ttu-id="a0d44-155">İki olay yapmak önemli `StackView` denetimi doğru şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="a0d44-155">Two events are important to make the `StackView` control behave correctly.</span></span> <span data-ttu-id="a0d44-156">Tanıtıcı <xref:System.Windows.Forms.UserControl.Load> denetim doğru konuma olay.</span><span class="sxs-lookup"><span data-stu-id="a0d44-156">Handle the <xref:System.Windows.Forms.UserControl.Load> event to position the control correctly.</span></span> <span data-ttu-id="a0d44-157">Tanıtıcı <xref:System.Windows.Forms.ToolStripItem.Click> her olay <xref:System.Windows.Forms.ToolStripButton> vermek `StackView` denetim durumu davranışını benzer <xref:System.Windows.Forms.RadioButton> denetimi.</span><span class="sxs-lookup"><span data-stu-id="a0d44-157">Handle the <xref:System.Windows.Forms.ToolStripItem.Click> event for each <xref:System.Windows.Forms.ToolStripButton> to give the `StackView` control state behavior similar to the <xref:System.Windows.Forms.RadioButton> control.</span></span>

1. <span data-ttu-id="a0d44-158">Windows Form Tasarımcısı'nda seçin `StackView` denetimi.</span><span class="sxs-lookup"><span data-stu-id="a0d44-158">In the Windows Forms Designer, select the `StackView` control.</span></span>

2. <span data-ttu-id="a0d44-159">İçinde **özellikleri** penceresinde tıklayın **olayları**.</span><span class="sxs-lookup"><span data-stu-id="a0d44-159">In the **Properties** window, click **Events**.</span></span>

3. <span data-ttu-id="a0d44-160">Oluşturulacak yükleme olayı çift `StackView_Load` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="a0d44-160">Double-click the Load event to generate the `StackView_Load` event handler.</span></span>

4. <span data-ttu-id="a0d44-161">İçinde `StackView_Load` olay işleyicisine aşağıdaki kodu kopyalayıp yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="a0d44-161">In the `StackView_Load` event handler, copy and paste the following code.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]

5. <span data-ttu-id="a0d44-162">Windows Form Tasarımcısı'nda seçin `mailStackButton` denetimi.</span><span class="sxs-lookup"><span data-stu-id="a0d44-162">In the Windows Forms Designer, select the `mailStackButton` control.</span></span>

6. <span data-ttu-id="a0d44-163">İçinde **özellikleri** penceresinde tıklayın **olayları**.</span><span class="sxs-lookup"><span data-stu-id="a0d44-163">In the **Properties** window, click **Events**.</span></span>

7. <span data-ttu-id="a0d44-164">Tıklama olayı çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a0d44-164">Double-click the Click event.</span></span>

     <span data-ttu-id="a0d44-165">Windows Form Tasarımcısı oluşturur `mailStackButton_Click` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="a0d44-165">The Windows Forms Designer generates the `mailStackButton_Click` event handler.</span></span>

8. <span data-ttu-id="a0d44-166">Yeniden adlandırma `mailStackButton_Click` olay işleyicisine `stackButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="a0d44-166">Rename the `mailStackButton_Click` event handler to `stackButton_Click`.</span></span>

     <span data-ttu-id="a0d44-167">Daha fazla bilgi için [bir kod sembol yeniden düzenlemeyi yeniden adlandırma](/visualstudio/ide/reference/rename).</span><span class="sxs-lookup"><span data-stu-id="a0d44-167">For more information, see [Rename a code symbol refactoring](/visualstudio/ide/reference/rename).</span></span>

9. <span data-ttu-id="a0d44-168">Aşağıdaki kodu ekleyin `stackButton_Click` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="a0d44-168">Insert the following code into the `stackButton_Click` event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]

10. <span data-ttu-id="a0d44-169">Windows Form Tasarımcısı'nda seçin `calendarStackButton` denetimi.</span><span class="sxs-lookup"><span data-stu-id="a0d44-169">In the Windows Forms Designer, select the `calendarStackButton` control.</span></span>

11. <span data-ttu-id="a0d44-170">İçinde **özellikleri** penceresinde ayarlanmış Click olayı `stackButton_Click` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="a0d44-170">In the **Properties** window, set the Click event to the `stackButton_Click` event handler.</span></span>

12. <span data-ttu-id="a0d44-171">10 ve 11. adımları yineleyin `contactsStackButton` ve `tasksStackButton` kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="a0d44-171">Repeat steps 10 and 11 for the `contactsStackButton` and `tasksStackButton` controls.</span></span>

## <a name="define-icons"></a><span data-ttu-id="a0d44-172">Simgeleri tanımlayın</span><span class="sxs-lookup"><span data-stu-id="a0d44-172">Define icons</span></span>

<span data-ttu-id="a0d44-173">Her `StackView` düğmeye sahip bir ilişkili simge.</span><span class="sxs-lookup"><span data-stu-id="a0d44-173">Each `StackView` button has an associated icon.</span></span> <span data-ttu-id="a0d44-174">Kolaylık olması için simgeleri Base64 ile kodlanmış bir dize olarak, önce seri durumdan temsil edilen bir <xref:System.Drawing.Bitmap> ondan oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a0d44-174">For convenience, each icon is represented as a Base64-encoded string, which is deserialized before a <xref:System.Drawing.Bitmap> is created from it.</span></span> <span data-ttu-id="a0d44-175">Bir üretim ortamında bir kaynak olarak bit eşlem verileri depolamak ve simgelerini Windows Form Tasarımcısı'nda görünür.</span><span class="sxs-lookup"><span data-stu-id="a0d44-175">In a production environment, you store bitmap data as a resource, and your icons appear in the Windows Forms Designer.</span></span> <span data-ttu-id="a0d44-176">Daha fazla bilgi için [nasıl yapılır: Windows formlarına arka plan görüntüleri ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dff9f95f(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a0d44-176">For more information, see [How to: Add Background Images to Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dff9f95f(v=vs.100)).</span></span>

1. <span data-ttu-id="a0d44-177">Kod Düzenleyicisi'nde aşağıdaki kodu ekleyin `StackView` sınıf tanımını.</span><span class="sxs-lookup"><span data-stu-id="a0d44-177">In the Code Editor, insert the following code into the `StackView` class definition.</span></span> <span data-ttu-id="a0d44-178">Bu kod için bit eşlemler başlatır <xref:System.Windows.Forms.ToolStripButton> simgeler.</span><span class="sxs-lookup"><span data-stu-id="a0d44-178">This code initializes the bitmaps for the <xref:System.Windows.Forms.ToolStripButton> icons.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]

2. <span data-ttu-id="a0d44-179">Bir çağrı ekleyin `InitializeImages` yönteminde `StackView` sınıf oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="a0d44-179">Add a call to the `InitializeImages` method in the `StackView` class constructor.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]

## <a name="implement-a-custom-renderer"></a><span data-ttu-id="a0d44-180">Uygulama özel Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="a0d44-180">Implement a custom renderer</span></span>

<span data-ttu-id="a0d44-181">Özelleştirebileceğiniz öğelerin çoğunu `StackView` my türetildiği bir sınıf uygulama Denetim <xref:System.Windows.Forms.ToolStripRenderer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a0d44-181">You can customize most elements of the `StackView` control my implementing a class that derives from the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="a0d44-182">Bu yordamda, uygulamanız bir <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tutamacı özelleştirir ve gradyan arka planlar için çizer sınıfı <xref:System.Windows.Forms.ToolStripButton> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="a0d44-182">In this procedure, you will implement a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class that customizes the grip and draws gradient backgrounds for the <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>

1. <span data-ttu-id="a0d44-183">Aşağıdaki kodu ekleyin `StackView` denetim tanımı.</span><span class="sxs-lookup"><span data-stu-id="a0d44-183">Insert the following code into the `StackView` control definition.</span></span>

     <span data-ttu-id="a0d44-184">Bu tanımı, `StackRenderer` sınıfı, hangi geçersiz kılmaları <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, ve <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> özel görünüm oluşturmak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="a0d44-184">This is the definition for the `StackRenderer` class, which overrides the <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, and <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> methods to produce a custom appearance.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]

2. <span data-ttu-id="a0d44-185">İçinde `StackView` denetimin Oluşturucu, yeni bir örneğini oluşturmak `StackRenderer` sınıfı ve bu örneğe atama `stackStrip` denetimin <xref:System.Windows.Forms.ToolStrip.Renderer%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a0d44-185">In the `StackView` control's constructor, create a new instance of the `StackRenderer` class and assign this instance to the `stackStrip` control's <xref:System.Windows.Forms.ToolStrip.Renderer%2A> property.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]

## <a name="test-the-stackview-control"></a><span data-ttu-id="a0d44-186">Test StackView denetimi</span><span class="sxs-lookup"><span data-stu-id="a0d44-186">Test the StackView control</span></span>

<span data-ttu-id="a0d44-187">`StackView` Denetim türetilir <xref:System.Windows.Forms.UserControl> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a0d44-187">The `StackView` control derives from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="a0d44-188">Bu nedenle, Denetim ile test edebilirsiniz **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="a0d44-188">Therefore, you can test the control with the **UserControl Test Container**.</span></span> <span data-ttu-id="a0d44-189">Daha fazla bilgi için [nasıl yapılır: Bir UserControl denetiminin çalışma zamanı davranışını sınama](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="a0d44-189">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

1. <span data-ttu-id="a0d44-190">Tuşuna **F5** projeyi oluşturmak ve başlatmak için **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="a0d44-190">Press **F5** to build the project and start the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="a0d44-191">Düğmelerinin üzerinde işaretçiyi `StackView` denetlemek ve ardından seçili durumuna görünümünü görmek için bir düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a0d44-191">Move the pointer over the buttons of the `StackView` control, and then click a button to see the appearance of its selected state.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a0d44-192">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="a0d44-192">Next steps</span></span>

<span data-ttu-id="a0d44-193">Bu kılavuzda, profesyonel bir Office XP denetiminin görünümünü ile yeniden kullanılabilir bir özel istemci denetimi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="a0d44-193">In this walkthrough, you have created a reusable custom client control with the professional appearance of an Office XP control.</span></span> <span data-ttu-id="a0d44-194">Kullanabileceğiniz <xref:System.Windows.Forms.ToolStrip> birçok başka amaçlarla denetimlerin ailesi:</span><span class="sxs-lookup"><span data-stu-id="a0d44-194">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="a0d44-195">Sahip, denetimler için kısayol menüleri oluşturma <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="a0d44-195">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="a0d44-196">Daha fazla bilgi için [ContextMenu bileşenine genel bakış](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a0d44-196">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="a0d44-197">Bir formu otomatik olarak doldurulan bir standart menü ile oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a0d44-197">Create a form with an automatically populated standard menu.</span></span> <span data-ttu-id="a0d44-198">Daha fazla bilgi için [izlenecek yol: Bir forma standart menü öğeleri sağlama](walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="a0d44-198">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>

- <span data-ttu-id="a0d44-199">Yerleştirme ile birden çok belge arabirimi (MDI) form oluşturma <xref:System.Windows.Forms.ToolStrip> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="a0d44-199">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="a0d44-200">Daha fazla bilgi için [nasıl yapılır: Menü birleştirme ve ToolStrip denetimleri içeren MDI formu oluşturma](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="a0d44-200">For more information, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a0d44-201">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0d44-201">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="a0d44-202">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="a0d44-202">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
- [<span data-ttu-id="a0d44-203">Nasıl yapılır: Bir forma standart menü öğeleri sağlama</span><span class="sxs-lookup"><span data-stu-id="a0d44-203">How to: Provide Standard Menu Items to a Form</span></span>](how-to-provide-standard-menu-items-to-a-form.md)
