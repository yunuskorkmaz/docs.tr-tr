---
title: "İzlenecek yol: Windows Forms'da Tasarım Zamanında WPF İçeriğini Düzenleme"
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
ms.openlocfilehash: a8f690438136450cb12dbcf5e17ddfcca617457e
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211440"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="7a26e-102">İzlenecek yol: Tasarım zamanında WPF içeriği Windows Forms'ta düzenleme</span><span class="sxs-lookup"><span data-stu-id="7a26e-102">Walkthrough: Arrange WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="7a26e-103">Bu izlenecek yol sabitleme ve dayama çizgileri, gibi Windows Forms düzeni özellikleri Windows Presentation Foundation (WPF) denetimleri düzenlemek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a26e-103">This walkthrough shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>

<span data-ttu-id="7a26e-104">Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="7a26e-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="7a26e-105">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7a26e-105">Create the project.</span></span>

- <span data-ttu-id="7a26e-106">WPF denetimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7a26e-106">Create the WPF control.</span></span>

- <span data-ttu-id="7a26e-107">Konak WPF denetimleri Düzen paneli içinde.</span><span class="sxs-lookup"><span data-stu-id="7a26e-107">Host WPF controls in a layout panel.</span></span>

- <span data-ttu-id="7a26e-108">WPF denetimleri hizalama dayama kullanın.</span><span class="sxs-lookup"><span data-stu-id="7a26e-108">Use snaplines to align WPF controls.</span></span>

- <span data-ttu-id="7a26e-109">Sabitleme ve WPF denetimleri yerleştirme.</span><span class="sxs-lookup"><span data-stu-id="7a26e-109">Anchor and dock WPF controls.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7a26e-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="7a26e-110">Prerequisites</span></span>

<span data-ttu-id="7a26e-111">Bu izlenecek yolu tamamlamak için Visual Studio ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="7a26e-111">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="7a26e-112">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7a26e-112">Create the project</span></span>

<span data-ttu-id="7a26e-113">Visual Studio'yu açın ve Visual Basic veya Visual içinde yeni bir Windows Forms uygulaması projesi oluşturma C# adlı `ArrangeElementHost`.</span><span class="sxs-lookup"><span data-stu-id="7a26e-113">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>

> [!NOTE]
> <span data-ttu-id="7a26e-114">WPF içeriği barındırma, yalnızca C# ve Visual Basic projelerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7a26e-114">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control"></a><span data-ttu-id="7a26e-115">WPF denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7a26e-115">Create the WPF control</span></span>

<span data-ttu-id="7a26e-116">Bir WPF denetiminde projeye ekledikten sonra form üzerinde düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a26e-116">After you add a WPF control to the project, you can arrange it on the form.</span></span>

