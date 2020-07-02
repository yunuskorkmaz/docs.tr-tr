---
title: WPF'ye Giriş
titleSuffix: ''
description: Windows 'da görsel açıdan etkileyici kullanıcı deneyimleri oluşturun. Windows Presentation Foundation (WPF) temel yeteneklerini ve kavramlarını bulun.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
dev_langs:
- csharp
- vb
ms.openlocfilehash: 7a79174f5f3aebe90190db45566b37bd5e9fbe3f
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853571"
---
# <a name="wpf-overview"></a>WPF’ye genel bakış

Windows Presentation Foundation (WPF), görsel açıdan etkileyici kullanıcı deneyimleri sayesinde Windows için masaüstü istemci uygulamaları oluşturmanıza olanak tanır.

![Contoso sağlık Kullanıcı arabirimi örneği](media/introduction-to-wpf/wpfintrofigure24.png)

WPF 'nin çekirdeği, modern grafik donanımının avantajlarından yararlanmak için oluşturulmuş, çözünürlükten bağımsız ve vektör tabanlı bir işleme altyapısıdır. WPF, Extensible Application Markup Language (XAML), denetimler, veri bağlama, düzen, 2B ve 3B grafikler, animasyon, stiller, şablonlar, belgeler, medya, metin ve tipografi içeren kapsamlı bir uygulama geliştirme özellikleri kümesiyle Core 'u genişletir. WPF .NET 'in bir parçası olduğundan, .NET API 'nin diğer öğelerini birleştiren uygulamalar oluşturabilirsiniz.

Bu genel bakış, Newcomers 'e yöneliktir ve WPF 'in temel yeteneklerini ve kavramlarını ele alır.

## <a name="program-with-wpf"></a>WPF ile program

WPF, ad alanında bulunan (en fazla bölüm için) .NET türlerinin bir alt kümesi olarak mevcuttur <xref:System.Windows> . Daha önce ASP.NET ve Windows Forms gibi yönetilen teknolojiler kullanarak .NET ile uygulamalar oluşturduysanız, temel WPF programlama deneyimi tanıdık gelmelidir; C# veya Visual Basic gibi en sevdiğiniz .NET programlama dilini kullanarak sınıfları örnekleyin, özellikleri ayarlar, yöntemleri çağırır ve olayları işleyebilirsiniz.

WPF, özellikleri ve olayları geliştiren ek programlama yapılarını içerir: [bağımlılık özellikleri](advanced/dependency-properties-overview.md) ve [yönlendirilmiş olaylar](advanced/routed-events-overview.md).

## <a name="markup-and-code-behind"></a>Biçimlendirme ve arka plan kodu

WPF, ASP.NET geliştiricilerin tanıdık olması gereken bir deneyim olan hem *biçimlendirme* hem de *arka plan kodu*kullanarak bir uygulama geliştirmenize olanak tanır. Genellikle XAML işaretlemesini kullanarak, davranışını uygulamak için yönetilen programlama dillerini (arka plan kod) kullanırken bir uygulamanın görünümünü uygulayın. Bu görünüm ve davranışın ayrımı aşağıdaki avantajlara sahiptir:

- Görünüme özgü biçimlendirme davranışa özgü kodla sıkı bir şekilde bağlı olmadığından geliştirme ve bakım maliyetleri azaltılır.

- Geliştiriciler uygulamanın davranışını uygulayan geliştiricilerle aynı anda bir uygulamanın görünümünü uygulayabildiğinden geliştirme daha etkilidir.

- WPF uygulamaları için [Genelleştirme ve yerelleştirme](advanced/wpf-globalization-and-localization-overview.md) basitleştirilmiştir.

### <a name="markup"></a>İşaretleme

XAML, uygulamanın görünümünü bildirimli olarak uygulayan XML tabanlı bir biçimlendirme dilidir. Genellikle Windows, iletişim kutuları, sayfalar ve Kullanıcı denetimleri oluşturmak ve bunları denetimler, şekiller ve grafiklerle doldurmanız için kullanırsınız.

Aşağıdaki örnek, tek bir düğme içeren bir pencerenin görünümünü uygulamak için XAML kullanır:

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

Özellikle, bu XAML `Window` sırasıyla ve öğelerini kullanarak bir pencere ve bir düğme tanımlar `Button` . Her öğe, `Window` `Title` pencerenin başlık çubuğu metnini belirtmek için öğenin özniteliği gibi özniteliklerle yapılandırılır. Çalışma zamanında WPF, biçimlendirme içinde tanımlanan öğeleri ve öznitelikleri WPF sınıflarının örneklerine dönüştürür. Örneğin, `Window` öğesi <xref:System.Windows.Window> <xref:System.Windows.Window.Title%2A> özelliği özniteliğin değeri olan bir sınıfının örneğine dönüştürülür `Title` .

Aşağıdaki şekilde, önceki örnekte XAML tarafından tanımlanan Kullanıcı arabirimi (UI) gösterilmektedir:

![Düğme içeren pencere](media/introduction-to-wpf/wpfintrofigure10.png)

XAML, XML tabanlı olduğundan, onunla oluşturduğunuz Kullanıcı arabirimi bir [öğe ağacı](advanced/trees-in-wpf.md)olarak bilinen iç içe geçmiş öğelerin hiyerarşisinde toplanır. Öğe ağacı, Usıs oluşturmak ve yönetmek için mantıksal ve sezgisel bir yol sağlar.

### <a name="code-behind"></a>Arka plan kodu

Bir uygulamanın ana davranışı, olayları işleme (örneğin, bir menü, araç çubuğu veya düğme) ve yanıt olarak iş mantığı ve veri erişim mantığını çağırma dahil olmak üzere kullanıcı etkileşimlerine yanıt veren işlevselliği uygulamaktır. WPF 'de, bu davranış biçimlendirme ile ilişkili kodda uygulanır. Bu tür bir kod, arka plan kodu olarak bilinir. Aşağıdaki örnek, önceki örnekteki ve arka plan kodundaki güncelleştirilmiş biçimlendirmeyi gösterir:

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.AWindow"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button" Click="button_Click">Click Me!</Button>

