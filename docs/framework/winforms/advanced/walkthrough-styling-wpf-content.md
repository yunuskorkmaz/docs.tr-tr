---
title: 'Walkthrough: Stil WPF içeriği'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 07241d41e3fbf270a76bd241765bfa369ee265d5
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646325"
---
# <a name="walkthrough-style-wpf-content"></a><span data-ttu-id="f0845-102">Walkthrough: Stil WPF içeriği</span><span class="sxs-lookup"><span data-stu-id="f0845-102">Walkthrough: Style WPF content</span></span>

<span data-ttu-id="f0845-103">Bu makalede, bir Windows Formu'nda barındırılan bir Windows Sunu Temeli (WPF) denetimine stil nasıl uygulanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f0845-103">This article show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f0845-104">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="f0845-104">Prerequisites</span></span>

<span data-ttu-id="f0845-105">Bu walkthrough tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0845-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="f0845-106">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="f0845-106">Create the project</span></span>

<span data-ttu-id="f0845-107">Visual Studio'yu açın ve Visual Basic veya Visual C# adlı `StylingWpfContent`yeni bir Windows Forms Uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f0845-107">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="f0845-108">WPF içeriği barındırırken yalnızca C# ve Visual Basic projeleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f0845-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="f0845-109">WPF denetim türlerini oluşturma</span><span class="sxs-lookup"><span data-stu-id="f0845-109">Create the WPF control types</span></span>

<span data-ttu-id="f0845-110">Projeye bir WPF denetim türü ekledikten sonra, bunu <xref:System.Windows.Forms.Integration.ElementHost> bir denetimde barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0845-110">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

1. <span data-ttu-id="f0845-111">Çözüme yeni <xref:System.Windows.Controls.UserControl> bir WPF projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f0845-111">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="f0845-112">Denetim türü için varsayılan adı `UserControl1.xaml`kullanın.</span><span class="sxs-lookup"><span data-stu-id="f0845-112">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="f0845-113">Daha fazla bilgi için [Bkz. Walkthrough: Tasarım Zamanında Windows Formlarında Yeni WPF İçeriği Oluşturma](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="f0845-113">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="f0845-114">Tasarım görünümünde, seçildiğinden `UserControl1` emin olun.</span><span class="sxs-lookup"><span data-stu-id="f0845-114">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="f0845-115">**Özellikler** penceresinde, **200**değerini <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> ve özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f0845-115">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="f0845-116">Bir <xref:System.Windows.Controls.Button?displayProperty=nameWithType> denetim ekleyin <xref:System.Windows.Controls.UserControl> ve <xref:System.Windows.Controls.ContentControl.Content%2A> **özelliğin**değerini İptal etmek için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f0845-116">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>

5. <span data-ttu-id="f0845-117">İkinci <xref:System.Windows.Controls.Button?displayProperty=nameWithType> bir denetim <xref:System.Windows.Controls.UserControl> ekleyin ve <xref:System.Windows.Controls.ContentControl.Content%2A> özelliğin değerini **Tamam'a**ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f0845-117">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>

6. <span data-ttu-id="f0845-118">Projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="f0845-118">Build the project.</span></span>

## <a name="apply-a-style-to-a-wpf-control"></a><span data-ttu-id="f0845-119">WPF Denetimine Stil Uygulama</span><span class="sxs-lookup"><span data-stu-id="f0845-119">Apply a Style to a WPF Control</span></span>

<span data-ttu-id="f0845-120">Görünümünü ve davranışını değiştirmek için WPF denetimine farklı stil uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0845-120">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>

1. <span data-ttu-id="f0845-121">Windows `Form1` Forms Designer'da açın.</span><span class="sxs-lookup"><span data-stu-id="f0845-121">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="f0845-122">Araç **Kutusunda,** formda bir `UserControl1` örneğini `UserControl1` oluşturmak için çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f0845-122">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

   <span data-ttu-id="f0845-123">Bir örneği `UserControl1` adlı <xref:System.Windows.Forms.Integration.ElementHost> `elementHost1`yeni bir denetimde barındırılır.</span><span class="sxs-lookup"><span data-stu-id="f0845-123">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

1. <span data-ttu-id="f0845-124">Akıllı etiket panelinde `elementHost1`açılan listeden **Barındırılan İçeriği** Düzenle'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f0845-124">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>

   <span data-ttu-id="f0845-125">`UserControl1`WPF Tasarımcısı'nda açılır.</span><span class="sxs-lookup"><span data-stu-id="f0845-125">`UserControl1` opens in the WPF Designer.</span></span>

1. <span data-ttu-id="f0845-126">XAML görünümünde, açılış etiketinden sonra `<UserControl>` aşağıdaki XAML'yi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f0845-126">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span> <span data-ttu-id="f0845-127">Bu XAML zıt degrade kenarlıklı bir degrade oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f0845-127">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="f0845-128">Denetim tıklatıldığında, basıldığında düğme görünümü oluşturmak için degradeler değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="f0845-128">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="f0845-129">Daha fazla bilgi için [Stil ve Templating'e](../../../desktop-wpf/fundamentals/styles-templates-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f0845-129">For more information, see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

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

1. <span data-ttu-id="f0845-130">İptal `SimpleButton` düğmesinin `<Button>` etiketine aşağıdaki XAML'yi ekleyerek önceki adımda tanımlanan stili **İptal** düğmesine uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f0845-130">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the **Cancel** button.</span></span>

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   <span data-ttu-id="f0845-131">Düğme bildiriminiz aşağıdaki XAML'ye benzeyecektir:</span><span class="sxs-lookup"><span data-stu-id="f0845-131">Your button declaration will resemble the following XAML:</span></span>

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. <span data-ttu-id="f0845-132">Projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="f0845-132">Build the project.</span></span>

1. <span data-ttu-id="f0845-133">Windows `Form1` Forms Designer'da açın.</span><span class="sxs-lookup"><span data-stu-id="f0845-133">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="f0845-134">Yeni stil düğme denetimine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f0845-134">The new style is applied to the button control.</span></span>

1. <span data-ttu-id="f0845-135">Hata **Ayıklama** menüsünden, uygulamayı çalıştırmak için **Hata Ayıklama'yı Başlat'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="f0845-135">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>

1. <span data-ttu-id="f0845-136">**Tamam** ve **İptal** düğmelerini tıklatın ve farklılıkları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="f0845-136">Click the **OK** and **Cancel** buttons and view the differences.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0845-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0845-137">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="f0845-138">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="f0845-138">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="f0845-139">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="f0845-139">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="f0845-140">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="f0845-140">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="f0845-141">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="f0845-141">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="f0845-142">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f0845-142">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