1. <span data-ttu-id="7a26e-117">Yeni bir WPF ekleme <xref:System.Windows.Controls.UserControl> projeye.</span><span class="sxs-lookup"><span data-stu-id="7a26e-117">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="7a26e-118">Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="7a26e-118">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="7a26e-119">Daha fazla bilgi için [izlenecek yol: Yeni bir WPF içeriği Windows formlarında tasarım zamanında oluşturma](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="7a26e-119">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="7a26e-120">Tasarım görünümünde emin `UserControl1` seçilir.</span><span class="sxs-lookup"><span data-stu-id="7a26e-120">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="7a26e-121">Daha fazla bilgi için [nasıl yapılır: Seçin ve tasarım yüzeyine öğeleri Taşı](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="7a26e-121">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="7a26e-122">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.</span><span class="sxs-lookup"><span data-stu-id="7a26e-122">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

4. <span data-ttu-id="7a26e-123">Değerini <xref:System.Windows.Controls.Control.Background%2A> özelliğini `Blue`.</span><span class="sxs-lookup"><span data-stu-id="7a26e-123">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>

5. <span data-ttu-id="7a26e-124">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7a26e-124">Build the project.</span></span>

## <a name="hosting-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="7a26e-125">Bir düzen paneli içinde WPF denetimleri barındırma</span><span class="sxs-lookup"><span data-stu-id="7a26e-125">Hosting WPF Controls in a Layout Panel</span></span>
 <span data-ttu-id="7a26e-126">Düzen bölmeleri diğer Windows Forms denetimleri kullandığınız aynı şekilde WPF denetimleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a26e-126">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>

#### <a name="to-host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="7a26e-127">WPF barındırmak için bir düzen paneline denetler.</span><span class="sxs-lookup"><span data-stu-id="7a26e-127">To host WPF controls in a layout panel</span></span>

1. <span data-ttu-id="7a26e-128">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="7a26e-128">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="7a26e-129">İçinde **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.TableLayoutPanel> forma denetim.</span><span class="sxs-lookup"><span data-stu-id="7a26e-129">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>

3. <span data-ttu-id="7a26e-130">Üzerinde <xref:System.Windows.Forms.TableLayoutPanel> denetimin akıllı etiket paneli, select **son satırı Kaldır**.</span><span class="sxs-lookup"><span data-stu-id="7a26e-130">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>

4. <span data-ttu-id="7a26e-131">Yeniden boyutlandırma <xref:System.Windows.Forms.TableLayoutPanel> denetimine daha büyük genişliği ve yüksekliği.</span><span class="sxs-lookup"><span data-stu-id="7a26e-131">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>

5. <span data-ttu-id="7a26e-132">İçinde **araç kutusu**, çift `UserControl1` bir örneğini oluşturmak için `UserControl1` ilk hücresindeki <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7a26e-132">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

     <span data-ttu-id="7a26e-133">Örneğini `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="7a26e-133">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

6. <span data-ttu-id="7a26e-134">İçinde **araç kutusu**, çift `UserControl1` ikinci hücresinde başka bir örneğini oluşturmak için <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7a26e-134">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="7a26e-135">İçinde **belge anahattı** penceresinde `tableLayoutPanel1`.</span><span class="sxs-lookup"><span data-stu-id="7a26e-135">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span> <span data-ttu-id="7a26e-136">Daha fazla bilgi için [Belge Anahattı penceresi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/46xf4h0w(v=vs.100)#using-the-document-outline-window-for-silverlight-and-wpf).</span><span class="sxs-lookup"><span data-stu-id="7a26e-136">For more information, see [Document Outline Window](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/46xf4h0w(v=vs.100)#using-the-document-outline-window-for-silverlight-and-wpf).</span></span>

8. <span data-ttu-id="7a26e-137">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.Forms.Control.Padding%2A> özelliğini `10, 10, 10, 10`.</span><span class="sxs-lookup"><span data-stu-id="7a26e-137">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to `10, 10, 10, 10`.</span></span>

     <span data-ttu-id="7a26e-138">Her ikisi de <xref:System.Windows.Forms.Integration.ElementHost> denetimleri yeni düzene uyacak şekilde yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="7a26e-138">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>

## <a name="using-snaplines-to-align-wpf-controls"></a><span data-ttu-id="7a26e-139">Dayama çizgileri kullanarak WPF denetimleri hizalama</span><span class="sxs-lookup"><span data-stu-id="7a26e-139">Using Snaplines to Align WPF Controls</span></span>
 <span data-ttu-id="7a26e-140">Dayama çizgileri kolay bir form üzerinde denetimleri hizalama etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="7a26e-140">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="7a26e-141">Dayama çizgileri WPF denetimleri de hizalamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a26e-141">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="7a26e-142">Daha fazla bilgi için [izlenecek yol: Forms dayama çizgileri kullanarak Windows denetimleri düzenleme](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="7a26e-142">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

#### <a name="to-use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="7a26e-143">Dayama çizgileri WPF hizalamak için kullanılacağını denetler</span><span class="sxs-lookup"><span data-stu-id="7a26e-143">To use snaplines to align WPF controls</span></span>

1. <span data-ttu-id="7a26e-144">Gelen **araç kutusu**, örneği sürükleyin `UserControl1` forma ve alanı yerleştirin <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7a26e-144">From the **Toolbox**, drag an instance of `UserControl1` onto the form and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

     <span data-ttu-id="7a26e-145">Örneğini `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="7a26e-145">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>

2. <span data-ttu-id="7a26e-146">Dayama çizgileri kullanarak, sol kenarı hizalama `elementHost3` sol kenarı <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7a26e-146">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

3. <span data-ttu-id="7a26e-147">Dayama çizgileri kullanarak, boyut `elementHost3` aynı genişliğe <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7a26e-147">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

4. <span data-ttu-id="7a26e-148">Taşıma `elementHost3` doğru <xref:System.Windows.Forms.TableLayoutPanel> denetimler arasında merkezi snapline görünene kadar denetim.</span><span class="sxs-lookup"><span data-stu-id="7a26e-148">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>

5. <span data-ttu-id="7a26e-149">İçinde **özellikleri** penceresini ayarlamak için kenar boşluğu özelliğinin değeri `20, 20, 20, 20`.</span><span class="sxs-lookup"><span data-stu-id="7a26e-149">In the **Properties** window, set the value of the Margin property to `20, 20, 20, 20`.</span></span>

6. <span data-ttu-id="7a26e-150">Taşıma `elementHost3` UZAĞINIZDA <xref:System.Windows.Forms.TableLayoutPanel> merkezi snapline tekrar görünene kadar denetim.</span><span class="sxs-lookup"><span data-stu-id="7a26e-150">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="7a26e-151">Merkezi snapline şimdi 20 kenar boşluğu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a26e-151">The center snapline now indicates a margin of 20.</span></span>

7. <span data-ttu-id="7a26e-152">Taşıma `elementHost3` sol kenarı sol kenarı ile hizalar kadar sağa doğru `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="7a26e-152">Move `elementHost3` to the right, until its left edge aligns with the left edge of `elementHost1`.</span></span>

8. <span data-ttu-id="7a26e-153">Genişliğini değiştirme `elementHost3` öğenin sağ kenarı sağ kenarından hizalar kadar `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="7a26e-153">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>

## <a name="anchoring-and-docking-wpf-controls"></a><span data-ttu-id="7a26e-154">Sabitleme ve yerleştirme WPF denetimleri</span><span class="sxs-lookup"><span data-stu-id="7a26e-154">Anchoring and Docking WPF Controls</span></span>
 <span data-ttu-id="7a26e-155">Bir form üzerinde barındırılan bir WPF denetiminde aynı sabitleme ve diğer Windows Forms denetimleri yerleşik davranışını sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7a26e-155">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>

#### <a name="to-anchor-and-dock-wpf-controls"></a><span data-ttu-id="7a26e-156">Sabitleme ve yerleştirme WPF denetimleri için</span><span class="sxs-lookup"><span data-stu-id="7a26e-156">To anchor and dock WPF controls</span></span>

1. <span data-ttu-id="7a26e-157">`elementHost1` öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7a26e-157">Select `elementHost1`.</span></span>

2. <span data-ttu-id="7a26e-158">İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini **üst, alt, sol, sağ**.</span><span class="sxs-lookup"><span data-stu-id="7a26e-158">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>

3. <span data-ttu-id="7a26e-159">Yeniden boyutlandırma <xref:System.Windows.Forms.TableLayoutPanel> daha büyük bir boyuta denetimi.</span><span class="sxs-lookup"><span data-stu-id="7a26e-159">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>

     <span data-ttu-id="7a26e-160">`elementHost1` Denetimi hücreyi dolduracak şekilde yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="7a26e-160">The `elementHost1` control resizes to fill the cell.</span></span>

4. <span data-ttu-id="7a26e-161">`elementHost2` öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7a26e-161">Select `elementHost2`.</span></span>

5. <span data-ttu-id="7a26e-162">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="7a26e-162">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

     <span data-ttu-id="7a26e-163">`elementHost2` Denetimi hücreyi dolduracak şekilde yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="7a26e-163">The `elementHost2` control resizes to fill the cell.</span></span>

6. <span data-ttu-id="7a26e-164">Seçin <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7a26e-164">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="7a26e-165">Değerini kendi <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Top>.</span><span class="sxs-lookup"><span data-stu-id="7a26e-165">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>

8. <span data-ttu-id="7a26e-166">`elementHost3` öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7a26e-166">Select `elementHost3`.</span></span>

9. <span data-ttu-id="7a26e-167">Değerini kendi <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="7a26e-167">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

     <span data-ttu-id="7a26e-168">`elementHost3` Denetimi form üzerinde kalan alanı dolduracak şekilde yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="7a26e-168">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>

10. <span data-ttu-id="7a26e-169">Formu yeniden boyutlandırın.</span><span class="sxs-lookup"><span data-stu-id="7a26e-169">Resize the form.</span></span>

     <span data-ttu-id="7a26e-170">Üç <xref:System.Windows.Forms.Integration.ElementHost> denetimleri uygun şekilde yeniden boyutlandırın.</span><span class="sxs-lookup"><span data-stu-id="7a26e-170">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>

     <span data-ttu-id="7a26e-171">Daha fazla bilgi için [nasıl yapılır: TableLayoutPanel denetiminde alt denetimleri sabitleme ve yerleştirme](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span><span class="sxs-lookup"><span data-stu-id="7a26e-171">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7a26e-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a26e-172">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="7a26e-173">Nasıl yapılır: Sabitleme ve TableLayoutPanel denetiminde alt denetimleri yerleştirme</span><span class="sxs-lookup"><span data-stu-id="7a26e-173">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="7a26e-174">Nasıl yapılır: Tasarım zamanında denetimi formların kenarlarına hizalama</span><span class="sxs-lookup"><span data-stu-id="7a26e-174">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [<span data-ttu-id="7a26e-175">İzlenecek yol: Dayama çizgileri kullanarak Windows Forms'da denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="7a26e-175">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="7a26e-176">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="7a26e-176">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="7a26e-177">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="7a26e-177">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="7a26e-178">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="7a26e-178">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
