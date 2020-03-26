---
title: WPF'ye Giriş
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
dev_langs:
- csharp
- vb
ms.openlocfilehash: 759c1ca20ac139ef856df08ec42fb259fc3920d1
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112017"
---
# <a name="wpf-overview"></a>WPF’ye genel bakış

Windows Sunu Temeli (WPF), görsel olarak çarpıcı kullanıcı deneyimleriyle Windows için masaüstü istemci uygulamaları oluşturmanıza olanak tanır.

![Contoso Healthcare UI örneği](media/introduction-to-wpf/wpfintrofigure24.png)

WPF'nin çekirdeği, modern grafik donanımLarından yararlanmak için oluşturulmuş çözünürlükten bağımsız ve vektör tabanlı bir işleme motorudur. WPF genişletilebilir Uygulama Biçimlendirme Dili (XAML), denetimler, veri bağlama, düzen, 2D ve 3D grafikler, animasyon, stiller, şablonlar, belgeler, medya, metin ve içeren kapsamlı bir uygulama geliştirme özellikleri kümesi ile çekirdek genişletir Tipografi. WPF .NET'in bir parçasıdır, böylece .NET API'nin diğer öğelerini içeren uygulamalar oluşturabilirsiniz.

Bu genel bakış yeni gelenler için tasarlanmıştır ve WPF'nin temel özelliklerini ve kavramlarını kapsar.

## <a name="program-with-wpf"></a>WPF programı

WPF, ad alanında bulunan (çoğunlukla) .NET türlerinin <xref:System.Windows> bir alt kümesi olarak bulunur. ASP.NET ve Windows Forms gibi yönetilen teknolojileri kullanarak .NET ile daha önce uygulama inşa ettiyseniz, temel WPF programlama deneyimi tanıdık olmalıdır; C# veya Visual Basic gibi favori .NET programlama dilini kullanarak sınıfları anında ayarlar, özellikleri ayarlar, arama yöntemleri ni çağırır ve olayları işlersiniz.

WPF özellikleri ve olayları geliştirmek ek programlama yapıları içerir: [bağımlılık özellikleri](advanced/dependency-properties-overview.md) ve [yönlendirilen olaylar.](advanced/routed-events-overview.md)

## <a name="markup-and-code-behind"></a>Biçimlendirme ve kod arkası

WPF, hem *biçimlendirme* hem de *kod arkası*kullanarak bir uygulama geliştirmenize olanak tanır ve geliştiricilerin ASP.NET aşina olması gereken bir deneyim. Genellikle, davranışını uygulamak için yönetilen programlama dillerini (kod arkası) kullanırken bir uygulamanın görünümünü uygulamak için XAML biçimlendirmesini kullanırsınız. Görünüm ve davranış bu ayrım aşağıdaki yararları vardır:

- Görünüme özel biçimlendirme davranışa özgü kodla sıkı bir şekilde birleştirilemediği için geliştirme ve bakım maliyetleri azalır.

- Tasarımcılar, uygulamanın davranışını uygulayan geliştiricilerle aynı anda bir uygulamanın görünümünü uygulayabildiklerinden, geliştirme daha verimlidir.

- WPF uygulamaları için [küreselleşme ve yerelleştirme](advanced/wpf-globalization-and-localization-overview.md) basitleştirilmiştir.

### <a name="markup"></a>İşaretleme

XAML, bir uygulamanın görünümünü bildirimsel olarak uygulayan XML tabanlı bir biçimlendirme dilidir. Genellikle pencereler, iletişim kutuları, sayfalar ve kullanıcı denetimleri oluşturmak ve bunları denetimler, şekiller ve grafiklerle doldurmak için kullanırsınız.

Aşağıdaki örnek, tek bir düğme içeren bir pencere görünümünü uygulamak için XAML kullanır:

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

Özellikle, bu XAML sırasıyla `Window` ve öğeleri kullanarak `Button` bir pencere ve bir düğme tanımlar. Her öğe, pencerenin başlık çubuğu `Window` metnini `Title` belirtmek için öğenin özniteliği gibi özniteliklerle yapılandırılır. Çalışma zamanında, WPF biçimlendirmede tanımlanan öğeleri ve öznitelikleri WPF sınıflarının örneklerine dönüştürür. Örneğin, `Window` öğe özelliği öznitelik değeri <xref:System.Windows.Window> <xref:System.Windows.Window.Title%2A> `Title` olan sınıfın bir örneğine dönüştürülür.

Aşağıdaki şekilde, önceki örnekte XAML tarafından tanımlanan kullanıcı arabirimi (UI) gösterilmektedir:

![Düğme içeren bir pencere](media/introduction-to-wpf/wpfintrofigure10.png)

XAML XML tabanlı olduğundan, onunla oluşturduğunuz [UI, öğe ağacı](advanced/trees-in-wpf.md)olarak bilinen iç içe öğeler hiyerarşisinde bir araya getirilir. Öğe ağacı, Kullanıcı Arabirimi oluşturmak ve yönetmek için mantıklı ve sezgisel bir yol sağlar.

