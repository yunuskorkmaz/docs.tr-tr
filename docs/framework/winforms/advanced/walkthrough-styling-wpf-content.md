---
title: 'İzlenecek yol: WPF İçeriği için Stil Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
ms.openlocfilehash: 32ca9658ddf4ab6e8690f29797b7ac7b09df2ca7
ms.sourcegitcommit: d98fdb087d9c8aba7d2cb93fe4b4ee35a2308cee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69012954"
---
# <a name="walkthrough-style-wpf-content"></a>İzlenecek yol: Biçim WPF içeriği

Bu izlenecek yol, bir Windows formunda barındırılan bir Windows Presentation Foundation (WPF) denetimine nasıl stil uygulanacağını gösterir.

 Bu kılavuzda, aşağıdaki görevleri gerçekleştirirsiniz:

- Projeyi oluşturun.

- WPF denetim türünü oluşturun.

- WPF denetimine bir stil uygulayın.

## <a name="prerequisites"></a>Önkoşullar

Bu yönergeyi tamamlamak için Visual Studio gerekir.

## <a name="create-the-project"></a>Projeyi oluşturma

Visual Studio 'Yu açın ve Visual Basic veya görsel C# adlı `StylingWpfContent`yeni bir Windows Forms uygulama projesi oluşturun.

> [!NOTE]
> WPF içeriği barındırırken yalnızca C# ve Visual Basic projeleri desteklenir.

## <a name="create-the-wpf-control-types"></a>WPF denetim türlerini oluşturma

Projeye bir WPF denetim türü ekledikten sonra, bunu bir <xref:System.Windows.Forms.Integration.ElementHost> denetimde barındırabilirsiniz.

1. Çözüme yeni bir WPF <xref:System.Windows.Controls.UserControl> projesi ekleyin. Denetim türü için varsayılan adı kullanın, `UserControl1.xaml`. Daha fazla bilgi için bkz [. İzlenecek yol: Tasarım zamanında](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)Windows Forms yeni WPF içeriği oluşturuluyor.

2. Tasarım görünümü ' de, ' `UserControl1` nin seçili olduğundan emin olun. Daha fazla bilgi için [nasıl yapılır: Tasarım Yüzeyi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100))öğeleri seçin ve taşıyın.

3. **Özellikler** penceresinde, <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin değerini olarak `200`ayarlayın.

4. Öğesine bir <xref:System.Windows.Controls.Button?displayProperty=nameWithType> denetim ekleyin <xref:System.Windows.Controls.ContentControl.Content%2A>ve özelliğin değerini iptal olarak ayarlayın. <xref:System.Windows.Controls.UserControl>

5. Öğesine ikinci <xref:System.Windows.Controls.Button?displayProperty=nameWithType> bir denetim ekleyin <xref:System.Windows.Controls.ContentControl.Content%2A>ve özelliğinin değerini Tamam olarak ayarlayın <xref:System.Windows.Controls.UserControl> .

6. Projeyi oluşturun.

## <a name="apply-a-style-to-a-wpf-control"></a>WPF denetimine stil uygulama

Görünümünü ve davranışını değiştirmek için WPF denetimine farklı stil uygulayabilirsiniz.

1. Windows Form Tasarımcısı `Form1` açın.

1. **Araç kutusunda**, form `UserControl1` üzerinde bir örnek `UserControl1` oluşturmak için çift tıklayın.

     Bir örneği `UserControl1` adlı <xref:System.Windows.Forms.Integration.ElementHost> Yeni`elementHost1`bir denetimde barındırılır.

1. İçin `elementHost1`akıllı etiket panelinde, açılan listeden **barındırılan içeriği Düzenle** ' ye tıklayın.

     `UserControl1`içinde [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]açılır.

1. Xaml görünümünde, `<UserControl>` açılış etiketinden sonra aşağıdaki xaml 'yi ekleyin.

     Bu XAML, çakışan gradyan kenarlığı olan bir gradyan oluşturur. Denetime tıklandığında degradeler, basılan düğme görünümü oluşturacak şekilde değiştirilir. Daha fazla bilgi için bkz. [Stil oluşturma ve şablon](../../wpf/controls/styling-and-templating.md)oluşturma.

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

1. Aşağıdaki XAML 'yi İptal düğmesinin `<Button>` etiketine ekleyerek, önceki adımda tanımlanan stili`SimpleButton` iptal düğmesine uygulayın.

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

1. Tamam ve Iptal düğmelerini tıklatın ve farkları görüntüleyin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Geçiş ve Birlikte Çalışabilirlik](../../wpf/advanced/migration-and-interoperability.md)
- [WPF Denetimlerini Kullanma](using-wpf-controls.md)
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
- [XAML'ye Genel Bakış (WPF)](../../wpf/advanced/xaml-overview-wpf.md)
- [Stil ve Şablon Oluşturma](../../wpf/controls/styling-and-templating.md)
