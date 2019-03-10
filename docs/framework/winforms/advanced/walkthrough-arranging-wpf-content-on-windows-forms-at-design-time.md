---
title: "İzlenecek yol: Tasarım zamanında WPF içeriğini Windows Forms'ta düzenleme"
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
ms.openlocfilehash: 0738d1522c8ade8f026a3bf69fbff0bc2c2d6d85
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712467"
---
# <a name="walkthrough-arranging-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="7edf4-102">İzlenecek yol: Tasarım zamanında WPF içeriğini Windows Forms'ta düzenleme</span><span class="sxs-lookup"><span data-stu-id="7edf4-102">Walkthrough: Arranging WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="7edf4-103">Bu izlenecek yol sabitleme ve dayama çizgileri, gibi Windows Forms düzeni özellikleri Windows Presentation Foundation (WPF) denetimleri düzenlemek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7edf4-103">This walkthrough shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>

 <span data-ttu-id="7edf4-104">Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="7edf4-104">In this walkthrough, you perform the following tasks:</span></span>

-   <span data-ttu-id="7edf4-105">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7edf4-105">Create the project.</span></span>

-   <span data-ttu-id="7edf4-106">WPF denetimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7edf4-106">Create the WPF control.</span></span>

-   <span data-ttu-id="7edf4-107">Konak WPF denetimleri Düzen paneli içinde.</span><span class="sxs-lookup"><span data-stu-id="7edf4-107">Host WPF controls in a layout panel.</span></span>

-   <span data-ttu-id="7edf4-108">WPF denetimleri hizalama dayama kullanın.</span><span class="sxs-lookup"><span data-stu-id="7edf4-108">Use snaplines to align WPF controls.</span></span>

-   <span data-ttu-id="7edf4-109">Sabitleme ve WPF denetimleri yerleştirme.</span><span class="sxs-lookup"><span data-stu-id="7edf4-109">Anchor and dock WPF controls.</span></span>

> [!NOTE]
>  <span data-ttu-id="7edf4-110">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="7edf4-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7edf4-111">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="7edf4-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7edf4-112">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="7edf4-112">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7edf4-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="7edf4-113">Prerequisites</span></span>  
 <span data-ttu-id="7edf4-114">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="7edf4-114">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="7edf4-115">Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="7edf4-115">Visual Studio 2012.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="7edf4-116">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7edf4-116">Creating the Project</span></span>  
 <span data-ttu-id="7edf4-117">İlk adım Windows Forms projesi oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="7edf4-117">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7edf4-118">WPF içeriği barındırma, yalnızca C# ve Visual Basic projelerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7edf4-118">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="7edf4-119">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7edf4-119">To create the project</span></span>  
  
-   <span data-ttu-id="7edf4-120">Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `ArrangeElementHost`.</span><span class="sxs-lookup"><span data-stu-id="7edf4-120">Create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>  
  
## <a name="creating-the-wpf-control"></a><span data-ttu-id="7edf4-121">WPF denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7edf4-121">Creating the WPF Control</span></span>  
 <span data-ttu-id="7edf4-122">Bir WPF denetiminde projeye ekledikten sonra form üzerinde düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7edf4-122">After you add a WPF control to the project, you can arrange it on the form.</span></span>  
  
#### <a name="to-create-wpf-controls"></a><span data-ttu-id="7edf4-123">WPF denetimleri oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7edf4-123">To create WPF controls</span></span>  
  
