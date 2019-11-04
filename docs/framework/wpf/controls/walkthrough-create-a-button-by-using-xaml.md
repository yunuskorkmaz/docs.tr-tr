---
title: 'İzlenecek yol: XAML Kullanarak bir Düğme Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: 6738b9e66c1223ea4ec50c070a421d119fd30bc4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458687"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a><span data-ttu-id="1c671-102">İzlenecek yol: XAML Kullanarak bir Düğme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1c671-102">Walkthrough: Create a Button by Using XAML</span></span>

<span data-ttu-id="1c671-103">Bu izlenecek yol amacı, bir Windows Presentation Foundation (WPF) uygulamasında kullanılmak üzere animasyonlu bir düğme oluşturmayı öğrenmektir.</span><span class="sxs-lookup"><span data-stu-id="1c671-103">The objective of this walkthrough is to learn how to create an animated button for use in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="1c671-104">Bu izlenecek yol, düğme bildiriminden düğme mantığının kodun ve ayrılma kodunun yeniden kullanılmasını sağlayan özelleştirilmiş bir düğme kaynağı oluşturmak için stilleri ve şablonu kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c671-104">This walkthrough uses styles and a template to create a customized button resource that allows reuse of code and separation of button logic from the button declaration.</span></span> <span data-ttu-id="1c671-105">Bu izlenecek yol tamamen [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1c671-105">This walkthrough is written entirely in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c671-106">Bu izlenecek yol, Visual Studio 'ya [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] yazarak veya kopyalayarak ve yapıştırarak uygulama oluşturma adımlarında size rehberlik eder.</span><span class="sxs-lookup"><span data-stu-id="1c671-106">This walkthrough guides you through the steps for creating the application by typing or copying and pasting [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] into Visual Studio.</span></span> <span data-ttu-id="1c671-107">Aynı uygulamayı oluşturmak için tasarımcının nasıl kullanılacağını öğrenmek isterseniz, bkz. [Microsoft Expression Blend kullanarak düğme oluşturma](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span><span class="sxs-lookup"><span data-stu-id="1c671-107">If you would prefer to learn how to use a designer to create the same application, see [Create a Button by Using Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span></span>

<span data-ttu-id="1c671-108">Aşağıdaki şekilde tamamlanmış düğmeler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1c671-108">The following figure shows the finished buttons.</span></span>

