---
title: "İzlenecek yol: Windows Formlarında Tasarım Zamanında WPF İçeriği Atama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0fa9e40a0a32d0bc9484a86da0f94d62f5c25aa7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-assigning-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="cbf79-102">İzlenecek yol: Windows Formlarında Tasarım Zamanında WPF İçeriği Atama</span><span class="sxs-lookup"><span data-stu-id="cbf79-102">Walkthrough: Assigning WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="cbf79-103">Bu kılavuz, Windows Presentation Foundation (WPF) denetim türlerini formunuzda görüntülemek istediğinizi seçmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="cbf79-103">This walkthrough show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="cbf79-104">Projenizde dahil tüm WPF denetim türlerini seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbf79-104">You can select any WPF control types which are included in your project.</span></span>  
  
 <span data-ttu-id="cbf79-105">Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="cbf79-105">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="cbf79-106">Projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cbf79-106">Create the project.</span></span>  
  
-   <span data-ttu-id="cbf79-107">WPF denetim türlerini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cbf79-107">Create the WPF control types.</span></span>  
  
-   <span data-ttu-id="cbf79-108">WPF denetimleri seçin.</span><span class="sxs-lookup"><span data-stu-id="cbf79-108">Select WPF controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cbf79-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="cbf79-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="cbf79-110">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="cbf79-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="cbf79-111">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="cbf79-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cbf79-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="cbf79-112">Prerequisites</span></span>  
 <span data-ttu-id="cbf79-113">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="cbf79-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="cbf79-114">.</span><span class="sxs-lookup"><span data-stu-id="cbf79-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="cbf79-115">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cbf79-115">Creating the Project</span></span>  
 <span data-ttu-id="cbf79-116">Windows Forms projesi oluşturmak için ilk adımdır bakın.</span><span class="sxs-lookup"><span data-stu-id="cbf79-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cbf79-117">WPF içeriği barındırma, yalnızca C# ve Visual Basic projeleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="cbf79-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="cbf79-118">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="cbf79-118">To create the project</span></span>  
  
-   <span data-ttu-id="cbf79-119">Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `SelectingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="cbf79-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="cbf79-120">WPF denetim türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="cbf79-120">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="cbf79-121">WPF denetim türleri projeye ekledikten sonra bunları farklı barındırabilir <xref:System.Windows.Forms.Integration.ElementHost> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="cbf79-121">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="cbf79-122">WPF denetim türleri oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="cbf79-122">To create WPF control types</span></span>  
  
1.  <span data-ttu-id="cbf79-123">Yeni bir WPF eklemek <xref:System.Windows.Controls.UserControl> çözüme proje.</span><span class="sxs-lookup"><span data-stu-id="cbf79-123">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="cbf79-124">Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="cbf79-124">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="cbf79-125">Daha fazla bilgi için bkz: [izlenecek yol: oluşturma yeni WPF içeriği Windows formlarında tasarım zamanında](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="cbf79-125">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="cbf79-126">Tasarım görünümü içinde olduğundan emin olun `UserControl1` seçilir.</span><span class="sxs-lookup"><span data-stu-id="cbf79-126">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="cbf79-127">Daha fazla bilgi için bkz: [nasıl yapılır: seçin ve tasarım yüzeyine taşıma öğelerde](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="cbf79-127">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="cbf79-128">İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.</span><span class="sxs-lookup"><span data-stu-id="cbf79-128">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="cbf79-129">Ekleme bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetimini <xref:System.Windows.Controls.UserControl> ve değeri ayarlayın <xref:System.Windows.Controls.TextBox.Text%2A> özelliğine **barındırılan içerik**.</span><span class="sxs-lookup"><span data-stu-id="cbf79-129">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>  
  
5.  <span data-ttu-id="cbf79-130">İkinci bir WPF eklemek <xref:System.Windows.Controls.UserControl> projeye.</span><span class="sxs-lookup"><span data-stu-id="cbf79-130">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="cbf79-131">Denetim türü için varsayılan adı kullanacak `UserControl2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="cbf79-131">Use the default name for the control type, `UserControl2.xaml`.</span></span>  
  
