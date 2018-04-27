---
title: Visual Studio'da WPF uygulaması oluşturma
ms.custom: 04/12/2018
ms.prod: .net-framework
ms.technology: dotnet-wpf
ms.topic: conceptual
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: edc7a22a7b108731e08c5d67ef8b8a52e9959ddc
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>İzlenecek yol: İlk WPF Masaüstü Uygulamam

Bu makalede, çoğu WPF uygulamaları için ortak olan öğeleri içeren basit bir Windows Presentation Foundation (WPF) uygulama geliştirmek gösterilmiştir: Genişletilebilir uygulama biçimlendirme dili (XAML) işaretleme, arka plan kodu, uygulama tanımları denetimleri, düzeni, veri bağlama ve stiller.

Bu izlenecek yol aşağıdaki adımları içerir:

- Uygulamanın kullanıcı arabirimini (UI) görünümünü tasarlamak için XAML kullanın.

- Uygulamanın davranışını oluşturmak için kod yazma.

- Uygulamasını yönetmek için uygulama tanımı oluşturun.

- Denetimler ekleme ve uygulama kullanıcı Arabirimi oluşturmak için bir düzen oluşturur.

- Bir uygulamanın UI genelinde tutarlı bir görünüm için stiller oluşturun.

- Kullanıcı arabirimini verilerden UI doldurmak hem UI eşitlenmiş ve verileri korumak için verilere bağlayın.

İzlenecek yol ucu tarafından tek başına kullanıcıların seçilen kişiler için harcama raporlarını görüntülemesine olanak sağlayan Windows uygulaması hazırladığınız. Uygulaması bir tarayıcı stili pencerede barındırılan birkaç WPF sayfaların oluşur.

> [!TIP]
> Bu izlenecek yolu oluşturmak için kullanılan örnek kod hem Visual Basic ve C# için kullanılabilir [WPF uygulamalarını giriş](http://go.microsoft.com/fwlink/?LinkID=160008).

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio 2012 veya üzeri

Visual Studio en son sürümünü yükleme hakkında daha fazla bilgi için bkz: [Visual Studio yükleme](/visualstudio/install/install-visual-studio).

## <a name="create-the-application-project"></a>Uygulama projesi oluşturun

İlk adım, uygulama tanımı, iki sayfaları ve görüntü içeren uygulama altyapısı oluşturmaktır.

