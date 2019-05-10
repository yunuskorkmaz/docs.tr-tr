---
title: Visual Studio'da WPF uygulaması oluşturma
ms.date: 03/20/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
author: mairaw
ms.author: mairaw
ms.custom: vs-dotnet
ms.openlocfilehash: 9d0abd18b2242ab21e8a915caac1ff9e3216acd0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617267"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>İzlenecek yol: İlk WPF masaüstü uygulamam

Bu makalede, çoğu WPF uygulamaları için ortak olan öğeler içeren bir Windows Presentation Foundation (WPF) masaüstü uygulaması geliştirme işlemini göstermektedir: Extensible Application Markup Language (XAML) işaretleme, arka plan kod, uygulama tanımları, denetimler, düzen, veri bağlama ve stilleri. Uygulama geliştirmek için Visual Studio kullanacaksınız. 

Bu izlenecek yol aşağıdaki adımları içerir:

- XAML, uygulamanın kullanıcı arabirimini (UI) görünümünü tasarlamak için kullanın.

- Uygulamanın davranışı oluşturmak için kod yazın.

- Uygulamayı yönetmek için bir uygulama tanımı oluşturur.

- Denetimler ekleme ve uygulama kullanıcı Arabirimi oluşturmak için düzenini oluşturun.

- Stilleri için uygulamanın UI genelinde tutarlı bir görünüm oluşturun.

- Verileri, veri kullanıcı Arabiriminden doldurmak ve verileri tutmak için kullanıcı arabirimini bağlamak ve UI eşitlenir.

İzlenecek yol sonunda, bağımsız bir seçilen kişilerin gider raporlarını görüntülemek kullanıcılara Windows uygulamasında oluşturulan. Uygulama, bir tarayıcı penceresinde barındırılan birçok WPF sayfadan oluşur.

> [!TIP]
> Bu izlenecek yolu oluşturmak için kullanılan örnek kod, hem Visual Basic için kullanılabilir ve C# adresindeki [izlenecek WPF uygulama örnek kodunu](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).
>
> Kod dili örnek kod arasında geçiş yapabilirsiniz C# ve Visual Basic'ı kullanarak **\< />** bu makalenin üst sağ taraftaki açılır.

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio 2017 veya üstü

   Visual Studio'nun en son sürümü yükleme hakkında daha fazla bilgi için bkz. [Visual Studio'yu yükleyin](/visualstudio/install/install-visual-studio). Bu makalede, Visual Studio 2019 kullanır.

## <a name="create-the-application-project"></a>Uygulama projesini oluşturun

İlk adım, bir uygulama tanımı, iki sayfaları ve görüntü içeren uygulama altyapısı oluşturmaktır.

1. Visual Basic veya Visual C# adlı yeni bir WPF uygulaması projesi oluşturma **`ExpenseIt`**:

   1. Visual Studio açıp seçin **dosya** > **yeni** > **proje**.

      **Yeni bir proje oluşturma** iletişim kutusu açılır.

      ![Yeni Proje iletişim kutusu oluşturma](./media/gettingstartedfigure0a.png)

   2. İçinde **dil** açılır listesinde, şunlardan birini seçin **C#** veya **Visual Basic**.

   3. Seçin **WPF uygulaması (.NET Framework)** şablonu ve ardından **sonraki**. 
    
   4. Seçin **yeni bir proje oluşturma**.

      **Yeni bir proje yapılandırma** iletişim kutusu açılır.

      ![Yeni Proje iletişim kutusu yapılandırın](./media/gettingstartedfigure0c.png)

   5. Proje adını girin **`ExpenseIt`** seçip **Oluştur**.

      Visual Studio projesi oluşturup adlı varsayılan uygulama penceresi için tasarımcı açılır **MainWindow.xaml**.

