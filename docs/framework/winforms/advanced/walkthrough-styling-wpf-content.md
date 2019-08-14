---
title: 'İzlenecek yol: WPF İçeriği için Stil Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
ms.openlocfilehash: 32ca9658ddf4ab6e8690f29797b7ac7b09df2ca7
ms.sourcegitcommit: d98fdb087d9c8aba7d2cb93fe4b4ee35a2308cee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69012954"
---
# <a name="walkthrough-style-wpf-content"></a><span data-ttu-id="a7b68-102">İzlenecek yol: Biçim WPF içeriği</span><span class="sxs-lookup"><span data-stu-id="a7b68-102">Walkthrough: Style WPF content</span></span>

<span data-ttu-id="a7b68-103">Bu izlenecek yol, bir Windows formunda barındırılan bir Windows Presentation Foundation (WPF) denetimine nasıl stil uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7b68-103">This walkthrough show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

 <span data-ttu-id="a7b68-104">Bu kılavuzda, aşağıdaki görevleri gerçekleştirirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a7b68-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="a7b68-105">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a7b68-105">Create the project.</span></span>

- <span data-ttu-id="a7b68-106">WPF denetim türünü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a7b68-106">Create the WPF control type.</span></span>

- <span data-ttu-id="a7b68-107">WPF denetimine bir stil uygulayın.</span><span class="sxs-lookup"><span data-stu-id="a7b68-107">Apply a style to the WPF control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a7b68-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="a7b68-108">Prerequisites</span></span>

<span data-ttu-id="a7b68-109">Bu yönergeyi tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="a7b68-109">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="a7b68-110">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="a7b68-110">Create the project</span></span>

<span data-ttu-id="a7b68-111">Visual Studio 'Yu açın ve Visual Basic veya görsel C# adlı `StylingWpfContent`yeni bir Windows Forms uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a7b68-111">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="a7b68-112">WPF içeriği barındırırken yalnızca C# ve Visual Basic projeleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a7b68-112">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="a7b68-113">WPF denetim türlerini oluşturma</span><span class="sxs-lookup"><span data-stu-id="a7b68-113">Create the WPF control types</span></span>

<span data-ttu-id="a7b68-114">Projeye bir WPF denetim türü ekledikten sonra, bunu bir <xref:System.Windows.Forms.Integration.ElementHost> denetimde barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7b68-114">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

1. <span data-ttu-id="a7b68-115">Çözüme yeni bir WPF <xref:System.Windows.Controls.UserControl> projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a7b68-115">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="a7b68-116">Denetim türü için varsayılan adı kullanın, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="a7b68-116">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="a7b68-117">Daha fazla bilgi için bkz [. İzlenecek yol: Tasarım zamanında](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)Windows Forms yeni WPF içeriği oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="a7b68-117">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="a7b68-118">Tasarım görünümü ' de, ' `UserControl1` nin seçili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a7b68-118">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="a7b68-119">Daha fazla bilgi için [nasıl yapılır: Tasarım Yüzeyi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100))öğeleri seçin ve taşıyın.</span><span class="sxs-lookup"><span data-stu-id="a7b68-119">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="a7b68-120">**Özellikler** penceresinde, <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin değerini olarak `200`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a7b68-120">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

4. <span data-ttu-id="a7b68-121">Öğesine bir <xref:System.Windows.Controls.Button?displayProperty=nameWithType> denetim ekleyin <xref:System.Windows.Controls.ContentControl.Content%2A>ve özelliğin değerini iptal olarak ayarlayın. <xref:System.Windows.Controls.UserControl></span><span class="sxs-lookup"><span data-stu-id="a7b68-121">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>

5. <span data-ttu-id="a7b68-122">Öğesine ikinci <xref:System.Windows.Controls.Button?displayProperty=nameWithType> bir denetim ekleyin <xref:System.Windows.Controls.ContentControl.Content%2A>ve özelliğinin değerini Tamam olarak ayarlayın <xref:System.Windows.Controls.UserControl> .</span><span class="sxs-lookup"><span data-stu-id="a7b68-122">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>

6. <span data-ttu-id="a7b68-123">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a7b68-123">Build the project.</span></span>

## <a name="apply-a-style-to-a-wpf-control"></a><span data-ttu-id="a7b68-124">WPF denetimine stil uygulama</span><span class="sxs-lookup"><span data-stu-id="a7b68-124">Apply a Style to a WPF Control</span></span>

<span data-ttu-id="a7b68-125">Görünümünü ve davranışını değiştirmek için WPF denetimine farklı stil uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7b68-125">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>

1. <span data-ttu-id="a7b68-126">Windows Form Tasarımcısı `Form1` açın.</span><span class="sxs-lookup"><span data-stu-id="a7b68-126">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="a7b68-127">**Araç kutusunda**, form `UserControl1` üzerinde bir örnek `UserControl1` oluşturmak için çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a7b68-127">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

     <span data-ttu-id="a7b68-128">Bir örneği `UserControl1` adlı <xref:System.Windows.Forms.Integration.ElementHost> Yeni`elementHost1`bir denetimde barındırılır.</span><span class="sxs-lookup"><span data-stu-id="a7b68-128">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

