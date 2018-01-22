---
title: "İzlenecek yol: Menü Birleştirme ve ToolStrip Denetimleri ile bir MDI Formu Oluşturma"
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
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3e0538151c19eb47f8a51330b7f2c06818d1e73f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="5f9db-102">İzlenecek yol: Menü Birleştirme ve ToolStrip Denetimleri ile bir MDI Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5f9db-102">Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls</span></span>
<span data-ttu-id="5f9db-103"><xref:System.Windows.Forms?displayProperty=nameWithType> Ad alanı birden çok belge arabirimi (MDI) uygulamaları destekler ve <xref:System.Windows.Forms.MenuStrip> denetimi, menü birleştirme destekler.</span><span class="sxs-lookup"><span data-stu-id="5f9db-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="5f9db-104">MDI formları için de <xref:System.Windows.Forms.ToolStrip> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="5f9db-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="5f9db-105">Bu kılavuzda nasıl kullanılacağı ortaya <xref:System.Windows.Forms.ToolStripPanel> denetimleriyle MDI formu.</span><span class="sxs-lookup"><span data-stu-id="5f9db-105">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="5f9db-106">Formun alt menüler ile birleştirme menü de destekler.</span><span class="sxs-lookup"><span data-stu-id="5f9db-106">The form also supports menu merging with child menus.</span></span> <span data-ttu-id="5f9db-107">Aşağıdaki görevler bu kılavuzda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5f9db-107">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="5f9db-108">Windows Forms projesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="5f9db-108">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="5f9db-109">Formunuz için ana menü oluşturma.</span><span class="sxs-lookup"><span data-stu-id="5f9db-109">Creating the main menu for your form.</span></span> <span data-ttu-id="5f9db-110">Menü gerçek adını değişir.</span><span class="sxs-lookup"><span data-stu-id="5f9db-110">The actual name of the menu will vary.</span></span>  
  
-   <span data-ttu-id="5f9db-111">Ekleme <xref:System.Windows.Forms.ToolStripPanel> denetimini **araç**.</span><span class="sxs-lookup"><span data-stu-id="5f9db-111">Adding the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox**.</span></span>  
  
-   <span data-ttu-id="5f9db-112">Alt form oluşturma.</span><span class="sxs-lookup"><span data-stu-id="5f9db-112">Creating a child form.</span></span>  
  
