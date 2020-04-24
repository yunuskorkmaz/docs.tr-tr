---
title: 'Walkthrough: Stil WPF içeriği'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 07241d41e3fbf270a76bd241765bfa369ee265d5
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646325"
---
# <a name="walkthrough-style-wpf-content"></a>Walkthrough: Stil WPF içeriği

Bu makalede, bir Windows Formu'nda barındırılan bir Windows Sunu Temeli (WPF) denetimine stil nasıl uygulanacağı gösterilmektedir.

## <a name="prerequisites"></a>Ön koşullar

Bu walkthrough tamamlamak için Visual Studio gerekir.

## <a name="create-the-project"></a>Proje oluşturma

Visual Studio'yu açın ve Visual Basic veya Visual C# adlı `StylingWpfContent`yeni bir Windows Forms Uygulama projesi oluşturun.

> [!NOTE]
> WPF içeriği barındırırken yalnızca C# ve Visual Basic projeleri desteklenir.

## <a name="create-the-wpf-control-types"></a>WPF denetim türlerini oluşturma

Projeye bir WPF denetim türü ekledikten sonra, bunu <xref:System.Windows.Forms.Integration.ElementHost> bir denetimde barındırabilirsiniz.

1. Çözüme yeni <xref:System.Windows.Controls.UserControl> bir WPF projesi ekleyin. Denetim türü için varsayılan adı `UserControl1.xaml`kullanın. Daha fazla bilgi için [Bkz. Walkthrough: Tasarım Zamanında Windows Formlarında Yeni WPF İçeriği Oluşturma](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. Tasarım görünümünde, seçildiğinden `UserControl1` emin olun.

3. **Özellikler** penceresinde, **200**değerini <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> ve özelliklerini ayarlayın.

4. Bir <xref:System.Windows.Controls.Button?displayProperty=nameWithType> denetim ekleyin <xref:System.Windows.Controls.UserControl> ve <xref:System.Windows.Controls.ContentControl.Content%2A> **özelliğin**değerini İptal etmek için ayarlayın.

5. İkinci <xref:System.Windows.Controls.Button?displayProperty=nameWithType> bir denetim <xref:System.Windows.Controls.UserControl> ekleyin ve <xref:System.Windows.Controls.ContentControl.Content%2A> özelliğin değerini **Tamam'a**ayarlayın.

6. Projeyi derleyin.

## <a name="apply-a-style-to-a-wpf-control"></a>WPF Denetimine Stil Uygulama

Görünümünü ve davranışını değiştirmek için WPF denetimine farklı stil uygulayabilirsiniz.

1. Windows `Form1` Forms Designer'da açın.

1. Araç **Kutusunda,** formda bir `UserControl1` örneğini `UserControl1` oluşturmak için çift tıklatın.

   Bir örneği `UserControl1` adlı <xref:System.Windows.Forms.Integration.ElementHost> `elementHost1`yeni bir denetimde barındırılır.

1. Akıllı etiket panelinde `elementHost1`açılan listeden **Barındırılan İçeriği** Düzenle'yi tıklatın.

   `UserControl1`WPF Tasarımcısı'nda açılır.

1. XAML görünümünde, açılış etiketinden sonra `<UserControl>` aşağıdaki XAML'yi ekleyin. Bu XAML zıt degrade kenarlıklı bir degrade oluşturur. Denetim tıklatıldığında, basıldığında düğme görünümü oluşturmak için degradeler değiştirilir. Daha fazla bilgi için [Stil ve Templating'e](../../../desktop-wpf/fundamentals/styles-templates-overview.md)bakın.

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

1. İptal `SimpleButton` düğmesinin `<Button>` etiketine aşağıdaki XAML'yi ekleyerek önceki adımda tanımlanan stili **İptal** düğmesine uygulayın.

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   Düğme bildiriminiz aşağıdaki XAML'ye benzeyecektir:

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. Projeyi derleyin.

1. Windows `Form1` Forms Designer'da açın.

1. Yeni stil düğme denetimine uygulanır.

1. Hata **Ayıklama** menüsünden, uygulamayı çalıştırmak için **Hata Ayıklama'yı Başlat'ı** seçin.

1. **Tamam** ve **İptal** düğmelerini tıklatın ve farklılıkları görüntüleyin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Geçiş ve Birlikte Çalışabilirlik](../../wpf/advanced/migration-and-interoperability.md)
- [WPF Denetimlerini Kullanma](using-wpf-controls.md)
- [Visual Studio’da XAML tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
