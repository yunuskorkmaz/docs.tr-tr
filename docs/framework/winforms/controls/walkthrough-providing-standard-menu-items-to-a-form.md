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
ms.openlocfilehash: ee80aad445c00bb4b98b49c80495fa512150bcef
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628780"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a><span data-ttu-id="7f138-102">İzlenecek yol: Bir Forma Standart Menü Öğeleri Sağlama</span><span class="sxs-lookup"><span data-stu-id="7f138-102">Walkthrough: Providing Standard Menu Items to a Form</span></span>

<span data-ttu-id="7f138-103"><xref:System.Windows.Forms.MenuStrip> denetimi ile formlarınızın standart bir menü sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f138-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

<span data-ttu-id="7f138-104">Bu izlenecek yol, bir <xref:System.Windows.Forms.MenuStrip> denetiminin standart bir menü oluşturmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7f138-104">This walkthrough demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a standard menu.</span></span> <span data-ttu-id="7f138-105">Form, bir Kullanıcı bir menü öğesi seçtiğinde da yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="7f138-105">The form also responds when a user selects a menu item.</span></span> <span data-ttu-id="7f138-106">Aşağıdaki görevler Bu izlenecek yolda gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7f138-106">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="7f138-107">Windows Forms projesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="7f138-107">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="7f138-108">Standart menü oluşturma.</span><span class="sxs-lookup"><span data-stu-id="7f138-108">Creating a standard menu.</span></span>

- <span data-ttu-id="7f138-109"><xref:System.Windows.Forms.StatusStrip> denetimi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="7f138-109">Creating a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

- <span data-ttu-id="7f138-110">Menü öğesi seçimini işleme.</span><span class="sxs-lookup"><span data-stu-id="7f138-110">Handling menu item selection.</span></span>

<span data-ttu-id="7f138-111">İşiniz bittiğinde, bir <xref:System.Windows.Forms.StatusStrip> denetimindeki menü öğesi seçimlerini görüntüleyen standart bir menü içeren bir formunuz olur.</span><span class="sxs-lookup"><span data-stu-id="7f138-111">When you are finished, you will have a form with a standard menu that displays menu item selections in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