### <a name="code-behind"></a>Kod arkası

Bir uygulamanın temel davranışı, olayları işleme (örneğin, bir menü, araç çubuğu nu veya düğmeyi tıklatma) ve yanıt olarak iş mantığı ve veri erişim mantığını çağırmak da dahil olmak üzere kullanıcı etkileşimlerine yanıt veren işlevselliği uygulamaktır. WPF'de, bu davranış biçimlendirmeyle ilişkili kodda uygulanır. Bu kod türü kod arkası olarak bilinir. Aşağıdaki örnek, önceki örnekten güncelleştirilmiş biçimlendirmeyi ve kodun arkasını gösterir:

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

Bu örnekte, kod arkası <xref:System.Windows.Window> sınıftan türetilen bir sınıf uygular. Öznitelik, `x:Class` biçimlendirmeyi kod arkası sınıfıyla ilişkilendirmek için kullanılır. `InitializeComponent`biçimlendirmede tanımlanan UI'yi kod arkası sınıfıyla birleştirmek için kod arkasındaki sınıfın oluşturucusundan çağrılır. (`InitializeComponent` uygulamanız oluşturulduğunda sizin için oluşturulur, bu nedenle el ile uygulamanız gerekmez.) Birleşimi `x:Class` ve `InitializeComponent` uygulamanızın oluşturulduğunda doğru şekilde başlatılmasını sağlamak. Kod arkası sınıfı, düğmenin <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı için bir olay işleyicisi de uygular. Düğme tıklatıldığında, olay işleyicisi <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> yöntemi arayarak bir ileti kutusu gösterir.

Aşağıdaki şekil, düğme tıklatıldığında sonucu gösterir:

![Bir MessageBox](media/introduction-to-wpf/wpfintrofigure25.png)

## <a name="controls"></a>Denetimler

Uygulama modeli tarafından teslim edilen kullanıcı deneyimleri denetimler oluşturulur. WPF'de *denetim,* pencere veya sayfada barındırılan, kullanıcı arabirimine sahip ve bazı davranışları uygulayan WPF sınıfları kategorisi için geçerli olan bir şemsiye terimdir.

Daha fazla bilgi için [Denetimler'e](controls/index.md)bakın.

### <a name="wpf-controls-by-function"></a>Fonksiyona göre WPF kontrolleri

Yerleşik WPF denetimleri burada listelenmiştir:

- **Düğmeler** <xref:System.Windows.Controls.Button> : <xref:System.Windows.Controls.Primitives.RepeatButton>ve .

- **Veri**Ekranı <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.ListView>: <xref:System.Windows.Controls.TreeView>, , ve .

- **Tarih Görüntüleme**ve <xref:System.Windows.Controls.Calendar> <xref:System.Windows.Controls.DatePicker>Seçim : ve .

- **İletişim Kutuları** <xref:Microsoft.Win32.OpenFileDialog>: <xref:System.Windows.Controls.PrintDialog>, <xref:Microsoft.Win32.SaveFileDialog>, ve .

- **Dijital Mürekkep** <xref:System.Windows.Controls.InkCanvas> : <xref:System.Windows.Controls.InkPresenter>ve .

- **Belgeler** <xref:System.Windows.Controls.DocumentViewer>: <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, <xref:System.Windows.Controls.StickyNoteControl>, ve .

- **Giriş**: <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.PasswordBox>, ve .

- **Düzen** <xref:System.Windows.Controls.Border>: <xref:System.Windows.Controls.Primitives.BulletDecorator> <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter> <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator> <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer> <xref:System.Windows.Controls.VirtualizingStackPanel> <xref:System.Windows.Window>, , , <xref:System.Windows.Controls.WrapPanel>, , , , , , , ve . <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.Primitives.Thumb> <xref:System.Windows.Controls.Viewbox>

- **Medya** <xref:System.Windows.Controls.Image>: <xref:System.Windows.Controls.MediaElement>, <xref:System.Windows.Controls.SoundPlayerAction>, ve .

- **Menüler** <xref:System.Windows.Controls.ContextMenu>: <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolBar>, ve .

- **Navigasyon** <xref:System.Windows.Controls.Frame>: <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.TabControl>, ve .

- **Seçim** <xref:System.Windows.Controls.CheckBox>: <xref:System.Windows.Controls.ComboBox> <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.Slider>, ve .

- **Kullanıcı**Bilgileri <xref:System.Windows.Controls.AccessText> <xref:System.Windows.Controls.Label>: <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar> <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.ToolTip>, , , , ve .

## <a name="input-and-commands"></a>Giriş ve komutlar

Denetimler en sık kullanıcı girişini algılar ve bunlara yanıt verir. [WPF giriş sistemi](advanced/input-overview.md) metin girişi, odak yönetimi ve fare konumlandırmasını desteklemek için hem doğrudan hem de yönlendirilmiş olayları kullanır.

Uygulamalar genellikle karmaşık giriş gereksinimlerine sahiptir. WPF, kullanıcı giriş eylemlerini bu eylemlere yanıt veren koddan ayıran bir [komut sistemi](advanced/commanding-overview.md) sağlar.

## <a name="layout"></a>Düzen

Bir kullanıcı arabirimi oluşturduğunuzda, denetimlerinizi bir düzen oluşturmak için konuma ve boyuta göre düzenlersiniz. Herhangi bir düzenin temel gereksinimi, pencere boyutu ve görüntü ayarlarındaki değişikliklere uyum sağlamaktır. WPF, bu koşullarda bir düzeni uyarlamak için kodu yazmaya zorlamak yerine, sizin için birinci sınıf, genişletilebilir bir düzen sistemi sağlar.

Düzen sisteminin temel taşı, değişen pencere ve görüntü koşullarına uyum sağlama yeteneğini artıran göreli konumlandırmadır. Buna ek olarak, düzen sistemi düzeni belirlemek için denetimler arasındaki anlaşma yönetir. Müzakere iki aşamalı bir süreçtir: Birincisi, bir denetim ebeveynine hangi konum ve boyutu gerektirdiğini söyler; ikincisi, üst öğe denetime hangi alana sahip olabileceğini söyler.

Düzen sistemi temel WPF sınıfları aracılığıyla alt denetimlere maruz kalır. Kılavuzlar, istifleme ve yerleştirme gibi yaygın düzenler için WPF birkaç düzen denetimi içerir:

- <xref:System.Windows.Controls.Canvas>: Alt denetimler kendi düzenini sağlar.

- <xref:System.Windows.Controls.DockPanel>: Alt denetimler panelin kenarlarına hizalanır.

- <xref:System.Windows.Controls.Grid>: Alt denetimler satır ve sütunlara göre konumlandırılır.

- <xref:System.Windows.Controls.StackPanel>: Alt denetimler dikey veya yatay olarak istiflenir.

- <xref:System.Windows.Controls.VirtualizingStackPanel>: Alt denetimler sanallaştırılır ve yatay veya dikey olarak yönlendirilmiş tek bir satır üzerinde düzenlenir.

- <xref:System.Windows.Controls.WrapPanel>: Alt kontroller soldan sağa doğru konumlandırılır ve geçerli hatta boşluktan daha fazla kontrol olduğunda bir sonraki satıra sarılır.

Aşağıdaki örnek, <xref:System.Windows.Controls.DockPanel> a'yı <xref:System.Windows.Controls.TextBox> çeşitli denetimleri düzenlemek için kullanır:

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_1.xaml)]

