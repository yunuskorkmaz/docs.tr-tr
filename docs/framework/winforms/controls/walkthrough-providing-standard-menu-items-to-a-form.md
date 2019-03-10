---
title: 'İzlenecek yol: Bir forma standart menü öğeleri sağlama'
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
ms.openlocfilehash: 846660fda37797e9d53d8f1d5a8a4f812d33e8df
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711765"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a><span data-ttu-id="cbc8c-102">İzlenecek yol: Bir forma standart menü öğeleri sağlama</span><span class="sxs-lookup"><span data-stu-id="cbc8c-102">Walkthrough: Providing Standard Menu Items to a Form</span></span>
<span data-ttu-id="cbc8c-103">Formlarınızla için standart bir menü sağlayabilir <xref:System.Windows.Forms.MenuStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="cbc8c-104">Bu izlenecek yolda nasıl kullanılacağını gösterir. bir <xref:System.Windows.Forms.MenuStrip> standart menü oluşturmak için denetimi.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-104">This walkthrough demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a standard menu.</span></span> <span data-ttu-id="cbc8c-105">Bir kullanıcı bir menü öğesi seçtiğinde, form ayrıca yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-105">The form also responds when a user selects a menu item.</span></span> <span data-ttu-id="cbc8c-106">Aşağıdaki görevler bu kılavuzda gösterilen:</span><span class="sxs-lookup"><span data-stu-id="cbc8c-106">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="cbc8c-107">Bir Windows Forms projesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-107">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="cbc8c-108">Standart menü oluşturma.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-108">Creating a standard menu.</span></span>  
  
