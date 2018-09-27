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
ms.openlocfilehash: 6236190340833e3f8810387e51ad53e1cb10d37b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47232878"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="d945d-102">İzlenecek yol: Menü Birleştirme ve ToolStrip Denetimleri ile bir MDI Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d945d-102">Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls</span></span>
<span data-ttu-id="d945d-103"><xref:System.Windows.Forms?displayProperty=nameWithType> Ad alanı birden çok belge arabirimi (MDI) uygulamaları destekler ve <xref:System.Windows.Forms.MenuStrip> denetimi, menü birleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="d945d-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="d945d-104">MDI formları aynı zamanda <xref:System.Windows.Forms.ToolStrip> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="d945d-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="d945d-105">Bu izlenecek yolda nasıl kullanılacağını gösterir <xref:System.Windows.Forms.ToolStripPanel> denetimleriyle MDI formu.</span><span class="sxs-lookup"><span data-stu-id="d945d-105">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="d945d-106">Formu ile alt menülerini birleştirme menüsünü de destekler.</span><span class="sxs-lookup"><span data-stu-id="d945d-106">The form also supports menu merging with child menus.</span></span> <span data-ttu-id="d945d-107">Aşağıdaki görevler bu kılavuzda gösterilen:</span><span class="sxs-lookup"><span data-stu-id="d945d-107">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="d945d-108">Bir Windows Forms projesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="d945d-108">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="d945d-109">Formunuz için ana menü oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="d945d-109">Creating the main menu for your form.</span></span> <span data-ttu-id="d945d-110">Menü gerçek adıyla değişir.</span><span class="sxs-lookup"><span data-stu-id="d945d-110">The actual name of the menu will vary.</span></span>  
  
-   <span data-ttu-id="d945d-111">Ekleme <xref:System.Windows.Forms.ToolStripPanel> denetimini **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="d945d-111">Adding the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox**.</span></span>  
  
-   <span data-ttu-id="d945d-112">Bir alt form oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="d945d-112">Creating a child form.</span></span>  
  
