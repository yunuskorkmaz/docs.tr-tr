---
title: Visual Studio 'da ilk WPF uygulamanızı oluşturma 2019-.NET Framework
titleSuffix: ''
description: Çoğu WPF uygulaması için ortak olan öğeleri içeren bir Windows Presentation Foundation (WPF) masaüstü uygulaması geliştirin.
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
ms.openlocfilehash: c9af988bcf291325b11df4fd22827b47090c0b48
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853888"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a>Öğretici: Visual Studio 'da ilk WPF uygulamanızı oluşturma 2019

Bu makalede, çoğu WPF uygulaması için ortak olan öğeleri içeren bir Windows Presentation Foundation (WPF) masaüstü uygulaması geliştirme gösterilmektedir: Extensible Application Markup Language (XAML) işaretleme, arka plan kod, uygulama tanımları, denetimler, düzen, veri bağlama ve stiller. Uygulamayı geliştirmek için Visual Studio 'Yu kullanırsınız.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
>
> - WPF projesi oluşturun.
> - Uygulamanın kullanıcı arabiriminin (UI) görünümünü tasarlamak için XAML kullanın.
> - Uygulamanın davranışını derlemek için kod yazın.
> - Uygulamayı yönetmek için bir uygulama tanımı oluşturun.
> - Uygulama kullanıcı arabirimini oluşturmak için denetimler ekleyin ve düzeni oluşturun.
> - Uygulamanın kullanıcı arabiriminde tutarlı bir görünüm için stiller oluşturun.
> - Kullanıcı arabirimini verileri veri kaynağından doldurmak ve verileri ve Kullanıcı arabirimini eşitlenmiş halde tutmak için veri ARABIRIMINE bağlayın.

Öğreticinin sonuna kadar, kullanıcıların seçili kişilere ait gider raporlarını görüntülemesine olanak sağlayan tek başına bir Windows uygulaması oluşturacaksınız. Uygulama, tarayıcı stili bir pencerede barındırılan çeşitli WPF sayfalarından oluşur.

> [!TIP]
> Bu öğreticide kullanılan örnek kod, [ÖĞRETICI WPF uygulaması örnek kodunda](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp)hem Visual Basic hem de C# için kullanılabilir.
>
> Bu sayfanın üst kısmındaki dil seçicisini kullanarak C# ve Visual Basic arasında örnek kodun kod dilini değiştirebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

- **.Net masaüstü geliştirme** iş yükü yüklü olan [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) .

   Visual Studio 'nun en son sürümünü yükleme hakkında daha fazla bilgi için bkz. [Visual Studio 'Yu yükleme](/visualstudio/install/install-visual-studio).

## <a name="create-the-application-project"></a>Uygulama projesi oluşturma

İlk adım, uygulama tanımı, iki sayfa ve bir görüntü içeren uygulama altyapısını oluşturmaktır.