-   <span data-ttu-id="cbc8c-109">Oluşturma bir <xref:System.Windows.Forms.StatusStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-109">Creating a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
-   <span data-ttu-id="cbc8c-110">Menü öğesi seçimi işleme.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-110">Handling menu item selection.</span></span>  
  
 <span data-ttu-id="cbc8c-111">İşlemi tamamladığınızda, menü öğesi seçimleri görüntüleyen bir standart menü formla olacaktır bir <xref:System.Windows.Forms.StatusStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-111">When you are finished, you will have a form with a standard menu that displays menu item selections in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
 <span data-ttu-id="cbc8c-112">Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: Bir forma standart menü öğeleri sağlama](how-to-provide-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="cbc8c-112">To copy the code in this topic as a single listing, see [How to: Provide Standard Menu Items to a Form](how-to-provide-standard-menu-items-to-a-form.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cbc8c-113">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-113">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="cbc8c-114">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-114">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="cbc8c-115">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="cbc8c-115">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cbc8c-116">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="cbc8c-116">Prerequisites</span></span>  
 <span data-ttu-id="cbc8c-117">Bu izlenecek yolu tamamlamak için şunlar gerekir:</span><span class="sxs-lookup"><span data-stu-id="cbc8c-117">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="cbc8c-118">Oluşturma ve Windows Forms application projesi Visual Studio'nun yüklü bilgisayarda çalıştırmak için yeterli izinleri yok.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-118">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="cbc8c-119">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cbc8c-119">Creating the Project</span></span>  
 <span data-ttu-id="cbc8c-120">İlk adım projeyi oluşturmak ve formu ayarlamaktır.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="cbc8c-121">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="cbc8c-121">To create the project</span></span>  
  
1.  <span data-ttu-id="cbc8c-122">Adlı bir Windows uygulaması projesi oluşturmak **StandardMenuForm** (**dosya** > **yeni** > **proje**  >  **Visual C#** veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms Uygulama**).</span><span class="sxs-lookup"><span data-stu-id="cbc8c-122">Create a Windows application project called **StandardMenuForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="cbc8c-123">Formu Windows Form Tasarımcısı'nda seçin.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-123">In the Windows Forms Designer, select the form.</span></span>  
  
## <a name="creating-a-standard-menu"></a><span data-ttu-id="cbc8c-124">Standart menü oluşturma</span><span class="sxs-lookup"><span data-stu-id="cbc8c-124">Creating a Standard Menu</span></span>  
 <span data-ttu-id="cbc8c-125">Windows Form Tasarımcısı otomatik olarak doldurabilirsiniz bir <xref:System.Windows.Forms.MenuStrip> standart menü öğeleri ile denetimi.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-125">The Windows Forms Designer can automatically populate a <xref:System.Windows.Forms.MenuStrip> control with standard menu items.</span></span>  
  
#### <a name="to-create-a-standard-menu"></a><span data-ttu-id="cbc8c-126">Standart menü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="cbc8c-126">To create a standard menu</span></span>  
  
1.  <span data-ttu-id="cbc8c-127">Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.MenuStrip> denetimi formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto your form.</span></span>  
  
2.  <span data-ttu-id="cbc8c-128">Tıklayın <xref:System.Windows.Forms.MenuStrip> denetimin akıllı etiket karakterini (![akıllı etiket karakterini](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) seçip **standart öğeleri Ekle**.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-128">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Insert Standard Items**.</span></span>  
  
     <span data-ttu-id="cbc8c-129"><xref:System.Windows.Forms.MenuStrip> Denetimi, standart menü öğeleri ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-129">The <xref:System.Windows.Forms.MenuStrip> control is populated with the standard menu items.</span></span>  
  
3.  <span data-ttu-id="cbc8c-130">Tıklayın **dosya** kendi varsayılan menü öğeleri ve ilişkili simgeleri görmek için menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-130">Click the **File** menu item to see its default menu items and corresponding icons.</span></span>  
  
## <a name="creating-a-statusstrip-control"></a><span data-ttu-id="cbc8c-131">StatusStrip denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="cbc8c-131">Creating a StatusStrip Control</span></span>  
 <span data-ttu-id="cbc8c-132">Kullanım <xref:System.Windows.Forms.StatusStrip> denetimi Windows Forms uygulamaları için durumu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-132">Use the <xref:System.Windows.Forms.StatusStrip> control to display status for your Windows Forms applications.</span></span> <span data-ttu-id="cbc8c-133">Menü öğeleri, kullanıcı tarafından seçilen görüntülenen geçerli örnekte, bir <xref:System.Windows.Forms.StatusStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-133">In the current example, menu items selected by the user are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
#### <a name="to-create-a-statusstrip-control"></a><span data-ttu-id="cbc8c-134">StatusStrip denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="cbc8c-134">To create a StatusStrip control</span></span>  
  
1.  <span data-ttu-id="cbc8c-135">Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.StatusStrip> denetimi formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-135">From the **Toolbox**, drag a <xref:System.Windows.Forms.StatusStrip> control onto your form.</span></span>  
  
     <span data-ttu-id="cbc8c-136"><xref:System.Windows.Forms.StatusStrip> Denetimi otomatik olarak noktaları formun altına.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-136">The <xref:System.Windows.Forms.StatusStrip> control automatically docks to the bottom of the form.</span></span>  
  
2.  <span data-ttu-id="cbc8c-137">Tıklayın <xref:System.Windows.Forms.StatusStrip> denetimin açılan düğmesine ve select **StatusLabel** eklemek için bir <xref:System.Windows.Forms.ToolStripStatusLabel> denetimini <xref:System.Windows.Forms.StatusStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-137">Click the <xref:System.Windows.Forms.StatusStrip> control's drop-down button and select **StatusLabel** to add a <xref:System.Windows.Forms.ToolStripStatusLabel> control to the <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
## <a name="handling-item-selection"></a><span data-ttu-id="cbc8c-138">İşleme öğe seçimi</span><span class="sxs-lookup"><span data-stu-id="cbc8c-138">Handling Item Selection</span></span>  
 <span data-ttu-id="cbc8c-139">Tanıtıcı <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olay kullanıcı menü öğesi seçtiğinde yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-139">Handle the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event to respond when the user selects a menu item.</span></span>  
  
#### <a name="to-handle-item-selection"></a><span data-ttu-id="cbc8c-140">Öğe seçimi işlemek için</span><span class="sxs-lookup"><span data-stu-id="cbc8c-140">To handle item selection</span></span>  
  
1.  <span data-ttu-id="cbc8c-141">Tıklayın **dosya** oluşturma içinde oluşturduğunuz bir menü öğesi bir standart menü bölümü.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-141">Click the **File** menu item that you created in the Creating a Standard Menu section.</span></span>  
  
2.  <span data-ttu-id="cbc8c-142">İçinde **özellikleri** penceresinde tıklayın **olayları**.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-142">In the **Properties** window, click **Events**.</span></span>  
  
3.  <span data-ttu-id="cbc8c-143">Çift <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olay.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-143">Double-click the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>  
  
     <span data-ttu-id="cbc8c-144">Windows Form Tasarımcısı için bir olay işleyicisi oluşturur <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olay.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-144">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>  
  
4.  <span data-ttu-id="cbc8c-145">Olay işleyicisine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-145">Insert the following code into the event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5.  <span data-ttu-id="cbc8c-146">INSERT `UpdateStatus` forma yardımcı yöntem tanımı.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-146">Insert the `UpdateStatus` utility method definition into the form.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## <a name="checkpoint"></a><span data-ttu-id="cbc8c-147">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="cbc8c-147">Checkpoint</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="cbc8c-148">Formunuza test etmek için</span><span class="sxs-lookup"><span data-stu-id="cbc8c-148">To test your form</span></span>  
  
1.  <span data-ttu-id="cbc8c-149">Derlemek ve formunuza çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-149">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="cbc8c-150">Tıklayın **dosya** menüsünü açmak için menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-150">Click the **File** menu item to open the menu.</span></span>  
  
3.  <span data-ttu-id="cbc8c-151">Üzerinde **dosya** menüsünde seçmek için öğelerden birine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-151">On the **File** menu, click one of the items to select it.</span></span>  
  
     <span data-ttu-id="cbc8c-152"><xref:System.Windows.Forms.StatusStrip> Denetim seçili öğeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-152">The <xref:System.Windows.Forms.StatusStrip> control displays the selected item.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="cbc8c-153">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="cbc8c-153">Next Steps</span></span>  
 <span data-ttu-id="cbc8c-154">Bu kılavuzda, bir form içeren bir standart menü oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-154">In this walkthrough, you have created a form with a standard menu.</span></span> <span data-ttu-id="cbc8c-155">Kullanabileceğiniz <xref:System.Windows.Forms.ToolStrip> birçok başka amaçlarla denetimlerin ailesi:</span><span class="sxs-lookup"><span data-stu-id="cbc8c-155">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="cbc8c-156">Sahip, denetimler için kısayol menüleri oluşturma <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-156">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="cbc8c-157">Daha fazla bilgi için [ContextMenu bileşenine genel bakış](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="cbc8c-157">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="cbc8c-158">Yerleştirme ile birden çok belge arabirimi (MDI) form oluşturma <xref:System.Windows.Forms.ToolStrip> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-158">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="cbc8c-159">Daha fazla bilgi için [izlenecek yol: Menü birleştirme ve ToolStrip denetimleri içeren MDI formu oluşturma](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="cbc8c-159">For more information, see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
-   <span data-ttu-id="cbc8c-160">Verin, <xref:System.Windows.Forms.ToolStrip> profesyonel bir görünümünü denetler.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-160">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="cbc8c-161">Daha fazla bilgi için [nasıl yapılır: Bir uygulama için ToolStrip oluşturucusunu ayarlama](how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="cbc8c-161">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbc8c-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbc8c-162">See also</span></span>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="cbc8c-163">MenuStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="cbc8c-163">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
