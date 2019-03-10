---
title: 'İzlenecek yol: Tasarım zamanında Windows Forms WPF içeriği atama'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
ms.openlocfilehash: 364cfe521a1e141bdfcfb3cfc47170714d010a87
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707930"
---
# <a name="walkthrough-assigning-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="f665d-102">İzlenecek yol: Tasarım zamanında Windows Forms WPF içeriği atama</span><span class="sxs-lookup"><span data-stu-id="f665d-102">Walkthrough: Assigning WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="f665d-103">Bu izlenecek yol, formu görüntülemek istediğiniz Windows Presentation Foundation (WPF) denetim türlerini seçmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="f665d-103">This walkthrough show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="f665d-104">Projenize dahil tüm WPF denetim türlerini seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f665d-104">You can select any WPF control types which are included in your project.</span></span>

 <span data-ttu-id="f665d-105">Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="f665d-105">In this walkthrough, you perform the following tasks:</span></span>

-   <span data-ttu-id="f665d-106">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f665d-106">Create the project.</span></span>

-   <span data-ttu-id="f665d-107">WPF denetim türlerini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f665d-107">Create the WPF control types.</span></span>

-   <span data-ttu-id="f665d-108">WPF denetimleri seçin.</span><span class="sxs-lookup"><span data-stu-id="f665d-108">Select WPF controls.</span></span>

> [!NOTE]
>  <span data-ttu-id="f665d-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="f665d-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f665d-110">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="f665d-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f665d-111">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="f665d-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f665d-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="f665d-112">Prerequisites</span></span>  
 <span data-ttu-id="f665d-113">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="f665d-113">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="f665d-114">Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="f665d-114">Visual Studio 2012.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="f665d-115">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f665d-115">Creating the Project</span></span>  
 <span data-ttu-id="f665d-116">İlk adım Windows Forms projesi oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="f665d-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f665d-117">WPF içeriği barındırma, yalnızca C# ve Visual Basic projelerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f665d-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="f665d-118">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f665d-118">To create the project</span></span>  
  
-   <span data-ttu-id="f665d-119">Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `SelectingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="f665d-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="f665d-120">WPF denetim türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="f665d-120">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="f665d-121">WPF denetim türleri projeye ekledikten sonra bunları farklı barındırabilirsiniz <xref:System.Windows.Forms.Integration.ElementHost> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="f665d-121">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="f665d-122">WPF denetim türleri oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f665d-122">To create WPF control types</span></span>  
  
1.  <span data-ttu-id="f665d-123">Yeni bir WPF ekleme <xref:System.Windows.Controls.UserControl> çözüme bir proje.</span><span class="sxs-lookup"><span data-stu-id="f665d-123">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="f665d-124">Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="f665d-124">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="f665d-125">Daha fazla bilgi için [izlenecek yol: Yeni bir WPF içeriği Windows formlarında tasarım zamanında oluşturma](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="f665d-125">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="f665d-126">Tasarım görünümünde emin `UserControl1` seçilir.</span><span class="sxs-lookup"><span data-stu-id="f665d-126">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="f665d-127">Daha fazla bilgi için [nasıl yapılır: Seçin ve tasarım yüzeyine öğeleri Taşı](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f665d-127">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>  
  
3.  <span data-ttu-id="f665d-128">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.</span><span class="sxs-lookup"><span data-stu-id="f665d-128">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="f665d-129">Ekleme bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetimini <xref:System.Windows.Controls.UserControl> ve değerini ayarlama <xref:System.Windows.Controls.TextBox.Text%2A> özelliğini **barındırılan içerik**.</span><span class="sxs-lookup"><span data-stu-id="f665d-129">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>  
  
5.  <span data-ttu-id="f665d-130">İkinci bir WPF ekleme <xref:System.Windows.Controls.UserControl> projeye.</span><span class="sxs-lookup"><span data-stu-id="f665d-130">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="f665d-131">Denetim türü için varsayılan adı kullanacak `UserControl2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="f665d-131">Use the default name for the control type, `UserControl2.xaml`.</span></span>  
  