1. Visual Basic veya Visual C# ' de adlı yeni bir WPF uygulama projesi oluşturun **`ExpenseIt`** :

   1. Visual Studio 'Yu açın ve **Başlarken** menüsünde **Yeni proje oluştur** ' u seçin.

      **Yeni proje oluştur** iletişim kutusu açılır.

   2. **Dil** açılan menüsünde, **C#** veya **Visual Basic**seçin.

   3. **WPF uygulaması (.NET Framework)** şablonunu seçin ve ardından **İleri**' yi seçin.

      ![Yeni proje iletişim kutusu oluştur](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)

      **Yeni projenizi yapılandırma** iletişim kutusu açılır.

   4. Proje adını girip **`ExpenseIt`** **Oluştur**' u seçin.

      ![Yeni bir proje iletişim kutusu Yapılandır](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      Visual Studio projeyi oluşturur ve **MainWindow. xaml**adlı varsayılan uygulama penceresi için tasarımcıyı açar.

2. *Application. xaml* (Visual Basic) veya *app. xaml* (C#) öğesini açın.

    Bu XAML dosyası bir WPF uygulamasını ve uygulama kaynaklarını tanımlar. Bu dosyayı, Kullanıcı arabirimini belirtmek için de kullanabilirsiniz. Bu durumda *MainWindow. xaml*, uygulamanın başladığı zaman otomatik olarak gösterilir.

    XAML 'niz Visual Basic aşağıdaki gibi görünmelidir:

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    C# dilinde aşağıdakiler gibi:

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. *MainWindow. xaml*' i açın.

    Bu XAML dosyası, uygulamanızın ana penceresidir ve sayfalarda oluşturulan içeriği görüntüler. <xref:System.Windows.Window>Sınıfı, bir pencerenin başlık, boyut veya simgesi gibi özelliklerini tanımlar ve kapatma ya da gizleme gibi olayları işler.

4. <xref:System.Windows.Window> <xref:System.Windows.Navigation.NavigationWindow> Aşağıdaki xaml 'de gösterildiği gibi, öğesini olarak değiştirin:

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   Bu uygulama, kullanıcı girişine bağlı olarak farklı içeriğe gider. Bunun nedeni, Main 'in <xref:System.Windows.Window> bir olarak değiştirilmesini sağlar <xref:System.Windows.Navigation.NavigationWindow> . <xref:System.Windows.Navigation.NavigationWindow>tüm özelliklerini devralır <xref:System.Windows.Window> . <xref:System.Windows.Navigation.NavigationWindow>Xaml dosyasındaki öğesi, sınıfının bir örneğini oluşturur <xref:System.Windows.Navigation.NavigationWindow> . Daha fazla bilgi için bkz. [gezintiye genel bakış](../app-development/navigation-overview.md).

5. <xref:System.Windows.Controls.Grid>Öğeleri etiketler arasından kaldırın <xref:System.Windows.Navigation.NavigationWindow> .

6. Öğesi için XAML kodunda aşağıdaki özellikleri değiştirin <xref:System.Windows.Navigation.NavigationWindow> :

    - <xref:System.Windows.Window.Title%2A>Özelliği "" olarak ayarlayın `ExpenseIt` .

    - <xref:System.Windows.FrameworkElement.Height%2A>Özelliği 350 piksel olarak ayarlayın.

    - <xref:System.Windows.FrameworkElement.Width%2A>Özelliği 500 piksel olarak ayarlayın.

    Visual Basic için XAML 'niz aşağıdaki gibi görünmelidir:

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    C# için aşağıdakiler gibi:

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. *MainWindow. xaml. vb* veya *MainWindow.xaml.cs*öğesini açın.

    Bu dosya, *MainWindow. xaml*içinde belirtilen olayları işlemek için kod içeren bir arka plan kod dosyasıdır. Bu dosya XAML 'de tanımlanan pencere için kısmi bir sınıf içerir.

8. C# kullanıyorsanız, ' `MainWindow` den türetmek için sınıfını değiştirin <xref:System.Windows.Navigation.NavigationWindow> . (Visual Basic, XAML 'de pencereyi değiştirdiğinizde bu otomatik olarak gerçekleşir.) C# kodunuz şu şekilde görünmelidir:

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a>Uygulamaya dosya ekleme

Bu bölümde, uygulamaya iki sayfa ve bir görüntü ekleyeceksiniz.

1. Projeye yeni bir sayfa ekleyin ve bunu adlandırın *`ExpenseItHome.xaml`* :

   1. **Çözüm Gezgini**, **`ExpenseIt`** proje düğümüne sağ tıklayın ve sayfa ekle ' yi seçin **Add**  >  **Page**.

   1. **Yeni öğe Ekle** Iletişim kutusunda **sayfa (WPF)** şablonu zaten seçilidir. Adı girin **`ExpenseItHome`** ve ardından **Ekle**' yi seçin.

    Bu sayfa, uygulama başlatıldığında görüntülenen ilk sayfasıdır. İçin bir gider raporu göstermek üzere içinden seçilecek kişilerin listesini gösterir.

1. Öğesini açın *`ExpenseItHome.xaml`* .

1. <xref:System.Windows.Controls.Page.Title%2A>"" Olarak ayarlayın `ExpenseIt - Home` .

1. Öğesini `DesignHeight` 350 piksel ve ile `DesignWidth` 500 piksel olarak ayarlayın.

    XAML artık Visual Basic için aşağıdaki gibi görünür:

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    C# için aşağıdakiler gibi:

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. *MainWindow. xaml*' i açın.

1. Öğeye bir <xref:System.Windows.Navigation.NavigationWindow.Source%2A> özellik ekleyin <xref:System.Windows.Navigation.NavigationWindow> ve bunu "" olarak ayarlayın `ExpenseItHome.xaml` .

    Bu *`ExpenseItHome.xaml`* , uygulama başlatıldığında açılan ilk sayfa olarak ayarlanır.

    Visual Basic örnek XAML:

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    Ve C#:

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Ayrıca, **Özellikler** penceresinin **çeşitli** kategorisindeki **Source** özelliğini de ayarlayabilirsiniz.
   >
   > ![Özellikler penceresi kaynak özelliği](./media/properties-source.png)

1. Projeye yeni bir WPF sayfası ekleyin ve bunu *ExpenseReportPage. xaml*olarak adlandırın::

   1. **Çözüm Gezgini**, **`ExpenseIt`** proje düğümüne sağ tıklayın ve sayfa ekle ' yi seçin **Add**  >  **Page**.

   1. **Yeni öğe Ekle** Iletişim kutusunda **sayfa (WPF)** şablonunu seçin. **ExpenseReportPage**adını girip **Ekle**' yi seçin.

    Bu sayfa, sayfada seçili olan kişinin gider raporunu gösterir **`ExpenseItHome`** .

1. *ExpenseReportPage. xaml*' i açın.

1. <xref:System.Windows.Controls.Page.Title%2A>"" Olarak ayarlayın `ExpenseIt - View Expense` .

1. Öğesini `DesignHeight` 350 piksel ve ile `DesignWidth` 500 piksel olarak ayarlayın.

    *ExpenseReportPage. xaml* artık Visual Basic ' de aşağıdakine benzer:

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    C# dilinde aşağıdakiler gibi:

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. *ExpenseItHome. xaml. vb* ve *ExpenseReportPage. xaml. vb*veya *ExpenseItHome.xaml.cs* ve *ExpenseReportPage.xaml.cs*öğesini açın.

    Yeni bir sayfa dosyası oluşturduğunuzda, Visual Studio otomatik olarak *arka plan kod* dosyasını oluşturur. Bu arka plan kod dosyaları, kullanıcı girişine yanıt verme mantığını işler.

    Kodunuz şunlar gibi görünmelidir **`ExpenseItHome`** :

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    **ExpenseReportPage**için aşağıdakiler gibi:

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. Projeye *watermark.png* adlı bir görüntü ekleyin. Kendi görüntünüzü oluşturabilir, dosyayı örnek koddan kopyalayabilir veya [Microsoft/WPF-Samples](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png) GitHub deposundan alabilirsiniz.

    1. Proje düğümüne sağ tıklayın ve **Add**  >  **Varolan öğe**Ekle ' yi seçin veya **SHIFT** + **alt** + **A**'ya basın.

    2. **Varolan öğe Ekle** iletişim kutusunda, dosya filtresini **tüm dosyalar** veya **görüntü dosyaları**olarak ayarlayın, kullanmak istediğiniz görüntü dosyasına gidin ve **Ekle**' yi seçin.

## <a name="build-and-run-the-application"></a>Uygulamayı derleme ve çalıştırma

1. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın veya **Hata Ayıkla** menüsünden **hata ayıklamayı Başlat** ' ı seçin.

    Aşağıdaki çizim, düğmeleri içeren uygulamayı göstermektedir <xref:System.Windows.Navigation.NavigationWindow> :

    ![Uygulamanızı derleyip çalıştırdıktan sonra.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. Visual Studio 'ya dönmek için uygulamayı kapatın.

## <a name="create-the-layout"></a>Düzen oluşturma

Düzen, Kullanıcı arabirimi öğelerini yerleştirmek için sıralı bir yol sağlar ve ayrıca bir kullanıcı arabirimi yeniden boyutlandırılırken bu öğelerin boyutunu ve konumunu yönetir. Genellikle aşağıdaki düzen denetimlerinden birini kullanarak bir düzen oluşturursunuz:

- <xref:System.Windows.Controls.Canvas>-Tuval alanına göreli koordinatları kullanarak alt öğeleri açıkça konumlandırabileceğiniz bir alan tanımlar.
- <xref:System.Windows.Controls.DockPanel>-Alt öğeleri yatay veya dikey olarak birbirlerine göre düzenlemek için kullanabileceğiniz bir alan tanımlar.
- <xref:System.Windows.Controls.Grid>-Sütun ve satırlardan oluşan esnek bir kılavuz alanı tanımlar.
- <xref:System.Windows.Controls.StackPanel>-Alt öğeleri yatay veya dikey olarak yönelimli tek bir satıra yerleştirir.
- <xref:System.Windows.Controls.VirtualizingStackPanel>-İçeriği yatay veya dikey olarak tek bir satırda düzenler ve sanallaştırır.
- <xref:System.Windows.Controls.WrapPanel>-Alt öğeleri soldan sağa, kapsayan kutunun kenarındaki içerikleri sonraki satıra kadar konumlandırır. Yönlendirme özelliğinin değerine bağlı olarak, sonraki sıralama yukarıdan aşağıya doğru veya sağdan sola doğru bir şekilde gerçekleşir.

Bu düzen denetimlerinin her biri, alt öğeleri için belirli bir düzen türünü destekler. `ExpenseIt`sayfalar yeniden boyutlandırılabilir ve her sayfanın diğer öğelerin yanı sıra yatay ve dikey olarak düzenlenmiş öğeleri vardır. Bu örnekte, <xref:System.Windows.Controls.Grid> uygulama için düzen öğesi olarak kullanılır.

> [!TIP]
> Öğeler hakkında daha fazla bilgi için <xref:System.Windows.Controls.Panel> bkz. [panellere genel bakış](../controls/panels-overview.md). Düzen hakkında daha fazla bilgi için bkz. [Düzen](../advanced/layout.md).

Bu bölümde, içinde sütun ve satır tanımları ekleyerek üç satırı ve 10 piksellik bir kenar boşluğu içeren tek sütunlu bir tablo oluşturursunuz <xref:System.Windows.Controls.Grid> *`ExpenseItHome.xaml`* .

1. İçinde, *`ExpenseItHome.xaml`* <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.Grid> öğesinde özelliğini sol, üst, sağ ve alt kenar boşluklarına karşılık gelen "10, 0, 10, 10" olarak ayarlayın:

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Ayrıca, **Özellikler** penceresinde, **Düzen** kategorisi altında **kenar boşluğu** değerlerini de ayarlayabilirsiniz:
   >
   > ![Özellikler penceresi kenar boşluğu değerleri](./media/properties-margin.png)

2. <xref:System.Windows.Controls.Grid>Satır ve sütun tanımları oluşturmak için AŞAĞıDAKI xaml etiketleri arasına ekleyin:

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <xref:System.Windows.Controls.RowDefinition.Height%2A>İki satır olarak ayarlanır <xref:System.Windows.GridLength.Auto%2A> , yani satırlar satırlardaki içeriğe göre boyutlandırılır. Varsayılan değer <xref:System.Windows.Controls.RowDefinition.Height%2A> <xref:System.Windows.GridUnitType.Star> boyutlardır, bu da satır yüksekliğinin, kullanılabilir alanın ağırlıklı oransıdır. Örneğin, her biri <xref:System.Windows.Controls.RowDefinition.Height%2A> "*" olan iki satır, kullanılabilir alanın yarısı olan bir yüksekliğe sahiptir.

    <xref:System.Windows.Controls.Grid>Şimdi AŞAĞıDAKI xaml 'yi içermelidir:

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Denetim Ekle

Bu bölümde, giriş sayfası kullanıcı arabirimini, bir kişinin gider raporlarını görüntülemek için bir kişi seçtiğiniz bir kişi listesini gösterecek şekilde güncelleştireceksiniz. Denetimler, kullanıcıların uygulamanızla etkileşime geçmesini sağlayan UI nesneleridir. Daha fazla bilgi için bkz. [denetimler](../controls/index.md).

Bu Kullanıcı arabirimini oluşturmak için aşağıdaki öğeleri öğesine ekleyin *`ExpenseItHome.xaml`* :

- A <xref:System.Windows.Controls.ListBox> (kişiler listesi için).
- A <xref:System.Windows.Controls.Label> (liste üst bilgisi için).
- A <xref:System.Windows.Controls.Button> (listede Seçilen kişiye ait gider raporunu görüntülemek için tıklayın).

Her denetim, <xref:System.Windows.Controls.Grid> iliştirilmiş özelliği ayarlanarak öğesinin bir satırına yerleştirilir <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> . Ekli Özellikler hakkında daha fazla bilgi için bkz. [ekli özelliklere genel bakış](../advanced/attached-properties-overview.md).

1. İçinde *`ExpenseItHome.xaml`* AŞAĞıDAKI xaml 'yi Etiketler arasına bir yere ekleyin <xref:System.Windows.Controls.Grid> :

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Ayrıca, denetimleri **araç kutusu** penceresinden tasarım penceresine sürükleyerek ve sonra **Özellikler penceresinde özelliklerini** ayarlayarak da oluşturabilirsiniz.

2. Uygulamayı derleyin ve çalıştırın.

    Aşağıdaki çizimde, oluşturduğunuz denetimler gösterilmektedir:

![ExpenseIt örnek bir ad listesini görüntüleyen ekran görüntüsü](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a>Görüntü ve başlık ekleme

Bu bölümde, ana sayfa Kullanıcı arabirimini bir görüntüyle ve bir sayfa başlığıyla güncelleştireceksiniz.

1. İçinde, *`ExpenseItHome.xaml`* <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> 230 piksellik bir sabit ile başka bir sütun ekleyin <xref:System.Windows.Controls.ColumnDefinition.Width%2A> :

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewColumn)]

2. <xref:System.Windows.Controls.Grid.RowDefinitions%2A>Toplam dört satır için başka bir satır ekleyin:

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewRows)]

