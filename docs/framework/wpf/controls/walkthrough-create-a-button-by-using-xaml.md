---
title: 'İzlenecek yol: XAML Kullanarak bir Düğme Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: a8cc227703e81e5de9dea7e44e10dfecca2cd05c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646475"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a>İzlenecek yol: XAML Kullanarak bir Düğme Oluşturma

Bu izbin amacı, windows sunu foundation (WPF) uygulamasında kullanılmak üzere animasyonlu bir düğme oluşturmayı öğrenmektir. Bu izlenme, kodun yeniden kullanılmasına ve düğme mantığının düğme bildiriminden ayrılmasına olanak tanıyan özelleştirilmiş bir düğme kaynağı oluşturmak için stilleri ve şablonu kullanır. Bu yol tamamen [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].

> [!IMPORTANT]
> Bu kılavuz, Visual Studio'ya yazarak veya kopyalayarak ve [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] yapıştırarak uygulamayı oluşturma adımlarında size yol gösterin. Aynı uygulamayı oluşturmak için tasarımcıyı nasıl kullanacağınızı öğrenmek istiyorsanız, [bkz.](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)

Aşağıdaki şekil, tamamlanan düğmeleri gösterir.

![XAML kullanılarak oluşturulan özel düğmeler](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")

## <a name="create-basic-buttons"></a>Temel Düğmeler Oluştur

Yeni bir proje oluşturarak ve pencereye birkaç düğme ekleyerek başlayalım.

### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>Yeni bir WPF projesi oluşturmak ve pencereye düğme eklemek için

1. Visual Studio’yu çalıştırın.

2. **Yeni bir WPF projesi oluşturun:** **Dosya** menüsünde **Yeni'yi**işaret edin ve ardından **Project'i**tıklatın. Windows **Application (WPF)** şablonunu bulun ve projeyi "AnimatedButton" olarak adlandırın. Bu uygulama için iskelet oluşturacaktır.

3. **Temel varsayılan düğmeler ekleyin:** Bu gözden geçirme için gereken tüm dosyalar şablon tarafından sağlanır. Solution Explorer'da çift tıklayarak Window1.xaml dosyasını açın. Varsayılan olarak, Window1.xaml bir <xref:System.Windows.Controls.Grid> öğe vardır. Aşağıdaki <xref:System.Windows.Controls.Grid> vurgulanan kodu Window1.xaml'a yazarak veya kopyalayarak ve yapıştırarak öğeyi kaldırın ve [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sayfaya birkaç düğme ekleyin:

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

     Uygulamayı çalıştırmak için F5 tuşuna basın; aşağıdaki şekilde görünen bir düğme kümesi görmeniz gerekir.

     ![Üç temel düğme](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")

     Şimdi temel düğmeleri oluşturduk, Window1.xaml dosyasında çalışmayı bitirdiniz. Gözden geçirme nin geri kalanı app.xaml dosyasına odaklanarak stilleri ve düğmeler için bir şablon u tanımlar.

## <a name="set-basic-properties"></a>Temel Özellikleri Ayarla

Ardından, düğme görünümünü ve düzenini denetlemek için bu düğmelerde bazı özellikler ayarlayalım. Düğmelerde özellikleri tek tek ayarlamak yerine, tüm uygulama için düğme özelliklerini tanımlamak için kaynakları kullanırsınız. Uygulama kaynakları kavramsal olarak Web sayfaları için dış Basamaklı Stil Sayfaları'na (CSS) benzer; ancak, bu izlenecek yol sonunda göreceğiniz gibi, kaynaklar Basamaklı Stil Sayfaları 'ndan (CSS) çok daha güçlüdür. Kaynaklar hakkında daha fazla bilgi edinmek için [XAML Kaynakları'na](../../../desktop-wpf/fundamentals/xaml-resources-define.md)bakın.

### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>Düğmelerde temel özellikleri ayarlamak için stilleri kullanmak için

1. **Application.Resources bloğunu tanımla:** app.xaml'ı açın ve zaten orada değilse aşağıdaki vurgulanmış biçimlendirmeyi ekleyin:

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

     Kaynak kapsamı, kaynağı tanımladığınız yere göre belirlenir. app.xaml dosyasındaki `Application.Resources` kaynakların tanımlanması, kaynağın uygulamanın herhangi bir yerinden kullanılmasını sağlar. Kaynaklarınızın kapsamını tanımlama hakkında daha fazla bilgi edinmek için [XAML Kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md)bölümüne bakın.

2. **Bir stil oluşturun ve temel özellik değerlerini onunla tanımlayın:** Aşağıdaki biçimlendirmeyi `Application.Resources` bloya ekleyin. Bu biçimlendirme, <xref:System.Windows.Style> düğmeleri 90 ve <xref:System.Windows.FrameworkElement.Margin%2A> 10'a <xref:System.Windows.FrameworkElement.Width%2A> ayarlayarak uygulamadaki tüm düğmeler için geçerli olan bir biçim oluşturur:

    ```xaml
    <Application.Resources>
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     Özellik, <xref:System.Windows.Style.TargetType%2A> stilin türünün <xref:System.Windows.Controls.Button>tüm nesneleri için geçerli olduğunu belirtir. Her <xref:System.Windows.Setter> biri <xref:System.Windows.Style>için farklı bir özellik değeri ayarlar. Bu nedenle, bu noktada uygulamadaki her düğmenin genişliği 90 ve kenar boşluğu 10'ardır.  Uygulamayı çalıştırmak için F5 tuşuna basarsanız, aşağıdaki pencereyi görürsünüz.

     ![Genişliği 90 ve kenar boşluğu 10 olan düğmeler](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")

     Hangi nesnelerin hedeflenmiş olduğunu hassas bir şekilde ayarlamak, karmaşık özellik değerlerini belirtme ve hatta stilleri diğer stiller için giriş olarak kullanma gibi çeşitli yollar da dahil olmak üzere, stilleri ile yapabileceğiniz çok daha fazla şey vardır. Daha fazla bilgi için [Stil ve Templating'e](../../../desktop-wpf/fundamentals/styles-templates-overview.md)bakın.

3. **Bir kaynağa stil özellik değeri ayarlama:** Kaynaklar, sık tanımlanmış nesneleri ve değerleri yeniden kullanmanın basit bir yolunu sağlar. Özellikle kodunuzu daha modüler hale getirmek için kaynakları kullanarak karmaşık değerleri tanımlamak yararlıdır. App.xaml'a aşağıdaki vurgulanmış işaretlemeyi ekleyin.

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

     `Application.Resources` Bloğun hemen altında "GrayBlueGradientBrush" adlı bir kaynak oluşturdunuz. Bu kaynak yatay bir degrade tanımlar. Bu kaynak, <xref:System.Windows.Controls.Control.Background%2A> özelliğin düğme stili ayarlayıcısı nın içinde de dahil olmak üzere uygulamanın herhangi bir yerinden bir özellik değeri olarak kullanılabilir. Şimdi, tüm düğmeler <xref:System.Windows.Controls.Control.Background%2A> bu degrade bir özellik değeri ne var.

     Uygulamayı çalıştırmak için F5'e basın. Aşağıdaki gibi görünmelidir.

     ![Degrade arka plana sahip düğmeler](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")

## <a name="create-a-template-that-defines-the-look-of-the-button"></a>Düğmenin Görünümünü Tanımlayan Bir Şablon Oluşturma

Bu bölümde, düğmenin görünümünü (sunusunu) özelleştiren bir şablon oluşturursunuz. Düğme sunusu, düğmeye benzersiz bir görünüm kazandırmak için dikdörtgenler ve diğer bileşenler de dahil olmak üzere çeşitli nesnelerden oluşur.

Şimdiye kadar, düğmelerin uygulamada nasıl göründüğünün denetimi düğmenin özelliklerini değiştirmekle sınırlı ydı. Düğmenin görünümünde daha radikal değişiklikler yapmak isterseniz ne olur? Şablonlar, bir nesnenin sunumu üzerinde güçlü denetim sağlar. Şablonlar stiller içinde kullanılabildığından, stilin uygulandığı tüm nesnelere şablon uygulayabilirsiniz (bu izlenecek yol, düğme).

### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>Düğmenin görünümünü tanımlamak için şablonu kullanmak için

1. **Şablonu ayarlayın:** Gibi <xref:System.Windows.Controls.Button> denetimlerin <xref:System.Windows.Controls.Control.Template%2A> bir özelliği olduğundan, şablon özellik değerini, bir <xref:System.Windows.Style> <xref:System.Windows.Setter>'yi kullanarak ayarladığımız diğer özellik değerleri gibi tanımlayabilirsiniz Düğme stilinize aşağıdaki vurgulanmış biçimlendirmeyi ekleyin.

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

2. **Düğme sunusunu değiştir:** Bu noktada, şablonu tanımlamanız gerekir. Aşağıdaki vurgulanan biçimlendirmeyi ekleyin. Bu biçimlendirme yuvarlatılmış kenarları ile iki <xref:System.Windows.Shapes.Rectangle> öğe <xref:System.Windows.Controls.DockPanel>belirtir, ardından bir . Düğmenin <xref:System.Windows.Controls.DockPanel> ana bilgisayariçin <xref:System.Windows.Controls.ContentPresenter> kullanılır. A <xref:System.Windows.Controls.ContentPresenter> düğmenin içeriğini görüntüler. Bu gözden geçirmede içerik metindir ("Düğme 1", "Düğme 2", "Düğme 3"). Tüm şablon bileşenleri (dikdörtgenler ve <xref:System.Windows.Controls.DockPanel>) bir <xref:System.Windows.Controls.Grid>içinde dışarı atılır .

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

     Uygulamayı çalıştırmak için F5'e basın. Aşağıdaki gibi görünmelidir.

     ![3 düğmeli pencere](./media/custom-button-animatedbutton-4.gif)

3. **Şablona cam efekti ekleyin:** Sonra cam ekleyeceğiz. Önce bir cam degrade etkisi oluşturmak bazı kaynaklar oluşturun. Bu degrade kaynaklarını `Application.Resources` bloğun herhangi bir yerine ekleyin:

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

     Bu kaynaklar, düğme <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Controls.Grid> şablonunun içine eklediğimiz bir dikdörtgen için kullanılır. Şablona aşağıdaki vurgulanmış biçimlendirmeyi ekleyin.

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

     "GlassCube" <xref:System.Windows.UIElement.Opacity%2A> `x:Name` özelliği ile dikdörtgenin 0 olduğuna dikkat edin, bu nedenle örneği çalıştırdığınızda, cam dikdörtgenin üst üste bindiğini görmezsiniz. Bunun nedeni, daha sonra kullanıcı nın düğmeyle etkileşime geçtiği zaman şablona tetikleyiciler eklememizdir. Ancak, <xref:System.Windows.UIElement.Opacity%2A> değeri 1 olarak değiştirip uygulamayı çalıştırarak düğmenin şimdi nasıl göründüğünü görebilirsiniz. Aşağıdaki şekle bakın. Bir sonraki adıma geçmeden <xref:System.Windows.UIElement.Opacity%2A> önce, geri yi 0 olarak değiştirin.

     ![XAML kullanılarak oluşturulan özel düğmeler](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")

## <a name="create-button-interactivity"></a>Düğme Etkileşimi Oluştur

Bu bölümde, fare işaretçisini düğmenin üzerine taşımak ve tıklatmak gibi kullanıcı eylemlerine yanıt olarak özellik değerlerini değiştirmek ve animasyonları çalıştırmak için özellik tetikleyicileri ve olay tetikleyicileri oluşturursunuz.

Etkileşim eklemenin kolay bir yolu (fare üzerinde, fareyi terk et, tıklatma vb.) şablonunuzda veya stilinizde tetikleyicileri tanımlamaktır. Bir <xref:System.Windows.Trigger>, bir özellik "koşul" gibi tanımlarsanız: düğme <xref:System.Windows.UIElement.IsMouseOver%2A> özelliği `true`değeri eşittir . Ardından, tetikleyici koşul doğru olduğunda gerçekleşen ayarlayıcıları (eylemler) tanımlarsınız.

### <a name="to-create-button-interactivity"></a>Düğme etkileşimi oluşturmak için

1. **Şablon tetikleyicileri ekleyin:** Vurgulanan biçimlendirmeyi şablonunuza ekleyin.

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

2. **Özellik tetikleyicileri ekleyin:** Vurgulanan biçimlendirmeyi `ControlTemplate.Triggers` bloya ekleyin:

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>

    <ControlTemplate.Triggers/>
    ```

     Uygulamayı çalıştırmak ve fare işaretçisini düğmelerin üzerinde çalıştırırken efekti görmek için F5 tuşuna basın.

3. **Odak tetikleyicisi ekleyin:** Daha sonra, düğme odaklandığında (örneğin, kullanıcı tıklattıktan sonra) servis talebiyle işlemek için benzer ayarlar ekleriz.

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

     Uygulamayı çalıştırmak için F5 tuşuna basın ve düğmelerden birine tıklayın. Düğmeyi tıklattıktan sonra vurgulanmış olarak kaldığına dikkat edin, çünkü hala odaklanmış. Başka bir düğmeyi tıklattığınızda, yeni düğme odağı kazanırken, sonuncusu onu kaybeder.

4. **Için** <xref:System.Windows.UIElement.MouseEnter> animasyonlar ekleyin **ve** <xref:System.Windows.UIElement.MouseLeave> **:** Sonra tetikleyicilere bazı animasyonlar ekliyoruz.   Aşağıdaki biçimlendirmeyi `ControlTemplate.Triggers` bloğun herhangi bir yerine ekleyin.

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

     Fare işaretçisi düğmeüzerinde hareket ettiğinde cam dikdörtgen küçülür ve işaretçi ayrıldığında normal boyuta geri döner.

     İşaretçi düğmenin üzerinden geçtiğinde tetiklenen iki animasyon<xref:System.Windows.UIElement.MouseEnter> vardır (olay yükseltilir). Bu animasyonlar X ve Y ekseni boyunca cam dikdörtgeni küçültür. Öğeler üzerindeki özelliklere <xref:System.Windows.Media.Animation.DoubleAnimation> dikkat <xref:System.Windows.Media.Animation.Timeline.Duration%2A> <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>edin — ve . Animasyonun <xref:System.Windows.Media.Animation.Timeline.Duration%2A> yarım saniyeden uzun bir süre içinde <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> oluştuğunu ve camın %10 küçüldüğünü belirtir.

     İkinci olay tetikleyicisi (<xref:System.Windows.UIElement.MouseLeave>) sadece ilkini durdurur. Bir <xref:System.Windows.Media.Animation.Storyboard>, tüm animasyonlu özellikleri durdurmak zaman varsayılan değerlerine döner. Bu nedenle, kullanıcı işaretçiyi düğmeden uzaklaştırdığında, düğme fare işaretçisi düğmenin üzerinden geçmeden önceki hale geri döner. Animasyonlar hakkında daha fazla bilgi için [Animasyona Genel Bakış'a](../graphics-multimedia/animation-overview.md)bakın.

5. **Düğme tıklatıldığında animasyon ekleyin:** Son adım, kullanıcı düğmeyi tıklattığında bir tetikleyici eklemektir. Aşağıdaki biçimlendirmeyi `ControlTemplate.Triggers` bloğun herhangi bir yerine ekleyin:

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

     Uygulamayı çalıştırmak için F5 tuşuna basın ve düğmelerden birini tıklatın. Bir düğmeyi tıklattığınızda, cam dikdörtgen etrafında döner.

## <a name="summary"></a>Özet
 Bu izleyerek, aşağıdaki egzersizleri yaptınız:

- Hedeflenen a <xref:System.Windows.Style> nesne türü<xref:System.Windows.Controls.Button>( ).

- Tüm uygulamadaki düğmelerin kontrollü temel özelliklerini <xref:System.Windows.Style>kullanarak .

- <xref:System.Windows.Style> Ayarlayıcıların özellik değerleri için kullanılacak degradeler gibi kaynaklar oluşturuldu.

- Düğmelere şablon uygulayarak tüm uygulamadaki düğmelerin görünümünü özelleştirmiş.

- Animasyon efektleri içeren kullanıcı eylemlerine <xref:System.Windows.UIElement.MouseEnter>(, <xref:System.Windows.UIElement.MouseLeave> <xref:System.Windows.Controls.Primitives.ButtonBase.Click>ve) yanıt olarak düğmeler için özelleştirilmiş davranış.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Expression Blend Kullanarak Düğme Oluşturma](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Animasyona Genel bakış](../graphics-multimedia/animation-overview.md)
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Bit Eşlem Efektlerine Genel Bakış](../graphics-multimedia/bitmap-effects-overview.md)