1. <span data-ttu-id="a7b68-129">İçin `elementHost1`akıllı etiket panelinde, açılan listeden **barındırılan içeriği Düzenle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a7b68-129">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>

     <span data-ttu-id="a7b68-130">`UserControl1`içinde [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]açılır.</span><span class="sxs-lookup"><span data-stu-id="a7b68-130">`UserControl1` opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

1. <span data-ttu-id="a7b68-131">Xaml görünümünde, `<UserControl>` açılış etiketinden sonra aşağıdaki xaml 'yi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a7b68-131">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span>

     <span data-ttu-id="a7b68-132">Bu XAML, çakışan gradyan kenarlığı olan bir gradyan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a7b68-132">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="a7b68-133">Denetime tıklandığında degradeler, basılan düğme görünümü oluşturacak şekilde değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="a7b68-133">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="a7b68-134">Daha fazla bilgi için bkz. [Stil oluşturma ve şablon](../../wpf/controls/styling-and-templating.md)oluşturma.</span><span class="sxs-lookup"><span data-stu-id="a7b68-134">For more information, see [Styling and Templating](../../wpf/controls/styling-and-templating.md).</span></span>

   ```xaml
   <UserControl.Resources>
    <LinearGradientBrush x:Key="NormalBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#FFF" Offset="0.0"/>
        <GradientStop Color="#CCC" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="PressedBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#BBB" Offset="0.0"/>
        <GradientStop Color="#EEE" Offset="0.1"/>
        <GradientStop Color="#EEE" Offset="0.9"/>
        <GradientStop Color="#FFF" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="NormalBorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#CCC" Offset="0.0"/>
        <GradientStop Color="#444" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="BorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#CCC" Offset="0.0"/>
        <GradientStop Color="#444" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="PressedBorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#444" Offset="0.0"/>
        <GradientStop Color="#888" Offset="1.0"/>
    </LinearGradientBrush>

    <Style x:Key="SimpleButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="Background" Value="{StaticResource NormalBrush}"/>
        <Setter Property="BorderBrush" Value="{StaticResource NormalBorderBrush}"/>
        <Setter Property="Template">
            <Setter.Value>
                <ControlTemplate TargetType="{x:Type Button}">
                    <Grid x:Name="Grid">
                        <Border x:Name="Border" Background="{TemplateBinding Background}" BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}" Padding="{TemplateBinding Padding}"/>
                        <ContentPresenter HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}" RecognizesAccessKey="True"/>
                    </Grid>
                    <ControlTemplate.Triggers>
                        <Trigger Property="IsPressed" Value="true">
                            <Setter Property="Background" Value="{StaticResource PressedBrush}" TargetName="Border"/>
                            <Setter Property="BorderBrush" Value="{StaticResource PressedBorderBrush}" TargetName="Border"/>
                        </Trigger>
                    </ControlTemplate.Triggers>
                </ControlTemplate>
            </Setter.Value>
        </Setter>
    </Style>
   </UserControl.Resources>
   ```

1. <span data-ttu-id="a7b68-135">Aşağıdaki XAML 'yi İptal düğmesinin `<Button>` etiketine ekleyerek, önceki adımda tanımlanan stili`SimpleButton` iptal düğmesine uygulayın.</span><span class="sxs-lookup"><span data-stu-id="a7b68-135">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the Cancel button.</span></span>

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   <span data-ttu-id="a7b68-136">Düğme bildirimidir aşağıdaki XAML 'ye benzeyecektir:</span><span class="sxs-lookup"><span data-stu-id="a7b68-136">Your button declaration will resemble the following XAML:</span></span>

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. <span data-ttu-id="a7b68-137">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a7b68-137">Build the project.</span></span>

1. <span data-ttu-id="a7b68-138">Windows Form Tasarımcısı `Form1` açın.</span><span class="sxs-lookup"><span data-stu-id="a7b68-138">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="a7b68-139">Yeni stil düğme denetimine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a7b68-139">The new style is applied to the button control.</span></span>

1. <span data-ttu-id="a7b68-140">**Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat** ' ı seçerek uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a7b68-140">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>

1. <span data-ttu-id="a7b68-141">Tamam ve Iptal düğmelerini tıklatın ve farkları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="a7b68-141">Click the OK and Cancel buttons and view the differences.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7b68-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7b68-142">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="a7b68-143">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="a7b68-143">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="a7b68-144">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="a7b68-144">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="a7b68-145">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="a7b68-145">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="a7b68-146">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="a7b68-146">XAML Overview (WPF)</span></span>](../../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="a7b68-147">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a7b68-147">Styling and Templating</span></span>](../../wpf/controls/styling-and-templating.md)