Çocuk <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.TextBox> kontrolleri onları düzenlemek için nasıl söylemek için izin verir. Bunu yapmak için, her `Dock` biri bir dock stili belirtmek için izin vermek için alt denetimleri maruz kalan ekli bir özellik <xref:System.Windows.Controls.DockPanel> uygular.

> [!NOTE]
> Alt denetimler tarafından kullanılmak üzere bir üst denetim tarafından uygulanan bir [özellik, ekli özellik](advanced/attached-properties-overview.md)olarak adlandırılan bir WPF yapısıdır.

Aşağıdaki şekil, önceki örnekte XAML biçimlendirmesinin sonucunu gösterir:

![DockPanel sayfası](media/introduction-to-wpf/wpfintrofigure11.png)

## <a name="data-binding"></a>Veri bağlama

Çoğu uygulama, kullanıcılara verileri görüntüleme ve görüntüleme araçları sağlamak için oluşturulur. WPF uygulamaları için, sql server ve ADO .NET gibi teknolojiler tarafından veri depolama ve bunlara erişim çalışmaları zaten sağlanmıştır. Verilere erişildikten ve bir uygulamanın yönetilen nesnelerine yüklendikten sonra, WPF uygulamaları için zor iş başlar. Esasen, bu iki şey içerir:

1. Yönetilen nesnelerden verileri, verilerin görüntülenebileceği ve düzenlenebileceği denetimlere kopyalama.

2. Denetimler kullanılarak verilerde yapılan değişikliklerin yönetilen nesnelere kopyalanmasını sağlamak.

Uygulama geliştirmeyi kolaylaştırmak için WPF, bu adımları otomatik olarak gerçekleştirmek için bir veri bağlama altyapısı sağlar. Veri bağlama altyapısının temel birimi, işi bir denetimi (bağlayıcı hedef) bir veri nesnesine (bağlayıcı kaynak) bağlamak olan <xref:System.Windows.Data.Binding> sınıftır. Bu ilişki aşağıdaki şekille gösterilmiştir:

![Temel veri bağlama diyagramı](media/introduction-to-wpf/databindingmostbasic.png)

Sonraki örnek, a'nın <xref:System.Windows.Controls.TextBox> özel `Person` bir nesne örneğine nasıl bağlanılmayı gösterir. Uygulama `Person` aşağıdaki kodda gösterilir:

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_2.cs)]