2. Açık *Application.xaml* (Visual Basic) veya *App.xaml* (C#).

    Bu XAML dosyasını bir WPF uygulaması ve uygulama kaynaklarını tanımlar. Bu dosya kullanıcı Arabirimi, bu durumda belirtmek için de *MainWindow.xaml*, uygulama başlatıldığında otomatik olarak gösterir.

    XAML, Visual Basic'te aşağıdaki gibi görünmelidir:

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    Ve aşağıdaki gibi C#:

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. Açık *MainWindow.xaml*.

    Bu XAML dosyası ana penceresinde, uygulamanızın ve sayfalarında oluşturulan içeriği görüntüler. <xref:System.Windows.Window> Sınıfı gibi başlık, boyut veya simge, bir penceresi özelliklerini tanımlar ve kapatma veya gizleme gibi olayları işler.

4. Değişiklik <xref:System.Windows.Window> öğesine bir <xref:System.Windows.Navigation.NavigationWindow>aşağıdaki XAML içinde gösterildiği gibi:

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   Bu uygulamanın kullanıcı girişi bağlı olarak farklı içerik gider. Bu nedenle, ana <xref:System.Windows.Window> için değiştirilmesi gereken bir <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow> tüm özelliklerini devralır <xref:System.Windows.Window>. <xref:System.Windows.Navigation.NavigationWindow> XAML dosyasında öğe bir örneğini oluşturur <xref:System.Windows.Navigation.NavigationWindow> sınıfı. Daha fazla bilgi için [gezintiye genel bakış](../app-development/navigation-overview.md).

5. Kaldırma <xref:System.Windows.Controls.Grid> öğeleri arasında <xref:System.Windows.Navigation.NavigationWindow> etiketler.

6. XAML kodunu şu özelliklerde değişiklik <xref:System.Windows.Navigation.NavigationWindow> öğesi:

    - Ayarlama <xref:System.Windows.Window.Title%2A> özelliğini "`ExpenseIt`".

    - Ayarlama <xref:System.Windows.FrameworkElement.Height%2A> özelliğini 350 piksel.

    - Ayarlama <xref:System.Windows.FrameworkElement.Width%2A> özelliğini 500 piksel.

    XAML, Visual Basic için aşağıdaki gibi görünmelidir:

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    Ve aşağıdaki gibi C#:

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. Açık *MainWindow.xaml.vb* veya *MainWindow.xaml.cs*.

    Bildirilen olaylarını işlemek için kod içeren bir arka plan kod dosyası bu dosyadır *MainWindow.xaml*. Bu dosya, XAML içinde tanımlanan penceresi için bir parçalı sınıf içerir.

8. Kullanıyorsanız C#, değiştirme `MainWindow` öğesinden türetilen sınıfın <xref:System.Windows.Navigation.NavigationWindow>. (XAML penceresinde değiştirdiğinizde Visual Basic'te bu otomatik olarak gerçekleşir.) C# Kod artık şu şekilde görünmelidir:

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a>Uygulama için dosyaları Ekle

Bu bölümde, uygulamaya iki sayfaları ve görüntü ekleyeceksiniz.

1. Projeye yeni bir sayfa ekleyin ve adlandırın *`ExpenseItHome.xaml`*:

   1. İçinde **Çözüm Gezgini**, sağ **`ExpenseIt`** projesini düğümünü ve ardından **Ekle** > **sayfa**.

   1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sayfa (WPF)** şablon zaten seçili. Bir ad girin **`ExpenseItHome`** ve ardından **Ekle**.

    Uygulama başlatıldığında görüntülenen ilk sayfa sayfasıdır. İçin harcama raporunu görüntülemek için seçmek için kişi listesi gösterilir.

1. Açık *`ExpenseItHome.xaml`*.

1. Ayarlama <xref:System.Windows.Controls.Page.Title%2A> için "`ExpenseIt - Home`".

1. Ayarlama `DesignHeight` ve `DesignWidth` öğe değerlerini 300 piksel.

    Artık XAML Visual Basic için şu şekilde görünür:

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    Ve aşağıdaki gibi C#:

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. Açık *MainWindow.xaml*.

1. Ekleme bir <xref:System.Windows.Navigation.NavigationWindow.Source%2A> özelliğini <xref:System.Windows.Navigation.NavigationWindow> öğesi ve ayarlamak "`ExpenseItHome.xaml`".

    Bu ayarlar *`ExpenseItHome.xaml`* ilk olarak uygulama başladığında açılır. 

    Visual Basic'te XAML. Örneğin:

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    C# ve:

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Ayrıca **kaynak** özelliğinde **çeşitli** kategorisi **özellikleri** penceresi.
   >
   > ![Özellikler penceresinde Source özelliği](./media/properties-source.png)

1. Başka bir yeni WPF sayfası projeye ekleyin ve adlandırın *ExpenseReportPage.xaml*::

   1. İçinde **Çözüm Gezgini**, sağ **`ExpenseIt`** projesini düğümünü ve ardından **Ekle** > **sayfa**.

   1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sayfa (WPF)** şablonu. Bir ad girin **ExpenseReportPage**ve ardından **Ekle**.

    Bu sayfada, harcama raporlarını seçildiğinde kişinin gösterilir **`ExpenseItHome`** sayfası.

1. Açık *ExpenseReportPage.xaml*.

1. Ayarlama <xref:System.Windows.Controls.Page.Title%2A> için "`ExpenseIt - View Expense`".

1. Ayarlama `DesignHeight` ve `DesignWidth` öğe değerlerini 300 piksel.

    *ExpenseReportPage.xaml* artık Visual Basic'te aşağıdaki gibi görünür:

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    Ve aşağıdaki gibi C#:

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. Açık *ExpenseItHome.xaml.vb* ve *ExpenseReportPage.xaml.vb*, veya *ExpenseItHome.xaml.cs* ve *ExpenseReportPage.xaml.cs*.

    Yeni bir sayfa dosyası oluşturduğunuzda, Visual Studio otomatik olarak oluşturur, *arka plan kod* dosya. Bu arka plan kod dosyaları, kullanıcı girişine yanıt mantığı işler.

    Kodunuz için şunun gibi görünmelidir **`ExpenseItHome`**:

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    Ve aşağıdaki gibi **ExpenseReportPage**:

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. Adlandırılmış resim ekleme *watermark.png* projeye. Kendi görüntünüzü oluşturma,'nden örnek kodu dosyasını kopyalayın veya bunu [burada](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).

    1. Proje düğümüne sağ tıklayıp **Ekle** > **var olan öğe**, veya basın **Shift**+**Alt** + **A**.

    2. İçinde **varolan öğeyi Ekle** iletişim kutusunda, dosya filtresi aşağıdaki seçeneklerden birine ayarlayın **tüm dosyaları** veya **görüntü dosyaları**, kullanın ve ardından istediğiniz görüntü dosyasına Gözat **Ekle** .

## <a name="build-and-run-the-application"></a>Uygulaması derleme ve çalıştırma

1. Uygulaması derleme ve çalıştırma için basın **F5** veya **hata ayıklamayı Başlat** gelen **hata ayıklama** menüsü.

    Uygulama ile aşağıdaki çizimde <xref:System.Windows.Navigation.NavigationWindow> düğmeleri:

    ![ExpenseIt örnek ekran görüntüsü](./media/gettingstartedfigure1.png)

2. Visual Studio'ya dönmek için uygulamayı kapatın.

## <a name="create-the-layout"></a>Düzen oluştur

Düzeni, kullanıcı Arabirimi öğeleri yerleştirmek için sıralı bir yol sağlar ve bir kullanıcı Arabirimi yeniden boyutlandırıldığında boyutunu ve konumunu söz konusu öğelerin da yönetir. Genellikle bir düzen aşağıdaki düzen denetimlerden birini oluşturursunuz:

- <xref:System.Windows.Controls.Canvas> -İçinde açıkça alt öğeleri tuval alanına göre koordinatlar kullanarak yerleştirebilir bir alan tanımlar.
- <xref:System.Windows.Controls.DockPanel> -Burada, alt öğeleri yatay veya dikey olarak birbirlerine göreli dizebileceğiniz bir alan tanımlar.
- <xref:System.Windows.Controls.Grid> -Sütun ve satırlardan oluşan esnek bir kılavuz alanı tanımlar.
- <xref:System.Windows.Controls.StackPanel> -Alt öğeleri yatay veya dikey olarak yönlendirilebilir tek bir çizgi yerleştirir.
- <xref:System.Windows.Controls.VirtualizingStackPanel> -Düzenler ve içerik yatay veya dikey yönlendirilmiş tek bir satırda sanallaştırır.
- <xref:System.Windows.Controls.WrapPanel> -Sonraki satır kutusunun kenarında içerik bozucu sağa doğru ardışık konumlarını alt öğeleri kalmadı. Sonraki sıralama yukarıdan aşağıya veya Yönlendirme özelliğinin değerine bağlı olarak bir soldan sağa ardışık olarak gerçekleşir.

Bu düzen denetimlerin her birinden alt öğeleri için belirli bir düzen türünü destekler. `ExpenseIt` sayfaları yeniden boyutlandırılıp boyutlandırılamayacağını ve her sayfanın diğer öğeleri Yatayda ve Dikeyde düzenlenmiş öğelere sahiptir. Bu örnekte, <xref:System.Windows.Controls.Grid> uygulama için Düzen öğesi kullanılır.

> [!TIP]
> Hakkında daha fazla bilgi için <xref:System.Windows.Controls.Panel> öğeler, bkz [panellere genel bakış](../controls/panels-overview.md). Düzen hakkında daha fazla bilgi için bkz. [Düzen](../advanced/layout.md).

Bu bölümde, bir tek sütunlu tablo üç satır ve 10-piksel kenar boşluğu ile sütun ve satır tanımlara ekleyerek oluşturduğunuz <xref:System.Windows.Controls.Grid> içinde *`ExpenseItHome.xaml`*.

1. İçinde *`ExpenseItHome.xaml`* ayarlayın <xref:System.Windows.FrameworkElement.Margin%2A> özelliği <xref:System.Windows.Controls.Grid> ", sol, üst, sağ ve alt kenar boşlukları için karşılık gelen 10,0,10,10 şeklinde", öğe:

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Ayrıca **kenar boşluğu** değerler **özellikleri** penceresi altında **Düzen** kategorisi:
   >
   > ![Özellikler penceresinde kenar boşluğu değerleri](./media/properties-margin.png)

2. Aşağıdaki XAML arasında ekleme <xref:System.Windows.Controls.Grid> etiketleri satır ve sütun tanımları oluşturmak için:

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <xref:System.Windows.Controls.RowDefinition.Height%2A> İki satır kümesine <xref:System.Windows.GridLength.Auto%2A>, satırları içeriği temel satırları boyutlandırılır anlamına gelir. Varsayılan <xref:System.Windows.Controls.RowDefinition.Height%2A> olduğu <xref:System.Windows.GridUnitType.Star> boyutlandırma, satır yüksekliğini kullanılabilir alanı ağırlıklı oranını olduğu anlamına gelir. Örneğin her iki satır varsa bir <xref:System.Windows.Controls.RowDefinition.Height%2A> , "*", sahip oldukları her ikiye kadar kullanılabilir alan olduğundan bir yükseklik.

    <xref:System.Windows.Controls.Grid> Artık aşağıdaki XAML içermelidir:

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Denetimler ekleme

Bu bölümde, giriş sayfası, harcama raporu görüntülemek için tek bir kişi seçtiğiniz kişi listesini gösteren kullanıcı Arabirimi güncelleştireceksiniz. Kullanıcıların uygulamanızla etkileşmesini UI nesneleri denetimlerdir. Daha fazla bilgi için [denetimleri](../controls/index.md).

Bu kullanıcı Arabirimi oluşturmak için aşağıdaki öğelere ekleyeceksiniz *`ExpenseItHome.xaml`*:

- A <xref:System.Windows.Controls.ListBox> (için kişi listesi).
- A <xref:System.Windows.Controls.Label> (için liste başlığı).
- A <xref:System.Windows.Controls.Button> (listede seçilen kişi için harcama raporlarını görüntülemek için tıklayın için).

Her denetim bir satırda yerleştirilir <xref:System.Windows.Controls.Grid> ayarlayarak <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> ekli özellik. Ekli özellikler hakkında daha fazla bilgi için bkz. [ekli özelliklere genel bakış](../advanced/attached-properties-overview.md).

1. İçinde *`ExpenseItHome.xaml`*, aşağıdaki XAML bir yerde arasında ekleme <xref:System.Windows.Controls.Grid> etiketler:

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Denetimlere sürükleyerek de oluşturabilirsiniz **araç kutusu** tasarım penceresini ve özelliklerini ayarlayarak ardından penceresinden **özellikleri** penceresi.

2. Derleme ve uygulamayı çalıştırın.

    Aşağıdaki çizim, oluşturduğunuz denetimleri gösterir:

    ![ExpenseIt örnek ekran görüntüsü](./media/gettingstartedfigure2.png)

3. Visual Studio'ya dönmek için uygulamayı kapatın.

## <a name="add-an-image-and-a-title"></a>Resim ve Başlık Ekle

Bu bölümde, giriş sayfası kullanıcı Arabirimi, görüntü ve sayfa başlığı ile güncelleştireceksiniz.

1. İçinde *`ExpenseItHome.xaml`*, başka bir sütuna eklemek <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> sabit ile <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 piksel:

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. Başka bir satır <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, toplam dört satır için:

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. Denetimleri ayarlayarak ikinci sütuna Taşı <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> özelliği 1 her üç denetimleri (Kenarlık, liste kutusu ve düğme).

4. Her denetim artırılarak bir satır aşağı taşı, <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> her üç denetimleri (Kenarlık, liste kutusu ve düğme) ve kenarlık öğesinin 1 değeriyle.

   XAML üç denetim için aşağıdaki gibi görünür:

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. Ayarlama <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> özelliğini *watermark.png* görüntü dosyası, aşağıdaki XAML herhangi bir yere arasında ekleyerek `<Grid>` ve `</Grid>` etiketler:

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. Önce <xref:System.Windows.Controls.Border> öğe, Ekle bir <xref:System.Windows.Controls.Label> "Harcama Raporu Görüntüle" içeriğe sahip. Bu sayfa başlığının etiketidir.

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. Derleme ve uygulamayı çalıştırın.

Hangi yeni eklediğiniz sonucu aşağıda gösterilmektedir:

![ExpenseIt örnek ekran görüntüsü](./media/gettingstartedfigure3.png)

## <a name="add-code-to-handle-events"></a>Olayları işlemek için kod ekleyin

1. İçinde *`ExpenseItHome.xaml`*, ekleme bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisine <xref:System.Windows.Controls.Button> öğesi. Daha fazla bilgi için [nasıl yapılır: Basit olay işleyicisi oluşturun](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. Açık *`ExpenseItHome.xaml.vb`* veya *`ExpenseItHome.xaml.cs`*.

3. Aşağıdaki kodu ekleyin `ExpenseItHome` sınıfı bir düğme eklemek için tıklama olay işleyicisi. Olay işleyicisi açılır **ExpenseReportPage** sayfası.

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>ExpenseReportPage için kullanıcı Arabirimi oluşturma

*ExpenseReportPage.xaml* seçili kişi için harcama raporlarını görüntüler **`ExpenseItHome`** sayfası. Bu bölümde, kullanıcı Arabiriminde oluşturacaksınız **ExpenseReportPage**. Ayrıca, arka plan ekleyebilir ve çeşitli kullanıcı Arabirimi öğeleri için renk dolgu.

1. Açık *ExpenseReportPage.xaml*.

2. Aşağıdaki XAML arasında ekleme <xref:System.Windows.Controls.Grid> etiketler:

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Bu kullanıcı arabirimini benzer *`ExpenseItHome.xaml`* rapor verilerini görüntülenen dışında bir <xref:System.Windows.Controls.DataGrid>.

3. Derleme ve uygulamayı çalıştırın.

4. Seçin **görünümü** düğmesi.

    Harcama Raporu sayfası görüntülenir. Ayrıca geri gezinme düğmesi etkinleştirilir dikkat edin.

Eklenen kullanıcı Arabirimi öğeleri aşağıdaki çizimde *ExpenseReportPage.xaml*.

![ExpenseIt örnek ekran görüntüsü](./media/gettingstartedfigure4.png)

## <a name="style-controls"></a>Stil denetimleri

Çeşitli öğelerin görünümünü genellikle bir kullanıcı arabiriminde aynı türdeki tüm öğeler için aynıdır. Kullanıcı Arabirimi kullanan [stilleri](../controls/styling-and-templating.md) görünümleri arasında birden çok öğe yeniden kullanılabilir hale getirmek için. Yeniden kullanılırlığı XAML oluşturulmasını ve yönetimini basitleştirmeye yardımcı olur. Bu bölümde, stiller, önceki adımlarda tanımlanan öğe başına özniteliklerini değiştirir.

1. Açık *Application.xaml* veya *App.xaml*.

2. Aşağıdaki XAML arasında ekleme <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> etiketler:

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Bu XAML aşağıdaki stilleri ekler:

    - `headerTextStyle`: Sayfa başlığı biçimlendirmek için <xref:System.Windows.Controls.Label>.

    - `labelStyle`: Biçimlendirilecek <xref:System.Windows.Controls.Label> kontrol eder.

    - `columnHeaderStyle`: Biçimlendirilecek <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.

    - `listHeaderStyle`: List üstbilgisi biçimlendirmek için <xref:System.Windows.Controls.Border> kontrol eder.

    - `listHeaderTextStyle`: List üstbilgisi biçimlendirmek için <xref:System.Windows.Controls.Label>.

    - `buttonStyle`: Biçimlendirilecek <xref:System.Windows.Controls.Button> üzerinde `ExpenseItHome.xaml`.

    Stilleri kaynakları ve alt olduğunu fark <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> özellik öğesi. Bu konumda, stilleri bir uygulamadaki tüm öğelere uygulanır. Bir .NET uygulamasında kaynakları kullanma örneği için bkz: [kullanım uygulama kaynaklarını](../advanced/how-to-use-application-resources.md).

3. İçinde *`ExpenseItHome.xaml`*, arasındaki her şeyi değiştirin <xref:System.Windows.Controls.Grid> aşağıdaki XAML ile öğeleri:

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    Gibi özellikler <xref:System.Windows.VerticalAlignment> ve <xref:System.Windows.Media.FontFamily> her denetimin görünümünü tanımlamak kaldırılır ve stilleri uygulayarak değiştirilir. Örneğin, `headerTextStyle` harcama raporu görünümü"için" uygulanan <xref:System.Windows.Controls.Label>.

4. Açık *ExpenseReportPage.xaml*.

5. Arasındaki her şeyi değiştirin <xref:System.Windows.Controls.Grid> aşağıdaki XAML ile öğeleri:

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Bu XAML stilleri ekler <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.Border> öğeleri.

6. Derleme ve uygulamayı çalıştırın. Pencere görünümü önceden aynıdır.

    ![ExpenseIt örnek ekran görüntüsü](./media/gettingstartedfigure4.png)

7. Visual Studio'ya dönmek için uygulamayı kapatın.

## <a name="bind-data-to-a-control"></a>Veriyi denetime bağlama

Bu bölümde, çeşitli denetimlere bağlı XML verileri oluşturacaksınız.

1. İçinde *`ExpenseItHome.xaml`*, açılış <xref:System.Windows.Controls.Grid> öğesi oluşturmak için aşağıdaki XAML ekleme bir <xref:System.Windows.Data.XmlDataProvider> her kişi için veri içeren:

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    Veri olarak oluşturulan bir <xref:System.Windows.Controls.Grid> kaynak. Normalde bu verilerin bir dosya olarak yüklenmesi, ancak kolaylık olması için satır içi veriler eklenir.

2. İçinde `<Grid.Resources>` öğesi, aşağıdaki `<xref:System.Windows.DataTemplate>` içinde verilerin nasıl görüntüleneceğini tanımlar <xref:System.Windows.Controls.ListBox>, sonra `<XmlDataProvider>` öğesi:

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    Veri şablonları hakkında daha fazla bilgi için bkz. [veri şablonu oluşturmaya genel bakış](../data/data-templating-overview.md).

3. Varolan <xref:System.Windows.Controls.ListBox> aşağıdaki XAML ile:

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Bu XAML bağlar <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği <xref:System.Windows.Controls.ListBox> veri kaynağı ve veri şablonu olarak geçerli <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.

## <a name="connect-data-to-controls"></a>Denetimlere veri bağlama

Ardından, seçili adını almak için kod ekleyeceksiniz **`ExpenseItHome`** sayfasında ve oluşturucusuna iletmektir **ExpenseReportPage**. **ExpenseReportPage** denetimlerin ne tanımlanır geçirilen öğe ile veri bağlamını ayarlar içinde *ExpenseReportPage.xaml* bağlayın.

1. Açık *ExpenseReportPage.xaml.vb* veya *ExpenseReportPage.xaml.cs*.

2. Seçilen kişiyi harcama raporu verilerini geçirebilirsiniz. Bu nedenle bir nesne alan bir oluşturucu ekleyin.

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Açık *`ExpenseItHome.xaml.vb`* veya *`ExpenseItHome.xaml.cs`*.

4. Değişiklik <xref:System.Windows.Controls.Primitives.ButtonBase.Click> seçilen kişiyi harcama raporu verilerini geçirme yeni oluşturucuyu çağırmak için olay işleyicisi.

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Veri şablonları ile stil verileri

Bu bölümde, veri şablonları kullanarak verilere bağlı listeler her öğe için kullanıcı Arabirimi güncelleştireceksiniz.

1. Açık *ExpenseReportPage.xaml*.

2. "Name" ve "Departman" içeriğini bağlama <xref:System.Windows.Controls.Label> uygun veri öğelerine kaynak özelliği. Veri bağlama hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md).

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Açılış <xref:System.Windows.Controls.Grid> öğesi, harcama raporu verilerini görüntülemek nasıl tanımlamak aşağıdaki veri şablonları ekleyin:

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. Değiştirin <xref:System.Windows.Controls.DataGridTextColumn> öğelerle <xref:System.Windows.Controls.DataGridTemplateColumn> altında <xref:System.Windows.Controls.DataGrid> öğesi ve şablonlar uygulayabilirsiniz.

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Derleme ve uygulamayı çalıştırın.

6. Bir kişi seçin ve ardından **görünümü** düğmesi.

Her iki sayfaları aşağıdaki resimde gösterilmektedir `ExpenseIt` uygulama denetimleri, düzeni, stiller, veri bağlama ve uygulanan veri şablonları:

![ExpenseIt örnek ekran görüntüleri](./media/gettingstartedfigure5.png)

> [!NOTE]
> Bu örnek, belirli bir WPF özelliğini gösterir ve güvenlik, yerelleştirme ve erişilebilirlik gibi şeyler için tüm en iyi uygulamaları izleyin değil. WPF ve .NET uygulama geliştirme en iyi yöntemler ilişkin kapsamlı bilgi için aşağıdaki konulara bakın:
>
> - [Erişilebilirlik](../../ui-automation/accessibility-best-practices.md)
>
> - [Güvenlik](../security-wpf.md)
>
> - [WPF Genelleştirme ve yerelleştirme](../advanced/wpf-globalization-and-localization-overview.md)
>
> - [WPF Performans](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu izlenecek yolda çeşitli teknikler Windows Presentation Foundation (WPF) kullanarak bir kullanıcı Arabirimi oluşturma hakkında bilgi edindiniz. Artık verilere bağlı .NET uygulaması yapı taşları ilgili temel bilgilere sahipsiniz. WPF mimarisi ve programlama modelleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [WPF mimarisi](../advanced/wpf-architecture.md)
- [XAML genel bakış (WPF)](../advanced/xaml-overview-wpf.md)
- [Bağımlılık özelliklerine genel bakış](../advanced/dependency-properties-overview.md)
- [Düzen](../advanced/layout.md)

Uygulamaları oluşturma hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Uygulama geliştirme](../app-development/index.md)
- [Denetimler](../controls/index.md)
- [Veri bağlamaya genel bakış](../data/data-binding-overview.md)
- [Grafikler ve multimedya](../graphics-multimedia/index.md)
- [WPF'deki Belgeler](../advanced/documents-in-wpf.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Panellere genel bakış](../controls/panels-overview.md)
- [Veri şablonu oluşturmaya genel bakış](../data/data-templating-overview.md)
- [Bir WPF uygulaması oluşturma](../app-development/building-a-wpf-application-wpf.md)
- [Stilleri ve şablonları](../controls/styles-and-templates.md)
