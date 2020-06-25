---
title: Stiller ve şablonlar
description: .NET Core için Windows Presentation Foundation (WPF) içindeki XAML Kaynakları hakkında bilgi edinin. Stiller ve Temalar ile ilgili XAML kaynaklarının türlerini anlayın.
author: adegeo
ms.author: adegeo
ms.date: 09/09/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: faa54e0a3c827717114ca6ca4f033c1c4c3acfa8
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325782"
---
# <a name="styles-and-templates-in-wpf"></a>WPF 'deki stiller ve şablonlar

Windows Presentation Foundation (WPF) stili ve şablon oluşturma, geliştiricilerin ve tasarımcıların görsel açıdan etkileyici efektler ve ürün için tutarlı bir görünüm oluşturmalarına olanak tanıyan bir özellik paketine başvurur. Bir uygulamanın görünümünü özelleştirirken, uygulamalar içinde ve arasında görünüm ve paylaşım imkanı sağlayan güçlü bir stil ve şablon oluşturma modeli istiyorsunuz. WPF bu modeli sağlar.

WPF stil modelinin başka bir özelliği de sununun ve mantığın ayrımı olur. Tasarımcılar, geliştiricilerin C# veya Visual Basic kullanarak programlama mantığı üzerinde çalıştığı aynı anda yalnızca XAML kullanarak bir uygulamanın görünümü üzerinde çalışabilir.

Bu genel bakış, uygulamanın stil ve şablon oluşturma yönlerine odaklanır ve veri bağlama kavramlarını ele almaz. Veri bağlama hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md).

Stillerin ve şablonların yeniden kullanılmasını sağlayan kaynakları anlamanız önemlidir. Kaynaklar hakkında daha fazla bilgi için bkz. [xaml kaynakları](xaml-resources-define.md).

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sample"></a>Örnek

Bu genel bakışta verilen örnek kod, aşağıdaki çizimde gösterilen [basit bir fotoğraf tarama uygulamasına](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) dayalıdır.