Aşağıdaki biçimlendirme özel <xref:System.Windows.Controls.TextBox> `Person` bir nesnenin bir örneğine bağlanır:

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

Bu örnekte, `Person` sınıf kod arkasında anında ve veri bağlamı olarak `DataBindingWindow`ayarlanır. Biçimlendirmede, <xref:System.Windows.Controls.TextBox.Text%2A> <xref:System.Windows.Controls.TextBox> özelliği `Person.Name` özelliğe bağlıdır (" XAML`{Binding ... }`sözdizimi kullanılarak). Bu XAML, WPF'ye <xref:System.Windows.Controls.TextBox> denetimi `Person` pencerenin <xref:System.Windows.FrameworkElement.DataContext%2A> özelliğinde depolanan nesneye bağlamasını söyler.

WPF veri bağlama altyapısı doğrulama, sıralama, filtreleme ve gruplandırma içeren ek destek sağlar. Ayrıca, standart WPF denetimleri tarafından görüntülenen kullanıcı arabirimi uygun olmadığında, bağlı veriler için özel kullanıcı arabirimi oluşturmak için veri şablonlarının kullanımını destekler.

Daha fazla bilgi için bkz: [Veri bağlama genel bakışı.](../../desktop-wpf/data/data-binding-overview.md)

## <a name="graphics"></a>Grafikler

WPF, aşağıdaki avantajlara sahip kapsamlı, ölçeklenebilir ve esnek grafik özellikleri kümesini sunar:

- **Çözünürlük-bağımsız ve cihazbağımsız grafikler.** WPF grafik sistemindeki temel ölçüm birimi, gerçek ekran çözünürlüğüne bakılmaksızın bir inçin 1/96th'si olan ve çözünürlükten bağımsız ve aygıttan bağımsız görüntülemenin temelini oluşturan aygıttan bağımsız pikseldir. Her aygıttan bağımsız piksel, işlettiginsistemin inç başına nokta (dpi) ayarına uyacak şekilde otomatik olarak ölçeklenir.

- **Geliştirilmiş hassasiyet.** WPF koordinat sistemi, tek hassasiyetli değil, çift duyarlıklı kayan nokta numaralarıyla ölçülür. Dönüşümler ve opaklık değerleri de çift duyarlıklı olarak ifade edilir. WPF ayrıca geniş bir renk gamı (scRGB) destekler ve farklı renk alanlarından girişleri yönetmek için entegre destek sağlar.

- **Gelişmiş grafik ve animasyon desteği.** WPF sizin için animasyon sahneleri yöneterek grafik programlama kolaylaştırır; sahne işleme, döngüoluşturma ve çift doğrusal enterpolasyon konusunda endişelenmenize gerek yoktur. Ayrıca, WPF isabet testi desteği ve tam alfa birleştirme desteği sağlar.

- **Donanım ivmesi.** WPF grafik sistemi, CPU kullanımını en aza indirmek için grafik donanımından yararlanır.

### <a name="2d-shapes"></a>2B şekiller

WPF, aşağıdaki resimde gösterilen dikdörtgenler ve elipsler gibi ortak vektör çizilmiş 2B şekiller kitaplığı sağlar:

![Elipsler ve dikdörtgenler](media/introduction-to-wpf/wpfintrofigure4.PNG)

Şekillerin ilginç bir yeteneği sadece görüntülemek için değil; şekiller, klavye ve fare girişi de dahil olmak üzere denetimlerden beklediğiniz birçok özelliği uygular. Aşağıdaki örnek, <xref:System.Windows.UIElement.MouseUp> bir <xref:System.Windows.Shapes.Ellipse> işlenme olayını gösterir:

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_8.cs)]

Aşağıdaki şekil, önceki kod tarafından nelerin üretildiğini gösterir:

!["Elips&#33; tıkladınız" metninin yer verdiği bir pencere](media/introduction-to-wpf/wpfintrofigure12.png)