6.  <span data-ttu-id="cbf79-132">İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.</span><span class="sxs-lookup"><span data-stu-id="cbf79-132">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
7.  <span data-ttu-id="cbf79-133">Ekleme bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetimini <xref:System.Windows.Controls.UserControl> ve değeri ayarlayın <xref:System.Windows.Controls.TextBox.Text%2A> özelliğine **barındırılan içerik 2**.</span><span class="sxs-lookup"><span data-stu-id="cbf79-133">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>  
  
 <span data-ttu-id="cbf79-134">**Not** genel olarak, daha karmaşık WPF içeriği barındırma.</span><span class="sxs-lookup"><span data-stu-id="cbf79-134">**Note** In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="cbf79-135"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Denetimi yalnızca tanım yalnızca amacıyla burada kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cbf79-135">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>  
  
1.  <span data-ttu-id="cbf79-136">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cbf79-136">Build the project.</span></span>  
  
## <a name="selecting-wpf-controls"></a><span data-ttu-id="cbf79-137">WPF denetimleri seçme</span><span class="sxs-lookup"><span data-stu-id="cbf79-137">Selecting WPF Controls</span></span>  
 <span data-ttu-id="cbf79-138">Farklı WPF İçerik atayabileceğiniz bir <xref:System.Windows.Forms.Integration.ElementHost> içeriği zaten barındırma denetim.</span><span class="sxs-lookup"><span data-stu-id="cbf79-138">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>  
  
#### <a name="to-select-wpf-controls"></a><span data-ttu-id="cbf79-139">WPF denetimleri seçmek için</span><span class="sxs-lookup"><span data-stu-id="cbf79-139">To select WPF controls</span></span>  
  
1.  <span data-ttu-id="cbf79-140">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="cbf79-140">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="cbf79-141">İçinde **araç**, çift `UserControl1` bir örneğini oluşturmak için `UserControl1` form üzerinde.</span><span class="sxs-lookup"><span data-stu-id="cbf79-141">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="cbf79-142">Örneği `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="cbf79-142">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="cbf79-143">İçin akıllı etiket panelinde `elementHost1`, açık **barındırılan içerik Seç** aşağı açılan liste.</span><span class="sxs-lookup"><span data-stu-id="cbf79-143">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>  
  
4.  <span data-ttu-id="cbf79-144">Seçin **UserControl 2** aşağı açılan liste kutusundan.</span><span class="sxs-lookup"><span data-stu-id="cbf79-144">Select **UserControl2** from the drop-down list box.</span></span>  
  
     <span data-ttu-id="cbf79-145">`elementHost1` Denetimi artık bir örneğini barındıran `UserControl2` türü.</span><span class="sxs-lookup"><span data-stu-id="cbf79-145">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>  
  
5.  <span data-ttu-id="cbf79-146">İçinde **özellikleri** penceresinde onaylayın <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> özelliği ayarlanmış **UserControl 2**.</span><span class="sxs-lookup"><span data-stu-id="cbf79-146">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>  
  
6.  <span data-ttu-id="cbf79-147">Gelen **araç**, **WPF birlikte çalışabilirliği** grubunda, sürükleyin bir <xref:System.Windows.Forms.Integration.ElementHost> forma denetim.</span><span class="sxs-lookup"><span data-stu-id="cbf79-147">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>  
  
     <span data-ttu-id="cbf79-148">Yeni denetim için varsayılan ad `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="cbf79-148">The default name for the new control is `elementHost2`.</span></span>  
  
7.  <span data-ttu-id="cbf79-149">İçin akıllı etiket panelinde `elementHost2`, açık **barındırılan içerik Seç** aşağı açılan liste.</span><span class="sxs-lookup"><span data-stu-id="cbf79-149">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>  
  
8.  <span data-ttu-id="cbf79-150">Seçin **UserControl1** aşağı açılan listeden.</span><span class="sxs-lookup"><span data-stu-id="cbf79-150">Select **UserControl1** from the drop-down list.</span></span>  
  
9. <span data-ttu-id="cbf79-151">`elementHost2` Denetimi artık bir örneğini barındıran `UserControl1` türü.</span><span class="sxs-lookup"><span data-stu-id="cbf79-151">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbf79-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cbf79-152">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="cbf79-153">Geçiş ve birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="cbf79-153">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="cbf79-154">WPF denetimlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="cbf79-154">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="cbf79-155">WPF Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="cbf79-155">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
