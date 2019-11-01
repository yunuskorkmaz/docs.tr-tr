---
title: "İzlenecek yol: Windows Forms'ta Tasarım Zamanında WPF İçeriğini Düzenleme"
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9062a3da9a6020762114702b6cce6b42414ab92d
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197449"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="87bf9-102">İzlenecek yol: tasarım zamanında Windows Forms WPF içeriğini düzenleme</span><span class="sxs-lookup"><span data-stu-id="87bf9-102">Walkthrough: Arrange WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="87bf9-103">Bu makalede, Windows Presentation Foundation (WPF) denetimlerini düzenlemek için bağlama ve yama çizgileri gibi Windows Forms düzen özelliklerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="87bf9-103">This article shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="87bf9-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="87bf9-104">Prerequisites</span></span>

<span data-ttu-id="87bf9-105">Bu yönergeyi tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="87bf9-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="87bf9-106">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="87bf9-106">Create the project</span></span>

<span data-ttu-id="87bf9-107">Visual Studio 'Yu açın ve Visual Basic veya görsel C# adlı `ArrangeElementHost`Windows Forms uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="87bf9-107">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>

> [!NOTE]
> <span data-ttu-id="87bf9-108">WPF içeriği barındırırken yalnızca C# ve Visual Basic projeleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="87bf9-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control"></a><span data-ttu-id="87bf9-109">WPF denetimini oluşturma</span><span class="sxs-lookup"><span data-stu-id="87bf9-109">Create the WPF control</span></span>

<span data-ttu-id="87bf9-110">Projeye bir WPF denetimi ekledikten sonra bunu form üzerinde düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87bf9-110">After you add a WPF control to the project, you can arrange it on the form.</span></span>