1. Visual Basic veya Visual C# adlı yeni bir WPF uygulaması projesi oluşturduğunuzda **ExpenseIt**:

   1. Visual Studio'yu açın ve seçin **dosya** > **yeni** > **proje**.

      **Yeni proje** iletişim kutusunu açar.

   2. Altında **yüklü** kategorisini genişletin **Visual C#** veya **Visual Basic** düğümünü ve ardından **Windows Klasik Masaüstü**.

   3. Seçin **WPF uygulaması (.NET Framework)** şablonu. Bir ad girin **ExpenseIt** ve ardından **Tamam**.

      ![Seçili WPF uygulaması ile yeni proje iletişim kutusu](media/new-project-dialog.png)

      Visual Studio projesi oluşturur ve tasarımcı adlı varsayılan uygulama penceresi açar **MainWindow.xaml**.

   > [!NOTE]
   > Bu kılavuzda kullanılır <xref:System.Windows.Controls.DataGrid> kullanılabilir .NET Framework 4 ve üzeri denetim. Sonraki veya projeniz .NET Framework 4 hedefleyen emin olun. Daha fazla bilgi için bkz: [nasıl yapılır: .NET Framework sürümü hedef](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

2. Açık *Application.xaml* (Visual Basic) veya *App.xaml* (C#).

    Bu XAML dosyası WPF uygulaması ve uygulama kaynaklarını tanımlar. Bu dosyayı otomatik olarak ne zaman gösterir UI belirtmek için de uygulamayı başlatır; Bu durumda, *MainWindow.xaml*.

    Visual Basic'te XAML aşağıdaki gibi görünmelidir:

    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    Ya da böyle C#:

    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. Açık *MainWindow.xaml*.

    Bu XAML dosyası, uygulamanızın ana penceresidir ve sayfalarda oluşturulan içeriği görüntüler. <xref:System.Windows.Window> Sınıfı başlık, boyut veya simge, gibi bir pencere özelliklerini tanımlar ve kapatma veya gizleme gibi olayları işler.

4. Değişiklik <xref:System.Windows.Window> öğesine bir <xref:System.Windows.Navigation.NavigationWindow>aşağıdaki XAML'de gösterildiği gibi:

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   Bu uygulama için kullanıcı girişi bağlı olarak farklı içeriğe götürür. Nedeni budur ana <xref:System.Windows.Window> için değiştirilmesi gereken bir <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow> tüm özelliklerini devralır <xref:System.Windows.Window>. <xref:System.Windows.Navigation.NavigationWindow> XAML dosyası öğesinde bir örneğini oluşturur <xref:System.Windows.Navigation.NavigationWindow> sınıfı. Daha fazla bilgi için bkz: [Gezinti genel bakış](../../../../docs/framework/wpf/app-development/navigation-overview.md).

5. Aşağıdaki özellikleri değiştirin <xref:System.Windows.Navigation.NavigationWindow> öğe:

    - Ayarlama <xref:System.Windows.Window.Title%2A> özelliğini "ExpenseIt".

    - Ayarlama <xref:System.Windows.FrameworkElement.Width%2A> özelliğini 500 piksel.

    - Ayarlama <xref:System.Windows.FrameworkElement.Height%2A> özelliğini 350 piksel.

    - Kaldırma <xref:System.Windows.Controls.Grid> öğeleri arasında <xref:System.Windows.Navigation.NavigationWindow> etiketler.

    Visual Basic'te XAML aşağıdaki gibi görünmelidir:

    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    Ya da böyle C#:

    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

6. Açık *MainWindow.xaml.vb* veya *MainWindow.xaml.cs*.

    Bu dosya bildirilen olayları işlemek için kod içeren bir arka plan kodu dosyasıdır *MainWindow.xaml*. Bu dosya XAML içinde tanımlanan penceresi için bir parçalı sınıf içerir.

7. C# kullanıyorsanız değiştirme `MainWindow` öğesinden türetilen sınıf <xref:System.Windows.Navigation.NavigationWindow>. (XAML penceresinde değiştirdiğinizde, Visual Basic'te, bu otomatik olarak gerçekleşir.)

   Kodunuzu aşağıdaki gibi görünmelidir:

   [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
   [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]

   > [!TIP]
   > C# ve Visual Basic'te arasında yer alan örnek kodunu kod dili Değiştir **dil** bu makalenin üst sağ taraftaki açılır.

## <a name="add-files-to-the-application"></a>Uygulama dosyaları ekleme

Bu bölümde, uygulama için iki sayfaları ve görüntü ekleyeceksiniz.

1. Yeni bir WPF sayfası projeye ekleyin ve adını *ExpenseItHome.XAML*:

   1. İçinde **Çözüm Gezgini**, sağ tıklayın **ExpenseIt** proje düğümünü ve seçin **Ekle** > **sayfa**.

   1. İçinde **Yeni Öğe Ekle** iletişim kutusunda, **sayfa (WPF)** şablon zaten seçilmiş. Bir ad girin **ExpenseItHome**ve ardından **Ekle**.

    Uygulama başlatıldığında görüntülenen ilk sayfa sayfasıdır. Kişiler için harcama raporunu göstermek için arasından seçim listesi gösterilir.

2. Açık *ExpenseItHome.XAML*.

3. Ayarlama <xref:System.Windows.Controls.Page.Title%2A> "ExpenseIt - Giriş".

    Visual Basic'te XAML aşağıdaki gibi görünmelidir:

    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    Veya bu C#:

    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

4. Açık *MainWindow.xaml*.

5. Ayarlama <xref:System.Windows.Navigation.NavigationWindow.Source%2A> özellikte <xref:System.Windows.Navigation.NavigationWindow> "ExpenseItHome.xaml" için.

    Bu ayarlar *ExpenseItHome.XAML* ilk sayfa olarak uygulama başladığında açılır. Visual Basic'te XAML aşağıdaki gibi görünmelidir:

    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    Veya bu C#:

    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Ayrıca ayarlayabilirsiniz **kaynak** özelliğinde **çeşitli** kategorisini **özellikleri** penceresi.
   >
   > ![Özellikleri penceresinde kaynak özelliği](media/properties-source.png)

6. Başka bir yeni WPF sayfası projeye ekleyin ve adını *ExpenseReportPage.xaml*::

   1. İçinde **Çözüm Gezgini**, sağ tıklayın **ExpenseIt** proje düğümünü ve seçin **Ekle** > **sayfa**.

   1. İçinde **Yeni Öğe Ekle** iletişim kutusunda, **sayfa (WPF)** şablon zaten seçilmiş. Bir ad girin **ExpenseReportPage**ve ardından **Ekle**.

    Bu sayfada seçili kişi için harcama raporunu gösterilir **ExpenseItHome** sayfası.

7. Açık *ExpenseReportPage.xaml*.

8. Ayarlama <xref:System.Windows.Controls.Page.Title%2A> "ExpenseIt - görünüm gider".

    Visual Basic'te XAML aşağıdaki gibi görünmelidir:

    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    Veya bu C#:

    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

9. Açık *ExpenseItHome.xaml.vb* ve *ExpenseReportPage.xaml.vb*, veya *ExpenseItHome.xaml.cs* ve *ExpenseReportPage.xaml.cs*.

    Yeni bir sayfa dosyası oluşturduğunuzda, Visual Studio otomatik olarak oluşturur bir *arka plan kodu* dosya. Bu arka plan kodu dosyaları için kullanıcı girişine yanıt mantığını işler.

    Kodunuz için şuna benzer görünmelidir **ExpenseItHome**:

    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    Ve bu gibi **ExpenseReport**:

    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

10. Adlı bir resim ekleyin *watermark.png* projeye. Kendi görüntünüzü oluşturabilir, dosyanın örnek kodu kopyalayabilir veya alın [burada](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/media/watermark.png).

   1. Proje düğümüne sağ tıklatıp **Ekle** > **varolan öğeyi**, veya basın **Shift**+**Alt** + **A**.

   2. İçinde **varolan öğeyi Ekle** iletişim kutusunda, kullanın ve ardından istediğiniz görüntü dosyasına Gözat **Ekle**.

## <a name="build-and-run-the-application"></a>Derleme ve uygulamayı çalıştırma

1. Derleme ve uygulamayı çalıştırmak için basın **F5** veya seçin **hata ayıklamayı Başlat** gelen **hata ayıklama** menüsü.

    Uygulamayla birlikte aşağıda gösterilmiştir <xref:System.Windows.Navigation.NavigationWindow> düğmeleri:

    ![ExpenseIt örnek ekran görüntüsü](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png)

2. Visual Studio'ya dönmek için uygulamayı kapatın.

## <a name="create-the-layout"></a>Düzeni oluşturma

Düzen kullanıcı Arabirimi öğeleri yerleştirmek için sıralı bir yol sağlar ve bir kullanıcı Arabirimi yeniden boyutlandırıldığında boyutunu ve konumunu bu öğelerin da yönetir. Genellikle bir düzen aşağıdaki düzen denetimlerinden biri ile oluşturursunuz:

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.VirtualizingStackPanel>
- <xref:System.Windows.Controls.WrapPanel>

Bu düzen denetimlerinin her biri kendi alt öğeleri için özel türde bir düzen destekler. ExpenseIt sayfaları yeniden boyutlandırılabilir ve her sayfanın diğer öğeleri yatay ve dikey olarak düzenlenmiş öğesine sahip. Sonuç olarak, <xref:System.Windows.Controls.Grid> uygulama için ideal Düzen öğesidir.

> [!TIP]
> Hakkında daha fazla bilgi için <xref:System.Windows.Controls.Panel> öğeler, bkz [paneller genel bakış](../../../../docs/framework/wpf/controls/panels-overview.md). Düzen hakkında daha fazla bilgi için bkz: [düzeni](../../../../docs/framework/wpf/advanced/layout.md).

Bölümünde, tek sütunlu bir tablo üç satır ve 10 piksel kenar boşluğu ile sütun ve satır tanımları ekleyerek oluşturduğunuz <xref:System.Windows.Controls.Grid> içinde *ExpenseItHome.XAML*.

1. Açık *ExpenseItHome.XAML*.

2. Ayarlama <xref:System.Windows.FrameworkElement.Margin%2A> özellikte <xref:System.Windows.Controls.Grid> ", sol, üst, sağ ve alt kenar boşlukları için karşılık gelen 10,0,10,10"şeklinde, öğe:

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Ayrıca ayarlayabilirsiniz **kenar boşluğu** değerler **özellikleri** penceresi altında **düzeni** Kategori:
   >
   > ![Özellikler penceresi kenar değerlerde](media/properties-margin.png)

3. Aşağıdaki XAML'i ekleyin <xref:System.Windows.Controls.Grid> etiketleri satır ve sütun tanımları oluşturmak için:

    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <xref:System.Windows.Controls.RowDefinition.Height%2A> İki satır kümesine <xref:System.Windows.GridLength.Auto%2A>, satırları boyutlandırılır anlamına temel satırları içerikte. Varsayılan <xref:System.Windows.Controls.RowDefinition.Height%2A> olan <xref:System.Windows.GridUnitType.Star> satır yüksekliğini kullanılabilir alan ağırlıklı bir kısmının anlamına gelir boyutlandırma. Her iki satır varsa, örneğin bir <xref:System.Windows.Controls.RowDefinition.Height%2A> , "*", kullanılabilir alanı yarısıdır yükseklik sahip oldukları her.

    <xref:System.Windows.Controls.Grid> Aşağıdaki XAML gibi görünmelidir:

    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Denetimler ekleme

Bu bölümde, bir kullanıcı için harcama raporunu göstermek için seçebilirsiniz kişilerin listesini göstermek için kullanıcı Arabirimi giriş sayfasını güncelleştirmeniz. Denetimler uygulamanız ile etkileşime girmesine izin veren UI nesneleridir. Daha fazla bilgi için bkz: [denetimleri](../../../../docs/framework/wpf/controls/index.md).

Bu kullanıcı Arabirimi oluşturmak için aşağıdaki öğeleri ekleyeceksiniz *ExpenseItHome.XAML*:

- <xref:System.Windows.Controls.ListBox> (listesi kişiler için).
- <xref:System.Windows.Controls.Label> (Liste üstbilgisi için).
- <xref:System.Windows.Controls.Button> (listede seçilen kişi için harcama raporunu görüntülemek için tıklatın için).

Her denetim bir satırda yerleştirilir <xref:System.Windows.Controls.Grid> ayarlayarak <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> özelliği eklenmiş. Ekli özellikler hakkında daha fazla bilgi için bkz: [bağlı özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).

1. Açık *ExpenseItHome.XAML*.

2. Aşağıdaki XAML'i yere ekleyin <xref:System.Windows.Controls.Grid> etiketler:

   [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Sürükleyerek denetimleri oluşturabilirsiniz **araç** tasarım penceresini ve bunların özelliklerini ayarlama penceresinden **özellikleri** penceresi.

3. Derleme ve uygulamayı çalıştırın.

Aşağıdaki resimde, az önce oluşturduğunuz denetimleri gösterilmektedir:

![ExpenseIt örnek ekran görüntüsü](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png)

## <a name="add-an-image-and-a-title"></a>Görüntüyü ve başlık ekleme

Bu bölümde, giriş sayfası kullanıcı Arabirimi bir görüntü ve sayfa başlığını güncelleştirin.

1. Açık *ExpenseItHome.XAML*.

2. Başka bir sütuna eklemek <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> bir sabit ile <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 piksel:

    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]

3. Başka bir satır ekleyin <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, dört satır toplam için:

    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]

4. Denetimleri ayarlayarak ikinci sütun taşımak <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> özelliği 1 her üç denetimleri (Kenarlık, ListBox ve düğmesi).

5. Her denetim artırılarak bir satır aşağı taşı kendi <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> değeri 1.

   XAML üç denetimleri için şimdi şöyle görünür:

    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

6. Ayarlama <xref:System.Windows.Controls.Panel.Background%2A> , <xref:System.Windows.Controls.Grid> olmasını *watermark.png* aşağıdaki XAML yere arasında ekleyerek resim dosyası `<Grid>` ve `<\/Grid>` etiketler:

    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

7. Önce <xref:System.Windows.Controls.Border> öğesi ekleme bir <xref:System.Windows.Controls.Label> "Gider raporu görüntüle" içeriğe sahip. Bu sayfa başlığıdır.

    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

8. Derleme ve uygulamayı çalıştırın.

Aşağıdaki çizimde ne eklemiş sonuçlarını gösterir:

![ExpenseIt örnek ekran görüntüsü](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png)

## <a name="add-code-to-handle-events"></a>Olayları işlemek için kod ekleme

1. Açık *ExpenseItHome.XAML*.

2. Ekleme bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisine <xref:System.Windows.Controls.Button> öğesi. Daha fazla bilgi için bkz: [nasıl yapılır: Basit olay işleyicisi oluşturun](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).

    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

3. Açık *ExpenseItHome.xaml.vb* veya *ExpenseItHome.xaml.cs*.

4. Aşağıdaki kodu ekleyin `ExpenseItHome` düğme eklemek için sınıfı olay işleyicisi'ı tıklatın. Olay işleyicisi açılır **ExpenseReportPage** sayfası.

    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>ExpenseReportPage için kullanıcı Arabirimi oluşturma

*ExpenseReportPage.xaml* seçili kişi için harcama raporunu görüntüler **ExpenseItHome** sayfası. Bu bölümde denetimleri gerekir ve ilişkin kullanıcı Arabirimi oluşturma **ExpenseReportPage**. Ayrıca, arka plan ekleyebilir ve Dolgu renkleri çeşitli kullanıcı Arabirimi öğeleri için.

1. Açık *ExpenseReportPage.xaml*.

2. Aşağıdaki XAML'i ekleyin <xref:System.Windows.Controls.Grid> etiketler:

    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Bu UI benzer *ExpenseItHome.XAML*, rapor verilerini görüntülenen dışında bir <xref:System.Windows.Controls.DataGrid>.

3. Derleme ve uygulamayı çalıştırın.

    > [!NOTE]
    > Bir hata alırsanız <xref:System.Windows.Controls.DataGrid> bulunamadı veya olmayabilir, projeniz .NET Framework 4 veya sonrasını hedefleyen emin olun. Daha fazla bilgi için bkz: [nasıl yapılır: .NET Framework sürümü hedef](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

4. Seçin **Görünüm** düğmesi.

    Harcama Raporu sayfası görüntülenir. Ayrıca geri gezinti düğmesi etkinleştirilir dikkat edin.

Eklenen kullanıcı Arabirimi öğeleri aşağıda gösterilmiştir *ExpenseReportPage.xaml*.

![ExpenseIt örnek ekran görüntüsü](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png)

## <a name="style-controls"></a>Stili denetimleri

Çeşitli öğelerin görünümü genellikle bir kullanıcı arabiriminde aynı türden tüm öğeler için aynıdır. UI kullanan [stilleri](../../../../docs/framework/wpf/controls/styling-and-templating.md) görünümlerin çoklu öğeler arasında yeniden kullanılabilir olması için. Kullanılırlığı XAML oluşturulmasını ve yönetimini basitleştirmeye yardımcı olur. Bu bölümde stilleri önceki adımlarda tanımlanan öğesi başına özniteliklerini değiştirir.

1. Açık *Application.xaml* veya *App.xaml*.

2. Aşağıdaki XAML'i ekleyin <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> etiketler:

    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Bu XAML aşağıdaki stilleri ekler:

    - `headerTextStyle`: Sayfa başlığı Biçimlendirilecek <xref:System.Windows.Controls.Label>.

    - `labelStyle`: Biçimlendirilecek <xref:System.Windows.Controls.Label> kontrol eder.

    - `columnHeaderStyle`: Biçimlendirilecek <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.

    - `listHeaderStyle`: List üstbilgisi Biçimlendirilecek <xref:System.Windows.Controls.Border> kontrol eder.

    - `listHeaderTextStyle`: List üstbilgisi Biçimlendirilecek <xref:System.Windows.Controls.Label>.

    - `buttonStyle`: Biçimlendirilecek <xref:System.Windows.Controls.Button> ExpenseItHome.XAML üzerinde.

    Stilleri kaynakları ve alt öğeleri olduğuna dikkat edin <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> özellik öğesi. Bu konumda stiller tüm öğelere uygulanır. Bir .NET Framework uygulamasında kaynaklarını kullanan bir örnek için bkz: [kullanım uygulama kaynakları](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).

3. Açık *ExpenseItHome.XAML*.

4. Arasındaki her şeyi değiştirin <xref:System.Windows.Controls.Grid> aşağıdaki XAML ile öğeleri:

    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    Gibi özellikler <xref:System.Windows.VerticalAlignment> ve <xref:System.Windows.Media.FontFamily> her denetimin görünümünü tanımlamak kaldırılır ve stiller uygulayarak değiştirilir. Örneğin, `headerTextStyle` harcama raporu görünümü"için" uygulanan <xref:System.Windows.Controls.Label>.

5. Açık *ExpenseReportPage.xaml*.

6. Arasındaki her şeyi değiştirin <xref:System.Windows.Controls.Grid> aşağıdaki XAML ile öğeleri:

    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Bu stiller ekler <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.Border> öğeleri.

## <a name="bind-data-to-a-control"></a>Bir denetimine veri bağlama

Bu bölümde, çeşitli denetimlere bağlı XML verileri oluşturacaksınız.

1. Açık *ExpenseItHome.XAML*.

2. Açtıktan sonra <xref:System.Windows.Controls.Grid> öğesi oluşturmak için aşağıdaki XAML eklemek bir <xref:System.Windows.Data.XmlDataProvider> her kişi için veri içeren:

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    Veri olarak oluşturulan bir <xref:System.Windows.Controls.Grid> kaynak. Normalde bu dosya olarak yüklenir, ancak kolaylık sağlamak için veriler satır içi eklenir.

3. İçinde `<Grid.Resources>` öğesi, aşağıdaki ekleyin <xref:System.Windows.DataTemplate>, verilerin nasıl görüntüleneceğini tanımlayan <xref:System.Windows.Controls.ListBox>:

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    Veri şablonları hakkında daha fazla bilgi için bkz: [veri şablonu özeti](../../../../docs/framework/wpf/data/data-templating-overview.md).

4. Varolan <xref:System.Windows.Controls.ListBox> aşağıdaki XAML ile:

    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Bu XAML bağlar <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği <xref:System.Windows.Controls.ListBox> veri kaynağı ve veri şablon olarak geçerlidir <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.

## <a name="connect-data-to-controls"></a>Veri denetimleri Bağlan

Ardından, seçili adı almak için kod ekleyeceksiniz **ExpenseItHome** sayfasında ve oluşturucusuna geçirin **ExpenseReportPage**. **ExpenseReportPage** ne denetimleri tanımlandığı geçirilen öğe ile veri bağlamını ayarlar içinde *ExpenseReportPage.xaml* bağlayın.

1. Açık *ExpenseReportPage.xaml.vb* veya *ExpenseReportPage.xaml.cs*.

2. Seçili kişinin harcama raporu verilerini geçirmek için bir nesne alan bir oluşturucu ekleyin.

    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Açık *ExpenseItHome.xaml.vb* veya *ExpenseItHome.xaml.cs*.

4. Değişiklik <xref:System.Windows.Controls.Primitives.ButtonBase.Click> seçili kişinin harcama raporu geçirilen yeni oluşturucuyu çağırmak için olay işleyicisi.

    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Veri şablonları ile stil verileri

Bu bölümde, veri şablonlarını kullanarak veri bağlama listesindeki her bir öğe için kullanıcı Arabirimi güncelleştireceksiniz.

1. Açık *ExpenseReportPage.xaml*.

2. "Name" ve "Departman" içeriğini bağlama <xref:System.Windows.Controls.Label> uygun veri öğelerine kaynak özelliği. Veri bağlama hakkında daha fazla bilgi için bkz: [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).

    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Açtıktan sonra <xref:System.Windows.Controls.Grid> öğesi, harcama raporu verilerini görüntülemek nasıl tanımlayan aşağıdaki veri şablonlarını ekleyin:

    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. Şablonlar için geçerli <xref:System.Windows.Controls.DataGrid> gider gösteren sütunları rapor verileri.

    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Derleme ve uygulamayı çalıştırın.

6. Bir kişi seçin ve ardından **Görünüm** düğmesi.

Her iki sayfa denetimleri, düzen, stiller, veri bağlama ve uygulanan veri şablonları ile ExpenseIt uygulamasının aşağıda gösterilmiştir:

![ExpenseIt örnek ekran görüntüleri](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png)

> [!NOTE]
> Bu örnek, belirli bir WPF özelliğini gösterir ve güvenlik, yerelleştirme ve erişilebilirlik gibi için tüm en iyi uygulamaları izleyin değil. Kapsamlı WPF ve .NET Framework uygulama geliştirme en iyi uygulamalar için aşağıdaki konulara bakın:
>
> - [Erişilebilirlik](../../../../docs/framework/ui-automation/accessibility-best-practices.md)
>
> - [Güvenlik](../../../../docs/framework/wpf/security-wpf.md)
>
> - [WPF Genelleştirme ve yerelleştirme](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
>
> - [WPF Performans](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu kılavuzda Windows Presentation Foundation (WPF) kullanarak kullanıcı Arabirimi oluşturma teknikleri sayısı öğrendiniz. Veri bağlama, .NET Framework uygulama yapı taşlarını temel bir anlayış şimdi olmalıdır. WPF mimarisi ve programlama modelleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [WPF mimarisi](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
- [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [Bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [Düzen](../../../../docs/framework/wpf/advanced/layout.md)

Uygulamaları oluşturma hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Uygulama geliştirme](../../../../docs/framework/wpf/app-development/index.md)
- [Denetimler](../../../../docs/framework/wpf/controls/index.md)
- [Veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Grafik ve çoklu ortam](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Paneller Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)
- [Veri şablonu özeti](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [Bir WPF uygulaması oluşturma](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [Stilleri ve şablonları](../../../../docs/framework/wpf/controls/styles-and-templates.md)