1.  <span data-ttu-id="7edf4-124">Yeni bir WPF ekleme <xref:System.Windows.Controls.UserControl> projeye.</span><span class="sxs-lookup"><span data-stu-id="7edf4-124">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="7edf4-125">Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="7edf4-125">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="7edf4-126">Daha fazla bilgi için [izlenecek yol: Yeni bir WPF içeriği Windows formlarında tasarım zamanında oluşturma](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="7edf4-126">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="7edf4-127">Tasarım görünümünde emin `UserControl1` seçilir.</span><span class="sxs-lookup"><span data-stu-id="7edf4-127">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="7edf4-128">Daha fazla bilgi için [nasıl yapılır: Seçin ve tasarım yüzeyine öğeleri Taşı](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="7edf4-128">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>  
  
3.  <span data-ttu-id="7edf4-129">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.</span><span class="sxs-lookup"><span data-stu-id="7edf4-129">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="7edf4-130">Değerini <xref:System.Windows.Controls.Control.Background%2A> özelliğini `Blue`.</span><span class="sxs-lookup"><span data-stu-id="7edf4-130">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
5.  <span data-ttu-id="7edf4-131">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7edf4-131">Build the project.</span></span>  
  
## <a name="hosting-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="7edf4-132">Bir düzen paneli içinde WPF denetimleri barındırma</span><span class="sxs-lookup"><span data-stu-id="7edf4-132">Hosting WPF Controls in a Layout Panel</span></span>  
 <span data-ttu-id="7edf4-133">Düzen bölmeleri diğer Windows Forms denetimleri kullandığınız aynı şekilde WPF denetimleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7edf4-133">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>  
  
#### <a name="to-host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="7edf4-134">WPF barındırmak için bir düzen paneline denetler.</span><span class="sxs-lookup"><span data-stu-id="7edf4-134">To host WPF controls in a layout panel</span></span>  
  
1.  <span data-ttu-id="7edf4-135">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="7edf4-135">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="7edf4-136">İçinde **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.TableLayoutPanel> forma denetim.</span><span class="sxs-lookup"><span data-stu-id="7edf4-136">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>  
  
3.  <span data-ttu-id="7edf4-137">Üzerinde <xref:System.Windows.Forms.TableLayoutPanel> denetimin akıllı etiket paneli, select **son satırı Kaldır**.</span><span class="sxs-lookup"><span data-stu-id="7edf4-137">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>  
  
4.  <span data-ttu-id="7edf4-138">Yeniden boyutlandırma <xref:System.Windows.Forms.TableLayoutPanel> denetimine daha büyük genişliği ve yüksekliği.</span><span class="sxs-lookup"><span data-stu-id="7edf4-138">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>  
  
5.  <span data-ttu-id="7edf4-139">İçinde **araç kutusu**, çift `UserControl1` bir örneğini oluşturmak için `UserControl1` ilk hücresindeki <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7edf4-139">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
     <span data-ttu-id="7edf4-140">Örneğini `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="7edf4-140">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
6.  <span data-ttu-id="7edf4-141">İçinde **araç kutusu**, çift `UserControl1` ikinci hücresinde başka bir örneğini oluşturmak için <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7edf4-141">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
7.  <span data-ttu-id="7edf4-142">İçinde **belge anahattı** penceresinde `tableLayoutPanel1`.</span><span class="sxs-lookup"><span data-stu-id="7edf4-142">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span> <span data-ttu-id="7edf4-143">Daha fazla bilgi için [Belge Anahattı penceresi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/46xf4h0w(v=vs.100)#using-the-document-outline-window-for-silverlight-and-wpf).</span><span class="sxs-lookup"><span data-stu-id="7edf4-143">For more information, see [Document Outline Window](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/46xf4h0w(v=vs.100)#using-the-document-outline-window-for-silverlight-and-wpf).</span></span>  
  
8.  <span data-ttu-id="7edf4-144">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.Forms.Control.Padding%2A> özelliğini `10, 10, 10, 10`.</span><span class="sxs-lookup"><span data-stu-id="7edf4-144">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to `10, 10, 10, 10`.</span></span>  
  
     <span data-ttu-id="7edf4-145">Her ikisi de <xref:System.Windows.Forms.Integration.ElementHost> denetimleri yeni düzene uyacak şekilde yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="7edf4-145">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>  
  
## <a name="using-snaplines-to-align-wpf-controls"></a><span data-ttu-id="7edf4-146">Dayama çizgileri kullanarak WPF denetimleri hizalama</span><span class="sxs-lookup"><span data-stu-id="7edf4-146">Using Snaplines to Align WPF Controls</span></span>  
 <span data-ttu-id="7edf4-147">Dayama çizgileri kolay bir form üzerinde denetimleri hizalama etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="7edf4-147">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="7edf4-148">Dayama çizgileri WPF denetimleri de hizalamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7edf4-148">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="7edf4-149">Daha fazla bilgi için [izlenecek yol: Forms dayama çizgileri kullanarak Windows denetimleri düzenleme](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="7edf4-149">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
#### <a name="to-use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="7edf4-150">Dayama çizgileri WPF hizalamak için kullanılacağını denetler</span><span class="sxs-lookup"><span data-stu-id="7edf4-150">To use snaplines to align WPF controls</span></span>  
  
1.  <span data-ttu-id="7edf4-151">Gelen **araç kutusu**, örneği sürükleyin `UserControl1` forma ve alanı yerleştirin <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7edf4-151">From the **Toolbox**, drag an instance of `UserControl1` onto the form and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
     <span data-ttu-id="7edf4-152">Örneğini `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="7edf4-152">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>  
  
2.  <span data-ttu-id="7edf4-153">Dayama çizgileri kullanarak, sol kenarı hizalama `elementHost3` sol kenarı <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7edf4-153">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
3.  <span data-ttu-id="7edf4-154">Dayama çizgileri kullanarak, boyut `elementHost3` aynı genişliğe <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7edf4-154">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
4.  <span data-ttu-id="7edf4-155">Taşıma `elementHost3` doğru <xref:System.Windows.Forms.TableLayoutPanel> denetimler arasında merkezi snapline görünene kadar denetim.</span><span class="sxs-lookup"><span data-stu-id="7edf4-155">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>  
  
5.  <span data-ttu-id="7edf4-156">İçinde **özellikleri** penceresini ayarlamak için kenar boşluğu özelliğinin değeri `20, 20, 20, 20`.</span><span class="sxs-lookup"><span data-stu-id="7edf4-156">In the **Properties** window, set the value of the Margin property to `20, 20, 20, 20`.</span></span>  
  
6.  <span data-ttu-id="7edf4-157">Taşıma `elementHost3` UZAĞINIZDA <xref:System.Windows.Forms.TableLayoutPanel> merkezi snapline tekrar görünene kadar denetim.</span><span class="sxs-lookup"><span data-stu-id="7edf4-157">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="7edf4-158">Merkezi snapline şimdi 20 kenar boşluğu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7edf4-158">The center snapline now indicates a margin of 20.</span></span>  
  
7.  <span data-ttu-id="7edf4-159">Taşıma `elementHost3` sol kenarı sol kenarı ile hizalar kadar sağa doğru `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="7edf4-159">Move `elementHost3` to the right, until its left edge aligns with the left edge of `elementHost1`.</span></span>  
  
8.  <span data-ttu-id="7edf4-160">Genişliğini değiştirme `elementHost3` öğenin sağ kenarı sağ kenarından hizalar kadar `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="7edf4-160">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>  
  
## <a name="anchoring-and-docking-wpf-controls"></a><span data-ttu-id="7edf4-161">Sabitleme ve yerleştirme WPF denetimleri</span><span class="sxs-lookup"><span data-stu-id="7edf4-161">Anchoring and Docking WPF Controls</span></span>  
 <span data-ttu-id="7edf4-162">Bir form üzerinde barındırılan bir WPF denetiminde aynı sabitleme ve diğer Windows Forms denetimleri yerleşik davranışını sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7edf4-162">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>  
  
#### <a name="to-anchor-and-dock-wpf-controls"></a><span data-ttu-id="7edf4-163">Sabitleme ve yerleştirme WPF denetimleri için</span><span class="sxs-lookup"><span data-stu-id="7edf4-163">To anchor and dock WPF controls</span></span>  
  
1.  <span data-ttu-id="7edf4-164">`elementHost1` öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7edf4-164">Select `elementHost1`.</span></span>  
  
2.  <span data-ttu-id="7edf4-165">İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini **üst, alt, sol, sağ**.</span><span class="sxs-lookup"><span data-stu-id="7edf4-165">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>  
  
3.  <span data-ttu-id="7edf4-166">Yeniden boyutlandırma <xref:System.Windows.Forms.TableLayoutPanel> daha büyük bir boyuta denetimi.</span><span class="sxs-lookup"><span data-stu-id="7edf4-166">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>  
  
     <span data-ttu-id="7edf4-167">`elementHost1` Denetimi hücreyi dolduracak şekilde yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="7edf4-167">The `elementHost1` control resizes to fill the cell.</span></span>  
  
4.  <span data-ttu-id="7edf4-168">`elementHost2` öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7edf4-168">Select `elementHost2`.</span></span>  
  
5.  <span data-ttu-id="7edf4-169">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="7edf4-169">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
     <span data-ttu-id="7edf4-170">`elementHost2` Denetimi hücreyi dolduracak şekilde yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="7edf4-170">The `elementHost2` control resizes to fill the cell.</span></span>  
  
6.  <span data-ttu-id="7edf4-171">Seçin <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7edf4-171">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
7.  <span data-ttu-id="7edf4-172">Değerini kendi <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Top>.</span><span class="sxs-lookup"><span data-stu-id="7edf4-172">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>  
  
8.  <span data-ttu-id="7edf4-173">`elementHost3` öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7edf4-173">Select `elementHost3`.</span></span>  
  
9. <span data-ttu-id="7edf4-174">Değerini kendi <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="7edf4-174">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
     <span data-ttu-id="7edf4-175">`elementHost3` Denetimi form üzerinde kalan alanı dolduracak şekilde yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="7edf4-175">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>  
  
10. <span data-ttu-id="7edf4-176">Formu yeniden boyutlandırın.</span><span class="sxs-lookup"><span data-stu-id="7edf4-176">Resize the form.</span></span>  
  
     <span data-ttu-id="7edf4-177">Üç <xref:System.Windows.Forms.Integration.ElementHost> denetimleri uygun şekilde yeniden boyutlandırın.</span><span class="sxs-lookup"><span data-stu-id="7edf4-177">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>  
  
     <span data-ttu-id="7edf4-178">Daha fazla bilgi için [nasıl yapılır: TableLayoutPanel denetiminde alt denetimleri sabitleme ve yerleştirme](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span><span class="sxs-lookup"><span data-stu-id="7edf4-178">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7edf4-179">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7edf4-179">See also</span></span>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="7edf4-180">Nasıl yapılır: Sabitleme ve TableLayoutPanel denetiminde alt denetimleri yerleştirme</span><span class="sxs-lookup"><span data-stu-id="7edf4-180">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="7edf4-181">Nasıl yapılır: Tasarım zamanında denetimi formların kenarlarına hizalama</span><span class="sxs-lookup"><span data-stu-id="7edf4-181">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [<span data-ttu-id="7edf4-182">İzlenecek yol: Dayama çizgileri kullanarak Windows Forms'da denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="7edf4-182">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="7edf4-183">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="7edf4-183">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="7edf4-184">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="7edf4-184">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="7edf4-185">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="7edf4-185">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
