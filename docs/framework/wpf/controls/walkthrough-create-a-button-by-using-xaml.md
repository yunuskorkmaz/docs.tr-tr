---
title: 'İzlenecek yol: XAML Kullanarak bir Düğme Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: 908a38485c879e3f28399bb7dbc8303afd4505da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024017"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a>İzlenecek yol: XAML Kullanarak bir Düğme Oluşturma
Bu kılavuzun amacı, bir Windows Presentation Foundation (WPF) uygulamasında kullanmak için bir animasyonlu düğme oluşturma öğrenmektir. Bu izlenecek yol, stil ve şablon kod yeniden kullanımını ve düğme mantığının ayrımı düğme bildiriminden imkan tanıyan özelleştirilmiş bir düğme kaynak oluşturmak için kullanır. Bu izlenecek yolda tamamen yazılır [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
> [!IMPORTANT]
>  Yazarak veya kopyalama ve yapıştırma uygulaması oluşturma adımlarında size sunduğumuz [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Microsoft Visual Studio içinde. Aynı uygulama oluşturacağınızı öğrenmek için bir tasarım aracı (Microsoft Expression Blend) kullanmayı öğrenmek tercih ediyorsanız [tarafından Microsoft Expression Blend kullanarak düğme oluşturma](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).  
  
 Aşağıdaki şekilde tamamlanmış düğmeleri gösterir.  
  
 ![XAML kullanılarak oluşturulan özel düğmeler](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-basic-buttons"></a>Temel düğmeler oluşturma  
 Yeni proje oluşturma ve birkaç düğme penceresine ekleyerek başlayalım tıklatın.  
  
#### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>Yeni bir WPF projesi oluşturun ve pencereyi düğme ekleme  
  
1. Visual Studio’yu çalıştırın.  
  
2. **Yeni bir WPF projesi oluşturun:** Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**. Bulma **Windows uygulaması (WPF)** şablonu ve "AnimatedButton olarak" proje adı. Bu uygulama için bir çatı oluşturur.  
  
3. **Temel varsayılan düğme ekleyin:** Bu kılavuz için gereksinim duyduğunuz tüm dosyaları, şablon tarafından sağlanır. Çözüm Gezgini'nde tıklayarak çift Window1.xaml dosyasını açın. Varsayılan olarak, var olan bir <xref:System.Windows.Controls.Grid> gt;Window1.XAML öğesinde. Kaldırma <xref:System.Windows.Controls.Grid> öğesi ve birkaç düğme ekleme [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] yazarak veya kopyalama ve yapıştırma gt;Window1.XAML aşağıdaki vurgulanmış kodu sayfası:  
  
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
  
     Uygulamayı çalıştırmak için F5 tuşuna basın; Aşağıdaki şekil gibi görünen bir düğme kümesi görmeniz gerekir.  
  
     ![Üç temel düğmeleri](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")  
  
     Temel düğmeleri oluşturduğunuza göre Window1.xaml dosyasında çalışma tamamlandı. Gözden geçirme geri kalanı, stil ve şablon düğmelerinin tanımlama app.xaml dosyası üzerinde odaklanır.  
  
## <a name="set-basic-properties"></a>Temel özelliklerini ayarlama  
 Ardından, bazı özellikler düğmenin görünümünü ve düzenini denetlemek için bu düğmeleri ayarlayalım. Özellikleri düğmelerini tek tek ayarlamak yerine, uygulamanın tamamı düğme özelliklerini tanımlamak için kaynakları kullanır. Uygulama kaynaklarını dışında kavramsal olarak benzer [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] Web sayfaları için; ancak, kaynakları çok daha güçlü [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)], bu izlenecek yolun sonuna kadar görürsünüz. Kaynaklar hakkında daha fazla bilgi için bkz. [XAML kaynakları](../advanced/xaml-resources.md).  
  
#### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>Düğmelerin temel özellikleri ayarlamak için stilleri kullanmak için  
  
1. **Application.Resources bloğu tanımlayın:** App.xaml açın ve aşağıdaki vurgulanmış biçimlendirmeyi zaten yoksa ekleyin:  
  
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
  
     Kaynak kapsam, kaynak tanımladığınız tarafından belirlenir. Kaynakları tanımlama `Application.Resources` içinde app.xaml dosyası gelen herhangi bir uygulamada kullanılmak için kaynak sağlar. Kaynaklarınızı kapsamını tanımlama hakkında daha fazla bilgi için bkz: [XAML kaynakları](../advanced/xaml-resources.md).  
  
2. **Stil oluşturma ve bunu temel özellik değerleri tanımlayın:** İçin aşağıdaki işaretlemeyi ekleyin `Application.Resources` blok. Bu biçimlendirme oluşturur bir <xref:System.Windows.Style> ayarlama, uygulamadaki tüm düğmelerin uygulanan <xref:System.Windows.FrameworkElement.Width%2A> 90 düğmelerin ve <xref:System.Windows.FrameworkElement.Margin%2A> 10:  
  
    ```xaml  
    <Application.Resources>  
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>  
    </Application.Resources>  
    ```  
  
     <xref:System.Windows.Style.TargetType%2A> Özellik belirtir stili türdeki tüm nesneler için geçerli olduğunu <xref:System.Windows.Controls.Button>. Her <xref:System.Windows.Setter> farklı özellik değeri için ayarlar <xref:System.Windows.Style>. Bu nedenle, bu noktada uygulamadaki her bir düğmenin genişliği 90 ve kenar boşluğu 10 sahiptir.  Uygulamayı çalıştırmak için F5 tuşuna basarsanız aşağıdaki pencereyi görürsünüz.  
  
     ![Genişliği 90 ve kenar boşluğu 10 düğmeleriyle](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")  
  
     Karmaşık özellik değerleri belirtme ve hatta stilleri giriş olarak diğer stilleri kullanarak hangi nesnelerin ince ayar yapmak için yol çeşitli dahil stilleri ile yapabileceğiniz çok daha fazla yoktur. Daha fazla bilgi için [stil ve şablon oluşturma](styling-and-templating.md).  
  
3. **Stil özelliği değeri bir kaynak olarak ayarlayın:** Kaynakların yaygın olarak tanımlanan nesneleri ve değerleri yeniden kullanmak için basit bir yol sağlar. Kodunuzu daha modüler hale getirmek için kaynakları kullanarak karmaşık değerleri tanımlamak özellikle yararlıdır. App.xaml için vurgulanan aşağıdaki işaretlemeyi ekleyin.  
  
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
  
     Doğrudan altında `Application.Resources` bloğu "GrayBlueGradientBrush" adlı bir kaynak oluşturulur. Bu kaynak Yatay Gradyan tanımlar. Bu kaynak her yerden bir özellik değeri olarak kullanılabilir için düğme stili ayarlayıcısının dahil olmak üzere uygulamada <xref:System.Windows.Controls.Control.Background%2A> özelliği. Şimdi tüm düğmeler sahip bir <xref:System.Windows.Controls.Control.Background%2A> Bu geçişin özellik değeri.  
  
     Uygulamayı çalıştırmak için F5'e basın. Aşağıdaki gibi görünmelidir.  
  
     ![Arka plan gradyan düğmeleriyle](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")  
  
## <a name="create-a-template-that-defines-the-look-of-the-button"></a>Düğmenin görünümünü tanımlayan bir şablon oluşturma  
 Bu bölümde, düğmenin görünümünü (sunu) özelleştirir bir şablon oluşturun. Düğme sunusu dikdörtgenler ve diğer bileşenleri dahil olmak üzere çeşitli nesnelerin düğmeyi benzersiz bir görünüm kazandırmak için oluşur.  
  
 Şu ana kadar düğmeleri uygulamada nasıl görüneceğini denetim düğmesi özelliklerini değiştirme ile sınırlı. Düğmenin görünümünü çok daha köklü değişiklikler yapmak istersek? Şablonlar, belirli bir nesne üzerinde güçlü denetim etkinleştirir. Şablonlar stiller içinde kullanılabilir olmadığından (Bu kılavuzda düğme) stilin uygulandığı tüm nesneler için bir şablonu uygulayabilirsiniz.  
  
#### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>Düğmenin görünümünü tanımlamak için şablonu kullanmak için  
  
1. **Şablonu ayarlayın:** Gibi denetimlerin çünkü <xref:System.Windows.Controls.Button> sahip bir <xref:System.Windows.Controls.Control.Template%2A> özelliği içindeki ayarlamadınız biz yalnızca diğer özellik değerleri gibi şablon özellik değeri tanımlayabilirsiniz bir <xref:System.Windows.Style> kullanarak bir <xref:System.Windows.Setter>. Aşağıdaki vurgulanmış biçimlendirmeyi düğmenizin stiline ekleyin.  
  
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
  
2. **Değiştir düğmesi sunumu:** Bu noktada, şablonu tanımlamanız gerekir. Vurgulanan aşağıdaki işaretlemeyi ekleyin. Bu işaretleme iki belirtir <xref:System.Windows.Shapes.Rectangle> yuvarlatılmış kenarlar, öğelerle arkasından bir <xref:System.Windows.Controls.DockPanel>. <xref:System.Windows.Controls.DockPanel> Kullanılan ana <xref:System.Windows.Controls.ContentPresenter> düğmesi. A <xref:System.Windows.Controls.ContentPresenter> düğme içeriğini görüntüler. Bu kılavuzda, metin ("Düğmesini 1", "2 Button", "Button 3") içeriktir. Şablon bileşenlerinin tümünü (dikdörtgenler ve <xref:System.Windows.Controls.DockPanel>) içine yerleştirilir bir <xref:System.Windows.Controls.Grid>.  
  
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
  
     ![](./media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")  
  
3. **Şablona bir glasseffect şablona ekleyin:** Bundan sonra cam ekleyeceksiniz. İlk olarak, bir cam gradyan efekti oluşturma bazı kaynaklar oluşturun. Bu gradyan dahilindeki herhangi bir yere ekleyin `Application.Resources` engelle:  
  
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
  
     Bu kaynaklar olarak kullanılan <xref:System.Windows.Shapes.Shape.Fill%2A> için biz takın bir dikdörtgen <xref:System.Windows.Controls.Grid> düğme şablonunun. Aşağıdaki vurgulanmış biçimlendirmeyi şablonuna ekleyin.  
  
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
  
     Dikkat <xref:System.Windows.UIElement.Opacity%2A> ile dikdörtgenin `x:Name` "glassCube" özelliği: 0, örneği çalıştırdığınızda, üst kısımdaki yayılan Cam Dikdörtgen görmek için. Kullanıcı düğmesi ile etkileşim kurduğunda daha sonra Tetikleyiciler için şablona ekleyeceğiz olmasıdır. Ancak, düğme artık değiştirerek nasıl göründüğünü görebilirsiniz <xref:System.Windows.UIElement.Opacity%2A> değeri 1 ve uygulamayı çalıştırma. Aşağıdaki şekle bakın. Sonraki adıma devam etmeden önce değiştirme <xref:System.Windows.UIElement.Opacity%2A> için 0.  
  
     ![XAML kullanılarak oluşturulan özel düğmeler](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-button-interactivity"></a>Etkileşimli düğme oluşturma  
 Bu bölümde, özellik Tetikleyicileri ve özellik değerlerini değiştirmek ve animasyon yanıt fare işaretçisi düğmenin üzerine hareket ve tıklamak gibi kullanıcı eylemlerini olarak çalıştırmak için olay tetikleyicilerini oluşturacaksınız.  
  
 (Fare bekletme, fareyi bırakın,'a tıklayın ve benzeri) etkileşim eklemek için kolay bir yol, şablon veya stil içindeki Tetikleyiciler tanımlamaktır. Oluşturmak için bir <xref:System.Windows.Trigger>, bir özelliği "koşul" gibi tanımlayın: Düğme <xref:System.Windows.UIElement.IsMouseOver%2A> özellik değeri eşittir `true`. Ayarlayıcılar (Eylemler) tetikleyici koşul true olduğunda, gerçekleşmesi tanımlarsınız.  
  
#### <a name="to-create-button-interactivity"></a>Etkileşimli düğme oluşturmak için  
  
1. **Şablon tetikleyicileri ekleyin:** Vurgulanan biçimlendirme şablonunuza ekleyin.  
  
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
  
2. **Özellik tetikleyicileri ekleyin:** Biçimlendirmeyi eklemek `ControlTemplate.Triggers` engelle:  
  
    ```xaml
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     Uygulamayı çalıştırmak ve düğmelerin üzerine fare işaretçisini çalıştırılmakta olan etkisini görmek için F5 tuşuna basın.  
  
3. **Odak tetikleyicisi ekleyin:** Ardından, düğmeyi (örneğin, kullanıcı buna tıkladığında sonra) odağı varken durumu işlemek için bazı benzer ayarlayıcılar ekleyeceğiz.  
  
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
  
     Düğmelerden birine tıklayın ve uygulamayı çalıştırmak için F5 tuşuna basın. Odak hala olduğundan tıkladıktan sonra düğme vurgulanmış kaldığına dikkat edin. Başka bir düğme tıklarsanız, sonuncu kaybeder sırada yeni düğme odak kazanır.  
  
4. **Animasyonlar ekleyin** <xref:System.Windows.UIElement.MouseEnter> **ve** <xref:System.Windows.UIElement.MouseLeave> **:** Sonraki bazı animasyonlar tetikleyicilere ekleriz. Herhangi bir yeri içinde aşağıdaki işaretlemeyi ekleyin `ControlTemplate.Triggers` blok.  
  
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
  
     Fare işaretçisi düğmenin üzerine taşır ve işaretçi çıktığında normal boyutuna geri döndürür Cam Dikdörtgen küçültür.  
  
     İşaretçisi düğmenin üzerine çıktığında tetiklenen iki animasyon vardır (<xref:System.Windows.UIElement.MouseEnter> olayı oluşturulur). Cam dikdörtgenin X ve Y ekseni boyunca animasyonlarına daraltır. Özelliklere dikkat edin <xref:System.Windows.Media.Animation.DoubleAnimation> öğeleri — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>. <xref:System.Windows.Media.Animation.Timeline.Duration%2A> Animasyon bir yarım saniye gerçekleşeceğini belirtir ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> cam 10 oranında küçüldüğünü belirtir.  
  
     İkinci olay tetikleyicisi (<xref:System.Windows.UIElement.MouseLeave>) yalnızca ilk durdurur. Ne zaman durdurmanız bir <xref:System.Windows.Media.Animation.Storyboard>, tüm animasyonlu özellikleri varsayılan değerlerine döndürür. Kullanıcı imleci düğmeden hareket ettiğinde, bu nedenle, düğmenin fare işaretçisi düğmenin üzerine taşınmış önceki şekilde döner. Animasyonlar hakkında daha fazla bilgi için bkz. [animasyona genel bakış](../graphics-multimedia/animation-overview.md).  
  
5. **Düğmeye tıklandığında animasyon ekleyin:** Son adım kullanıcı düğmeye tıkladığında bir tetikleyici için eklemektir. Herhangi bir yeri içinde aşağıdaki işaretlemeyi ekleyin `ControlTemplate.Triggers` engelle:  
  
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
  
     Uygulamayı çalıştırmak ve düğmelerden birine tıklayın için F5 tuşuna basın. Bir düğmeye tıkladığınızda, geçici bir çözüm Cam Dikdörtgen sanal makineleri çalıştırır.  
  
## <a name="summary"></a>Özet  
 Bu kılavuzda, aşağıdaki çalışmaları gerçekleştirdiniz:  
  
- Hedeflenen bir <xref:System.Windows.Style> bir nesne türüne (<xref:System.Windows.Controls.Button>).  
  
- Düğmeleri kullanarak tüm uygulama temel özelliklerini kontrol <xref:System.Windows.Style>.  
  
- Özellik değerleri için kullanılacak gradyan gibi kaynaklara oluşturulan <xref:System.Windows.Style> ayarlayıcılar.  
  
- Uygulamanın tamamı düğme görünümünü düğmeleri için bir şablon uygulanarak özelleştirilmiş.  
  
- Özelleştirilmiş kullanıcı eylemlerine düğme davranışı (gibi <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, ve <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) animasyon efektleri dahil.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Expression Blend Kullanarak Düğme Oluşturma](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [Stil ve Şablon Oluşturma](styling-and-templating.md)
- [Animasyona Genel bakış](../graphics-multimedia/animation-overview.md)
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Bit Eşlem Etkilerine Genel Bakış](../graphics-multimedia/bitmap-effects-overview.md)
