---
title: 'İzlenecek yol: Menü Birleştirme ve ToolStrip Denetimleri içeren MDI Formu Oluşturma'
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
ms.openlocfilehash: 5853760231cbece27805923c009d83e16c9b0a5e
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211555"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="5be3b-102">İzlenecek yol: Menü Birleştirme ve ToolStrip Denetimleri içeren MDI Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5be3b-102">Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls</span></span>

<span data-ttu-id="5be3b-103"><xref:System.Windows.Forms?displayProperty=nameWithType> Ad alanı birden çok belge arabirimi (MDI) uygulamaları destekler ve <xref:System.Windows.Forms.MenuStrip> denetimi, menü birleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="5be3b-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="5be3b-104">MDI formları aynı zamanda <xref:System.Windows.Forms.ToolStrip> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="5be3b-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="5be3b-105">Bu izlenecek yolda nasıl kullanılacağını gösterir <xref:System.Windows.Forms.ToolStripPanel> denetimleriyle MDI formu.</span><span class="sxs-lookup"><span data-stu-id="5be3b-105">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="5be3b-106">Formu ile alt menülerini birleştirme menüsünü de destekler.</span><span class="sxs-lookup"><span data-stu-id="5be3b-106">The form also supports menu merging with child menus.</span></span> <span data-ttu-id="5be3b-107">Aşağıdaki görevler bu kılavuzda gösterilen:</span><span class="sxs-lookup"><span data-stu-id="5be3b-107">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="5be3b-108">Bir Windows Forms projesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="5be3b-108">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="5be3b-109">Formunuz için ana menü oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="5be3b-109">Creating the main menu for your form.</span></span> <span data-ttu-id="5be3b-110">Menü gerçek adıyla değişir.</span><span class="sxs-lookup"><span data-stu-id="5be3b-110">The actual name of the menu will vary.</span></span>

- <span data-ttu-id="5be3b-111">Ekleme <xref:System.Windows.Forms.ToolStripPanel> denetimini **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="5be3b-111">Adding the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox**.</span></span>

- <span data-ttu-id="5be3b-112">Bir alt form oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="5be3b-112">Creating a child form.</span></span>

- <span data-ttu-id="5be3b-113">Düzenleme <xref:System.Windows.Forms.ToolStripPanel> z sırasına göre denetimler.</span><span class="sxs-lookup"><span data-stu-id="5be3b-113">Arranging <xref:System.Windows.Forms.ToolStripPanel> controls by z-order.</span></span>