<span data-ttu-id="1c671-109">![XAML kullanılarak oluşturulan özel düğmeler](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="1c671-109">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-basic-buttons"></a><span data-ttu-id="1c671-110">Temel düğmeler oluştur</span><span class="sxs-lookup"><span data-stu-id="1c671-110">Create Basic Buttons</span></span>

<span data-ttu-id="1c671-111">Yeni bir proje oluşturup pencereye birkaç düğme ekleyerek başlayalım.</span><span class="sxs-lookup"><span data-stu-id="1c671-111">Let's start by creating a new project and adding a few buttons to the window.</span></span>

### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a><span data-ttu-id="1c671-112">Yeni bir WPF projesi oluşturmak ve pencereye düğme eklemek için</span><span class="sxs-lookup"><span data-stu-id="1c671-112">To create a new WPF project and add buttons to the window</span></span>

1. <span data-ttu-id="1c671-113">Visual Studio 'Yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="1c671-113">Start Visual Studio.</span></span>

2. <span data-ttu-id="1c671-114">**Yeni BIR WPF projesi oluşturun:** **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1c671-114">**Create a new WPF project:** On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="1c671-115">**Windows uygulaması (WPF)** şablonunu bulun ve projeyi "AnimatedButton" olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="1c671-115">Find the **Windows Application (WPF)** template and name the project "AnimatedButton".</span></span> <span data-ttu-id="1c671-116">Bu işlem, uygulama için iskelet oluşturacaktır.</span><span class="sxs-lookup"><span data-stu-id="1c671-116">This will create the skeleton for the application.</span></span>

3. <span data-ttu-id="1c671-117">**Temel varsayılan düğmeleri ekle:** Bu izlenecek yol için gereken tüm dosyalar, şablon tarafından sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1c671-117">**Add basic default buttons:** All the files you need for this walkthrough are provided by the template.</span></span> <span data-ttu-id="1c671-118">Çözüm Gezgini içinde çift tıklayarak Window1. xaml dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="1c671-118">Open the Window1.xaml file by double clicking it in Solution Explorer.</span></span> <span data-ttu-id="1c671-119">Varsayılan olarak, Window1. xaml içinde bir <xref:System.Windows.Controls.Grid> öğesi vardır.</span><span class="sxs-lookup"><span data-stu-id="1c671-119">By default, there is a <xref:System.Windows.Controls.Grid> element in Window1.xaml.</span></span> <span data-ttu-id="1c671-120"><xref:System.Windows.Controls.Grid> öğesini kaldırın ve aşağıdaki vurgulanmış kodu Window1. xaml 'e yazıp kopyalayıp yapıştırarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sayfasına birkaç düğme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1c671-120">Remove the <xref:System.Windows.Controls.Grid> element and add a few buttons to the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page by typing or copy and pasting the following highlighted code to Window1.xaml:</span></span>

    ```xaml
    <Window x:Class="AnimatedButton.Window1"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      Title="AnimatedButton" Height="300" Width="300"
      Background="Black">
      <!-- Buttons arranged vertically inside a StackPanel. -->
      <StackPanel HorizontalAlignment="Left">
          <Button>Button 1</Button>
          <Button>Button 2</Button>
          <Button>Button 3</Button>
      </StackPanel>
    </Window>
    ```

     <span data-ttu-id="1c671-121">Uygulamayı çalıştırmak için F5 tuşuna basın; Aşağıdaki şekilde görünen bir düğme kümesi görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1c671-121">Press F5 to run the application; you should see a set of buttons that looks like the following figure.</span></span>

     <span data-ttu-id="1c671-122">![Üç temel düğme](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span><span class="sxs-lookup"><span data-stu-id="1c671-122">![Three basic buttons](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span></span>

     <span data-ttu-id="1c671-123">Temel düğmeleri oluşturduğunuza göre, artık Window1. xaml dosyasında çalışmayı tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="1c671-123">Now that you have created the basic buttons, you are finished working in the Window1.xaml file.</span></span> <span data-ttu-id="1c671-124">İzlenecek yolun geri kalanı App. xaml dosyasına odaklanmakta ve düğmeler için stilleri ve şablonları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1c671-124">The rest of the walkthrough focuses on the app.xaml file, defining styles and a template for the buttons.</span></span>

## <a name="set-basic-properties"></a><span data-ttu-id="1c671-125">Temel özellikleri ayarla</span><span class="sxs-lookup"><span data-stu-id="1c671-125">Set Basic Properties</span></span>

<span data-ttu-id="1c671-126">Sonra, düğme görünümünü ve yerleşimini denetlemek için bu düğmelerdeki bazı özellikleri ayarlayalim.</span><span class="sxs-lookup"><span data-stu-id="1c671-126">Next, let's set some properties on these buttons to control the button appearance and layout.</span></span> <span data-ttu-id="1c671-127">Düğmelerin özelliklerini tek tek ayarlamak yerine, tüm uygulama için düğme özelliklerini tanımlamak üzere kaynakları kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="1c671-127">Rather than setting properties on the buttons individually, you will use resources to define button properties for the entire application.</span></span> <span data-ttu-id="1c671-128">Uygulama kaynakları, Web sayfaları için kavramsal olarak dış Geçişli Stil Sayfaları (CSS) ile benzerdir; Ancak, Bu izlenecek yolun sonuna göre göreceğiniz gibi kaynaklar Geçişli Stil Sayfaları (CSS) ' den çok daha güçlüdür.</span><span class="sxs-lookup"><span data-stu-id="1c671-128">Application resources are conceptually similar to external Cascading Style Sheets (CSS) for Web pages; however, resources are much more powerful than Cascading Style Sheets (CSS), as you will see by the end of this walkthrough.</span></span> <span data-ttu-id="1c671-129">Kaynaklar hakkında daha fazla bilgi için bkz. [xaml kaynakları](../advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="1c671-129">To learn more about resources, see [XAML Resources](../advanced/xaml-resources.md).</span></span>

### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a><span data-ttu-id="1c671-130">Düğmelerin üzerinde temel özellikleri ayarlamak üzere stilleri kullanmak için</span><span class="sxs-lookup"><span data-stu-id="1c671-130">To use styles to set basic properties on the buttons</span></span>

1. <span data-ttu-id="1c671-131">**Bir Application. resources bloğu tanımlayın:** App. xaml ' i açın ve henüz yoksa, aşağıdaki vurgulanmış biçimlendirmeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1c671-131">**Define an Application.Resources block:** Open app.xaml and add the following highlighted markup if it is not already there:</span></span>

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

     <span data-ttu-id="1c671-132">Kaynak kapsamı, kaynağı tanımladığınız konuma göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="1c671-132">Resource scope is determined by where you define the resource.</span></span> <span data-ttu-id="1c671-133">App. xaml dosyasında `Application.Resources` kaynakların tanımlanması, kaynağın uygulamanın herhangi bir yerinden kullanılabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c671-133">Defining resources in `Application.Resources` in the app.xaml file enables the resource to be used from anywhere in the application.</span></span> <span data-ttu-id="1c671-134">Kaynaklarınızın kapsamını tanımlama hakkında daha fazla bilgi edinmek için bkz. [xaml kaynakları](../advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="1c671-134">To learn more about defining the scope of your resources, see [XAML Resources](../advanced/xaml-resources.md).</span></span>

2. <span data-ttu-id="1c671-135">**Bir stil oluşturun ve bununla birlikte temel özellik değerlerini tanımlayın:** `Application.Resources` bloğuna aşağıdaki biçimlendirmeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1c671-135">**Create a style and define basic property values with it:** Add the following markup to the `Application.Resources` block.</span></span> <span data-ttu-id="1c671-136">Bu biçimlendirme, uygulamadaki tüm düğmelere uygulanan bir <xref:System.Windows.Style> oluşturur, 90 düğmelerin <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Margin%2A> ve 10 olarak ayarlanıyor:</span><span class="sxs-lookup"><span data-stu-id="1c671-136">This markup creates a <xref:System.Windows.Style> that applies to all buttons in the application, setting the <xref:System.Windows.FrameworkElement.Width%2A> of the buttons to 90 and the <xref:System.Windows.FrameworkElement.Margin%2A> to 10:</span></span>

    ```xaml
    <Application.Resources>
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     <span data-ttu-id="1c671-137"><xref:System.Windows.Style.TargetType%2A> özelliği, stilin <xref:System.Windows.Controls.Button>türündeki tüm nesneler için geçerli olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1c671-137">The <xref:System.Windows.Style.TargetType%2A> property specifies that the style applies to all objects of type <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="1c671-138">Her <xref:System.Windows.Setter> <xref:System.Windows.Style>için farklı bir özellik değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1c671-138">Each <xref:System.Windows.Setter> sets a different property value for the <xref:System.Windows.Style>.</span></span> <span data-ttu-id="1c671-139">Bu nedenle, bu noktada uygulamadaki her düğmenin genişliği 90 ve bir kenar boşluğu 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="1c671-139">Therefore, at this point every button in the application has a width of 90 and a margin of 10.</span></span>  <span data-ttu-id="1c671-140">Uygulamayı çalıştırmak için F5 tuşuna basarsanız, aşağıdaki pencereyi görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="1c671-140">If you press F5 to run the application, you see the following window.</span></span>

     <span data-ttu-id="1c671-141">![Genişliği 90 ve kenar boşluğu 10 olan düğmeler](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span><span class="sxs-lookup"><span data-stu-id="1c671-141">![Buttons with a width of 90 and a margin of 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span></span>

     <span data-ttu-id="1c671-142">Hangi nesnelerin hedeflendiğine, karmaşık özellik değerlerini belirtmeye ve hatta stilleri diğer stiller için giriş olarak kullanmaya yönelik çeşitli yollar da dahil olmak üzere stillerle çok daha fazla şey yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c671-142">There is much more you can do with styles, including a variety of ways to fine-tune what objects are targeted, specifying complex property values, and even using styles as input for other styles.</span></span> <span data-ttu-id="1c671-143">Daha fazla bilgi için bkz. [Stil oluşturma ve şablon](../../../desktop-wpf/fundamentals/styles-templates-overview.md)oluşturma.</span><span class="sxs-lookup"><span data-stu-id="1c671-143">For more information, see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

3. <span data-ttu-id="1c671-144">**Bir stil özelliği değerini bir kaynak olarak ayarlayın:** Kaynaklar, yaygın olarak tanımlanmış nesneleri ve değerleri yeniden kullanmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c671-144">**Set a style property value to a resource:** Resources enable a simple way to reuse commonly defined objects and values.</span></span> <span data-ttu-id="1c671-145">Kodunuzun daha modüler olmasını sağlamak için kaynakları kullanarak karmaşık değerler tanımlamak özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1c671-145">It is especially useful to define complex values using resources to make your code more modular.</span></span> <span data-ttu-id="1c671-146">Aşağıdaki Vurgulanan biçimlendirmeyi App. xaml öğesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1c671-146">Add the following highlighted markup to app.xaml.</span></span>

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

     <span data-ttu-id="1c671-147">Doğrudan `Application.Resources` bloğunun altında "Gribluegradientbrush" adlı bir kaynak oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="1c671-147">Directly under the `Application.Resources` block, you created a resource called "GrayBlueGradientBrush".</span></span> <span data-ttu-id="1c671-148">Bu kaynak yatay degradeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1c671-148">This resource defines a horizontal gradient.</span></span> <span data-ttu-id="1c671-149">Bu kaynak, <xref:System.Windows.Controls.Control.Background%2A> özelliği için düğme stili ayarlayıcısı içinde olmak üzere, uygulamanın herhangi bir yerinden bir özellik değeri olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1c671-149">This resource can be used as a property value from anywhere in the application, including inside the button style setter for the <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="1c671-150">Şimdi, tüm düğmelerin bu degradenin <xref:System.Windows.Controls.Control.Background%2A> Özellik değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="1c671-150">Now, all the buttons have a <xref:System.Windows.Controls.Control.Background%2A> property value of this gradient.</span></span>

     <span data-ttu-id="1c671-151">Uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1c671-151">Press F5 to run the application.</span></span> <span data-ttu-id="1c671-152">Aşağıdaki gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="1c671-152">It should look like the following.</span></span>

     <span data-ttu-id="1c671-153">![Gradyan arka planına sahip düğmeler](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span><span class="sxs-lookup"><span data-stu-id="1c671-153">![Buttons with a gradient background](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span></span>

## <a name="create-a-template-that-defines-the-look-of-the-button"></a><span data-ttu-id="1c671-154">Düğmenin görünümünü tanımlayan bir şablon oluşturun</span><span class="sxs-lookup"><span data-stu-id="1c671-154">Create a Template That Defines the Look of the Button</span></span>

<span data-ttu-id="1c671-155">Bu bölümde, düğmenin görünümünü (sunu) özelleştiren bir şablon oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="1c671-155">In this section, you create a template that customizes the appearance (presentation) of the button.</span></span> <span data-ttu-id="1c671-156">Düğme sunusu, düğmeye benzersiz bir görünüm kazandırmak için dikdörtgenler ve diğer bileşenler dahil olmak üzere çeşitli nesnelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="1c671-156">The button presentation is made up of several objects including rectangles and other components to give the button a unique look.</span></span>

<span data-ttu-id="1c671-157">Şimdiye kadar, düğmelerin uygulamada nasıl göründüğlerinin denetimi, düğmenin özelliklerini değiştirmek için sınırlandırılan denetim.</span><span class="sxs-lookup"><span data-stu-id="1c671-157">So far, the control of how buttons look in the application has been confined to changing properties of the button.</span></span> <span data-ttu-id="1c671-158">Düğmenin görünümünde daha fazla radikal değişiklik yapmak isterseniz ne yapmalısınız?</span><span class="sxs-lookup"><span data-stu-id="1c671-158">What if you want to make more radical changes to the button's appearance?</span></span> <span data-ttu-id="1c671-159">Şablonlar bir nesne sunumu üzerinde güçlü denetimi etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="1c671-159">Templates enable powerful control over the presentation of an object.</span></span> <span data-ttu-id="1c671-160">Şablonlar stiller içinde kullanılabileceği için stilin uygulandığı tüm nesnelere şablon uygulayabilirsiniz (Bu kılavuzda, düğme).</span><span class="sxs-lookup"><span data-stu-id="1c671-160">Because templates can be used within styles, you can apply a template to all objects that the style applies to (in this walkthrough, the button).</span></span>

### <a name="to-use-the-template-to-define-the-look-of-the-button"></a><span data-ttu-id="1c671-161">Düğme görünümünü tanımlamak üzere şablonu kullanmak için</span><span class="sxs-lookup"><span data-stu-id="1c671-161">To use the template to define the look of the button</span></span>

1. <span data-ttu-id="1c671-162">**Şablonu ayarlayın:** <xref:System.Windows.Controls.Button> gibi denetimlerde <xref:System.Windows.Controls.Control.Template%2A> özelliği bulunduğundan, Şablon özellik değerini bir <xref:System.Windows.Style> ayarlamış olduğumuz diğer özellik değerleri gibi bir <xref:System.Windows.Setter>kullanarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c671-162">**Set up the template:** Because controls like <xref:System.Windows.Controls.Button> have a <xref:System.Windows.Controls.Control.Template%2A> property, you can define the template property value just like the other property values we have set in a <xref:System.Windows.Style> using a <xref:System.Windows.Setter>.</span></span> <span data-ttu-id="1c671-163">Düğme stilinize aşağıdaki vurgulanmış biçimlendirmeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1c671-163">Add the following highlighted markup to your button style.</span></span>

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

2. <span data-ttu-id="1c671-164">**Düğme sunumunu Değiştir:** Bu noktada, şablonu tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1c671-164">**Alter button presentation:** At this point, you need to define the template.</span></span> <span data-ttu-id="1c671-165">Aşağıdaki Vurgulanan biçimlendirmeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1c671-165">Add the following highlighted markup.</span></span> <span data-ttu-id="1c671-166">Bu biçimlendirme, yuvarlatılmış kenarları olan iki <xref:System.Windows.Shapes.Rectangle> öğesini ve ardından bir <xref:System.Windows.Controls.DockPanel>belirtir.</span><span class="sxs-lookup"><span data-stu-id="1c671-166">This markup specifies two <xref:System.Windows.Shapes.Rectangle> elements with rounded edges, followed by a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="1c671-167"><xref:System.Windows.Controls.DockPanel>, düğmenin <xref:System.Windows.Controls.ContentPresenter> barındırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1c671-167">The <xref:System.Windows.Controls.DockPanel> is used to host the <xref:System.Windows.Controls.ContentPresenter> of the button.</span></span> <span data-ttu-id="1c671-168"><xref:System.Windows.Controls.ContentPresenter> düğmenin içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1c671-168">A <xref:System.Windows.Controls.ContentPresenter> displays the content of the button.</span></span> <span data-ttu-id="1c671-169">Bu kılavuzda içerik metindir ("Button 1", "Button 2", "Button 3").</span><span class="sxs-lookup"><span data-stu-id="1c671-169">In this walkthrough, the content is text ("Button 1", "Button 2", "Button 3").</span></span> <span data-ttu-id="1c671-170">Tüm şablon bileşenleri (dikdörtgenler ve <xref:System.Windows.Controls.DockPanel>) bir <xref:System.Windows.Controls.Grid>içinde düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="1c671-170">All of the template components (the rectangles and the <xref:System.Windows.Controls.DockPanel>) are laid out inside of a <xref:System.Windows.Controls.Grid>.</span></span>

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

     <span data-ttu-id="1c671-171">Uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1c671-171">Press F5 to run the application.</span></span> <span data-ttu-id="1c671-172">Aşağıdaki gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="1c671-172">It should look like the following.</span></span>

     ![3 tuşlu pencere](./media/custom-button-animatedbutton-4.gif)

3. <span data-ttu-id="1c671-174">**Şablona bir glasseffect ekleyin:** Daha sonra camı ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1c671-174">**Add a glasseffect to the template:** Next you will add the glass.</span></span> <span data-ttu-id="1c671-175">İlk olarak, bir cam Gradyan Efekti oluşturan bazı kaynaklar oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="1c671-175">First you create some resources that create a glass gradient effect.</span></span> <span data-ttu-id="1c671-176">Bu gradyan kaynaklarını `Application.Resources` bloğunun içinde herhangi bir yere ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1c671-176">Add these gradient resources anywhere within the `Application.Resources` block:</span></span>

    ```xaml
    <Application.Resources>
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">
        <GradientStop Color="WhiteSmoke" Offset="0.2" />
        <GradientStop Color="Transparent" Offset="0.4" />
        <GradientStop Color="WhiteSmoke" Offset="0.5" />
        <GradientStop Color="Transparent" Offset="0.75" />
        <GradientStop Color="WhiteSmoke" Offset="0.9" />
        <GradientStop Color="Transparent" Offset="1" />
      </GradientStopCollection>
      <LinearGradientBrush x:Key="MyGlassBrushResource"
        StartPoint="0,0" EndPoint="1,1" Opacity="0.75"
        GradientStops="{StaticResource MyGlassGradientStopsResource}" />
    <!-- Styles and other resources below here. -->
    ```

     <span data-ttu-id="1c671-177">Bu kaynaklar, düğme şablonunun <xref:System.Windows.Controls.Grid> eklediğimiz bir dikdörtgen için <xref:System.Windows.Shapes.Shape.Fill%2A> olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1c671-177">These resources are used as the <xref:System.Windows.Shapes.Shape.Fill%2A> for a rectangle that we insert into the <xref:System.Windows.Controls.Grid> of the button template.</span></span> <span data-ttu-id="1c671-178">Aşağıdaki Vurgulanan biçimlendirmeyi şablona ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1c671-178">Add the following highlighted markup to the template.</span></span>

    ```xaml
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
          <!-- These transforms have no effect as they are declared here.
          The reason the transforms are included is to be targets
          for animation (see later). -->
          <Rectangle.RenderTransform>
            <TransformGroup>
              <ScaleTransform />
              <RotateTransform />
            </TransformGroup>
          </Rectangle.RenderTransform>
          <!-- A BevelBitmapEffect is applied to give the button a "Beveled" look. -->
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
    </ControlTemplate>
    </Setter.Value>
    ```

     <span data-ttu-id="1c671-179">"GlassCube" öğesinin `x:Name` özelliği ile dikdörtgenin <xref:System.Windows.UIElement.Opacity%2A> 0 olduğuna dikkat edin, bu nedenle örneği çalıştırdığınızda en üstte açık olan cam dikdörtgeni görmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c671-179">Notice that the <xref:System.Windows.UIElement.Opacity%2A> of the rectangle with the `x:Name` property of "glassCube" is 0, so when you run the sample, you do not see the glass rectangle overlaid on top.</span></span> <span data-ttu-id="1c671-180">Bunun nedeni, daha sonra kullanıcı düğme ile etkileşime geçtiğinde şablon için tetiklemeleri ekliyoruz.</span><span class="sxs-lookup"><span data-stu-id="1c671-180">This is because we will later add triggers to the template for when the user interacts with the button.</span></span> <span data-ttu-id="1c671-181">Ancak, <xref:System.Windows.UIElement.Opacity%2A> değerini 1 olarak değiştirip uygulamayı çalıştırarak düğmenin şimdi nasıl göründüğünü görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c671-181">However, you can see what the button looks like now by changing the <xref:System.Windows.UIElement.Opacity%2A> value to 1 and running the application.</span></span> <span data-ttu-id="1c671-182">Aşağıdaki şekle bakın.</span><span class="sxs-lookup"><span data-stu-id="1c671-182">See the following figure.</span></span> <span data-ttu-id="1c671-183">Sonraki adıma geçmeden önce, <xref:System.Windows.UIElement.Opacity%2A> tekrar 0 olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1c671-183">Before proceeding to the next step, change the <xref:System.Windows.UIElement.Opacity%2A> back to 0.</span></span>

     <span data-ttu-id="1c671-184">![XAML kullanılarak oluşturulan özel düğmeler](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="1c671-184">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-button-interactivity"></a><span data-ttu-id="1c671-185">Düğme etkileşimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="1c671-185">Create Button Interactivity</span></span>

<span data-ttu-id="1c671-186">Bu bölümde, özellik değerlerini değiştirmek ve fare işaretçisini düğmenin üzerine taşımak ve tıklatmak gibi kullanıcı eylemlerine yanıt olarak animasyon çalıştırmak için özellik Tetikleyicileri ve olay tetikleyicileri oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="1c671-186">In this section, you will create property triggers and event triggers to change property values and run animations in response to user actions such as moving the mouse pointer over the button and clicking.</span></span>

<span data-ttu-id="1c671-187">Etkileşim eklemenin kolay bir yolu (fareyle açık, fare tuşu, tıklama vb.), şablonunuz veya stiliniz içinde tetiklerinizi tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="1c671-187">An easy way to add interactivity (mouse-over, mouse-leave, click, and so on) is to define triggers within your template or style.</span></span> <span data-ttu-id="1c671-188">Bir <xref:System.Windows.Trigger>oluşturmak için, şöyle bir "koşul" özelliği tanımlarsınız: düğme <xref:System.Windows.UIElement.IsMouseOver%2A> Özellik değeri `true`eşittir.</span><span class="sxs-lookup"><span data-stu-id="1c671-188">To create a <xref:System.Windows.Trigger>, you define a property "condition" such as: The button <xref:System.Windows.UIElement.IsMouseOver%2A> property value is equal to `true`.</span></span> <span data-ttu-id="1c671-189">Sonra tetikleyici koşulu true olduğunda gerçekleşen ayarlayıcıları (Eylemler) tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="1c671-189">You then define setters (actions) that take place when the trigger condition is true.</span></span>

### <a name="to-create-button-interactivity"></a><span data-ttu-id="1c671-190">Düğme etkileşimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1c671-190">To create button interactivity</span></span>

1. <span data-ttu-id="1c671-191">**Şablon Tetikleyicileri ekle:** Şablonunuz için vurgulanan biçimlendirmeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1c671-191">**Add template triggers:** Add the highlighted markup to your template.</span></span>

    ```xaml
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

2. <span data-ttu-id="1c671-192">**Özellik Tetikleyicileri ekle:** `ControlTemplate.Triggers` bloğuna vurgulanan biçimlendirmeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1c671-192">**Add property triggers:** Add the highlighted markup to the `ControlTemplate.Triggers` block:</span></span>

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>

    <ControlTemplate.Triggers/>
    ```

     <span data-ttu-id="1c671-193">F5 tuşuna basarak uygulamayı çalıştırın ve fare işaretçisini düğmelerin üzerinde çalıştırırken etkiyi görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="1c671-193">Press F5 to run the application and see the effect as you run the mouse pointer over the buttons.</span></span>

3. <span data-ttu-id="1c671-194">**Bir odak tetikleyicisi ekleyin:** Daha sonra, düğme odağa sahip olduğunda (örneğin, Kullanıcı onu tıkladıktan sonra) durumu işlemek için bazı benzer ayarlayıcıları ekleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="1c671-194">**Add a focus trigger:** Next, we'll add some similar setters to handle the case when the button has focus (for example, after the user clicks it).</span></span>

    ```xaml
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

     <span data-ttu-id="1c671-195">F5 tuşuna basarak uygulamayı çalıştırın ve düğmelerden birine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1c671-195">Press F5 to run the application and click on one of the buttons.</span></span> <span data-ttu-id="1c671-196">Düğme, hala odağa sahip olduğu için tıkladıktan sonra vurgulandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1c671-196">Notice that the button stays highlighted after you click it because it still has focus.</span></span> <span data-ttu-id="1c671-197">Başka bir düğmeye tıklarsanız, son bir düğme odağı kaybetirken yeni düğme odağı kazanır.</span><span class="sxs-lookup"><span data-stu-id="1c671-197">If you click another button, the new button gains focus while the last one loses it.</span></span>

4. <span data-ttu-id="1c671-198"><xref:System.Windows.UIElement.MouseEnter> **ve** <xref:System.Windows.UIElement.MouseLeave> **için animasyonlar ekleyin** **:** sonraki tetikleyicilere bazı animasyonlar ekliyoruz.</span><span class="sxs-lookup"><span data-stu-id="1c671-198">**Add animations for**  <xref:System.Windows.UIElement.MouseEnter> **and** <xref:System.Windows.UIElement.MouseLeave> **:** Next we add some animations to the triggers.</span></span> <span data-ttu-id="1c671-199">Aşağıdaki biçimlendirmeyi `ControlTemplate.Triggers` bloğunun içinde herhangi bir yere ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1c671-199">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block.</span></span>

    ```xaml
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

     <span data-ttu-id="1c671-200">Fare işaretçisi düğmenin üzerine geldiğinde ve işaretçi ayrıldığında normal boyutuna geri döndüğünde Cam dikdörtgen küçülür.</span><span class="sxs-lookup"><span data-stu-id="1c671-200">The glass rectangle shrinks when the mouse pointer moves over the button and returns back to normal size when the pointer leaves.</span></span>

     <span data-ttu-id="1c671-201">İşaretçi düğmenin üzerine gittiğinde tetiklenen iki animasyon vardır (<xref:System.Windows.UIElement.MouseEnter> olay tetiklenir).</span><span class="sxs-lookup"><span data-stu-id="1c671-201">There are two animations that are triggered when the pointer goes over the button (<xref:System.Windows.UIElement.MouseEnter> event is raised).</span></span> <span data-ttu-id="1c671-202">Bu animasyonlar, cam dikdörtgeni X ve Y ekseni üzerinde daraltır.</span><span class="sxs-lookup"><span data-stu-id="1c671-202">These animations shrink the glass rectangle along the X and Y axis.</span></span> <span data-ttu-id="1c671-203"><xref:System.Windows.Media.Animation.DoubleAnimation> öğelerinde özelliklerine dikkat edin — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span><span class="sxs-lookup"><span data-stu-id="1c671-203">Notice the properties on the <xref:System.Windows.Media.Animation.DoubleAnimation> elements — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span></span> <span data-ttu-id="1c671-204"><xref:System.Windows.Media.Animation.Timeline.Duration%2A>, animasyonun saniyenin yarısı üzerinde oluştuğunu belirtir ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>, camı %10 oranında küçültür.</span><span class="sxs-lookup"><span data-stu-id="1c671-204">The <xref:System.Windows.Media.Animation.Timeline.Duration%2A> specifies that the animation occurs over half a second, and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> specifies that the glass shrinks by 10%.</span></span>

     <span data-ttu-id="1c671-205">İkinci olay tetikleyicisi (<xref:System.Windows.UIElement.MouseLeave>) yalnızca ilk birini durduruyor.</span><span class="sxs-lookup"><span data-stu-id="1c671-205">The second event trigger (<xref:System.Windows.UIElement.MouseLeave>) simply stops the first one.</span></span> <span data-ttu-id="1c671-206">Bir <xref:System.Windows.Media.Animation.Storyboard>durdurduğunuzda, tüm animasyonlu özellikler varsayılan değerlerine döndürülür.</span><span class="sxs-lookup"><span data-stu-id="1c671-206">When you stop a <xref:System.Windows.Media.Animation.Storyboard>, all the animated properties return to their default values.</span></span> <span data-ttu-id="1c671-207">Bu nedenle, Kullanıcı işaretçiyi düğme dışına taşıdıkça düğme, fare işaretçisi düğmenin üzerine taşınmadan önce olduğu şekilde geri döner.</span><span class="sxs-lookup"><span data-stu-id="1c671-207">Therefore, when the user moves the pointer off the button, the button goes back to the way it was before the mouse pointer moved over the button.</span></span> <span data-ttu-id="1c671-208">Animasyonlar hakkında daha fazla bilgi için bkz. [animasyon genel bakış](../graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1c671-208">For more information about animations, see [Animation Overview](../graphics-multimedia/animation-overview.md).</span></span>

5. <span data-ttu-id="1c671-209">**Düğmeye tıklandığında bir animasyon ekleyin:** Son adım, kullanıcının düğmeye tıkladığı zaman için bir tetikleyici eklemektir.</span><span class="sxs-lookup"><span data-stu-id="1c671-209">**Add an animation for when the button is clicked:** The final step is to add a trigger for when the user clicks the button.</span></span> <span data-ttu-id="1c671-210">Aşağıdaki biçimlendirmeyi `ControlTemplate.Triggers` bloğunun içinde herhangi bir yere ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1c671-210">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block:</span></span>

    ```xaml
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

     <span data-ttu-id="1c671-211">F5 tuşuna basarak uygulamayı çalıştırın ve düğmelerden birine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1c671-211">Press F5 to run the application, and click one of the buttons.</span></span> <span data-ttu-id="1c671-212">Bir düğmeye tıkladığınızda Cam dikdörtgen etrafında döner.</span><span class="sxs-lookup"><span data-stu-id="1c671-212">When you click a button, the glass rectangle spins around.</span></span>

## <a name="summary"></a><span data-ttu-id="1c671-213">Özet</span><span class="sxs-lookup"><span data-stu-id="1c671-213">Summary</span></span>
 <span data-ttu-id="1c671-214">Bu kılavuzda, aşağıdaki alıştırmaları gerçekleştirdiyseniz:</span><span class="sxs-lookup"><span data-stu-id="1c671-214">In this walkthrough, you performed the following exercises:</span></span>

- <span data-ttu-id="1c671-215">Bir <xref:System.Windows.Style> nesne türüne hedeflenmiş (<xref:System.Windows.Controls.Button>).</span><span class="sxs-lookup"><span data-stu-id="1c671-215">Targeted a <xref:System.Windows.Style> to an object type (<xref:System.Windows.Controls.Button>).</span></span>

- <span data-ttu-id="1c671-216"><xref:System.Windows.Style>kullanarak tüm uygulamadaki düğmelerin temel özellikleri denetlenir.</span><span class="sxs-lookup"><span data-stu-id="1c671-216">Controlled basic properties of the buttons in the entire application using the <xref:System.Windows.Style>.</span></span>

- <span data-ttu-id="1c671-217"><xref:System.Windows.Style> ayarlayıcılarının özellik değerleri için kullanılacak degradeler gibi kaynaklar oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="1c671-217">Created resources like gradients to use for property values of the <xref:System.Windows.Style> setters.</span></span>

- <span data-ttu-id="1c671-218">Düğmelere bir şablon uygulayarak tüm uygulamadaki düğmelerin görünümü özelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="1c671-218">Customized the look of buttons in the entire application by applying a template to the buttons.</span></span>

- <span data-ttu-id="1c671-219">Animasyon efektlerini içeren (<xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>ve <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) kullanıcı eylemlerine yanıt olarak düğmelerin özelleştirilmiş davranışı.</span><span class="sxs-lookup"><span data-stu-id="1c671-219">Customized behavior for the buttons in response to user actions (such as <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, and <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) that included animation effects.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c671-220">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c671-220">See also</span></span>

- [<span data-ttu-id="1c671-221">Microsoft Expression Blend Kullanarak Düğme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1c671-221">Create a Button by Using Microsoft Expression Blend</span></span>](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [<span data-ttu-id="1c671-222">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1c671-222">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="1c671-223">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="1c671-223">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="1c671-224">Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1c671-224">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="1c671-225">Bit Eşlem Etkilerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1c671-225">Bitmap Effects Overview</span></span>](../graphics-multimedia/bitmap-effects-overview.md)
