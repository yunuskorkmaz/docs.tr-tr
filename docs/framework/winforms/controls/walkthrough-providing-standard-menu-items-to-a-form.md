---
title: 'İzlenecek yol: Bir Forma Standart Menü Öğeleri Sağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
ms.openlocfilehash: ebfacadfee3ea069359a72ea0402751e9e6280d7
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211513"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a><span data-ttu-id="32cd6-102">İzlenecek yol: Bir Forma Standart Menü Öğeleri Sağlama</span><span class="sxs-lookup"><span data-stu-id="32cd6-102">Walkthrough: Providing Standard Menu Items to a Form</span></span>

<span data-ttu-id="32cd6-103">Formlarınızla için standart bir menü sağlayabilir <xref:System.Windows.Forms.MenuStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="32cd6-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

<span data-ttu-id="32cd6-104">Bu izlenecek yolda nasıl kullanılacağını gösterir. bir <xref:System.Windows.Forms.MenuStrip> standart menü oluşturmak için denetimi.</span><span class="sxs-lookup"><span data-stu-id="32cd6-104">This walkthrough demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a standard menu.</span></span> <span data-ttu-id="32cd6-105">Bir kullanıcı bir menü öğesi seçtiğinde, form ayrıca yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="32cd6-105">The form also responds when a user selects a menu item.</span></span> <span data-ttu-id="32cd6-106">Aşağıdaki görevler bu kılavuzda gösterilen:</span><span class="sxs-lookup"><span data-stu-id="32cd6-106">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="32cd6-107">Bir Windows Forms projesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="32cd6-107">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="32cd6-108">Standart menü oluşturma.</span><span class="sxs-lookup"><span data-stu-id="32cd6-108">Creating a standard menu.</span></span>

- <span data-ttu-id="32cd6-109">Oluşturma bir <xref:System.Windows.Forms.StatusStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="32cd6-109">Creating a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

- <span data-ttu-id="32cd6-110">Menü öğesi seçimi işleme.</span><span class="sxs-lookup"><span data-stu-id="32cd6-110">Handling menu item selection.</span></span>

<span data-ttu-id="32cd6-111">İşlemi tamamladığınızda, menü öğesi seçimleri görüntüleyen bir standart menü formla olacaktır bir <xref:System.Windows.Forms.StatusStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="32cd6-111">When you are finished, you will have a form with a standard menu that displays menu item selections in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

