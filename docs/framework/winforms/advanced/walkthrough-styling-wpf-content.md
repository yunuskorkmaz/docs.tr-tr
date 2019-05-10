---
title: 'İzlenecek yol: WPF İçeriği için Stil Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
ms.openlocfilehash: d815311a89ba09ade7e3092ca4eeab67cbe20bd0
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211253"
---
# <a name="walkthrough-style-wpf-content"></a><span data-ttu-id="c4881-102">İzlenecek yol: WPF içeriği için stil</span><span class="sxs-lookup"><span data-stu-id="c4881-102">Walkthrough: Style WPF content</span></span>

<span data-ttu-id="c4881-103">Bu izlenecek yol, bir Windows Form üzerinde barındırılan bir Windows Presentation Foundation (WPF) denetimine stil uygulamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4881-103">This walkthrough show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

 <span data-ttu-id="c4881-104">Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="c4881-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="c4881-105">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c4881-105">Create the project.</span></span>

- <span data-ttu-id="c4881-106">WPF denetim türü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c4881-106">Create the WPF control type.</span></span>

- <span data-ttu-id="c4881-107">Bir stil uygulamak için WPF control.a</span><span class="sxs-lookup"><span data-stu-id="c4881-107">Apply a style to the WPF control.a</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c4881-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c4881-108">Prerequisites</span></span>

<span data-ttu-id="c4881-109">Bu izlenecek yolu tamamlamak için Visual Studio ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="c4881-109">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="c4881-110">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c4881-110">Create the project</span></span>

<span data-ttu-id="c4881-111">Visual Studio'yu açın ve Visual Basic veya Visual içinde yeni bir Windows Forms uygulaması projesi oluşturma C# adlı `StylingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="c4881-111">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="c4881-112">WPF içeriği barındırma, yalnızca C# ve Visual Basic projelerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c4881-112">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="c4881-113">WPF denetim türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="c4881-113">Create the WPF control types</span></span>

<span data-ttu-id="c4881-114">WPF denetim türü projeye ekledikten sonra içinde barındırabilirsiniz bir <xref:System.Windows.Forms.Integration.ElementHost> denetimi.</span><span class="sxs-lookup"><span data-stu-id="c4881-114">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

1. <span data-ttu-id="c4881-115">Yeni bir WPF ekleme <xref:System.Windows.Controls.UserControl> çözüme bir proje.</span><span class="sxs-lookup"><span data-stu-id="c4881-115">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="c4881-116">Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="c4881-116">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="c4881-117">Daha fazla bilgi için [izlenecek yol: Yeni bir WPF içeriği Windows formlarında tasarım zamanında oluşturma](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="c4881-117">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="c4881-118">Tasarım görünümünde emin `UserControl1` seçilir.</span><span class="sxs-lookup"><span data-stu-id="c4881-118">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="c4881-119">Daha fazla bilgi için [nasıl yapılır: Seçin ve tasarım yüzeyine öğeleri Taşı](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c4881-119">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="c4881-120">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.</span><span class="sxs-lookup"><span data-stu-id="c4881-120">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

4. <span data-ttu-id="c4881-121">Ekleme bir <xref:System.Windows.Controls.Button?displayProperty=nameWithType> denetimini <xref:System.Windows.Controls.UserControl> ve değerini ayarlama <xref:System.Windows.Controls.ContentControl.Content%2A> özelliğini **iptal**.</span><span class="sxs-lookup"><span data-stu-id="c4881-121">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>

5. <span data-ttu-id="c4881-122">İkinci bir ekleme <xref:System.Windows.Controls.Button?displayProperty=nameWithType> denetimini <xref:System.Windows.Controls.UserControl> ve değerini ayarlama <xref:System.Windows.Controls.ContentControl.Content%2A> özelliğini **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c4881-122">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>

6. <span data-ttu-id="c4881-123">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c4881-123">Build the project.</span></span>

## <a name="apply-a-style-to-a-wpf-control"></a><span data-ttu-id="c4881-124">WPF denetime stil uygulama</span><span class="sxs-lookup"><span data-stu-id="c4881-124">Apply a Style to a WPF Control</span></span>

<span data-ttu-id="c4881-125">Farklı görünümünü ve davranışını değiştirmek için bir WPF denetimi stil uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4881-125">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>

1. <span data-ttu-id="c4881-126">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="c4881-126">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="c4881-127">İçinde **araç kutusu**, çift `UserControl1` bir örneğini oluşturmak için `UserControl1` form üzerinde.</span><span class="sxs-lookup"><span data-stu-id="c4881-127">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

     <span data-ttu-id="c4881-128">Örneği `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="c4881-128">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

3. <span data-ttu-id="c4881-129">Akıllı etiket panelinde `elementHost1`, tıklayın **barındırılan içerik Düzenle** aşağı açılan listeden.</span><span class="sxs-lookup"><span data-stu-id="c4881-129">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>

     <span data-ttu-id="c4881-130">`UserControl1` açılır [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c4881-130">`UserControl1` opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

4. <span data-ttu-id="c4881-131">XAML Görünümü'nde, aşağıdaki XAML sonra Ekle `<UserControl>` etiketiyle.</span><span class="sxs-lookup"><span data-stu-id="c4881-131">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span>

     <span data-ttu-id="c4881-132">Bu XAML gradyan karşıt gradyan kenarlıklı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c4881-132">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="c4881-133">Denetim tıklandığında gradyanlar basılan düğme görünümünü oluşturmak için değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="c4881-133">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="c4881-134">Daha fazla bilgi için [stil ve şablon oluşturma](../../wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="c4881-134">For more information, see [Styling and Templating](../../wpf/controls/styling-and-templating.md).</span></span>

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

4. <span data-ttu-id="c4881-135">Uygulama `SimpleButton` aşağıdaki XAML içinde ekleyerek iptal düğmesi için önceki adımda tanımlanan stil `<Button>` İptal düğmesinin etiketi.</span><span class="sxs-lookup"><span data-stu-id="c4881-135">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the Cancel button.</span></span>

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   <span data-ttu-id="c4881-136">Düğme bildirimi, aşağıdaki XAML benzeyecektir:</span><span class="sxs-lookup"><span data-stu-id="c4881-136">Your button declaration will resemble the following XAML:</span></span>

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

5. <span data-ttu-id="c4881-137">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c4881-137">Build the project.</span></span>

6. <span data-ttu-id="c4881-138">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="c4881-138">Open `Form1` in the Windows Forms Designer.</span></span>

7. <span data-ttu-id="c4881-139">Düğme denetimine yeni stil uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c4881-139">The new style is applied to the button control.</span></span>

8. <span data-ttu-id="c4881-140">Gelen **hata ayıklama** menüsünde **hata ayıklamayı Başlat** uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c4881-140">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>

9. <span data-ttu-id="c4881-141">Tamam ve İptal düğmeleri tıklatabilir ve farkları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="c4881-141">Click the OK and Cancel buttons and view the differences.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4881-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4881-142">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="c4881-143">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="c4881-143">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="c4881-144">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="c4881-144">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="c4881-145">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="c4881-145">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="c4881-146">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="c4881-146">XAML Overview (WPF)</span></span>](../../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="c4881-147">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c4881-147">Styling and Templating</span></span>](../../wpf/controls/styling-and-templating.md)