</Window>
```

```csharp
using System.Windows; // Window, RoutedEventArgs, MessageBox

namespace SDKSample
{
    public partial class AWindow : Window
    {
        public AWindow()
        {
            // InitializeComponent call is required to merge the UI
            // that is defined in markup with this class, including  
            // setting properties and registering event handlers
            InitializeComponent();
        }

        void button_Click(object sender, RoutedEventArgs e)
        {
            // Show message box when button is clicked.
            MessageBox.Show("Hello, Windows Presentation Foundation!");
        }
    }
}
```

```vb
Namespace SDKSample

    Partial Public Class AWindow
        Inherits System.Windows.Window

        Public Sub New()

            ' InitializeComponent call is required to merge the UI
            ' that is defined in markup with this class, including  
            ' setting properties and registering event handlers
            InitializeComponent()

        End Sub

        Private Sub button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)

            ' Show message box when button is clicked.
            MessageBox.Show("Hello, Windows Presentation Foundation!")

        End Sub

    End Class

End Namespace
```

Bu örnekte, arka plan kodu sınıfından türetilen bir sınıf uygular <xref:System.Windows.Window> . `x:Class`Özniteliği, biçimlendirmeyi arka plan kod sınıfıyla ilişkilendirmek için kullanılır. `InitializeComponent`arka plan kod sınıfı ile biçimlendirme içinde tanımlanan Kullanıcı arabirimini birleştirmek için, kod arkasındaki sınıfın oluşturucusundan çağrılır. ( `InitializeComponent` uygulamanızın oluşturulduğu zaman sizin için oluşturulur, bu nedenle el ile uygulamanız gerekmez.) Birleşimi ve uygulamanızın `x:Class` `InitializeComponent` oluşturulduğu her seferinde doğru başlatıldığından emin olun. Arka plan kod sınıfı, düğmenin olayı için bir olay işleyicisi de uygular <xref:System.Windows.Controls.Primitives.ButtonBase.Click> . Düğmeye tıklandığında, olay işleyicisi yöntemini çağırarak bir ileti kutusu gösterir <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> .

Aşağıdaki şekilde düğme tıklandığında sonuç gösterilmektedir:

![Bir MessageBox](media/introduction-to-wpf/wpfintrofigure25.png)

## <a name="controls"></a>Denetimler

Uygulama modeli tarafından sunulan kullanıcı deneyimleri, oluşturulan denetimlerdir. WPF 'de *Denetim* , bir pencere veya sayfada BARıNDıRıLAN bir WPF sınıfı kategorisi için geçerli olan ve bir kullanıcı arabirimine sahip olan ve bazı davranışları uygulayan bir şemsiye terimidir.

Daha fazla bilgi için bkz. [denetimler](controls/index.md).

### <a name="wpf-controls-by-function"></a>İşleve göre WPF denetimleri

Yerleşik WPF denetimleri burada listelenmiştir:

- **Düğmeler**: <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.Primitives.RepeatButton> .

- **Veri görüntüleme**: <xref:System.Windows.Controls.DataGrid> , <xref:System.Windows.Controls.ListView> , ve <xref:System.Windows.Controls.TreeView> .

- **Tarih görüntüleme ve seçim**: <xref:System.Windows.Controls.Calendar> ve <xref:System.Windows.Controls.DatePicker> .

- **İletişim kutuları**: <xref:Microsoft.Win32.OpenFileDialog> , <xref:System.Windows.Controls.PrintDialog> , ve <xref:Microsoft.Win32.SaveFileDialog> .

- **Dijital mürekkep**: <xref:System.Windows.Controls.InkCanvas> ve <xref:System.Windows.Controls.InkPresenter> .

- **Belgeler**: <xref:System.Windows.Controls.DocumentViewer> , <xref:System.Windows.Controls.FlowDocumentPageViewer> , <xref:System.Windows.Controls.FlowDocumentReader> , <xref:System.Windows.Controls.FlowDocumentScrollViewer> ve <xref:System.Windows.Controls.StickyNoteControl> .

- **Giriş**: <xref:System.Windows.Controls.TextBox> , <xref:System.Windows.Controls.RichTextBox> , ve <xref:System.Windows.Controls.PasswordBox> .

- **Düzen**: <xref:System.Windows.Controls.Border> , <xref:System.Windows.Controls.Primitives.BulletDecorator> ,,, <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Expander> , <xref:System.Windows.Controls.Grid> , <xref:System.Windows.Controls.GridView> , <xref:System.Windows.Controls.GridSplitter> , <xref:System.Windows.Controls.GroupBox> , <xref:System.Windows.Controls.Panel> , <xref:System.Windows.Controls.Primitives.ResizeGrip> , <xref:System.Windows.Controls.Separator> , <xref:System.Windows.Controls.Primitives.ScrollBar> , <xref:System.Windows.Controls.ScrollViewer> , <xref:System.Windows.Controls.StackPanel> , <xref:System.Windows.Controls.Primitives.Thumb> , <xref:System.Windows.Controls.Viewbox> , <xref:System.Windows.Controls.VirtualizingStackPanel> ,, <xref:System.Windows.Window> ve <xref:System.Windows.Controls.WrapPanel> .

- **Medya**: <xref:System.Windows.Controls.Image> , <xref:System.Windows.Controls.MediaElement> , ve <xref:System.Windows.Controls.SoundPlayerAction> .

- **Menüler**: <xref:System.Windows.Controls.ContextMenu> , <xref:System.Windows.Controls.Menu> , ve <xref:System.Windows.Controls.ToolBar> .

- **Gezinti**: <xref:System.Windows.Controls.Frame> ,,, <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationWindow> ve <xref:System.Windows.Controls.TabControl> .

- **Seçim**: <xref:System.Windows.Controls.CheckBox> , <xref:System.Windows.Controls.ComboBox> , <xref:System.Windows.Controls.ListBox> , <xref:System.Windows.Controls.RadioButton> , ve <xref:System.Windows.Controls.Slider> .

- **Kullanıcı bilgileri**: <xref:System.Windows.Controls.AccessText> , <xref:System.Windows.Controls.Label> , <xref:System.Windows.Controls.Primitives.Popup> , <xref:System.Windows.Controls.ProgressBar> , <xref:System.Windows.Controls.Primitives.StatusBar> , <xref:System.Windows.Controls.TextBlock> , ve <xref:System.Windows.Controls.ToolTip> .

## <a name="input-and-commands"></a>Giriş ve komutlar

Denetimler çoğu zaman Kullanıcı girişini algılar ve yanıtlar. [WPF giriş sistemi](advanced/input-overview.md) metin girişi, odak yönetimi ve fare konumlandırmayı desteklemek için hem doğrudan hem de yönlendirilmiş olayları kullanır.

Uygulamalar genellikle karmaşık giriş gereksinimlerine sahiptir. WPF, Kullanıcı giriş eylemlerini bu eylemlere yanıt veren koddan ayıran bir [komut sistemi](advanced/commanding-overview.md) sağlar.

## <a name="layout"></a>Layout

Bir kullanıcı arabirimi oluşturduğunuzda, bir düzen oluşturmak için denetimlerinizi konuma ve boyuta göre düzenleyin. Herhangi bir düzenin önemli bir gereksinimi, pencere boyutu ve görüntüleme ayarlarındaki değişikliklere uyum sağlar. Bu koşullarda bir düzeni uyarlamak için kodu yazmanızı zorlamak yerine WPF, sizin için birinci sınıf bir Genişletilebilir düzen sistemi sağlar.

Düzen sisteminin temel taşı, değişen pencere ve görüntüleme koşullarına uyum sağlayan göreli konumlardır. Ayrıca, Düzen sistemi, düzeni belirleme denetimleri arasındaki anlaşmayı yönetir. Anlaşma iki adımlı bir işlemdir: ilk olarak, bir denetim üst öğeye gereken konumu ve boyutu söyler; İkincisi, üst öğe denetime ne kadar boşluk yapabileceğini söyler.

Düzen sistemi, temel WPF sınıfları aracılığıyla alt denetimlere açıktır. WPF, yığınlama ve yerleştirme gibi ortak düzenler için çeşitli düzen denetimleri içerir:

- <xref:System.Windows.Controls.Canvas>: Alt denetimler kendi düzenlerini sağlar.

- <xref:System.Windows.Controls.DockPanel>: Alt denetimler panelin kenarlarına hizalanır.

- <xref:System.Windows.Controls.Grid>: Alt denetimler satırlara ve sütunlara göre konumlandırılır.

- <xref:System.Windows.Controls.StackPanel>: Alt denetimler dikey ya da yatay olarak yığılır.

- <xref:System.Windows.Controls.VirtualizingStackPanel>: Alt denetimler sanallaştırılır ve yatay veya dikey olarak yönelimli tek bir satırda düzenlenir.

- <xref:System.Windows.Controls.WrapPanel>: Alt denetimler soldan sağa düzende konumlandırılır ve geçerli satırda alanın izin verdiğinden daha fazla denetim olduğunda sonraki satıra kaydırılır.

Aşağıdaki örnek, <xref:System.Windows.Controls.DockPanel> çeşitli denetimleri düzenlemek için bir kullanır <xref:System.Windows.Controls.TextBox> :

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_1.xaml)]

, <xref:System.Windows.Controls.DockPanel> Alt <xref:System.Windows.Controls.TextBox> denetimlerin nasıl düzenlendiğini anlatmasını sağlar. Bunu yapmak için, <xref:System.Windows.Controls.DockPanel> `Dock` bir yuva stili belirtmesini sağlamak üzere alt denetimlere açık olan iliştirilmiş bir özellik uygular.

> [!NOTE]
> Alt denetimler tarafından kullanılmak üzere bir üst denetim tarafından uygulanan bir özellik, [iliştirilmiş özelliği](advanced/attached-properties-overview.md)olarak ADLANDıRıLAN bir WPF yapısıdır.

Aşağıdaki şekilde, önceki örnekteki XAML biçimlendirmesinin sonucu gösterilmektedir:

![DockPanel sayfası](media/introduction-to-wpf/wpfintrofigure11.png)

## <a name="data-binding"></a>Veri bağlama

Birçok uygulama, kullanıcılara verileri görüntüleme ve düzenleme araçlarını sağlamak için oluşturulur. WPF uygulamaları için, veri depolama ve erişme işi SQL Server ve ADO .NET gibi teknolojiler tarafından zaten sunulmaktadır. Verilere erişildikten ve uygulamanın yönetilen nesnelerine yüklendikten sonra, WPF uygulamalarına yönelik sabit çalışma başlar. Temelde, bu iki şeyi içerir:

1. Yönetilen nesnelerden verileri, verilerin görüntülenebildiği ve düzenlenebileceği denetimlere kopyalama.

2. Denetimler kullanılarak verilerde yapılan değişikliklerin, yönetilen nesnelere geri kopyalanmasını sağlamak.

WPF, uygulama geliştirmeyi basitleştirmek için, bu adımları otomatik olarak gerçekleştirmek üzere bir veri bağlama altyapısı sağlar. Veri bağlama altyapısının çekirdek birimi, <xref:System.Windows.Data.Binding> işi bir denetimi (bağlama hedefi) bir veri nesnesine (bağlama kaynağı) bağlamak olan sınıftır. Bu ilişki aşağıdaki şekilde gösterilmiştir:

![Temel veri bağlama diyagramı](media/introduction-to-wpf/databindingmostbasic.png)

Sonraki örnekte, bir <xref:System.Windows.Controls.TextBox> özel nesne örneğine nasıl bağlanacağı gösterilmektedir `Person` . `Person`Uygulama aşağıdaki kodda gösterilmiştir:

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_2.cs)]

Aşağıdaki biçimlendirme, öğesini bir <xref:System.Windows.Controls.TextBox> özel nesne örneğine bağlar `Person` :

```xaml
 <Window
     xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
     xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
     x:Class="SDKSample.DataBindingWindow">

   <!-- Bind the TextBox to the data source (TextBox.Text to Person.Name) -->
   <TextBox Name="personNameTextBox" Text="{Binding Path=Name}" />

 </Window>
