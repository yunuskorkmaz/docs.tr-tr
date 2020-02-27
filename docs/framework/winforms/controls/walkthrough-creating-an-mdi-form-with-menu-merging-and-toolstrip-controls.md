---
title: 'İzlenecek yol: Menü Birleştirme ve ToolStrip Denetimleri ile bir MDI Formu Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
ms.openlocfilehash: e0343b98cb71521b35418e70550a93e0bfe20fa8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628793"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="b5344-102">İzlenecek yol: Menü Birleştirme ve ToolStrip Denetimleri ile bir MDI Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b5344-102">Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls</span></span>

<span data-ttu-id="b5344-103"><xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı birden çok belge arabirimi (MDI) uygulamasını destekler ve <xref:System.Windows.Forms.MenuStrip> denetimi menüyü birleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="b5344-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="b5344-104">MDI Forms denetimleri de <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="b5344-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="b5344-105">Bu izlenecek yol, <xref:System.Windows.Forms.ToolStripPanel> denetimlerinin MDI formu ile nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5344-105">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="b5344-106">Form Ayrıca alt menülerle menü birleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="b5344-106">The form also supports menu merging with child menus.</span></span> <span data-ttu-id="b5344-107">Aşağıdaki görevler Bu izlenecek yolda gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="b5344-107">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="b5344-108">Windows Forms projesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="b5344-108">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="b5344-109">Formunuz için ana menü oluşturma.</span><span class="sxs-lookup"><span data-stu-id="b5344-109">Creating the main menu for your form.</span></span> <span data-ttu-id="b5344-110">Menünün gerçek adı farklılık gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="b5344-110">The actual name of the menu will vary.</span></span>

- <span data-ttu-id="b5344-111">**Araç kutusuna**<xref:System.Windows.Forms.ToolStripPanel> denetimi ekleme.</span><span class="sxs-lookup"><span data-stu-id="b5344-111">Adding the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox**.</span></span>

- <span data-ttu-id="b5344-112">Alt form oluşturma.</span><span class="sxs-lookup"><span data-stu-id="b5344-112">Creating a child form.</span></span>

- <span data-ttu-id="b5344-113"><xref:System.Windows.Forms.ToolStripPanel> denetimleri z düzeninde düzenleme.</span><span class="sxs-lookup"><span data-stu-id="b5344-113">Arranging <xref:System.Windows.Forms.ToolStripPanel> controls by z-order.</span></span>

