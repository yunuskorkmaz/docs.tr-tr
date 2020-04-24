---
title: Visual Studio 2019'da ilk WPF uygulamanızı oluşturun - .NET Framework
titleSuffix: ''
ms.date: 09/06/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
ms.topic: tutorial
ms.custom: mvc,vs-dotnet
ms.openlocfilehash: 9381873faa8cca1accf95d823f5183a218d28813
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646424"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a>Öğretici: Visual Studio 2019'da ilk WPF uygulamanızı oluşturun

Bu makalede, çoğu WPF uygulamasında ortak olan öğeleri içeren bir Windows Presentation Foundation (WPF) masaüstü uygulaması nın nasıl geliştirilildiği gösterilmektedir: Genişletilebilir Uygulama Biçimlendirme Dili (XAML) biçimlendirme, kod arkası, uygulama tanımları, denetimler, düzen, veri bağlama ve stilleri. Uygulamayı geliştirmek için Visual Studio'yu kullanacaksınız.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
>
> - Bir WPF projesi oluşturun.
> - Uygulamanın kullanıcı arabiriminin (UI) görünümünü tasarlamak için XAML'yi kullanın.
> - Uygulamanın davranışını oluşturmak için kod yazın.
> - Uygulamayı yönetmek için bir uygulama tanımı oluşturun.
> - Denetimler ekleyin ve uygulama kullanıcı yı oluşturmak için düzen oluşturun.
> - Uygulamanın Kullanıcı Arabirimi boyunca tutarlı bir görünüm için stiller oluşturun.
> - Kullanıcı UI'yi verilere bağlayın, hem veri kullanıcı larını doldurmak hem de verileri ve Kullanıcı Yı'nı eşitlemek için.

Öğreticinin sonunda, kullanıcıların seçilen kişilerin gider raporlarını görüntülemesine olanak tanıyan bağımsız bir Windows uygulaması oluşturmuş olacaksınız. Uygulama, tarayıcı tarzı bir pencerede barındırılan birkaç WPF sayfalarından oluşur.