<span data-ttu-id="5be3b-114">İşlemi tamamladığınızda, menü birleştirme ve taşınabilir destekleyen MDI Formu olacaktır <xref:System.Windows.Forms.ToolStrip> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="5be3b-114">When you are finished, you will have an MDI form that supports menu merging and movable <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="5be3b-115">Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: Menü birleştirme ve ToolStrip denetimleri içeren MDI formu oluşturma](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="5be3b-115">To copy the code in this topic as a single listing, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5be3b-116">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="5be3b-116">Prerequisites</span></span>

<span data-ttu-id="5be3b-117">Bu izlenecek yolu tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="5be3b-117">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="5be3b-118">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="5be3b-118">Create the project</span></span>

1. <span data-ttu-id="5be3b-119">Visual Studio'da adlı bir Windows uygulaması projesi oluşturmak **MdiForm** (**dosya** > **yeni** > **proje**  >  **Visual C#**  veya **Visual Basic** > **Klasik Masaüstü**  >   **Windows Forms uygulamalarındaki**).</span><span class="sxs-lookup"><span data-stu-id="5be3b-119">In Visual Studio, create a Windows Application project called **MdiForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="5be3b-120">Formu Windows Form Tasarımcısı'nda seçin.</span><span class="sxs-lookup"><span data-stu-id="5be3b-120">In the Windows Forms Designer, select the form.</span></span>

3. <span data-ttu-id="5be3b-121">Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.Form.IsMdiContainer%2A> için `true`.</span><span class="sxs-lookup"><span data-stu-id="5be3b-121">In the Properties window, set the value of the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> to `true`.</span></span>

## <a name="create-the-main-menu"></a><span data-ttu-id="5be3b-122">Ana menü oluşturma</span><span class="sxs-lookup"><span data-stu-id="5be3b-122">Create the main menu</span></span>

<span data-ttu-id="5be3b-123">Üst MDI formu ana menü içerir.</span><span class="sxs-lookup"><span data-stu-id="5be3b-123">The parent MDI form contains the main menu.</span></span> <span data-ttu-id="5be3b-124">Ana menü öğesi adlı tek menü sahip **penceresi**.</span><span class="sxs-lookup"><span data-stu-id="5be3b-124">The main menu has one menu item named **Window**.</span></span> <span data-ttu-id="5be3b-125">İle **penceresi** menü öğesi alt formları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5be3b-125">With the **Window** menu item, you can create child forms.</span></span> <span data-ttu-id="5be3b-126">Ana menüye menü öğeleri alt formları birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5be3b-126">Menu items from child forms are merged into the main menu.</span></span>

1. <span data-ttu-id="5be3b-127">Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.MenuStrip> forma denetim.</span><span class="sxs-lookup"><span data-stu-id="5be3b-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the form.</span></span>

2. <span data-ttu-id="5be3b-128">Ekleme bir <xref:System.Windows.Forms.ToolStripMenuItem> için <xref:System.Windows.Forms.MenuStrip> denetlemek ve adlandırın **penceresi**.</span><span class="sxs-lookup"><span data-stu-id="5be3b-128">Add a <xref:System.Windows.Forms.ToolStripMenuItem> to the <xref:System.Windows.Forms.MenuStrip> control and name it **Window**.</span></span>

3. <span data-ttu-id="5be3b-129">Seçin <xref:System.Windows.Forms.MenuStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="5be3b-129">Select the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

4. <span data-ttu-id="5be3b-130">Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliğini `ToolStripMenuItem1`.</span><span class="sxs-lookup"><span data-stu-id="5be3b-130">In the Properties window, set the value of the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to `ToolStripMenuItem1`.</span></span>

5. <span data-ttu-id="5be3b-131">Eklemek için bir alt **penceresi** menü öğesini ve ardından ad alt **yeni**.</span><span class="sxs-lookup"><span data-stu-id="5be3b-131">Add a subitem to the **Window** menu item, and then name the subitem **New**.</span></span>

6. <span data-ttu-id="5be3b-132">Özellikler penceresinde tıklayın **olayları**.</span><span class="sxs-lookup"><span data-stu-id="5be3b-132">In the Properties window, click **Events**.</span></span>

7. <span data-ttu-id="5be3b-133">Çift <xref:System.Windows.Forms.ToolStripItem.Click> olay.</span><span class="sxs-lookup"><span data-stu-id="5be3b-133">Double-click the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

     <span data-ttu-id="5be3b-134">Windows Form Tasarımcısı için bir olay işleyicisi oluşturur <xref:System.Windows.Forms.ToolStripItem.Click> olay.</span><span class="sxs-lookup"><span data-stu-id="5be3b-134">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

8. <span data-ttu-id="5be3b-135">Olay işleyicisine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5be3b-135">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]

## <a name="add-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="5be3b-136">ToolStripPanel denetimi araç kutusuna ekleme</span><span class="sxs-lookup"><span data-stu-id="5be3b-136">Add the ToolStripPanel control to the Toolbox</span></span>

<span data-ttu-id="5be3b-137">Kullanırken <xref:System.Windows.Forms.MenuStrip> denetimleriyle MDI Formu olmalıdır <xref:System.Windows.Forms.ToolStripPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="5be3b-137">When you use <xref:System.Windows.Forms.MenuStrip> controls with an MDI form you must have the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="5be3b-138">Eklemelisiniz <xref:System.Windows.Forms.ToolStripPanel> denetimini **araç kutusu** , MDI Formu Windows Form Tasarımcısı'nda oluşturulacak.</span><span class="sxs-lookup"><span data-stu-id="5be3b-138">You must add the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox** to build your MDI form in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="5be3b-139">Açık **araç kutusu**ve ardından **tüm Windows Formları** kullanılabilir Windows Forms denetimleri göstermek için sekmesinde.</span><span class="sxs-lookup"><span data-stu-id="5be3b-139">Open the **Toolbox**, and then click the **All Windows Forms** tab to show the available Windows Forms controls.</span></span>

2. <span data-ttu-id="5be3b-140">Kısayol menüsünü açmak için sağ tıklatın ve seçin **öğelerini Seç**.</span><span class="sxs-lookup"><span data-stu-id="5be3b-140">Right-click to open the shortcut menu, and select **Choose Items**.</span></span>

3. <span data-ttu-id="5be3b-141">İçinde **araç kutusu öğelerini Seç** iletişim kutusu, aşağı kaydırın **adı** bulana kadar sütun **ToolStripPanel**.</span><span class="sxs-lookup"><span data-stu-id="5be3b-141">In the **Choose Toolbox Items** dialog box, scroll down the **Name** column until you find **ToolStripPanel**.</span></span>

4. <span data-ttu-id="5be3b-142">Onay kutusunu **ToolStripPanel**ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="5be3b-142">Select the check box by **ToolStripPanel**, and then click **OK**.</span></span>

     <span data-ttu-id="5be3b-143"><xref:System.Windows.Forms.ToolStripPanel> Denetimi görünür **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="5be3b-143">The <xref:System.Windows.Forms.ToolStripPanel> control appears in the **Toolbox**.</span></span>

## <a name="create-a-child-form"></a><span data-ttu-id="5be3b-144">Bir alt form oluşturun</span><span class="sxs-lookup"><span data-stu-id="5be3b-144">Create a child form</span></span>

<span data-ttu-id="5be3b-145">Bu yordamda, kendi ayrı bir alt form sınıfı tanımlayacak <xref:System.Windows.Forms.MenuStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="5be3b-145">In this procedure, you will define a separate child form class that has its own <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="5be3b-146">Bu form için menü öğeleri bu üst formu ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5be3b-146">The menu items for this form are merged with those of the parent form.</span></span>

1. <span data-ttu-id="5be3b-147">Adlı yeni bir form ekleyin `ChildForm` projeye.</span><span class="sxs-lookup"><span data-stu-id="5be3b-147">Add a new form named `ChildForm` to the project.</span></span>

     <span data-ttu-id="5be3b-148">Daha fazla bilgi için [nasıl yapılır: Windows formlarını bir projeye ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="5be3b-148">For more information, see [How to: Add Windows Forms to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).</span></span>

2. <span data-ttu-id="5be3b-149">Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.MenuStrip> alt forma denetim.</span><span class="sxs-lookup"><span data-stu-id="5be3b-149">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the child form.</span></span>

3. <span data-ttu-id="5be3b-150">Tıklayın <xref:System.Windows.Forms.MenuStrip> denetimin akıllı etiket karakterini (![akıllı etiket karakterini](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) ve ardından **öğe düzenleme**.</span><span class="sxs-lookup"><span data-stu-id="5be3b-150">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), and then select **Edit Items**.</span></span>

4. <span data-ttu-id="5be3b-151">İçinde **öğeler Koleksiyonu Düzenleyicisi** iletişim kutusunda, yeni bir <xref:System.Windows.Forms.ToolStripMenuItem> adlı **ChildMenuItem** alt menüsü.</span><span class="sxs-lookup"><span data-stu-id="5be3b-151">In the **Items Collection Editor** dialog box, add a new <xref:System.Windows.Forms.ToolStripMenuItem> named **ChildMenuItem** to the child menu.</span></span>

     <span data-ttu-id="5be3b-152">Daha fazla bilgi için [ToolStrip öğeler Koleksiyonu Düzenleyicisi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="5be3b-152">For more information, see [ToolStrip Items Collection Editor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).</span></span>

## <a name="test-the-form"></a><span data-ttu-id="5be3b-153">Form test</span><span class="sxs-lookup"><span data-stu-id="5be3b-153">Test the form</span></span>

1. <span data-ttu-id="5be3b-154">Tuşuna **F5** derlemek ve formunuza çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="5be3b-154">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="5be3b-155">Tıklayın **penceresi** menüsünü açın ve ardından menü öğesi **yeni**.</span><span class="sxs-lookup"><span data-stu-id="5be3b-155">Click the **Window** menu item to open the menu, and then click **New**.</span></span>

     <span data-ttu-id="5be3b-156">Yeni bir alt form, form denetiminin MDI istemci alanında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5be3b-156">A new child form is created in the form's MDI client area.</span></span> <span data-ttu-id="5be3b-157">Alt formun menüsünde ana menü ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5be3b-157">The child form's menu is merged with the main menu.</span></span>

3. <span data-ttu-id="5be3b-158">Alt formu kapatın.</span><span class="sxs-lookup"><span data-stu-id="5be3b-158">Close the child form.</span></span>

     <span data-ttu-id="5be3b-159">Alt formun menüsü, ana menüden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="5be3b-159">The child form's menu is removed from the main menu.</span></span>

4. <span data-ttu-id="5be3b-160">Tıklayın **yeni** birkaç kez.</span><span class="sxs-lookup"><span data-stu-id="5be3b-160">Click **New** several times.</span></span>

     <span data-ttu-id="5be3b-161">Alt formları otomatik olarak altında listelenen **penceresi** menü öğesi olduğundan <xref:System.Windows.Forms.MenuStrip> denetimin <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliğine atanır.</span><span class="sxs-lookup"><span data-stu-id="5be3b-161">The child forms are automatically listed under the **Window** menu item because the <xref:System.Windows.Forms.MenuStrip> control's <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property is assigned.</span></span>

## <a name="add-toolstrip-support"></a><span data-ttu-id="5be3b-162">ToolStrip desteği eklendi</span><span class="sxs-lookup"><span data-stu-id="5be3b-162">Add ToolStrip support</span></span>

<span data-ttu-id="5be3b-163">Bu yordamda, dört ekleyeceksiniz <xref:System.Windows.Forms.ToolStrip> MDI üst formu için denetimler.</span><span class="sxs-lookup"><span data-stu-id="5be3b-163">In this procedure, you will add four <xref:System.Windows.Forms.ToolStrip> controls to the MDI parent form.</span></span> <span data-ttu-id="5be3b-164">Her <xref:System.Windows.Forms.ToolStrip> denetimi içinde eklenir bir <xref:System.Windows.Forms.ToolStripPanel> form kenarına yerleştirildiğini denetimi.</span><span class="sxs-lookup"><span data-stu-id="5be3b-164">Each <xref:System.Windows.Forms.ToolStrip> control is added inside a <xref:System.Windows.Forms.ToolStripPanel> control, which is docked to the edge of the form.</span></span>

1. <span data-ttu-id="5be3b-165">Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.ToolStripPanel> forma denetim.</span><span class="sxs-lookup"><span data-stu-id="5be3b-165">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStripPanel> control onto the form.</span></span>

2. <span data-ttu-id="5be3b-166">İle <xref:System.Windows.Forms.ToolStripPanel> çift tıklayın, Denetim seçili <xref:System.Windows.Forms.ToolStrip> denetim **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="5be3b-166">With the <xref:System.Windows.Forms.ToolStripPanel> control selected, double-click the <xref:System.Windows.Forms.ToolStrip> control in the **Toolbox**.</span></span>

     <span data-ttu-id="5be3b-167">A <xref:System.Windows.Forms.ToolStrip> denetim oluşturuldu <xref:System.Windows.Forms.ToolStripPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="5be3b-167">A <xref:System.Windows.Forms.ToolStrip> control is created in the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

3. <span data-ttu-id="5be3b-168">Seçin <xref:System.Windows.Forms.ToolStripPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="5be3b-168">Select the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

4. <span data-ttu-id="5be3b-169">Özellikler penceresinde, denetimin değiştirin <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="5be3b-169">In the Properties window, change the value of the control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span>

     <span data-ttu-id="5be3b-170"><xref:System.Windows.Forms.ToolStripPanel> Kontrol noktalarını sol tarafındaki formun ana menü altında.</span><span class="sxs-lookup"><span data-stu-id="5be3b-170">The <xref:System.Windows.Forms.ToolStripPanel> control docks to the left side of the form, underneath the main menu.</span></span> <span data-ttu-id="5be3b-171">MDI istemci alanını uyacak şekilde yeniden boyutlandırır <xref:System.Windows.Forms.ToolStripPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="5be3b-171">The MDI client area resizes to fit the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

5. <span data-ttu-id="5be3b-172">1 ile 4 arasındaki adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="5be3b-172">Repeat steps 1 through 4.</span></span>

     <span data-ttu-id="5be3b-173">Yeni dock <xref:System.Windows.Forms.ToolStripPanel> üst form denetimi.</span><span class="sxs-lookup"><span data-stu-id="5be3b-173">Dock the new <xref:System.Windows.Forms.ToolStripPanel> control to the top of the form.</span></span>

     <span data-ttu-id="5be3b-174"><xref:System.Windows.Forms.ToolStripPanel> Denetim ana menü altında ancak ilk sağındaki yerleştirilmiştir <xref:System.Windows.Forms.ToolStripPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="5be3b-174">The <xref:System.Windows.Forms.ToolStripPanel> control is docked underneath the main menu, but to the right of the first <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="5be3b-175">Bu adım doğru konumlandırmada z düzenini önemini gösterir <xref:System.Windows.Forms.ToolStripPanel> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="5be3b-175">This step illustrates the importance of z-order in correctly positioning <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

6. <span data-ttu-id="5be3b-176">Daha fazla iki için 1 ile 4 arasındaki adımları yineleyin <xref:System.Windows.Forms.ToolStripPanel> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="5be3b-176">Repeat steps 1 through 4 for two more <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

     <span data-ttu-id="5be3b-177">Yeni dock <xref:System.Windows.Forms.ToolStripPanel> sağa ve formun altına denetimleri.</span><span class="sxs-lookup"><span data-stu-id="5be3b-177">Dock the new <xref:System.Windows.Forms.ToolStripPanel> controls to the right and bottom of the form.</span></span>

## <a name="arrange-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="5be3b-178">Z sırasına ToolStripPanel denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="5be3b-178">Arrange ToolStripPanel controls by Z-order</span></span>

<span data-ttu-id="5be3b-179">Bir yerleşik konumunu <xref:System.Windows.Forms.ToolStripPanel> , MDI formu denetimi, z düzenini denetimin konumu tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="5be3b-179">The position of a docked <xref:System.Windows.Forms.ToolStripPanel> control on your MDI form is determined by the control's position in the z-order.</span></span> <span data-ttu-id="5be3b-180">Belge Anahattı penceresi içinde denetimlerin z düzenini kolayca düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5be3b-180">You can easily arrange the z-order of your controls in the Document Outline window.</span></span>

1. <span data-ttu-id="5be3b-181">İçinde **görünümü** menüsünde tıklatın **diğer Windows**ve ardından **belge anahattı**.</span><span class="sxs-lookup"><span data-stu-id="5be3b-181">In the **View** menu, click **Other Windows**, and then click **Document Outline**.</span></span>

     <span data-ttu-id="5be3b-182">Düzenlemesini, <xref:System.Windows.Forms.ToolStripPanel> denetimleri önceki yordamın bildiriliyor.</span><span class="sxs-lookup"><span data-stu-id="5be3b-182">The arrangement of your <xref:System.Windows.Forms.ToolStripPanel> controls from the previous procedure is nonstandard.</span></span> <span data-ttu-id="5be3b-183">Z düzenini doğru olmadığı için budur.</span><span class="sxs-lookup"><span data-stu-id="5be3b-183">This is because the z-order is not correct.</span></span> <span data-ttu-id="5be3b-184">Belge Anahattı penceresi denetimlerinin z sıralamasını değiştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="5be3b-184">Use the Document Outline window to change the z-order of the controls.</span></span>

2. <span data-ttu-id="5be3b-185">Belge Anahattı penceresini seçin **ToolStripPanel4**.</span><span class="sxs-lookup"><span data-stu-id="5be3b-185">In the Document Outline window, select **ToolStripPanel4**.</span></span>

3. <span data-ttu-id="5be3b-186">Aşağı ok düğmesini tekrar tekrar kadar **ToolStripPanel4** listesinin alt.</span><span class="sxs-lookup"><span data-stu-id="5be3b-186">Click the down-arrow button repeatedly, until **ToolStripPanel4** is at the bottom of the list.</span></span>

     <span data-ttu-id="5be3b-187">**ToolStripPanel4** denetim, diğer denetimlerin altında formun altına yerleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5be3b-187">The **ToolStripPanel4** control is docked to the bottom of the form, underneath the other controls.</span></span>

4. <span data-ttu-id="5be3b-188">Seçin **ToolStripPanel2**.</span><span class="sxs-lookup"><span data-stu-id="5be3b-188">Select **ToolStripPanel2**.</span></span>

5. <span data-ttu-id="5be3b-189">Aşağı ok düğmesini denetimi üçüncü listede konumlandırmak için bir kez tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5be3b-189">Click the down-arrow button one time to position the control third in the list.</span></span>

     <span data-ttu-id="5be3b-190">**ToolStripPanel2** denetimi için ana menü altında ve diğer denetimleri yukarıda formun üst yerleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5be3b-190">The **ToolStripPanel2** control is docked to the top of the form, underneath the main menu and above the other controls.</span></span>

6. <span data-ttu-id="5be3b-191">Çeşitli denetimleri seçin **belge anahattı** penceresi ve z düzeninde farklı konumlara taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5be3b-191">Select various controls in the **Document Outline** window and move them to different positions in the z-order.</span></span> <span data-ttu-id="5be3b-192">Yerleşik denetimler yerleşimini z düzenini etkisini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5be3b-192">Note the effect of the z-order on the placement of docked controls.</span></span> <span data-ttu-id="5be3b-193">CTRL-Z kullanın veya **geri** üzerinde **Düzenle** değişikliklerinizi geri almak için menü.</span><span class="sxs-lookup"><span data-stu-id="5be3b-193">Use CTRL-Z or **Undo** on the **Edit** menu to undo your changes.</span></span>

## <a name="checkpoint---test-your-form"></a><span data-ttu-id="5be3b-194">Checkpoint - formunuza test</span><span class="sxs-lookup"><span data-stu-id="5be3b-194">Checkpoint - test your form</span></span>

1. <span data-ttu-id="5be3b-195">Tuşuna **F5** derlemek ve formunuza çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="5be3b-195">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="5be3b-196">Tutamacı tıklayın bir <xref:System.Windows.Forms.ToolStrip> denetlemek ve denetimi form üzerinde farklı konumlara sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="5be3b-196">Click the grip of a <xref:System.Windows.Forms.ToolStrip> control and drag the control to different positions on the form.</span></span>

     <span data-ttu-id="5be3b-197">Sürükleyebilirsiniz bir <xref:System.Windows.Forms.ToolStrip> bir denetimden <xref:System.Windows.Forms.ToolStripPanel> başka bir denetim.</span><span class="sxs-lookup"><span data-stu-id="5be3b-197">You can drag a <xref:System.Windows.Forms.ToolStrip> control from one <xref:System.Windows.Forms.ToolStripPanel> control to another.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5be3b-198">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="5be3b-198">Next steps</span></span>

<span data-ttu-id="5be3b-199">Bu kılavuzda, MDI üst formu ile oluşturduğunuz <xref:System.Windows.Forms.ToolStrip> denetimleri ve menü birleştirme.</span><span class="sxs-lookup"><span data-stu-id="5be3b-199">In this walkthrough, you have created an MDI parent form with <xref:System.Windows.Forms.ToolStrip> controls and menu merging.</span></span> <span data-ttu-id="5be3b-200">Kullanabileceğiniz <xref:System.Windows.Forms.ToolStrip> birçok başka amaçlarla denetimlerin ailesi:</span><span class="sxs-lookup"><span data-stu-id="5be3b-200">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="5be3b-201">Sahip, denetimler için kısayol menüleri oluşturma <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="5be3b-201">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="5be3b-202">Daha fazla bilgi için [ContextMenu bileşenine genel bakış](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5be3b-202">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="5be3b-203">Bir formu otomatik olarak doldurulan bir standart menü ile oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="5be3b-203">Created a form with an automatically populated standard menu.</span></span> <span data-ttu-id="5be3b-204">Daha fazla bilgi için [izlenecek yol: Bir forma standart menü öğeleri sağlama](walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="5be3b-204">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>

- <span data-ttu-id="5be3b-205">Verin, <xref:System.Windows.Forms.ToolStrip> profesyonel bir görünümünü denetler.</span><span class="sxs-lookup"><span data-stu-id="5be3b-205">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="5be3b-206">Daha fazla bilgi için [nasıl yapılır: Bir uygulama için ToolStrip oluşturucusunu ayarlama](how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="5be3b-206">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5be3b-207">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5be3b-207">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="5be3b-208">Nasıl yapılır: MDI üst formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="5be3b-208">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="5be3b-209">Nasıl yapılır: MDI alt formları oluştur</span><span class="sxs-lookup"><span data-stu-id="5be3b-209">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="5be3b-210">Nasıl yapılır: Bir MDI açılan menüsüne MenuStrip ekleme</span><span class="sxs-lookup"><span data-stu-id="5be3b-210">How to: Insert a MenuStrip into an MDI Drop-Down Menu</span></span>](how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)
- [<span data-ttu-id="5be3b-211">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="5be3b-211">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
