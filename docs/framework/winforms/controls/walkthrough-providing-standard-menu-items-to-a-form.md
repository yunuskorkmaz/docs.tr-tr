---
title: "İzlenecek yol: Bir Forma Standart Menü Öğeleri Sağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 89089617a62ab079dd4cccf3ddf6e1e774bac8ba
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a><span data-ttu-id="fe0d1-102">İzlenecek yol: Bir Forma Standart Menü Öğeleri Sağlama</span><span class="sxs-lookup"><span data-stu-id="fe0d1-102">Walkthrough: Providing Standard Menu Items to a Form</span></span>
<span data-ttu-id="fe0d1-103">Formlarınızı ile için standart menü sağlayabilirsiniz <xref:System.Windows.Forms.MenuStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="fe0d1-104">Bu kılavuzda nasıl kullanılacağını gösteren bir <xref:System.Windows.Forms.MenuStrip> standart menü oluşturmak için denetim.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-104">This walkthrough demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a standard menu.</span></span> <span data-ttu-id="fe0d1-105">Bir kullanıcı bir menü öğesi seçtiğinde formun ayrıca yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-105">The form also responds when a user selects a menu item.</span></span> <span data-ttu-id="fe0d1-106">Aşağıdaki görevler bu kılavuzda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="fe0d1-106">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="fe0d1-107">Windows Forms projesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-107">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="fe0d1-108">Standart menü oluşturma.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-108">Creating a standard menu.</span></span>  
  