-   <span data-ttu-id="5f9db-113">Düzenleme <xref:System.Windows.Forms.ToolStripPanel> denetimlerinin z düzeni.</span><span class="sxs-lookup"><span data-stu-id="5f9db-113">Arranging <xref:System.Windows.Forms.ToolStripPanel> controls by z-order.</span></span>  
  
 <span data-ttu-id="5f9db-114">İşiniz bittiğinde, menü birleştirme ve taşınabilir destekleyen MDI Formu olacaktır <xref:System.Windows.Forms.ToolStrip> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="5f9db-114">When you are finished, you will have an MDI form that supports menu merging and movable <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="5f9db-115">Bu konuda tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: menü birleştirme ve ToolStrip denetimleri içeren MDI formu oluşturma](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="5f9db-115">To copy the code in this topic as a single listing, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f9db-116">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="5f9db-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="5f9db-117">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="5f9db-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="5f9db-118">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="5f9db-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5f9db-119">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="5f9db-119">Prerequisites</span></span>  
 <span data-ttu-id="5f9db-120">Bu kılavuzu tamamlamak için gerekir:</span><span class="sxs-lookup"><span data-stu-id="5f9db-120">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="5f9db-121">Oluşturma ve Windows Forms uygulaması projeleri bilgisayarda çalıştırmak için yeterli izinlere nerede [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yüklenir.</span><span class="sxs-lookup"><span data-stu-id="5f9db-121">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="5f9db-122">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5f9db-122">Creating the Project</span></span>  
 <span data-ttu-id="5f9db-123">Projeyi oluşturmak ve formu ayarlamak için ilk adımdır bakın.</span><span class="sxs-lookup"><span data-stu-id="5f9db-123">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="5f9db-124">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5f9db-124">To create the project</span></span>  
  
1.  <span data-ttu-id="5f9db-125">Adlı bir Windows uygulaması projesi oluşturduğunuzda **MdiForm**.</span><span class="sxs-lookup"><span data-stu-id="5f9db-125">Create a Windows Application project called **MdiForm**.</span></span>  
  
     <span data-ttu-id="5f9db-126">Daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="5f9db-126">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="5f9db-127">Windows Forms Tasarımcısı'nda formu seçin.</span><span class="sxs-lookup"><span data-stu-id="5f9db-127">In the Windows Forms Designer, select the form.</span></span>  
  
3.  <span data-ttu-id="5f9db-128">Özellikler penceresinde değerini <xref:System.Windows.Forms.Form.IsMdiContainer%2A> için `true`.</span><span class="sxs-lookup"><span data-stu-id="5f9db-128">In the Properties window, set the value of the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> to `true`.</span></span>  
  
## <a name="creating-the-main-menu"></a><span data-ttu-id="5f9db-129">Ana menü oluşturma</span><span class="sxs-lookup"><span data-stu-id="5f9db-129">Creating the Main Menu</span></span>  
 <span data-ttu-id="5f9db-130">MDI Formu üst ana menü içerir.</span><span class="sxs-lookup"><span data-stu-id="5f9db-130">The parent MDI form contains the main menu.</span></span> <span data-ttu-id="5f9db-131">Ana menü öğesi adlı bir menü sahip **penceresi**.</span><span class="sxs-lookup"><span data-stu-id="5f9db-131">The main menu has one menu item named **Window**.</span></span> <span data-ttu-id="5f9db-132">İle **penceresi** menü öğesi, alt formları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f9db-132">With the **Window** menu item, you can create child forms.</span></span> <span data-ttu-id="5f9db-133">Alt formlar menü öğelerinden ana menüye birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5f9db-133">Menu items from child forms are merged into the main menu.</span></span>  
  
#### <a name="to-create-the-main-menu"></a><span data-ttu-id="5f9db-134">Ana menü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5f9db-134">To create the Main menu</span></span>  
  
1.  <span data-ttu-id="5f9db-135">Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.MenuStrip> forma denetim.</span><span class="sxs-lookup"><span data-stu-id="5f9db-135">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the form.</span></span>  
  
2.  <span data-ttu-id="5f9db-136">Ekleme bir <xref:System.Windows.Forms.ToolStripMenuItem> için <xref:System.Windows.Forms.MenuStrip> denetlemek ve adlandırın **penceresi**.</span><span class="sxs-lookup"><span data-stu-id="5f9db-136">Add a <xref:System.Windows.Forms.ToolStripMenuItem> to the <xref:System.Windows.Forms.MenuStrip> control and name it **Window**.</span></span>  
  
3.  <span data-ttu-id="5f9db-137">Seçin <xref:System.Windows.Forms.MenuStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="5f9db-137">Select the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
4.  <span data-ttu-id="5f9db-138">Özellikler penceresinde değerini <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliğine `ToolStripMenuItem1`.</span><span class="sxs-lookup"><span data-stu-id="5f9db-138">In the Properties window, set the value of the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to `ToolStripMenuItem1`.</span></span>  
  
5.  <span data-ttu-id="5f9db-139">Bir alt eklemek **penceresi** menü öğesini ve ardından ad alt **yeni**.</span><span class="sxs-lookup"><span data-stu-id="5f9db-139">Add a subitem to the **Window** menu item, and then name the subitem **New**.</span></span>  
  
6.  <span data-ttu-id="5f9db-140">Özellikler penceresinde **olayları**.</span><span class="sxs-lookup"><span data-stu-id="5f9db-140">In the Properties window, click **Events**.</span></span>  
  
7.  <span data-ttu-id="5f9db-141">Çift <xref:System.Windows.Forms.ToolStripItem.Click> olay.</span><span class="sxs-lookup"><span data-stu-id="5f9db-141">Double-click the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>  
  
     <span data-ttu-id="5f9db-142">Windows Form Tasarımcısı için bir olay işleyicisi oluşturur <xref:System.Windows.Forms.ToolStripItem.Click> olay.</span><span class="sxs-lookup"><span data-stu-id="5f9db-142">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>  
  
8.  <span data-ttu-id="5f9db-143">Olay işleyicisi aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5f9db-143">Insert the following code into the event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="5f9db-144">ToolStripPanel denetimi araç kutusuna ekleme</span><span class="sxs-lookup"><span data-stu-id="5f9db-144">Adding the ToolStripPanel Control to the Toolbox</span></span>  
 <span data-ttu-id="5f9db-145">Kullandığınızda <xref:System.Windows.Forms.MenuStrip> olmalıdır MDI Formu denetimleriyle <xref:System.Windows.Forms.ToolStripPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="5f9db-145">When you use <xref:System.Windows.Forms.MenuStrip> controls with an MDI form you must have the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="5f9db-146">Eklemelisiniz <xref:System.Windows.Forms.ToolStripPanel> denetimini **araç** Windows Forms Tasarımcısı'nda, MDI formu oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="5f9db-146">You must add the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox** to build your MDI form in the Windows Forms Designer.</span></span>  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="5f9db-147">ToolStripPanel denetimi araç kutusuna ekleme</span><span class="sxs-lookup"><span data-stu-id="5f9db-147">To add the ToolStripPanel control to the Toolbox</span></span>  
  
1.  <span data-ttu-id="5f9db-148">Açık **araç**ve ardından **tüm Windows Formları** kullanılabilir Windows Forms denetimleri göstermek için sekmesi.</span><span class="sxs-lookup"><span data-stu-id="5f9db-148">Open the **Toolbox**, and then click the **All Windows Forms** tab to show the available Windows Forms controls.</span></span>  
  
2.  <span data-ttu-id="5f9db-149">Kısayol menüsünü açmak için sağ tıklatın ve seçin **öğeleri Seç**.</span><span class="sxs-lookup"><span data-stu-id="5f9db-149">Right-click to open the shortcut menu, and select **Choose Items**.</span></span>  
  
3.  <span data-ttu-id="5f9db-150">İçinde **araç kutusu öğelerini Seç** iletişim kutusu, aşağı **adı** bulana kadar sütun **ToolStripPanel**.</span><span class="sxs-lookup"><span data-stu-id="5f9db-150">In the **Choose Toolbox Items** dialog box, scroll down the **Name** column until you find **ToolStripPanel**.</span></span>  
  
4.  <span data-ttu-id="5f9db-151">Onay kutusunu seçin **ToolStripPanel**ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="5f9db-151">Select the check box by **ToolStripPanel**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="5f9db-152"><xref:System.Windows.Forms.ToolStripPanel> Denetimi görünür **araç**.</span><span class="sxs-lookup"><span data-stu-id="5f9db-152">The <xref:System.Windows.Forms.ToolStripPanel> control appears in the **Toolbox**.</span></span>  
  
## <a name="creating-a-child-form"></a><span data-ttu-id="5f9db-153">Alt Form oluşturma</span><span class="sxs-lookup"><span data-stu-id="5f9db-153">Creating a Child Form</span></span>  
 <span data-ttu-id="5f9db-154">Bu yordamda, kendi ayrı alt form sınıfı tanımlayacaksınız <xref:System.Windows.Forms.MenuStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="5f9db-154">In this procedure, you will define a separate child form class that has its own <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="5f9db-155">Bu form için menü öğeleri üst formu olanlar birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5f9db-155">The menu items for this form are merged with those of the parent form.</span></span>  
  
#### <a name="to-define-a-child-form"></a><span data-ttu-id="5f9db-156">Bir alt form tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="5f9db-156">To define a child form</span></span>  
  
1.  <span data-ttu-id="5f9db-157">Adlı yeni bir form ekleme `ChildForm` projeye.</span><span class="sxs-lookup"><span data-stu-id="5f9db-157">Add a new form named `ChildForm` to the project.</span></span>  
  
     <span data-ttu-id="5f9db-158">Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms projeye eklemek](http://msdn.microsoft.com/library/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span><span class="sxs-lookup"><span data-stu-id="5f9db-158">For more information, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/library/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
2.  <span data-ttu-id="5f9db-159">Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.MenuStrip> alt forma denetim.</span><span class="sxs-lookup"><span data-stu-id="5f9db-159">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the child form.</span></span>  
  
3.  <span data-ttu-id="5f9db-160">Tıklatın <xref:System.Windows.Forms.MenuStrip> denetimin akıllı etiket karakteri (![akıllı etiket karakteri](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) ve ardından **öğe düzenleme**.</span><span class="sxs-lookup"><span data-stu-id="5f9db-160">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), and then select **Edit Items**.</span></span>  
  
4.  <span data-ttu-id="5f9db-161">İçinde **öğeleri koleksiyonu Düzenleyicisi** iletişim kutusunda, yeni bir ekleme <xref:System.Windows.Forms.ToolStripMenuItem> adlı **ChildMenuItem** alt menüsüne.</span><span class="sxs-lookup"><span data-stu-id="5f9db-161">In the **Items Collection Editor** dialog box, add a new <xref:System.Windows.Forms.ToolStripMenuItem> named **ChildMenuItem** to the child menu.</span></span>  
  
     <span data-ttu-id="5f9db-162">Daha fazla bilgi için bkz: [ToolStrip öğeleri koleksiyonu Düzenleyicisi](http://msdn.microsoft.com/library/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).</span><span class="sxs-lookup"><span data-stu-id="5f9db-162">For more information, see [ToolStrip Items Collection Editor](http://msdn.microsoft.com/library/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).</span></span>  
  
## <a name="testing-the-form"></a><span data-ttu-id="5f9db-163">Formun test etme</span><span class="sxs-lookup"><span data-stu-id="5f9db-163">Testing the Form</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="5f9db-164">Formunuz sınamak için</span><span class="sxs-lookup"><span data-stu-id="5f9db-164">To test your form</span></span>  
  
1.  <span data-ttu-id="5f9db-165">Derleme ve formunuza çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5f9db-165">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="5f9db-166">Tıklatın **penceresi** menüsünü açın ve ardından menü öğesi **yeni**.</span><span class="sxs-lookup"><span data-stu-id="5f9db-166">Click the **Window** menu item to open the menu, and then click **New**.</span></span>  
  
     <span data-ttu-id="5f9db-167">Yeni bir alt form formun MDI istemci alanında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5f9db-167">A new child form is created in the form's MDI client area.</span></span> <span data-ttu-id="5f9db-168">Alt formun menüsünde ana menü ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5f9db-168">The child form's menu is merged with the main menu.</span></span>  
  
3.  <span data-ttu-id="5f9db-169">Alt formu kapatın.</span><span class="sxs-lookup"><span data-stu-id="5f9db-169">Close the child form.</span></span>  
  
     <span data-ttu-id="5f9db-170">Alt formun menüsünde ana menüden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="5f9db-170">The child form's menu is removed from the main menu.</span></span>  
  
4.  <span data-ttu-id="5f9db-171">Tıklatın **yeni** birkaç kez.</span><span class="sxs-lookup"><span data-stu-id="5f9db-171">Click **New** several times.</span></span>  
  
     <span data-ttu-id="5f9db-172">Alt formları otomatik olarak W altında listelenen**penceresi** menü öğesi için <xref:System.Windows.Forms.MenuStrip> denetimin <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliğine atanır.</span><span class="sxs-lookup"><span data-stu-id="5f9db-172">The child forms are automatically listed under the W**indow** menu item because the <xref:System.Windows.Forms.MenuStrip> control's <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property is assigned.</span></span>  
  
## <a name="adding-toolstrip-support"></a><span data-ttu-id="5f9db-173">ToolStrip desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="5f9db-173">Adding ToolStrip Support</span></span>  
 <span data-ttu-id="5f9db-174">Bu yordamda, dört ekleyeceksiniz <xref:System.Windows.Forms.ToolStrip> MDI üst formu denetimleri.</span><span class="sxs-lookup"><span data-stu-id="5f9db-174">In this procedure, you will add four <xref:System.Windows.Forms.ToolStrip> controls to the MDI parent form.</span></span> <span data-ttu-id="5f9db-175">Her <xref:System.Windows.Forms.ToolStrip> denetimi içinde eklenir bir <xref:System.Windows.Forms.ToolStripPanel> formun kenarına yerleşik denetim.</span><span class="sxs-lookup"><span data-stu-id="5f9db-175">Each <xref:System.Windows.Forms.ToolStrip> control is added inside a <xref:System.Windows.Forms.ToolStripPanel> control, which is docked to the edge of the form.</span></span>  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a><span data-ttu-id="5f9db-176">MDI üst forma ToolStrip denetimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="5f9db-176">To add ToolStrip controls to the MDI parent form</span></span>  
  
1.  <span data-ttu-id="5f9db-177">Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.ToolStripPanel> forma denetim.</span><span class="sxs-lookup"><span data-stu-id="5f9db-177">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStripPanel> control onto the form.</span></span>  
  
2.  <span data-ttu-id="5f9db-178">İle <xref:System.Windows.Forms.ToolStripPanel> denetim seçilen, çift <xref:System.Windows.Forms.ToolStrip> denetim **araç**.</span><span class="sxs-lookup"><span data-stu-id="5f9db-178">With the <xref:System.Windows.Forms.ToolStripPanel> control selected, double-click the <xref:System.Windows.Forms.ToolStrip> control in the **Toolbox**.</span></span>  
  
     <span data-ttu-id="5f9db-179">A <xref:System.Windows.Forms.ToolStrip> denetim oluşturulur <xref:System.Windows.Forms.ToolStripPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="5f9db-179">A <xref:System.Windows.Forms.ToolStrip> control is created in the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
3.  <span data-ttu-id="5f9db-180">Seçin <xref:System.Windows.Forms.ToolStripPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="5f9db-180">Select the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
4.  <span data-ttu-id="5f9db-181">Özellikler penceresinde denetimin değerini değiştirmek <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="5f9db-181">In the Properties window, change the value of the control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span>  
  
     <span data-ttu-id="5f9db-182"><xref:System.Windows.Forms.ToolStripPanel> Kontrol noktalarını formun ana menüye altına sol tarafına.</span><span class="sxs-lookup"><span data-stu-id="5f9db-182">The <xref:System.Windows.Forms.ToolStripPanel> control docks to the left side of the form, underneath the main menu.</span></span> <span data-ttu-id="5f9db-183">MDI istemci alanını uyacak şekilde yeniden boyutlandırır <xref:System.Windows.Forms.ToolStripPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="5f9db-183">The MDI client area resizes to fit the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
5.  <span data-ttu-id="5f9db-184">1 ile 4 arasındaki adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="5f9db-184">Repeat steps 1 through 4.</span></span>  
  
     <span data-ttu-id="5f9db-185">Yeni yerleştirme <xref:System.Windows.Forms.ToolStripPanel> formun üstünde denetimine.</span><span class="sxs-lookup"><span data-stu-id="5f9db-185">Dock the new <xref:System.Windows.Forms.ToolStripPanel> control to the top of the form.</span></span>  
  
     <span data-ttu-id="5f9db-186"><xref:System.Windows.Forms.ToolStripPanel> Denetim ana menü altında ancak ilk sağındaki yerleştirilmiştir <xref:System.Windows.Forms.ToolStripPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="5f9db-186">The <xref:System.Windows.Forms.ToolStripPanel> control is docked underneath the main menu, but to the right of the first <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="5f9db-187">Bu adım doğru konumlandırmada z-sırası önemini gösterir <xref:System.Windows.Forms.ToolStripPanel> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="5f9db-187">This step illustrates the importance of z-order in correctly positioning <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
6.  <span data-ttu-id="5f9db-188">Daha fazla iki için 1-4 arasındaki adımları yineleyin <xref:System.Windows.Forms.ToolStripPanel> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="5f9db-188">Repeat steps 1 through 4 for two more <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
     <span data-ttu-id="5f9db-189">Yeni yerleştirme <xref:System.Windows.Forms.ToolStripPanel> formun alt ve sağ denetimleri.</span><span class="sxs-lookup"><span data-stu-id="5f9db-189">Dock the new <xref:System.Windows.Forms.ToolStripPanel> controls to the right and bottom of the form.</span></span>  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="5f9db-190">Z düzeni tarafından ToolStripPanel denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="5f9db-190">Arranging ToolStripPanel Controls by Z-order</span></span>  
 <span data-ttu-id="5f9db-191">Bir yerleşik konumunu <xref:System.Windows.Forms.ToolStripPanel> MDI formu denetimi z düzenini denetimin konumu tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="5f9db-191">The position of a docked <xref:System.Windows.Forms.ToolStripPanel> control on your MDI form is determined by the control's position in the z-order.</span></span> <span data-ttu-id="5f9db-192">Belge Anahattı penceresi, denetimlerinde z sıralamasını kolayca düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f9db-192">You can easily arrange the z-order of your controls in the Document Outline window.</span></span>  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="5f9db-193">Z düzeni tarafından ToolStripPanel denetimlerini düzenlemek için</span><span class="sxs-lookup"><span data-stu-id="5f9db-193">To arrange ToolStripPanel controls by Z-order</span></span>  
  
1.  <span data-ttu-id="5f9db-194">İçinde **Görünüm** menüsünde tıklatın **diğer pencereler**ve ardından **belge anahattı**.</span><span class="sxs-lookup"><span data-stu-id="5f9db-194">In the **View** menu, click **Other Windows**, and then click **Document Outline**.</span></span>  
  
     <span data-ttu-id="5f9db-195">Düzenlenmesi, <xref:System.Windows.Forms.ToolStripPanel> denetimleri önceki yordamın standart olmayan.</span><span class="sxs-lookup"><span data-stu-id="5f9db-195">The arrangement of your <xref:System.Windows.Forms.ToolStripPanel> controls from the previous procedure is nonstandard.</span></span> <span data-ttu-id="5f9db-196">Z düzeni doğru olmadığından budur.</span><span class="sxs-lookup"><span data-stu-id="5f9db-196">This is because the z-order is not correct.</span></span> <span data-ttu-id="5f9db-197">Belge Anahattı penceresi denetimlerinin z sıralamasını değiştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="5f9db-197">Use the Document Outline window to change the z-order of the controls.</span></span>  
  
2.  <span data-ttu-id="5f9db-198">Belge Anahattı penceresi seçin **ToolStripPanel4**.</span><span class="sxs-lookup"><span data-stu-id="5f9db-198">In the Document Outline window, select **ToolStripPanel4**.</span></span>  
  
3.  <span data-ttu-id="5f9db-199">Aşağı ok düğmesine tıklayın kadar sürekli, **ToolStripPanel4** listenin alt kısmında vardır.</span><span class="sxs-lookup"><span data-stu-id="5f9db-199">Click the down-arrow button repeatedly, until **ToolStripPanel4** is at the bottom of the list.</span></span>  
  
     <span data-ttu-id="5f9db-200">**ToolStripPanel4** denetim, formun diğer denetimleri altına altına yerleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5f9db-200">The **ToolStripPanel4** control is docked to the bottom of the form, underneath the other controls.</span></span>  
  
4.  <span data-ttu-id="5f9db-201">Seçin **ToolStripPanel2**.</span><span class="sxs-lookup"><span data-stu-id="5f9db-201">Select **ToolStripPanel2**.</span></span>  
  
5.  <span data-ttu-id="5f9db-202">Aşağı ok düğmesine denetimi üçüncü listede konumlandırmak için bir kez tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5f9db-202">Click the down-arrow button one time to position the control third in the list.</span></span>  
  
     <span data-ttu-id="5f9db-203">**ToolStripPanel2** denetim ana menü altında ve diğer denetimlerin yukarıdaki form üstüne yerleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5f9db-203">The **ToolStripPanel2** control is docked to the top of the form, underneath the main menu and above the other controls.</span></span>  
  
6.  <span data-ttu-id="5f9db-204">İçindeki çeşitli denetimlerin seçin **belge anahattı** penceresi ve bunları z sırayla farklı konumlara taşıyın.</span><span class="sxs-lookup"><span data-stu-id="5f9db-204">Select various controls in the **Document Outline** window and move them to different positions in the z-order.</span></span> <span data-ttu-id="5f9db-205">Yerleşik denetimleri yerleştirme z düzenini etkisi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5f9db-205">Note the effect of the z-order on the placement of docked controls.</span></span> <span data-ttu-id="5f9db-206">CTRL-Z kullanın veya **geri** üzerinde **Düzenle** yaptığınız değişiklikleri geri almak için menüsü.</span><span class="sxs-lookup"><span data-stu-id="5f9db-206">Use CTRL-Z or **Undo** on the **Edit** menu to undo your changes.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="5f9db-207">Denetim noktası</span><span class="sxs-lookup"><span data-stu-id="5f9db-207">Checkpoint</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="5f9db-208">Formunuz sınamak için</span><span class="sxs-lookup"><span data-stu-id="5f9db-208">To test your form</span></span>  
  
1.  <span data-ttu-id="5f9db-209">Derleme ve formunuza çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5f9db-209">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="5f9db-210">Tutamacı birini tıklatın bir <xref:System.Windows.Forms.ToolStrip> denetlemek ve denetimi form üzerinde farklı konumlara sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="5f9db-210">Click the grip of a <xref:System.Windows.Forms.ToolStrip> control and drag the control to different positions on the form.</span></span>  
  
     <span data-ttu-id="5f9db-211">Sürükleyebilirsiniz bir <xref:System.Windows.Forms.ToolStrip> birinden denetim <xref:System.Windows.Forms.ToolStripPanel> başka bir denetim.</span><span class="sxs-lookup"><span data-stu-id="5f9db-211">You can drag a <xref:System.Windows.Forms.ToolStrip> control from one <xref:System.Windows.Forms.ToolStripPanel> control to another.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5f9db-212">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="5f9db-212">Next Steps</span></span>  
 <span data-ttu-id="5f9db-213">Bu kılavuzda, MDI üst formu ile oluşturduğunuz <xref:System.Windows.Forms.ToolStrip> denetimleri ve menü birleştirme.</span><span class="sxs-lookup"><span data-stu-id="5f9db-213">In this walkthrough, you have created an MDI parent form with <xref:System.Windows.Forms.ToolStrip> controls and menu merging.</span></span> <span data-ttu-id="5f9db-214">Kullanabileceğiniz <xref:System.Windows.Forms.ToolStrip> birçok başka amaçlarla denetimlerin ailesi:</span><span class="sxs-lookup"><span data-stu-id="5f9db-214">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="5f9db-215">İle denetimleri için kısayol menüleri oluşturma <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="5f9db-215">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="5f9db-216">Daha fazla bilgi için bkz: [ContextMenu bileşenine genel bakış](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5f9db-216">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="5f9db-217">Bir form otomatik olarak doldurulan bir standart menüsüyle oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5f9db-217">Created a form with an automatically populated standard menu.</span></span> <span data-ttu-id="5f9db-218">Daha fazla bilgi için bkz: [izlenecek yol: bir forma standart menü öğeleri sağlama](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="5f9db-218">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
-   <span data-ttu-id="5f9db-219">Verin, <xref:System.Windows.Forms.ToolStrip> profesyonel görünüm denetler.</span><span class="sxs-lookup"><span data-stu-id="5f9db-219">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="5f9db-220">Daha fazla bilgi için bkz: [nasıl yapılır: bir uygulama için ToolStrip oluşturucusunu ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="5f9db-220">For more information, see [How to: Set the ToolStrip Renderer for an Application](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f9db-221">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f9db-221">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="5f9db-222">Nasıl yapılır: MDI Üst Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5f9db-222">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="5f9db-223">Nasıl yapılır: MDI Alt Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5f9db-223">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="5f9db-224">Nasıl yapılır: Bir MDI Açılan Menüsüne MenuStrip ekleme</span><span class="sxs-lookup"><span data-stu-id="5f9db-224">How to: Insert a MenuStrip into an MDI Drop-Down Menu</span></span>](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)  
 [<span data-ttu-id="5f9db-225">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="5f9db-225">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
