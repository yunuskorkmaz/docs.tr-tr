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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bc5f5e2d8808c0a60df721bf2c0ed76b45ef49a0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666255"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="c622b-102">İzlenecek yol: Tasarım zamanında Windows Forms WPF içeriği atama</span><span class="sxs-lookup"><span data-stu-id="c622b-102">Walkthrough: Assign WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="c622b-103">Bu makalede, formunuzda görüntülemek istediğiniz Windows Presentation Foundation (WPF) denetim türlerini seçme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c622b-103">This article show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="c622b-104">Projenize dahil olan herhangi bir WPF denetim türünü seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c622b-104">You can select any WPF control types which are included in your project.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c622b-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c622b-105">Prerequisites</span></span>

<span data-ttu-id="c622b-106">Bu yönergeyi tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="c622b-106">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="c622b-107">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c622b-107">Create the project</span></span>

<span data-ttu-id="c622b-108">Visual Studio 'Yu açın ve Visual Basic veya görsel C# adlı `SelectingWpfContent`yeni bir Windows Forms uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c622b-108">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="c622b-109">WPF içeriği barındırırken yalnızca C# ve Visual Basic projeleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c622b-109">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="c622b-110">WPF denetim türlerini oluşturma</span><span class="sxs-lookup"><span data-stu-id="c622b-110">Create the WPF control types</span></span>

<span data-ttu-id="c622b-111">Projeye wpf denetim türlerini ekledikten sonra, bunları farklı <xref:System.Windows.Forms.Integration.ElementHost> denetimlerde barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c622b-111">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>

1. <span data-ttu-id="c622b-112">Çözüme yeni bir WPF <xref:System.Windows.Controls.UserControl> projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c622b-112">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="c622b-113">Denetim türü için varsayılan adı kullanın, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="c622b-113">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="c622b-114">Daha fazla bilgi için bkz [. İzlenecek yol: Tasarım zamanında](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)Windows Forms yeni WPF içeriği oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="c622b-114">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="c622b-115">Tasarım görünümü ' de, ' `UserControl1` nin seçili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c622b-115">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="c622b-116">**Özellikler** penceresinde, <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin değerini **200**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c622b-116">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="c622b-117">Öğesine bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetim ekleyin <xref:System.Windows.Controls.TextBox.Text%2A>ve özelliğin değerini barındırılan içerik olarak ayarlayın <xref:System.Windows.Controls.UserControl> .</span><span class="sxs-lookup"><span data-stu-id="c622b-117">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

5. <span data-ttu-id="c622b-118">Projeye ikinci bir WPF <xref:System.Windows.Controls.UserControl> ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c622b-118">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="c622b-119">Denetim türü için varsayılan adı kullanın, `UserControl2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="c622b-119">Use the default name for the control type, `UserControl2.xaml`.</span></span>

6. <span data-ttu-id="c622b-120">**Özellikler** penceresinde, <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin değerini **200**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c622b-120">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

7. <span data-ttu-id="c622b-121">Öğesine bir <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> denetim ekleyin <xref:System.Windows.Controls.TextBox.Text%2A>ve özelliğin değerini barındırılan içerik 2 olarak ayarlayın <xref:System.Windows.Controls.UserControl> .</span><span class="sxs-lookup"><span data-stu-id="c622b-121">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="c622b-122">Genel olarak, daha karmaşık WPF içeriğini barındırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="c622b-122">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="c622b-123"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Denetim burada yalnızca tanım amacıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c622b-123">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

8. <span data-ttu-id="c622b-124">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c622b-124">Build the project.</span></span>

## <a name="select-wpf-controls"></a><span data-ttu-id="c622b-125">WPF denetimlerini seçin</span><span class="sxs-lookup"><span data-stu-id="c622b-125">Select WPF controls</span></span>

<span data-ttu-id="c622b-126">Zaten barındıran içeriği olan bir <xref:System.Windows.Forms.Integration.ElementHost> denetime farklı WPF içeriği atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c622b-126">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>

1. <span data-ttu-id="c622b-127">Windows Form Tasarımcısı `Form1` açın.</span><span class="sxs-lookup"><span data-stu-id="c622b-127">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="c622b-128">**Araç kutusunda**, form `UserControl1` üzerinde bir örnek `UserControl1` oluşturmak için çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c622b-128">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

   <span data-ttu-id="c622b-129">Bir örneği `UserControl1` adlı <xref:System.Windows.Forms.Integration.ElementHost> Yeni`elementHost1`bir denetimde barındırılır.</span><span class="sxs-lookup"><span data-stu-id="c622b-129">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

3. <span data-ttu-id="c622b-130">İçin `elementHost1`akıllı etiket panelinde **barındırılan içerik Seç** açılan listesini açın.</span><span class="sxs-lookup"><span data-stu-id="c622b-130">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>

4. <span data-ttu-id="c622b-131">Açılan liste kutusundan **UserControl2** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c622b-131">Select **UserControl2** from the drop-down list box.</span></span>

   <span data-ttu-id="c622b-132">Denetim artık `UserControl2` türün bir örneğini barındırır. `elementHost1`</span><span class="sxs-lookup"><span data-stu-id="c622b-132">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>

5. <span data-ttu-id="c622b-133">**Özellikler** penceresinde, <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> özelliğinin **UserControl2**olarak ayarlandığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="c622b-133">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>

6. <span data-ttu-id="c622b-134">**Araç kutusu**' nda, **WPF birlikte çalışabilirlik** grubunda bir <xref:System.Windows.Forms.Integration.ElementHost> denetimi form üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="c622b-134">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>

   <span data-ttu-id="c622b-135">Yeni denetim `elementHost2`için varsayılan ad.</span><span class="sxs-lookup"><span data-stu-id="c622b-135">The default name for the new control is `elementHost2`.</span></span>

7. <span data-ttu-id="c622b-136">İçin `elementHost2`akıllı etiket panelinde **barındırılan içerik Seç** açılan listesini açın.</span><span class="sxs-lookup"><span data-stu-id="c622b-136">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>

8. <span data-ttu-id="c622b-137">Açılan listeden **UserControl1** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="c622b-137">Select **UserControl1** from the drop-down list.</span></span>

9. <span data-ttu-id="c622b-138">Denetim artık `UserControl1` türün bir örneğini barındırır. `elementHost2`</span><span class="sxs-lookup"><span data-stu-id="c622b-138">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>

## <a name="see-also"></a><span data-ttu-id="c622b-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c622b-139">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="c622b-140">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="c622b-140">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="c622b-141">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="c622b-141">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="c622b-142">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="c622b-142">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
