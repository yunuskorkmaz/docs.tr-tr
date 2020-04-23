---
title: Stiller ve şablonlar
description: .NET Core için Windows Presentation Foundation (WPF)'deki XAML kaynakları hakkında bilgi edinin. Stiller ve temalarla ilgili XAML kaynaklarının türlerini anlayın.
author: thraka
ms.author: adegeo
ms.date: 09/09/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: f845e739ec3cae502d1e4fd6631f987c5364a42e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071887"
---
# <a name="styles-and-templates-in-wpf"></a>WPF'deki stiller ve şablonlar

Windows Presentation Foundation (WPF) stili ve baştan çıkarıcı tasarımı, geliştiricilerin ve tasarımcıların görsel olarak zorlayıcı efektler ve ürünleri için tutarlı bir görünüm oluşturmasına izin veren bir dizi özellik anlamına gelir. Bir uygulamanın görünümünü özelleştirirken, uygulamalar içinde ve arasında görünümün bakımını ve paylaşımını sağlayan güçlü bir stil ve baştan çıkarıcı bir model istersiniz. WPF bu modeli sağlar.

WPF stil modelinin bir diğer özelliği de sunum ve mantığın ayrılmasıdır. Tasarımcılar, geliştiricilerin C# veya Visual Basic kullanarak programlama mantığı üzerinde çalıştıkları aynı zamanda yalnızca XAML kullanarak bir uygulamanın görünümü üzerinde çalışabilirler.

Bu genel bakış, uygulamanın stil ve cazip yönlerine odaklanır ve veri bağlayıcı kavramları tartışmaz. Veri bağlama hakkında bilgi için [bkz.](../data/data-binding-overview.md)

Stillerin ve şablonların yeniden kullanılmasını sağlayan kaynakları anlamak önemlidir. Kaynaklar hakkında daha fazla bilgi için [Bkz. XAML Kaynakları.](xaml-resources-define.md)

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sample"></a>Örnek

Bu genel bakışta sağlanan örnek kod, aşağıdaki resimde gösterilen basit bir [fotoğraf tarama uygulamasına](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) dayanmaktadır.

