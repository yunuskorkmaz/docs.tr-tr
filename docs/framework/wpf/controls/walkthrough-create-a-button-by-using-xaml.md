---
title: 'İzlenecek yol: XAML Kullanarak bir Düğme Oluşturma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 94ec5e56862190026b43331488cbc699fe7dfda4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a><span data-ttu-id="ec774-102">İzlenecek yol: XAML Kullanarak bir Düğme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ec774-102">Walkthrough: Create a Button by Using XAML</span></span>
<span data-ttu-id="ec774-103">Animasyonlu bir düğme kullanılmak üzere oluşturma konusunda bilgi almak için bu kılavuzun amacı olan bir [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="ec774-103">The objective of this walkthrough is to learn how to create an animated button for use in a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] application.</span></span> <span data-ttu-id="ec774-104">Bu kılavuz, kodu yeniden kullanma ve düğme mantığının ayrılması düğme bildiriminden izin veren bir özelleştirilmiş düğme kaynak oluşturmak için stilleri ve bir şablonu kullanır.</span><span class="sxs-lookup"><span data-stu-id="ec774-104">This walkthrough uses styles and a template to create a customized button resource that allows reuse of code and separation of button logic from the button declaration.</span></span> <span data-ttu-id="ec774-105">Bu kılavuzda tamamen yazılmış [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ec774-105">This walkthrough is written entirely in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ec774-106">Bu kılavuzda, uygulamayı yazarak veya kopyalama ve yapıştırma oluşturmak için adımlarında size rehberlik [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Microsoft Visual Studio uygulamasına.</span><span class="sxs-lookup"><span data-stu-id="ec774-106">This walkthrough guides you through the steps for creating the application by typing or copying and pasting [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] into Microsoft Visual Studio.</span></span> <span data-ttu-id="ec774-107">Aynı uygulamayı oluşturmak için bkz. tasarım aracı (Microsoft Expression Blend) kullanmayı öğrenmek tercih ederseniz [oluştur düğmesi Microsoft Expression Blend kullanarak tarafından](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span><span class="sxs-lookup"><span data-stu-id="ec774-107">If you would prefer to learn how to use a design tool (Microsoft Expression Blend) to create the same application, see [Create a Button by Using Microsoft Expression Blend](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span></span>  
  
 <span data-ttu-id="ec774-108">Aşağıdaki şekil tamamlanmış düğmeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec774-108">The following figure shows the finished buttons.</span></span>  
  
 <span data-ttu-id="ec774-109">![XAML kullanılarak oluşturulmuş özel düğmeler](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="ec774-109">![Custom buttons that were created by using XAML](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>  
  
## <a name="create-basic-buttons"></a><span data-ttu-id="ec774-110">Temel düğmeler oluşturma</span><span class="sxs-lookup"><span data-stu-id="ec774-110">Create Basic Buttons</span></span>  
 <span data-ttu-id="ec774-111">Yeni proje oluşturma ve pencereyi birkaç düğme ekleyerek başlayalım tıklatın.</span><span class="sxs-lookup"><span data-stu-id="ec774-111">Let's start by creating a new project and adding a few buttons to the window.</span></span>  
  
#### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a><span data-ttu-id="ec774-112">Yeni bir WPF projesi oluşturun ve pencereyi düğme ekleme</span><span class="sxs-lookup"><span data-stu-id="ec774-112">To create a new WPF project and add buttons to the window</span></span>  
  
1.  <span data-ttu-id="ec774-113">Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="ec774-113">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="ec774-114">**Yeni bir WPF projesi oluşturun:** üzerinde **dosya** menüsündeki **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="ec774-114">**Create a new WPF project:** On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="ec774-115">Bul **Windows uygulaması (WPF)** şablonu ve adını "AnimatedButton olarak" proje.</span><span class="sxs-lookup"><span data-stu-id="ec774-115">Find the **Windows Application (WPF)** template and name the project "AnimatedButton".</span></span> <span data-ttu-id="ec774-116">Bu uygulama için bir çatı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ec774-116">This will create the skeleton for the application.</span></span>  
  
3.  <span data-ttu-id="ec774-117">**Temel varsayılan düğme ekleme:** bu kılavuz için gereken tüm dosyaları şablon tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ec774-117">**Add basic default buttons:** All the files you need for this walkthrough are provided by the template.</span></span> <span data-ttu-id="ec774-118">Çift Çözüm Gezgini'nde tıklatarak Window1.xaml dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="ec774-118">Open the Window1.xaml file by double clicking it in Solution Explorer.</span></span> <span data-ttu-id="ec774-119">Varsayılan olarak, var olan bir <xref:System.Windows.Controls.Grid> Window1.xaml öğesinde.</span><span class="sxs-lookup"><span data-stu-id="ec774-119">By default, there is a <xref:System.Windows.Controls.Grid> element in Window1.xaml.</span></span> <span data-ttu-id="ec774-120">Kaldırma <xref:System.Windows.Controls.Grid> öğesi ve birkaç düğme ekleme [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sayfa yazarak veya kopyalama ve yapıştırma Window1.xaml aşağıdaki vurgulanmış kodu:</span><span class="sxs-lookup"><span data-stu-id="ec774-120">Remove the <xref:System.Windows.Controls.Grid> element and add a few buttons to the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page by typing or copy and pasting the following highlighted code to Window1.xaml:</span></span>  
  
    ```xaml  
    <Window x:Class="AnimatedButton.Window1"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      Title="AnimatedButton" Height="300" Width="300"   
      Background="Black">   <!-- Buttons arranged vertically inside a StackPanel. -->   <StackPanel HorizontalAlignment="Left">     <Button>Button 1</Button>     <Button>Button 2</Button>     <Button>Button 3</Button>   </StackPanel>  
  
    </Window>  
    ```  
  
     <span data-ttu-id="ec774-121">Uygulamayı çalıştırmak için F5 tuşuna basın; Aşağıdaki şekil gibi görünen düğmeler kümesi görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec774-121">Press F5 to run the application; you should see a set of buttons that looks like the following figure.</span></span>  
  
     <span data-ttu-id="ec774-122">![Üç temel düğme](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span><span class="sxs-lookup"><span data-stu-id="ec774-122">![Three basic buttons](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span></span>  
  
     <span data-ttu-id="ec774-123">Temel düğmeleri oluşturduğunuza göre Window1.xaml dosyasındaki çalışma tamamlanmış demektir.</span><span class="sxs-lookup"><span data-stu-id="ec774-123">Now that you have created the basic buttons, you are finished working in the Window1.xaml file.</span></span> <span data-ttu-id="ec774-124">İzlenecek yol kalan stilleri ve düğmeleri için bir şablon tanımlama app.xaml dosyası üzerinde odaklanır.</span><span class="sxs-lookup"><span data-stu-id="ec774-124">The rest of the walkthrough focuses on the app.xaml file, defining styles and a template for the buttons.</span></span>  
  
## <a name="set-basic-properties"></a><span data-ttu-id="ec774-125">Temel özellikleri ayarlama</span><span class="sxs-lookup"><span data-stu-id="ec774-125">Set Basic Properties</span></span>  
 <span data-ttu-id="ec774-126">Ardından, şimdi bazı özellikler düğmesi görünümünü ve düzenini denetlemek için bu düğmelerin ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ec774-126">Next, let's set some properties on these buttons to control the button appearance and layout.</span></span> <span data-ttu-id="ec774-127">Özellikler çubuğundaki düğmeler tek tek ayarlamak yerine, tüm uygulama düğmesi özelliklerini tanımlamak için kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="ec774-127">Rather than setting properties on the buttons individually, you will use resources to define button properties for the entire application.</span></span> <span data-ttu-id="ec774-128">Uygulama kaynakları için dış kavramsal olarak benzer [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] Web sayfaları için; ancak, çok daha güçlü kaynaklardır [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)], bu örneklerde sonuna göreceğiniz gibi.</span><span class="sxs-lookup"><span data-stu-id="ec774-128">Application resources are conceptually similar to external [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] for Web pages; however, resources are much more powerful than [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)], as you will see by the end of this walkthrough.</span></span> <span data-ttu-id="ec774-129">Kaynakları hakkında daha fazla bilgi edinmek için [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="ec774-129">To learn more about resources, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
#### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a><span data-ttu-id="ec774-130">Düğmelerin temel özelliklerini ayarlamak için stiller kullanmak için</span><span class="sxs-lookup"><span data-stu-id="ec774-130">To use styles to set basic properties on the buttons</span></span>  
  
1.  <span data-ttu-id="ec774-131">**Bir Application.Resources bloğu tanımlayın:** app.xaml açın ve aşağıdaki vurgulanmış biçimlendirmeyi zaten yoksa ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ec774-131">**Define an Application.Resources block:** Open app.xaml and add the following highlighted markup if it is not already there:</span></span>  
  
    ```xaml  
    <Application x:Class="AnimatedButton.App"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      StartupUri="Window1.xaml"  
      >  
      <Application.Resources>
        <!-- Resources for the entire application can be defined here. -->
      </Application.Resources>  
    </Application>  
    ```  
  
     <span data-ttu-id="ec774-132">Kaynak kapsamı kaynak tanımladığınız tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="ec774-132">Resource scope is determined by where you define the resource.</span></span> <span data-ttu-id="ec774-133">Kaynakları tanımlama `Application.Resources` app.xaml dosyası gelen herhangi bir uygulamada kullanılmak üzere kaynak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec774-133">Defining resources in `Application.Resources` in the app.xaml file enables the resource to be used from anywhere in the application.</span></span> <span data-ttu-id="ec774-134">Kaynaklarınızın kapsamını tanımlama hakkında daha fazla bilgi için bkz: [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="ec774-134">To learn more about defining the scope of your resources, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
2.  <span data-ttu-id="ec774-135">**Stil oluşturma ve onunla temel özellik değerlerini tanımlayabileceğiniz:** aşağıdaki biçimlendirmeleri eklemek `Application.Resources` bloğu.</span><span class="sxs-lookup"><span data-stu-id="ec774-135">**Create a style and define basic property values with it:** Add the following markup to the `Application.Resources` block.</span></span> <span data-ttu-id="ec774-136">Bu biçimlendirme oluşturur bir <xref:System.Windows.Style> uygulama ayarı, tüm düğmeleri uygulanan <xref:System.Windows.FrameworkElement.Width%2A> 90 düğmelerin ve <xref:System.Windows.FrameworkElement.Margin%2A> 10:</span><span class="sxs-lookup"><span data-stu-id="ec774-136">This markup creates a <xref:System.Windows.Style> that applies to all buttons in the application, setting the <xref:System.Windows.FrameworkElement.Width%2A> of the buttons to 90 and the <xref:System.Windows.FrameworkElement.Margin%2A> to 10:</span></span>  
  
    ```xaml  
    <Application.Resources>  
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>  
    </Application.Resources>  
    ```  
  
     <span data-ttu-id="ec774-137"><xref:System.Windows.Style.TargetType%2A> Özellik belirtir stil türündeki tüm nesnelere uygulanır <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="ec774-137">The <xref:System.Windows.Style.TargetType%2A> property specifies that the style applies to all objects of type <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="ec774-138">Her <xref:System.Windows.Setter> için farklı özellik değeri ayarlar <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="ec774-138">Each <xref:System.Windows.Setter> sets a different property value for the <xref:System.Windows.Style>.</span></span> <span data-ttu-id="ec774-139">Bu nedenle, bu noktada uygulamadaki her düğmenin genişliği 90 ve kenar boşluğu 10 vardır.</span><span class="sxs-lookup"><span data-stu-id="ec774-139">Therefore, at this point every button in the application has a width of 90 and a margin of 10.</span></span>  <span data-ttu-id="ec774-140">Uygulamayı çalıştırmak için F5 tuşuna basarsanız, aşağıdaki penceresine bakın.</span><span class="sxs-lookup"><span data-stu-id="ec774-140">If you press F5 to run the application, you see the following window.</span></span>  
  
     <span data-ttu-id="ec774-141">![Genişliği 90 ve kenar boşluğu 10 düğmeleriyle](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span><span class="sxs-lookup"><span data-stu-id="ec774-141">![Buttons with a width of 90 and a margin of 10](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span></span>  
  
     <span data-ttu-id="ec774-142">Çeşitli şekillerde hangi nesneleri hedeflenen ince ayar yapmak için de dahil olmak üzere, karmaşık özellik değerleri belirtme ve bile stilleri diğer stilleri için girdi olarak kullanarak stilleri ile yapabileceğiniz daha fazla yoktur.</span><span class="sxs-lookup"><span data-stu-id="ec774-142">There is much more you can do with styles, including a variety of ways to fine-tune what objects are targeted, specifying complex property values, and even using styles as input for other styles.</span></span> <span data-ttu-id="ec774-143">Daha fazla bilgi için bkz: [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="ec774-143">For more information, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
3.  <span data-ttu-id="ec774-144">**Bir kaynak için bir stil özellik değerini ayarla:** kaynakların yaygın olarak tanımlanan nesnelerin ve değerleri yeniden kullanmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec774-144">**Set a style property value to a resource:** Resources enable a simple way to reuse commonly defined objects and values.</span></span> <span data-ttu-id="ec774-145">Kodunuzu daha modüler hale getirmek için kaynakları kullanarak karmaşık değerleri tanımlamak özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="ec774-145">It is especially useful to define complex values using resources to make your code more modular.</span></span> <span data-ttu-id="ec774-146">Aşağıdaki vurgulanmış biçimlendirmeyi için app.xaml ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ec774-146">Add the following highlighted markup to app.xaml.</span></span>  
  
    ```xaml  
    <Application.Resources>  
      <LinearGradientBrush x:Key="GrayBlueGradientBrush" StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>  
      <Style TargetType="{x:Type Button}">  
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />  
        <Setter Property="Width" Value="80" />  
        <Setter Property="Margin" Value="10" />  
      </Style>  
    </Application.Resources>  
    ```  
  
     <span data-ttu-id="ec774-147">Doğrudan altında `Application.Resources` bloğu "GrayBlueGradientBrush" adlı bir kaynak oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="ec774-147">Directly under the `Application.Resources` block, you created a resource called "GrayBlueGradientBrush".</span></span> <span data-ttu-id="ec774-148">Bu kaynak yatay bir gradyan tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ec774-148">This resource defines a horizontal gradient.</span></span> <span data-ttu-id="ec774-149">Bu kaynak yerinden özellik değeri olarak kullanılabilir düğmesi stili ayarlayıcı içine dahil olmak üzere uygulamada <xref:System.Windows.Controls.Control.Background%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ec774-149">This resource can be used as a property value from anywhere in the application, including inside the button style setter for the <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="ec774-150">Şimdi, tüm düğmeleri sahip bir <xref:System.Windows.Controls.Control.Background%2A> Bu geçişin özellik değeri.</span><span class="sxs-lookup"><span data-stu-id="ec774-150">Now, all the buttons have a <xref:System.Windows.Controls.Control.Background%2A> property value of this gradient.</span></span>  
  
     <span data-ttu-id="ec774-151">Uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ec774-151">Press F5 to run the application.</span></span> <span data-ttu-id="ec774-152">Aşağıdaki gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="ec774-152">It should look like the following.</span></span>  
  
     <span data-ttu-id="ec774-153">![Gradyan arka planı düğmeleriyle](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span><span class="sxs-lookup"><span data-stu-id="ec774-153">![Buttons with a gradient background](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span></span>  
  
## <a name="create-a-template-that-defines-the-look-of-the-button"></a><span data-ttu-id="ec774-154">Düğmenin görünümünü tanımlayan bir şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="ec774-154">Create a Template That Defines the Look of the Button</span></span>  
 <span data-ttu-id="ec774-155">Bu bölümde, düğmenin (sunu) görünümünü özelleştiren bir şablon oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ec774-155">In this section, you create a template that customizes the appearance (presentation) of the button.</span></span> <span data-ttu-id="ec774-156">Düğme sunusu dikdörtgenler ve diğer bileşenler dahil olmak üzere çeşitli nesnelerin benzersiz bir görünüm düğmesi kazandırmak için oluşur.</span><span class="sxs-lookup"><span data-stu-id="ec774-156">The button presentation is made up of several objects including rectangles and other components to give the button a unique look.</span></span>  
  
 <span data-ttu-id="ec774-157">Şu ana kadar düğmeleri uygulamada nasıl göründüğünü denetim düğmesi özelliklerini değiştirme için sınırlı.</span><span class="sxs-lookup"><span data-stu-id="ec774-157">So far, the control of how buttons look in the application has been confined to changing properties of the button.</span></span> <span data-ttu-id="ec774-158">Ne düğmenin görünümünü daha köklü değişiklikler yapmak isterseniz?</span><span class="sxs-lookup"><span data-stu-id="ec774-158">What if you want to make more radical changes to the button's appearance?</span></span> <span data-ttu-id="ec774-159">Şablonlar, bir nesne sunumu üzerinde güçlü denetim etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="ec774-159">Templates enable powerful control over the presentation of an object.</span></span> <span data-ttu-id="ec774-160">Şablonları stilleri içinde kullanılabilir olmadığından (Bu kılavuzda düğmesi) stili uygulandığı tüm nesneler için bir şablon uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec774-160">Because templates can be used within styles, you can apply a template to all objects that the style applies to (in this walkthrough, the button).</span></span>  
  
#### <a name="to-use-the-template-to-define-the-look-of-the-button"></a><span data-ttu-id="ec774-161">Düğmenin görünümünü tanımlamak için şablonu kullanmak için</span><span class="sxs-lookup"><span data-stu-id="ec774-161">To use the template to define the look of the button</span></span>  
  
1.  <span data-ttu-id="ec774-162">**Şablonu ayarlayın:** gibi denetimlerin çünkü <xref:System.Windows.Controls.Button> sahip bir <xref:System.Windows.Controls.Control.Template%2A> özelliğine ayarlarız, yalnızca diğer özellik değerleri gibi şablon özellik değeri tanımlayabilirsiniz bir <xref:System.Windows.Style> kullanarak bir <xref:System.Windows.Setter>.</span><span class="sxs-lookup"><span data-stu-id="ec774-162">**Set up the template:** Because controls like <xref:System.Windows.Controls.Button> have a <xref:System.Windows.Controls.Control.Template%2A> property, you can define the template property value just like the other property values we have set in a <xref:System.Windows.Style> using a <xref:System.Windows.Setter>.</span></span> <span data-ttu-id="ec774-163">Aşağıdaki vurgulanmış biçimlendirmeyi düğmesi stilinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ec774-163">Add the following highlighted markup to your button style.</span></span>  
  
    ```xaml
    <Application.Resources>  
      <LinearGradientBrush x:Key="GrayBlueGradientBrush"   
        StartPoint="0,0" EndPoint="1,1">  
        <GradientStop Color="DarkGray" Offset="0" />  
        <GradientStop Color="#CCCCFF" Offset="0.5" />  
        <GradientStop Color="DarkGray" Offset="1" />  
      </LinearGradientBrush>  
      <Style TargetType="{x:Type Button}">  
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />  
        <Setter Property="Width" Value="80" />  
        <Setter Property="Margin" Value="10" />  
        <Setter Property="Template">
          <Setter.Value>
            <!-- The button template is defined here. -->
          </Setter.Value>
        </Setter>  
      </Style>  
    </Application.Resources>  
    ```  
  
2.  <span data-ttu-id="ec774-164">**Düğme sunusu alter:** bu noktada, şablonu tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec774-164">**Alter button presentation:** At this point, you need to define the template.</span></span> <span data-ttu-id="ec774-165">Aşağıdaki vurgulanmış biçimlendirmeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ec774-165">Add the following highlighted markup.</span></span> <span data-ttu-id="ec774-166">Bu biçimlendirme iki belirtir <xref:System.Windows.Shapes.Rectangle> yuvarlatılmış kenarlar ile öğeleri arkasından bir <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="ec774-166">This markup specifies two <xref:System.Windows.Shapes.Rectangle> elements with rounded edges, followed by a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="ec774-167"><xref:System.Windows.Controls.DockPanel> Kullanılan ana bilgisayara <xref:System.Windows.Controls.ContentPresenter> düğmesinin.</span><span class="sxs-lookup"><span data-stu-id="ec774-167">The <xref:System.Windows.Controls.DockPanel> is used to host the <xref:System.Windows.Controls.ContentPresenter> of the button.</span></span> <span data-ttu-id="ec774-168">A <xref:System.Windows.Controls.ContentPresenter> düğmenin içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ec774-168">A <xref:System.Windows.Controls.ContentPresenter> displays the content of the button.</span></span> <span data-ttu-id="ec774-169">Bu kılavuzda, içeriği metin ("Düğmesine 1", "Button 2", "Button 3") olur.</span><span class="sxs-lookup"><span data-stu-id="ec774-169">In this walkthrough, the content is text ("Button 1", "Button 2", "Button 3").</span></span> <span data-ttu-id="ec774-170">Tüm şablon bileşenleri (dikdörtgenler ve <xref:System.Windows.Controls.DockPanel>) içinde düzenlenmiştir bir <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="ec774-170">All of the template components (the rectangles and the <xref:System.Windows.Controls.DockPanel>) are laid out inside of a <xref:System.Windows.Controls.Grid>.</span></span>  
  
    ```xaml  
    <Setter.Value>  
      <ControlTemplate TargetType="Button">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}" ClipToBounds="True">
          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}" RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />
          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20" Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />
          <!-- Present Content (text) of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20" Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>
      </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     <span data-ttu-id="ec774-171">Uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ec774-171">Press F5 to run the application.</span></span> <span data-ttu-id="ec774-172">Aşağıdaki gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="ec774-172">It should look like the following.</span></span>  
  
     <span data-ttu-id="ec774-173">![](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")</span><span class="sxs-lookup"><span data-stu-id="ec774-173">![](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")</span></span>  
  
3.  <span data-ttu-id="ec774-174">**Şablona bir glasseffect şablonuna ekleyin:** cam sonra ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="ec774-174">**Add a glasseffect to the template:** Next you will add the glass.</span></span> <span data-ttu-id="ec774-175">İlk olarak, cam gradyan etkisi oluşturmak bazı kaynakları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ec774-175">First you create some resources that create a glass gradient effect.</span></span> <span data-ttu-id="ec774-176">İçindeki bu gradyan kaynaklarını herhangi bir yere ekleyin `Application.Resources` engelle:</span><span class="sxs-lookup"><span data-stu-id="ec774-176">Add these gradient resources anywhere within the `Application.Resources` block:</span></span>  
  
    ```xaml  
    <Application.Resources>  
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">     <GradientStop Color="WhiteSmoke" Offset="0.2" />     <GradientStop Color="Transparent" Offset="0.4" />     <GradientStop Color="WhiteSmoke" Offset="0.5" />     <GradientStop Color="Transparent" Offset="0.75" />     <GradientStop Color="WhiteSmoke" Offset="0.9" />     <GradientStop Color="Transparent" Offset="1" />   </GradientStopCollection>   <LinearGradientBrush x:Key="MyGlassBrushResource"     StartPoint="0,0" EndPoint="1,1" Opacity="0.75"     GradientStops="{StaticResource MyGlassGradientStopsResource}" />  
    <!-- Styles and other resources below here. -->  
    ```  
  
     <span data-ttu-id="ec774-177">Bu kaynaklar olarak kullanılan <xref:System.Windows.Shapes.Shape.Fill%2A> biz takın bir dikdörtgen için <xref:System.Windows.Controls.Grid> düğmesini şablonunun.</span><span class="sxs-lookup"><span data-stu-id="ec774-177">These resources are used as the <xref:System.Windows.Shapes.Shape.Fill%2A> for a rectangle that we insert into the <xref:System.Windows.Controls.Grid> of the button template.</span></span> <span data-ttu-id="ec774-178">Aşağıdaki vurgulanmış biçimlendirmeyi şablonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ec774-178">Add the following highlighted markup to the template.</span></span>  
  
    ```  
    <Setter.Value>  
      <ControlTemplate TargetType="{x:Type Button}">  
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}"  
    ClipToBounds="True">  
  
        <!-- Outer Rectangle with rounded corners. -->  
        <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"   
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"   
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />  
  
        <!-- Inner Rectangle with rounded corners. -->  
        <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"   
          VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20"   
          Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />  
  
        <!-- Glass Rectangle -->     <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"       VerticalAlignment="Stretch"       StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"       Fill="{StaticResource MyGlassBrushResource}"       RenderTransformOrigin="0.5,0.5">       <Rectangle.Stroke>         <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">           <LinearGradientBrush.GradientStops>             <GradientStop Offset="0.0" Color="LightBlue" />             <GradientStop Offset="1.0" Color="Gray" />           </LinearGradientBrush.GradientStops>         </LinearGradientBrush>       </Rectangle.Stroke>       <!-- These transforms have no effect as they are declared here.             The reason the transforms are included is to be targets             for animation (see later). -->       <Rectangle.RenderTransform>         <TransformGroup>           <ScaleTransform />           <RotateTransform />         </TransformGroup>       </Rectangle.RenderTransform>       <!-- A BevelBitmapEffect is applied to give the button a             "Beveled" look. -->       <Rectangle.BitmapEffect>         <BevelBitmapEffect />       </Rectangle.BitmapEffect>     </Rectangle>  
  
        <!-- Present Text of the button. -->  
        <DockPanel Name="myContentPresenterDockPanel">  
          <ContentPresenter x:Name="myContentPresenter" Margin="20"   
            Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />  
        </DockPanel>  
      </Grid>  
    </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     <span data-ttu-id="ec774-179">Dikkat <xref:System.Windows.UIElement.Opacity%2A> ile dikdörtgenin `x:Name` "glassCube" özelliği: 0, örneği çalıştırdığınızda, en üstte yer paylaşımlı Cam Dikdörtgen görmek için.</span><span class="sxs-lookup"><span data-stu-id="ec774-179">Notice that the <xref:System.Windows.UIElement.Opacity%2A> of the rectangle with the `x:Name` property of "glassCube" is 0, so when you run the sample, you do not see the glass rectangle overlaid on top.</span></span> <span data-ttu-id="ec774-180">Kullanıcı düğmesi ile etkileşim kurduğunda daha sonra Tetikleyiciler için şablonuna ekleyeceğiz olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="ec774-180">This is because we will later add triggers to the template for when the user interacts with the button.</span></span> <span data-ttu-id="ec774-181">Ancak, düğme nasıl şimdi değiştirerek göründüğünü görebilirsiniz <xref:System.Windows.UIElement.Opacity%2A> değeri 1 ve uygulamayı çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="ec774-181">However, you can see what the button looks like now by changing the <xref:System.Windows.UIElement.Opacity%2A> value to 1 and running the application.</span></span> <span data-ttu-id="ec774-182">Aşağıdaki şekle bakın.</span><span class="sxs-lookup"><span data-stu-id="ec774-182">See the following figure.</span></span> <span data-ttu-id="ec774-183">Bir sonraki adıma devam etmeden önce değiştirmek <xref:System.Windows.UIElement.Opacity%2A> 0 dön.</span><span class="sxs-lookup"><span data-stu-id="ec774-183">Before proceeding to the next step, change the <xref:System.Windows.UIElement.Opacity%2A> back to 0.</span></span>  
  
     <span data-ttu-id="ec774-184">![XAML kullanılarak oluşturulmuş özel düğmeler](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="ec774-184">![Custom buttons that were created by using XAML](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>  
  
## <a name="create-button-interactivity"></a><span data-ttu-id="ec774-185">Etkileşimli düğme oluşturma</span><span class="sxs-lookup"><span data-stu-id="ec774-185">Create Button Interactivity</span></span>  
 <span data-ttu-id="ec774-186">Bu bölümde, özellik tetikleyiciler ve özellik değerlerini değiştirmek ve fare işaretçisini düğmenin üzerine taşıyarak ve tıklatma gibi kullanıcı eylemleri yanıtta animasyonları çalıştırmak için olay tetikleyicileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ec774-186">In this section, you will create property triggers and event triggers to change property values and run animations in response to user actions such as moving the mouse pointer over the button and clicking.</span></span>  
  
 <span data-ttu-id="ec774-187">(Fare üzerinde fare bırakın, tıklatın ve benzeri) etkileşim eklemek için kolay bir yol, şablon veya stil içinde Tetikleyiciler tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="ec774-187">An easy way to add interactivity (mouse-over, mouse-leave, click, and so on) is to define triggers within your template or style.</span></span> <span data-ttu-id="ec774-188">Oluşturmak için bir <xref:System.Windows.Trigger>, bir özellik "koşul" gibi tanımlayın: düğme <xref:System.Windows.UIElement.IsMouseOver%2A> özellik değeri eşittir `true`.</span><span class="sxs-lookup"><span data-stu-id="ec774-188">To create a <xref:System.Windows.Trigger>, you define a property "condition" such as: The button <xref:System.Windows.UIElement.IsMouseOver%2A> property value is equal to `true`.</span></span> <span data-ttu-id="ec774-189">Tetikleme koşulu doğru olduğunda, gerçekleşmesi ayarlayıcılar (Eylem) tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="ec774-189">You then define setters (actions) that take place when the trigger condition is true.</span></span>  
  
#### <a name="to-create-button-interactivity"></a><span data-ttu-id="ec774-190">Etkileşimli düğme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ec774-190">To create button interactivity</span></span>  
  
1.  <span data-ttu-id="ec774-191">**Şablon tetikleyicileri ekleyin:** şablonunuza vurgulanmış biçimlendirmeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ec774-191">**Add template triggers:** Add the highlighted markup to your template.</span></span>  
  
    ```  
    <Setter.Value>  
      <ControlTemplate TargetType="{x:Type Button}">  
        <Grid Width="{TemplateBinding Width}"   
          Height="{TemplateBinding Height}" ClipToBounds="True">  
  
          <!-- Outer Rectangle with rounded corners. -->  
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"   
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"   
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />  
  
          <!-- Inner Rectangle with rounded corners. -->  
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"   
            VerticalAlignment="Stretch" Stroke="Transparent"   
            StrokeThickness="20"   
            Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20"   
          />  
  
          <!-- Glass Rectangle -->  
          <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"  
            VerticalAlignment="Stretch"  
            StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"  
            Fill="{StaticResource MyGlassBrushResource}"  
            RenderTransformOrigin="0.5,0.5">  
            <Rectangle.Stroke>  
              <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">  
                <LinearGradientBrush.GradientStops>  
                  <GradientStop Offset="0.0" Color="LightBlue" />  
                  <GradientStop Offset="1.0" Color="Gray" />  
                </LinearGradientBrush.GradientStops>  
              </LinearGradientBrush>  
            </Rectangle.Stroke>  
  
            <!-- These transforms have no effect as they   
                 are declared here.   
                 The reason the transforms are included is to be targets   
                 for animation (see later). -->  
            <Rectangle.RenderTransform>  
              <TransformGroup>  
                <ScaleTransform />  
                <RotateTransform />  
              </TransformGroup>  
            </Rectangle.RenderTransform>  
  
              <!-- A BevelBitmapEffect is applied to give the button a   
                   "Beveled" look. -->  
            <Rectangle.BitmapEffect>  
              <BevelBitmapEffect />  
            </Rectangle.BitmapEffect>  
          </Rectangle>  
  
          <!-- Present Text of the button. -->  
          <DockPanel Name="myContentPresenterDockPanel">  
            <ContentPresenter x:Name="myContentPresenter" Margin="20"   
              Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />  
          </DockPanel>  
        </Grid>  
  
        <ControlTemplate.Triggers>       <!-- Set action triggers for the buttons and define            what the button does in response to those triggers. -->     </ControlTemplate.Triggers>  
      </ControlTemplate>  
    </Setter.Value>  
    ```  
  
2.  <span data-ttu-id="ec774-192">**Özellik tetikleyicileri ekleyin:** vurgulanan biçimlendirmeleri eklemek `ControlTemplate.Triggers` engelle:</span><span class="sxs-lookup"><span data-stu-id="ec774-192">**Add property triggers:** Add the highlighted markup to the `ControlTemplate.Triggers` block:</span></span>  
  
    ```  
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     <span data-ttu-id="ec774-193">Uygulamayı çalıştırın ve fare işaretçisini düğmeleri çalışacak şekilde etkisini görmek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ec774-193">Press F5 to run the application and see the effect as you run the mouse pointer over the buttons.</span></span>  
  
3.  <span data-ttu-id="ec774-194">**Odak tetikleyicisi ekleyin:** ardından, düğme (örneğin, kullanıcı bunu tıklattıktan sonra) odağa sahip olduğunda durumu işlemek için bazı benzer ayarlayıcılar ekleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="ec774-194">**Add a focus trigger:** Next, we'll add some similar setters to handle the case when the button has focus (for example, after the user clicks it).</span></span>  
  
    ```  
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->  
      <Trigger Property="IsMouseOver" Value="True">  
  
        <!-- Below are three property settings that occur when the   
             condition is met (user mouses over button).  -->  
        <!-- Change the color of the outer rectangle when user          mouses over it. -->  
        <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"  
          Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />  
  
        <!-- Sets the glass opacity to 1, therefore, the          glass "appears" when user mouses over it. -->  
        <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />  
  
        <!-- Makes the text slightly blurry as though you were          looking at it through blurry glass. -->  
        <Setter Property="ContentPresenter.BitmapEffect"       TargetName="myContentPresenter">  
          <Setter.Value>  
            <BlurBitmapEffect Radius="1" />  
          </Setter.Value>  
        </Setter>  
      </Trigger>  
      <!-- Set properties when button has focus. -->   <Trigger Property="IsFocused" Value="true">     <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />     <Setter Property="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />   </Trigger>  
  
    </ControlTemplate.Triggers>  
    ```  
  
     <span data-ttu-id="ec774-195">Uygulamayı çalıştırın ve düğmeleri birini tıklatın için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ec774-195">Press F5 to run the application and click on one of the buttons.</span></span> <span data-ttu-id="ec774-196">Odağı hala içerdiğinden tıklattıktan sonra düğmesi vurgulanan kalır dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="ec774-196">Notice that the button stays highlighted after you click it because it still has focus.</span></span> <span data-ttu-id="ec774-197">Başka bir düğmesine tıklarsanız, sonuncu onu kaybederse ederken yeni düğme odağı kazanır.</span><span class="sxs-lookup"><span data-stu-id="ec774-197">If you click another button, the new button gains focus while the last one loses it.</span></span>  
  
4.  <span data-ttu-id="ec774-198">**İçin animasyon ekleme** <xref:System.Windows.UIElement.MouseEnter> **ve** <xref:System.Windows.UIElement.MouseLeave> **:** bazı animasyonları tetikleyicilere sonraki ekleriz.  </span><span class="sxs-lookup"><span data-stu-id="ec774-198">**Add animations for**  <xref:System.Windows.UIElement.MouseEnter> **and** <xref:System.Windows.UIElement.MouseLeave> **:** Next we add some animations to the triggers.</span></span> <span data-ttu-id="ec774-199">Herhangi bir yere içinde aşağıdaki biçimlendirmeleri eklemek `ControlTemplate.Triggers` bloğu.</span><span class="sxs-lookup"><span data-stu-id="ec774-199">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block.</span></span>  
  
    ```  
    <!-- Animations that start when mouse enters and leaves button. -->  
    <EventTrigger RoutedEvent="Mouse.MouseEnter">  
      <EventTrigger.Actions>  
        <BeginStoryboard Name="mouseEnterBeginStoryboard">  
          <Storyboard>  
          <!-- This animation makes the glass rectangle shrink in the X direction. -->  
            <DoubleAnimation Storyboard.TargetName="glassCube"   
              Storyboard.TargetProperty=  
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleX)"  
              By="-0.1" Duration="0:0:0.5" />  
            <!-- This animation makes the glass rectangle shrink in the Y direction. -->  
            <DoubleAnimation  
            Storyboard.TargetName="glassCube"   
              Storyboard.TargetProperty=  
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleY)"   
              By="-0.1" Duration="0:0:0.5" />  
          </Storyboard>  
        </BeginStoryboard>  
      </EventTrigger.Actions>  
    </EventTrigger>  
    <EventTrigger RoutedEvent="Mouse.MouseLeave">  
      <EventTrigger.Actions>  
        <!-- Stopping the storyboard sets all animated properties back to default. -->  
        <StopStoryboard BeginStoryboardName="mouseEnterBeginStoryboard" />  
      </EventTrigger.Actions>  
    </EventTrigger>  
    ```  
  
     <span data-ttu-id="ec774-200">Fare işaretçisini düğmenin üzerinde hareket işaretçi ayrıldığında normal boyutuna geri iade ettiğinde Cam Dikdörtgen küçültür.</span><span class="sxs-lookup"><span data-stu-id="ec774-200">The glass rectangle shrinks when the mouse pointer moves over the button and returns back to normal size when the pointer leaves.</span></span>  
  
     <span data-ttu-id="ec774-201">İşaretçi düğmenin üzerine gittiğinde tetiklenen iki animasyon vardır (<xref:System.Windows.UIElement.MouseEnter> olayı oluşturulur).</span><span class="sxs-lookup"><span data-stu-id="ec774-201">There are two animations that are triggered when the pointer goes over the button (<xref:System.Windows.UIElement.MouseEnter> event is raised).</span></span> <span data-ttu-id="ec774-202">Animasyonlarına Cam Dikdörtgen X ve Y ekseni boyunca küçültün.</span><span class="sxs-lookup"><span data-stu-id="ec774-202">These animations shrink the glass rectangle along the X and Y axis.</span></span> <span data-ttu-id="ec774-203">Üzerindeki özelliklere dikkat edin <xref:System.Windows.Media.Animation.DoubleAnimation> öğeleri — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span><span class="sxs-lookup"><span data-stu-id="ec774-203">Notice the properties on the <xref:System.Windows.Media.Animation.DoubleAnimation> elements — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span></span> <span data-ttu-id="ec774-204"><xref:System.Windows.Media.Animation.Timeline.Duration%2A> Animasyonun yarım saniyenin, gerçekleşeceğini belirtir ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> cam 10 oranında küçültür belirtir.</span><span class="sxs-lookup"><span data-stu-id="ec774-204">The <xref:System.Windows.Media.Animation.Timeline.Duration%2A> specifies that the animation occurs over half a second, and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> specifies that the glass shrinks by 10%.</span></span>  
  
     <span data-ttu-id="ec774-205">İkinci olay tetikleyicisi (<xref:System.Windows.UIElement.MouseLeave>) yalnızca ilk durdurur.</span><span class="sxs-lookup"><span data-stu-id="ec774-205">The second event trigger (<xref:System.Windows.UIElement.MouseLeave>) simply stops the first one.</span></span> <span data-ttu-id="ec774-206">Ne zaman durdurup bir <xref:System.Windows.Media.Animation.Storyboard>, animasyonlu tüm özellikler varsayılan değerlerine döner.</span><span class="sxs-lookup"><span data-stu-id="ec774-206">When you stop a <xref:System.Windows.Media.Animation.Storyboard>, all the animated properties return to their default values.</span></span> <span data-ttu-id="ec774-207">Kullanıcı işaretçiyi düğmeden taşındığında, bu nedenle, düğme geri düğmenin üzerinde fare imlecini taşındı önceki yol gider.</span><span class="sxs-lookup"><span data-stu-id="ec774-207">Therefore, when the user moves the pointer off the button, the button goes back to the way it was before the mouse pointer moved over the button.</span></span> <span data-ttu-id="ec774-208">Animasyon hakkında daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ec774-208">For more information about animations, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span>  
  
5.  <span data-ttu-id="ec774-209">**Düğme tıklatıldığında için animasyon ekleme:** son adım kullanıcı düğmesine tıkladığında için bir tetikleyici eklemektir.</span><span class="sxs-lookup"><span data-stu-id="ec774-209">**Add an animation for when the button is clicked:** The final step is to add a trigger for when the user clicks the button.</span></span> <span data-ttu-id="ec774-210">Herhangi bir yere içinde aşağıdaki biçimlendirmeleri eklemek `ControlTemplate.Triggers` engelle:</span><span class="sxs-lookup"><span data-stu-id="ec774-210">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block:</span></span>  
  
    ```  
    <!-- Animation fires when button is clicked, causing glass to spin.  -->  
    <EventTrigger RoutedEvent="Button.Click">  
      <EventTrigger.Actions>  
        <BeginStoryboard>  
          <Storyboard>  
            <DoubleAnimation Storyboard.TargetName="glassCube"   
              Storyboard.TargetProperty=  
              "(Rectangle.RenderTransform).(TransformGroup.Children)[1].(RotateTransform.Angle)"   
              By="360" Duration="0:0:0.5" />  
          </Storyboard>  
        </BeginStoryboard>  
      </EventTrigger.Actions>  
    </EventTrigger>  
    ```  
  
     <span data-ttu-id="ec774-211">Uygulamayı çalıştırın ve düğmeleri birini tıklatın için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ec774-211">Press F5 to run the application, and click one of the buttons.</span></span> <span data-ttu-id="ec774-212">Bir düğmeye tıkladığınızda, Cam Dikdörtgen çevrede döner.</span><span class="sxs-lookup"><span data-stu-id="ec774-212">When you click a button, the glass rectangle spins around.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="ec774-213">Özet</span><span class="sxs-lookup"><span data-stu-id="ec774-213">Summary</span></span>  
 <span data-ttu-id="ec774-214">Bu kılavuzda, aşağıdaki çalışmaları gerçekleştirdiniz:</span><span class="sxs-lookup"><span data-stu-id="ec774-214">In this walkthrough, you performed the following exercises:</span></span>  
  
-   <span data-ttu-id="ec774-215">Hedeflenen bir <xref:System.Windows.Style> bir nesne türü için (<xref:System.Windows.Controls.Button>).</span><span class="sxs-lookup"><span data-stu-id="ec774-215">Targeted a <xref:System.Windows.Style> to an object type (<xref:System.Windows.Controls.Button>).</span></span>  
  
-   <span data-ttu-id="ec774-216">Tüm uygulama kullanarak düğmelerin temel özelliklerini kontrol <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="ec774-216">Controlled basic properties of the buttons in the entire application using the <xref:System.Windows.Style>.</span></span>  
  
-   <span data-ttu-id="ec774-217">Oluşturulan özellik değerleri için kullanılacak gradyan gibi kaynakları <xref:System.Windows.Style> ayarlayıcılar.</span><span class="sxs-lookup"><span data-stu-id="ec774-217">Created resources like gradients to use for property values of the <xref:System.Windows.Style> setters.</span></span>  
  
-   <span data-ttu-id="ec774-218">Tüm uygulama düğmelerini görünümünü düğmeleri için bir şablon uygulayarak özelleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="ec774-218">Customized the look of buttons in the entire application by applying a template to the buttons.</span></span>  
  
-   <span data-ttu-id="ec774-219">Özelleştirilmiş kullanıcı eylemlerine yanıt olarak düğme davranışını (gibi <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, ve <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) animasyon efektleri dahil.</span><span class="sxs-lookup"><span data-stu-id="ec774-219">Customized behavior for the buttons in response to user actions (such as <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, and <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) that included animation effects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec774-220">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ec774-220">See Also</span></span>  
 [<span data-ttu-id="ec774-221">Microsoft Expression Blend Kullanarak Düğme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ec774-221">Create a Button by Using Microsoft Expression Blend</span></span>](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)  
 [<span data-ttu-id="ec774-222">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ec774-222">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="ec774-223">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="ec774-223">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="ec774-224">Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ec774-224">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="ec774-225">Bit Eşlem Etkilerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ec774-225">Bitmap Effects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)
