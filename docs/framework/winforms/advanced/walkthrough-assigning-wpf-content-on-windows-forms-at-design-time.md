---
title: Windows Forms için WPF denetimleri seçin
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 19f1dfec282b025f5a1fa367ec5fa9a52472c691
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746804"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="f83af-102">İzlenecek yol: tasarım zamanında Windows Forms WPF içeriği atama</span><span class="sxs-lookup"><span data-stu-id="f83af-102">Walkthrough: Assign WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="f83af-103">Bu makalede, formunuzda görüntülemek istediğiniz Windows Presentation Foundation (WPF) denetim türlerini seçme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f83af-103">This article show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="f83af-104">Projenize dahil olan herhangi bir WPF denetim türünü seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f83af-104">You can select any WPF control types that are included in your project.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f83af-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f83af-105">Prerequisites</span></span>

<span data-ttu-id="f83af-106">Bu yönergeyi tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="f83af-106">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="f83af-107">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="f83af-107">Create the project</span></span>

<span data-ttu-id="f83af-108">Visual Studio 'Yu açın ve Visual Basic veya görsel C# adlı `SelectingWpfContent`Windows Forms uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f83af-108">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="f83af-109">WPF içeriği barındırırken yalnızca C# ve Visual Basic projeleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f83af-109">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="f83af-110">WPF denetim türlerini oluşturma</span><span class="sxs-lookup"><span data-stu-id="f83af-110">Create the WPF control types</span></span>

<span data-ttu-id="f83af-111">Projeye WPF denetim türlerini ekledikten sonra, bunları farklı <xref:System.Windows.Forms.Integration.ElementHost> denetimlerinde barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f83af-111">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>

1. <span data-ttu-id="f83af-112">Çözüme yeni bir WPF <xref:System.Windows.Controls.UserControl> projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f83af-112">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="f83af-113">Denetim türü için varsayılan adı kullanın, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="f83af-113">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="f83af-114">Daha fazla bilgi için bkz. [Izlenecek yol: tasarım zamanında Windows Forms yenı WPF Içeriği oluşturma](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="f83af-114">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="f83af-115">Tasarım görünümü ' de `UserControl1` ' nin seçili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f83af-115">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="f83af-116">**Özellikler** penceresinde <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin değerini **200**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f83af-116">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="f83af-117"><xref:System.Windows.Controls.UserControl> <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> bir denetim ekleyin ve <xref:System.Windows.Controls.TextBox.Text%2A> özelliğinin değerini **barındırılan içerik**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f83af-117">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

5. <span data-ttu-id="f83af-118">Projeye ikinci bir WPF <xref:System.Windows.Controls.UserControl> ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f83af-118">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="f83af-119">Denetim türü için varsayılan adı kullanın, `UserControl2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="f83af-119">Use the default name for the control type, `UserControl2.xaml`.</span></span>

6. <span data-ttu-id="f83af-120">**Özellikler** penceresinde <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin değerini **200**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f83af-120">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

7. <span data-ttu-id="f83af-121"><xref:System.Windows.Controls.UserControl> <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> bir denetim ekleyin ve <xref:System.Windows.Controls.TextBox.Text%2A> özelliğinin değerini **barındırılan içerik 2**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f83af-121">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="f83af-122">Genel olarak, daha karmaşık WPF içeriğini barındırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="f83af-122">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="f83af-123"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetimi yalnızca tanım amacıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f83af-123">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

8. <span data-ttu-id="f83af-124">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f83af-124">Build the project.</span></span>

## <a name="select-wpf-controls"></a><span data-ttu-id="f83af-125">WPF denetimlerini seçin</span><span class="sxs-lookup"><span data-stu-id="f83af-125">Select WPF controls</span></span>

<span data-ttu-id="f83af-126">Zaten barındırma içeriği olan bir <xref:System.Windows.Forms.Integration.ElementHost> denetimine farklı WPF içeriği atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f83af-126">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>

1. <span data-ttu-id="f83af-127">Windows Form Tasarımcısı `Form1` açın.</span><span class="sxs-lookup"><span data-stu-id="f83af-127">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="f83af-128">**Araç kutusunda**`UserControl1` ' ye çift tıklayarak formda `UserControl1` bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f83af-128">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

   <span data-ttu-id="f83af-129">`UserControl1` örneği, `elementHost1`adlı yeni bir <xref:System.Windows.Forms.Integration.ElementHost> denetiminde barındırılır.</span><span class="sxs-lookup"><span data-stu-id="f83af-129">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

3. <span data-ttu-id="f83af-130">`elementHost1`için akıllı etiket panelinde **barındırılan Içerik Seç** açılan listesini açın.</span><span class="sxs-lookup"><span data-stu-id="f83af-130">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>

4. <span data-ttu-id="f83af-131">Açılan liste kutusundan **UserControl2** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f83af-131">Select **UserControl2** from the drop-down list box.</span></span>

   <span data-ttu-id="f83af-132">`elementHost1` denetimi artık `UserControl2` türünün bir örneğini barındırır.</span><span class="sxs-lookup"><span data-stu-id="f83af-132">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>

5. <span data-ttu-id="f83af-133">**Özellikler** penceresinde, <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> özelliğinin **UserControl2**olarak ayarlandığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="f83af-133">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>

6. <span data-ttu-id="f83af-134">**Araç kutusundan** **WPF birlikte çalışabilirlik** grubunda, form üzerine bir <xref:System.Windows.Forms.Integration.ElementHost> denetimi sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="f83af-134">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>

   <span data-ttu-id="f83af-135">Yeni denetim için varsayılan ad `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="f83af-135">The default name for the new control is `elementHost2`.</span></span>

7. <span data-ttu-id="f83af-136">`elementHost2`için akıllı etiket panelinde **barındırılan Içerik Seç** açılan listesini açın.</span><span class="sxs-lookup"><span data-stu-id="f83af-136">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>

8. <span data-ttu-id="f83af-137">Açılan listeden **UserControl1** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f83af-137">Select **UserControl1** from the drop-down list.</span></span>

9. <span data-ttu-id="f83af-138">`elementHost2` denetimi artık `UserControl1` türünün bir örneğini barındırır.</span><span class="sxs-lookup"><span data-stu-id="f83af-138">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>

## <a name="see-also"></a><span data-ttu-id="f83af-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f83af-139">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="f83af-140">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="f83af-140">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="f83af-141">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="f83af-141">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="f83af-142">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="f83af-142">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
