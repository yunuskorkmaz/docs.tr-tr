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
# <a name="walkthrough-create-a-button-by-using-xaml"></a>İzlenecek yol: XAML Kullanarak bir Düğme Oluşturma

Bu izlenecek yol amacı, bir Windows Presentation Foundation (WPF) uygulamasında kullanılmak üzere animasyonlu bir düğme oluşturmayı öğrenmektir. Bu izlenecek yol, düğme bildiriminden düğme mantığının kodun ve ayrılma kodunun yeniden kullanılmasını sağlayan özelleştirilmiş bir düğme kaynağı oluşturmak için stilleri ve şablonu kullanır. Bu izlenecek yol tamamen [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]yazılmıştır.

> [!IMPORTANT]
> Bu izlenecek yol, Visual Studio 'ya [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] yazarak veya kopyalayarak ve yapıştırarak uygulama oluşturma adımlarında size rehberlik eder. Aynı uygulamayı oluşturmak için tasarımcının nasıl kullanılacağını öğrenmek isterseniz, bkz. [Microsoft Expression Blend kullanarak düğme oluşturma](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).

Aşağıdaki şekilde tamamlanmış düğmeler gösterilmektedir.

![XAML kullanılarak oluşturulan özel düğmeler](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")

## <a name="create-basic-buttons"></a>Temel düğmeler oluştur

Yeni bir proje oluşturup pencereye birkaç düğme ekleyerek başlayalım.

### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>Yeni bir WPF projesi oluşturmak ve pencereye düğme eklemek için

1. Visual Studio 'Yu başlatın.

2. **Yeni BIR WPF projesi oluşturun:** **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın. **Windows uygulaması (WPF)** şablonunu bulun ve projeyi "AnimatedButton" olarak adlandırın. Bu işlem, uygulama için iskelet oluşturacaktır.

3. **Temel varsayılan düğmeleri ekle:** Bu izlenecek yol için gereken tüm dosyalar, şablon tarafından sağlanmaktadır. Çözüm Gezgini içinde çift tıklayarak Window1. xaml dosyasını açın. Varsayılan olarak, Window1. xaml içinde bir <xref:System.Windows.Controls.Grid> öğesi vardır. <xref:System.Windows.Controls.Grid> öğesini kaldırın ve aşağıdaki vurgulanmış kodu Window1. xaml 'e yazıp kopyalayıp yapıştırarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sayfasına birkaç düğme ekleyin:

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

     Uygulamayı çalıştırmak için F5 tuşuna basın; Aşağıdaki şekilde görünen bir düğme kümesi görmeniz gerekir.

     ![Üç temel düğme](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")

     Temel düğmeleri oluşturduğunuza göre, artık Window1. xaml dosyasında çalışmayı tamamladınız. İzlenecek yolun geri kalanı App. xaml dosyasına odaklanmakta ve düğmeler için stilleri ve şablonları tanımlar.

## <a name="set-basic-properties"></a>Temel özellikleri ayarla

Sonra, düğme görünümünü ve yerleşimini denetlemek için bu düğmelerdeki bazı özellikleri ayarlayalim. Düğmelerin özelliklerini tek tek ayarlamak yerine, tüm uygulama için düğme özelliklerini tanımlamak üzere kaynakları kullanırsınız. Uygulama kaynakları, Web sayfaları için kavramsal olarak dış Geçişli Stil Sayfaları (CSS) ile benzerdir; Ancak, Bu izlenecek yolun sonuna göre göreceğiniz gibi kaynaklar Geçişli Stil Sayfaları (CSS) ' den çok daha güçlüdür. Kaynaklar hakkında daha fazla bilgi için bkz. [xaml kaynakları](../advanced/xaml-resources.md).

### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>Düğmelerin üzerinde temel özellikleri ayarlamak üzere stilleri kullanmak için

1. **Bir Application. resources bloğu tanımlayın:** App. xaml ' i açın ve henüz yoksa, aşağıdaki vurgulanmış biçimlendirmeyi ekleyin:

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

     Kaynak kapsamı, kaynağı tanımladığınız konuma göre belirlenir. App. xaml dosyasında `Application.Resources` kaynakların tanımlanması, kaynağın uygulamanın herhangi bir yerinden kullanılabilmesini sağlar. Kaynaklarınızın kapsamını tanımlama hakkında daha fazla bilgi edinmek için bkz. [xaml kaynakları](../advanced/xaml-resources.md).

2. **Bir stil oluşturun ve bununla birlikte temel özellik değerlerini tanımlayın:** `Application.Resources` bloğuna aşağıdaki biçimlendirmeyi ekleyin. Bu biçimlendirme, uygulamadaki tüm düğmelere uygulanan bir <xref:System.Windows.Style> oluşturur, 90 düğmelerin <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Margin%2A> ve 10 olarak ayarlanıyor:

    ```xaml
    <Application.Resources>
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     <xref:System.Windows.Style.TargetType%2A> özelliği, stilin <xref:System.Windows.Controls.Button>türündeki tüm nesneler için geçerli olduğunu belirtir. Her <xref:System.Windows.Setter> <xref:System.Windows.Style>için farklı bir özellik değeri ayarlar. Bu nedenle, bu noktada uygulamadaki her düğmenin genişliği 90 ve bir kenar boşluğu 10 ' dur.  Uygulamayı çalıştırmak için F5 tuşuna basarsanız, aşağıdaki pencereyi görürsünüz.

     ![Genişliği 90 ve kenar boşluğu 10 olan düğmeler](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")

     Hangi nesnelerin hedeflendiğine, karmaşık özellik değerlerini belirtmeye ve hatta stilleri diğer stiller için giriş olarak kullanmaya yönelik çeşitli yollar da dahil olmak üzere stillerle çok daha fazla şey yapabilirsiniz. Daha fazla bilgi için bkz. [Stil oluşturma ve şablon](../../../desktop-wpf/fundamentals/styles-templates-overview.md)oluşturma.

3. **Bir stil özelliği değerini bir kaynak olarak ayarlayın:** Kaynaklar, yaygın olarak tanımlanmış nesneleri ve değerleri yeniden kullanmak için basit bir yol sağlar. Kodunuzun daha modüler olmasını sağlamak için kaynakları kullanarak karmaşık değerler tanımlamak özellikle yararlıdır. Aşağıdaki Vurgulanan biçimlendirmeyi App. xaml öğesine ekleyin.

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

     Doğrudan `Application.Resources` bloğunun altında "Gribluegradientbrush" adlı bir kaynak oluşturdunuz. Bu kaynak yatay degradeyi tanımlar. Bu kaynak, <xref:System.Windows.Controls.Control.Background%2A> özelliği için düğme stili ayarlayıcısı içinde olmak üzere, uygulamanın herhangi bir yerinden bir özellik değeri olarak kullanılabilir. Şimdi, tüm düğmelerin bu degradenin <xref:System.Windows.Controls.Control.Background%2A> Özellik değeri vardır.

     Uygulamayı çalıştırmak için F5 tuşuna basın. Aşağıdaki gibi görünmelidir.

     ![Gradyan arka planına sahip düğmeler](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")

## <a name="create-a-template-that-defines-the-look-of-the-button"></a>Düğmenin görünümünü tanımlayan bir şablon oluşturun

Bu bölümde, düğmenin görünümünü (sunu) özelleştiren bir şablon oluşturursunuz. Düğme sunusu, düğmeye benzersiz bir görünüm kazandırmak için dikdörtgenler ve diğer bileşenler dahil olmak üzere çeşitli nesnelerden oluşur.

Şimdiye kadar, düğmelerin uygulamada nasıl göründüğlerinin denetimi, düğmenin özelliklerini değiştirmek için sınırlandırılan denetim. Düğmenin görünümünde daha fazla radikal değişiklik yapmak isterseniz ne yapmalısınız? Şablonlar bir nesne sunumu üzerinde güçlü denetimi etkinleştirir. Şablonlar stiller içinde kullanılabileceği için stilin uygulandığı tüm nesnelere şablon uygulayabilirsiniz (Bu kılavuzda, düğme).

### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>Düğme görünümünü tanımlamak üzere şablonu kullanmak için

1. **Şablonu ayarlayın:** <xref:System.Windows.Controls.Button> gibi denetimlerde <xref:System.Windows.Controls.Control.Template%2A> özelliği bulunduğundan, Şablon özellik değerini bir <xref:System.Windows.Style> ayarlamış olduğumuz diğer özellik değerleri gibi bir <xref:System.Windows.Setter>kullanarak tanımlayabilirsiniz. Düğme stilinize aşağıdaki vurgulanmış biçimlendirmeyi ekleyin.

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

2. **Düğme sunumunu Değiştir:** Bu noktada, şablonu tanımlamanız gerekir. Aşağıdaki Vurgulanan biçimlendirmeyi ekleyin. Bu biçimlendirme, yuvarlatılmış kenarları olan iki <xref:System.Windows.Shapes.Rectangle> öğesini ve ardından bir <xref:System.Windows.Controls.DockPanel>belirtir. <xref:System.Windows.Controls.DockPanel>, düğmenin <xref:System.Windows.Controls.ContentPresenter> barındırmak için kullanılır. <xref:System.Windows.Controls.ContentPresenter> düğmenin içeriğini görüntüler. Bu kılavuzda içerik metindir ("Button 1", "Button 2", "Button 3"). Tüm şablon bileşenleri (dikdörtgenler ve <xref:System.Windows.Controls.DockPanel>) bir <xref:System.Windows.Controls.Grid>içinde düzenlenir.

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

     Uygulamayı çalıştırmak için F5 tuşuna basın. Aşağıdaki gibi görünmelidir.

     ![3 tuşlu pencere](./media/custom-button-animatedbutton-4.gif)

3. **Şablona bir glasseffect ekleyin:** Daha sonra camı ekleyeceksiniz. İlk olarak, bir cam Gradyan Efekti oluşturan bazı kaynaklar oluşturursunuz. Bu gradyan kaynaklarını `Application.Resources` bloğunun içinde herhangi bir yere ekleyin:

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

     Bu kaynaklar, düğme şablonunun <xref:System.Windows.Controls.Grid> eklediğimiz bir dikdörtgen için <xref:System.Windows.Shapes.Shape.Fill%2A> olarak kullanılır. Aşağıdaki Vurgulanan biçimlendirmeyi şablona ekleyin.

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

     "GlassCube" öğesinin `x:Name` özelliği ile dikdörtgenin <xref:System.Windows.UIElement.Opacity%2A> 0 olduğuna dikkat edin, bu nedenle örneği çalıştırdığınızda en üstte açık olan cam dikdörtgeni görmezsiniz. Bunun nedeni, daha sonra kullanıcı düğme ile etkileşime geçtiğinde şablon için tetiklemeleri ekliyoruz. Ancak, <xref:System.Windows.UIElement.Opacity%2A> değerini 1 olarak değiştirip uygulamayı çalıştırarak düğmenin şimdi nasıl göründüğünü görebilirsiniz. Aşağıdaki şekle bakın. Sonraki adıma geçmeden önce, <xref:System.Windows.UIElement.Opacity%2A> tekrar 0 olarak değiştirin.

     ![XAML kullanılarak oluşturulan özel düğmeler](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")

## <a name="create-button-interactivity"></a>Düğme etkileşimi oluşturma

Bu bölümde, özellik değerlerini değiştirmek ve fare işaretçisini düğmenin üzerine taşımak ve tıklatmak gibi kullanıcı eylemlerine yanıt olarak animasyon çalıştırmak için özellik Tetikleyicileri ve olay tetikleyicileri oluşturacaksınız.

Etkileşim eklemenin kolay bir yolu (fareyle açık, fare tuşu, tıklama vb.), şablonunuz veya stiliniz içinde tetiklerinizi tanımlamaktır. Bir <xref:System.Windows.Trigger>oluşturmak için, şöyle bir "koşul" özelliği tanımlarsınız: düğme <xref:System.Windows.UIElement.IsMouseOver%2A> Özellik değeri `true`eşittir. Sonra tetikleyici koşulu true olduğunda gerçekleşen ayarlayıcıları (Eylemler) tanımlarsınız.

### <a name="to-create-button-interactivity"></a>Düğme etkileşimi oluşturmak için

1. **Şablon Tetikleyicileri ekle:** Şablonunuz için vurgulanan biçimlendirmeyi ekleyin.

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

2. **Özellik Tetikleyicileri ekle:** `ControlTemplate.Triggers` bloğuna vurgulanan biçimlendirmeyi ekleyin:

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>

    <ControlTemplate.Triggers/>
    ```

     F5 tuşuna basarak uygulamayı çalıştırın ve fare işaretçisini düğmelerin üzerinde çalıştırırken etkiyi görüntüleyin.

3. **Bir odak tetikleyicisi ekleyin:** Daha sonra, düğme odağa sahip olduğunda (örneğin, Kullanıcı onu tıkladıktan sonra) durumu işlemek için bazı benzer ayarlayıcıları ekleyeceğiz.

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

     F5 tuşuna basarak uygulamayı çalıştırın ve düğmelerden birine tıklayın. Düğme, hala odağa sahip olduğu için tıkladıktan sonra vurgulandığına dikkat edin. Başka bir düğmeye tıklarsanız, son bir düğme odağı kaybetirken yeni düğme odağı kazanır.

4. <xref:System.Windows.UIElement.MouseEnter> **ve** <xref:System.Windows.UIElement.MouseLeave> **için animasyonlar ekleyin** **:** sonraki tetikleyicilere bazı animasyonlar ekliyoruz. Aşağıdaki biçimlendirmeyi `ControlTemplate.Triggers` bloğunun içinde herhangi bir yere ekleyin.

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

     Fare işaretçisi düğmenin üzerine geldiğinde ve işaretçi ayrıldığında normal boyutuna geri döndüğünde Cam dikdörtgen küçülür.

     İşaretçi düğmenin üzerine gittiğinde tetiklenen iki animasyon vardır (<xref:System.Windows.UIElement.MouseEnter> olay tetiklenir). Bu animasyonlar, cam dikdörtgeni X ve Y ekseni üzerinde daraltır. <xref:System.Windows.Media.Animation.DoubleAnimation> öğelerinde özelliklerine dikkat edin — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>. <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, animasyonun saniyenin yarısı üzerinde oluştuğunu belirtir ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>, camı %10 oranında küçültür.

     İkinci olay tetikleyicisi (<xref:System.Windows.UIElement.MouseLeave>) yalnızca ilk birini durduruyor. Bir <xref:System.Windows.Media.Animation.Storyboard>durdurduğunuzda, tüm animasyonlu özellikler varsayılan değerlerine döndürülür. Bu nedenle, Kullanıcı işaretçiyi düğme dışına taşıdıkça düğme, fare işaretçisi düğmenin üzerine taşınmadan önce olduğu şekilde geri döner. Animasyonlar hakkında daha fazla bilgi için bkz. [animasyon genel bakış](../graphics-multimedia/animation-overview.md).

5. **Düğmeye tıklandığında bir animasyon ekleyin:** Son adım, kullanıcının düğmeye tıkladığı zaman için bir tetikleyici eklemektir. Aşağıdaki biçimlendirmeyi `ControlTemplate.Triggers` bloğunun içinde herhangi bir yere ekleyin:

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

     F5 tuşuna basarak uygulamayı çalıştırın ve düğmelerden birine tıklayın. Bir düğmeye tıkladığınızda Cam dikdörtgen etrafında döner.

## <a name="summary"></a>Özet
 Bu kılavuzda, aşağıdaki alıştırmaları gerçekleştirdiyseniz:

- Bir <xref:System.Windows.Style> nesne türüne hedeflenmiş (<xref:System.Windows.Controls.Button>).

- <xref:System.Windows.Style>kullanarak tüm uygulamadaki düğmelerin temel özellikleri denetlenir.

- <xref:System.Windows.Style> ayarlayıcılarının özellik değerleri için kullanılacak degradeler gibi kaynaklar oluşturuldu.

- Düğmelere bir şablon uygulayarak tüm uygulamadaki düğmelerin görünümü özelleştirildi.

- Animasyon efektlerini içeren (<xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>ve <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) kullanıcı eylemlerine yanıt olarak düğmelerin özelleştirilmiş davranışı.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Expression Blend Kullanarak Düğme Oluşturma](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Animasyona Genel bakış](../graphics-multimedia/animation-overview.md)
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Bit Eşlem Etkilerine Genel Bakış](../graphics-multimedia/bitmap-effects-overview.md)
