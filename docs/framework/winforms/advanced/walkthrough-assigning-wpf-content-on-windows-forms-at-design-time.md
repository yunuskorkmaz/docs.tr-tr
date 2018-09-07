---
title: 'İzlenecek yol: Windows Formlarında Tasarım Zamanında WPF İçeriği Atama'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
ms.openlocfilehash: 6db75e9d8ec5aeb1a0c7310d39391f8f264649d3
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44081118"
---
# <a name="walkthrough-assigning-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="54d71-102">İzlenecek yol: Windows Formlarında Tasarım Zamanında WPF İçeriği Atama</span><span class="sxs-lookup"><span data-stu-id="54d71-102">Walkthrough: Assigning WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="54d71-103">Bu izlenecek yol, formu görüntülemek istediğiniz Windows Presentation Foundation (WPF) denetim türlerini seçmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="54d71-103">This walkthrough show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="54d71-104">Projenize dahil tüm WPF denetim türlerini seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54d71-104">You can select any WPF control types which are included in your project.</span></span>  
  
 <span data-ttu-id="54d71-105">Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="54d71-105">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="54d71-106">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="54d71-106">Create the project.</span></span>  
  
-   <span data-ttu-id="54d71-107">WPF denetim türlerini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="54d71-107">Create the WPF control types.</span></span>  
  
-   <span data-ttu-id="54d71-108">WPF denetimleri seçin.</span><span class="sxs-lookup"><span data-stu-id="54d71-108">Select WPF controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54d71-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="54d71-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="54d71-110">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="54d71-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="54d71-111">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="54d71-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="54d71-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="54d71-112">Prerequisites</span></span>  
 <span data-ttu-id="54d71-113">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="54d71-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="54d71-114">.</span><span class="sxs-lookup"><span data-stu-id="54d71-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="54d71-115">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="54d71-115">Creating the Project</span></span>  
 <span data-ttu-id="54d71-116">İlk adım Windows Forms projesi oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="54d71-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54d71-117">WPF içeriği barındırma, yalnızca C# ve Visual Basic projelerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="54d71-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="54d71-118">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="54d71-118">To create the project</span></span>  
  
-   <span data-ttu-id="54d71-119">Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `SelectingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="54d71-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="54d71-120">WPF denetim türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="54d71-120">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="54d71-121">WPF denetim türleri projeye ekledikten sonra bunları farklı barındırabilirsiniz <xref:System.Windows.Forms.Integration.ElementHost> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="54d71-121">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="54d71-122">WPF denetim türleri oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="54d71-122">To create WPF control types</span></span>  
  
1.  <span data-ttu-id="54d71-123">Yeni bir WPF ekleme <xref:System.Windows.Controls.UserControl> çözüme bir proje.</span><span class="sxs-lookup"><span data-stu-id="54d71-123">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="54d71-124">Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="54d71-124">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="54d71-125">Daha fazla bilgi için [izlenecek yol: oluşturma yeni WPF içeriği Windows Forms'ta tasarım zamanında](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="54d71-125">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="54d71-126">Tasarım görünümünde emin `UserControl1` seçilir.</span><span class="sxs-lookup"><span data-stu-id="54d71-126">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="54d71-127">Daha fazla bilgi için [nasıl yapılır: seçin ve tasarım yüzeyinde taşımak öğeleri](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="54d71-127">For more information, see [How to: Select and Move Elements on the Design Surface](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="54d71-128">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.</span><span class="sxs-lookup"><span data-stu-id="54d71-128">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="54d71-129">Ekleme bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetimini <xref:System.Windows.Controls.UserControl> ve değerini ayarlama <xref:System.Windows.Controls.TextBox.Text%2A> özelliğini **barındırılan içerik**.</span><span class="sxs-lookup"><span data-stu-id="54d71-129">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>  
  
5.  <span data-ttu-id="54d71-130">İkinci bir WPF ekleme <xref:System.Windows.Controls.UserControl> projeye.</span><span class="sxs-lookup"><span data-stu-id="54d71-130">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="54d71-131">Denetim türü için varsayılan adı kullanacak `UserControl2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="54d71-131">Use the default name for the control type, `UserControl2.xaml`.</span></span>  
  
