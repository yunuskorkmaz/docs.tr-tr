---
title: 'İzlenecek yol: WPF içeriği için stil oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
ms.openlocfilehash: ef81d9272acdddfc7d547de6f44725481e55dc3e
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303731"
---
# <a name="walkthrough-styling-wpf-content"></a><span data-ttu-id="71566-102">İzlenecek yol: WPF içeriği için stil oluşturma</span><span class="sxs-lookup"><span data-stu-id="71566-102">Walkthrough: Styling WPF Content</span></span>
<span data-ttu-id="71566-103">Bu izlenecek yol, bir Windows Form üzerinde barındırılan bir Windows Presentation Foundation (WPF) denetimine stil uygulamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="71566-103">This walkthrough show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

 <span data-ttu-id="71566-104">Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="71566-104">In this walkthrough, you perform the following tasks:</span></span>

-   <span data-ttu-id="71566-105">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="71566-105">Create the project.</span></span>

-   <span data-ttu-id="71566-106">WPF denetim türü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="71566-106">Create the WPF control type.</span></span>

-   <span data-ttu-id="71566-107">Bir stil WPF denetimi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="71566-107">Apply a style to the WPF control.</span></span>

> [!NOTE]
>  <span data-ttu-id="71566-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="71566-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="71566-109">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="71566-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="71566-110">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="71566-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="71566-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="71566-111">Prerequisites</span></span>  
 <span data-ttu-id="71566-112">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="71566-112">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="71566-113">Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="71566-113">Visual Studio 2012.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="71566-114">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="71566-114">Creating the Project</span></span>  
 <span data-ttu-id="71566-115">İlk adım Windows Forms projesi oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="71566-115">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71566-116">WPF içeriği barındırma, yalnızca C# ve Visual Basic projelerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="71566-116">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="71566-117">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="71566-117">To create the project</span></span>  
  