<span data-ttu-id="7f138-112">Bu konudaki kodu tek bir liste olarak kopyalamak için bkz. [nasıl yapılır: bir forma standart menü öğeleri sağlama](how-to-provide-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="7f138-112">To copy the code in this topic as a single listing, see [How to: Provide Standard Menu Items to a Form](how-to-provide-standard-menu-items-to-a-form.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7f138-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="7f138-113">Prerequisites</span></span>

<span data-ttu-id="7f138-114">Bu izlenecek yolu tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f138-114">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="7f138-115">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="7f138-115">Create the project</span></span>

1. <span data-ttu-id="7f138-116">Visual Studio 'da, **StandardMenuForm** adlı bir Windows **uygulama projesi oluşturun** \*\* >  > \*\* \*\* > (\*\* **Visual C#**  veya **Visual Basic** > **Klasik Masaüstü** > Windows Forms **uygulaması**).</span><span class="sxs-lookup"><span data-stu-id="7f138-116">In Visual Studio, create a Windows application project called **StandardMenuForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="7f138-117">Windows Form Tasarımcısı, formunu seçin.</span><span class="sxs-lookup"><span data-stu-id="7f138-117">In the Windows Forms Designer, select the form.</span></span>

## <a name="create-a-standard-menu"></a><span data-ttu-id="7f138-118">Standart menü oluşturma</span><span class="sxs-lookup"><span data-stu-id="7f138-118">Create a standard menu</span></span>

<span data-ttu-id="7f138-119">Windows Form Tasarımcısı, standart menü öğeleriyle <xref:System.Windows.Forms.MenuStrip> denetimini otomatik olarak doldurabilir.</span><span class="sxs-lookup"><span data-stu-id="7f138-119">The Windows Forms Designer can automatically populate a <xref:System.Windows.Forms.MenuStrip> control with standard menu items.</span></span>

1. <span data-ttu-id="7f138-120">**Araç kutusundan**bir <xref:System.Windows.Forms.MenuStrip> denetimini formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="7f138-120">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto your form.</span></span>

2. <span data-ttu-id="7f138-121"><xref:System.Windows.Forms.MenuStrip> denetimin tasarımcı eylemleri simgesine (![küçük siyah ok](./media/designer-actions-glyph.gif)) tıklayın ve **standart öğeleri ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7f138-121">Click the <xref:System.Windows.Forms.MenuStrip> control's designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) and select **Insert Standard Items**.</span></span>

     <span data-ttu-id="7f138-122"><xref:System.Windows.Forms.MenuStrip> denetim standart menü öğeleriyle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="7f138-122">The <xref:System.Windows.Forms.MenuStrip> control is populated with the standard menu items.</span></span>

3. <span data-ttu-id="7f138-123">Varsayılan menü öğelerini ve bunlara karşılık gelen simgeleri görmek için **Dosya** menü öğesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7f138-123">Click the **File** menu item to see its default menu items and corresponding icons.</span></span>

## <a name="create-a-statusstrip-control"></a><span data-ttu-id="7f138-124">StatusStrip denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7f138-124">Create a StatusStrip control</span></span>

<span data-ttu-id="7f138-125">Windows Forms uygulamalarınızın durumunu göstermek için <xref:System.Windows.Forms.StatusStrip> denetimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7f138-125">Use the <xref:System.Windows.Forms.StatusStrip> control to display status for your Windows Forms applications.</span></span> <span data-ttu-id="7f138-126">Geçerli örnekte, Kullanıcı tarafından seçilen menü öğeleri <xref:System.Windows.Forms.StatusStrip> denetiminde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7f138-126">In the current example, menu items selected by the user are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

1. <span data-ttu-id="7f138-127">**Araç kutusundan**bir <xref:System.Windows.Forms.StatusStrip> denetimini formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="7f138-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.StatusStrip> control onto your form.</span></span>

     <span data-ttu-id="7f138-128"><xref:System.Windows.Forms.StatusStrip> denetimi otomatik olarak formun alt kısmına göre yapılır.</span><span class="sxs-lookup"><span data-stu-id="7f138-128">The <xref:System.Windows.Forms.StatusStrip> control automatically docks to the bottom of the form.</span></span>

2. <span data-ttu-id="7f138-129"><xref:System.Windows.Forms.StatusStrip> denetimine bir <xref:System.Windows.Forms.ToolStripStatusLabel> denetimi eklemek için <xref:System.Windows.Forms.StatusStrip> denetiminin açılan düğmesine tıklayın ve **Statuslabel** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="7f138-129">Click the <xref:System.Windows.Forms.StatusStrip> control's drop-down button and select **StatusLabel** to add a <xref:System.Windows.Forms.ToolStripStatusLabel> control to the <xref:System.Windows.Forms.StatusStrip> control.</span></span>

## <a name="handle-item-selection"></a><span data-ttu-id="7f138-130">Öğe seçimini işle</span><span class="sxs-lookup"><span data-stu-id="7f138-130">Handle item selection</span></span>

<span data-ttu-id="7f138-131">Kullanıcı bir menü öğesi seçtiğinde yanıt vermek için <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olayı işleyin.</span><span class="sxs-lookup"><span data-stu-id="7f138-131">Handle the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event to respond when the user selects a menu item.</span></span>

1. <span data-ttu-id="7f138-132">Standart menü oluşturma bölümünde oluşturduğunuz **Dosya** menü öğesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7f138-132">Click the **File** menu item that you created in the Creating a Standard Menu section.</span></span>

2. <span data-ttu-id="7f138-133">**Özellikler** penceresinde **Olaylar**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7f138-133">In the **Properties** window, click **Events**.</span></span>

3. <span data-ttu-id="7f138-134"><xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olayına çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7f138-134">Double-click the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

     <span data-ttu-id="7f138-135">Windows Form Tasarımcısı, <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olayı için bir olay işleyicisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7f138-135">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

4. <span data-ttu-id="7f138-136">Olay işleyicisine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7f138-136">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]

5. <span data-ttu-id="7f138-137">`UpdateStatus` yardımcı program yöntemi tanımını forma ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7f138-137">Insert the `UpdateStatus` utility method definition into the form.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]

## <a name="checkpoint--test-your-form"></a><span data-ttu-id="7f138-138">Kontrol noktası-formunuzu test etme</span><span class="sxs-lookup"><span data-stu-id="7f138-138">Checkpoint -test your form</span></span>

1. <span data-ttu-id="7f138-139">Formunuzu derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7f138-139">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="7f138-140">Menüyü açmak için **Dosya** menü öğesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7f138-140">Click the **File** menu item to open the menu.</span></span>

3. <span data-ttu-id="7f138-141">**Dosya** menüsünde, seçmek istediğiniz öğelerden birine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7f138-141">On the **File** menu, click one of the items to select it.</span></span>

     <span data-ttu-id="7f138-142"><xref:System.Windows.Forms.StatusStrip> Denetim seçili öğeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7f138-142">The <xref:System.Windows.Forms.StatusStrip> control displays the selected item.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7f138-143">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="7f138-143">Next steps</span></span>

<span data-ttu-id="7f138-144">Bu kılavuzda, standart bir menü içeren bir form oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="7f138-144">In this walkthrough, you have created a form with a standard menu.</span></span> <span data-ttu-id="7f138-145">Denetimlerin <xref:System.Windows.Forms.ToolStrip> ailesini birçok farklı amaçla kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7f138-145">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="7f138-146"><xref:System.Windows.Forms.ContextMenuStrip>denetimlerle ilgili kısayol menüleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7f138-146">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="7f138-147">Daha fazla bilgi için bkz. [ContextMenu bileşenine genel bakış](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7f138-147">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="7f138-148">Yerleştirme <xref:System.Windows.Forms.ToolStrip> denetimleri ile birden çok belge arabirimi (MDI) formu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7f138-148">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="7f138-149">Daha fazla bilgi için bkz. [Izlenecek yol: menü birleştirme ve ToolStrip denetimleriyle BIR MDI formu oluşturma](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="7f138-149">For more information, see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

- <span data-ttu-id="7f138-150"><xref:System.Windows.Forms.ToolStrip> denetimlerine profesyonel bir görünüm kazandırın.</span><span class="sxs-lookup"><span data-stu-id="7f138-150">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="7f138-151">Daha fazla bilgi için bkz. [nasıl yapılır: bir uygulama Için ToolStrip oluşturucuyu ayarlama](how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="7f138-151">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7f138-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f138-152">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="7f138-153">MenuStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="7f138-153">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