```

[!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_6.vb)]
[!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_6.cs)]

Bu örnekte, `Person` sınıfı arka plan kodunda oluşturulur ve için veri bağlamı olarak ayarlanır `DataBindingWindow` . Biçimlendirme bölümünde <xref:System.Windows.Controls.TextBox.Text%2A> öğesinin özelliği <xref:System.Windows.Controls.TextBox> `Person.Name` özelliğine bağlanır (" `{Binding ... }` " xaml sözdizimi kullanılarak). Bu XAML, WPF <xref:System.Windows.Controls.TextBox> `Person` 'in denetimi pencerenin özelliğinde depolanan nesneye bağlamasını söyler <xref:System.Windows.FrameworkElement.DataContext%2A> .

WPF veri bağlama altyapısı, doğrulama, sıralama, filtreleme ve gruplamayı içeren ek destek sağlar. Ayrıca, veri bağlama, standart WPF denetimleri tarafından görüntülenecek kullanıcı arabirimi uygun olmadığında, bağlantılı veriler için özel kullanıcı arabirimi oluşturmak üzere veri şablonlarının kullanımını destekler.

Daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../../desktop-wpf/data/data-binding-overview.md).

## <a name="graphics"></a>Grafikler

WPF, aşağıdaki avantajları içeren kapsamlı, ölçeklenebilir ve esnek bir grafik özellikleri kümesi sunar:

- **Çözünürlükten bağımsız ve cihazdan bağımsız grafikler**. WPF Grafik sistemindeki temel ölçü birimi, gerçek ekran çözünürlüğünden bağımsız olarak bir inç 1/96th olan cihazdan bağımsız pikseldir ve çözünürlükten bağımsız ve cihazdan bağımsız işleme için temel sağlar. Her cihazdan bağımsız piksel, üzerinde oluşturduğu sistemin inç başına nokta (DPI) ayarıyla eşleşecek şekilde otomatik olarak ölçeklendirilir.

- **İyileştirilmiş duyarlık**. WPF koordinat sistemi, tek duyarlık yerine çift duyarlıklı kayan noktalı sayılar ile ölçülür. Dönüşümler ve opaklık değerleri de çift duyarlıklı olarak ifade edilir. WPF ayrıca geniş bir renk gamutu (scRGB) destekler ve farklı renk uzaylarından girişleri yönetmek için tümleşik destek sağlar.

- **Gelişmiş grafikler ve animasyon desteği**. WPF, sizin için animasyon sahneleri yöneterek grafik programlamayı basitleştirir; sahne işleme, işleme döngüleri ve Bilinear ilişkilendirme konusunda endişelenmenize gerek yoktur. Ayrıca WPF, isabet testi desteği ve tam alfa birleştirme desteği sağlar.

- **Donanım hızlandırma**. WPF Grafik sistemi, CPU kullanımını en aza indirmek için grafik donanımından yararlanır.

### <a name="2d-shapes"></a>2B şekiller

WPF, aşağıdaki çizimde gösterilen dikdörtgenler ve üç nokta gibi yaygın bir vektör çizilmiş 2B şekil kitaplığı sağlar:

![Üç nokta ve dikdörtgen](media/introduction-to-wpf/wpfintrofigure4.PNG)

Şekillerin ilginç bir özelliği yalnızca görüntüleme için değildir; şekiller, klavye ve fare girişi dahil olmak üzere denetimlerden beklediğinizi birçok özelliği uygular. Aşağıdaki örnek, <xref:System.Windows.UIElement.MouseUp> işlenmekte olan olayını gösterir <xref:System.Windows.Shapes.Ellipse> :

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_8.cs)]

Aşağıdaki şekilde, önceki kod tarafından üretilen değer gösterilmektedir:

!["Elips tıkladınız&#33;" metnini içeren pencere](media/introduction-to-wpf/wpfintrofigure12.png)

Daha fazla bilgi için bkz. [WPF 'de şekillere ve temel çizime genel bakış](../../desktop-wpf/data/data-binding-overview.md).

### <a name="2d-geometries"></a>2B geometriler

WPF tarafından sunulan 2B şekiller, temel şekillerin standart kümesini kapsar. Ancak, özelleştirilmiş bir kullanıcı arabiriminin tasarımını kolaylaştırmak için özel şekiller oluşturmanız gerekebilir. Bu amaçla WPF, geometriler sağlar. Aşağıdaki şekilde, doğrudan çizilemeyen, fırça olarak kullanılan veya diğer şekilleri ve denetimleri kırpmak için kullanılan özel bir şekil oluşturmak için geometriler kullanımı gösterilmektedir.

<xref:System.Windows.Shapes.Path>nesneler, kapalı veya açık şekiller, birden çok şekil ve hatta eğri şekiller çizmek için kullanılabilir.

<xref:System.Windows.Media.Geometry>nesneler kırpma, isabet sınama ve 2B grafik verileri işleme için kullanılabilir.

![Yolun çeşitli kullanımları](media/introduction-to-wpf/wpfintrofigure5.png)

Daha fazla bilgi için bkz. [geometriye genel bakış](graphics-multimedia/geometry-overview.md).

### <a name="2d-effects"></a>2B efektler

WPF 2B özellikleri alt kümesi degradeler, bit eşlemler, çizimler, videolar, döndürme, ölçeklendirme ve eğriltme gibi görsel etkileri içerir. Bunlar fırçalar ile elde edilir; Aşağıdaki şekilde bazı örnekler gösterilmektedir:

![Farklı fırçaların çizimi](media/introduction-to-wpf/wpfintrofigure6.png)

Daha fazla bilgi için bkz. [WPF Fırçalarına Genel Bakış](graphics-multimedia/wpf-brushes-overview.md).

### <a name="3d-rendering"></a>3B işleme

WPF ayrıca, daha heyecan verici ve ilginç Kullanıcı arabirimleri oluşturulmasına olanak tanımak için 2B grafiklerle tümleştirilen 3B işleme özelliklerini de içerir. Örneğin, aşağıdaki şekilde 3B şekiller üzerinde işlenen 2D görüntüleri gösterilmektedir:

![Visual3d değil örnek ekran görüntüsü](media/introduction-to-wpf/wpfintrofigure13.png)

Daha fazla bilgi için bkz. [3B grafiklere genel bakış](graphics-multimedia/3-d-graphics-overview.md).

## <a name="animation"></a>Animasyon

WPF animasyon desteği, denetimlerin büyümesi, sallanması, dönmesi ve belirmesini, ilginç sayfa geçişleri oluşturmak ve daha fazlasını yapmanızı sağlar. Birçok WPF sınıfının, hatta özel sınıfların animasyonunu yapabilirsiniz. Aşağıdaki şekilde, eylem içinde basit bir animasyon gösterilmektedir:

![Animasyonlu küpün görüntüleri](media/introduction-to-wpf/wpfintrofigure7.png)

Daha fazla bilgi için bkz. [animasyon genel bakış](graphics-multimedia/animation-overview.md).

## <a name="media"></a>Medya

Zengin içerik iletmenin bir yolu, Audiovisual medyası kullanmaktır. WPF, görüntüler, videolar ve ses için özel destek sağlar.

### <a name="images"></a>Görüntüler

Görüntüler çoğu uygulama için ortaktır ve WPF bunları kullanmak için çeşitli yollar sağlar. Aşağıdaki şekilde, küçük resim görüntüleri içeren bir liste kutusuyla bir kullanıcı arabirimi gösterilmektedir. Küçük resim seçildiğinde görüntü tam boyut olarak gösterilir.

![Küçük resim görüntüleri ve tam&#45;boyutu görüntüsü](media/introduction-to-wpf/wpfintrofigure8.png)

Daha fazla bilgi için bkz. [Imaging 'e genel bakış](graphics-multimedia/imaging-overview.md).

### <a name="video-and-audio"></a>Video ve ses

<xref:System.Windows.Controls.MediaElement>Denetim hem videoyu hem de sesi oynatabilen ve özel bir medya yürütücüsünün temeli olması yeterince esnektir. Aşağıdaki XAML biçimlendirmesi bir medya oynatıcı uygular:

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_9.xaml)]

Aşağıdaki şekilde gösterilen pencerede <xref:System.Windows.Controls.MediaElement> Denetim eylemi gösterilmektedir:

![Ses ve video ile MediaElement denetimi](media/introduction-to-wpf/wpfintrofigure1.png)

Daha fazla bilgi için bkz. [grafik ve multimedya](graphics-multimedia/index.md).

## <a name="text-and-typography"></a>Metin ve tipografi

WPF, yüksek kaliteli metin işlemesini kolaylaştırmak için aşağıdaki özellikleri sunar:

- OpenType yazı tipi desteği.

- ClearType geliştirmeleri.

- Donanım hızlandırmasının avantajlarından yararlanan yüksek performans.

- Medya, grafik ve animasyonla metin tümleştirmesi.

- Uluslararası yazı tipi desteği ve geri dönüş mekanizmaları.

Grafiklerle metin tümleştirmesinin bir sunumu olarak aşağıdaki şekil metin düzenlemelerinin uygulamasını göstermektedir:

![Çeşitli metin süslemeleri içeren metin](media/introduction-to-wpf/wpfintrofigure23.png)

Daha fazla bilgi için bkz. [tipografi Windows Presentation Foundation](advanced/typography-in-wpf.md).

## <a name="customize-wpf-apps"></a>WPF uygulamalarını özelleştirme

Bu noktaya kadar, uygulama geliştirmeye yönelik temel WPF yapı taşlarını gördünüz. Genellikle denetimlerden oluşan uygulama içeriğini barındırmak ve sunmak için uygulama modelini kullanırsınız. Bir kullanıcı arabirimindeki denetimlerin düzenlemesini basitleştirmek ve düzenlemenin pencere boyutu ve görüntüleme ayarlarında yapılan değişiklikler üzerinde tutulmasını sağlamak için WPF düzen sistemini kullanırsınız. Çoğu uygulama, kullanıcıların verilerle etkileşime girmesine izin vertiğinden, Kullanıcı arabiriminizi verilerle tümleştirme işini azaltmak için veri bağlamayı kullanırsınız. Uygulamanızın görsel görünümünü geliştirmek için WPF tarafından sunulan kapsamlı grafik, animasyon ve medya desteği aralığını kullanırsınız.

Genellikle, temel bilgiler, gerçekten ayrı ve görsel açıdan etkileyici bir kullanıcı deneyimi oluşturmak ve yönetmek için yeterli değildir. Standart WPF denetimleri uygulamanızın istenen görünümüyle tümleştirilemeyebilir. Veriler en etkili şekilde görüntülenmeyebilir. Uygulamanızın genel kullanıcı deneyimi, Windows temalarının varsayılan görünümü ve hislerine uygun olmayabilir. Birçok şekilde, bir sunum teknolojisinin diğer genişletilebilirlik türleri kadar çok görsel genişletilebilirliği olması gerekir.

Bu nedenle WPF, denetimler, Tetikleyiciler, denetim ve veri şablonları, stiller, Kullanıcı arabirimi kaynakları ve Temalar ve kaplamalar için zengin bir içerik modeli de dahil olmak üzere benzersiz kullanıcı deneyimleri oluşturmak için çeşitli mekanizmalar sunar.

### <a name="content-model"></a>İçerik modeli

WPF denetimlerinin çoğunluğunun ana amacı içeriği görüntülemektir. WPF içinde, bir denetimin içeriğini oluşturan öğelerin türü ve sayısı denetimin *içerik modeli*olarak adlandırılır. Bazı denetimler, tek bir öğe ve içerik türü içerebilir; Örneğin, öğesinin içeriği <xref:System.Windows.Controls.TextBox> özelliğine atanan bir dize değeridir <xref:System.Windows.Controls.TextBox.Text%2A> . Aşağıdaki örnek bir öğesinin içeriğini ayarlar <xref:System.Windows.Controls.TextBox> :

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

Aşağıdaki şekilde sonuç gösterilmektedir:

![Metin içeren TextBox denetimi](media/introduction-to-wpf/wpfintrofigure21.png)

Bununla birlikte, diğer denetimler farklı türde içeriklerde birden çok öğe içerebilir; özelliği tarafından belirtilen bir öğesinin içeriği, <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ContentControl.Content%2A> düzen denetimleri, metin, Resimler ve şekiller gibi çeşitli öğeleri içerebilir. Aşağıdaki örnek, bir,, <xref:System.Windows.Controls.Button> a ve içeren içeriği içeren bir gösterir <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.Border> <xref:System.Windows.Controls.MediaElement> :

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ButtonContentWindow"
    Title="Button Content">

  <Button Margin="20">
    <!-- Button Content -->
    <DockPanel Width="200" Height="180">
      <Label DockPanel.Dock="Top" HorizontalAlignment="Center">Click Me!</Label>
      <Border Background="Black" BorderBrush="Yellow" BorderThickness="2"
        CornerRadius="2" Margin="5">
        <MediaElement Source="media/wpf.wmv" Stretch="Fill" />
      </Border>
    </DockPanel>
  </Button>
</Window>
```