Daha fazla bilgi için [WPF'ye genel bakışta Şekiller ve temel çizime](../../desktop-wpf/data/data-binding-overview.md)bakın.

### <a name="2d-geometries"></a>2B geometriler

WPF tarafından sağlanan 2B şekiller standart temel şekil kümesini kapsar. Ancak, özelleştirilmiş bir kullanıcı arabiriminin tasarımını kolaylaştırmak için özel şekiller oluşturmanız gerekebilir. Bu amaçla, WPF geometrisağlar. Aşağıdaki şekil, doğrudan çizilebilen, fırça olarak kullanılabilen veya diğer şekil ve denetimleri kesmek için kullanılabilecek özel bir şekil oluşturmak için geometrilerin kullanımını gösterir.

<xref:System.Windows.Shapes.Path>nesneler kapalı veya açık şekiller, birden çok şekil ve hatta eğri şekiller çizmek için kullanılabilir.

<xref:System.Windows.Media.Geometry>nesneler kırpma, isabet testi ve 2B grafik verilerini işlemek için kullanılabilir.

![Bir yolun çeşitli kullanımları](media/introduction-to-wpf/wpfintrofigure5.png)

Daha fazla bilgi için [Geometri'ye genel bakış](graphics-multimedia/geometry-overview.md)bilgisine bakın.

### <a name="2d-effects"></a>2B efektler

WPF 2D yeteneklerinin bir alt kümesi, degradeler, bit eşlemler, çizimler, videolarla boyama, döndürme, ölçekleme ve eğrilme gibi görsel efektler içerir. Bunların hepsi fırçalarla elde edilir; aşağıdaki şekil bazı örnekler gösterir:

![Farklı fırçaların çizimi](media/introduction-to-wpf/wpfintrofigure6.png)

Daha fazla bilgi için [WPF fırçaları genel bakış](graphics-multimedia/wpf-brushes-overview.md)bakın.

### <a name="3d-rendering"></a>3B işleme

WPF ayrıca daha heyecan verici ve ilginç kullanıcı arabirimleri oluşturulmasına izin vermek için 2B grafik ile entegre 3D render yetenekleri içerir. Örneğin, aşağıdaki şekilde 3B şekiller üzerine işlenen 2B görüntüler gösterilmektedir:

![Visual3D örnek ekran görüntüsü](media/introduction-to-wpf/wpfintrofigure13.png)

Daha fazla bilgi için [3B grafiklere genel bakış](graphics-multimedia/3-d-graphics-overview.md)bakın.

## <a name="animation"></a>Animasyon

WPF animasyon desteği, ilginç sayfa geçişleri ve daha fazlası oluşturmak için denetimlerin büyümesini, titremesini, dönmesini ve solmasını sağlar. Çoğu WPF sınıflarını, hatta özel sınıfları canlandırabilirsiniz. Aşağıdaki şekil, eylem basit bir animasyon gösterir:

![Animasyonlu küpün görüntüleri](media/introduction-to-wpf/wpfintrofigure7.png)

Daha fazla bilgi için [Animasyona genel bakış](graphics-multimedia/animation-overview.md)bilgisine bakın.

## <a name="media"></a>Medya

Zengin içerik iletmek için bir yolu görsel-işitsel medya kullanımı geçer. WPF görüntüler, video ve ses için özel destek sağlar.

### <a name="images"></a>Görüntüler

Görüntüler çoğu uygulamada yaygındır ve WPF bunları kullanmak için çeşitli yollar sağlar. Aşağıdaki şekilde küçük resim görüntüleri içeren bir liste kutusu ile bir kullanıcı arabirimi gösterir. Küçük resim seçildiğinde, görüntü tam boyutlu olarak gösterilir.

![Küçük resim görüntüleri ve tam&#45;boyutunda görüntü](media/introduction-to-wpf/wpfintrofigure8.png)

Daha fazla bilgi için [Görüntüleme genel görünümüne](graphics-multimedia/imaging-overview.md)bakın.

### <a name="video-and-audio"></a>Video ve ses

Denetim <xref:System.Windows.Controls.MediaElement> hem video hem de ses oynatma yeteneğine sahiptir ve özel bir medya oynatıcı için temel olacak kadar esnektir. Aşağıdaki XAML biçimlendirmesi bir ortam oynatıcı uygular:

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_9.xaml)]

Aşağıdaki şekildeki pencere, <xref:System.Windows.Controls.MediaElement> eylem denetimini gösterir:

![Ses ve video ile MediaElement kontrolü](media/introduction-to-wpf/wpfintrofigure1.png)

Daha fazla bilgi için [Grafik ve multimedya](graphics-multimedia/index.md)ya da

## <a name="text-and-typography"></a>Metin ve tipografi

WPF, yüksek kaliteli metin oluşturmayı kolaylaştırmak için aşağıdaki özellikleri sunar:

- OpenType yazı tipi desteği.

- ClearType geliştirmeleri.

- Donanım ivmesi avantajlarından yararlanan yüksek performans.

- Metnin medya, grafik ve animasyonla bütünleştirilmesi.

- Uluslararası yazı tipi desteği ve geri dönüş mekanizmaları.

Grafikile metin entegrasyonunun bir göstergesi olarak, aşağıdaki şekil metin süslemeleri uygulamasını gösterir:

![Çeşitli metin süslemeleri ile Metin](media/introduction-to-wpf/wpfintrofigure23.png)

Daha fazla bilgi için [Windows Presentation Foundation'da Tipografi'ye](advanced/typography-in-wpf.md)bakın.

## <a name="customize-wpf-apps"></a>WPF uygulamalarını özelleştirin

Bu noktaya kadar, uygulamaları geliştirmek için temel WPF yapı taşlarını gördünüz. Uygulama modelini, çoğunlukla denetimlerden oluşan uygulama içeriğini barındırmak ve sunmak için kullanırsınız. Kullanıcı arabirimindeki denetimlerin düzenlenmesini kolaylaştırmak ve düzenlemenin pencere boyutu ve ekran ayarlarındaki değişiklikler karşısında tutulmasını sağlamak için WPF düzen sistemini kullanırsınız. Çoğu uygulama kullanıcıların verilerle etkileşimkurmasına izin verdiğinden, kullanıcı arabiriminizi verilerle tümleştirme işini azaltmak için veri bağlamayı kullanırsınız. Uygulamanızın görsel görünümünü geliştirmek için WPF tarafından sağlanan kapsamlı grafik, animasyon ve ortam desteğini kullanırsınız.

Çoğu zaman, ancak, temel oluşturma ve gerçekten farklı ve görsel olarak çarpıcı kullanıcı deneyimi yönetmek için yeterli değildir. Standart WPF denetimleri uygulamanızın istenen görünümüyle bütünleşmeyebilir. Veriler en etkili şekilde görüntülenmeyebilir. Uygulamanızın genel kullanıcı deneyimi, Windows temalarının varsayılan görünümüne ve hissine uygun olmayabilir. Birçok yönden, bir sunum teknolojisi kadar genişletilebilirlik diğer tür olarak görsel genişletilebilirlik gerekir.

Bu nedenle WPF, denetimler, tetikleyiciler, denetim ve veri şablonları, stiller, kullanıcı arabirimi kaynakları ve temalar ve görünümler için zengin bir içerik modeli de dahil olmak üzere benzersiz kullanıcı deneyimleri oluşturmak için çeşitli mekanizmalar sağlar.

### <a name="content-model"></a>İçerik modeli

WPF denetimlerinin çoğunluğunun temel amacı içeriği görüntülemektir. WPF'de, denetimin içeriğini oluşturabilecek öğelerin türü ve sayısı denetimin *içerik modeli*olarak adlandırılır. Bazı denetimler tek bir öğe ve içerik türü içerebilir; örneğin, a <xref:System.Windows.Controls.TextBox> içeriği <xref:System.Windows.Controls.TextBox.Text%2A> özelliğine atanan bir dize değeridir. Aşağıdaki örnekte bir <xref:System.Windows.Controls.TextBox>içeriği n

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

Aşağıdaki şekil sonucu gösterir:

![Metin içeren textbox denetimi](media/introduction-to-wpf/wpfintrofigure21.png)

Ancak diğer denetimler, farklı içerik türlerinde birden çok öğe içerebilir; özellik tarafından <xref:System.Windows.Controls.Button>belirtilen bir içeriğin içeriği, düzen denetimleri, metin, resim ve şekiller de dahil olmak üzere çeşitli öğeler içerebilir. <xref:System.Windows.Controls.ContentControl.Content%2A> Aşağıdaki örnek, <xref:System.Windows.Controls.Button> a , a <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Border>a ve <xref:System.Windows.Controls.MediaElement>a içeren içerikli bir

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

Aşağıdaki şekil bu düğmenin içeriğini gösterir:

![Birden çok içerik türü içeren bir düğme](media/introduction-to-wpf/wpfintrofigure22.png)

Çeşitli denetimler tarafından desteklenen içerik türleri hakkında daha fazla bilgi için [WPF içerik modeline](controls/wpf-content-model.md)bakın.

### <a name="triggers"></a>Tetikleyiciler

XAML biçimlendirmesinin temel amacı bir uygulamanın görünümünü uygulamak olsa da, bir uygulamanın davranışının bazı yönlerini uygulamak için XAML'yi de kullanabilirsiniz. Bir örnek, kullanıcı etkileşimlerine dayalı olarak bir uygulamanın görünümünü değiştirmek için tetikleyicilerin kullanılmasıdır. Daha fazla bilgi için [Stiller ve şablonlara](../../desktop-wpf/fundamentals/styles-templates-overview.md)bakın.

### <a name="control-templates"></a>Denetim şablonları

WPF denetimleri için varsayılan kullanıcı arabirimleri genellikle diğer denetimlerden ve şekillerden oluşturulur. Örneğin, a <xref:System.Windows.Controls.Button> hem de <xref:Microsoft.Windows.Themes.ButtonChrome> <xref:System.Windows.Controls.ContentPresenter> denetimlerden oluşur. Standart <xref:Microsoft.Windows.Themes.ButtonChrome> düğme görünümü sağlarken, <xref:System.Windows.Controls.ContentPresenter> özellik tarafından <xref:System.Windows.Controls.ContentControl.Content%2A> belirtildiği gibi düğmenin içeriğini görüntüler.

Bazen denetimin varsayılan görünümü, bir uygulamanın genel görünümüyle uyumsuz olabilir. Bu durumda, a'yı, <xref:System.Windows.Controls.ControlTemplate> içeriğini ve davranışını değiştirmeden denetimin kullanıcı arabiriminin görünümünü değiştirmek için kullanabilirsiniz.

Aşağıdaki örnek, bir <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate>aşağıdakileri kullanarak görünümün nasıl değiştirilebildiğini gösterir:

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_17.vb)]