6.  <span data-ttu-id="f665d-132">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.</span><span class="sxs-lookup"><span data-stu-id="f665d-132">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
7.  <span data-ttu-id="f665d-133">Ekleme bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetimini <xref:System.Windows.Controls.UserControl> ve değerini ayarlama <xref:System.Windows.Controls.TextBox.Text%2A> özelliğini **barındırılan içerik 2**.</span><span class="sxs-lookup"><span data-stu-id="f665d-133">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>  
  
 <span data-ttu-id="f665d-134">**Not** genel olarak, daha karmaşık bir WPF içeriği barındırmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="f665d-134">**Note** In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="f665d-135"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Denetimi yalnızca yalnızca tanım amaçlıdır için burada kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f665d-135">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>  
  
1.  <span data-ttu-id="f665d-136">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f665d-136">Build the project.</span></span>  
  
## <a name="selecting-wpf-controls"></a><span data-ttu-id="f665d-137">WPF denetimleri seçme</span><span class="sxs-lookup"><span data-stu-id="f665d-137">Selecting WPF Controls</span></span>  
 <span data-ttu-id="f665d-138">Farklı bir WPF içeriği için atayabileceğiniz bir <xref:System.Windows.Forms.Integration.ElementHost> içerik barındırma zaten denetimi.</span><span class="sxs-lookup"><span data-stu-id="f665d-138">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>  
  
#### <a name="to-select-wpf-controls"></a><span data-ttu-id="f665d-139">WPF denetimleri seçin</span><span class="sxs-lookup"><span data-stu-id="f665d-139">To select WPF controls</span></span>  
  
1.  <span data-ttu-id="f665d-140">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="f665d-140">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="f665d-141">İçinde **araç kutusu**, çift `UserControl1` bir örneğini oluşturmak için `UserControl1` form üzerinde.</span><span class="sxs-lookup"><span data-stu-id="f665d-141">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="f665d-142">Örneği `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="f665d-142">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="f665d-143">Akıllı etiket panelinde `elementHost1`açın **barındırılan içerik Seç** aşağı açılan listesi.</span><span class="sxs-lookup"><span data-stu-id="f665d-143">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>  
  
4.  <span data-ttu-id="f665d-144">Seçin **UserControl 2** aşağı açılan liste kutusundan.</span><span class="sxs-lookup"><span data-stu-id="f665d-144">Select **UserControl2** from the drop-down list box.</span></span>  
  
     <span data-ttu-id="f665d-145">`elementHost1` Denetimi artık bir örneğini barındıran `UserControl2` türü.</span><span class="sxs-lookup"><span data-stu-id="f665d-145">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>  
  
5.  <span data-ttu-id="f665d-146">İçinde **özellikleri** penceresinde onaylayın <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> özelliği **UserControl 2**.</span><span class="sxs-lookup"><span data-stu-id="f665d-146">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>  
  
6.  <span data-ttu-id="f665d-147">Gelen **araç kutusu**, **WPF birlikte çalışabilirliği** grubundan bir <xref:System.Windows.Forms.Integration.ElementHost> forma denetim.</span><span class="sxs-lookup"><span data-stu-id="f665d-147">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>  
  
     <span data-ttu-id="f665d-148">Yeni denetim için varsayılan ad `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="f665d-148">The default name for the new control is `elementHost2`.</span></span>  
  
7.  <span data-ttu-id="f665d-149">Akıllı etiket panelinde `elementHost2`açın **barındırılan içerik Seç** aşağı açılan listesi.</span><span class="sxs-lookup"><span data-stu-id="f665d-149">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>  
  
8.  <span data-ttu-id="f665d-150">Seçin **UserControl1** aşağı açılan listeden.</span><span class="sxs-lookup"><span data-stu-id="f665d-150">Select **UserControl1** from the drop-down list.</span></span>  
  
9. <span data-ttu-id="f665d-151">`elementHost2` Denetimi artık bir örneğini barındıran `UserControl1` türü.</span><span class="sxs-lookup"><span data-stu-id="f665d-151">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f665d-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f665d-152">See also</span></span>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="f665d-153">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="f665d-153">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="f665d-154">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="f665d-154">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="f665d-155">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="f665d-155">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
