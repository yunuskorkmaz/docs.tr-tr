---
title: Stiller ve şablonlar
description: .NET Core için Windows Presentation Foundation (WPF) içindeki XAML Kaynakları hakkında bilgi edinin. Stiller ve Temalar ile ilgili XAML kaynaklarının türlerini anlayın.
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
# <a name="styles-and-templates-in-wpf"></a>WPF 'deki stiller ve şablonlar

Windows Presentation Foundation (WPF) stili ve şablon oluşturma, geliştiricilerin ve tasarımcıların görsel açıdan etkileyici efektler ve ürün için tutarlı bir görünüm oluşturmalarına olanak tanıyan bir özellik paketine başvurur. Bir uygulamanın görünümünü özelleştirirken, uygulamalar içinde ve arasında görünüm ve paylaşım imkanı sağlayan güçlü bir stil ve şablon oluşturma modeli istiyorsunuz. WPF bu modeli sağlar.

WPF stil modelinin başka bir özelliği de sununun ve mantığın ayrımı olur. Tasarımcılar, geliştiricilerin C# veya Visual Basic kullanarak programlama mantığı üzerinde çalıştığı aynı anda yalnızca XAML kullanarak bir uygulamanın görünümü üzerinde çalışabilir.

Bu genel bakış, uygulamanın stil ve şablon oluşturma yönlerine odaklanır ve veri bağlama kavramlarını ele almaz. Veri bağlama hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md).

Stillerin ve şablonların yeniden kullanılmasını sağlayan kaynakları anlamanız önemlidir. Kaynaklar hakkında daha fazla bilgi için bkz. [xaml kaynakları](xaml-resources-define.md).

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sample"></a>Örnek

Bu genel bakışta verilen örnek kod, aşağıdaki çizimde gösterilen [basit bir fotoğraf tarama uygulamasına](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) dayalıdır.

