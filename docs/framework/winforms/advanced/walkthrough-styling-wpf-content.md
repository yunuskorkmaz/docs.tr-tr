---
title: 'İzlenecek yol: biçim WPF içeriği'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e52297f51c74fc3dba93c987fd5b9bd5b6801777
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732548"
---
# <a name="walkthrough-style-wpf-content"></a>İzlenecek yol: biçim WPF içeriği

Bu makalede, bir Windows formunda barındırılan bir Windows Presentation Foundation (WPF) denetimine stil uygulamayı nasıl uygulayacağınız gösterilmektedir.

## <a name="prerequisites"></a>Prerequisites

Bu yönergeyi tamamlamak için Visual Studio gerekir.

## <a name="create-the-project"></a>Projeyi oluşturma

Visual Studio 'Yu açın ve Visual Basic veya görsel C# adlı `StylingWpfContent`Windows Forms uygulama projesi oluşturun.

> [!NOTE]
> WPF içeriği barındırırken yalnızca C# ve Visual Basic projeleri desteklenir.

## <a name="create-the-wpf-control-types"></a>WPF denetim türlerini oluşturma

Projeye bir WPF denetim türü ekledikten sonra, bunu bir <xref:System.Windows.Forms.Integration.ElementHost> denetiminde barındırabilirsiniz.

1. Çözüme yeni bir WPF <xref:System.Windows.Controls.UserControl> projesi ekleyin. Denetim türü için varsayılan adı kullanın, `UserControl1.xaml`. Daha fazla bilgi için bkz. [Izlenecek yol: tasarım zamanında Windows Forms yenı WPF Içeriği oluşturma](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. Tasarım görünümü ' de `UserControl1` ' nin seçili olduğundan emin olun.

3. **Özellikler** penceresinde <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin değerini **200**olarak ayarlayın.

4. <xref:System.Windows.Controls.UserControl> <xref:System.Windows.Controls.Button?displayProperty=nameWithType> bir denetim ekleyin ve <xref:System.Windows.Controls.ContentControl.Content%2A> özelliğinin değerini **iptal**olarak ayarlayın.

5. <xref:System.Windows.Controls.UserControl> ikinci bir <xref:System.Windows.Controls.Button?displayProperty=nameWithType> denetimi ekleyin ve <xref:System.Windows.Controls.ContentControl.Content%2A> özelliğinin değerini **Tamam**olarak ayarlayın.

6. Projeyi oluşturun.

## <a name="apply-a-style-to-a-wpf-control"></a>WPF denetimine stil uygulama

Görünümünü ve davranışını değiştirmek için WPF denetimine farklı stil uygulayabilirsiniz.

1. Windows Form Tasarımcısı `Form1` açın.

1. **Araç kutusunda**`UserControl1` ' ye çift tıklayarak formda `UserControl1` bir örneğini oluşturun.

   `UserControl1` örneği, `elementHost1`adlı yeni bir <xref:System.Windows.Forms.Integration.ElementHost> denetiminde barındırılır.

1. `elementHost1`için akıllı etiket panelinde, açılan listeden **barındırılan Içeriği Düzenle** ' ye tıklayın.

   `UserControl1` WPF tasarımcısında açılır.

1. XAML görünümü ' nde, `<UserControl>` açýlýþ etiketinden sonra aşağıdaki XAML 'yi ekleyin. Bu XAML, çakışan gradyan kenarlığı olan bir gradyan oluşturur. Denetime tıklandığında degradeler, basılan düğme görünümü oluşturacak şekilde değiştirilir. Daha fazla bilgi için bkz. [Stil oluşturma ve şablon](../../../desktop-wpf/fundamentals/styles-templates-overview.md)oluşturma.

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

1. Aşağıdaki XAML 'yi **iptal** düğmesinin `<Button>` etiketine ekleyerek, önceki adımda tanımlanan `SimpleButton` stilini iptal düğmesine uygulayın.

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   Düğme bildirimidir aşağıdaki XAML 'ye benzeyecektir:

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. Projeyi oluşturun.

1. Windows Form Tasarımcısı `Form1` açın.

1. Yeni stil düğme denetimine uygulanır.

1. **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat** ' ı seçerek uygulamayı çalıştırın.

1. **Tamam** ve **iptal** düğmelerini tıklatın ve farkları görüntüleyin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Geçiş ve Birlikte Çalışabilirlik](../../wpf/advanced/migration-and-interoperability.md)
- [WPF Denetimlerini Kullanma](using-wpf-controls.md)
- [Visual Studio’da XAML tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [XAML'ye Genel Bakış (WPF)](../../wpf/advanced/xaml-overview-wpf.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