Aşağıdaki şekilde bu düğmenin içeriği gösterilmektedir:

![Birden çok türde içerik içeren bir düğme](media/introduction-to-wpf/wpfintrofigure22.png)

Çeşitli denetimler tarafından desteklenen içerik türleri hakkında daha fazla bilgi için bkz. [WPF içerik modeli](controls/wpf-content-model.md).

### <a name="triggers"></a>Tetikleyiciler

XAML biçimlendirmesinin ana amacı uygulamanın görünümünü uygulamak olsa da, bir uygulamanın davranışının bazı yönlerini uygulamak için XAML de kullanabilirsiniz. Bir örnek, bir uygulamanın görünümünü kullanıcı etkileşimlerine göre değiştirmek için tetikleyicilerin kullanılması. Daha fazla bilgi için bkz. [Stiller ve şablonlar](../../desktop-wpf/fundamentals/styles-templates-overview.md).

### <a name="control-templates"></a>Denetim şablonları

WPF denetimleri için varsayılan kullanıcı arabirimleri genellikle diğer denetimlerden ve şekillerden oluşturulur. Örneğin, bir, <xref:System.Windows.Controls.Button> <xref:Microsoft.Windows.Themes.ButtonChrome> ve <xref:System.Windows.Controls.ContentPresenter> denetimlerinden oluşur. , <xref:Microsoft.Windows.Themes.ButtonChrome> Standart düğme görünümünü sağlar, ancak <xref:System.Windows.Controls.ContentPresenter> düğme içeriğini özelliği tarafından belirtilen şekilde görüntüler <xref:System.Windows.Controls.ContentControl.Content%2A> .

