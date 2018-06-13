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
ms.openlocfilehash: 2d2443f1f7153ed35aecbbb9d69c9e1421269e24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541612"
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="a4c73-102">İzlenecek yol: Profesyonel Stilde ToolStrip Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a4c73-102">Walkthrough: Creating a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="a4c73-103">Uygulamanızın verebilirsiniz <xref:System.Windows.Forms.ToolStrip> türetilmiş kendi sınıfı yazarak profesyonel görünümünü ve davranışını denetler <xref:System.Windows.Forms.ToolStripProfessionalRenderer> türü.</span><span class="sxs-lookup"><span data-stu-id="a4c73-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="a4c73-104">Bu kılavuzda nasıl kullanılacağı ortaya <xref:System.Windows.Forms.ToolStrip> benzer bir bileşik denetim oluşturmak için denetimleri **Gezinti Bölmesi** Microsoft Outlook® tarafından sağlanan.</span><span class="sxs-lookup"><span data-stu-id="a4c73-104">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that resembles the **Navigation Pane** provided by Microsoft® Outlook®.</span></span> <span data-ttu-id="a4c73-105">Aşağıdaki görevler bu kılavuzda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a4c73-105">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="a4c73-106">Windows Denetim Kitaplığı projesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="a4c73-106">Creating a Windows Control Library project.</span></span>  
  
-   <span data-ttu-id="a4c73-107">StackView denetimi tasarlarken.</span><span class="sxs-lookup"><span data-stu-id="a4c73-107">Designing the StackView Control.</span></span>  
  
