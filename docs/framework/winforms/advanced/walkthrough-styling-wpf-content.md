---
title: "İzlenecek yol: WPF İçeriği için Stil Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0fa4772ebb321f927087fe13d0d50a6ae8145e55
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-styling-wpf-content"></a><span data-ttu-id="3a99f-102">İzlenecek yol: WPF İçeriği için Stil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3a99f-102">Walkthrough: Styling WPF Content</span></span>
<span data-ttu-id="3a99f-103">Bu kılavuz, bir Windows formunda barındırılan bir Windows Presentation Foundation (WPF) denetim stil uygulamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a99f-103">This walkthrough show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>  
  
 <span data-ttu-id="3a99f-104">Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="3a99f-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="3a99f-105">Projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3a99f-105">Create the project.</span></span>  
  
-   <span data-ttu-id="3a99f-106">WPF denetim türü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3a99f-106">Create the WPF control type.</span></span>  
  
-   <span data-ttu-id="3a99f-107">Stil WPF denetimi uygular.</span><span class="sxs-lookup"><span data-stu-id="3a99f-107">Apply a style to the WPF control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a99f-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="3a99f-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="3a99f-109">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="3a99f-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="3a99f-110">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="3a99f-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3a99f-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="3a99f-111">Prerequisites</span></span>  
 <span data-ttu-id="3a99f-112">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="3a99f-112">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="3a99f-113">.</span><span class="sxs-lookup"><span data-stu-id="3a99f-113">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="3a99f-114">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3a99f-114">Creating the Project</span></span>  
 <span data-ttu-id="3a99f-115">Windows Forms projesi oluşturmak için ilk adımdır bakın.</span><span class="sxs-lookup"><span data-stu-id="3a99f-115">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a99f-116">WPF içeriği barındırma, yalnızca C# ve Visual Basic projeleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3a99f-116">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="3a99f-117">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3a99f-117">To create the project</span></span>  
  