Bazen bir denetimin varsayılan görünümü bir uygulamanın genel görünümüyle birlikte kullanılamaz. Bu durumda, <xref:System.Windows.Controls.ControlTemplate> içeriğini ve davranışını değiştirmeden denetimin kullanıcı arabiriminin görünümünü değiştirmek için bir kullanabilirsiniz.

Aşağıdaki örnek, öğesinin görünümünü kullanarak nasıl değiştirileceğini göstermektedir <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate> :

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_17.vb)]

Bu örnekte, varsayılan düğme Kullanıcı arabirimi <xref:System.Windows.Shapes.Ellipse> koyu mavi kenarlığa sahip olan ve kullanılarak doldurulmuş bir ile değiştirilmiştir <xref:System.Windows.Media.RadialGradientBrush> . <xref:System.Windows.Controls.ContentPresenter>Denetimde içeriğini görüntüleyen denetim <xref:System.Windows.Controls.Button> , "bana tıklama!" <xref:System.Windows.Controls.Button>Tıklandığında <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay, denetimin varsayılan davranışının bir parçası olarak yine de oluşturulur <xref:System.Windows.Controls.Button> . Sonuç aşağıdaki şekilde gösterilmiştir:

![Elips düğme ve ikinci bir pencere](media/introduction-to-wpf/wpfintrofigure2.png)

