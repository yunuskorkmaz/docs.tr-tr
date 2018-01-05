---
title: "İzlenecek yol: Windows Forms'ta Tasarım Zamanında WPF İçeriğini Düzenleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c222e6f43bd595d264caeca2d9f79f7845f7f99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-arranging-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="bcca6-102">İzlenecek yol: Windows Forms'ta Tasarım Zamanında WPF İçeriğini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="bcca6-102">Walkthrough: Arranging WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="bcca6-103">Bu kılavuzda Windows Forms düzeni özellikleri sabitleme ve dayama çizgileri, gibi Windows Presentation Foundation (WPF) denetimlerini düzenlemek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bcca6-103">This walkthrough shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>  
  
 <span data-ttu-id="bcca6-104">Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="bcca6-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="bcca6-105">Projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bcca6-105">Create the project.</span></span>  
  
-   <span data-ttu-id="bcca6-106">WPF denetimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bcca6-106">Create the WPF control.</span></span>  
  
-   <span data-ttu-id="bcca6-107">Düzen panelinde konak WPF denetimleri.</span><span class="sxs-lookup"><span data-stu-id="bcca6-107">Host WPF controls in a layout panel.</span></span>  
  
-   <span data-ttu-id="bcca6-108">WPF denetimleri hizalamak için kullanım dayama çizgileri.</span><span class="sxs-lookup"><span data-stu-id="bcca6-108">Use snaplines to align WPF controls.</span></span>  
  
-   <span data-ttu-id="bcca6-109">Sabitleme ve yerleştirme WPF denetimleri.</span><span class="sxs-lookup"><span data-stu-id="bcca6-109">Anchor and dock WPF controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bcca6-110">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="bcca6-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="bcca6-111">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="bcca6-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="bcca6-112">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="bcca6-112">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="bcca6-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="bcca6-113">Prerequisites</span></span>  
 <span data-ttu-id="bcca6-114">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="bcca6-114">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="bcca6-115">.</span><span class="sxs-lookup"><span data-stu-id="bcca6-115">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="bcca6-116">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bcca6-116">Creating the Project</span></span>  
 <span data-ttu-id="bcca6-117">Windows Forms projesi oluşturmak için ilk adımdır bakın.</span><span class="sxs-lookup"><span data-stu-id="bcca6-117">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bcca6-118">WPF içeriği barındırma, yalnızca C# ve Visual Basic projeleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="bcca6-118">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="bcca6-119">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="bcca6-119">To create the project</span></span>  
  
-   <span data-ttu-id="bcca6-120">Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `ArrangeElementHost`.</span><span class="sxs-lookup"><span data-stu-id="bcca6-120">Create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>  
  
## <a name="creating-the-wpf-control"></a><span data-ttu-id="bcca6-121">WPF denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="bcca6-121">Creating the WPF Control</span></span>  
 <span data-ttu-id="bcca6-122">Projeye bir WPF denetimi ekledikten sonra formdaki düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bcca6-122">After you add a WPF control to the project, you can arrange it on the form.</span></span>  
  
#### <a name="to-create-wpf-controls"></a><span data-ttu-id="bcca6-123">WPF denetimleri oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="bcca6-123">To create WPF controls</span></span>  
  