1. <span data-ttu-id="87bf9-111">Projeye yeni bir WPF <xref:System.Windows.Controls.UserControl> ekleyin.</span><span class="sxs-lookup"><span data-stu-id="87bf9-111">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="87bf9-112">Denetim türü için varsayılan adı kullanın, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="87bf9-112">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="87bf9-113">Daha fazla bilgi için bkz. [Izlenecek yol: tasarım zamanında Windows Forms yenı WPF Içeriği oluşturma](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="87bf9-113">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="87bf9-114">Tasarım görünümü ' de `UserControl1` ' nin seçili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="87bf9-114">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="87bf9-115">**Özellikler** penceresinde <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin değerini **200**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="87bf9-115">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="87bf9-116"><xref:System.Windows.Controls.Control.Background%2A> özelliğinin değerini **mavi**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="87bf9-116">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to **Blue**.</span></span>

5. <span data-ttu-id="87bf9-117">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="87bf9-117">Build the project.</span></span>

## <a name="host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="87bf9-118">Düzen panelinde WPF denetimleri barındırma</span><span class="sxs-lookup"><span data-stu-id="87bf9-118">Host WPF controls in a layout panel</span></span>

<span data-ttu-id="87bf9-119">Düzen panellerinde WPF denetimlerini, diğer Windows Forms denetimlerini kullandığınız şekilde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87bf9-119">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>

1. <span data-ttu-id="87bf9-120">Windows Form Tasarımcısı `Form1` açın.</span><span class="sxs-lookup"><span data-stu-id="87bf9-120">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="87bf9-121">**Araç kutusunda**bir <xref:System.Windows.Forms.TableLayoutPanel> denetimini form üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="87bf9-121">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>

3. <span data-ttu-id="87bf9-122"><xref:System.Windows.Forms.TableLayoutPanel> denetimin akıllı etiket panelinde **son satırı Kaldır**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="87bf9-122">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>

4. <span data-ttu-id="87bf9-123"><xref:System.Windows.Forms.TableLayoutPanel> denetimini daha büyük bir genişlik ve yükseklik olarak yeniden boyutlandırın.</span><span class="sxs-lookup"><span data-stu-id="87bf9-123">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>

5. <span data-ttu-id="87bf9-124">**Araç kutusunda**, <xref:System.Windows.Forms.TableLayoutPanel> denetiminin ilk hücresinde bir `UserControl1` örneği oluşturmak için `UserControl1` ' a çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="87bf9-124">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

   <span data-ttu-id="87bf9-125">`UserControl1` örneği, `elementHost1`adlı yeni bir <xref:System.Windows.Forms.Integration.ElementHost> denetiminde barındırılır.</span><span class="sxs-lookup"><span data-stu-id="87bf9-125">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

6. <span data-ttu-id="87bf9-126">**Araç kutusunda**, <xref:System.Windows.Forms.TableLayoutPanel> denetiminin ikinci hücresinde başka bir örnek oluşturmak için `UserControl1` ' a çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="87bf9-126">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="87bf9-127">**Belge Anahattı** penceresinde `tableLayoutPanel1`' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="87bf9-127">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span>

8. <span data-ttu-id="87bf9-128">**Özellikler** penceresinde, <xref:System.Windows.Forms.Control.Padding%2A> özelliğinin değerini **10, 10, 10, 10**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="87bf9-128">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to **10, 10, 10, 10**.</span></span>

   <span data-ttu-id="87bf9-129"><xref:System.Windows.Forms.Integration.ElementHost> denetimlerinin her ikisi de yeni düzene sığacak şekilde yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="87bf9-129">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>

## <a name="use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="87bf9-130">WPF denetimlerini hizalamak için dayama çizgileri kullanma</span><span class="sxs-lookup"><span data-stu-id="87bf9-130">Use snaplines to align WPF controls</span></span>

<span data-ttu-id="87bf9-131">Anlık görüntü çizgileri, bir formdaki denetimlerin kolay hizalamasını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="87bf9-131">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="87bf9-132">WPF denetimlerinizi de hizalamak için Snapın çizgilerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87bf9-132">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="87bf9-133">Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms denetimleri yerleştirme, yama çizgileri kullanarak](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="87bf9-133">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

1. <span data-ttu-id="87bf9-134">**Araç kutusundan**bir `UserControl1` örneğini form üzerine sürükleyin ve <xref:System.Windows.Forms.TableLayoutPanel> denetiminin altındaki alana yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="87bf9-134">From the **Toolbox**, drag an instance of `UserControl1` onto the form, and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

   <span data-ttu-id="87bf9-135">`UserControl1` örneği, `elementHost3`adlı yeni bir <xref:System.Windows.Forms.Integration.ElementHost> denetiminde barındırılır.</span><span class="sxs-lookup"><span data-stu-id="87bf9-135">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>

2. <span data-ttu-id="87bf9-136">Anlık görüntü çizgilerini kullanarak `elementHost3` sol kenarını <xref:System.Windows.Forms.TableLayoutPanel> denetiminin sol kenarıyla hizalayın.</span><span class="sxs-lookup"><span data-stu-id="87bf9-136">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

3. <span data-ttu-id="87bf9-137">Snaplines, boyut `elementHost3` <xref:System.Windows.Forms.TableLayoutPanel> denetimiyle aynı genişliğe sahip olacak şekilde kullanma.</span><span class="sxs-lookup"><span data-stu-id="87bf9-137">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

4. <span data-ttu-id="87bf9-138">Denetimler arasında bir merkez ek çizgi görünene kadar `elementHost3` <xref:System.Windows.Forms.TableLayoutPanel> denetimine doğru taşıyın.</span><span class="sxs-lookup"><span data-stu-id="87bf9-138">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>

5. <span data-ttu-id="87bf9-139">**Özellikler** penceresinde, Margin özelliğinin değerini **20, 20, 20, 20**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="87bf9-139">In the **Properties** window, set the value of the Margin property to **20, 20, 20, 20**.</span></span>

6. <span data-ttu-id="87bf9-140">Center Snapın satırı yeniden görünene kadar `elementHost3` <xref:System.Windows.Forms.TableLayoutPanel> denetiminden uzağa taşıyın.</span><span class="sxs-lookup"><span data-stu-id="87bf9-140">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="87bf9-141">Center Snapın çizgisi artık 20 ' nin bir kenar boşluğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="87bf9-141">The center snapline now indicates a margin of 20.</span></span>

7. <span data-ttu-id="87bf9-142">Sol kenarı `elementHost1`sol kenarıyla hizalanana kadar `elementHost3` sağa taşıyın.</span><span class="sxs-lookup"><span data-stu-id="87bf9-142">Move `elementHost3` to the right until its left edge aligns with the left edge of `elementHost1`.</span></span>

8. <span data-ttu-id="87bf9-143">Sağ kenarı `elementHost2`sağ kenarıyla hizalanana kadar `elementHost3` genişliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="87bf9-143">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>

## <a name="anchor-and-dock-wpf-controls"></a><span data-ttu-id="87bf9-144">WPF denetimlerini sabitleme ve yerleştirme</span><span class="sxs-lookup"><span data-stu-id="87bf9-144">Anchor and dock WPF controls</span></span>

<span data-ttu-id="87bf9-145">Bir form üzerinde barındırılan WPF denetimi, diğer Windows Forms denetimleriyle aynı sabitleme ve yerleştirme davranışına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="87bf9-145">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>

1. <span data-ttu-id="87bf9-146">`elementHost1`seçin.</span><span class="sxs-lookup"><span data-stu-id="87bf9-146">Select `elementHost1`.</span></span>

2. <span data-ttu-id="87bf9-147">**Özellikler** penceresinde, <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini **üst, alt, sol, sağ**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="87bf9-147">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>

3. <span data-ttu-id="87bf9-148"><xref:System.Windows.Forms.TableLayoutPanel> denetimini daha büyük bir boyutla yeniden boyutlandırın.</span><span class="sxs-lookup"><span data-stu-id="87bf9-148">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>

   <span data-ttu-id="87bf9-149">`elementHost1` denetim hücreyi dolduracak şekilde yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="87bf9-149">The `elementHost1` control resizes to fill the cell.</span></span>

4. <span data-ttu-id="87bf9-150">`elementHost2`seçin.</span><span class="sxs-lookup"><span data-stu-id="87bf9-150">Select `elementHost2`.</span></span>

5. <span data-ttu-id="87bf9-151">**Özellikler** penceresinde <xref:System.Windows.Forms.Control.Dock%2A> özelliğinin değerini <xref:System.Windows.Forms.DockStyle.Fill>olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="87bf9-151">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

   <span data-ttu-id="87bf9-152">`elementHost2` denetim hücreyi dolduracak şekilde yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="87bf9-152">The `elementHost2` control resizes to fill the cell.</span></span>

6. <span data-ttu-id="87bf9-153"><xref:System.Windows.Forms.TableLayoutPanel> denetimini seçin.</span><span class="sxs-lookup"><span data-stu-id="87bf9-153">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="87bf9-154"><xref:System.Windows.Forms.Control.Dock%2A> özelliğinin değerini <xref:System.Windows.Forms.DockStyle.Top>olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="87bf9-154">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>

8. <span data-ttu-id="87bf9-155">`elementHost3`seçin.</span><span class="sxs-lookup"><span data-stu-id="87bf9-155">Select `elementHost3`.</span></span>

9. <span data-ttu-id="87bf9-156"><xref:System.Windows.Forms.Control.Dock%2A> özelliğinin değerini <xref:System.Windows.Forms.DockStyle.Fill>olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="87bf9-156">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

   <span data-ttu-id="87bf9-157">`elementHost3` denetim, formdaki kalan alanı dolduracak şekilde yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="87bf9-157">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>

10. <span data-ttu-id="87bf9-158">Formu yeniden boyutlandırın.</span><span class="sxs-lookup"><span data-stu-id="87bf9-158">Resize the form.</span></span>

    <span data-ttu-id="87bf9-159">Her üç <xref:System.Windows.Forms.Integration.ElementHost> denetimi uygun şekilde yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="87bf9-159">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>

    <span data-ttu-id="87bf9-160">Daha fazla bilgi için bkz. [nasıl yapılır: bir TableLayoutPanel denetiminde alt denetimleri sabitleme ve yerleştirme](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span><span class="sxs-lookup"><span data-stu-id="87bf9-160">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="87bf9-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87bf9-161">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="87bf9-162">Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="87bf9-162">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="87bf9-163">Nasıl yapılır: Tasarım Zamanında Denetimi Formların Kenarlarına Hizalama</span><span class="sxs-lookup"><span data-stu-id="87bf9-163">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [<span data-ttu-id="87bf9-164">İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="87bf9-164">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="87bf9-165">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="87bf9-165">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="87bf9-166">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="87bf9-166">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="87bf9-167">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="87bf9-167">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