![StillistesiGörünümü](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

Bu basit fotoğraf örneği, görsel olarak zorlayıcı bir kullanıcı deneyimi oluşturmak için stil ve baştan çıkarma kullanır. Örnekiki <xref:System.Windows.Controls.TextBlock> öğe ve <xref:System.Windows.Controls.ListBox> görüntü listesine bağlı bir denetim vardır.

Tam örnek için, [Stil ve Templating Örnek Giriş](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)bakın.

## <a name="styles"></a>Stiller

Birden <xref:System.Windows.Style> çok öğeye özellik değerleri kümesi uygulamak için uygun bir yol olarak düşünebilirsiniz. Bir stil, <xref:System.Windows.FrameworkElement> bir öğeden türeyen <xref:System.Windows.FrameworkContentElement> veya bir <xref:System.Windows.Window> öğe <xref:System.Windows.Controls.Button>den türeyen herhangi bir öğe üzerinde kullanabilirsiniz.

Bir stili bildirmenin en yaygın yolu, `Resources` XAML dosyasındaki bölümdekaynak olarak dır. Stiller kaynak olduğundan, tüm kaynaklar için geçerli olan aynı kapsam kurallarına uyarlar. Basitçe söylemek gerekirse, bir stili beyan ettiğiniz yer stilin uygulanabileceği yeri etkiler. Örneğin, uygulama tanımı XAML dosyanızın kök öğesindeki stili bildirirseniz, stil uygulamanızın herhangi bir yerinde kullanılabilir.

Örneğin, aşağıdaki XAML kodu, biri otomatik `TextBlock`olarak tüm `TextBlock` öğelere uygulanan ve diğeri açıkça başvurulması gereken bir , iki stil bildirir.

[!code-xaml[SnippetDefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

Aşağıda, yukarıda kullanılan stillerin bir örneği verilmiştir.

[!code-xaml[SnippetTextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

![Stildeki metin blokları](./media/styles-and-templates-overview/stylingintro-textblocks.png)

Daha fazla bilgi için [bkz.](styles-templates-create-apply-style.md)

## <a name="controltemplates"></a>ControlTemplates

WPF'de, <xref:System.Windows.Controls.ControlTemplate> denetimin görünümü kontrol görünümünü tanımlar. Yeni <xref:System.Windows.Controls.ControlTemplate> bir denetim tanımlayıp denetime atayarak denetimin yapısını ve görünümünü değiştirebilirsiniz. Çoğu durumda, şablonlar size kendi özel denetimlerinizi yazmak zorunda kalmamanız için yeterli esneklik sağlar.

Her denetimin [Denetim.Şablon](xref:System.Windows.Controls.Control.Template) özelliğine atanmış varsayılan bir şablonu vardır. Şablon, denetimin görsel sunusunu denetimin yetenekleriyle bağlar. XAML'de bir şablon tanımladığınız için, herhangi bir kod yazmadan denetimin görünümünü değiştirebilirsiniz. Her şablon, <xref:System.Windows.Controls.Button>belirli bir denetim için tasarlanmıştır.

Genellikle bir XAML dosyasının `Resources` bölümünde kaynak olarak bir şablon bildirirsiniz. Tüm kaynaklarda olduğu gibi kapsam landırma kuralları da geçerlidir.

Denetim şablonları bir stilden çok daha fazla ilgilidir. Bunun nedeni, denetim şablonunun tüm denetimin görsel görünümünü yeniden yazması, bir stilise yalnızca varolan denetime özellik değişiklikleri uygular. Ancak, [Denetim.Şablon](xref:System.Windows.Controls.Control.Template) özelliğini ayarlayarak denetim şablonu uygulandığından, şablonu tanımlamak veya ayarlamak için bir stil kullanabilirsiniz.

Tasarımcılar genellikle varolan bir şablonun bir kopyasını oluşturmanıza ve değiştirmenize izin verir. Örneğin, Visual Studio WPF tasarımcısında `CheckBox` bir denetim seçin ve ardından sağ tıklatın ve **şablonu edit'i** > seçin**Kopya oluştur.** Bu *komut, şablon tanımlayan bir stil*oluşturur.

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

Şablonun bir kopyasını düzenlemek, şablonların nasıl çalıştığını öğrenmenin harika bir yoludur. Yeni bir boş şablon oluşturmak yerine, bir kopyasını ve görsel sununun birkaç yönünü değiştirmek daha kolaydır.

Örneğin, bkz. [denetim için şablon oluştur.](../themes/how-to-create-apply-template.md)

### <a name="templatebinding"></a>Templatebinding

Önceki bölümde tanımlanan şablon kaynağının Şablon Bağlayıcı [Biçimlendirme Uzantısı'nı](../../framework/wpf/advanced/templatebinding-markup-extension.md)kullandığını fark etmiş olabilirsiniz. A, `TemplateBinding` şablon senaryoları için en iyi duruma getirilmiş bir `{Binding RelativeSource={RelativeSource TemplatedParent}}`bağlama biçimidir ve bu da . `TemplateBinding`denetim özelliklerine şablonun bölümlerini bağlamak için yararlıdır. Örneğin, her denetimin <xref:System.Windows.Controls.Control.BorderThickness> bir özelliği vardır. Şablondaki `TemplateBinding` hangi öğenin bu denetim ayarından etkilendiğini yönetmek için a kullanın.

### <a name="contentcontrol-and-itemscontrol"></a>İçerikKontrol ve ÖğelerKontrol

A' <xref:System.Windows.Controls.ContentPresenter> da <xref:System.Windows.Controls.ControlTemplate> beyan <xref:System.Windows.Controls.ContentControl>edilirse, <xref:System.Windows.Controls.ContentPresenter> otomatik olarak ve <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <xref:System.Windows.Controls.ContentControl.Content%2A> özelliklere bağlanır. Aynı şekilde, <xref:System.Windows.Controls.ItemsPresenter> bir otomatik <xref:System.Windows.Controls.ControlTemplate> olarak <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> ve <xref:System.Windows.Controls.ItemsControl.Items%2A> özellikleri bağlanır bir içinde bir.

## <a name="datatemplates"></a>Veri Şablonları

Bu örnek uygulamada, fotoğraf <xref:System.Windows.Controls.ListBox> listesine bağlı bir denetim vardır.

[!code-xaml[ListBox](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window3.xaml#SnippetListBox)]

Bu <xref:System.Windows.Controls.ListBox> şu anda aşağıdaki gibi görünüyor.

![Şablonu uygulamadan önce ListBox](./media/styles-and-templates-overview/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")

Denetimlerin çoğunda bir tür içerik vardır ve bu içerik genellikle bağlandığınız verilerden gelir. Bu örnekte, veriler fotoğraf listesidir. WPF'de, verilerin <xref:System.Windows.DataTemplate> görsel temsilini tanımlamak için a kullanırsınız. Temel olarak, bir <xref:System.Windows.DataTemplate> içine ne koymak veri render uygulamasında neye benzediğini belirler.

Örnek uygulamamızda, her `Photo` özel `Source` nesne, görüntünün dosya yolunu belirten bir tür dize özelliğine sahiptir. Şu anda, fotoğraf nesneleri dosya yolları olarak görünür.

[!code-csharp[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Photo.cs#PhotoClass)]
[!code-vb[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/Photo.vb#PhotoClass)]

Fotoğrafların görüntü olarak görünmesi için <xref:System.Windows.DataTemplate> bir kaynak oluşturursunuz.

[!code-xaml[DataTemplate](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window4.xaml#SnippetDataTemplate)]

Özelliğin <xref:System.Windows.DataTemplate.DataType%2A> <xref:System.Windows.Style.TargetType%2A> özelliğine benzer olduğuna dikkat <xref:System.Windows.Style>edin. Kaynaklar <xref:System.Windows.DataTemplate> bölümündeyseniz, <xref:System.Windows.DataTemplate.DataType%2A> özelliği bir türe belirtdiğinizde ve bir `x:Key`özelliği atladiğinizde, bu tür görüntülendiğinde <xref:System.Windows.DataTemplate> uygulanır. Her zaman bir <xref:System.Windows.DataTemplate> `x:Key` ile atama katmak ve daha `StaticResource` sonra <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özellik veya <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> özellik gibi türleri almak özellikleri için bir olarak ayarlamak için seçeneğiniz vardır.

Esasen, <xref:System.Windows.DataTemplate> yukarıdaki örnekte bir `Photo` nesne olduğunda, bir <xref:System.Windows.Controls.Image> <xref:System.Windows.Controls.Border>. Bununla, <xref:System.Windows.DataTemplate>uygulamamız şimdi bu gibi görünüyor.

![Fotoğraf görüntüsü](./media/styles-and-templates-overview/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")

Veri baştan çıkarıcı model diğer özellikler sağlar. Örneğin, a <xref:System.Windows.Controls.HeaderedItemsControl> veya a <xref:System.Windows.Controls.Menu> gibi bir tür kullanarak diğer koleksiyonları içeren <xref:System.Windows.Controls.TreeView>toplama verilerini <xref:System.Windows.HierarchicalDataTemplate>görüntülerseniz, . Başka bir veri cazip <xref:System.Windows.Controls.DataTemplateSelector>özelliği , özel mantığa dayalı kullanmak için bir <xref:System.Windows.DataTemplate> seçmenize olanak sağlar. Daha fazla bilgi için, farklı veri cazip özellikleri hakkında daha ayrıntılı bir tartışma sağlayan [Veri Templating Genel Bakış'a](../../framework/wpf/data/data-templating-overview.md)bakın.

## <a name="triggers"></a>Tetikleyiciler

Tetikleyici, özellik değeri değiştiğinde veya bir olay yükseltildiğinde, animasyon gibi özellikleri ayarlar veya eylemleri başlatır. <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>ve <xref:System.Windows.DataTemplate> tüm `Triggers` tetikleyiciler kümesi içerebilir bir özelliği var. Tetikleyicilerin çeşitli türleri vardır.

### <a name="propertytriggers"></a>ÖzellikTetikleyiciler

Özellik <xref:System.Windows.Trigger> değerlerini belirleyen veya bir özelliğin değerini temel alan eylemleri başlatan bir özellik tetikleyicisi olarak adlandırılır.

Özellik tetikleyicilerinin nasıl kullanılacağını göstermek için, seçilmedikçe her biri <xref:System.Windows.Controls.ListBoxItem> kısmen saydam hale getirebilirsiniz. Aşağıdaki stil a <xref:System.Windows.UIElement.Opacity%2A> <xref:System.Windows.Controls.ListBoxItem> değerini `0.5`ayarlar. <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> Özellik `true`, ancak, <xref:System.Windows.UIElement.Opacity%2A> `1.0`ayarlanır.

[!code-xaml[PropertyTrigger](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window5.xaml#SnippetPropertyTrigger)]

Bu örnek, <xref:System.Windows.Trigger> bir özellik değeri ayarlamak için <xref:System.Windows.Trigger> a kullanır, ancak sınıfın da bir tetikleyici eylemleri gerçekleştirmek için etkinleştirmek <xref:System.Windows.TriggerBase.EnterActions%2A> ve <xref:System.Windows.TriggerBase.ExitActions%2A> özellikleri olduğunu unutmayın.

Bu <xref:System.Windows.FrameworkElement.MaxHeight%2A> özelliği ayarlanır <xref:System.Windows.Controls.ListBoxItem> dikkat `75`edin. Aşağıdaki resimde, üçüncü öğe seçili öğedir.

![StillistesiGörünümü](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

### <a name="eventtriggers-and-storyboards"></a>EventTriggers ve Storyboards

Tetikleyici başka bir <xref:System.Windows.EventTrigger>tür , bir olayın oluşumuna dayalı eylemler kümesi başlar. <xref:System.Windows.EventTrigger> Örneğin, aşağıdaki nesneler, fare işaretçisi <xref:System.Windows.Controls.ListBoxItem>girdiğinde <xref:System.Windows.FrameworkElement.MaxHeight%2A> , özelliğin ikinci bir `90` `0.2` döneme ait bir değere animasyon verdiğini belirtir. Fare öğeden uzaklaştığında, özellik `1` saniyelik bir süre içinde özgün değere geri döner. Animasyon için bir <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> değer belirtmenin <xref:System.Windows.ContentElement.MouseLeave> nasıl gerekli olmadığını unutmayın. Bunun nedeni, animasyonun özgün değeri takip edebilmesidir.

[!code-xaml[StyleEventTriggers](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window6.xaml#SnippetStyleEventTriggers)]

Daha fazla bilgi için [Storyboards'a genel bakış](../../framework/wpf/graphics-multimedia/storyboards-overview.md)bilgisine bakın.

Aşağıdaki resimde, fare üçüncü öğeyi işaret ediyor.

![Stil örnek ekran görüntüsü](./media/styles-and-templates-overview/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTriggers, DataTriggers ve MultiDataTriggers

Buna ek <xref:System.Windows.Trigger> <xref:System.Windows.EventTrigger>olarak ve , tetikleyiciler diğer türleri vardır. <xref:System.Windows.MultiTrigger>özellik değerlerini birden çok koşula göre ayarlamanızı sağlar. Kullandığınız <xref:System.Windows.DataTrigger> ve <xref:System.Windows.MultiDataTrigger> durumunuzun özelliği verilere bağlı olduğunda.

## <a name="visual-states"></a>Görsel Durumlar

Denetimler her zaman belirli bir **durumdadır.** Örneğin, fare bir denetimin yüzeyi üzerinde hareket ettiğinde, denetim in ortak `MouseOver`bir durumda olduğu kabul edilir. Belirli bir durum olmadan bir denetim ortak `Normal` durumda olarak kabul edilir. Devletler gruplara ayrılır ve daha önce bahsedilen durumlar devlet `CommonStates`grubunun bir parçasıdır. Çoğu denetimin iki `CommonStates` durum `FocusStates`grubu var: ve . Denetime uygulanan her durum grubundan, denetim her grubun bir durumundadır, örneğin. `CommonStates.MouseOver` `FocusStates.Unfocused` Ancak, denetim gibi aynı grup içinde iki farklı durumda `CommonStates.Normal` olamaz. `CommonStates.Disabled` Burada, çoğu denetimin tanıdığı ve kullandığı durumlar tablosu ve resuletmek tir.

| VisualState Adı | VisualStateGroup Adı | Açıklama |
| ---------------- | --------------------- | ----------- |
| Normal           | Commonstates          | Varsayılan durum. |
| Mouseover        | Commonstates          | Fare işaretçisi denetimin üzerine konumlandırılır. |
| Pressed          | Commonstates          | Kontrol basılı. |
| Devre dışı         | Commonstates          | Denetim devre dışı. |
| Odaklı          | Odak Devletler           | Kontrol odak noktası. |
| Odaklanmamış        | Odak Devletler           | Denetimin odak noktası yok. |

Denetim şablonunun <xref:System.Windows.VisualStateManager?displayProperty=fullName> kök öğesi üzerinde bir öğe tanımlayarak, denetim belirli bir duruma girdiğinde animasyonları tetikleyebilirsiniz. Hangi `VisualStateManager` kombinasyonları <xref:System.Windows.VisualStateGroup> ve <xref:System.Windows.VisualState> izlemek için bildirir. Denetim izlenen bir duruma girdiğinde, animasyon tarafından `VisaulStateManager` tanımlanan başlatılır.

Örneğin, aşağıdaki XAML kodu adlı `CommonStates.MouseOver` `backgroundElement`öğenin dolgu rengini canlandırmak için durumu izler. Denetim `CommonStates.Normal` duruma döndüğünde, adlı `backgroundElement` öğenin dolgu rengi geri yüklenir.

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

Storyboards hakkında daha fazla bilgi için [Storyboards Genel Bakış'a](../../framework/wpf/graphics-multimedia/storyboards-overview.md)bakın.

## <a name="shared-resources-and-themes"></a>Paylaşılan kaynaklar ve temalar

Tipik bir WPF uygulaması, uygulama boyunca uygulanan birden çok UI kaynağına sahip olabilir. Toplu olarak, bu kaynak kümesi uygulamanın teması olarak kabul edilebilir. WPF, <xref:System.Windows.ResourceDictionary> sınıf olarak kapsüllenmiş bir kaynak sözlüğü kullanarak kullanıcı arabirimi kaynaklarını tema olarak paketleme desteği sağlar.

WPF temaları, WPF'nin herhangi bir öğenin görsellerini özelleştirmek için ortaya çıkardığı stil ve baştan çıkarıcı mekanizma kullanılarak tanımlanır.

WPF tema kaynakları katıştırılmış kaynak sözlüklerinde depolanır. Bu kaynak sözlükleri imzalı bir derlemenin içine katıştırılmış olmalıdır ve kodun kendisiyle aynı derlemeye veya yan yana bir derlemeye katıştırılabilir. WPF denetimleri içeren derleme presentationFramework.dll için tema kaynakları yan yana bir dizi derlemede dir.

Tema, bir öğenin stilini ararken aranacak en son yer olur. Genellikle, arama, uygun bir kaynak arayan öğe ağacında yürüyerek başlar, ardından uygulama kaynağı koleksiyonuna bakar ve son olarak sistemi sorgular. Bu, uygulama geliştiricilere temaya ulaşmadan önce ağaç veya uygulama düzeyindeki herhangi bir nesnenin stilini yeniden tanımlama şansı verir.

Kaynak sözlüklerini, bir temayı birden çok uygulamada yeniden kullanmanızı sağlayan tek tek dosyalar olarak tanımlayabilirsiniz. Ayrıca, aynı kaynak türlerini sağlayan ancak farklı değerlere sahip birden çok kaynak sözlükleri tanımlayarak değiştirilebilir temalar da oluşturabilirsiniz. Bu stilleri veya diğer kaynakları uygulama düzeyinde yeniden tanımlamak, bir uygulamayı yüzdürme için önerilen yaklaşımdır.

Uygulamalar arasında stiller ve şablonlar da dahil olmak üzere bir kaynak kümesini paylaşmak <xref:System.Windows.ResourceDictionary> için bir `shared.xaml` XAML dosyası oluşturabilir ve dosyaya başvuru içeren bir dosya tanımlayabilirsiniz.

```xaml
<ResourceDictionary.MergedDictionaries>
  <ResourceDictionary Source="Shared.xaml" />
</ResourceDictionary.MergedDictionaries>
```

Bir uygulamadaki `shared.xaml`denetimlerin tutarlı bir <xref:System.Windows.ResourceDictionary> görünüme sahip olmasını sağlayan, bir stil ve fırça kaynakları kümesiiçeren bir uygulamanın paylaşımıdır.

Daha fazla bilgi [için, Birleştirme kaynak sözlüklerine](../../framework/wpf/advanced/merged-resource-dictionaries.md)bakın.

Özel denetiminiz için bir tema oluşturuyorsanız, [Denetim yazma genel bakışının](../../framework/wpf/controls/control-authoring-overview.md#defining-resources-at-the-theme-level) **tema düzeyi bölümündeki Tanımlayıcı kaynakları** görün.

## <a name="see-also"></a>Ayrıca bkz.

- [WPF İçinde URI'leri Paketleme](../../framework/wpf/app-development/pack-uris-in-wpf.md)
- [Nasıl yapılır: ControlTemplate ile Oluşturulan Öğeleri Bulma](../../framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)
- [DataTemplate tarafından oluşturulan öğeleri bulma](../../framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