6.  <span data-ttu-id="54d71-132">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.</span><span class="sxs-lookup"><span data-stu-id="54d71-132">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
7.  <span data-ttu-id="54d71-133">Ekleme bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetimini <xref:System.Windows.Controls.UserControl> ve değerini ayarlama <xref:System.Windows.Controls.TextBox.Text%2A> özelliğini **barındırılan içerik 2**.</span><span class="sxs-lookup"><span data-stu-id="54d71-133">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>  
  
 <span data-ttu-id="54d71-134">**Not** genel olarak, daha karmaşık bir WPF içeriği barındırmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="54d71-134">**Note** In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="54d71-135"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Denetimi yalnızca yalnızca tanım amaçlıdır için burada kullanılır.</span><span class="sxs-lookup"><span data-stu-id="54d71-135">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>  
  
1.  <span data-ttu-id="54d71-136">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="54d71-136">Build the project.</span></span>  
  
## <a name="selecting-wpf-controls"></a><span data-ttu-id="54d71-137">WPF denetimleri seçme</span><span class="sxs-lookup"><span data-stu-id="54d71-137">Selecting WPF Controls</span></span>  
 <span data-ttu-id="54d71-138">Farklı bir WPF içeriği için atayabileceğiniz bir <xref:System.Windows.Forms.Integration.ElementHost> içerik barındırma zaten denetimi.</span><span class="sxs-lookup"><span data-stu-id="54d71-138">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>  
  
#### <a name="to-select-wpf-controls"></a><span data-ttu-id="54d71-139">WPF denetimleri seçin</span><span class="sxs-lookup"><span data-stu-id="54d71-139">To select WPF controls</span></span>  
  
1.  <span data-ttu-id="54d71-140">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="54d71-140">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="54d71-141">İçinde **araç kutusu**, çift `UserControl1` bir örneğini oluşturmak için `UserControl1` form üzerinde.</span><span class="sxs-lookup"><span data-stu-id="54d71-141">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="54d71-142">Örneği `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="54d71-142">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="54d71-143">Akıllı etiket panelinde `elementHost1`açın **barındırılan içerik Seç** aşağı açılan listesi.</span><span class="sxs-lookup"><span data-stu-id="54d71-143">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>  
  
4.  <span data-ttu-id="54d71-144">Seçin **UserControl 2** aşağı açılan liste kutusundan.</span><span class="sxs-lookup"><span data-stu-id="54d71-144">Select **UserControl2** from the drop-down list box.</span></span>  
  
     <span data-ttu-id="54d71-145">`elementHost1` Denetimi artık bir örneğini barındıran `UserControl2` türü.</span><span class="sxs-lookup"><span data-stu-id="54d71-145">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>  
  
5.  <span data-ttu-id="54d71-146">İçinde **özellikleri** penceresinde onaylayın <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> özelliği **UserControl 2**.</span><span class="sxs-lookup"><span data-stu-id="54d71-146">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>  
  
6.  <span data-ttu-id="54d71-147">Gelen **araç kutusu**, **WPF birlikte çalışabilirliği** grubundan bir <xref:System.Windows.Forms.Integration.ElementHost> forma denetim.</span><span class="sxs-lookup"><span data-stu-id="54d71-147">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>  
  
     <span data-ttu-id="54d71-148">Yeni denetim için varsayılan ad `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="54d71-148">The default name for the new control is `elementHost2`.</span></span>  
  
7.  <span data-ttu-id="54d71-149">Akıllı etiket panelinde `elementHost2`açın **barındırılan içerik Seç** aşağı açılan listesi.</span><span class="sxs-lookup"><span data-stu-id="54d71-149">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>  
  
8.  <span data-ttu-id="54d71-150">Seçin **UserControl1** aşağı açılan listeden.</span><span class="sxs-lookup"><span data-stu-id="54d71-150">Select **UserControl1** from the drop-down list.</span></span>  
  
9. <span data-ttu-id="54d71-151">`elementHost2` Denetimi artık bir örneğini barındıran `UserControl1` türü.</span><span class="sxs-lookup"><span data-stu-id="54d71-151">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54d71-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="54d71-152">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="54d71-153">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="54d71-153">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="54d71-154">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="54d71-154">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="54d71-155">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="54d71-155">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