Bu örnekte, varsayılan düğme kullanıcı arabirimi <xref:System.Windows.Shapes.Ellipse> koyu mavi kenarlık lı bir <xref:System.Windows.Media.RadialGradientBrush>ile değiştirildi ve bir . <xref:System.Windows.Controls.Button>Denetim, <xref:System.Windows.Controls.ContentPresenter> "Beni tıklatın!" içeriğini görüntüler. <xref:System.Windows.Controls.Button> Tıklatıldığında, olay denetimin <xref:System.Windows.Controls.Primitives.ButtonBase.Click> varsayılan davranışının <xref:System.Windows.Controls.Button> bir parçası olarak yine de yükseltilir. Sonuç aşağıdaki şekilde gösterilmiştir:

![Bir eliptik düğme ve ikinci bir pencere](media/introduction-to-wpf/wpfintrofigure2.png)

### <a name="data-templates"></a>Veri şablonları

Denetim şablonu denetimin görünümünü belirtmenize olanak sağlarken, veri şablonu denetimin içeriğinin görünümünü belirtmenize olanak tanır. Veri şablonları, bağlı verilerin nasıl görüntüleneceğini geliştirmek için sık sık kullanılır. Aşağıdaki şekil, her görevin <xref:System.Windows.Controls.ListBox> `Task` bir adı, açıklaması ve önceliği olan nesneler koleksiyonuna bağlı bir nesne için varsayılan görünümü gösterir:

![Varsayılan görünüme sahip bir liste kutusu](media/introduction-to-wpf/wpfintrofigure18.png)

Varsayılan görünüm, bir <xref:System.Windows.Controls.ListBox>.'den beklediğiniz şeydir. Ancak, her görevin varsayılan görünümü yalnızca görev adını içerir. Görev adını, açıklamayı ve önceliği göstermek için, <xref:System.Windows.Controls.ListBox> denetimin bağlı liste öğelerinin varsayılan <xref:System.Windows.DataTemplate>görünümünün bir . Aşağıdaki XAML, özniteliği <xref:System.Windows.DataTemplate>kullanarak <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> her göreve uygulanan böyle bir , tanımlar:

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

Aşağıdaki şekil bu kodun etkisini gösterir:

![Veri şablonu kullanan liste kutusu](media/introduction-to-wpf/wpfintrofigure19.png)

Davranışının <xref:System.Windows.Controls.ListBox> ve genel görünümünükoruduğunu unutmayın; yalnızca liste kutusu tarafından görüntülenen içeriğin görünümü değişti.

Daha fazla bilgi için [bkz.](data/data-templating-overview.md)

### <a name="styles"></a>Stiller

Stiller, geliştiricilerin ve tasarımcıların ürünleri için belirli bir görünümde standartlaştırmalarını sağlar. WPF, temeli <xref:System.Windows.Style> öğe olan güçlü bir stil modeli sağlar. Aşağıdaki örnek, penceredeki her biri <xref:System.Windows.Controls.Button> için arka plan `Orange`rengini aşağıdakilere ayarlayan bir stil oluşturur:

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

Bu stil tüm <xref:System.Windows.Controls.Button> denetimleri hedeflediğinden, stil aşağıdaki şekilde gösterildiği gibi penceredeki tüm düğmelere otomatik olarak uygulanır:

![İki turuncu düğme](media/introduction-to-wpf/wpfintrofigure20.png)

Daha fazla bilgi için [Stiller ve şablonlara](../../desktop-wpf/fundamentals/styles-templates-overview.md)bakın.

### <a name="resources"></a>Kaynaklar

Bir uygulamadaki denetimler, yazı tiplerinden arka plan renklerinden şablonları, veri şablonlarını ve stilleri denetlemeye kadar her şeyi içerebilen aynı görünümü paylaşmalıdır. WPF'nin kullanıcı arabirimi kaynakları için desteğini kullanarak bu kaynakları yeniden kullanmak üzere tek bir konumda saklayabilirsiniz.

Aşağıdaki örnek, a ve a <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Label>tarafından paylaşılan ortak bir arka plan rengini tanımlar:

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

Bu örnek, özellik öğesini `Window.Resources` kullanarak bir arka plan renk kaynağı uygular. Bu kaynak tüm çocuklar için <xref:System.Windows.Window>kullanılabilir. Çözümlenme sırasına göre listelenen aşağıdakiler de dahil olmak üzere çeşitli kaynak kapsamları vardır:

1. Bireysel denetim (devralınan <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> özelliği kullanarak).

2. A <xref:System.Windows.Window> veya <xref:System.Windows.Controls.Page> a (ayrıca <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> devralınan özelliği kullanarak).

3. Bir <xref:System.Windows.Application> <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> (özelliği kullanarak).

Kapsamların çeşitliliği, kaynaklarınızı tanımlama ve paylaşma biçiminize göre esneklik sağlar.