3. <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>Her üç denetimin (kenarlık, ListBox ve düğme) her birinde özelliği 1 olarak ayarlayarak denetimleri ikinci sütuna taşıyın.

4. <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>Üç denetimin (kenarlık, ListBox ve düğme) ve kenarlık öğesinin her biri için değerini 1 artırarak her denetimi bir satırı aşağı taşıyın.

   Üç denetim için XAML artık aşağıdaki gibi görünür:

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>AŞAĞıDAKI xaml 'yi ve etiketleri arasında bir yere ekleyerek özelliği *watermark.png* görüntü dosyasına ayarlayın `<Grid>` `</Grid>` :

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. Öğesinden önce <xref:System.Windows.Controls.Border> , <xref:System.Windows.Controls.Label> "harcama raporu görüntüle" içerikli bir öğesi ekleyin. Bu etiket sayfanın başlığıdır.

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. Uygulamayı derleyin ve çalıştırın.

Aşağıdaki çizimde, yeni eklediklerinize ilişkin sonuçlar gösterilmektedir:

![Yeni görüntü arka planını ve sayfa başlığını gösteren ExpenseIt örnek ekran görüntüsü](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a>Olayları işlemek için kod ekleme

1. İçinde *`ExpenseItHome.xaml`* , öğesine bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisi ekleyin <xref:System.Windows.Controls.Button> . Daha fazla bilgi için bkz. [nasıl yapılır: basit olay Işleyicisi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. Veya öğesini açın *`ExpenseItHome.xaml.vb`* *`ExpenseItHome.xaml.cs`* .

3. `ExpenseItHome`Bir düğme tıklama olayı işleyicisi eklemek için aşağıdaki kodu sınıfına ekleyin. Olay işleyicisi **ExpenseReportPage** sayfasını açar.

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>ExpenseReportPage için Kullanıcı arabirimi oluşturma

*ExpenseReportPage. xaml* , sayfada seçili olan kişinin gider raporunu görüntüler **`ExpenseItHome`** . Bu bölümde, **ExpenseReportPage**için Kullanıcı arabirimi oluşturacaksınız. Ayrıca, çeşitli UI öğelerine arkaplan ve Fill renkleri de ekleyeceksiniz.

1. *ExpenseReportPage. xaml*' i açın.

2. Aşağıdaki XAML etiketleri arasına ekleyin <xref:System.Windows.Controls.Grid> :

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    *`ExpenseItHome.xaml`* Rapor verileri bir içinde görüntülenirken, bu kullanıcı arabirimi öğesine benzerdir <xref:System.Windows.Controls.DataGrid> .

3. Uygulamayı derleyin ve çalıştırın.

4. **Görünüm** düğmesini seçin.

    Gider raporu sayfası görüntülenir. Ayrıca, geri gezinme düğmesinin etkin olduğuna dikkat edin.

Aşağıdaki çizimde, *ExpenseReportPage. xaml*'e eklenen UI öğeleri gösterilmektedir.

![Yalnızca ExpenseReportPage için oluşturulan kullanıcı arabirimini gösteren ExpenseIt örnek ekran görüntüsü.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a>Stil denetimleri

Çeşitli öğelerin görünümü, bir kullanıcı arabirimindeki aynı türdeki tüm öğeler için genellikle aynıdır. UI, görünümleri birden çok öğe arasında yeniden kullanılabilir hale getirmek için [stilleri](../../../desktop-wpf/fundamentals/styles-templates-overview.md) kullanır. Stillerin yeniden kullanılabilirliği XAML oluşturma ve yönetimini basitleştirmeye yardımcı olur. Bu bölüm, önceki adımlarda tanımlanan öğe başına özniteliklerin stil ile yerini alır.

1. *Application. xaml* veya *app. xaml*açın.

2. Aşağıdaki XAML etiketleri arasına ekleyin <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> :

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Bu XAML aşağıdaki stilleri ekler:

    - `headerTextStyle`: Sayfa başlığını biçimlendirmek için <xref:System.Windows.Controls.Label> .

    - `labelStyle`: Denetimleri biçimlendirmek için <xref:System.Windows.Controls.Label> .

    - `columnHeaderStyle`: Öğesini biçimlendirmek için <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> .

    - `listHeaderStyle`: Liste üst bilgi denetimlerini biçimlendirmek için <xref:System.Windows.Controls.Border> .

    - `listHeaderTextStyle`: Liste üst bilgisini biçimlendirmek için <xref:System.Windows.Controls.Label> .

    - `buttonStyle`: ' İ biçimlendirmek <xref:System.Windows.Controls.Button> için `ExpenseItHome.xaml` .

    Stillerin kaynak ve özellik öğesinin alt öğesi olduğuna dikkat edin <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> . Bu konumda, stiller bir uygulamadaki tüm öğelere uygulanır. Bir .NET uygulamasında kaynak kullanmanın bir örneği için bkz. [uygulama kaynaklarını kullanma](../advanced/how-to-use-application-resources.md).

3. İçinde *`ExpenseItHome.xaml`* , öğeler arasındaki her şeyi <xref:System.Windows.Controls.Grid> aşağıdaki xaml ile değiştirin:

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <xref:System.Windows.VerticalAlignment>Ve <xref:System.Windows.Media.FontFamily> her bir denetimin görünümünü tanımlayan özellikler, stiller uygulanarak kaldırılır ve değiştirilmez. Örneğin, `headerTextStyle` "harcama raporu görüntüle" öğesine uygulanır <xref:System.Windows.Controls.Label> .

4. *ExpenseReportPage. xaml*' i açın.

5. <xref:System.Windows.Controls.Grid>AŞAĞıDAKI XAML ile öğeler arasındaki her şeyi değiştirin:

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Bu XAML, <xref:System.Windows.Controls.Label> ve öğelerine stiller ekler <xref:System.Windows.Controls.Border> .

6. Uygulamayı derleyin ve çalıştırın. Pencere görünümü daha önce olduğu gibi.

    ![En son bölümle aynı görünüme sahip olan ExpenseIt örnek ekran görüntüsü.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. Visual Studio 'ya dönmek için uygulamayı kapatın.

## <a name="bind-data-to-a-control"></a>Verileri bir denetime bağlama

Bu bölümde, çeşitli denetimlere bağlanan XML verilerini oluşturacaksınız.

1. ' De, *`ExpenseItHome.xaml`* açılış <xref:System.Windows.Controls.Grid> öğesinden sonra, <xref:System.Windows.Data.XmlDataProvider> her bir kişiye ait verileri içeren bir oluşturmak için aşağıdaki xaml 'yi ekleyin:

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    Veriler bir kaynak olarak oluşturulur <xref:System.Windows.Controls.Grid> . Normalde bu veriler bir dosya olarak yüklenir, ancak kolaylık sağlaması için veriler satır içi eklenir.

2. Öğesi içinde, `<Grid.Resources>` `<xref:System.Windows.DataTemplate>` <xref:System.Windows.Controls.ListBox> öğesinden sonra ' de verilerin nasıl görüntüleneceğini tanımlayan aşağıdaki öğeyi ekleyin `<XmlDataProvider>` :

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    Veri şablonları hakkında daha fazla bilgi için bkz. [veri şablonu oluşturmaya genel bakış](../data/data-templating-overview.md).

3. Var olan <xref:System.Windows.Controls.ListBox> AŞAĞıDAKI XAML ile değiştirin:

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Bu XAML <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> , öğesinin özelliğini <xref:System.Windows.Controls.ListBox> veri kaynağına bağlar ve veri şablonunu olarak uygular <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> .

## <a name="connect-data-to-controls"></a>Verileri denetimlere bağlama

Daha sonra, sayfada seçilen adı almak için kod ekleyeceksiniz **`ExpenseItHome`** ve bunu **ExpenseReportPage**oluşturucusuna geçireceğiz. **ExpenseReportPage** ,, *ExpenseReportPage. xaml* ' de tanımlanan denetimlerin, geçirilen öğeyle veri bağlamını ayarlar.

1. *ExpenseReportPage. xaml. vb* veya *ExpenseReportPage.xaml.cs*öğesini açın.

2. Seçili kişinin gider raporu verilerini geçirebilmeniz için bir nesnesi alan bir Oluşturucu ekleyin.

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Veya öğesini açın *`ExpenseItHome.xaml.vb`* *`ExpenseItHome.xaml.cs`* .

4. <xref:System.Windows.Controls.Primitives.ButtonBase.Click>Olay işleyicisini, seçilen kişinin harcama raporu verilerini geçen yeni oluşturucuyu çağırmak üzere değiştirin.

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Veri şablonlarıyla stil verileri

Bu bölümde, veri şablonlarını kullanarak veri bağlantılı listelerdeki her öğe için Kullanıcı arabirimini güncelleştireceksiniz.

1. *ExpenseReportPage. xaml*' i açın.

2. "Name" ve "Department" <xref:System.Windows.Controls.Label> öğelerinin içeriğini uygun veri kaynağı özelliğine bağlayın. Veri bağlama hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md).

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Açılış öğesinden sonra <xref:System.Windows.Controls.Grid> , harcama raporu verilerinin nasıl görüntüleneceğini tanımlayan aşağıdaki veri şablonlarını ekleyin:

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <xref:System.Windows.Controls.DataGridTextColumn>Öğeleri <xref:System.Windows.Controls.DataGridTemplateColumn> öğesi altında ile değiştirin <xref:System.Windows.Controls.DataGrid> ve şablonları bunlara uygulayın.

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Uygulamayı derleyin ve çalıştırın.

6. Bir kişi seçin ve ardından **Görünüm** düğmesini seçin.

Aşağıdaki çizimde `ExpenseIt` denetimler, düzen, stiller, veri bağlama ve veri şablonları uygulanmış uygulamanın her iki sayfası gösterilmektedir:

![Uygulamanın her iki sayfası da adlar listesini ve bir gider raporunu gösterir.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> Bu örnek, WPF 'nin belirli bir özelliğini gösterir ve güvenlik, yerelleştirme ve erişilebilirlik gibi şeyler için en iyi uygulamaları izlemez. WPF ve .NET uygulama geliştirmenin en iyi uygulamalarının kapsamlı kapsamı için aşağıdaki konulara bakın:
>
> - [Erişilebilirlik](../../ui-automation/accessibility-best-practices.md)
> - [Güvenlik](../security-wpf.md)
> - [WPF Genelleştirme ve yerelleştirme](../advanced/wpf-globalization-and-localization-overview.md)
> - [WPF performansı](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu kılavuzda, Windows Presentation Foundation (WPF) kullanarak Kullanıcı arabirimi oluşturmaya yönelik çeşitli teknikler öğrendiniz. Artık, veri bağlantılı bir .NET uygulamasının yapı taşlarından daha basit bir bilgiye sahip olmanız gerekir. WPF mimarisi ve programlama modelleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [WPF mimarisi](../advanced/wpf-architecture.md)
- [XAML 'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Bağımlılık özelliklerine genel bakış](../advanced/dependency-properties-overview.md)
- [Layout](../advanced/layout.md)

Uygulama oluşturma hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Uygulama geliştirme](../app-development/index.md)
- [Denetimler](../controls/index.md)
- [Veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Grafikler ve multimedya](../graphics-multimedia/index.md)
- [WPF'deki Belgeler](../advanced/documents-in-wpf.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Panellere genel bakış](../controls/panels-overview.md)
- [Veri şablonu genel bakış](../data/data-templating-overview.md)
- [WPF uygulaması oluşturma](../app-development/building-a-wpf-application-wpf.md)
- [Stiller ve şablonlar](../controls/styles-and-templates.md)