### <a name="data-templates"></a>Veri şablonları

Bir denetim şablonu bir denetimin görünümünü belirtmenize izin verirken, bir veri şablonu bir denetimin içeriğinin görünümünü belirtmenize olanak tanır. Veri şablonları genellikle, bağlantılı verilerin nasıl görüntülendiğini iyileştirmek için kullanılır. Aşağıdaki şekilde, <xref:System.Windows.Controls.ListBox> `Task` her görevin bir adı, açıklaması ve önceliği olduğu bir nesne koleksiyonuna bağlanan bir için varsayılan görünüm gösterilmektedir:

![Varsayılan görünümü içeren bir liste kutusu](media/introduction-to-wpf/wpfintrofigure18.png)

Varsayılan görünüm, bir ' dan beklediğiniz şeydir <xref:System.Windows.Controls.ListBox> . Ancak, her görevin varsayılan görünümü yalnızca görev adını içerir. Görev adını, açıklamasını ve önceliğini göstermek için, <xref:System.Windows.Controls.ListBox> denetimin bağlantılı liste öğelerinin varsayılan görünümünün bir kullanılarak değiştirilmesi gerekir <xref:System.Windows.DataTemplate> . Aşağıdaki XAML, bu tür bir <xref:System.Windows.DataTemplate> , özniteliği kullanılarak her bir göreve uygulanan böyle bir tanımlar <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> :

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="SDKSample.DataTemplateWindow"
  Title="With a Data Template">
  <Window.Resources>
    <!-- Data Template (applied to each bound task item in the task collection) -->
    <DataTemplate x:Key="myTaskTemplate">
      <Border Name="border" BorderBrush="DarkSlateBlue" BorderThickness="2"
        CornerRadius="2" Padding="5" Margin="5">
        <Grid>
          <Grid.RowDefinitions>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
          </Grid.RowDefinitions>
          <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition />
          </Grid.ColumnDefinitions>
          <TextBlock Grid.Row="0" Grid.Column="0" Padding="0,0,5,0" Text="Task Name:"/>
          <TextBlock Grid.Row="0" Grid.Column="1" Text="{Binding Path=TaskName}"/>
          <TextBlock Grid.Row="1" Grid.Column="0" Padding="0,0,5,0" Text="Description:"/>
          <TextBlock Grid.Row="1" Grid.Column="1" Text="{Binding Path=Description}"/>
          <TextBlock Grid.Row="2" Grid.Column="0" Padding="0,0,5,0" Text="Priority:"/>
          <TextBlock Grid.Row="2" Grid.Column="1" Text="{Binding Path=Priority}"/>
        </Grid>
      </Border>
    </DataTemplate>
  </Window.Resources>

  <!-- UI -->
  <DockPanel>
    <!-- Title -->
    <Label DockPanel.Dock="Top" FontSize="18" Margin="5" Content="My Task List:"/>

    <!-- Data template is specified by the ItemTemplate attribute -->
    <ListBox
      ItemsSource="{Binding}"
      ItemTemplate="{StaticResource myTaskTemplate}"
      HorizontalContentAlignment="Stretch"
      IsSynchronizedWithCurrentItem="True"
      Margin="5,0,5,5" />

 </DockPanel>