-   <span data-ttu-id="a4c73-108">Özel oluşturucu oluşturma.</span><span class="sxs-lookup"><span data-stu-id="a4c73-108">Implementing a Custom Renderer.</span></span>  
  
 <span data-ttu-id="a4c73-109">İşiniz bittiğinde, profesyonel bir Microsoft Office® XP denetiminin görünümünü ile yeniden kullanılabilir özel istemci denetime sahip olur.</span><span class="sxs-lookup"><span data-stu-id="a4c73-109">When you are finished, you will have a reusable custom client control with the professional appearance of a Microsoft Office® XP control.</span></span>  
  
 <span data-ttu-id="a4c73-110">Bu konuda tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: bir profesyonel stilde ToolStrip denetimi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="a4c73-110">To copy the code in this topic as a single listing, see [How to: Create a Professionally Styled ToolStrip Control](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4c73-111">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="a4c73-111">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a4c73-112">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="a4c73-112">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a4c73-113">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="a4c73-113">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a4c73-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="a4c73-114">Prerequisites</span></span>  
 <span data-ttu-id="a4c73-115">Bu kılavuzu tamamlamak için gerekir:</span><span class="sxs-lookup"><span data-stu-id="a4c73-115">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="a4c73-116">Oluşturma ve Windows Forms uygulaması projeleri, Visual Studio yüklü olduğu bilgisayarda çalıştırmak için yeterli izinleri yok.</span><span class="sxs-lookup"><span data-stu-id="a4c73-116">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-a-windows-control-library-project"></a><span data-ttu-id="a4c73-117">Windows Denetim Kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="a4c73-117">Creating a Windows Control Library Project</span></span>  
 <span data-ttu-id="a4c73-118">İlk adım, denetim kitaplığı projesi oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="a4c73-118">The first step is to create the control library project.</span></span>  
  
#### <a name="to-create-the-control-library-project"></a><span data-ttu-id="a4c73-119">Denetim Kitaplığı projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a4c73-119">To create the control library project</span></span>  
  
1.  <span data-ttu-id="a4c73-120">Adlı yeni bir Windows Denetim Kitaplığı projesi oluşturun `StackViewLibrary`.</span><span class="sxs-lookup"><span data-stu-id="a4c73-120">Create a new Windows Control Library project named `StackViewLibrary`.</span></span>  
  
2.  <span data-ttu-id="a4c73-121">İçinde **Çözüm Gezgini**, projenin varsayılan denetim seçim dilinizi bağlı olarak "UserControl1.cs" veya "UserControl1.vb" adlı kaynak dosya silerek silin.</span><span class="sxs-lookup"><span data-stu-id="a4c73-121">In **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span>  
  
     <span data-ttu-id="a4c73-122">Daha fazla bilgi için bkz: [NIB: nasıl yapılır: Kaldır, silme ve dışlama öğeleri](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span><span class="sxs-lookup"><span data-stu-id="a4c73-122">For more information, see [NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span></span>  
  
3.  <span data-ttu-id="a4c73-123">Yeni bir ekleme <xref:System.Windows.Forms.UserControl> öğesinin **StackViewLibrary** projesi.</span><span class="sxs-lookup"><span data-stu-id="a4c73-123">Add a new <xref:System.Windows.Forms.UserControl> item to the **StackViewLibrary** project.</span></span> <span data-ttu-id="a4c73-124">Yeni kaynak dosyasını, temel bir ad verin `StackView`.</span><span class="sxs-lookup"><span data-stu-id="a4c73-124">Give the new source file a base name of `StackView`.</span></span>  
  
## <a name="designing-the-stackview-control"></a><span data-ttu-id="a4c73-125">StackView denetim tasarlama</span><span class="sxs-lookup"><span data-stu-id="a4c73-125">Designing the StackView Control</span></span>  
 <span data-ttu-id="a4c73-126">`StackView` Denetimidir bir alt ile bileşik denetim <xref:System.Windows.Forms.ToolStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="a4c73-126">The `StackView` control is a composite control with one child <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="a4c73-127">Bileşik denetimler hakkında daha fazla bilgi için bkz: [özel denetimler çeşit](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="a4c73-127">For more information about composite controls, see [Varieties of Custom Controls](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).</span></span>  
  
#### <a name="to-design-the-stackview-control"></a><span data-ttu-id="a4c73-128">Tasarım StackView denetimi</span><span class="sxs-lookup"><span data-stu-id="a4c73-128">To design the StackView control</span></span>  
  
1.  <span data-ttu-id="a4c73-129">Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.ToolStrip> tasarım yüzeyine denetimine.</span><span class="sxs-lookup"><span data-stu-id="a4c73-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStrip> control to the design surface.</span></span>  
  
2.  <span data-ttu-id="a4c73-130">İçinde **özellikleri** penceresindeki ayarlayın <xref:System.Windows.Forms.ToolStrip> denetimin özelliklerini aşağıdaki tabloya göre.</span><span class="sxs-lookup"><span data-stu-id="a4c73-130">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStrip> control's properties according to the following table.</span></span>  
  
    |<span data-ttu-id="a4c73-131">Özellik</span><span class="sxs-lookup"><span data-stu-id="a4c73-131">Property</span></span>|<span data-ttu-id="a4c73-132">Değer</span><span class="sxs-lookup"><span data-stu-id="a4c73-132">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="a4c73-133">Ad</span><span class="sxs-lookup"><span data-stu-id="a4c73-133">Name</span></span>|`stackStrip`|  
    |<span data-ttu-id="a4c73-134">CanOverflow</span><span class="sxs-lookup"><span data-stu-id="a4c73-134">CanOverflow</span></span>|`false`|  
    |<span data-ttu-id="a4c73-135">Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="a4c73-135">Dock</span></span>|<xref:System.Windows.Forms.DockStyle.Bottom>|  
    |<span data-ttu-id="a4c73-136">Yazı tipi</span><span class="sxs-lookup"><span data-stu-id="a4c73-136">Font</span></span>|`Tahoma, 10pt, style=Bold`|  
    |<span data-ttu-id="a4c73-137">GripStyle</span><span class="sxs-lookup"><span data-stu-id="a4c73-137">GripStyle</span></span>|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|  
    |<span data-ttu-id="a4c73-138">LayoutStyle</span><span class="sxs-lookup"><span data-stu-id="a4c73-138">LayoutStyle</span></span>|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|  
    |<span data-ttu-id="a4c73-139">Doldurma</span><span class="sxs-lookup"><span data-stu-id="a4c73-139">Padding</span></span>|`0, 7, 0, 0`|  
    |<span data-ttu-id="a4c73-140">RenderMode</span><span class="sxs-lookup"><span data-stu-id="a4c73-140">RenderMode</span></span>|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|  
  
3.  <span data-ttu-id="a4c73-141">Windows Forms Tasarımcısı'nda tıklayın <xref:System.Windows.Forms.ToolStrip> denetimin **Ekle** düğmesini tıklatın ve eklemek bir <xref:System.Windows.Forms.ToolStripButton> için `stackStrip` denetim.</span><span class="sxs-lookup"><span data-stu-id="a4c73-141">In the Windows Forms Designer, click the <xref:System.Windows.Forms.ToolStrip> control's **Add** button and add a <xref:System.Windows.Forms.ToolStripButton> to the `stackStrip` control.</span></span>  
  
4.  <span data-ttu-id="a4c73-142">İçinde **özellikleri** penceresindeki ayarlayın <xref:System.Windows.Forms.ToolStripButton> denetimin özelliklerini aşağıdaki tabloya göre.</span><span class="sxs-lookup"><span data-stu-id="a4c73-142">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStripButton> control's properties according to the following table.</span></span>  
  
    |<span data-ttu-id="a4c73-143">Özellik</span><span class="sxs-lookup"><span data-stu-id="a4c73-143">Property</span></span>|<span data-ttu-id="a4c73-144">Değer</span><span class="sxs-lookup"><span data-stu-id="a4c73-144">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="a4c73-145">Ad</span><span class="sxs-lookup"><span data-stu-id="a4c73-145">Name</span></span>|`mailStackButton`|  
    |<span data-ttu-id="a4c73-146">CheckOnClick</span><span class="sxs-lookup"><span data-stu-id="a4c73-146">CheckOnClick</span></span>|<span data-ttu-id="a4c73-147">true</span><span class="sxs-lookup"><span data-stu-id="a4c73-147">true</span></span>|  
    |<span data-ttu-id="a4c73-148">CheckState</span><span class="sxs-lookup"><span data-stu-id="a4c73-148">CheckState</span></span>|<xref:System.Windows.Forms.CheckState.Checked>|  
    |<span data-ttu-id="a4c73-149">DisplayStyle</span><span class="sxs-lookup"><span data-stu-id="a4c73-149">DisplayStyle</span></span>|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|  
    |<span data-ttu-id="a4c73-150">ImageAlign</span><span class="sxs-lookup"><span data-stu-id="a4c73-150">ImageAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
    |<span data-ttu-id="a4c73-151">ImageScaling</span><span class="sxs-lookup"><span data-stu-id="a4c73-151">ImageScaling</span></span>|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|  
    |<span data-ttu-id="a4c73-152">ImageTransparentColor</span><span class="sxs-lookup"><span data-stu-id="a4c73-152">ImageTransparentColor</span></span>|`238, 238, 238`|  
    |<span data-ttu-id="a4c73-153">Kenar boşluğu</span><span class="sxs-lookup"><span data-stu-id="a4c73-153">Margin</span></span>|`0, 0, 0, 0`|  
    |<span data-ttu-id="a4c73-154">Doldurma</span><span class="sxs-lookup"><span data-stu-id="a4c73-154">Padding</span></span>|`3, 3, 3, 3`|  
    |<span data-ttu-id="a4c73-155">Metin</span><span class="sxs-lookup"><span data-stu-id="a4c73-155">Text</span></span>|<span data-ttu-id="a4c73-156">**Posta**</span><span class="sxs-lookup"><span data-stu-id="a4c73-156">**Mail**</span></span>|  
    |<span data-ttu-id="a4c73-157">TextAlign</span><span class="sxs-lookup"><span data-stu-id="a4c73-157">TextAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
  
5.  <span data-ttu-id="a4c73-158">Daha fazla üç için yineleme adım 7 <xref:System.Windows.Forms.ToolStripButton> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="a4c73-158">Repeat step 7 for three more <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>  
  
     <span data-ttu-id="a4c73-159">Denetimleri adlandırın `calendarStackButton`, `contactsStackButton`, ve `tasksStackButton`.</span><span class="sxs-lookup"><span data-stu-id="a4c73-159">Name the controls `calendarStackButton`, `contactsStackButton`, and `tasksStackButton`.</span></span> <span data-ttu-id="a4c73-160">Değerini <xref:System.Windows.Forms.Control.Text%2A> özelliğine **Takvim**, **kişiler**, ve **görevleri**sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="a4c73-160">Set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to **Calendar**, **Contacts**, and **Tasks**, respectively.</span></span>  
  
## <a name="handling-events"></a><span data-ttu-id="a4c73-161">Olayları İşleme</span><span class="sxs-lookup"><span data-stu-id="a4c73-161">Handling Events</span></span>  
 <span data-ttu-id="a4c73-162">İki olay yapmak önemli olan `StackView` denetim doğru şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="a4c73-162">Two events are important to make the `StackView` control behave correctly.</span></span> <span data-ttu-id="a4c73-163">Tanıtıcı <xref:System.Windows.Forms.UserControl.Load> denetim doğru konuma olay.</span><span class="sxs-lookup"><span data-stu-id="a4c73-163">Handle the <xref:System.Windows.Forms.UserControl.Load> event to position the control correctly.</span></span> <span data-ttu-id="a4c73-164">İşleme <xref:System.Windows.Forms.ToolStripItem.Click> her olay <xref:System.Windows.Forms.ToolStripButton> vermek için `StackView` denetim durumu davranışını benzer <xref:System.Windows.Forms.RadioButton> denetim.</span><span class="sxs-lookup"><span data-stu-id="a4c73-164">Handle the <xref:System.Windows.Forms.ToolStripItem.Click> event for each <xref:System.Windows.Forms.ToolStripButton> to give the `StackView` control state behavior similar to the <xref:System.Windows.Forms.RadioButton> control.</span></span>  
  
#### <a name="to-handle-events"></a><span data-ttu-id="a4c73-165">Olayları işlemek için</span><span class="sxs-lookup"><span data-stu-id="a4c73-165">To handle events</span></span>  
  
1.  <span data-ttu-id="a4c73-166">Windows Forms Tasarımcısı'nda seçin `StackView` denetim.</span><span class="sxs-lookup"><span data-stu-id="a4c73-166">In the Windows Forms Designer, select the `StackView` control.</span></span>  
  
2.  <span data-ttu-id="a4c73-167">İçinde **özellikleri** penceresinde tıklatın **olayları**.</span><span class="sxs-lookup"><span data-stu-id="a4c73-167">In the **Properties** window, click **Events**.</span></span>  
  
3.  <span data-ttu-id="a4c73-168">Oluşturulacak yük olayı çift `StackView_Load` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="a4c73-168">Double-click the Load event to generate the `StackView_Load` event handler.</span></span>  
  
4.  <span data-ttu-id="a4c73-169">İçinde `StackView_Load` olay işleyicisi, aşağıdaki kodu kopyalayıp yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="a4c73-169">In the `StackView_Load` event handler, copy and paste the following code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]  
  
5.  <span data-ttu-id="a4c73-170">Windows Forms Tasarımcısı'nda seçin `mailStackButton` denetim.</span><span class="sxs-lookup"><span data-stu-id="a4c73-170">In the Windows Forms Designer, select the `mailStackButton` control.</span></span>  
  
6.  <span data-ttu-id="a4c73-171">İçinde **özellikleri** penceresinde tıklatın **olayları**.</span><span class="sxs-lookup"><span data-stu-id="a4c73-171">In the **Properties** window, click **Events**.</span></span>  
  
7.  <span data-ttu-id="a4c73-172">Click olayını çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a4c73-172">Double-click the Click event.</span></span>  
  
     <span data-ttu-id="a4c73-173">Windows Form Tasarımcısı oluşturur `mailStackButton_Click` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="a4c73-173">The Windows Forms Designer generates the `mailStackButton_Click` event handler.</span></span>  
  
8.  <span data-ttu-id="a4c73-174">Yeniden Adlandır `mailStackButton_Click` olay işleyicisine `stackButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="a4c73-174">Rename the `mailStackButton_Click` event handler to `stackButton_Click`.</span></span>  
  
     <span data-ttu-id="a4c73-175">Daha fazla bilgi için bkz: [nasıl yapılır: bir tanımlayıcı (Visual Basic) yeniden adlandırmak](http://msdn.microsoft.com/library/e5a5edf8-3dba-4119-81f4-fc2aba180e0c).</span><span class="sxs-lookup"><span data-stu-id="a4c73-175">For more information, see [How to: Rename an Identifier (Visual Basic)](http://msdn.microsoft.com/library/e5a5edf8-3dba-4119-81f4-fc2aba180e0c).</span></span>  
  
9. <span data-ttu-id="a4c73-176">Aşağıdaki kodu ekleyin `stackButton_Click` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="a4c73-176">Insert the following code into the `stackButton_Click` event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]  
  
10. <span data-ttu-id="a4c73-177">Windows Forms Tasarımcısı'nda seçin `calendarStackButton` denetim.</span><span class="sxs-lookup"><span data-stu-id="a4c73-177">In the Windows Forms Designer, select the `calendarStackButton` control.</span></span>  
  
11. <span data-ttu-id="a4c73-178">İçinde **özellikleri** penceresinde ayarlanmış Click olayını `stackButton_Click` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="a4c73-178">In the **Properties** window, set the Click event to the `stackButton_Click` event handler.</span></span>  
  
12. <span data-ttu-id="a4c73-179">10 ve 11. adımları tekrarlayarak `contactsStackButton` ve `tasksStackButton` kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="a4c73-179">Repeat steps 10 and 11 for the `contactsStackButton` and `tasksStackButton` controls.</span></span>  
  
## <a name="defining-icons"></a><span data-ttu-id="a4c73-180">Simgeler tanımlama</span><span class="sxs-lookup"><span data-stu-id="a4c73-180">Defining Icons</span></span>  
 <span data-ttu-id="a4c73-181">Her `StackView` düğmesi ilişkili bir simge bulunur.</span><span class="sxs-lookup"><span data-stu-id="a4c73-181">Each `StackView` button has an associated icon.</span></span> <span data-ttu-id="a4c73-182">Kolaylık olması için her bir simgeyi Base64 ile kodlanmış bir dize hangi önce seri temsil edilen bir <xref:System.Drawing.Bitmap> buradan oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a4c73-182">For convenience, each icon is represented as a Base64-encoded string, which is deserialized before a <xref:System.Drawing.Bitmap> is created from it.</span></span> <span data-ttu-id="a4c73-183">Bir üretim ortamında, bir kaynak olarak bit eşlem verileri depolamak ve Windows Forms Tasarımcısı'nda, simgeler görünür.</span><span class="sxs-lookup"><span data-stu-id="a4c73-183">In a production environment, you store bitmap data as a resource, and your icons appear in the Windows Forms Designer.</span></span> <span data-ttu-id="a4c73-184">Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms için arka plan görüntüleri ekleme](http://msdn.microsoft.com/library/7a509ba2-055c-4ae6-b88a-54625c6d9aff).</span><span class="sxs-lookup"><span data-stu-id="a4c73-184">For more information, see [How to: Add Background Images to Windows Forms](http://msdn.microsoft.com/library/7a509ba2-055c-4ae6-b88a-54625c6d9aff).</span></span>  
  
#### <a name="to-define-icons"></a><span data-ttu-id="a4c73-185">Simgeler tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="a4c73-185">To define icons</span></span>  
  
1.  <span data-ttu-id="a4c73-186">Kod Düzenleyicisi'nde, aşağıdaki kodu ekleyin `StackView` sınıf tanımının.</span><span class="sxs-lookup"><span data-stu-id="a4c73-186">In the Code Editor, insert the following code into the `StackView` class definition.</span></span> <span data-ttu-id="a4c73-187">Bu kod için bit eşlemler başlatır <xref:System.Windows.Forms.ToolStripButton> simgeler.</span><span class="sxs-lookup"><span data-stu-id="a4c73-187">This code initializes the bitmaps for the <xref:System.Windows.Forms.ToolStripButton> icons.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]  
  
2.  <span data-ttu-id="a4c73-188">Bir çağrı ekleyin `InitializeImages` yönteminde `StackView` sınıfı oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="a4c73-188">Add a call to the `InitializeImages` method in the `StackView` class constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="implementing-a-custom-renderer"></a><span data-ttu-id="a4c73-189">Özel oluşturucu uygulama</span><span class="sxs-lookup"><span data-stu-id="a4c73-189">Implementing a Custom Renderer</span></span>  
 <span data-ttu-id="a4c73-190">Çoğu öğeleri özelleştirebilirsiniz `StackView` my türeyen bir sınıf uygulama Denetim <xref:System.Windows.Forms.ToolStripRenderer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a4c73-190">You can customize most elements of the `StackView` control my implementing a class that derives from the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="a4c73-191">Bu yordamda, gerçekleştireceksiniz bir <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tutamacı özelleştirir ve gradyan arka planlar için çizer sınıfı <xref:System.Windows.Forms.ToolStripButton> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="a4c73-191">In this procedure, you will implement a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class that customizes the grip and draws gradient backgrounds for the <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>  
  
#### <a name="to-implement-a-custom-renderer"></a><span data-ttu-id="a4c73-192">Özel oluşturucu uygulamak için</span><span class="sxs-lookup"><span data-stu-id="a4c73-192">To implement a custom renderer</span></span>  
  
1.  <span data-ttu-id="a4c73-193">Aşağıdaki kodu ekleyin `StackView` denetim tanımı.</span><span class="sxs-lookup"><span data-stu-id="a4c73-193">Insert the following code into the `StackView` control definition.</span></span>  
  
     <span data-ttu-id="a4c73-194">Tanımı budur `StackRenderer` sınıfı, hangi geçersiz kılmaları <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, ve <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> özel görünüm oluşturmak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="a4c73-194">This is the definition for the `StackRenderer` class, which overrides the <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, and <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> methods to produce a custom appearance.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]  
  
2.  <span data-ttu-id="a4c73-195">İçinde `StackView` denetimin oluşturucusu, yeni bir örneğini oluşturmak `StackRenderer` sınıfı ve bu örneğine atadığınız `stackStrip` denetimin <xref:System.Windows.Forms.ToolStrip.Renderer%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a4c73-195">In the `StackView` control's constructor, create a new instance of the `StackRenderer` class and assign this instance to the `stackStrip` control's <xref:System.Windows.Forms.ToolStrip.Renderer%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="testing-the-stackview-control"></a><span data-ttu-id="a4c73-196">StackView denetim test etme</span><span class="sxs-lookup"><span data-stu-id="a4c73-196">Testing the StackView Control</span></span>  
 <span data-ttu-id="a4c73-197">`StackView` Denetim türer <xref:System.Windows.Forms.UserControl> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a4c73-197">The `StackView` control derives from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="a4c73-198">Bu nedenle, denetimle test edebilirsiniz **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="a4c73-198">Therefore, you can test the control with the **UserControl Test Container**.</span></span> <span data-ttu-id="a4c73-199">Daha fazla bilgi için bkz: [nasıl yapılır: bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="a4c73-199">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-the-stackview-control"></a><span data-ttu-id="a4c73-200">StackView denetimini sınamak için</span><span class="sxs-lookup"><span data-stu-id="a4c73-200">To test the StackView control</span></span>  
  
1.  <span data-ttu-id="a4c73-201">Projeyi derlemek ve başlatmak için F5 tuşuna basın **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="a4c73-201">Press F5 to build the project and start the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="a4c73-202">Düğmelerinin işaretçiyi `StackView` denetlemek ve ardından seçili durumu görünümünü görmek için bir düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a4c73-202">Move the pointer over the buttons of the `StackView` control, and then click a button to see the appearance of its selected state.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a4c73-203">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="a4c73-203">Next Steps</span></span>  
 <span data-ttu-id="a4c73-204">Bu kılavuzda, bir Office XP denetimini profesyonel görünüm ile yeniden kullanılabilir özel istemci denetimi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="a4c73-204">In this walkthrough, you have created a reusable custom client control with the professional appearance of an Office XP control.</span></span> <span data-ttu-id="a4c73-205">Kullanabileceğiniz <xref:System.Windows.Forms.ToolStrip> birçok başka amaçlarla denetimlerin ailesi:</span><span class="sxs-lookup"><span data-stu-id="a4c73-205">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="a4c73-206">İle denetimleri için kısayol menüleri oluşturma <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="a4c73-206">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="a4c73-207">Daha fazla bilgi için bkz: [ContextMenu bileşenine genel bakış](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a4c73-207">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="a4c73-208">Bir form ile otomatik olarak doldurulan bir standart menü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a4c73-208">Create a form with an automatically populated standard menu.</span></span> <span data-ttu-id="a4c73-209">Daha fazla bilgi için bkz: [izlenecek yol: bir forma standart menü öğeleri sağlama](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="a4c73-209">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
-   <span data-ttu-id="a4c73-210">Yerleştirme ile birden çok belge arabirimi (MDI) form oluşturma <xref:System.Windows.Forms.ToolStrip> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="a4c73-210">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="a4c73-211">Daha fazla bilgi için bkz: [nasıl yapılır: menü birleştirme ve ToolStrip denetimleri içeren MDI formu oluşturma](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="a4c73-211">For more information, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c73-212">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a4c73-212">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="a4c73-213">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="a4c73-213">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="a4c73-214">Nasıl yapılır: Bir Forma Standart Menü Öğeleri Sağlama</span><span class="sxs-lookup"><span data-stu-id="a4c73-214">How to: Provide Standard Menu Items to a Form</span></span>](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