-   <span data-ttu-id="d945d-113">Düzenleme <xref:System.Windows.Forms.ToolStripPanel> z sırasına göre denetimler.</span><span class="sxs-lookup"><span data-stu-id="d945d-113">Arranging <xref:System.Windows.Forms.ToolStripPanel> controls by z-order.</span></span>  
  
 <span data-ttu-id="d945d-114">İşlemi tamamladığınızda, menü birleştirme ve taşınabilir destekleyen MDI Formu olacaktır <xref:System.Windows.Forms.ToolStrip> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="d945d-114">When you are finished, you will have an MDI form that supports menu merging and movable <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="d945d-115">Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: menü birleştirme ve ToolStrip denetimleri içeren MDI formu oluşturma](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d945d-115">To copy the code in this topic as a single listing, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d945d-116">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="d945d-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d945d-117">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="d945d-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d945d-118">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d945d-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d945d-119">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="d945d-119">Prerequisites</span></span>  
 <span data-ttu-id="d945d-120">Bu izlenecek yolu tamamlamak için şunlar gerekir:</span><span class="sxs-lookup"><span data-stu-id="d945d-120">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="d945d-121">Oluşturma ve Windows Forms application projesi Visual Studio'nun yüklü bilgisayarda çalıştırmak için yeterli izinleri yok.</span><span class="sxs-lookup"><span data-stu-id="d945d-121">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="d945d-122">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d945d-122">Creating the Project</span></span>  
 <span data-ttu-id="d945d-123">İlk adım projeyi oluşturmak ve formu ayarlamaktır.</span><span class="sxs-lookup"><span data-stu-id="d945d-123">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="d945d-124">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d945d-124">To create the project</span></span>  
  
1.  <span data-ttu-id="d945d-125">Adlı bir Windows uygulaması projesi oluşturmak **MdiForm** (**dosya** > **yeni** > **proje**  >  **Visual C#** veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms uygulamalarındaki**).</span><span class="sxs-lookup"><span data-stu-id="d945d-125">Create a Windows Application project called **MdiForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="d945d-126">Formu Windows Form Tasarımcısı'nda seçin.</span><span class="sxs-lookup"><span data-stu-id="d945d-126">In the Windows Forms Designer, select the form.</span></span>  
  
3.  <span data-ttu-id="d945d-127">Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.Form.IsMdiContainer%2A> için `true`.</span><span class="sxs-lookup"><span data-stu-id="d945d-127">In the Properties window, set the value of the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> to `true`.</span></span>  
  
## <a name="creating-the-main-menu"></a><span data-ttu-id="d945d-128">Ana menü oluşturma</span><span class="sxs-lookup"><span data-stu-id="d945d-128">Creating the Main Menu</span></span>  
 <span data-ttu-id="d945d-129">Üst MDI formu ana menü içerir.</span><span class="sxs-lookup"><span data-stu-id="d945d-129">The parent MDI form contains the main menu.</span></span> <span data-ttu-id="d945d-130">Ana menü öğesi adlı tek menü sahip **penceresi**.</span><span class="sxs-lookup"><span data-stu-id="d945d-130">The main menu has one menu item named **Window**.</span></span> <span data-ttu-id="d945d-131">İle **penceresi** menü öğesi alt formları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d945d-131">With the **Window** menu item, you can create child forms.</span></span> <span data-ttu-id="d945d-132">Ana menüye menü öğeleri alt formları birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d945d-132">Menu items from child forms are merged into the main menu.</span></span>  
  
#### <a name="to-create-the-main-menu"></a><span data-ttu-id="d945d-133">Ana menü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d945d-133">To create the Main menu</span></span>  
  
1.  <span data-ttu-id="d945d-134">Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.MenuStrip> forma denetim.</span><span class="sxs-lookup"><span data-stu-id="d945d-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the form.</span></span>  
  
2.  <span data-ttu-id="d945d-135">Ekleme bir <xref:System.Windows.Forms.ToolStripMenuItem> için <xref:System.Windows.Forms.MenuStrip> denetlemek ve adlandırın **penceresi**.</span><span class="sxs-lookup"><span data-stu-id="d945d-135">Add a <xref:System.Windows.Forms.ToolStripMenuItem> to the <xref:System.Windows.Forms.MenuStrip> control and name it **Window**.</span></span>  
  
3.  <span data-ttu-id="d945d-136">Seçin <xref:System.Windows.Forms.MenuStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d945d-136">Select the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
4.  <span data-ttu-id="d945d-137">Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliğini `ToolStripMenuItem1`.</span><span class="sxs-lookup"><span data-stu-id="d945d-137">In the Properties window, set the value of the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to `ToolStripMenuItem1`.</span></span>  
  
5.  <span data-ttu-id="d945d-138">Eklemek için bir alt **penceresi** menü öğesini ve ardından ad alt **yeni**.</span><span class="sxs-lookup"><span data-stu-id="d945d-138">Add a subitem to the **Window** menu item, and then name the subitem **New**.</span></span>  
  
6.  <span data-ttu-id="d945d-139">Özellikler penceresinde tıklayın **olayları**.</span><span class="sxs-lookup"><span data-stu-id="d945d-139">In the Properties window, click **Events**.</span></span>  
  
7.  <span data-ttu-id="d945d-140">Çift <xref:System.Windows.Forms.ToolStripItem.Click> olay.</span><span class="sxs-lookup"><span data-stu-id="d945d-140">Double-click the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>  
  
     <span data-ttu-id="d945d-141">Windows Form Tasarımcısı için bir olay işleyicisi oluşturur <xref:System.Windows.Forms.ToolStripItem.Click> olay.</span><span class="sxs-lookup"><span data-stu-id="d945d-141">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>  
  
8.  <span data-ttu-id="d945d-142">Olay işleyicisine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d945d-142">Insert the following code into the event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="d945d-143">ToolStripPanel denetimi araç kutusuna ekleme</span><span class="sxs-lookup"><span data-stu-id="d945d-143">Adding the ToolStripPanel Control to the Toolbox</span></span>  
 <span data-ttu-id="d945d-144">Kullanırken <xref:System.Windows.Forms.MenuStrip> denetimleriyle MDI Formu olmalıdır <xref:System.Windows.Forms.ToolStripPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d945d-144">When you use <xref:System.Windows.Forms.MenuStrip> controls with an MDI form you must have the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="d945d-145">Eklemelisiniz <xref:System.Windows.Forms.ToolStripPanel> denetimini **araç kutusu** , MDI Formu Windows Form Tasarımcısı'nda oluşturulacak.</span><span class="sxs-lookup"><span data-stu-id="d945d-145">You must add the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox** to build your MDI form in the Windows Forms Designer.</span></span>  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="d945d-146">ToolStripPanel denetimi araç kutusuna eklemek için</span><span class="sxs-lookup"><span data-stu-id="d945d-146">To add the ToolStripPanel control to the Toolbox</span></span>  
  
1.  <span data-ttu-id="d945d-147">Açık **araç kutusu**ve ardından **tüm Windows Formları** kullanılabilir Windows Forms denetimleri göstermek için sekmesinde.</span><span class="sxs-lookup"><span data-stu-id="d945d-147">Open the **Toolbox**, and then click the **All Windows Forms** tab to show the available Windows Forms controls.</span></span>  
  
2.  <span data-ttu-id="d945d-148">Kısayol menüsünü açmak için sağ tıklatın ve seçin **öğelerini Seç**.</span><span class="sxs-lookup"><span data-stu-id="d945d-148">Right-click to open the shortcut menu, and select **Choose Items**.</span></span>  
  
3.  <span data-ttu-id="d945d-149">İçinde **araç kutusu öğelerini Seç** iletişim kutusu, aşağı kaydırın **adı** bulana kadar sütun **ToolStripPanel**.</span><span class="sxs-lookup"><span data-stu-id="d945d-149">In the **Choose Toolbox Items** dialog box, scroll down the **Name** column until you find **ToolStripPanel**.</span></span>  
  
4.  <span data-ttu-id="d945d-150">Onay kutusunu **ToolStripPanel**ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="d945d-150">Select the check box by **ToolStripPanel**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="d945d-151"><xref:System.Windows.Forms.ToolStripPanel> Denetimi görünür **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="d945d-151">The <xref:System.Windows.Forms.ToolStripPanel> control appears in the **Toolbox**.</span></span>  
  
## <a name="creating-a-child-form"></a><span data-ttu-id="d945d-152">Bir alt Form oluşturma</span><span class="sxs-lookup"><span data-stu-id="d945d-152">Creating a Child Form</span></span>  
 <span data-ttu-id="d945d-153">Bu yordamda, kendi ayrı bir alt form sınıfı tanımlayacak <xref:System.Windows.Forms.MenuStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d945d-153">In this procedure, you will define a separate child form class that has its own <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="d945d-154">Bu form için menü öğeleri bu üst formu ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d945d-154">The menu items for this form are merged with those of the parent form.</span></span>  
  
#### <a name="to-define-a-child-form"></a><span data-ttu-id="d945d-155">Bir alt form tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="d945d-155">To define a child form</span></span>  
  
1.  <span data-ttu-id="d945d-156">Adlı yeni bir form ekleyin `ChildForm` projeye.</span><span class="sxs-lookup"><span data-stu-id="d945d-156">Add a new form named `ChildForm` to the project.</span></span>  
  
     <span data-ttu-id="d945d-157">Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms bir proje eklemek](https://msdn.microsoft.com/library/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span><span class="sxs-lookup"><span data-stu-id="d945d-157">For more information, see [How to: Add Windows Forms to a Project](https://msdn.microsoft.com/library/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
2.  <span data-ttu-id="d945d-158">Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.MenuStrip> alt forma denetim.</span><span class="sxs-lookup"><span data-stu-id="d945d-158">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the child form.</span></span>  
  
3.  <span data-ttu-id="d945d-159">Tıklayın <xref:System.Windows.Forms.MenuStrip> denetimin akıllı etiket karakterini (![akıllı etiket karakterini](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) ve ardından **öğe düzenleme**.</span><span class="sxs-lookup"><span data-stu-id="d945d-159">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), and then select **Edit Items**.</span></span>  
  
4.  <span data-ttu-id="d945d-160">İçinde **öğeler Koleksiyonu Düzenleyicisi** iletişim kutusunda, yeni bir <xref:System.Windows.Forms.ToolStripMenuItem> adlı **ChildMenuItem** alt menüsü.</span><span class="sxs-lookup"><span data-stu-id="d945d-160">In the **Items Collection Editor** dialog box, add a new <xref:System.Windows.Forms.ToolStripMenuItem> named **ChildMenuItem** to the child menu.</span></span>  
  
     <span data-ttu-id="d945d-161">Daha fazla bilgi için [ToolStrip öğeler Koleksiyonu Düzenleyicisi](https://msdn.microsoft.com/library/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).</span><span class="sxs-lookup"><span data-stu-id="d945d-161">For more information, see [ToolStrip Items Collection Editor](https://msdn.microsoft.com/library/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).</span></span>  
  
## <a name="testing-the-form"></a><span data-ttu-id="d945d-162">Form test etme</span><span class="sxs-lookup"><span data-stu-id="d945d-162">Testing the Form</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="d945d-163">Formunuza test etmek için</span><span class="sxs-lookup"><span data-stu-id="d945d-163">To test your form</span></span>  
  
1.  <span data-ttu-id="d945d-164">Derlemek ve formunuza çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d945d-164">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="d945d-165">Tıklayın **penceresi** menüsünü açın ve ardından menü öğesi **yeni**.</span><span class="sxs-lookup"><span data-stu-id="d945d-165">Click the **Window** menu item to open the menu, and then click **New**.</span></span>  
  
     <span data-ttu-id="d945d-166">Yeni bir alt form, form denetiminin MDI istemci alanında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d945d-166">A new child form is created in the form's MDI client area.</span></span> <span data-ttu-id="d945d-167">Alt formun menüsünde ana menü ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d945d-167">The child form's menu is merged with the main menu.</span></span>  
  
3.  <span data-ttu-id="d945d-168">Alt formu kapatın.</span><span class="sxs-lookup"><span data-stu-id="d945d-168">Close the child form.</span></span>  
  
     <span data-ttu-id="d945d-169">Alt formun menüsü, ana menüden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="d945d-169">The child form's menu is removed from the main menu.</span></span>  
  
4.  <span data-ttu-id="d945d-170">Tıklayın **yeni** birkaç kez.</span><span class="sxs-lookup"><span data-stu-id="d945d-170">Click **New** several times.</span></span>  
  
     <span data-ttu-id="d945d-171">Alt formları otomatik olarak altında listelenen **penceresi** menü öğesi olduğundan <xref:System.Windows.Forms.MenuStrip> denetimin <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliğine atanır.</span><span class="sxs-lookup"><span data-stu-id="d945d-171">The child forms are automatically listed under the **Window** menu item because the <xref:System.Windows.Forms.MenuStrip> control's <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property is assigned.</span></span>  
  
## <a name="adding-toolstrip-support"></a><span data-ttu-id="d945d-172">ToolStrip desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="d945d-172">Adding ToolStrip Support</span></span>  
 <span data-ttu-id="d945d-173">Bu yordamda, dört ekleyeceksiniz <xref:System.Windows.Forms.ToolStrip> MDI üst formu için denetimler.</span><span class="sxs-lookup"><span data-stu-id="d945d-173">In this procedure, you will add four <xref:System.Windows.Forms.ToolStrip> controls to the MDI parent form.</span></span> <span data-ttu-id="d945d-174">Her <xref:System.Windows.Forms.ToolStrip> denetimi içinde eklenir bir <xref:System.Windows.Forms.ToolStripPanel> form kenarına yerleştirildiğini denetimi.</span><span class="sxs-lookup"><span data-stu-id="d945d-174">Each <xref:System.Windows.Forms.ToolStrip> control is added inside a <xref:System.Windows.Forms.ToolStripPanel> control, which is docked to the edge of the form.</span></span>  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a><span data-ttu-id="d945d-175">MDI üst formu için ToolStrip denetimleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="d945d-175">To add ToolStrip controls to the MDI parent form</span></span>  
  
1.  <span data-ttu-id="d945d-176">Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.ToolStripPanel> forma denetim.</span><span class="sxs-lookup"><span data-stu-id="d945d-176">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStripPanel> control onto the form.</span></span>  
  
2.  <span data-ttu-id="d945d-177">İle <xref:System.Windows.Forms.ToolStripPanel> çift tıklayın, Denetim seçili <xref:System.Windows.Forms.ToolStrip> denetim **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="d945d-177">With the <xref:System.Windows.Forms.ToolStripPanel> control selected, double-click the <xref:System.Windows.Forms.ToolStrip> control in the **Toolbox**.</span></span>  
  
     <span data-ttu-id="d945d-178">A <xref:System.Windows.Forms.ToolStrip> denetim oluşturuldu <xref:System.Windows.Forms.ToolStripPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d945d-178">A <xref:System.Windows.Forms.ToolStrip> control is created in the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
3.  <span data-ttu-id="d945d-179">Seçin <xref:System.Windows.Forms.ToolStripPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d945d-179">Select the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
4.  <span data-ttu-id="d945d-180">Özellikler penceresinde, denetimin değiştirin <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="d945d-180">In the Properties window, change the value of the control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span>  
  
     <span data-ttu-id="d945d-181"><xref:System.Windows.Forms.ToolStripPanel> Kontrol noktalarını sol tarafındaki formun ana menü altında.</span><span class="sxs-lookup"><span data-stu-id="d945d-181">The <xref:System.Windows.Forms.ToolStripPanel> control docks to the left side of the form, underneath the main menu.</span></span> <span data-ttu-id="d945d-182">MDI istemci alanını uyacak şekilde yeniden boyutlandırır <xref:System.Windows.Forms.ToolStripPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d945d-182">The MDI client area resizes to fit the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
5.  <span data-ttu-id="d945d-183">1 ile 4 arasındaki adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="d945d-183">Repeat steps 1 through 4.</span></span>  
  
     <span data-ttu-id="d945d-184">Yeni dock <xref:System.Windows.Forms.ToolStripPanel> üst form denetimi.</span><span class="sxs-lookup"><span data-stu-id="d945d-184">Dock the new <xref:System.Windows.Forms.ToolStripPanel> control to the top of the form.</span></span>  
  
     <span data-ttu-id="d945d-185"><xref:System.Windows.Forms.ToolStripPanel> Denetim ana menü altında ancak ilk sağındaki yerleştirilmiştir <xref:System.Windows.Forms.ToolStripPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d945d-185">The <xref:System.Windows.Forms.ToolStripPanel> control is docked underneath the main menu, but to the right of the first <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="d945d-186">Bu adım doğru konumlandırmada z düzenini önemini gösterir <xref:System.Windows.Forms.ToolStripPanel> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="d945d-186">This step illustrates the importance of z-order in correctly positioning <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
6.  <span data-ttu-id="d945d-187">Daha fazla iki için 1 ile 4 arasındaki adımları yineleyin <xref:System.Windows.Forms.ToolStripPanel> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="d945d-187">Repeat steps 1 through 4 for two more <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
     <span data-ttu-id="d945d-188">Yeni dock <xref:System.Windows.Forms.ToolStripPanel> sağa ve formun altına denetimleri.</span><span class="sxs-lookup"><span data-stu-id="d945d-188">Dock the new <xref:System.Windows.Forms.ToolStripPanel> controls to the right and bottom of the form.</span></span>  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="d945d-189">Z sırasına ToolStripPanel denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="d945d-189">Arranging ToolStripPanel Controls by Z-order</span></span>  
 <span data-ttu-id="d945d-190">Bir yerleşik konumunu <xref:System.Windows.Forms.ToolStripPanel> , MDI formu denetimi, z düzenini denetimin konumu tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="d945d-190">The position of a docked <xref:System.Windows.Forms.ToolStripPanel> control on your MDI form is determined by the control's position in the z-order.</span></span> <span data-ttu-id="d945d-191">Belge Anahattı penceresi içinde denetimlerin z düzenini kolayca düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d945d-191">You can easily arrange the z-order of your controls in the Document Outline window.</span></span>  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="d945d-192">Z düzenini ToolStripPanel denetimleriyle düzenlemek için</span><span class="sxs-lookup"><span data-stu-id="d945d-192">To arrange ToolStripPanel controls by Z-order</span></span>  
  
1.  <span data-ttu-id="d945d-193">İçinde **görünümü** menüsünde tıklatın **diğer Windows**ve ardından **belge anahattı**.</span><span class="sxs-lookup"><span data-stu-id="d945d-193">In the **View** menu, click **Other Windows**, and then click **Document Outline**.</span></span>  
  
     <span data-ttu-id="d945d-194">Düzenlemesini, <xref:System.Windows.Forms.ToolStripPanel> denetimleri önceki yordamın bildiriliyor.</span><span class="sxs-lookup"><span data-stu-id="d945d-194">The arrangement of your <xref:System.Windows.Forms.ToolStripPanel> controls from the previous procedure is nonstandard.</span></span> <span data-ttu-id="d945d-195">Z düzenini doğru olmadığı için budur.</span><span class="sxs-lookup"><span data-stu-id="d945d-195">This is because the z-order is not correct.</span></span> <span data-ttu-id="d945d-196">Belge Anahattı penceresi denetimlerinin z sıralamasını değiştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="d945d-196">Use the Document Outline window to change the z-order of the controls.</span></span>  
  
2.  <span data-ttu-id="d945d-197">Belge Anahattı penceresini seçin **ToolStripPanel4**.</span><span class="sxs-lookup"><span data-stu-id="d945d-197">In the Document Outline window, select **ToolStripPanel4**.</span></span>  
  
3.  <span data-ttu-id="d945d-198">Aşağı ok düğmesini tekrar tekrar kadar **ToolStripPanel4** listesinin alt.</span><span class="sxs-lookup"><span data-stu-id="d945d-198">Click the down-arrow button repeatedly, until **ToolStripPanel4** is at the bottom of the list.</span></span>  
  
     <span data-ttu-id="d945d-199">**ToolStripPanel4** denetim, diğer denetimlerin altında formun altına yerleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d945d-199">The **ToolStripPanel4** control is docked to the bottom of the form, underneath the other controls.</span></span>  
  
4.  <span data-ttu-id="d945d-200">Seçin **ToolStripPanel2**.</span><span class="sxs-lookup"><span data-stu-id="d945d-200">Select **ToolStripPanel2**.</span></span>  
  
5.  <span data-ttu-id="d945d-201">Aşağı ok düğmesini denetimi üçüncü listede konumlandırmak için bir kez tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d945d-201">Click the down-arrow button one time to position the control third in the list.</span></span>  
  
     <span data-ttu-id="d945d-202">**ToolStripPanel2** denetimi için ana menü altında ve diğer denetimleri yukarıda formun üst yerleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d945d-202">The **ToolStripPanel2** control is docked to the top of the form, underneath the main menu and above the other controls.</span></span>  
  
6.  <span data-ttu-id="d945d-203">Çeşitli denetimleri seçin **belge anahattı** penceresi ve z düzeninde farklı konumlara taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d945d-203">Select various controls in the **Document Outline** window and move them to different positions in the z-order.</span></span> <span data-ttu-id="d945d-204">Yerleşik denetimler yerleşimini z düzenini etkisini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d945d-204">Note the effect of the z-order on the placement of docked controls.</span></span> <span data-ttu-id="d945d-205">CTRL-Z kullanın veya **geri** üzerinde **Düzenle** değişikliklerinizi geri almak için menü.</span><span class="sxs-lookup"><span data-stu-id="d945d-205">Use CTRL-Z or **Undo** on the **Edit** menu to undo your changes.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="d945d-206">Denetim noktası</span><span class="sxs-lookup"><span data-stu-id="d945d-206">Checkpoint</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="d945d-207">Formunuza test etmek için</span><span class="sxs-lookup"><span data-stu-id="d945d-207">To test your form</span></span>  
  
1.  <span data-ttu-id="d945d-208">Derlemek ve formunuza çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d945d-208">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="d945d-209">Tutamacı tıklayın bir <xref:System.Windows.Forms.ToolStrip> denetlemek ve denetimi form üzerinde farklı konumlara sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="d945d-209">Click the grip of a <xref:System.Windows.Forms.ToolStrip> control and drag the control to different positions on the form.</span></span>  
  
     <span data-ttu-id="d945d-210">Sürükleyebilirsiniz bir <xref:System.Windows.Forms.ToolStrip> bir denetimden <xref:System.Windows.Forms.ToolStripPanel> başka bir denetim.</span><span class="sxs-lookup"><span data-stu-id="d945d-210">You can drag a <xref:System.Windows.Forms.ToolStrip> control from one <xref:System.Windows.Forms.ToolStripPanel> control to another.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d945d-211">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="d945d-211">Next Steps</span></span>  
 <span data-ttu-id="d945d-212">Bu kılavuzda, MDI üst formu ile oluşturduğunuz <xref:System.Windows.Forms.ToolStrip> denetimleri ve menü birleştirme.</span><span class="sxs-lookup"><span data-stu-id="d945d-212">In this walkthrough, you have created an MDI parent form with <xref:System.Windows.Forms.ToolStrip> controls and menu merging.</span></span> <span data-ttu-id="d945d-213">Kullanabileceğiniz <xref:System.Windows.Forms.ToolStrip> birçok başka amaçlarla denetimlerin ailesi:</span><span class="sxs-lookup"><span data-stu-id="d945d-213">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="d945d-214">Sahip, denetimler için kısayol menüleri oluşturma <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="d945d-214">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="d945d-215">Daha fazla bilgi için [ContextMenu bileşenine genel bakış](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d945d-215">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="d945d-216">Bir formu otomatik olarak doldurulan bir standart menü ile oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="d945d-216">Created a form with an automatically populated standard menu.</span></span> <span data-ttu-id="d945d-217">Daha fazla bilgi için [izlenecek yol: bir forma standart menü öğeleri sağlama](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="d945d-217">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
-   <span data-ttu-id="d945d-218">Verin, <xref:System.Windows.Forms.ToolStrip> profesyonel bir görünümünü denetler.</span><span class="sxs-lookup"><span data-stu-id="d945d-218">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="d945d-219">Daha fazla bilgi için [nasıl yapılır: bir uygulama için ToolStrip oluşturucusunu ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="d945d-219">For more information, see [How to: Set the ToolStrip Renderer for an Application](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d945d-220">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d945d-220">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="d945d-221">Nasıl yapılır: MDI Üst Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d945d-221">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="d945d-222">Nasıl yapılır: MDI Alt Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d945d-222">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="d945d-223">Nasıl yapılır: Bir MDI Açılan Menüsüne MenuStrip ekleme</span><span class="sxs-lookup"><span data-stu-id="d945d-223">How to: Insert a MenuStrip into an MDI Drop-Down Menu</span></span>](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)  
 [<span data-ttu-id="d945d-224">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="d945d-224">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