</Window>
```

Aşağıdaki şekilde, bu kodun etkisi gösterilmektedir:

![Veri şablonu kullanan liste kutusu](media/introduction-to-wpf/wpfintrofigure19.png)

Öğesinin <xref:System.Windows.Controls.ListBox> davranışını ve genel görünümünü beklediğine ve yalnızca liste kutusu tarafından görüntülenen içeriğin görünümü değiştiği unutulmamalıdır.

Daha fazla bilgi için bkz. [veri şablonu oluşturmaya genel bakış](data/data-templating-overview.md).

### <a name="styles"></a>Stiller

Stiller, geliştiricilerin ve tasarımcıların ürünlerinin belirli bir görünümünü standartlaştırmasını sağlar. WPF, öğesi olan bir güçlü stil modeli sunar <xref:System.Windows.Style> . Aşağıdaki örnek, her bir pencerede için arka plan rengini ayarlayan bir stil oluşturur <xref:System.Windows.Controls.Button> `Orange` :

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.StyleWindow"
    Title="Styles">
  <!-- Style that will be applied to all buttons -->
  <Style TargetType="{x:Type Button}">
    <Setter Property="Background" Value="Orange" />
    <Setter Property="BorderBrush" Value="Crimson" />
    <Setter Property="FontSize" Value="20" />
    <Setter Property="FontWeight" Value="Bold" />
    <Setter Property="Margin" Value="5" />
  </Style>
  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>

  <!-- This label will not have the style applied to it -->
  <Label>Don't Click Me!</Label>

  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>
</Window>
```

Bu stil tüm denetimleri hedeflediğinden <xref:System.Windows.Controls.Button> , stil, aşağıdaki şekilde gösterildiği gibi penceredeki tüm düğmelere otomatik olarak uygulanır:

![İki turuncu düğme](media/introduction-to-wpf/wpfintrofigure20.png)

Daha fazla bilgi için bkz. [Stiller ve şablonlar](../../desktop-wpf/fundamentals/styles-templates-overview.md).

### <a name="resources"></a>Kaynaklar

Bir uygulamadaki denetimler aynı görünümü paylaşmalıdır. Bu, yazı tiplerinden ve arka plan renklerinden şablonları, veri şablonlarını ve stilleri denetleyebilen herhangi bir şeyi içerebilir. Bu kaynakları yeniden kullanım için tek bir konumda kapsüllemek üzere, WPF 'nin Kullanıcı arabirimi kaynakları desteğini kullanabilirsiniz.

Aşağıdaki örnek, ve tarafından paylaşılan ortak bir arka plan rengi tanımlar <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Label> :

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ResourcesWindow"
    Title="Resources Window">

  <!-- Define window-scoped background color resource -->
  <Window.Resources>
    <SolidColorBrush x:Key="defaultBackground" Color="Red" />
  </Window.Resources>

  <!-- Button background is defined by window-scoped resource -->
  <Button Background="{StaticResource defaultBackground}">One Button</Button>

  <!-- Label background is defined by window-scoped resource -->
  <Label Background="{StaticResource defaultBackground}">One Label</Label>