-   <span data-ttu-id="fe0d1-109">Oluşturma bir <xref:System.Windows.Forms.StatusStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-109">Creating a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
-   <span data-ttu-id="fe0d1-110">Menü öğesi seçimi işleme.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-110">Handling menu item selection.</span></span>  
  
 <span data-ttu-id="fe0d1-111">İşiniz bittiğinde, menü öğesi seçimleri görüntüleyen bir standart menü ile bir biçimde olacaktır bir <xref:System.Windows.Forms.StatusStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-111">When you are finished, you will have a form with a standard menu that displays menu item selections in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
 <span data-ttu-id="fe0d1-112">Bu konuda tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: bir forma standart menü öğeleri sağlayan](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="fe0d1-112">To copy the code in this topic as a single listing, see [How to: Provide Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe0d1-113">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-113">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="fe0d1-114">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-114">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="fe0d1-115">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="fe0d1-115">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fe0d1-116">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="fe0d1-116">Prerequisites</span></span>  
 <span data-ttu-id="fe0d1-117">Bu kılavuzu tamamlamak için gerekir:</span><span class="sxs-lookup"><span data-stu-id="fe0d1-117">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="fe0d1-118">Oluşturma ve Windows Forms uygulaması projeleri bilgisayarda çalıştırmak için yeterli izinlere nerede [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yüklenir.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-118">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="fe0d1-119">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fe0d1-119">Creating the Project</span></span>  
 <span data-ttu-id="fe0d1-120">Projeyi oluşturmak ve formu ayarlamak için ilk adımdır bakın.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="fe0d1-121">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fe0d1-121">To create the project</span></span>  
  
1.  <span data-ttu-id="fe0d1-122">Adlı bir Windows uygulaması projesi oluşturduğunuzda **StandardMenuForm**.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-122">Create a Windows application project called **StandardMenuForm**.</span></span>  
  
     <span data-ttu-id="fe0d1-123">Daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="fe0d1-123">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="fe0d1-124">Windows Forms Tasarımcısı'nda formu seçin.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-124">In the Windows Forms Designer, select the form.</span></span>  
  
## <a name="creating-a-standard-menu"></a><span data-ttu-id="fe0d1-125">Standart menü oluşturma</span><span class="sxs-lookup"><span data-stu-id="fe0d1-125">Creating a Standard Menu</span></span>  
 <span data-ttu-id="fe0d1-126">Windows Form Tasarımcısı otomatik olarak doldurur bir <xref:System.Windows.Forms.MenuStrip> standart menü öğeleri denetimiyle.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-126">The Windows Forms Designer can automatically populate a <xref:System.Windows.Forms.MenuStrip> control with standard menu items.</span></span>  
  
#### <a name="to-create-a-standard-menu"></a><span data-ttu-id="fe0d1-127">Standart menü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fe0d1-127">To create a standard menu</span></span>  
  
1.  <span data-ttu-id="fe0d1-128">Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.MenuStrip> Formunuza denetim.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-128">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto your form.</span></span>  
  
2.  <span data-ttu-id="fe0d1-129">Tıklatın <xref:System.Windows.Forms.MenuStrip> denetimin akıllı etiket karakteri (![akıllı etiket karakteri](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) seçip **standart öğeleri Ekle**.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-129">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Insert Standard Items**.</span></span>  
  
     <span data-ttu-id="fe0d1-130"><xref:System.Windows.Forms.MenuStrip> Denetim standart menü öğeleri ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-130">The <xref:System.Windows.Forms.MenuStrip> control is populated with the standard menu items.</span></span>  
  
3.  <span data-ttu-id="fe0d1-131">Tıklatın **dosya** varsayılan menü öğeleri ve ilişkili simgeleri görmek için menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-131">Click the **File** menu item to see its default menu items and corresponding icons.</span></span>  
  
## <a name="creating-a-statusstrip-control"></a><span data-ttu-id="fe0d1-132">StatusStrip denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="fe0d1-132">Creating a StatusStrip Control</span></span>  
 <span data-ttu-id="fe0d1-133">Kullanım <xref:System.Windows.Forms.StatusStrip> Windows Forms uygulamalarının durumunu görüntülemek için denetimi.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-133">Use the <xref:System.Windows.Forms.StatusStrip> control to display status for your Windows Forms applications.</span></span> <span data-ttu-id="fe0d1-134">Menü öğeleri kullanıcı tarafından seçilen görüntülenen geçerli örnekte bir <xref:System.Windows.Forms.StatusStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-134">In the current example, menu items selected by the user are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
#### <a name="to-create-a-statusstrip-control"></a><span data-ttu-id="fe0d1-135">StatusStrip denetimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fe0d1-135">To create a StatusStrip control</span></span>  
  
1.  <span data-ttu-id="fe0d1-136">Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.StatusStrip> Formunuza denetim.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-136">From the **Toolbox**, drag a <xref:System.Windows.Forms.StatusStrip> control onto your form.</span></span>  
  
     <span data-ttu-id="fe0d1-137"><xref:System.Windows.Forms.StatusStrip> Denetimi otomatik olarak noktalarını formun altına.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-137">The <xref:System.Windows.Forms.StatusStrip> control automatically docks to the bottom of the form.</span></span>  
  
2.  <span data-ttu-id="fe0d1-138">Tıklatın <xref:System.Windows.Forms.StatusStrip> denetimin açılan düğmesine ve select **StatusLabel'i** eklemek için bir <xref:System.Windows.Forms.ToolStripStatusLabel> denetimini <xref:System.Windows.Forms.StatusStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-138">Click the <xref:System.Windows.Forms.StatusStrip> control's drop-down button and select **StatusLabel** to add a <xref:System.Windows.Forms.ToolStripStatusLabel> control to the <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
## <a name="handling-item-selection"></a><span data-ttu-id="fe0d1-139">İşleme öğe seçimi</span><span class="sxs-lookup"><span data-stu-id="fe0d1-139">Handling Item Selection</span></span>  
 <span data-ttu-id="fe0d1-140">Tanıtıcı <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> kullanıcı menü öğesi seçtiğinde yanıt olay.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-140">Handle the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event to respond when the user selects a menu item.</span></span>  
  
#### <a name="to-handle-item-selection"></a><span data-ttu-id="fe0d1-141">Öğe seçimi işlemek için</span><span class="sxs-lookup"><span data-stu-id="fe0d1-141">To handle item selection</span></span>  
  
1.  <span data-ttu-id="fe0d1-142">Tıklatın **dosya** oluşturma oluşturulan menü öğesi bir standart menü bölümü.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-142">Click the **File** menu item that you created in the Creating a Standard Menu section.</span></span>  
  
2.  <span data-ttu-id="fe0d1-143">İçinde **özellikleri** penceresinde tıklatın **olayları**.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-143">In the **Properties** window, click **Events**.</span></span>  
  
3.  <span data-ttu-id="fe0d1-144">Çift <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olay.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-144">Double-click the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>  
  
     <span data-ttu-id="fe0d1-145">Windows Form Tasarımcısı için bir olay işleyicisi oluşturur <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olay.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-145">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>  
  
4.  <span data-ttu-id="fe0d1-146">Olay işleyicisi aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-146">Insert the following code into the event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5.  <span data-ttu-id="fe0d1-147">INSERT `UpdateStatus` forma yardımcı yöntem tanımı.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-147">Insert the `UpdateStatus` utility method definition into the form.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## <a name="checkpoint"></a><span data-ttu-id="fe0d1-148">Denetim noktası</span><span class="sxs-lookup"><span data-stu-id="fe0d1-148">Checkpoint</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="fe0d1-149">Formunuz sınamak için</span><span class="sxs-lookup"><span data-stu-id="fe0d1-149">To test your form</span></span>  
  
1.  <span data-ttu-id="fe0d1-150">Derleme ve formunuza çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-150">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="fe0d1-151">Tıklatın **dosya** menüsünü açmak için menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-151">Click the **File** menu item to open the menu.</span></span>  
  
3.  <span data-ttu-id="fe0d1-152">Üzerinde **dosya** menüsünde seçmek için öğelerden birini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-152">On the **File** menu, click one of the items to select it.</span></span>  
  
     <span data-ttu-id="fe0d1-153"><xref:System.Windows.Forms.StatusStrip> Denetimi, seçilen öğeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-153">The <xref:System.Windows.Forms.StatusStrip> control displays the selected item.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="fe0d1-154">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="fe0d1-154">Next Steps</span></span>  
 <span data-ttu-id="fe0d1-155">Bu kılavuzda, bir forma standart menü ile oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-155">In this walkthrough, you have created a form with a standard menu.</span></span> <span data-ttu-id="fe0d1-156">Kullanabileceğiniz <xref:System.Windows.Forms.ToolStrip> birçok başka amaçlarla denetimlerin ailesi:</span><span class="sxs-lookup"><span data-stu-id="fe0d1-156">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="fe0d1-157">İle denetimleri için kısayol menüleri oluşturma <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-157">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="fe0d1-158">Daha fazla bilgi için bkz: [ContextMenu bileşenine genel bakış](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="fe0d1-158">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="fe0d1-159">Yerleştirme ile birden çok belge arabirimi (MDI) form oluşturma <xref:System.Windows.Forms.ToolStrip> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-159">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="fe0d1-160">Daha fazla bilgi için bkz: [izlenecek yol: menü birleştirme ve ToolStrip denetimleri içeren MDI formu oluşturma](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="fe0d1-160">For more information, see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
-   <span data-ttu-id="fe0d1-161">Verin, <xref:System.Windows.Forms.ToolStrip> profesyonel görünüm denetler.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-161">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="fe0d1-162">Daha fazla bilgi için bkz: [nasıl yapılır: bir uygulama için ToolStrip oluşturucusunu ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="fe0d1-162">For more information, see [How to: Set the ToolStrip Renderer for an Application](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe0d1-163">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe0d1-163">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="fe0d1-164">MenuStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="fe0d1-164">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