<span data-ttu-id="b5344-114">İşiniz bittiğinde, menü birleştirme ve taşınabilir <xref:System.Windows.Forms.ToolStrip> denetimlerini destekleyen bir MDI formunuza sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="b5344-114">When you are finished, you will have an MDI form that supports menu merging and movable <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="b5344-115">Bu konudaki kodu tek bir liste olarak kopyalamak için bkz. [nasıl yapılır: menü birleştirme ve ToolStrip denetimleri Ile MDI formu oluşturma](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="b5344-115">To copy the code in this topic as a single listing, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b5344-116">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="b5344-116">Prerequisites</span></span>

<span data-ttu-id="b5344-117">Bu izlenecek yolu tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="b5344-117">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="b5344-118">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="b5344-118">Create the project</span></span>

1. <span data-ttu-id="b5344-119">Visual Studio 'da, **MDIForm** adlı bir Windows uygulama projesi**oluşturun (** **Visual C#**  veya **Visual Basic** > **Klasik Masaüstü** > Windows Forms **uygulaması** **) > \*\* \*\* >  > .**</span><span class="sxs-lookup"><span data-stu-id="b5344-119">In Visual Studio, create a Windows Application project called **MdiForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="b5344-120">Windows Form Tasarımcısı, formunu seçin.</span><span class="sxs-lookup"><span data-stu-id="b5344-120">In the Windows Forms Designer, select the form.</span></span>

3. <span data-ttu-id="b5344-121">Özellikler penceresi, <xref:System.Windows.Forms.Form.IsMdiContainer%2A> değerini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b5344-121">In the Properties window, set the value of the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> to `true`.</span></span>

## <a name="create-the-main-menu"></a><span data-ttu-id="b5344-122">Ana menüyü oluşturma</span><span class="sxs-lookup"><span data-stu-id="b5344-122">Create the main menu</span></span>

<span data-ttu-id="b5344-123">Üst MDI formu ana menüyü içerir.</span><span class="sxs-lookup"><span data-stu-id="b5344-123">The parent MDI form contains the main menu.</span></span> <span data-ttu-id="b5344-124">Ana menüde **pencere**adlı bir menü öğesi vardır.</span><span class="sxs-lookup"><span data-stu-id="b5344-124">The main menu has one menu item named **Window**.</span></span> <span data-ttu-id="b5344-125">**Pencere** menü öğesiyle alt formlar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5344-125">With the **Window** menu item, you can create child forms.</span></span> <span data-ttu-id="b5344-126">Alt formlardan menü öğeleri ana menüde birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b5344-126">Menu items from child forms are merged into the main menu.</span></span>

1. <span data-ttu-id="b5344-127">**Araç kutusundan**bir <xref:System.Windows.Forms.MenuStrip> denetimini form üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="b5344-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the form.</span></span>

2. <span data-ttu-id="b5344-128"><xref:System.Windows.Forms.MenuStrip> denetimine <xref:System.Windows.Forms.ToolStripMenuItem> ekleyin ve **pencereye**adlandırın.</span><span class="sxs-lookup"><span data-stu-id="b5344-128">Add a <xref:System.Windows.Forms.ToolStripMenuItem> to the <xref:System.Windows.Forms.MenuStrip> control and name it **Window**.</span></span>

3. <span data-ttu-id="b5344-129"><xref:System.Windows.Forms.MenuStrip> denetimini seçin.</span><span class="sxs-lookup"><span data-stu-id="b5344-129">Select the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

4. <span data-ttu-id="b5344-130">Özellikler penceresi, <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliğinin değerini `ToolStripMenuItem1`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b5344-130">In the Properties window, set the value of the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to `ToolStripMenuItem1`.</span></span>

5. <span data-ttu-id="b5344-131">**Pencere** menü öğesine bir alt öğe ekleyin ve ardından **Yeni**alt öğesi adlandırın.</span><span class="sxs-lookup"><span data-stu-id="b5344-131">Add a subitem to the **Window** menu item, and then name the subitem **New**.</span></span>

6. <span data-ttu-id="b5344-132">Özellikler penceresi, **Olaylar**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b5344-132">In the Properties window, click **Events**.</span></span>

7. <span data-ttu-id="b5344-133"><xref:System.Windows.Forms.ToolStripItem.Click> olayına çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b5344-133">Double-click the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

     <span data-ttu-id="b5344-134">Windows Form Tasarımcısı, <xref:System.Windows.Forms.ToolStripItem.Click> olayı için bir olay işleyicisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b5344-134">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

8. <span data-ttu-id="b5344-135">Olay işleyicisine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b5344-135">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]

## <a name="add-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="b5344-136">Araç kutusuna ToolStripPanel denetimini ekleme</span><span class="sxs-lookup"><span data-stu-id="b5344-136">Add the ToolStripPanel control to the Toolbox</span></span>

<span data-ttu-id="b5344-137">MDI formuyla <xref:System.Windows.Forms.MenuStrip> denetimleri kullandığınızda <xref:System.Windows.Forms.ToolStripPanel> denetimine sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b5344-137">When you use <xref:System.Windows.Forms.MenuStrip> controls with an MDI form you must have the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="b5344-138">Windows Form Tasarımcısı MDI formunuzu oluşturmak için **araç kutusuna** <xref:System.Windows.Forms.ToolStripPanel> denetimini eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b5344-138">You must add the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox** to build your MDI form in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="b5344-139">**Araç kutusunu**açın ve kullanılabilir Windows Forms denetimlerini göstermek için **tüm Windows Forms** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b5344-139">Open the **Toolbox**, and then click the **All Windows Forms** tab to show the available Windows Forms controls.</span></span>

2. <span data-ttu-id="b5344-140">Sağ tıklayarak kısayol menüsünü açın ve **öğeleri seç**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="b5344-140">Right-click to open the shortcut menu, and select **Choose Items**.</span></span>

3. <span data-ttu-id="b5344-141">**Araç kutusu öğelerini Seç** iletişim kutusunda, **ToolStripPanel**' i bulana kadar **ad** sütununu aşağı kaydırın.</span><span class="sxs-lookup"><span data-stu-id="b5344-141">In the **Choose Toolbox Items** dialog box, scroll down the **Name** column until you find **ToolStripPanel**.</span></span>

4. <span data-ttu-id="b5344-142">**ToolStripPanel**'e göre onay kutusunu seçin ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b5344-142">Select the check box by **ToolStripPanel**, and then click **OK**.</span></span>

     <span data-ttu-id="b5344-143"><xref:System.Windows.Forms.ToolStripPanel> denetimi **araç kutusunda**görünür.</span><span class="sxs-lookup"><span data-stu-id="b5344-143">The <xref:System.Windows.Forms.ToolStripPanel> control appears in the **Toolbox**.</span></span>

## <a name="create-a-child-form"></a><span data-ttu-id="b5344-144">Alt form oluşturma</span><span class="sxs-lookup"><span data-stu-id="b5344-144">Create a child form</span></span>

<span data-ttu-id="b5344-145">Bu yordamda, kendi <xref:System.Windows.Forms.MenuStrip> denetimine sahip ayrı bir alt form sınıfı tanımlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="b5344-145">In this procedure, you will define a separate child form class that has its own <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="b5344-146">Bu formun menü öğeleri üst form ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b5344-146">The menu items for this form are merged with those of the parent form.</span></span>

1. <span data-ttu-id="b5344-147">Projeye `ChildForm` adlı yeni bir form ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b5344-147">Add a new form named `ChildForm` to the project.</span></span>

     <span data-ttu-id="b5344-148">Daha fazla bilgi için bkz. [nasıl yapılır: bir projeye Windows Forms ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b5344-148">For more information, see [How to: Add Windows Forms to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).</span></span>

2. <span data-ttu-id="b5344-149">**Araç kutusundan**bir <xref:System.Windows.Forms.MenuStrip> denetimini alt form üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="b5344-149">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the child form.</span></span>

3. <span data-ttu-id="b5344-150"><xref:System.Windows.Forms.MenuStrip> denetimin tasarımcı eylemleri glifsimgesine (![küçük siyah ok](./media/designer-actions-glyph.gif)) tıklayın ve ardından **öğeleri Düzenle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="b5344-150">Click the <xref:System.Windows.Forms.MenuStrip> control's designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)), and then select **Edit Items**.</span></span>

4. <span data-ttu-id="b5344-151">**Öğeler koleksiyonu Düzenleyicisi** iletişim kutusunda alt menüye **ChildMenuItem** adlı yeni bir <xref:System.Windows.Forms.ToolStripMenuItem> ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b5344-151">In the **Items Collection Editor** dialog box, add a new <xref:System.Windows.Forms.ToolStripMenuItem> named **ChildMenuItem** to the child menu.</span></span>

     <span data-ttu-id="b5344-152">Daha fazla bilgi için bkz. [ToolStrip öğeleri koleksiyon Düzenleyicisi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b5344-152">For more information, see [ToolStrip Items Collection Editor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).</span></span>

## <a name="test-the-form"></a><span data-ttu-id="b5344-153">Formu test etme</span><span class="sxs-lookup"><span data-stu-id="b5344-153">Test the form</span></span>

1. <span data-ttu-id="b5344-154">Formunuzu derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b5344-154">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="b5344-155">Menüyü açmak için **pencere** menü öğesine tıklayın ve sonra **Yeni**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b5344-155">Click the **Window** menu item to open the menu, and then click **New**.</span></span>

     <span data-ttu-id="b5344-156">Formun MDI istemci alanında yeni bir alt form oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b5344-156">A new child form is created in the form's MDI client area.</span></span> <span data-ttu-id="b5344-157">Alt formun menüsü, ana menü ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b5344-157">The child form's menu is merged with the main menu.</span></span>

3. <span data-ttu-id="b5344-158">Alt formu kapatın.</span><span class="sxs-lookup"><span data-stu-id="b5344-158">Close the child form.</span></span>

     <span data-ttu-id="b5344-159">Alt formun menüsü, ana menüden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="b5344-159">The child form's menu is removed from the main menu.</span></span>

4. <span data-ttu-id="b5344-160">**Yeni** birkaç kez tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b5344-160">Click **New** several times.</span></span>

     <span data-ttu-id="b5344-161"><xref:System.Windows.Forms.MenuStrip> denetiminin <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliği atandığından, alt formlar **pencere** menü öğesi altında otomatik olarak listelenir.</span><span class="sxs-lookup"><span data-stu-id="b5344-161">The child forms are automatically listed under the **Window** menu item because the <xref:System.Windows.Forms.MenuStrip> control's <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property is assigned.</span></span>

## <a name="add-toolstrip-support"></a><span data-ttu-id="b5344-162">ToolStrip desteği ekle</span><span class="sxs-lookup"><span data-stu-id="b5344-162">Add ToolStrip support</span></span>

<span data-ttu-id="b5344-163">Bu yordamda, MDI parent form 'a dört <xref:System.Windows.Forms.ToolStrip> denetimi ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b5344-163">In this procedure, you will add four <xref:System.Windows.Forms.ToolStrip> controls to the MDI parent form.</span></span> <span data-ttu-id="b5344-164">Her <xref:System.Windows.Forms.ToolStrip> denetimi, formun kenarına yerleştirilen bir <xref:System.Windows.Forms.ToolStripPanel> denetiminin içine eklenir.</span><span class="sxs-lookup"><span data-stu-id="b5344-164">Each <xref:System.Windows.Forms.ToolStrip> control is added inside a <xref:System.Windows.Forms.ToolStripPanel> control, which is docked to the edge of the form.</span></span>

1. <span data-ttu-id="b5344-165">**Araç kutusundan**bir <xref:System.Windows.Forms.ToolStripPanel> denetimini form üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="b5344-165">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStripPanel> control onto the form.</span></span>

2. <span data-ttu-id="b5344-166"><xref:System.Windows.Forms.ToolStripPanel> denetimi seçiliyken **araç kutusunda**<xref:System.Windows.Forms.ToolStrip> denetimine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b5344-166">With the <xref:System.Windows.Forms.ToolStripPanel> control selected, double-click the <xref:System.Windows.Forms.ToolStrip> control in the **Toolbox**.</span></span>

     <span data-ttu-id="b5344-167"><xref:System.Windows.Forms.ToolStripPanel> denetiminde <xref:System.Windows.Forms.ToolStrip> denetimi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b5344-167">A <xref:System.Windows.Forms.ToolStrip> control is created in the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

3. <span data-ttu-id="b5344-168"><xref:System.Windows.Forms.ToolStripPanel> denetimini seçin.</span><span class="sxs-lookup"><span data-stu-id="b5344-168">Select the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

4. <span data-ttu-id="b5344-169">Özellikler penceresi, denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliğinin değerini <xref:System.Windows.Forms.DockStyle.Left>olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b5344-169">In the Properties window, change the value of the control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span>

     <span data-ttu-id="b5344-170"><xref:System.Windows.Forms.ToolStripPanel> denetim noktaları formun sol tarafına, ana menünün altına göre yapılır.</span><span class="sxs-lookup"><span data-stu-id="b5344-170">The <xref:System.Windows.Forms.ToolStripPanel> control docks to the left side of the form, underneath the main menu.</span></span> <span data-ttu-id="b5344-171">MDI istemci alanı, <xref:System.Windows.Forms.ToolStripPanel> denetimine uyacak şekilde yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b5344-171">The MDI client area resizes to fit the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

5. <span data-ttu-id="b5344-172">1 ile 4 arasındaki adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="b5344-172">Repeat steps 1 through 4.</span></span>

     <span data-ttu-id="b5344-173">Yeni <xref:System.Windows.Forms.ToolStripPanel> denetimini formun en üstüne yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="b5344-173">Dock the new <xref:System.Windows.Forms.ToolStripPanel> control to the top of the form.</span></span>

     <span data-ttu-id="b5344-174"><xref:System.Windows.Forms.ToolStripPanel> denetimi ana menünün altına, ancak ilk <xref:System.Windows.Forms.ToolStripPanel> denetiminin sağına yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b5344-174">The <xref:System.Windows.Forms.ToolStripPanel> control is docked underneath the main menu, but to the right of the first <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="b5344-175">Bu adımda, <xref:System.Windows.Forms.ToolStripPanel> denetimlerinde doğru şekilde konumlama ile z düzeninin önemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b5344-175">This step illustrates the importance of z-order in correctly positioning <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

6. <span data-ttu-id="b5344-176">İki <xref:System.Windows.Forms.ToolStripPanel> denetimi için 1 ile 4 arasındaki adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="b5344-176">Repeat steps 1 through 4 for two more <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

     <span data-ttu-id="b5344-177">Yeni <xref:System.Windows.Forms.ToolStripPanel> denetimlerini formun sağına ve sonuna yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="b5344-177">Dock the new <xref:System.Windows.Forms.ToolStripPanel> controls to the right and bottom of the form.</span></span>

## <a name="arrange-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="b5344-178">ToolStripPanel denetimlerini Z sırasına göre düzenleme</span><span class="sxs-lookup"><span data-stu-id="b5344-178">Arrange ToolStripPanel controls by Z-order</span></span>

<span data-ttu-id="b5344-179">MDI formunuzdaki yerleşik bir <xref:System.Windows.Forms.ToolStripPanel> denetiminin konumu, denetimin z düzeninde bulunduğu konuma göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="b5344-179">The position of a docked <xref:System.Windows.Forms.ToolStripPanel> control on your MDI form is determined by the control's position in the z-order.</span></span> <span data-ttu-id="b5344-180">Belge Anahattı penceresinde, denetimlerinizin z düzenini kolayca düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5344-180">You can easily arrange the z-order of your controls in the Document Outline window.</span></span>

1. <span data-ttu-id="b5344-181">**Görünüm** menüsünde **diğer pencereler**' e ve ardından **Belge Anahattı**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b5344-181">In the **View** menu, click **Other Windows**, and then click **Document Outline**.</span></span>

     <span data-ttu-id="b5344-182">Önceki yordamdan <xref:System.Windows.Forms.ToolStripPanel> denetimlerinizi düzenleme işlemi standart dışı.</span><span class="sxs-lookup"><span data-stu-id="b5344-182">The arrangement of your <xref:System.Windows.Forms.ToolStripPanel> controls from the previous procedure is nonstandard.</span></span> <span data-ttu-id="b5344-183">Bunun nedeni, z düzeninin doğru olmaması.</span><span class="sxs-lookup"><span data-stu-id="b5344-183">This is because the z-order is not correct.</span></span> <span data-ttu-id="b5344-184">Denetimlerin z düzenini değiştirmek için belge anahattı penceresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5344-184">Use the Document Outline window to change the z-order of the controls.</span></span>

2. <span data-ttu-id="b5344-185">Belge Anahattı penceresinde **ToolStripPanel4**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="b5344-185">In the Document Outline window, select **ToolStripPanel4**.</span></span>

3. <span data-ttu-id="b5344-186">**ToolStripPanel4** listenin en altında olana kadar aşağı ok düğmesine tekrar tekrar tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b5344-186">Click the down-arrow button repeatedly, until **ToolStripPanel4** is at the bottom of the list.</span></span>

     <span data-ttu-id="b5344-187">**ToolStripPanel4** denetimi, formun alt kısmına, diğer denetimlerin altına yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b5344-187">The **ToolStripPanel4** control is docked to the bottom of the form, underneath the other controls.</span></span>

4. <span data-ttu-id="b5344-188">**ToolStripPanel2**öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b5344-188">Select **ToolStripPanel2**.</span></span>

5. <span data-ttu-id="b5344-189">Listeyi listede üçüncü olarak konumlandırmak için aşağı ok düğmesine bir kez tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b5344-189">Click the down-arrow button one time to position the control third in the list.</span></span>

     <span data-ttu-id="b5344-190">**ToolStripPanel2** denetimi formun en üstüne, ana menünün altına ve diğer denetimlerin üstüne yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b5344-190">The **ToolStripPanel2** control is docked to the top of the form, underneath the main menu and above the other controls.</span></span>

6. <span data-ttu-id="b5344-191">**Belge ana hattı** penceresinde çeşitli denetimler ' i seçin ve z düzeninde farklı konumlara taşıyın.</span><span class="sxs-lookup"><span data-stu-id="b5344-191">Select various controls in the **Document Outline** window and move them to different positions in the z-order.</span></span> <span data-ttu-id="b5344-192">Sabitlenmiş denetimlerin yerleştirilme üzerinde z düzeninin etkisini göz önünde edin.</span><span class="sxs-lookup"><span data-stu-id="b5344-192">Note the effect of the z-order on the placement of docked controls.</span></span> <span data-ttu-id="b5344-193">Değişikliklerinizi geri almak için **düzenleme** menüsünde CTRL-Z veya **geri al** komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5344-193">Use CTRL-Z or **Undo** on the **Edit** menu to undo your changes.</span></span>

## <a name="checkpoint---test-your-form"></a><span data-ttu-id="b5344-194">Kontrol noktası-formunuzu test etme</span><span class="sxs-lookup"><span data-stu-id="b5344-194">Checkpoint - test your form</span></span>

1. <span data-ttu-id="b5344-195">Formunuzu derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b5344-195">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="b5344-196"><xref:System.Windows.Forms.ToolStrip> denetimin bir öğesine tıklayın ve denetimi formdaki farklı konumlara sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="b5344-196">Click the grip of a <xref:System.Windows.Forms.ToolStrip> control and drag the control to different positions on the form.</span></span>

     <span data-ttu-id="b5344-197">Bir <xref:System.Windows.Forms.ToolStrip> denetimini, bir <xref:System.Windows.Forms.ToolStripPanel> denetiminden diğerine sürükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5344-197">You can drag a <xref:System.Windows.Forms.ToolStrip> control from one <xref:System.Windows.Forms.ToolStripPanel> control to another.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b5344-198">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="b5344-198">Next steps</span></span>

<span data-ttu-id="b5344-199">Bu kılavuzda, <xref:System.Windows.Forms.ToolStrip> denetimleri ve menü birleştirme ile bir MDI parent formu oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="b5344-199">In this walkthrough, you have created an MDI parent form with <xref:System.Windows.Forms.ToolStrip> controls and menu merging.</span></span> <span data-ttu-id="b5344-200">Denetimlerin <xref:System.Windows.Forms.ToolStrip> ailesini birçok farklı amaçla kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b5344-200">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="b5344-201"><xref:System.Windows.Forms.ContextMenuStrip>denetimlerle ilgili kısayol menüleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b5344-201">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="b5344-202">Daha fazla bilgi için bkz. [ContextMenu bileşenine genel bakış](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b5344-202">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="b5344-203">Otomatik olarak doldurulmuş bir standart menü içeren bir form oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="b5344-203">Created a form with an automatically populated standard menu.</span></span> <span data-ttu-id="b5344-204">Daha fazla bilgi için bkz. [Izlenecek yol: bir forma standart menü öğeleri sağlama](walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="b5344-204">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>

- <span data-ttu-id="b5344-205"><xref:System.Windows.Forms.ToolStrip> denetimlerine profesyonel bir görünüm kazandırın.</span><span class="sxs-lookup"><span data-stu-id="b5344-205">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="b5344-206">Daha fazla bilgi için bkz. [nasıl yapılır: bir uygulama Için ToolStrip oluşturucuyu ayarlama](how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="b5344-206">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b5344-207">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5344-207">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="b5344-208">Nasıl yapılır: MDI Üst Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b5344-208">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="b5344-209">Nasıl yapılır: MDI Alt Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b5344-209">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="b5344-210">Nasıl yapılır: Bir MDI Açılan Menüsüne MenuStrip ekleme</span><span class="sxs-lookup"><span data-stu-id="b5344-210">How to: Insert a MenuStrip into an MDI Drop-Down Menu</span></span>](how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)
- [<span data-ttu-id="b5344-211">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="b5344-211">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