</Window>
```

Bu örnek, özellik öğesini kullanarak bir arka plan rengi kaynağı uygular `Window.Resources` . Bu kaynak, öğesinin tüm alt öğeleri için kullanılabilir <xref:System.Windows.Window> . Aşağıdakiler de dahil olmak üzere çeşitli kaynak kapsamları çözümlendikleri sırayla listelenmiştir:

1. Tek bir denetim (devralınan özelliği kullanarak <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> ).

2. A <xref:System.Windows.Window> veya a <xref:System.Windows.Controls.Page> (devralınan özelliği de kullanılarak <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> ).

3. Bir <xref:System.Windows.Application> (özelliğini kullanarak <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> ).

Çeşitli kapsamlar, kaynaklarınızı tanımladığınız ve paylaştığınız yönteme göre esneklik sağlar.

Kaynaklarınızın belirli bir kapsamla doğrudan ilişkilendirilmesi için alternatif olarak, bir veya daha fazla kaynağı, <xref:System.Windows.ResourceDictionary> uygulamanın diğer bölümlerinde başvurulabilen ayrı bir kullanarak paketleyebilir. Örneğin, aşağıdaki örnek bir kaynak sözlüğünde varsayılan bir arka plan rengi tanımlar:

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

Aşağıdaki örnek, bir uygulama genelinde paylaşılmak üzere önceki örnekte tanımlanan kaynak sözlüğüne başvurur:

```xaml
<Application
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.App">

  <Application.Resources>
    <ResourceDictionary>
      <ResourceDictionary.MergedDictionaries>
        <ResourceDictionary Source="BackgroundColorResources.xaml"/>
      </ResourceDictionary.MergedDictionaries>
    </ResourceDictionary>
  </Application.Resources>
</Application>
```

Kaynaklar ve kaynak sözlükleri, Temalar ve kaplamalar için WPF desteğinin temelini içerir.

Daha fazla bilgi için bkz. [kaynaklar](../../desktop-wpf/fundamentals/xaml-resources-define.md).

### <a name="custom-controls"></a>Özel denetimler

WPF, özelleştirme desteği sunan bir konak sağlasa da, mevcut WPF denetimlerinin uygulamanızın veya kullanıcılarınızın ihtiyaçlarını karşılamadığında karşılaşabileceğiniz durumlarla karşılaşabilirsiniz. Bu durum şu durumlarda oluşabilir:

- İhtiyaç duyduğunuz Kullanıcı arabirimi, mevcut WPF uygulamalarının görünümü özelleştirilerek oluşturulamaz.

- Gerekli olan davranış, mevcut WPF uygulamaları tarafından desteklenmez (veya kolayca desteklenmez).

Ancak, bu noktada, yeni bir denetim oluşturmak için üç WPF modelinden birini kullanabilirsiniz. Her model belirli bir senaryoyu hedefler ve özel denetiminizin belirli bir WPF Taban sınıfından türemesini gerektirir. Üç model burada listelenmiştir:

- **Kullanıcı denetimi modeli**. Özel denetim, öğesinden türetilir <xref:System.Windows.Controls.UserControl> ve bir veya daha fazla denetimden oluşur.

- **Denetim modeli**. Özel bir denetim, ' dan türetilir <xref:System.Windows.Controls.Control> ve, WPF denetimlerinin çoğunluğunda olduğu gibi, davranışlarını, şablonlarının görünümlerini kullanarak ayıran uygulamalar oluşturmak için kullanılır. Öğesinden türetme <xref:System.Windows.Controls.Control> , Kullanıcı denetimlerinden özel bir kullanıcı arabirimi oluşturmak için daha fazla özgürlük sağlar, ancak daha fazla çaba gerektirebilir.

- **Framework öğe modeli**. Özel denetim, <xref:System.Windows.FrameworkElement> görünümü özel işleme mantığı (şablon değil) tarafından tanımlandığında öğesinden türetilir.

Aşağıdaki örnek, öğesinden türetilen özel bir sayısal yukarı/aşağı denetimi göstermektedir <xref:System.Windows.Controls.UserControl> :

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_34.vb)]

Aşağıdaki örnek, Kullanıcı denetimini öğesine eklemek için gereken XAML 'yi göstermektedir <xref:System.Windows.Window> :

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_37.xaml)]

Aşağıdaki şekilde, `NumericUpDown` içinde barındırılan denetim gösterilmektedir <xref:System.Windows.Window> :

![Özel bir UserControl](media/introduction-to-wpf/wpfintrofigure3.png)

Özel denetimler hakkında daha fazla bilgi için bkz. [Denetim yazma genel bakış](controls/control-authoring-overview.md).

## <a name="wpf-best-practices"></a>WPF en iyi uygulamaları

Her türlü geliştirme platformunda olduğu gibi, WPF istenen sonuca ulaşmak için çeşitli yollarla kullanılabilir. WPF uygulamalarınızın gerekli Kullanıcı deneyimini sağlayıp, genel olarak hedef kitle taleplerini karşıladığından emin olmanın bir yolu olarak erişilebilirlik, Genelleştirme ve yerelleştirme ve performans için önerilen en iyi uygulamalar vardır. Daha fazla bilgi için bkz.

- [Erişilebilirlik](../ui-automation/accessibility-best-practices.md)
- [WPF Genelleştirme ve yerelleştirme](advanced/wpf-globalization-and-localization-overview.md)
- [WPF uygulama performansı](advanced/optimizing-wpf-application-performance.md)
- [WPF güvenliği](security-wpf.md)

## <a name="next-steps"></a>Sonraki adımlar

WPF 'nin temel özelliklerine baktık. Şimdi ilk WPF uygulamanızı oluşturma zamanı.

> [!div class="nextstepaction"]
> [İzlenecek yol: ilk WPF Masaüstü Uygulamam](getting-started/walkthrough-my-first-wpf-desktop-application.md)

## <a name="see-also"></a>Ayrıca bkz.

- [WPF kullanmaya başlama](getting-started/index.md)
- [Windows Presentation Foundation](index.md)
- [WPF topluluk kaynakları](getting-started/community-feedback.md)