-   <span data-ttu-id="3a99f-118">Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `StylingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="3a99f-118">Create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="3a99f-119">WPF denetim türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="3a99f-119">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="3a99f-120">Bir WPF denetim türü için Proje ekledikten sonra içinde barındırabilir bir <xref:System.Windows.Forms.Integration.ElementHost> denetim.</span><span class="sxs-lookup"><span data-stu-id="3a99f-120">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="3a99f-121">WPF denetim türleri oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3a99f-121">To create WPF control types</span></span>  
  
1.  <span data-ttu-id="3a99f-122">Yeni bir WPF eklemek <xref:System.Windows.Controls.UserControl> çözüme proje.</span><span class="sxs-lookup"><span data-stu-id="3a99f-122">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="3a99f-123">Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="3a99f-123">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="3a99f-124">Daha fazla bilgi için bkz: [izlenecek yol: oluşturma yeni WPF içeriği Windows formlarında tasarım zamanında](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="3a99f-124">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="3a99f-125">Tasarım görünümü içinde olduğundan emin olun `UserControl1` seçilir.</span><span class="sxs-lookup"><span data-stu-id="3a99f-125">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="3a99f-126">Daha fazla bilgi için bkz: [nasıl yapılır: seçin ve tasarım yüzeyine taşıma öğelerde](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="3a99f-126">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="3a99f-127">İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.</span><span class="sxs-lookup"><span data-stu-id="3a99f-127">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="3a99f-128">Ekleme bir <xref:System.Windows.Controls.Button?displayProperty=nameWithType> denetimini <xref:System.Windows.Controls.UserControl> ve değeri ayarlayın <xref:System.Windows.Controls.ContentControl.Content%2A> özelliğine **iptal**.</span><span class="sxs-lookup"><span data-stu-id="3a99f-128">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>  
  
5.  <span data-ttu-id="3a99f-129">İkinci bir ekleme <xref:System.Windows.Controls.Button?displayProperty=nameWithType> denetimini <xref:System.Windows.Controls.UserControl> ve değeri ayarlayın <xref:System.Windows.Controls.ContentControl.Content%2A> özelliğine **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="3a99f-129">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>  
  
6.  <span data-ttu-id="3a99f-130">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3a99f-130">Build the project.</span></span>  
  
## <a name="applying-a-style-to-a-wpf-control"></a><span data-ttu-id="3a99f-131">WPF denetimi için bir stil uygulama</span><span class="sxs-lookup"><span data-stu-id="3a99f-131">Applying a Style to a WPF Control</span></span>  
 <span data-ttu-id="3a99f-132">Farklı bir WPF denetimine görünümünü ve davranışını değiştirmek için stil oluşturma uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a99f-132">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>  
  
#### <a name="to-apply-a-style-to-a-wpf-control"></a><span data-ttu-id="3a99f-133">WPF denetimi için bir stil uygulamak için</span><span class="sxs-lookup"><span data-stu-id="3a99f-133">To apply a style to a WPF control</span></span>  
  
1.  <span data-ttu-id="3a99f-134">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="3a99f-134">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="3a99f-135">İçinde **araç**, çift `UserControl1` bir örneğini oluşturmak için `UserControl1` form üzerinde.</span><span class="sxs-lookup"><span data-stu-id="3a99f-135">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="3a99f-136">Örneği `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="3a99f-136">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="3a99f-137">İçin akıllı etiket panelinde `elementHost1`, tıklatın **barındırılan içeriği Düzenle** aşağı açılan listeden.</span><span class="sxs-lookup"><span data-stu-id="3a99f-137">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>  
  
     <span data-ttu-id="3a99f-138">`UserControl1`açılır [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3a99f-138">`UserControl1` opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="3a99f-139">XAML Görünümü'nde sonra aşağıdaki XAML eklemek `<UserControl>` etiketi açma.</span><span class="sxs-lookup"><span data-stu-id="3a99f-139">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span>  
  
     <span data-ttu-id="3a99f-140">Bu XAML gradyan karşıt gradyan kenarlık oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3a99f-140">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="3a99f-141">Denetim tıklatıldığında gradyan basılan düğme görünümünü oluşturmak için değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="3a99f-141">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="3a99f-142">Daha fazla bilgi için bkz: [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="3a99f-142">For more information, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
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
  
1.  <span data-ttu-id="3a99f-143">Uygulama `SimpleButton` aşağıdaki XAML'de ekleyerek iptal düğmesi için önceki adımda tanımlanan stili `<Button>` iptal düğmesi etiketi.</span><span class="sxs-lookup"><span data-stu-id="3a99f-143">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the Cancel button.</span></span>  
  
    ```  
    Style="{StaticResource SimpleButton}  
    ```  
  
     <span data-ttu-id="3a99f-144">Düğme bildirimi aşağıdaki XAML benzeyecektir.</span><span class="sxs-lookup"><span data-stu-id="3a99f-144">Your button declaration will resemble the following XAML.</span></span>  
  
```xaml  
<Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"  
                Style="{StaticResource SimpleButton}">Cancel</Button>  
```  
  
1.  <span data-ttu-id="3a99f-145">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3a99f-145">Build the project.</span></span>  
  
2.  <span data-ttu-id="3a99f-146">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="3a99f-146">Open `Form1` in the Windows Forms Designer.</span></span>  
  
3.  <span data-ttu-id="3a99f-147">Yeni stil düğme denetimi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3a99f-147">The new style is applied to the button control.</span></span>  
  
4.  <span data-ttu-id="3a99f-148">Gelen **hata ayıklama** menüsünde, select **hata ayıklamayı Başlat** uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3a99f-148">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>  
  
5.  <span data-ttu-id="3a99f-149">Tamam ve İptal düğmeleri tıklayın ve farkları görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a99f-149">Click the OK and Cancel buttons and view the differences.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a99f-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3a99f-150">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="3a99f-151">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="3a99f-151">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="3a99f-152">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="3a99f-152">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="3a99f-153">WPF Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="3a99f-153">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="3a99f-154">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="3a99f-154">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="3a99f-155">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3a99f-155">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