![Stilli ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

Bu basit fotoğraf örneği, görsel açıdan etkileyici bir kullanıcı deneyimi oluşturmak için stil ve şablon oluşturma kullanır. Örnekte, iki <xref:System.Windows.Controls.TextBlock> öğe ve bir <xref:System.Windows.Controls.ListBox> görüntü listesine bağlanan bir denetim vardır.

Tüm örnek için bkz. [Stil ve şablon oluşturma örneğine giriş](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).

## <a name="styles"></a>Stiller

Bir <xref:System.Windows.Style> özellik değerleri kümesini birden çok öğeye uygulamak için kullanışlı bir yol olarak düşünebilirsiniz. Ya da ' dan türetilen herhangi bir öğe için bir stil <xref:System.Windows.FrameworkElement> kullanabilirsiniz <xref:System.Windows.FrameworkContentElement> <xref:System.Windows.Window> <xref:System.Windows.Controls.Button> .

Bir stil belirtmenin en yaygın yolu, `Resources` BIR xaml dosyasındaki bölümünde kaynak olarak kullanılır. Stiller kaynaklar olduğundan, tüm kaynaklar için uygulanan aynı kapsam kurallarına uyar. Basitçe, stilin uygulanabileceğini bir stil bildirdiğiniz yere koyun. Örneğin, stili uygulama tanımı XAML dosyanızın kök öğesinde bildirirseniz, bu stil uygulamanızda herhangi bir yerde kullanılabilir.

Örneğin, aşağıdaki XAML kodu bir için iki stil bildirir, bir `TextBlock` otomatik olarak tüm `TextBlock` öğelere uygulanır ve açıkça başvurulması gereken başka bir tane.

[!code-xaml[SnippetDefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

Yukarıda belirtilen stillerin bir örneği aşağıda verilmiştir.

[!code-xaml[SnippetTextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

![Stilli metinblokları](./media/styles-and-templates-overview/stylingintro-textblocks.png)

Daha fazla bilgi için bkz. [Denetim için stil oluşturma](styles-templates-create-apply-style.md).

## <a name="controltemplates"></a>ControlTemplates

WPF 'de <xref:System.Windows.Controls.ControlTemplate> bir denetim, denetimin görünümünü tanımlar. Bir denetimin yapısını ve görünümünü, yeni bir tanımlayarak bir <xref:System.Windows.Controls.ControlTemplate> denetime atayarak değiştirebilirsiniz. Birçok durumda, şablonlar size, kendi özel denetimlerinizi yazmak zorunda olmadığınız için yeterli esneklik sunar.

Her denetimin [Control. Template](xref:System.Windows.Controls.Control.Template) özelliğine atanmış varsayılan bir şablonu vardır. Şablon, denetimin özelliklerine sahip olan denetimin görsel sunumunu bağlar. XAML 'de bir şablon tanımladığınız için, herhangi bir kod yazmadan denetimin görünümünü değiştirebilirsiniz. Her şablon, gibi belirli bir denetim için tasarlanmıştır <xref:System.Windows.Controls.Button> .

Genellikle bir şablonu bir XAML dosyasının bölümünde kaynak olarak bildirirsiniz `Resources` . Tüm kaynaklarda olduğu gibi, kapsam kuralları da geçerlidir.

Denetim şablonları, bir stille daha fazla yer kaplar. Bunun nedeni denetim şablonunun tüm denetimin görsel görünümünü yeniden, ancak bir stil ise yalnızca var olan denetimdeki özellik değişikliklerini uygular. Ancak, denetimin şablonu [Control. Template](xref:System.Windows.Controls.Control.Template) özelliği ayarlanarak uygulandığından, bir şablon tanımlamak veya ayarlamak için bir stil kullanabilirsiniz.

Tasarımcılar genellikle var olan bir şablonun bir kopyasını oluşturmanıza ve bunu değiştirmenize izin verir. Örneğin, Visual Studio WPF Tasarımcısında bir `CheckBox` denetim seçin ve sağ tıklayın ve **Şablonu Düzenle**' yi seçin  >  **Create a copy**. Bu komut *, bir şablonu tanımlayan bir stil*oluşturur.

```xaml
<Style x:Key="CheckBoxStyle1" TargetType="{x:Type CheckBox}">
    <Setter Property="FocusVisualStyle" Value="{StaticResource FocusVisual1}"/>
    <Setter Property="Background" Value="{StaticResource OptionMark.Static.Background1}"/>
    <Setter Property="BorderBrush" Value="{StaticResource OptionMark.Static.Border1}"/>
    <Setter Property="Foreground" Value="{DynamicResource {x:Static SystemColors.ControlTextBrushKey}}"/>
    <Setter Property="BorderThickness" Value="1"/>
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="{x:Type CheckBox}">
                <Grid x:Name="templateRoot" Background="Transparent" SnapsToDevicePixels="True">
                    <Grid.ColumnDefinitions>
                        <ColumnDefinition Width="Auto"/>
                        <ColumnDefinition Width="*"/>
                    </Grid.ColumnDefinitions>
                    <Border x:Name="checkBoxBorder" Background="{TemplateBinding Background}" BorderThickness="{TemplateBinding BorderThickness}" BorderBrush="{TemplateBinding BorderBrush}" HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="1" VerticalAlignment="{TemplateBinding VerticalContentAlignment}">
                        <Grid x:Name="markGrid">
                            <Path x:Name="optionMark" Data="F1 M 9.97498,1.22334L 4.6983,9.09834L 4.52164,9.09834L 0,5.19331L 1.27664,3.52165L 4.255,6.08833L 8.33331,1.52588e-005L 9.97498,1.22334 Z " Fill="{StaticResource OptionMark.Static.Glyph1}" Margin="1" Opacity="0" Stretch="None"/>
                            <Rectangle x:Name="indeterminateMark" Fill="{StaticResource OptionMark.Static.Glyph1}" Margin="2" Opacity="0"/>
                        </Grid>
                    </Border>
                    <ContentPresenter x:Name="contentPresenter" Grid.Column="1" Focusable="False" HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" RecognizesAccessKey="True" SnapsToDevicePixels="{TemplateBinding SnapsToDevicePixels}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}"/>
                </Grid>
                <ControlTemplate.Triggers>
                    <Trigger Property="HasContent" Value="true">
                        <Setter Property="FocusVisualStyle" Value="{StaticResource OptionMarkFocusVisual1}"/>
                        <Setter Property="Padding" Value="4,-1,0,0"/>

... content removed to save space ...
```

Şablonun bir kopyasının düzenlenmesinin, şablonların nasıl çalıştığını öğrenmek için harika bir yoldur. Yeni boş bir şablon oluşturmak yerine, bir kopyayı düzenlemek ve görsel sununun birkaç yönlerini değiştirmek daha kolaydır.

Bir örnek için bkz. [bir denetim için şablon oluşturma](../themes/how-to-create-apply-template.md).

### <a name="templatebinding"></a>TemplateBinding

Önceki bölümde tanımlanan şablon kaynağının [TemplateBinding biçimlendirme uzantısını](../../framework/wpf/advanced/templatebinding-markup-extension.md)kullandığını fark etmiş olabilirsiniz. `TemplateBinding`, İle oluşturulmuş bir bağlamaya benzer şekilde, şablon senaryoları için bir bağlamanın en iyi duruma getirilmiş bir biçimidir `{Binding RelativeSource={RelativeSource TemplatedParent}}` . `TemplateBinding`, şablonun parçalarını denetimin özelliklerine bağlamak için yararlıdır. Örneğin, her denetimin bir özelliği vardır <xref:System.Windows.Controls.Control.BorderThickness> . `TemplateBinding`Şablondaki hangi öğenin bu denetim ayarından etkilendiğini yönetmek için kullanın.

### <a name="contentcontrol-and-itemscontrol"></a>ContentControl ve ItemsControl

, <xref:System.Windows.Controls.ContentPresenter> Bir içinde bildiriminde bildirilirse, <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ContentControl> <xref:System.Windows.Controls.ContentPresenter> otomatik olarak <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> ve <xref:System.Windows.Controls.ContentControl.Content%2A> özelliklerine bağlanır. Benzer şekilde, <xref:System.Windows.Controls.ItemsPresenter> içinde olan bir, <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ItemsControl> ve özelliklerine otomatik olarak bağlanır <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.ItemsControl.Items%2A> .

## <a name="datatemplates"></a>Veri şablonları

Bu örnek uygulamada, <xref:System.Windows.Controls.ListBox> bir fotoğraf listesine bağlanan bir denetim vardır.

[!code-xaml[ListBox](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window3.xaml#SnippetListBox)]

Bu <xref:System.Windows.Controls.ListBox> Şu anda aşağıdaki gibi görünüyor.

![Şablonu uygulamadan önce ListBox](./media/styles-and-templates-overview/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")

Çoğu denetim bazı içerik türlerine sahiptir ve içerik genellikle bağladığınız verilerden gelir. Bu örnekte, veriler fotoğraflar listesidir. WPF 'de, <xref:System.Windows.DataTemplate> verilerin görsel temsilini tanımlamak için kullanırsınız. Temel olarak, ' a yerleştirdiğiniz özellikler, <xref:System.Windows.DataTemplate> işlenen uygulamada verilerin ne şekilde göründüğünü belirler.

Örnek uygulamamızda her özel nesne, `Photo` `Source` görüntünün dosya yolunu belirten String türünde bir özelliğe sahiptir. Şu anda, fotoğraf nesneleri dosya yolları olarak görünür.

[!code-csharp[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Photo.cs#PhotoClass)]
[!code-vb[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/Photo.vb#PhotoClass)]

Fotoğrafların görüntü olarak görünmesi için <xref:System.Windows.DataTemplate> kaynak olarak bir oluşturun.

[!code-xaml[DataTemplate](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window4.xaml#SnippetDataTemplate)]

<xref:System.Windows.DataTemplate.DataType%2A>Özelliğinin özelliğine benzediğine dikkat edin <xref:System.Windows.Style.TargetType%2A> <xref:System.Windows.Style> . <xref:System.Windows.DataTemplate>Kaynaklar bölümünde ise, <xref:System.Windows.DataTemplate.DataType%2A> bir tür için özelliği belirttiğinizde ve bir öğesini atarsanız, `x:Key` <xref:System.Windows.DataTemplate> Bu tür her göründüğünde uygulanır. Her zaman <xref:System.Windows.DataTemplate> öğesini ile atama `x:Key` ve `StaticResource` <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özellik veya özellik gibi türleri alan özellikler için bir olarak ayarlama <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> seçeneğiniz vardır.

Temel olarak, <xref:System.Windows.DataTemplate> Yukarıdaki örnekteki bir nesne olduğunda, bir, `Photo` içinde olarak görünmesi gerektiğini tanımlar <xref:System.Windows.Controls.Image> <xref:System.Windows.Controls.Border> . Bununla birlikte <xref:System.Windows.DataTemplate> , uygulamamız artık şuna benzer.

![Fotoğraf resmi](./media/styles-and-templates-overview/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")

Veri şablonu oluşturma modeli, diğer özellikleri sağlar. Örneğin, veya gibi bir tür kullanarak diğer koleksiyonları içeren koleksiyon verileri görüntülüyorsanız, <xref:System.Windows.Controls.HeaderedItemsControl> <xref:System.Windows.Controls.Menu> <xref:System.Windows.Controls.TreeView> <xref:System.Windows.HierarchicalDataTemplate> . Başka bir veri şablonu oluşturma özelliği, <xref:System.Windows.Controls.DataTemplateSelector> <xref:System.Windows.DataTemplate> özel mantığa göre kullanmak üzere seçeneğini seçmenize olanak sağlar. Daha fazla bilgi için, farklı veri şablonu oluşturma özellikleri hakkında daha ayrıntılı bir tartışma sağlayan [veri şablonu oluşturmaya genel bakış](../../framework/wpf/data/data-templating-overview.md)bölümüne bakın.

## <a name="triggers"></a>Tetikleyiciler

Bir tetikleyici, özellik değeri değiştiğinde veya bir olay ortaya çıktığında animasyon gibi eylemleri ayarlar veya başlatır. <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate> , ve <xref:System.Windows.DataTemplate> hepsi `Triggers` bir tetikleyici kümesi içerebilen bir özelliğine sahiptir. Birkaç tetikleyici türü vardır.

### <a name="propertytriggers"></a>PropertyTriggers

Özellik <xref:System.Windows.Trigger> değerlerini ayarlayan veya bir özelliğin değerine göre eylemleri Başlatan bir özellik tetikleyicisi olarak adlandırılır.

Özellik tetiklerinin nasıl kullanılacağını göstermek için, seçili değilse her bir <xref:System.Windows.Controls.ListBoxItem> kısmen saydam yapabilirsiniz. Aşağıdaki stil, <xref:System.Windows.UIElement.Opacity%2A> a değerini <xref:System.Windows.Controls.ListBoxItem> olarak ayarlar `0.5` . Ancak, özelliği olduğunda, olarak <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> `true` <xref:System.Windows.UIElement.Opacity%2A> ayarlanır `1.0` .

[!code-xaml[PropertyTrigger](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window5.xaml#SnippetPropertyTrigger)]

Bu örnek, bir <xref:System.Windows.Trigger> özellik değeri ayarlamak için bir kullanır, ancak <xref:System.Windows.Trigger> sınıfın, <xref:System.Windows.TriggerBase.EnterActions%2A> <xref:System.Windows.TriggerBase.ExitActions%2A> bir tetikleyicinin eylemleri gerçekleştirmesini sağlayan ve özellikleri de olduğunu unutmayın.

<xref:System.Windows.FrameworkElement.MaxHeight%2A>Öğesinin özelliğinin <xref:System.Windows.Controls.ListBoxItem> olarak ayarlandığını unutmayın `75` . Aşağıdaki çizimde, üçüncü öğe seçili öğedir.

![Stilli ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

### <a name="eventtriggers-and-storyboards"></a>EventTriggers ve film şeritleri

Bir <xref:System.Windows.EventTrigger> olay oluşumuna göre bir dizi eylem başlatan, başka bir tetikleyici türü. Örneğin, aşağıdaki <xref:System.Windows.EventTrigger> nesneler fare işaretçisi <xref:System.Windows.Controls.ListBoxItem> üzerine girdiğinde, <xref:System.Windows.FrameworkElement.MaxHeight%2A> özelliği `90` ikinci bir dönemdeki bir değere hareketlendirir `0.2` . Fare öğeden uzaklaştığında, özelliği ikinci bir süre içinde orijinal değere döner `1` . Animasyon için bir değer belirtmek için nasıl gerekli değildir Not <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> <xref:System.Windows.ContentElement.MouseLeave> . Bunun nedeni, animasyonun özgün değeri takip edebilmesini sağlar.

[!code-xaml[StyleEventTriggers](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window6.xaml#SnippetStyleEventTriggers)]

Daha fazla bilgi için görsel taslaklara [genel bakış](../../framework/wpf/graphics-multimedia/storyboards-overview.md)bölümüne bakın.

Aşağıdaki çizimde, fare üçüncü öğeyi işaret ediyor.

![Stil örnek ekran görüntüsü](./media/styles-and-templates-overview/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>Çoklu Tetikleyiciler, veri Tetikleyicileri ve MultiDataTriggers

Ve ' ye ek olarak <xref:System.Windows.Trigger> <xref:System.Windows.EventTrigger> , başka tetikleyici türleri de vardır. <xref:System.Windows.MultiTrigger>özellik değerlerini birden çok koşula göre ayarlamanıza olanak sağlar. <xref:System.Windows.DataTrigger> <xref:System.Windows.MultiDataTrigger> Koşulunuz özelliği veri ile bağlantılı olduğunda ve kullanın.

## <a name="visual-states"></a>Görsel durumlar

Denetimler her zaman belirli bir **durumda**. Örneğin, fare bir denetimin yüzeyi üzerinde dolaştığında, denetim ortak bir durumunda olduğu kabul edilir `MouseOver` . Belirli bir durumu olmayan bir denetim, ortak durumda olduğu kabul edilir `Normal` . Durumlar gruplar halinde bozulur ve yukarıda bahsedilen durumlar durum grubunun bir parçasıdır `CommonStates` . Çoğu denetim iki durum grubuna sahiptir: `CommonStates` ve `FocusStates` . Bir denetime uygulanan her bir durum grubunda, bir denetim her bir grubun ve gibi her zaman bir durumdadır `CommonStates.MouseOver` `FocusStates.Unfocused` . Ancak, bir denetim aynı grup içindeki ve gibi iki farklı durumda olamaz `CommonStates.Normal` `CommonStates.Disabled` . Denetimlerin çoğu tarafından tanınmasına ve kullanımına yönelik bir eyalet tablosu aşağıda verilmiştir.

| VisualState adı | VisualStateGroup adı | Description |
| ---------------- | --------------------- | ----------- |
| Normal           | Ortak durumlar          | Varsayılan durum. |
| Gelme olayından        | Ortak durumlar          | Fare işaretçisi denetimin üzerine yerleştirilir. |
| Pressed          | Ortak durumlar          | Denetime basıldığında. |
| Devre dışı         | Ortak durumlar          | Denetim devre dışı bırakıldı. |
| Odaklı          | Odaklardaki durumlar           | Denetim odağa sahiptir. |
| Odaklanmadan gözetle        | Odaklardaki durumlar           | Denetimin odağı yok. |

Bir <xref:System.Windows.VisualStateManager?displayProperty=fullName> denetim şablonunun kök öğesinde bir tanımlayarak, bir denetim belirli bir duruma girdiğinde animasyonları tetikleyebilirsiniz. , `VisualStateManager` Hangi birleşimlerinin <xref:System.Windows.VisualStateGroup> ve izlenecek olduğunu bildirir <xref:System.Windows.VisualState> . Denetim bir izlenen duruma girdiğinde, tarafından tanımlanan animasyon `VisaulStateManager` başlatılır.

Örneğin, aşağıdaki XAML kodu, `CommonStates.MouseOver` adlı öğenin Fill rengine animasyon eklemek için durumu izler `backgroundElement` . Denetim `CommonStates.Normal` duruma döndüğünde adlı öğesinin Fill Color `backgroundElement` geri yüklenir.

```xaml
<ControlTemplate x:Key="roundbutton" TargetType="Button">
    <Grid>
        <VisualStateManager.VisualStateGroups>
            <VisualStateGroup Name="CommonStates">
                <VisualState Name="Normal">
                    <ColorAnimation Storyboard.TargetName="backgroundElement"
                                    Storyboard.TargetProperty="(Shape.Fill).(SolidColorBrush.Color)"
                                    To="{TemplateBinding Background}"
                                    Duration="0:0:0.3"/>
                </VisualState>
                <VisualState Name="MouseOver">
                    <ColorAnimation Storyboard.TargetName="backgroundElement"
                                    Storyboard.TargetProperty="(Shape.Fill).(SolidColorBrush.Color)"
                                    To="Yellow"
                                    Duration="0:0:0.3"/>
                </VisualState>
            </VisualStateGroup>
        </VisualStateManager.VisualStateGroups>

        ...
```

Görsel Taslaklar hakkında daha fazla bilgi için bkz. [görsel taslakları genel bakış](../../framework/wpf/graphics-multimedia/storyboards-overview.md).

## <a name="shared-resources-and-themes"></a>Paylaşılan kaynaklar ve Temalar

Tipik bir WPF uygulamasında, uygulamanın tamamında uygulanan birden çok UI kaynağı olabilir. Toplu olarak, bu kaynak kümesi uygulama için tema olarak kabul edilebilir. WPF, sınıf olarak Kapsüllenen bir kaynak sözlüğü kullanarak, Kullanıcı arabirimi kaynaklarını bir tema olarak paketleme desteği sağlar <xref:System.Windows.ResourceDictionary> .

WPF temaları, WPF 'nin herhangi bir öğenin görsellerini özelleştirmek için sunduğu stil oluşturma ve şablon oluşturma mekanizması kullanılarak tanımlanır.

WPF teması kaynakları, gömülü kaynak sözlüklerinde depolanır. Bu kaynak sözlüklerinin imzalı bir derleme içine katıştırılması ve kodun kendisi ya da yan yana bütünleştirilmiş kodda aynı derlemeye katıştırılması gerekir. PresentationFramework.dll için WPF denetimleri içeren bütünleştirilmiş kod, tema kaynakları ise yan yana derlemelerin bir dizisidir.

Tema, bir öğenin stilini ararken bakacağız son yer olur. Genellikle arama, uygun bir kaynak için arama öğesi ağacının ardından başlatılır, ardından uygulama kaynak koleksiyonuna bakar ve son olarak sistemi sorgular. Bu, uygulama geliştiricilere, temaya ulaşmadan önce ağaç veya uygulama düzeyindeki herhangi bir nesnenin stilini yeniden tanımlamayı sağlar.

Kaynak sözlüklerini birden çok uygulama genelinde bir temayı yeniden kullanmanıza imkan tanıyan tek tek dosyalar olarak tanımlayabilirsiniz. Aynı kaynak türlerini ve farklı değerleri sağlayan birden çok kaynak sözlüğü tanımlayarak, değiştirilebilir temalar da oluşturabilirsiniz. Uygulama düzeyindeki bu stilleri veya diğer kaynakları yeniden tanımlama, bir uygulamanın kaplama oluşturma için önerilen yaklaşımdır.

Stiller ve şablonlar dahil olmak üzere bir kaynak kümesini, uygulamalar arasında paylaşmak için bir XAML dosyası oluşturabilir ve bir <xref:System.Windows.ResourceDictionary> dosyanın başvurusunu içeren bir tanımlayabilirsiniz `shared.xaml` .

```xaml
<ResourceDictionary.MergedDictionaries>
  <ResourceDictionary Source="Shared.xaml" />
</ResourceDictionary.MergedDictionaries>
```

Bu, bir `shared.xaml` <xref:System.Windows.ResourceDictionary> uygulama içindeki denetimlerin tutarlı bir görünüme sahip olmasını sağlayan bir stil ve fırça kaynakları kümesi içeren öğesini tanımlayan, öğesinin paylaşımdır.

Daha fazla bilgi için bkz. [birleştirilmiş kaynak sözlükleri](../../framework/wpf/advanced/merged-resource-dictionaries.md).

Özel denetiminiz için bir tema oluşturuyorsanız, [Denetim yazma genel bakış](../../framework/wpf/controls/control-authoring-overview.md#defining-resources-at-the-theme-level)konusunun **Tema düzeyinde kaynakları tanımlama** bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [WPF İçinde URI'leri Paketleme](../../framework/wpf/app-development/pack-uris-in-wpf.md)
- [Nasıl yapılır: ControlTemplate ile Oluşturulan Öğeleri Bulma](../../framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)
- [DataTemplate tarafından oluşturulan öğeleri bulma](../../framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