-   <span data-ttu-id="71566-118">Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `StylingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="71566-118">Create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="71566-119">WPF denetim türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="71566-119">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="71566-120">WPF denetim türü projeye ekledikten sonra içinde barındırabilirsiniz bir <xref:System.Windows.Forms.Integration.ElementHost> denetimi.</span><span class="sxs-lookup"><span data-stu-id="71566-120">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="71566-121">WPF denetim türleri oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="71566-121">To create WPF control types</span></span>  
  
1.  <span data-ttu-id="71566-122">Yeni bir WPF ekleme <xref:System.Windows.Controls.UserControl> çözüme bir proje.</span><span class="sxs-lookup"><span data-stu-id="71566-122">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="71566-123">Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="71566-123">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="71566-124">Daha fazla bilgi için [izlenecek yol: Yeni bir WPF içeriği Windows formlarında tasarım zamanında oluşturma](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="71566-124">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="71566-125">Tasarım görünümünde emin `UserControl1` seçilir.</span><span class="sxs-lookup"><span data-stu-id="71566-125">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="71566-126">Daha fazla bilgi için [nasıl yapılır: Seçin ve tasarım yüzeyine öğeleri Taşı](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="71566-126">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>  
  
3.  <span data-ttu-id="71566-127">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.</span><span class="sxs-lookup"><span data-stu-id="71566-127">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="71566-128">Ekleme bir <xref:System.Windows.Controls.Button?displayProperty=nameWithType> denetimini <xref:System.Windows.Controls.UserControl> ve değerini ayarlama <xref:System.Windows.Controls.ContentControl.Content%2A> özelliğini **iptal**.</span><span class="sxs-lookup"><span data-stu-id="71566-128">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>  
  
5.  <span data-ttu-id="71566-129">İkinci bir ekleme <xref:System.Windows.Controls.Button?displayProperty=nameWithType> denetimini <xref:System.Windows.Controls.UserControl> ve değerini ayarlama <xref:System.Windows.Controls.ContentControl.Content%2A> özelliğini **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="71566-129">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>  
  
6.  <span data-ttu-id="71566-130">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="71566-130">Build the project.</span></span>  
  
## <a name="applying-a-style-to-a-wpf-control"></a><span data-ttu-id="71566-131">WPF denetime stil uygulama</span><span class="sxs-lookup"><span data-stu-id="71566-131">Applying a Style to a WPF Control</span></span>  
 <span data-ttu-id="71566-132">Farklı görünümünü ve davranışını değiştirmek için bir WPF denetimi stil uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71566-132">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>  
  
#### <a name="to-apply-a-style-to-a-wpf-control"></a><span data-ttu-id="71566-133">Bir WPF denetimine stil uygulamak için</span><span class="sxs-lookup"><span data-stu-id="71566-133">To apply a style to a WPF control</span></span>  
  
1.  <span data-ttu-id="71566-134">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="71566-134">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="71566-135">İçinde **araç kutusu**, çift `UserControl1` bir örneğini oluşturmak için `UserControl1` form üzerinde.</span><span class="sxs-lookup"><span data-stu-id="71566-135">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="71566-136">Örneği `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="71566-136">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="71566-137">Akıllı etiket panelinde `elementHost1`, tıklayın **barındırılan içerik Düzenle** aşağı açılan listeden.</span><span class="sxs-lookup"><span data-stu-id="71566-137">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>  
  
     <span data-ttu-id="71566-138">`UserControl1` açılır [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="71566-138">`UserControl1` opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="71566-139">XAML Görünümü'nde, aşağıdaki XAML sonra Ekle `<UserControl>` etiketiyle.</span><span class="sxs-lookup"><span data-stu-id="71566-139">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span>  
  
     <span data-ttu-id="71566-140">Bu XAML gradyan karşıt gradyan kenarlıklı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="71566-140">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="71566-141">Denetim tıklandığında gradyanlar basılan düğme görünümünü oluşturmak için değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="71566-141">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="71566-142">Daha fazla bilgi için [stil ve şablon oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="71566-142">For more information, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
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
  
1.  <span data-ttu-id="71566-143">Uygulama `SimpleButton` aşağıdaki XAML içinde ekleyerek iptal düğmesi için önceki adımda tanımlanan stil `<Button>` İptal düğmesinin etiketi.</span><span class="sxs-lookup"><span data-stu-id="71566-143">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the Cancel button.</span></span>  
  
    ```  
    Style="{StaticResource SimpleButton}  
    ```  
  
     <span data-ttu-id="71566-144">Düğme bildirimi, aşağıdaki XAML andıracaktır.</span><span class="sxs-lookup"><span data-stu-id="71566-144">Your button declaration will resemble the following XAML.</span></span>  
  
```xaml  
<Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"  
                Style="{StaticResource SimpleButton}">Cancel</Button>  
```  
  
1.  <span data-ttu-id="71566-145">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="71566-145">Build the project.</span></span>  
  
2.  <span data-ttu-id="71566-146">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="71566-146">Open `Form1` in the Windows Forms Designer.</span></span>  
  
3.  <span data-ttu-id="71566-147">Düğme denetimine yeni stil uygulanır.</span><span class="sxs-lookup"><span data-stu-id="71566-147">The new style is applied to the button control.</span></span>  
  
4.  <span data-ttu-id="71566-148">Gelen **hata ayıklama** menüsünde **hata ayıklamayı Başlat** uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="71566-148">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>  
  
5.  <span data-ttu-id="71566-149">Tamam ve İptal düğmeleri tıklatabilir ve farkları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="71566-149">Click the OK and Cancel buttons and view the differences.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71566-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71566-150">See also</span></span>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="71566-151">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="71566-151">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="71566-152">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="71566-152">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)
- [<span data-ttu-id="71566-153">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="71566-153">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="71566-154">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="71566-154">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="71566-155">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="71566-155">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