Kaynaklarınızı belirli bir kapsamla doğrudan ilişkilendirmeye alternatif olarak, bir uygulamanın diğer <xref:System.Windows.ResourceDictionary> bölümlerinde başvurulabilecek ayrı bir kaynak kullanarak bir veya daha fazla kaynağı paketleyebilirsiniz. Örneğin, aşağıdaki örnek, kaynak sözlüğünde varsayılan arka plan rengini tanımlar:

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

Aşağıdaki örnek, bir uygulama arasında paylaşılabilmek için önceki örnekte tanımlanan kaynak sözlüğüne başvurur:

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

Kaynaklar ve kaynak sözlükleri temalar ve görünümler için WPF desteğinin temelidir.

Daha fazla bilgi için [Kaynaklar'a](../../desktop-wpf/fundamentals/xaml-resources-define.md)bakın.

### <a name="custom-controls"></a>Özel denetimler

WPF bir dizi özelleştirme desteği sağlasa da, varolan WPF denetimlerinin uygulamanızın veya kullanıcılarının gereksinimlerini karşılamadığı durumlarla karşılaşabilirsiniz. Bu, şu anda oluşabilir:

- Gereksinim duyduğunuz kullanıcı arabirimi, varolan WPF uygulamalarının görünümünü ve hissini özelleştirerek oluşturulamaz.

- Gereksinim duyduğunuz davranış, varolan WPF uygulamaları tarafından desteklenmez (veya kolayca desteklenmez).

Ancak bu noktada, yeni bir denetim oluşturmak için üç WPF modelinden birinden yararlanabilirsiniz. Her model belirli bir senaryoyu hedefler ve belirli bir WPF taban sınıfından türeyen özel denetiminizin gerekli olmasını gerektirir. Üç model burada listelenmiştir:

- **Kullanıcı Kontrol Modeli**. Özel denetim, bir <xref:System.Windows.Controls.UserControl> veya daha fazla denetimden kaynaklanır ve bu denetimlerden oluşur.

- **Kontrol Modeli**. Özel denetim, WPF <xref:System.Windows.Controls.Control> denetimlerinin çoğu gibi şablonları kullanarak davranışlarını görünümlerinden ayıran uygulamalardan kaynaklanır ve oluşturmak için kullanılır. Türeyen <xref:System.Windows.Controls.Control> kaynak, kullanıcı denetimlerinden daha özel bir kullanıcı arabirimi oluşturmanıza daha fazla özgürlük sağlar, ancak daha fazla çaba gerektirebilir.

- **Çerçeve Öğesi Modeli**. Özel denetim, görünümünün <xref:System.Windows.FrameworkElement> özel işleme mantığıyla (şablonlar değil) tanımlandığından kaynaklanır.

Aşağıdaki örnek, aşağıdakilerden <xref:System.Windows.Controls.UserControl>türeyen özel bir sayısal yukarı/aşağı denetimi gösterir:

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_34.vb)]

Aşağıdaki örnek, kullanıcı denetimini aşağıdaki <xref:System.Windows.Window>lere dahil etmek için gereken XAML'yi göstermektedir:

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_37.xaml)]

Aşağıdaki şekilde barındırılan `NumericUpDown` denetim <xref:System.Windows.Window>gösterir:

![Özel Bir UserControl](media/introduction-to-wpf/wpfintrofigure3.png)

Özel denetimler hakkında daha fazla bilgi için [bkz.](controls/control-authoring-overview.md)

## <a name="wpf-best-practices"></a>WPF en iyi uygulamaları

Herhangi bir geliştirme platformunda olduğu gibi, WPF istenilen sonucu elde etmek için çeşitli şekillerde kullanılabilir. WPF uygulamalarınızın gerekli kullanıcı deneyimini sağlamasını ve genel olarak hedef kitlenin taleplerini karşılamasını sağlamanın bir yolu olarak, erişilebilirlik, küreselleşme ve yerelleştirme ve performans için önerilen en iyi uygulamalar vardır. Daha fazla bilgi için bkz.

- [Erişilebilirlik](../ui-automation/accessibility-best-practices.md)
- [WPF küreselleşmeve yerelleştirme](advanced/wpf-globalization-and-localization-overview.md)
- [WPF uygulama performansı](advanced/optimizing-wpf-application-performance.md)
- [WPF güvenliği](security-wpf.md)

## <a name="next-steps"></a>Sonraki adımlar

WPF'nin temel özelliklerine baktık. Şimdi ilk WPF uygulamanızı oluşturma zamanı.

> [!div class="nextstepaction"]
> [Walkthrough: İlk WPF masaüstü uygulamam](getting-started/walkthrough-my-first-wpf-desktop-application.md)

## <a name="see-also"></a>Ayrıca bkz.

- [WPF kullanmaya başlama](getting-started/index.md)
- [Windows Presentation Foundation](index.md)
- [WPF topluluk kaynakları](getting-started/community-feedback.md)
