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
ms.openlocfilehash: a05e0af94cc84db117c7b8caf389d084cd4c3fd5
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a>İzlenecek yol: XAML Kullanarak bir Düğme Oluşturma
Bu kılavuzun amacı, bir Windows Presentation Foundation (WPF) uygulamasında kullanmak için animasyonlu bir düğme oluşturmayı öğrenin sağlamaktır. Bu kılavuz, kodu yeniden kullanma ve düğme mantığının ayrılması düğme bildiriminden izin veren bir özelleştirilmiş düğme kaynak oluşturmak için stilleri ve bir şablonu kullanır. Bu kılavuzda tamamen yazılmış [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
> [!IMPORTANT]
>  Bu kılavuzda, uygulamayı yazarak veya kopyalama ve yapıştırma oluşturmak için adımlarında size rehberlik [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Microsoft Visual Studio uygulamasına. Aynı uygulamayı oluşturmak için bkz. tasarım aracı (Microsoft Expression Blend) kullanmayı öğrenmek tercih ederseniz [oluştur düğmesi Microsoft Expression Blend kullanarak tarafından](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md).  
  
 Aşağıdaki şekil tamamlanmış düğmeleri gösterir.  
  
 ![XAML kullanılarak oluşturulmuş özel düğmeler](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-basic-buttons"></a>Temel düğmeler oluşturma  
 Yeni proje oluşturma ve pencereyi birkaç düğme ekleyerek başlayalım tıklatın.  
  
#### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>Yeni bir WPF projesi oluşturun ve pencereyi düğme ekleme  
  
1.  Visual Studio'yu başlatın.  
  
2.  **Yeni bir WPF projesi oluşturun:** üzerinde **dosya** menüsündeki **yeni**ve ardından **proje**. Bul **Windows uygulaması (WPF)** şablonu ve adını "AnimatedButton olarak" proje. Bu uygulama için bir çatı oluşturur.  
  
3.  **Temel varsayılan düğme ekleme:** bu kılavuz için gereken tüm dosyaları şablon tarafından sağlanır. Çift Çözüm Gezgini'nde tıklatarak Window1.xaml dosyasını açın. Varsayılan olarak, var olan bir <xref:System.Windows.Controls.Grid> Window1.xaml öğesinde. Kaldırma <xref:System.Windows.Controls.Grid> öğesi ve birkaç düğme ekleme [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sayfa yazarak veya kopyalama ve yapıştırma Window1.xaml aşağıdaki vurgulanmış kodu:  
  
    ```xaml  
    <Window x:Class="AnimatedButton.Window1"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      Title="AnimatedButton" Height="300" Width="300"   
      Background="Black">   <!-- Buttons arranged vertically inside a StackPanel. -->   <StackPanel HorizontalAlignment="Left">     <Button>Button 1</Button>     <Button>Button 2</Button>     <Button>Button 3</Button>   </StackPanel>  
  
    </Window>  
    ```  
  
     Uygulamayı çalıştırmak için F5 tuşuna basın; Aşağıdaki şekil gibi görünen düğmeler kümesi görmeniz gerekir.  
  
     ![Üç temel düğme](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")  
  
     Temel düğmeleri oluşturduğunuza göre Window1.xaml dosyasındaki çalışma tamamlanmış demektir. İzlenecek yol kalan stilleri ve düğmeleri için bir şablon tanımlama app.xaml dosyası üzerinde odaklanır.  
  
## <a name="set-basic-properties"></a>Temel özellikleri ayarlama  
 Ardından, şimdi bazı özellikler düğmesi görünümünü ve düzenini denetlemek için bu düğmelerin ayarlayın. Özellikler çubuğundaki düğmeler tek tek ayarlamak yerine, tüm uygulama düğmesi özelliklerini tanımlamak için kaynakları kullanır. Uygulama kaynakları için dış kavramsal olarak benzer [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] Web sayfaları için; ancak, çok daha güçlü kaynaklardır [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)], bu örneklerde sonuna göreceğiniz gibi. Kaynakları hakkında daha fazla bilgi edinmek için [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
#### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>Düğmelerin temel özelliklerini ayarlamak için stiller kullanmak için  
  
1.  **Bir Application.Resources bloğu tanımlayın:** app.xaml açın ve aşağıdaki vurgulanmış biçimlendirmeyi zaten yoksa ekleyin:  
  
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
  
     Kaynak kapsamı kaynak tanımladığınız tarafından belirlenir. Kaynakları tanımlama `Application.Resources` app.xaml dosyası gelen herhangi bir uygulamada kullanılmak üzere kaynak sağlar. Kaynaklarınızın kapsamını tanımlama hakkında daha fazla bilgi için bkz: [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
2.  **Stil oluşturma ve onunla temel özellik değerlerini tanımlayabileceğiniz:** aşağıdaki biçimlendirmeleri eklemek `Application.Resources` bloğu. Bu biçimlendirme oluşturur bir <xref:System.Windows.Style> uygulama ayarı, tüm düğmeleri uygulanan <xref:System.Windows.FrameworkElement.Width%2A> 90 düğmelerin ve <xref:System.Windows.FrameworkElement.Margin%2A> 10:  
  
    ```xaml  
    <Application.Resources>  
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>  
    </Application.Resources>  
    ```  
  
     <xref:System.Windows.Style.TargetType%2A> Özellik belirtir stil türündeki tüm nesnelere uygulanır <xref:System.Windows.Controls.Button>. Her <xref:System.Windows.Setter> için farklı özellik değeri ayarlar <xref:System.Windows.Style>. Bu nedenle, bu noktada uygulamadaki her düğmenin genişliği 90 ve kenar boşluğu 10 vardır.  Uygulamayı çalıştırmak için F5 tuşuna basarsanız, aşağıdaki penceresine bakın.  
  
     ![Genişliği 90 ve kenar boşluğu 10 düğmeleriyle](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")  
  
     Çeşitli şekillerde hangi nesneleri hedeflenen ince ayar yapmak için de dahil olmak üzere, karmaşık özellik değerleri belirtme ve bile stilleri diğer stilleri için girdi olarak kullanarak stilleri ile yapabileceğiniz daha fazla yoktur. Daha fazla bilgi için bkz: [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
3.  **Bir kaynak için bir stil özellik değerini ayarla:** kaynakların yaygın olarak tanımlanan nesnelerin ve değerleri yeniden kullanmak için basit bir yol sağlar. Kodunuzu daha modüler hale getirmek için kaynakları kullanarak karmaşık değerleri tanımlamak özellikle yararlıdır. Aşağıdaki vurgulanmış biçimlendirmeyi için app.xaml ekleyin.  
  
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
  
     Doğrudan altında `Application.Resources` bloğu "GrayBlueGradientBrush" adlı bir kaynak oluşturuldu. Bu kaynak yatay bir gradyan tanımlar. Bu kaynak yerinden özellik değeri olarak kullanılabilir düğmesi stili ayarlayıcı içine dahil olmak üzere uygulamada <xref:System.Windows.Controls.Control.Background%2A> özelliği. Şimdi, tüm düğmeleri sahip bir <xref:System.Windows.Controls.Control.Background%2A> Bu geçişin özellik değeri.  
  
     Uygulamayı çalıştırmak için F5 tuşuna basın. Aşağıdaki gibi görünmelidir.  
  
     ![Gradyan arka planı düğmeleriyle](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")  
  
## <a name="create-a-template-that-defines-the-look-of-the-button"></a>Düğmenin görünümünü tanımlayan bir şablon oluşturma  
 Bu bölümde, düğmenin (sunu) görünümünü özelleştiren bir şablon oluşturun. Düğme sunusu dikdörtgenler ve diğer bileşenler dahil olmak üzere çeşitli nesnelerin benzersiz bir görünüm düğmesi kazandırmak için oluşur.  
  
 Şu ana kadar düğmeleri uygulamada nasıl göründüğünü denetim düğmesi özelliklerini değiştirme için sınırlı. Ne düğmenin görünümünü daha köklü değişiklikler yapmak isterseniz? Şablonlar, bir nesne sunumu üzerinde güçlü denetim etkinleştirir. Şablonları stilleri içinde kullanılabilir olmadığından (Bu kılavuzda düğmesi) stili uygulandığı tüm nesneler için bir şablon uygulayabilirsiniz.  
  
#### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>Düğmenin görünümünü tanımlamak için şablonu kullanmak için  
  
1.  **Şablonu ayarlayın:** gibi denetimlerin çünkü <xref:System.Windows.Controls.Button> sahip bir <xref:System.Windows.Controls.Control.Template%2A> özelliğine ayarlarız, yalnızca diğer özellik değerleri gibi şablon özellik değeri tanımlayabilirsiniz bir <xref:System.Windows.Style> kullanarak bir <xref:System.Windows.Setter>. Aşağıdaki vurgulanmış biçimlendirmeyi düğmesi stilinize ekleyin.  
  
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
  
2.  **Düğme sunusu alter:** bu noktada, şablonu tanımlamanız gerekir. Aşağıdaki vurgulanmış biçimlendirmeyi ekleyin. Bu biçimlendirme iki belirtir <xref:System.Windows.Shapes.Rectangle> yuvarlatılmış kenarlar ile öğeleri arkasından bir <xref:System.Windows.Controls.DockPanel>. <xref:System.Windows.Controls.DockPanel> Kullanılan ana bilgisayara <xref:System.Windows.Controls.ContentPresenter> düğmesinin. A <xref:System.Windows.Controls.ContentPresenter> düğmenin içeriğini görüntüler. Bu kılavuzda, içeriği metin ("Düğmesine 1", "Button 2", "Button 3") olur. Tüm şablon bileşenleri (dikdörtgenler ve <xref:System.Windows.Controls.DockPanel>) içinde düzenlenmiştir bir <xref:System.Windows.Controls.Grid>.  
  
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
  
     ![](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")  
  
3.  **Şablona bir glasseffect şablonuna ekleyin:** cam sonra ekleyeceksiniz. İlk olarak, cam gradyan etkisi oluşturmak bazı kaynakları oluşturun. İçindeki bu gradyan kaynaklarını herhangi bir yere ekleyin `Application.Resources` engelle:  
  
    ```xaml  
    <Application.Resources>  
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">     <GradientStop Color="WhiteSmoke" Offset="0.2" />     <GradientStop Color="Transparent" Offset="0.4" />     <GradientStop Color="WhiteSmoke" Offset="0.5" />     <GradientStop Color="Transparent" Offset="0.75" />     <GradientStop Color="WhiteSmoke" Offset="0.9" />     <GradientStop Color="Transparent" Offset="1" />   </GradientStopCollection>   <LinearGradientBrush x:Key="MyGlassBrushResource"     StartPoint="0,0" EndPoint="1,1" Opacity="0.75"     GradientStops="{StaticResource MyGlassGradientStopsResource}" />  
    <!-- Styles and other resources below here. -->  
    ```  
  
     Bu kaynaklar olarak kullanılan <xref:System.Windows.Shapes.Shape.Fill%2A> biz takın bir dikdörtgen için <xref:System.Windows.Controls.Grid> düğmesini şablonunun. Aşağıdaki vurgulanmış biçimlendirmeyi şablonuna ekleyin.  
  
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
  
     Dikkat <xref:System.Windows.UIElement.Opacity%2A> ile dikdörtgenin `x:Name` "glassCube" özelliği: 0, örneği çalıştırdığınızda, en üstte yer paylaşımlı Cam Dikdörtgen görmek için. Kullanıcı düğmesi ile etkileşim kurduğunda daha sonra Tetikleyiciler için şablonuna ekleyeceğiz olmasıdır. Ancak, düğme nasıl şimdi değiştirerek göründüğünü görebilirsiniz <xref:System.Windows.UIElement.Opacity%2A> değeri 1 ve uygulamayı çalıştırmak için. Aşağıdaki şekle bakın. Bir sonraki adıma devam etmeden önce değiştirmek <xref:System.Windows.UIElement.Opacity%2A> 0 dön.  
  
     ![XAML kullanılarak oluşturulmuş özel düğmeler](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-button-interactivity"></a>Etkileşimli düğme oluşturma  
 Bu bölümde, özellik tetikleyiciler ve özellik değerlerini değiştirmek ve fare işaretçisini düğmenin üzerine taşıyarak ve tıklatma gibi kullanıcı eylemleri yanıtta animasyonları çalıştırmak için olay tetikleyicileri oluşturur.  
  
 (Fare üzerinde fare bırakın, tıklatın ve benzeri) etkileşim eklemek için kolay bir yol, şablon veya stil içinde Tetikleyiciler tanımlamaktır. Oluşturmak için bir <xref:System.Windows.Trigger>, bir özellik "koşul" gibi tanımlayın: düğme <xref:System.Windows.UIElement.IsMouseOver%2A> özellik değeri eşittir `true`. Tetikleme koşulu doğru olduğunda, gerçekleşmesi ayarlayıcılar (Eylem) tanımlarsınız.  
  
#### <a name="to-create-button-interactivity"></a>Etkileşimli düğme oluşturmak için  
  
1.  **Şablon tetikleyicileri ekleyin:** şablonunuza vurgulanmış biçimlendirmeyi ekleyin.  
  
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
  
2.  **Özellik tetikleyicileri ekleyin:** vurgulanan biçimlendirmeleri eklemek `ControlTemplate.Triggers` engelle:  
  
    ```  
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     Uygulamayı çalıştırın ve fare işaretçisini düğmeleri çalışacak şekilde etkisini görmek için F5 tuşuna basın.  
  
3.  **Odak tetikleyicisi ekleyin:** ardından, düğme (örneğin, kullanıcı bunu tıklattıktan sonra) odağa sahip olduğunda durumu işlemek için bazı benzer ayarlayıcılar ekleyeceğiz.  
  
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
  
     Uygulamayı çalıştırın ve düğmeleri birini tıklatın için F5 tuşuna basın. Odağı hala içerdiğinden tıklattıktan sonra düğmesi vurgulanan kalır dikkat edin. Başka bir düğmesine tıklarsanız, sonuncu onu kaybederse ederken yeni düğme odağı kazanır.  
  
4.  **İçin animasyon ekleme** <xref:System.Windows.UIElement.MouseEnter> **ve** <xref:System.Windows.UIElement.MouseLeave> **:** bazı animasyonları tetikleyicilere sonraki ekleriz.   Herhangi bir yere içinde aşağıdaki biçimlendirmeleri eklemek `ControlTemplate.Triggers` bloğu.  
  
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
  
     Fare işaretçisini düğmenin üzerinde hareket işaretçi ayrıldığında normal boyutuna geri iade ettiğinde Cam Dikdörtgen küçültür.  
  
     İşaretçi düğmenin üzerine gittiğinde tetiklenen iki animasyon vardır (<xref:System.Windows.UIElement.MouseEnter> olayı oluşturulur). Animasyonlarına Cam Dikdörtgen X ve Y ekseni boyunca küçültün. Üzerindeki özelliklere dikkat edin <xref:System.Windows.Media.Animation.DoubleAnimation> öğeleri — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>. <xref:System.Windows.Media.Animation.Timeline.Duration%2A> Animasyonun yarım saniyenin, gerçekleşeceğini belirtir ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> cam 10 oranında küçültür belirtir.  
  
     İkinci olay tetikleyicisi (<xref:System.Windows.UIElement.MouseLeave>) yalnızca ilk durdurur. Ne zaman durdurup bir <xref:System.Windows.Media.Animation.Storyboard>, animasyonlu tüm özellikler varsayılan değerlerine döner. Kullanıcı işaretçiyi düğmeden taşındığında, bu nedenle, düğme geri düğmenin üzerinde fare imlecini taşındı önceki yol gider. Animasyon hakkında daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
5.  **Düğme tıklatıldığında için animasyon ekleme:** son adım kullanıcı düğmesine tıkladığında için bir tetikleyici eklemektir. Herhangi bir yere içinde aşağıdaki biçimlendirmeleri eklemek `ControlTemplate.Triggers` engelle:  
  
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
  
     Uygulamayı çalıştırın ve düğmeleri birini tıklatın için F5 tuşuna basın. Bir düğmeye tıkladığınızda, Cam Dikdörtgen çevrede döner.  
  
## <a name="summary"></a>Özet  
 Bu kılavuzda, aşağıdaki çalışmaları gerçekleştirdiniz:  
  
-   Hedeflenen bir <xref:System.Windows.Style> bir nesne türü için (<xref:System.Windows.Controls.Button>).  
  
-   Tüm uygulama kullanarak düğmelerin temel özelliklerini kontrol <xref:System.Windows.Style>.  
  
-   Oluşturulan özellik değerleri için kullanılacak gradyan gibi kaynakları <xref:System.Windows.Style> ayarlayıcılar.  
  
-   Tüm uygulama düğmelerini görünümünü düğmeleri için bir şablon uygulayarak özelleştirilmiş.  
  
-   Özelleştirilmiş kullanıcı eylemlerine yanıt olarak düğme davranışını (gibi <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, ve <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) animasyon efektleri dahil.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Microsoft Expression Blend Kullanarak Düğme Oluşturma](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)  
 [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Bit Eşlem Etkilerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)