<span data-ttu-id="32cd6-112">Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: Bir forma standart menü öğeleri sağlama](how-to-provide-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="32cd6-112">To copy the code in this topic as a single listing, see [How to: Provide Standard Menu Items to a Form](how-to-provide-standard-menu-items-to-a-form.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="32cd6-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="32cd6-113">Prerequisites</span></span>

<span data-ttu-id="32cd6-114">Bu izlenecek yolu tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="32cd6-114">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="32cd6-115">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="32cd6-115">Create the project</span></span>

1. <span data-ttu-id="32cd6-116">Visual Studio'da adlı bir Windows uygulaması projesi oluşturmak **StandardMenuForm** (**dosya** > **yeni** > **proje**   >  **Visual C#**  veya **Visual Basic** > **Klasik Masaüstü**  >  **Windows Forms uygulamalarındaki**).</span><span class="sxs-lookup"><span data-stu-id="32cd6-116">In Visual Studio, create a Windows application project called **StandardMenuForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="32cd6-117">Formu Windows Form Tasarımcısı'nda seçin.</span><span class="sxs-lookup"><span data-stu-id="32cd6-117">In the Windows Forms Designer, select the form.</span></span>

## <a name="create-a-standard-menu"></a><span data-ttu-id="32cd6-118">Standart menü oluşturma</span><span class="sxs-lookup"><span data-stu-id="32cd6-118">Create a standard menu</span></span>

<span data-ttu-id="32cd6-119">Windows Form Tasarımcısı otomatik olarak doldurabilirsiniz bir <xref:System.Windows.Forms.MenuStrip> standart menü öğeleri ile denetimi.</span><span class="sxs-lookup"><span data-stu-id="32cd6-119">The Windows Forms Designer can automatically populate a <xref:System.Windows.Forms.MenuStrip> control with standard menu items.</span></span>

1. <span data-ttu-id="32cd6-120">Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.MenuStrip> denetimi formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="32cd6-120">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto your form.</span></span>

2. <span data-ttu-id="32cd6-121">Tıklayın <xref:System.Windows.Forms.MenuStrip> denetimin akıllı etiket karakterini (![akıllı etiket karakterini](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) seçip **standart öğeleri Ekle**.</span><span class="sxs-lookup"><span data-stu-id="32cd6-121">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Insert Standard Items**.</span></span>

     <span data-ttu-id="32cd6-122"><xref:System.Windows.Forms.MenuStrip> Denetimi, standart menü öğeleri ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="32cd6-122">The <xref:System.Windows.Forms.MenuStrip> control is populated with the standard menu items.</span></span>

3. <span data-ttu-id="32cd6-123">Tıklayın **dosya** kendi varsayılan menü öğeleri ve ilişkili simgeleri görmek için menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="32cd6-123">Click the **File** menu item to see its default menu items and corresponding icons.</span></span>

## <a name="create-a-statusstrip-control"></a><span data-ttu-id="32cd6-124">StatusStrip denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="32cd6-124">Create a StatusStrip control</span></span>

<span data-ttu-id="32cd6-125">Kullanım <xref:System.Windows.Forms.StatusStrip> denetimi Windows Forms uygulamaları için durumu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="32cd6-125">Use the <xref:System.Windows.Forms.StatusStrip> control to display status for your Windows Forms applications.</span></span> <span data-ttu-id="32cd6-126">Menü öğeleri, kullanıcı tarafından seçilen görüntülenen geçerli örnekte, bir <xref:System.Windows.Forms.StatusStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="32cd6-126">In the current example, menu items selected by the user are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

1. <span data-ttu-id="32cd6-127">Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.StatusStrip> denetimi formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="32cd6-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.StatusStrip> control onto your form.</span></span>

     <span data-ttu-id="32cd6-128"><xref:System.Windows.Forms.StatusStrip> Denetimi otomatik olarak noktaları formun altına.</span><span class="sxs-lookup"><span data-stu-id="32cd6-128">The <xref:System.Windows.Forms.StatusStrip> control automatically docks to the bottom of the form.</span></span>

2. <span data-ttu-id="32cd6-129">Tıklayın <xref:System.Windows.Forms.StatusStrip> denetimin açılan düğmesine ve select **StatusLabel** eklemek için bir <xref:System.Windows.Forms.ToolStripStatusLabel> denetimini <xref:System.Windows.Forms.StatusStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="32cd6-129">Click the <xref:System.Windows.Forms.StatusStrip> control's drop-down button and select **StatusLabel** to add a <xref:System.Windows.Forms.ToolStripStatusLabel> control to the <xref:System.Windows.Forms.StatusStrip> control.</span></span>

## <a name="handle-item-selection"></a><span data-ttu-id="32cd6-130">Tanıtıcı öğe seçimi</span><span class="sxs-lookup"><span data-stu-id="32cd6-130">Handle item selection</span></span>

<span data-ttu-id="32cd6-131">Tanıtıcı <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olay kullanıcı menü öğesi seçtiğinde yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="32cd6-131">Handle the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event to respond when the user selects a menu item.</span></span>

1. <span data-ttu-id="32cd6-132">Tıklayın **dosya** oluşturma içinde oluşturduğunuz bir menü öğesi bir standart menü bölümü.</span><span class="sxs-lookup"><span data-stu-id="32cd6-132">Click the **File** menu item that you created in the Creating a Standard Menu section.</span></span>

2. <span data-ttu-id="32cd6-133">İçinde **özellikleri** penceresinde tıklayın **olayları**.</span><span class="sxs-lookup"><span data-stu-id="32cd6-133">In the **Properties** window, click **Events**.</span></span>

3. <span data-ttu-id="32cd6-134">Çift <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olay.</span><span class="sxs-lookup"><span data-stu-id="32cd6-134">Double-click the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

     <span data-ttu-id="32cd6-135">Windows Form Tasarımcısı için bir olay işleyicisi oluşturur <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olay.</span><span class="sxs-lookup"><span data-stu-id="32cd6-135">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

4. <span data-ttu-id="32cd6-136">Olay işleyicisine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="32cd6-136">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]

5. <span data-ttu-id="32cd6-137">INSERT `UpdateStatus` forma yardımcı yöntem tanımı.</span><span class="sxs-lookup"><span data-stu-id="32cd6-137">Insert the `UpdateStatus` utility method definition into the form.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]

## <a name="checkpoint--test-your-form"></a><span data-ttu-id="32cd6-138">Checkpoint-formunuza test</span><span class="sxs-lookup"><span data-stu-id="32cd6-138">Checkpoint -test your form</span></span>

1. <span data-ttu-id="32cd6-139">Tuşuna **F5** derlemek ve formunuza çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="32cd6-139">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="32cd6-140">Tıklayın **dosya** menüsünü açmak için menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="32cd6-140">Click the **File** menu item to open the menu.</span></span>

3. <span data-ttu-id="32cd6-141">Üzerinde **dosya** menüsünde seçmek için öğelerden birine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="32cd6-141">On the **File** menu, click one of the items to select it.</span></span>

     <span data-ttu-id="32cd6-142"><xref:System.Windows.Forms.StatusStrip> Denetim seçili öğeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="32cd6-142">The <xref:System.Windows.Forms.StatusStrip> control displays the selected item.</span></span>

## <a name="next-steps"></a><span data-ttu-id="32cd6-143">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="32cd6-143">Next steps</span></span>

<span data-ttu-id="32cd6-144">Bu kılavuzda, bir form içeren bir standart menü oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="32cd6-144">In this walkthrough, you have created a form with a standard menu.</span></span> <span data-ttu-id="32cd6-145">Kullanabileceğiniz <xref:System.Windows.Forms.ToolStrip> birçok başka amaçlarla denetimlerin ailesi:</span><span class="sxs-lookup"><span data-stu-id="32cd6-145">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="32cd6-146">Sahip, denetimler için kısayol menüleri oluşturma <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="32cd6-146">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="32cd6-147">Daha fazla bilgi için [ContextMenu bileşenine genel bakış](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="32cd6-147">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="32cd6-148">Yerleştirme ile birden çok belge arabirimi (MDI) form oluşturma <xref:System.Windows.Forms.ToolStrip> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="32cd6-148">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="32cd6-149">Daha fazla bilgi için [izlenecek yol: Menü birleştirme ve ToolStrip denetimleri içeren MDI formu oluşturma](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="32cd6-149">For more information, see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

- <span data-ttu-id="32cd6-150">Verin, <xref:System.Windows.Forms.ToolStrip> profesyonel bir görünümünü denetler.</span><span class="sxs-lookup"><span data-stu-id="32cd6-150">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="32cd6-151">Daha fazla bilgi için [nasıl yapılır: Bir uygulama için ToolStrip oluşturucusunu ayarlama](how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="32cd6-151">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="32cd6-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32cd6-152">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="32cd6-153">MenuStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="32cd6-153">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
