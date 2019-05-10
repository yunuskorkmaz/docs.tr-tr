---
title: "İzlenecek yol: Windows Forms'da Tasarım Zamanında WPF İçeriği Atama"
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
ms.openlocfilehash: 09427bfc836f40ca9c7aa76f4904bfe7083bf8dc
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211229"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="e29aa-102">İzlenecek yol: Tasarım zamanında Windows Forms WPF içeriği atama</span><span class="sxs-lookup"><span data-stu-id="e29aa-102">Walkthrough: Assign WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="e29aa-103">Bu izlenecek yol, formu görüntülemek istediğiniz Windows Presentation Foundation (WPF) denetim türlerini seçmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="e29aa-103">This walkthrough show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="e29aa-104">Projenize dahil tüm WPF denetim türlerini seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e29aa-104">You can select any WPF control types which are included in your project.</span></span>

<span data-ttu-id="e29aa-105">Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="e29aa-105">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="e29aa-106">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e29aa-106">Create the project.</span></span>

- <span data-ttu-id="e29aa-107">WPF denetim türlerini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e29aa-107">Create the WPF control types.</span></span>

- <span data-ttu-id="e29aa-108">WPF denetimleri seçin.</span><span class="sxs-lookup"><span data-stu-id="e29aa-108">Select WPF controls.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e29aa-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="e29aa-109">Prerequisites</span></span>

<span data-ttu-id="e29aa-110">Bu izlenecek yolu tamamlamak için Visual Studio ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="e29aa-110">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="e29aa-111">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e29aa-111">Create the project</span></span>

<span data-ttu-id="e29aa-112">Visual Studio'yu açın ve Visual Basic veya Visual içinde yeni bir Windows Forms uygulaması projesi oluşturma C# adlı `SelectingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="e29aa-112">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="e29aa-113">WPF içeriği barındırma, yalnızca C# ve Visual Basic projelerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e29aa-113">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="e29aa-114">WPF denetim türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="e29aa-114">Create the WPF control types</span></span>

<span data-ttu-id="e29aa-115">WPF denetim türleri projeye ekledikten sonra bunları farklı barındırabilirsiniz <xref:System.Windows.Forms.Integration.ElementHost> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="e29aa-115">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>

## <a name="create-wpf-control-types"></a><span data-ttu-id="e29aa-116">WPF denetim türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="e29aa-116">Create WPF control types</span></span>