> [!TIP]
> Bu öğreticide kullanılan örnek kod, [Öğretici WPF Uygulama Örnek Kodu'nda](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp)hem Visual Basic hem de C# için kullanılabilir.
>
> Bu sayfanın üstündeki dil seçiciyi kullanarak örnek kodun kod dilini C# ve Visual Basic arasında geçiş yapabilirsiniz.

## <a name="prerequisites"></a>Ön koşullar

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ile **.NET masaüstü geliştirme** iş yükü yüklendi.

   Visual Studio'nun en son sürümünü yükleme hakkında daha fazla bilgi için Visual [Studio'yu yükle'ye](/visualstudio/install/install-visual-studio)bakın.

## <a name="create-the-application-project"></a>Uygulama projesini oluşturma

İlk adım, uygulama tanımı, iki sayfa ve bir görüntü içeren uygulama altyapısı oluşturmaktır.

1. Visual Basic veya Visual C# adlı **`ExpenseIt`** yeni bir WPF Uygulama projesi oluşturun:

   1. Visual Studio'yu açın ve **Başlat menüsü** altında yeni bir **proje oluştur'u** seçin.

      **Yeni proje oluştur** iletişim kutusu açılır.

   2. **Dil** açılır düşüşünde **C#** veya **Visual Basic'i**seçin.

   3. **WPF Uygulaması (.NET Framework)** şablonunu seçin ve sonra **İleri'yi**seçin.

      ![Yeni bir proje iletişim kutusu oluşturma](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)

      Yeni proje iletişim **günlüğüne Yapıla** açılır.

   4. Proje adını **`ExpenseIt`** girin ve sonra **Oluştur'u**seçin.

      ![Yeni bir proje iletişim kutusunu yapılandırma](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      Visual Studio projeyi oluşturur ve **MainWindow.xaml**adlı varsayılan uygulama penceresi için tasarımcıyı açar.

2. *Open Application.xaml* (Visual Basic) veya *App.xaml* (C#).

    Bu XAML dosyası bir WPF uygulamasını ve uygulama kaynaklarını tanımlar. Ayrıca ui belirtmek için bu dosyayı kullanın, Bu durumda *MainWindow.xaml*, otomatik olarak uygulama başladığında gösterir.

    XAML'niz Visual Basic'te aşağıdaki gibi görünmelidir:

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    Ve C#'daki gibi:

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. *Açık MainWindow.xaml*.

    Bu XAML dosyası uygulamanızın ana penceresidir ve sayfalarda oluşturulan içeriği görüntüler. Sınıf, <xref:System.Windows.Window> başlığı, boyutu veya simgesi gibi bir pencerenin özelliklerini tanımlar ve kapatma veya gizleme gibi olayları işler.

4. Aşağıdaki <xref:System.Windows.Window> XAML'de gösterildiği gibi öğeyi bir <xref:System.Windows.Navigation.NavigationWindow>olarak değiştirin:

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   Bu uygulama, kullanıcı girişine bağlı olarak farklı içeriğe yönlendirin. Bu nedenle ana <xref:System.Windows.Window> bir <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow>tüm özelliklerini <xref:System.Windows.Window>devralır. XAML dosyasındaki <xref:System.Windows.Navigation.NavigationWindow> öğe sınıfın bir örneğini <xref:System.Windows.Navigation.NavigationWindow> oluşturur. Daha fazla bilgi için [Gezintiye genel bakış](../app-development/navigation-overview.md)alabiliyorum.

5. <xref:System.Windows.Navigation.NavigationWindow> Etiketler arasındaki <xref:System.Windows.Controls.Grid> öğeleri kaldırın.

6. Öğe için XAML kodunda aşağıdaki <xref:System.Windows.Navigation.NavigationWindow> özellikleri değiştirin:

    - <xref:System.Windows.Window.Title%2A> Özelliği " "`ExpenseIt`olarak ayarlayın.

    - <xref:System.Windows.FrameworkElement.Height%2A> Özelliği 350 piksele ayarlayın.

    - <xref:System.Windows.FrameworkElement.Width%2A> Özelliği 500 piksele ayarlayın.

    XAML'niz Visual Basic için aşağıdaki gibi görünmelidir:

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    Ve C# için aşağıdaki gibi:

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. *Açık MainWindow.xaml.vb* veya *MainWindow.xaml.cs*.

    Bu *dosya, MainWindow.xaml'da*bildirilen olayları işlemek için kod içeren kod arkası bir dosyadır. Bu dosya XAML'de tanımlanan pencere için kısmi bir sınıf içerir.

8. C# kullanıyorsanız, `MainWindow` 'den <xref:System.Windows.Navigation.NavigationWindow>türeecek sınıfı değiştirin. (Visual Basic'te, XAML'de pencereyi değiştirdiğinizde bu otomatik olarak gerçekleşir.) C# kodunuz şimdi şu na benzemelidir:

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a>Uygulamaya dosya ekleme

Bu bölümde, uygulamaya iki sayfa ve bir resim eklersiniz.

1. Projeye yeni bir sayfa ekleyin ve *`ExpenseItHome.xaml`* adlandırın:

   1. **Çözüm Gezgini'nde**proje **`ExpenseIt`** düğümüne sağ tıklayın ve**Sayfa** **Ekle'yi** > seçin.

   1. Yeni **Öğe Ekle** iletişim kutusunda, **Sayfa (WPF)** şablonu zaten seçilir. Adı **`ExpenseItHome`** girin ve sonra **Ekle'yi**seçin.

    Bu sayfa, uygulama başlatıldığında görüntülenen ilk sayfadır. Bu, bir gider raporu göstermek için seçilecek kişilerin listesini gösterir.

1. Aç. *`ExpenseItHome.xaml`*

1. " <xref:System.Windows.Controls.Page.Title%2A> "`ExpenseIt - Home`".

1. `DesignHeight` 350 piksele ve 500 `DesignWidth` piksele ayarlayın.

    XAML şimdi Visual Basic için aşağıdaki gibi görünür:

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    Ve C# için aşağıdaki gibi:

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. *Açık MainWindow.xaml*.

1. Öğeye <xref:System.Windows.Navigation.NavigationWindow.Source%2A> bir özellik ekleyin ve`ExpenseItHome.xaml`" " olarak ayarlayın. <xref:System.Windows.Navigation.NavigationWindow>

    Bu, *`ExpenseItHome.xaml`* uygulama başladığında açılan ilk sayfa olarak ayarlar.

    Örnek XAML Visual Basic:

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    Ve C#' da:

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > **Kaynak** özelliğini **Özellikler** penceresinin **çeşitli** kategorisinde de ayarlayabilirsiniz.
   >
   > ![Özellikler penceresinde kaynak özelliği](./media/properties-source.png)

1. Projeye yeni bir WPF sayfası daha ekleyin ve *expensereport.xaml*adını verin ::

   1. **Çözüm Gezgini'nde**proje **`ExpenseIt`** düğümüne sağ tıklayın ve**Sayfa** **Ekle'yi** > seçin.

   1. Yeni **Öğe Ekle** iletişim kutusunda **Sayfa (WPF)** şablonu öğesini seçin. **GiderRaporu Sayfası**adını girin ve sonra **Ekle'yi**seçin.

    Bu sayfada, **`ExpenseItHome`** sayfada seçilen kişinin gider raporu gösterilecek.

1. *Açık GiderReportPage.xaml*.

1. " <xref:System.Windows.Controls.Page.Title%2A> "`ExpenseIt - View Expense`".

1. `DesignHeight` 350 piksele ve 500 `DesignWidth` piksele ayarlayın.

    *ExpenseReportPage.xaml* şimdi Visual Basic aşağıdaki gibi görünüyor:

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    Ve C#'daki gibi:

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. Açık *GiderItHome.xaml.vb* ve *GiderReportPage.xaml.vb*, veya *ExpenseItHome.xaml.cs* ve *ExpenseReportPage.xaml.cs*.

    Yeni bir Sayfa dosyası oluşturduğunuzda, Visual Studio otomatik olarak *kod arkasındaki* dosyayı oluşturur. Bu kod arkası dosyalar, kullanıcı girişine yanıt verme mantığını işler.

    Kodunuz aşağıdaki **`ExpenseItHome`** gibi görünmelidir:

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    Ve **GiderReportPage**için aşağıdaki gibi:

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. Projeye *filigran.png* adlı bir resim ekleyin. Kendi resminizi oluşturabilir, dosyayı örnek koddan kopyalayabilir veya [microsoft/WPF-Samples](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png) GitHub deposundan alabilirsiniz.

    1. Proje düğümüne sağ tıklayın ve**Varolan Öğe** **ekle'yi** > seçin veya **Shift**+**Alt**+**A tuşuna**basın.

    2. **Varolan Öğe Ekle** iletişim kutusunda, dosya filtresini **Tüm Dosyalar** veya **Resim Dosyaları'na**ayarlayın, kullanmak istediğiniz resim dosyasına göz atın ve sonra **Ekle'yi**seçin.

## <a name="build-and-run-the-application"></a>Uygulamayı derleme ve çalıştırma

1. Uygulamayı oluşturmak ve çalıştırmak için Hata **Ayıklama** menüsünden **F5** tuşuna basın veya Hata **Ayıklama başlat'ı** seçin.

    Aşağıdaki resimde <xref:System.Windows.Navigation.NavigationWindow> düğmeleri ile uygulama gösterir:

    ![Oluşturup çalıştırdıktan sonra uygulama.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. Visual Studio'ya dönmek için uygulamayı kapatın.

## <a name="create-the-layout"></a>Düzeni oluşturma

Düzen, Kullanıcı Arabirimi öğelerini yerleştirmek için sıralı bir yol sağlar ve kullanıcı arabirimi yeniden boyutlandığında bu öğelerin boyutunu ve konumunu yönetir. Genellikle aşağıdaki düzen denetimlerinden biriyle bir düzen oluşturursunuz:

- <xref:System.Windows.Controls.Canvas>- Tuval alanına göre koordinatları kullanarak alt öğeleri açıkça konumlandırabileceğiniz bir alan tanımlar.
- <xref:System.Windows.Controls.DockPanel>- Alt öğeleri yatay veya dikey olarak, birbirlerine göre düzenleyebileceğiniz bir alan tanımlar.
- <xref:System.Windows.Controls.Grid>- Sütun ve satırlardan oluşan esnek bir ızgara alanı tanımlar.
- <xref:System.Windows.Controls.StackPanel>- Alt öğeleri yatay veya dikey olarak yönlendirilebilen tek bir satıra düzenler.
- <xref:System.Windows.Controls.VirtualizingStackPanel>- İçeriği yatay veya dikey olarak yönlendirilen tek bir satırda düzenler ve sanallaştırır.
- <xref:System.Windows.Controls.WrapPanel>- Alt öğeleri soldan sağa sıralı konuma yerleştirerek içeriği içeren kutunun kenarındaki bir sonraki satıra ayırın. Sonraki sıralama, Yönlendirme özelliğinin değerine bağlı olarak yukarıdan aşağıya veya sağdan sola sırayla gerçekleşir.

Bu düzen denetimlerinin her biri, alt öğeleri için belirli bir düzen türünü destekler. `ExpenseIt`sayfalar yeniden boyutlandırılabilir ve her sayfada diğer öğelerle birlikte yatay ve dikey olarak düzenlenmiş öğeler vardır. Bu örnekte, <xref:System.Windows.Controls.Grid> uygulama için düzen öğesi olarak kullanılır.

> [!TIP]
> Öğeler hakkında <xref:System.Windows.Controls.Panel> daha fazla bilgi için [Paneller genel bakış](../controls/panels-overview.md)bakın. Düzen hakkında daha fazla bilgi için [Bkz. Düzen.](../advanced/layout.md)

Bu bölümde, <xref:System.Windows.Controls.Grid> içinde *`ExpenseItHome.xaml`* sütun ve satır tanımları ekleyerek üç satır ve 10 piksel kenar boşluğu içeren tek sütunlu bir tablo oluşturursunuz.

1. In *`ExpenseItHome.xaml`*, <xref:System.Windows.FrameworkElement.Margin%2A> öğe üzerindeki <xref:System.Windows.Controls.Grid> özelliği "10,0,10,10" olarak ayarlayın, hangi sol, üst, sağ ve alt kenar boşlukları karşılık gelir:

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > **Özellikler** penceresinde, **Düzen** kategorisi altında **Kenar Boşluğu** değerlerini de ayarlayabilirsiniz:
   >
   > ![Özellikler penceresinde kenar boşluğu değerleri](./media/properties-margin.png)

2. Satır ve sütun tanımlarını <xref:System.Windows.Controls.Grid> oluşturmak için etiketlerin arasına aşağıdaki XAML'yi ekleyin:

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    İki <xref:System.Windows.Controls.RowDefinition.Height%2A> satırın <xref:System.Windows.GridLength.Auto%2A>kümesi, satırlar satırlarda içeriğe göre boyutlandırılır anlamına gelir. Varsayılan <xref:System.Windows.Controls.RowDefinition.Height%2A> boyutlandırmadır, <xref:System.Windows.GridUnitType.Star> bu da satır yüksekliğinin kullanılabilir alanın ağırlıklı bir oranı olduğu anlamına gelir. Örneğin, her <xref:System.Windows.Controls.RowDefinition.Height%2A> biri "*" olan iki satır varsa, her birinin kullanılabilir alanın yarısı olan bir yüksekliğe sahiptir.

    Şimdi <xref:System.Windows.Controls.Grid> aşağıdaki XAML içermelidir:

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Denetim ekleme

Bu bölümde, harcama raporunu görüntülemek için bir kişi seçtiğiniz kişilerin listesini göstermek için ana sayfa kullanıcı arabirimi bilgilerini güncelleştireceksiniz. Denetimler, kullanıcıların uygulamanızla etkileşimkurmasını sağlayan Kullanıcı GEtki nesneleridir. Daha fazla bilgi için [Denetimler'e](../controls/index.md)bakın.

Bu UI'yi oluşturmak için *`ExpenseItHome.xaml`* aşağıdaki öğeleri eklersiniz:

- A <xref:System.Windows.Controls.ListBox> (kişi listesi için).
- A <xref:System.Windows.Controls.Label> (liste üstbilgi için).
- A <xref:System.Windows.Controls.Button> (listede seçilen kişinin gider raporunu görüntülemek için tıklatın).

Her denetim <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> ekli özelliği ayarlayarak bir satır yerleştirilir. Ekteki özellikler hakkında daha fazla bilgi için [bkz.](../advanced/attached-properties-overview.md)

1. In *`ExpenseItHome.xaml`*, <xref:System.Windows.Controls.Grid> etiketleri arasında bir yere aşağıdaki XAML ekleyin:

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Denetimleri **Araç Kutusu** penceresinden tasarım penceresine sürükleyerek ve özellikleri özellikleriözelliklerini ayarlayarak **Properties** da oluşturabilirsiniz.

2. Uygulamayı derleyin ve çalıştırın.

    Aşağıdaki resimde oluşturduğunuz denetimler gösterilmektedir:

![GiderAd listesini gösteren örnek ekran görüntüsü](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a>Resim ve başlık ekleme

Bu bölümde, ana sayfa kullanıcı kullanıcı sını bir resim ve sayfa başlığıyla güncelleştirirsiniz.

1. In *`ExpenseItHome.xaml`*, 230 <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> piksel <xref:System.Windows.Controls.ColumnDefinition.Width%2A> sabit başka bir sütun ekleyin:

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewColumn)]

2. Toplam dört satır <xref:System.Windows.Controls.Grid.RowDefinitions%2A>için başka bir satır ekleyin:

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewRows)]

3. <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> Üç denetimin (Kenarlık, ListBox ve Düğme) her birinde özelliği 1'e ayarlayarak denetimleri ikinci sütuna taşıyın.

4. Her denetimi, üç denetimin (Kenarlık, ListBox ve Düğme) her biri için 1'e ve Kenarlık öğesine göre 1'e ekleyerek <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> her denetimi bir satıraşağı taşıyın.

   Üç denetim için XAML şimdi aşağıdaki gibi görünüyor:

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. Aşağıdaki XAML'yi `</Grid>` etiketler in arasına ekleyerek özelliği *filigran.png* resim dosyasına `<Grid>` ayarlayın: <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. Öğeden <xref:System.Windows.Controls.Border> önce, <xref:System.Windows.Controls.Label> "Gider Raporu Görüntüle" içeriğiyle bir öğe ekleyin. Bu etiket sayfanın başlığıdır.

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. Uygulamayı derleyin ve çalıştırın.

Aşağıdaki resimde az önce eklediğiniz şeyin sonuçları gösterilmektedir:

![GiderYeni resim arka planını ve sayfa başlığını gösteren örnek ekran görüntüsü](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a>Olayları işlemek için kod ekleme

1. In *`ExpenseItHome.xaml`*, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> öğeye bir <xref:System.Windows.Controls.Button> olay işleyicisi ekleyin. Daha fazla bilgi için [bkz: Basit bir olay işleyicisi oluşturun.](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. Aç *`ExpenseItHome.xaml.vb`* *`ExpenseItHome.xaml.cs`* veya .

3. Bir düğme tıklatmak `ExpenseItHome` olay işleyicisi eklemek için sınıfa aşağıdaki kodu ekleyin. Olay işleyicisi **Gider Raporu Sayfası** sayfasını açar.

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>Gider Raporu Sayfası için UI oluşturma

**`ExpenseItHome`** *ExpenseReportPage.xaml,* sayfada seçilen kişinin gider raporunu görüntüler. Bu bölümde, **GiderReportPage**için UI'yi oluşturursunuz. Ayrıca, çeşitli UI öğelerine arka plan ve dolgu renkleri eklersiniz.

1. *Açık GiderReportPage.xaml*.

2. Etiketler arasına aşağıdaki XAML'yi <xref:System.Windows.Controls.Grid> ekleyin:

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Bu UI benzer *`ExpenseItHome.xaml`*, rapor verileri dışında <xref:System.Windows.Controls.DataGrid>bir .

3. Uygulamayı derleyin ve çalıştırın.

4. **Görünüm** düğmesini seçin.

    Gider raporu sayfası görüntülenir. Ayrıca, geri navigasyon düğmesinin etkin olduğunu da unutmayın.

Aşağıdaki resimde *ExpenseReportPage.xaml'a*eklenen UI öğeleri gösterilmektedir.

![ExpenseReportPage için oluşturulan UI'yi gösteren örnek ekran görüntüsü.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a>Stil denetimleri

Çeşitli öğelerin görünümü genellikle bir UI aynı türdeki tüm öğeler için aynıdır. UI, görünümleri birden çok öğe arasında yeniden kullanılabilir hale getirmek için [stilleri](../../../desktop-wpf/fundamentals/styles-templates-overview.md) kullanır. Stillerin yeniden kullanılabilirliği XAML oluşturma ve yönetimini basitleştirmeye yardımcı olur. Bu bölüm, önceki adımlarda tanımlanan öğe başına öznitelikleri stilleri ile değiştirir.

1. *Açık Uygulama.xaml* veya *App.xaml*.

2. Etiketler arasına aşağıdaki XAML'yi <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> ekleyin:

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Bu XAML aşağıdaki stilleri ekler:

    - `headerTextStyle`: Sayfa başlığını <xref:System.Windows.Controls.Label>biçimlendirmek için .

    - `labelStyle`: Denetimleri <xref:System.Windows.Controls.Label> biçimlendirmek için.

    - `columnHeaderStyle`: Biçimlendirmek <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>için .

    - `listHeaderStyle`: Liste üstbilgi <xref:System.Windows.Controls.Border> denetimlerini biçimlendirmek için.

    - `listHeaderTextStyle`: Liste üstbilgisini <xref:System.Windows.Controls.Label>biçimlendirmek için .

    - `buttonStyle`: Üzerinde `ExpenseItHome.xaml` <xref:System.Windows.Controls.Button> biçimlendirmek için .

    Stillerin özellik öğesinin kaynakları <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> ve çocukları olduğuna dikkat edin. Bu konumda, stilleri bir uygulamadaki tüm öğelere uygulanır. Bir .NET uygulamasında kaynakları kullanma örneği [için](../advanced/how-to-use-application-resources.md)bkz.

3. In *`ExpenseItHome.xaml`*, <xref:System.Windows.Controls.Grid> aşağıdaki XAML ile öğeler arasındaki her şeyi değiştirin:

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    Her denetimin <xref:System.Windows.VerticalAlignment> <xref:System.Windows.Media.FontFamily> görünümünü tanımlayan özellikler kaldırılır ve stilleri uygulanarak değiştirilir. Örneğin, `headerTextStyle` "Görünüm Gider Raporu"na <xref:System.Windows.Controls.Label>uygulanır.

4. *Açık GiderReportPage.xaml*.

5. <xref:System.Windows.Controls.Grid> Öğeler arasındaki her şeyi aşağıdaki XAML ile değiştirin:

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Bu XAML stilleri <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.Border> öğeleri ekler.

6. Uygulamayı derleyin ve çalıştırın. Pencere görünümü öncekiyle aynıdır.

    ![GiderÖnceki bölümde ki görünüme sahip örnek ekran görüntüsü.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. Visual Studio'ya dönmek için uygulamayı kapatın.

## <a name="bind-data-to-a-control"></a>Verileri denetime bağlama

Bu bölümde, çeşitli denetimlere bağlı XML verileri oluşturursunuz.

1. Açılış *`ExpenseItHome.xaml`* <xref:System.Windows.Controls.Grid> öğesinden sonra, her kişi için verileri <xref:System.Windows.Data.XmlDataProvider> içeren bir tane oluşturmak için aşağıdaki XAML'yi ekleyin:

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    Veriler kaynak <xref:System.Windows.Controls.Grid> olarak oluşturulur. Normalde bu veriler bir dosya olarak yüklenir, ancak basitlik için veriler satır satıreklenir.

2. Öğe `<Grid.Resources>` içinde, `<XmlDataProvider>` aşağıdaki `<xref:System.Windows.DataTemplate>` öğeyi ekleyin, hangi veri görüntülemek <xref:System.Windows.Controls.ListBox>için nasıl tanımlar , öğesonra:

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    Veri şablonları hakkında daha fazla bilgi için [bkz.](../data/data-templating-overview.md)

3. Varolan <xref:System.Windows.Controls.ListBox> xaml'ı aşağıdaki XAML ile değiştirin:

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Bu XAML, veri <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> kaynağının <xref:System.Windows.Controls.ListBox> özelliğini bağlar ve veri şablonu <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.

## <a name="connect-data-to-controls"></a>Verileri denetimlere bağlama

Ardından, **`ExpenseItHome`** sayfada seçilen adı almak için kod ekler ve **GiderReportPage'in**oluşturucusuna iletirsiniz. **ExpenseReportPage,** *harcamaReportPage.xaml* bağlamada tanımlanan denetimlerin aktarDığı öğeyle veri bağlamını ayarlar.

1. *Açık GiderReportPage.xaml.vb* veya *ExpenseReportPage.xaml.cs*.

2. Seçili kişinin gider raporu verilerini geçirebilmeniz için nesne alan bir oluşturucu ekleyin.

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Aç *`ExpenseItHome.xaml.vb`* *`ExpenseItHome.xaml.cs`* veya .

4. <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Seçilen kişinin gider raporu verilerini geçen yeni oluşturucuyu çağırmak için olay işleyicisini değiştirin.

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Veri şablonları ile stil verileri

Bu bölümde, veri şablonlarını kullanarak veri ye bağlı listelerdeki her öğe için Kullanıcı Arabirimi'ni güncelleştirebilirsiniz.

1. *Açık GiderReportPage.xaml*.

2. "Ad" ve "Departman" <xref:System.Windows.Controls.Label> öğelerinin içeriğini uygun veri kaynağı özelliğine bağla. Veri bağlama hakkında daha fazla bilgi için [bkz.](../../../desktop-wpf/data/data-binding-overview.md)

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Açılış <xref:System.Windows.Controls.Grid> öğesinden sonra, gider raporu verilerinin nasıl görüntüleyeceğini tanımlayan aşağıdaki veri şablonlarını ekleyin:

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. Öğeleri <xref:System.Windows.Controls.DataGridTextColumn> öğenin <xref:System.Windows.Controls.DataGridTemplateColumn> <xref:System.Windows.Controls.DataGrid> altında değiştirin ve şablonları onlara uygulayın.

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Uygulamayı derleyin ve çalıştırın.

6. Bir kişi seçin ve ardından **Görünüm** düğmesini seçin.

Aşağıdaki resimde, uygulamanın `ExpenseIt` denetimleri, düzeni, stilleri, veri bağlama ve uygulanan veri şablonları ile her iki sayfa gösterilmektedir:

![Ad listesini ve gider raporunu gösteren uygulamanın her iki sayfası.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> Bu örnek WPF'nin belirli bir özelliğini gösterir ve güvenlik, yerelleştirme ve erişilebilirlik gibi şeyler için en iyi tüm uygulamaları izlemez. WPF ve .NET uygulama geliştirme en iyi uygulamaları kapsamlı kapsama alanı için aşağıdaki konulara bakın:
>
> - [Erişilebilirlik](../../ui-automation/accessibility-best-practices.md)
> - [Güvenlik](../security-wpf.md)
> - [WPF küreselleşmeve yerelleştirme](../advanced/wpf-globalization-and-localization-overview.md)
> - [WPF performansı](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu walkthrough windows presentation foundation (WPF) kullanarak bir ui oluşturmak için bir dizi teknik öğrendim. Artık veriye bağlı bir .NET uygulamasının yapı taşları hakkında temel bir anlayışa sahip olmalısınız. WPF mimarisi ve programlama modelleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [WPF mimarisi](../advanced/wpf-architecture.md)
- [XAML genel bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Bağımlılık özelliklerine genel bakış](../advanced/dependency-properties-overview.md)
- [Düzen](../advanced/layout.md)

Uygulama oluşturma hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Uygulama geliştirme](../app-development/index.md)
- [Denetimler](../controls/index.md)
- [Veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Grafik ve multimedya](../graphics-multimedia/index.md)
- [WPF'deki Belgeler](../advanced/documents-in-wpf.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Paneller genel bakış](../controls/panels-overview.md)
- [Veri cazip genel bakış](../data/data-templating-overview.md)
- [WPF uygulaması oluşturma](../app-development/building-a-wpf-application-wpf.md)
- [Stiller ve şablonlar](../controls/styles-and-templates.md)