1.  <span data-ttu-id="bcca6-124">Yeni bir WPF eklemek <xref:System.Windows.Controls.UserControl> projeye.</span><span class="sxs-lookup"><span data-stu-id="bcca6-124">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="bcca6-125">Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="bcca6-125">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="bcca6-126">Daha fazla bilgi için bkz: [izlenecek yol: oluşturma yeni WPF içeriği Windows formlarında tasarım zamanında](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="bcca6-126">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="bcca6-127">Tasarım görünümü içinde olduğundan emin olun `UserControl1` seçilir.</span><span class="sxs-lookup"><span data-stu-id="bcca6-127">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="bcca6-128">Daha fazla bilgi için bkz: [nasıl yapılır: seçin ve tasarım yüzeyine taşıma öğelerde](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="bcca6-128">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="bcca6-129">İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.</span><span class="sxs-lookup"><span data-stu-id="bcca6-129">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="bcca6-130">Değerini <xref:System.Windows.Controls.Control.Background%2A> özelliğine `Blue`.</span><span class="sxs-lookup"><span data-stu-id="bcca6-130">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
5.  <span data-ttu-id="bcca6-131">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bcca6-131">Build the project.</span></span>  
  
## <a name="hosting-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="bcca6-132">WPF denetimlerini Düzen panelinde barındırma</span><span class="sxs-lookup"><span data-stu-id="bcca6-132">Hosting WPF Controls in a Layout Panel</span></span>  
 <span data-ttu-id="bcca6-133">WPF denetimleri Düzen panelleri diğer Windows Forms denetimleri kullandığınız şekilde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bcca6-133">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>  
  
#### <a name="to-host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="bcca6-134">WPF barındırmak için bir düzen panelinde denetler.</span><span class="sxs-lookup"><span data-stu-id="bcca6-134">To host WPF controls in a layout panel</span></span>  
  
1.  <span data-ttu-id="bcca6-135">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="bcca6-135">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="bcca6-136">İçinde **araç**, sürükleyin bir <xref:System.Windows.Forms.TableLayoutPanel> forma denetim.</span><span class="sxs-lookup"><span data-stu-id="bcca6-136">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>  
  
3.  <span data-ttu-id="bcca6-137">Üzerinde <xref:System.Windows.Forms.TableLayoutPanel> denetimin akıllı etiket paneli, select **son satırı Kaldır**.</span><span class="sxs-lookup"><span data-stu-id="bcca6-137">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>  
  
4.  <span data-ttu-id="bcca6-138">Yeniden boyutlandırma <xref:System.Windows.Forms.TableLayoutPanel> denetimine büyük genişlik ve yükseklik.</span><span class="sxs-lookup"><span data-stu-id="bcca6-138">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>  
  
5.  <span data-ttu-id="bcca6-139">İçinde **araç**, çift `UserControl1` bir örneğini oluşturmak için `UserControl1` ilk hücrenin <xref:System.Windows.Forms.TableLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="bcca6-139">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
     <span data-ttu-id="bcca6-140">Örneğinin `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="bcca6-140">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
6.  <span data-ttu-id="bcca6-141">İçinde **araç**, çift `UserControl1` ikinci hücresinde başka bir örnek oluşturmak için <xref:System.Windows.Forms.TableLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="bcca6-141">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
7.  <span data-ttu-id="bcca6-142">İçinde **belge anahattı** penceresinde, seçin `tableLayoutPanel1`.</span><span class="sxs-lookup"><span data-stu-id="bcca6-142">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span> <span data-ttu-id="bcca6-143">Daha fazla bilgi için bkz: [Belge Anahattı penceresi](http://msdn.microsoft.com/en-us/9054f2bc-f6f8-4242-9fe0-be71089b12f8).</span><span class="sxs-lookup"><span data-stu-id="bcca6-143">For more information, see [Document Outline Window](http://msdn.microsoft.com/en-us/9054f2bc-f6f8-4242-9fe0-be71089b12f8).</span></span>  
  
8.  <span data-ttu-id="bcca6-144">İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.Forms.Control.Padding%2A> özelliğine `10, 10, 10, 10`.</span><span class="sxs-lookup"><span data-stu-id="bcca6-144">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to `10, 10, 10, 10`.</span></span>  
  
     <span data-ttu-id="bcca6-145">Her ikisi de <xref:System.Windows.Forms.Integration.ElementHost> denetimleri yeni düzen sığması için yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="bcca6-145">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>  
  
## <a name="using-snaplines-to-align-wpf-controls"></a><span data-ttu-id="bcca6-146">Dayama çizgileri kullanarak WPF denetimleri hizalama</span><span class="sxs-lookup"><span data-stu-id="bcca6-146">Using Snaplines to Align WPF Controls</span></span>  
 <span data-ttu-id="bcca6-147">Dayama çizgileri kolay bir form üzerinde denetimleri hizalama etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="bcca6-147">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="bcca6-148">Dayama çizgileri WPF denetimleri de hizalamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bcca6-148">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="bcca6-149">Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms kullanarak dayama çizgileri düzenleme denetimlerinde](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="bcca6-149">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
#### <a name="to-use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="bcca6-150">Dayama çizgileri WPF hizalamak için kullanmak üzere denetler</span><span class="sxs-lookup"><span data-stu-id="bcca6-150">To use snaplines to align WPF controls</span></span>  
  
1.  <span data-ttu-id="bcca6-151">Gelen **araç**, bir örneğini sürükleyin `UserControl1` forma ve alanda yerleştirin <xref:System.Windows.Forms.TableLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="bcca6-151">From the **Toolbox**, drag an instance of `UserControl1` onto the form and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
     <span data-ttu-id="bcca6-152">Örneğinin `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="bcca6-152">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>  
  
2.  <span data-ttu-id="bcca6-153">Dayama çizgileri kullanarak, sol hizalar `elementHost3` sol kenarı ile <xref:System.Windows.Forms.TableLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="bcca6-153">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
3.  <span data-ttu-id="bcca6-154">Dayama çizgileri kullanarak, boyut `elementHost3` aynı genişliğe <xref:System.Windows.Forms.TableLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="bcca6-154">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
4.  <span data-ttu-id="bcca6-155">Taşıma `elementHost3` doğru <xref:System.Windows.Forms.TableLayoutPanel> merkezi snapline arasında denetimleri görünene kadar denetim.</span><span class="sxs-lookup"><span data-stu-id="bcca6-155">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>  
  
5.  <span data-ttu-id="bcca6-156">İçinde **özellikleri** penceresinde ayarlamak için kenar boşluğu özelliğinin değeri `20, 20, 20, 20`.</span><span class="sxs-lookup"><span data-stu-id="bcca6-156">In the **Properties** window, set the value of the Margin property to `20, 20, 20, 20`.</span></span>  
  
6.  <span data-ttu-id="bcca6-157">Taşıma `elementHost3` merkezden <xref:System.Windows.Forms.TableLayoutPanel> merkezi snapline yeniden görünene kadar denetim.</span><span class="sxs-lookup"><span data-stu-id="bcca6-157">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="bcca6-158">Merkezi snapline şimdi 20 kenar boşluğu belirtir.</span><span class="sxs-lookup"><span data-stu-id="bcca6-158">The center snapline now indicates a margin of 20.</span></span>  
  
7.  <span data-ttu-id="bcca6-159">Taşıma `elementHost3` sol kenarı sol ucuyla hizalar kadar sağa `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="bcca6-159">Move `elementHost3` to the right, until its left edge aligns with the left edge of `elementHost1`.</span></span>  
  
8.  <span data-ttu-id="bcca6-160">Genişliğini değiştirme `elementHost3` sağ kenarı sağ ucuyla hizalar kadar `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="bcca6-160">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>  
  
## <a name="anchoring-and-docking-wpf-controls"></a><span data-ttu-id="bcca6-161">Sabitleme ve WPF denetimleri yerleştirme</span><span class="sxs-lookup"><span data-stu-id="bcca6-161">Anchoring and Docking WPF Controls</span></span>  
 <span data-ttu-id="bcca6-162">Bir form üzerinde barındırılan bir WPF denetimi aynı sabitleme ve diğer Windows Forms denetimleri davranışı yerleştirme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bcca6-162">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>  
  
#### <a name="to-anchor-and-dock-wpf-controls"></a><span data-ttu-id="bcca6-163">Sabitleme ve yerleştirme WPF denetimleri için</span><span class="sxs-lookup"><span data-stu-id="bcca6-163">To anchor and dock WPF controls</span></span>  
  
1.  <span data-ttu-id="bcca6-164">Seçin `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="bcca6-164">Select `elementHost1`.</span></span>  
  
2.  <span data-ttu-id="bcca6-165">İçinde **özellikleri** penceresindeki ayarlayın <xref:System.Windows.Forms.Control.Anchor%2A> özelliğine **üst, alt, sol, sağ**.</span><span class="sxs-lookup"><span data-stu-id="bcca6-165">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>  
  
3.  <span data-ttu-id="bcca6-166">Yeniden boyutlandırma <xref:System.Windows.Forms.TableLayoutPanel> daha büyük bir boyuta denetim.</span><span class="sxs-lookup"><span data-stu-id="bcca6-166">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>  
  
     <span data-ttu-id="bcca6-167">`elementHost1` Denetimi hücre dolduracak şekilde yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="bcca6-167">The `elementHost1` control resizes to fill the cell.</span></span>  
  
4.  <span data-ttu-id="bcca6-168">Seçin `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="bcca6-168">Select `elementHost2`.</span></span>  
  
5.  <span data-ttu-id="bcca6-169">İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="bcca6-169">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
     <span data-ttu-id="bcca6-170">`elementHost2` Denetimi hücre dolduracak şekilde yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="bcca6-170">The `elementHost2` control resizes to fill the cell.</span></span>  
  
6.  <span data-ttu-id="bcca6-171">Seçin <xref:System.Windows.Forms.TableLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="bcca6-171">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
7.  <span data-ttu-id="bcca6-172">Değerini kendi <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Top>.</span><span class="sxs-lookup"><span data-stu-id="bcca6-172">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>  
  
8.  <span data-ttu-id="bcca6-173">Seçin `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="bcca6-173">Select `elementHost3`.</span></span>  
  
9. <span data-ttu-id="bcca6-174">Değerini kendi <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="bcca6-174">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
     <span data-ttu-id="bcca6-175">`elementHost3` Denetimi formdaki kalan alanı dolduracak şekilde yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="bcca6-175">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>  
  
10. <span data-ttu-id="bcca6-176">Formu yeniden boyutlandırın.</span><span class="sxs-lookup"><span data-stu-id="bcca6-176">Resize the form.</span></span>  
  
     <span data-ttu-id="bcca6-177">Üç <xref:System.Windows.Forms.Integration.ElementHost> denetimleri uygun şekilde yeniden boyutlandırın.</span><span class="sxs-lookup"><span data-stu-id="bcca6-177">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>  
  
     <span data-ttu-id="bcca6-178">Daha fazla bilgi için bkz: [nasıl yapılır: bağlantı ve bir TableLayoutPanel denetiminde alt denetimleri yerleştirme](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span><span class="sxs-lookup"><span data-stu-id="bcca6-178">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcca6-179">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bcca6-179">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="bcca6-180">Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="bcca6-180">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="bcca6-181">Nasıl yapılır: Tasarım Zamanında Denetimi Formların Kenarlarına Hizalama</span><span class="sxs-lookup"><span data-stu-id="bcca6-181">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [<span data-ttu-id="bcca6-182">İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="bcca6-182">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="bcca6-183">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="bcca6-183">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="bcca6-184">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="bcca6-184">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="bcca6-185">WPF Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="bcca6-185">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