1. <span data-ttu-id="e29aa-117">Yeni bir WPF ekleme <xref:System.Windows.Controls.UserControl> çözüme bir proje.</span><span class="sxs-lookup"><span data-stu-id="e29aa-117">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="e29aa-118">Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="e29aa-118">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="e29aa-119">Daha fazla bilgi için [izlenecek yol: Yeni bir WPF içeriği Windows formlarında tasarım zamanında oluşturma](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="e29aa-119">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="e29aa-120">Tasarım görünümünde emin `UserControl1` seçilir.</span><span class="sxs-lookup"><span data-stu-id="e29aa-120">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="e29aa-121">Daha fazla bilgi için [nasıl yapılır: Seçin ve tasarım yüzeyine öğeleri Taşı](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e29aa-121">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="e29aa-122">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.</span><span class="sxs-lookup"><span data-stu-id="e29aa-122">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

4. <span data-ttu-id="e29aa-123">Ekleme bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetimini <xref:System.Windows.Controls.UserControl> ve değerini ayarlama <xref:System.Windows.Controls.TextBox.Text%2A> özelliğini **barındırılan içerik**.</span><span class="sxs-lookup"><span data-stu-id="e29aa-123">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

5. <span data-ttu-id="e29aa-124">İkinci bir WPF ekleme <xref:System.Windows.Controls.UserControl> projeye.</span><span class="sxs-lookup"><span data-stu-id="e29aa-124">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="e29aa-125">Denetim türü için varsayılan adı kullanacak `UserControl2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="e29aa-125">Use the default name for the control type, `UserControl2.xaml`.</span></span>

6. <span data-ttu-id="e29aa-126">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.</span><span class="sxs-lookup"><span data-stu-id="e29aa-126">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

7. <span data-ttu-id="e29aa-127">Ekleme bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetimini <xref:System.Windows.Controls.UserControl> ve değerini ayarlama <xref:System.Windows.Controls.TextBox.Text%2A> özelliğini **barındırılan içerik 2**.</span><span class="sxs-lookup"><span data-stu-id="e29aa-127">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>

 <span data-ttu-id="e29aa-128">**Not** genel olarak, daha karmaşık bir WPF içeriği barındırmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="e29aa-128">**Note** In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="e29aa-129"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Denetimi yalnızca yalnızca tanım amaçlıdır için burada kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e29aa-129">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

1. <span data-ttu-id="e29aa-130">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e29aa-130">Build the project.</span></span>

## <a name="select-wpf-controls"></a><span data-ttu-id="e29aa-131">WPF denetimleri seçin</span><span class="sxs-lookup"><span data-stu-id="e29aa-131">Select WPF controls</span></span>

<span data-ttu-id="e29aa-132">Farklı bir WPF içeriği için atayabileceğiniz bir <xref:System.Windows.Forms.Integration.ElementHost> içerik barındırma zaten denetimi.</span><span class="sxs-lookup"><span data-stu-id="e29aa-132">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>

1. <span data-ttu-id="e29aa-133">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="e29aa-133">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="e29aa-134">İçinde **araç kutusu**, çift `UserControl1` bir örneğini oluşturmak için `UserControl1` form üzerinde.</span><span class="sxs-lookup"><span data-stu-id="e29aa-134">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

     <span data-ttu-id="e29aa-135">Örneği `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="e29aa-135">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

3. <span data-ttu-id="e29aa-136">Akıllı etiket panelinde `elementHost1`açın **barındırılan içerik Seç** aşağı açılan listesi.</span><span class="sxs-lookup"><span data-stu-id="e29aa-136">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>

4. <span data-ttu-id="e29aa-137">Seçin **UserControl 2** aşağı açılan liste kutusundan.</span><span class="sxs-lookup"><span data-stu-id="e29aa-137">Select **UserControl2** from the drop-down list box.</span></span>

     <span data-ttu-id="e29aa-138">`elementHost1` Denetimi artık bir örneğini barındıran `UserControl2` türü.</span><span class="sxs-lookup"><span data-stu-id="e29aa-138">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>

5. <span data-ttu-id="e29aa-139">İçinde **özellikleri** penceresinde onaylayın <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> özelliği **UserControl 2**.</span><span class="sxs-lookup"><span data-stu-id="e29aa-139">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>

6. <span data-ttu-id="e29aa-140">Gelen **araç kutusu**, **WPF birlikte çalışabilirliği** grubundan bir <xref:System.Windows.Forms.Integration.ElementHost> forma denetim.</span><span class="sxs-lookup"><span data-stu-id="e29aa-140">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>

     <span data-ttu-id="e29aa-141">Yeni denetim için varsayılan ad `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="e29aa-141">The default name for the new control is `elementHost2`.</span></span>

7. <span data-ttu-id="e29aa-142">Akıllı etiket panelinde `elementHost2`açın **barındırılan içerik Seç** aşağı açılan listesi.</span><span class="sxs-lookup"><span data-stu-id="e29aa-142">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>

8. <span data-ttu-id="e29aa-143">Seçin **UserControl1** aşağı açılan listeden.</span><span class="sxs-lookup"><span data-stu-id="e29aa-143">Select **UserControl1** from the drop-down list.</span></span>

9. <span data-ttu-id="e29aa-144">`elementHost2` Denetimi artık bir örneğini barındıran `UserControl1` türü.</span><span class="sxs-lookup"><span data-stu-id="e29aa-144">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>

## <a name="see-also"></a><span data-ttu-id="e29aa-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e29aa-145">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="e29aa-146">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="e29aa-146">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="e29aa-147">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="e29aa-147">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="e29aa-148">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="e29aa-148">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