![Stilli ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

Bu basit fotoğraf örneği, görsel açıdan etkileyici bir kullanıcı deneyimi oluşturmak için stil ve şablon oluşturma kullanır. Örnekte, iki <xref:System.Windows.Controls.TextBlock> öğe ve bir görüntü <xref:System.Windows.Controls.ListBox> listesine bağlanan bir denetim vardır.

Tüm örnek için bkz. [Stil ve şablon oluşturma örneğine giriş](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).

## <a name="styles"></a>Stiller

Bir özellik değerleri kümesini birden <xref:System.Windows.Style> çok öğeye uygulamak için kullanışlı bir yol olarak düşünebilirsiniz. Ya <xref:System.Windows.FrameworkElement> da ' dan <xref:System.Windows.FrameworkContentElement> türetilen herhangi bir <xref:System.Windows.Window> öğe için bir stil kullanabilirsiniz. <xref:System.Windows.Controls.Button>

Bir stil belirtmenin en yaygın yolu, bir XAML dosyasındaki `Resources` bölümünde kaynak olarak kullanılır. Stiller kaynaklar olduğundan, tüm kaynaklar için uygulanan aynı kapsam kurallarına uyar. Basitçe, stilin uygulanabileceğini bir stil bildirdiğiniz yere koyun. Örneğin, stili uygulama tanımı XAML dosyanızın kök öğesinde bildirirseniz, bu stil uygulamanızda herhangi bir yerde kullanılabilir.

Örneğin, aşağıdaki XAML kodu bir `TextBlock`için iki stil bildirir, bir otomatik olarak tüm `TextBlock` öğelere uygulanır ve açıkça başvurulması gereken başka bir tane.

[!code-xaml[SnippetDefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

Yukarıda belirtilen stillerin bir örneği aşağıda verilmiştir.

[!code-xaml[SnippetTextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

![Stilli metinblokları](./media/styles-and-templates-overview/stylingintro-textblocks.png)

Daha fazla bilgi için bkz. [Denetim için stil oluşturma](styles-templates-create-apply-style.md).

## <a name="controltemplates"></a>ControlTemplates

WPF <xref:System.Windows.Controls.ControlTemplate> 'de bir denetim, denetimin görünümünü tanımlar. Bir denetimin yapısını ve görünümünü, yeni <xref:System.Windows.Controls.ControlTemplate> bir tanımlayarak bir denetime atayarak değiştirebilirsiniz. Birçok durumda, şablonlar size, kendi özel denetimlerinizi yazmak zorunda olmadığınız için yeterli esneklik sunar.

Her denetimin [Control. Template](xref:System.Windows.Controls.Control.Template) özelliğine atanmış varsayılan bir şablonu vardır. Şablon, denetimin özelliklerine sahip olan denetimin görsel sunumunu bağlar. XAML 'de bir şablon tanımladığınız için, herhangi bir kod yazmadan denetimin görünümünü değiştirebilirsiniz. Her şablon, gibi belirli bir denetim için tasarlanmıştır <xref:System.Windows.Controls.Button>.

Genellikle bir şablonu bir XAML dosyasının `Resources` bölümünde kaynak olarak bildirirsiniz. Tüm kaynaklarda olduğu gibi, kapsam kuralları da geçerlidir.

Denetim şablonları, bir stille daha fazla yer kaplar. Bunun nedeni denetim şablonunun tüm denetimin görsel görünümünü yeniden, ancak bir stil ise yalnızca var olan denetimdeki özellik değişikliklerini uygular. Ancak, denetimin şablonu [Control. Template](xref:System.Windows.Controls.Control.Template) özelliği ayarlanarak uygulandığından, bir şablon tanımlamak veya ayarlamak için bir stil kullanabilirsiniz.

Tasarımcılar genellikle var olan bir şablonun bir kopyasını oluşturmanıza ve bunu değiştirmenize izin verir. Örneğin, Visual Studio WPF `CheckBox` tasarımcısında bir denetim seçin ve sağ tıklayın ve **şablonu** > Düzenle ' yi seçin.**Create a copy** Bu komut *, bir şablonu tanımlayan bir stil*oluşturur.

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

Önceki bölümde tanımlanan şablon kaynağının [TemplateBinding biçimlendirme uzantısını](../../framework/wpf/advanced/templatebinding-markup-extension.md)kullandığını fark etmiş olabilirsiniz. `TemplateBinding` , İle `{Binding RelativeSource={RelativeSource TemplatedParent}}`oluşturulmuş bir bağlamaya benzer şekilde, şablon senaryoları için bir bağlamanın en iyi duruma getirilmiş bir biçimidir. `TemplateBinding`, şablonun parçalarını denetimin özelliklerine bağlamak için yararlıdır. Örneğin, her denetimin bir <xref:System.Windows.Controls.Control.BorderThickness> özelliği vardır. Şablondaki hangi `TemplateBinding` öğenin bu denetim ayarından etkilendiğini yönetmek için kullanın.

### <a name="contentcontrol-and-itemscontrol"></a>ContentControl ve ItemsControl

<xref:System.Windows.Controls.ContentPresenter> <xref:System.Windows.Controls.ControlTemplate> , Bir <xref:System.Windows.Controls.ContentControl> <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <xref:System.Windows.Controls.ContentControl.Content%2A> içinde bildiriminde bildirilirse, otomatik olarak ve özelliklerine bağlanır. <xref:System.Windows.Controls.ContentPresenter> Benzer şekilde, <xref:System.Windows.Controls.ItemsPresenter> içinde <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ItemsControl> olan bir, <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> ve <xref:System.Windows.Controls.ItemsControl.Items%2A> özelliklerine otomatik olarak bağlanır.

## <a name="datatemplates"></a>Veri şablonları

Bu örnek uygulamada, bir fotoğraf listesine bağlanan <xref:System.Windows.Controls.ListBox> bir denetim vardır.

[!code-xaml[ListBox](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window3.xaml#SnippetListBox)]

Bu <xref:System.Windows.Controls.ListBox> Şu anda aşağıdaki gibi görünüyor.

![Şablonu uygulamadan önce ListBox](./media/styles-and-templates-overview/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")

Çoğu denetim bazı içerik türlerine sahiptir ve içerik genellikle bağladığınız verilerden gelir. Bu örnekte, veriler fotoğraflar listesidir. WPF 'de, verilerin görsel temsilini <xref:System.Windows.DataTemplate> tanımlamak için kullanırsınız. Temel olarak, ' a <xref:System.Windows.DataTemplate> yerleştirdiğiniz özellikler, işlenen uygulamada verilerin ne şekilde göründüğünü belirler.

Örnek uygulamamızda her özel `Photo` nesne, görüntünün dosya yolunu `Source` belirten String türünde bir özelliğe sahiptir. Şu anda, fotoğraf nesneleri dosya yolları olarak görünür.

[!code-csharp[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Photo.cs#PhotoClass)]
[!code-vb[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/Photo.vb#PhotoClass)]

Fotoğrafların görüntü olarak görünmesi için kaynak olarak bir <xref:System.Windows.DataTemplate> oluşturun.

[!code-xaml[DataTemplate](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window4.xaml#SnippetDataTemplate)]

<xref:System.Windows.DataTemplate.DataType%2A> Özelliğinin <xref:System.Windows.Style.TargetType%2A> özelliğine benzediğine dikkat edin <xref:System.Windows.Style>. Kaynaklar bölümünde <xref:System.Windows.DataTemplate> ise, bir tür için <xref:System.Windows.DataTemplate.DataType%2A> özelliği belirttiğinizde ve bir `x:Key`öğesini <xref:System.Windows.DataTemplate> atarsanız, bu tür her göründüğünde uygulanır. Her <xref:System.Windows.DataTemplate> zaman öğesini ile atama `x:Key` ve `StaticResource` <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özellik veya <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> özellik gibi türleri alan özellikler için bir olarak ayarlama seçeneğiniz vardır.

Temel olarak, <xref:System.Windows.DataTemplate> yukarıdaki örnekteki bir `Photo` nesne olduğunda, bir, <xref:System.Windows.Controls.Image> içinde olarak görünmesi gerektiğini tanımlar. <xref:System.Windows.Controls.Border> Bununla birlikte <xref:System.Windows.DataTemplate>, uygulamamız artık şuna benzer.

![Fotoğraf resmi](./media/styles-and-templates-overview/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")

Veri şablonu oluşturma modeli, diğer özellikleri sağlar. <xref:System.Windows.Controls.HeaderedItemsControl> Örneğin, <xref:System.Windows.Controls.Menu> veya <xref:System.Windows.Controls.TreeView>gibi bir tür kullanarak diğer koleksiyonları içeren koleksiyon verileri görüntülüyorsanız, <xref:System.Windows.HierarchicalDataTemplate>. Başka bir veri şablonu oluşturma özelliği <xref:System.Windows.Controls.DataTemplateSelector>, özel mantığa <xref:System.Windows.DataTemplate> göre kullanmak üzere seçeneğini seçmenize olanak sağlar. Daha fazla bilgi için, farklı veri şablonu oluşturma özellikleri hakkında daha ayrıntılı bir tartışma sağlayan [veri şablonu oluşturmaya genel bakış](../../framework/wpf/data/data-templating-overview.md)bölümüne bakın.

## <a name="triggers"></a>Tetikleyiciler

Bir tetikleyici, özellik değeri değiştiğinde veya bir olay ortaya çıktığında animasyon gibi eylemleri ayarlar veya başlatır. <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, ve <xref:System.Windows.DataTemplate> hepsi bir tetikleyici `Triggers` kümesi içerebilen bir özelliğine sahiptir. Birkaç tetikleyici türü vardır.

### <a name="propertytriggers"></a>PropertyTriggers

Özellik <xref:System.Windows.Trigger> değerlerini ayarlayan veya bir özelliğin değerine göre eylemleri Başlatan bir özellik tetikleyicisi olarak adlandırılır.

Özellik tetiklerinin nasıl kullanılacağını göstermek için, seçili değilse her <xref:System.Windows.Controls.ListBoxItem> bir kısmen saydam yapabilirsiniz. Aşağıdaki stil, a <xref:System.Windows.UIElement.Opacity%2A> <xref:System.Windows.Controls.ListBoxItem> değerini olarak `0.5`ayarlar. Ancak <xref:System.Windows.UIElement.Opacity%2A> , <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> özelliği `true`olduğunda, olarak ayarlanır `1.0`.

[!code-xaml[PropertyTrigger](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window5.xaml#SnippetPropertyTrigger)]

Bu örnek, bir <xref:System.Windows.Trigger> Özellik değeri ayarlamak için bir kullanır, ancak <xref:System.Windows.Trigger> sınıfın, <xref:System.Windows.TriggerBase.EnterActions%2A> bir tetikleyicinin eylemleri gerçekleştirmesini sağlayan <xref:System.Windows.TriggerBase.ExitActions%2A> ve özellikleri de olduğunu unutmayın.

Öğesinin <xref:System.Windows.FrameworkElement.MaxHeight%2A> <xref:System.Windows.Controls.ListBoxItem> özelliğinin olarak `75`ayarlandığını unutmayın. Aşağıdaki çizimde, üçüncü öğe seçili öğedir.

![Stilli ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

### <a name="eventtriggers-and-storyboards"></a>EventTriggers ve film şeritleri

Bir olay oluşumuna göre bir dizi <xref:System.Windows.EventTrigger>eylem başlatan, başka bir tetikleyici türü. <xref:System.Windows.EventTrigger> Örneğin, aşağıdaki nesneler fare işaretçisi <xref:System.Windows.Controls.ListBoxItem> <xref:System.Windows.FrameworkElement.MaxHeight%2A> `90` üzerine girdiğinde, özelliği ikinci bir `0.2` dönemdeki bir değere hareketlendirir. Fare öğeden uzaklaştığında, özelliği `1` ikinci bir süre içinde orijinal değere döner. <xref:System.Windows.ContentElement.MouseLeave> Animasyon için bir <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> değer belirtmek için nasıl gerekli değildir Not. Bunun nedeni, animasyonun özgün değeri takip edebilmesini sağlar.

[!code-xaml[StyleEventTriggers](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window6.xaml#SnippetStyleEventTriggers)]

Daha fazla bilgi için görsel taslaklara [genel bakış](../../framework/wpf/graphics-multimedia/storyboards-overview.md)bölümüne bakın.

Aşağıdaki çizimde, fare üçüncü öğeyi işaret ediyor.

![Stil örnek ekran görüntüsü](./media/styles-and-templates-overview/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>Çoklu Tetikleyiciler, veri Tetikleyicileri ve MultiDataTriggers

Ve <xref:System.Windows.EventTrigger>' ye <xref:System.Windows.Trigger> ek olarak, başka tetikleyici türleri de vardır. <xref:System.Windows.MultiTrigger>özellik değerlerini birden çok koşula göre ayarlamanıza olanak sağlar. Koşulunuz <xref:System.Windows.DataTrigger> özelliği <xref:System.Windows.MultiDataTrigger> veri ile bağlantılı olduğunda ve kullanın.

## <a name="visual-states"></a>Görsel durumlar

Denetimler her zaman belirli bir **durumda**. Örneğin, fare bir denetimin yüzeyi üzerinde dolaştığında, denetim ortak bir durumunda olduğu kabul edilir `MouseOver`. Belirli bir durumu olmayan bir denetim, ortak `Normal` durumda olduğu kabul edilir. Durumlar gruplar halinde bozulur ve yukarıda bahsedilen durumlar durum grubunun `CommonStates`bir parçasıdır. Çoğu denetim iki durum grubuna sahiptir: `CommonStates` ve `FocusStates`. Bir denetime uygulanan her bir durum grubunda, bir denetim her bir grubun `CommonStates.MouseOver` ve `FocusStates.Unfocused`gibi her zaman bir durumdadır. Ancak, bir denetim aynı grup içindeki `CommonStates.Normal` ve `CommonStates.Disabled`gibi iki farklı durumda olamaz. Denetimlerin çoğu tarafından tanınmasına ve kullanımına yönelik bir eyalet tablosu aşağıda verilmiştir.

| VisualState adı | VisualStateGroup adı | Açıklama |
| ---------------- | --------------------- | ----------- |
| Normal           | Ortak durumlar          | Varsayılan durum. |
| Gelme olayından        | Ortak durumlar          | Fare işaretçisi denetimin üzerine yerleştirilir. |
| Pressed          | Ortak durumlar          | Denetime basıldığında. |
| Devre dışı         | Ortak durumlar          | Denetim devre dışı bırakıldı. |
| Odaklı          | Odaklardaki durumlar           | Denetim odağa sahiptir. |
| Odaklanmadan gözetle        | Odaklardaki durumlar           | Denetimin odağı yok. |

Bir denetim şablonunun <xref:System.Windows.VisualStateManager?displayProperty=fullName> kök öğesinde bir tanımlayarak, bir denetim belirli bir duruma girdiğinde animasyonları tetikleyebilirsiniz. , `VisualStateManager` Hangi birleşimlerinin <xref:System.Windows.VisualStateGroup> ve <xref:System.Windows.VisualState> izlenecek olduğunu bildirir. Denetim bir izlenen duruma girdiğinde, tarafından `VisaulStateManager` tanımlanan animasyon başlatılır.

Örneğin, aşağıdaki XAML kodu, adlı `CommonStates.MouseOver` `backgroundElement`öğenin Fill rengine animasyon eklemek için durumu izler. Denetim `CommonStates.Normal` duruma döndüğünde adlı `backgroundElement` öğesinin Fill Color geri yüklenir.

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

Tipik bir WPF uygulamasında, uygulamanın tamamında uygulanan birden çok UI kaynağı olabilir. Toplu olarak, bu kaynak kümesi uygulama için tema olarak kabul edilebilir. WPF, <xref:System.Windows.ResourceDictionary> sınıf olarak Kapsüllenen bir kaynak sözlüğü kullanarak, Kullanıcı arabirimi kaynaklarını bir tema olarak paketleme desteği sağlar.

WPF temaları, WPF 'nin herhangi bir öğenin görsellerini özelleştirmek için sunduğu stil oluşturma ve şablon oluşturma mekanizması kullanılarak tanımlanır.

WPF teması kaynakları, gömülü kaynak sözlüklerinde depolanır. Bu kaynak sözlüklerinin imzalı bir derleme içine katıştırılması ve kodun kendisi ya da yan yana bütünleştirilmiş kodda aynı derlemeye katıştırılması gerekir. PresentationFramework. dll için WPF denetimleri içeren derleme, tema kaynakları ise yan yana derlemelerin bir serisinde yer almaktadır.

Tema, bir öğenin stilini ararken bakacağız son yer olur. Genellikle arama, uygun bir kaynak için arama öğesi ağacının ardından başlatılır, ardından uygulama kaynak koleksiyonuna bakar ve son olarak sistemi sorgular. Bu, uygulama geliştiricilere, temaya ulaşmadan önce ağaç veya uygulama düzeyindeki herhangi bir nesnenin stilini yeniden tanımlamayı sağlar.

Kaynak sözlüklerini birden çok uygulama genelinde bir temayı yeniden kullanmanıza imkan tanıyan tek tek dosyalar olarak tanımlayabilirsiniz. Aynı kaynak türlerini ve farklı değerleri sağlayan birden çok kaynak sözlüğü tanımlayarak, değiştirilebilir temalar da oluşturabilirsiniz. Uygulama düzeyindeki bu stilleri veya diğer kaynakları yeniden tanımlama, bir uygulamanın kaplama oluşturma için önerilen yaklaşımdır.

Stiller ve şablonlar dahil olmak üzere bir kaynak kümesini, uygulamalar arasında paylaşmak için bir XAML dosyası oluşturabilir ve bir <xref:System.Windows.ResourceDictionary> `shared.xaml` dosyanın başvurusunu içeren bir tanımlayabilirsiniz.

```xaml
<ResourceDictionary.MergedDictionaries>
  <ResourceDictionary Source="Shared.xaml" />
</ResourceDictionary.MergedDictionaries>
```

Bu, bir uygulama içindeki `shared.xaml`denetimlerin tutarlı bir görünüme sahip <xref:System.Windows.ResourceDictionary> olmasını sağlayan bir stil ve fırça kaynakları kümesi içeren öğesini tanımlayan, öğesinin paylaşımdır.

Daha fazla bilgi için bkz. [birleştirilmiş kaynak sözlükleri](../../framework/wpf/advanced/merged-resource-dictionaries.md).

Özel denetiminiz için bir tema oluşturuyorsanız, [Denetim yazma genel bakış](../../framework/wpf/controls/control-authoring-overview.md#defining-resources-at-the-theme-level)konusunun **Tema düzeyinde kaynakları tanımlama** bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [WPF İçinde URI'leri Paketleme](../../framework/wpf/app-development/pack-uris-in-wpf.md)
- [Nasıl yapılır: ControlTemplate ile Oluşturulan Öğeleri Bulma](../../framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)
- [DataTemplate tarafından oluşturulan öğeleri bulma](../../framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
