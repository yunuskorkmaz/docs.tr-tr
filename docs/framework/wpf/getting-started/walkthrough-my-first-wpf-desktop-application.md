---
title: "İzlenecek yol: İlk WPF Masaüstü Uygulamam"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
caps.latest.revision: "71"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 16ed99181f8462e805638b5d3881464b16f21177
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>İzlenecek yol: İlk WPF Masaüstü Uygulamam
Bu kılavuzda geliştirilmesini tanıtılmaktadır bir [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] en yaygın olan öğeleri içeren uygulama [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar: [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] biçimlendirme, arka plan kodu, uygulama tanımları, denetimleri, düzeni veri bağlama ve stiller. 
  
 Bu kılavuz, basit bir geliştirme size rehberlik eder [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aşağıdaki adımları kullanarak uygulama. 
  
-   Tanımlama [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulamanın görünümünü tasarlamak için [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. 
  
-   Uygulamanın davranışını oluşturmak için kod yazma. 
  
-   Uygulamasını yönetmek için bir uygulama tanımını oluşturma. 
  
-   Denetimler ekleme ve uygulama oluşturmak için düzen oluşturma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. 
  
-   Bir uygulamanın genelinde tutarlı bir görünüm oluşturmak için stiller oluşturma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. 
  
-   Bağlama [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] her ikisine de verilere doldurmak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] veri ve canlı verileri ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] eşitlenir. 
  
 İzlenecek yol ucu tarafından bir tek başına oluşturacaksınız [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] kullanıcıların seçilen kişiler için harcama raporlarını görüntülemesine olanak sağlayan uygulama. Uygulamayı birkaç oluşacaktır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tarayıcı stili pencerede barındırılan sayfaları. 
  
 Bu izlenecek yolu oluşturmak için kullanılan örnek kod için kullanılabilir [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] ve [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] adresindeki [WPF uygulamalarını giriş](http://go.microsoft.com/fwlink/?LinkID=160008). 

## <a name="prerequisites"></a>Önkoşullar  

- [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]veya üzeri

Visual Studio en son sürümünü yükleme hakkında daha fazla bilgi için bkz: [Visual Studio yükleme](/visualstudio/install/install-visual-studio).
  
## <a name="creating-the-application-project"></a>Uygulama projesi oluşturma  
 Bu bölümde, uygulama tanımı, iki sayfaları ve görüntü içeren uygulama altyapısı oluşturun. 
  
1. Visual Basic veya Visual C# adlı yeni bir WPF uygulaması projesi oluşturduğunuzda `ExpenseIt`. Daha fazla bilgi için bkz: [nasıl yapılır: yeni bir WPF uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82). 
  
    > [!NOTE]
    >  Bu kılavuzda kullanılır <xref:System.Windows.Controls.DataGrid> .NET Framework 4'te kullanılabilir denetim. Sonraki veya projeniz .NET Framework 4 hedefleyen emin olun. Daha fazla bilgi için bkz:[nasıl yapılır: .NET Framework sürümü hedef](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework). 
  
2. Application.xaml (Visual Basic) veya App.xaml (C#) açın. 
  
     Bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya tanımlayan bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama ve uygulama kaynaklarını. Bu dosyayı belirtmek için de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] otomatik olarak uygulama başladığında; gösteren bu durumda, MainWindow.xaml. 
  
     [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Visual Basic'te gibi görünmelidir:  
  
    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]  
  
     Ya da böyle C#:  
  
    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]  
  
3. MainWindow.xaml açın. 
  
     Bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası, uygulamanızın ana penceresidir ve sayfalarda oluşturulan içeriği görüntüler. <xref:System.Windows.Window> Sınıfı başlık, boyut veya simge, gibi bir pencere özelliklerini tanımlar ve kapatma veya gizleme gibi olayları işler. 
  
4. Değişiklik <xref:System.Windows.Window> öğesine bir <xref:System.Windows.Navigation.NavigationWindow>. 
  
     Bu uygulama kullanıcı etkileşimi bağlı olarak farklı içerik gider. Bu nedenle, ana <xref:System.Windows.Window> için değiştirilmesi gereken bir <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow>tüm özelliklerini devralır <xref:System.Windows.Window>. <xref:System.Windows.Navigation.NavigationWindow> XAML dosyası öğesinde bir örneğini oluşturur <xref:System.Windows.Navigation.NavigationWindow> sınıfı. Daha fazla bilgi için bkz: [Gezinti genel bakış](../../../../docs/framework/wpf/app-development/navigation-overview.md). 
  
5. Aşağıdaki özellikleri değiştirin <xref:System.Windows.Navigation.NavigationWindow> öğe:  
  
    -   Ayarlama <xref:System.Windows.Window.Title%2A> özelliğini "ExpenseIt". 
  
    -   Ayarlama <xref:System.Windows.FrameworkElement.Width%2A> özelliğini 500 piksel. 
  
    -   Ayarlama <xref:System.Windows.FrameworkElement.Height%2A> özelliğini 350 piksel. 
  
    -   Kaldırma <xref:System.Windows.Controls.Grid> öğeleri arasında <xref:System.Windows.Navigation.NavigationWindow> etiketler. 
  
     [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Visual Basic'te gibi görünmelidir:  
  
    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]  
  
     Ya da böyle C#:  
  
    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]  
  
6. MainWindow.xaml.vb veya MainWindow.xaml.cs açın. 
  
     Bu dosya MainWindow.xaml içinde bildirilen olayları işlemek için kod içeren bir arka plan kodu dosyasıdır. Bu dosya XAML içinde tanımlanan penceresi için bir parçalı sınıf içerir. 
  
7. C# kullanıyorsanız değiştirme `MainWindow` öğesinden türetilen sınıf <xref:System.Windows.Navigation.NavigationWindow>. 
  
     XAML penceresinde değiştirdiğinizde, Visual Basic'te, bu otomatik olarak gerçekleşir. 
  
     Kodunuzu aşağıdaki gibi görünmelidir. 
  
    [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
    [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]  
  
## <a name="adding-files-to-the-application"></a>Dosyalar için uygulama ekleme  
 Bu bölümde, uygulamaya iki sayfaları ve görüntü ekleyin. 
  
1. Yeni sayfa (WPF) adlı projeye eklemek `ExpenseItHome.xaml`. Daha fazla bilgi için bkz: [nasıl yapılır: bir WPF projesi için yeni öğeler eklemek](http://msdn.microsoft.com/library/17e6b238-fc32-4385-98ef-2f66ca09d9ad). 
  
     Uygulama başlatıldığında görüntülenen ilk sayfa sayfasıdır. Bir kullanıcı için harcama raporunu göstermek için bir kişinin seçebileceği kişilerin listesini gösterir. 
  
2. ExpenseItHome.xaml açın. 
  
3. Ayarlama <xref:System.Windows.Controls.Page.Title%2A> "ExpenseIt - Giriş". 
  
     [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Visual Basic'te gibi görünmelidir:  
  
    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]  
  
     Veya bu C#:  
  
    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]  
  
4. MainWindow.xaml açın. 
  
5. Ayarlama <xref:System.Windows.Navigation.NavigationWindow.Source%2A> özellikte <xref:System.Windows.Navigation.NavigationWindow> "ExpenseItHome.xaml" için. 
  
     Bu uygulama başladığında açılan ilk sayfa olarak ExpenseItHome.xaml ayarlar. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Visual Basic'te gibi görünmelidir:  
  
    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]  
  
     Veya bu C#:  
  
    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]  
  
6. Yeni sayfa (WPF) adlı projeye eklemek `ExpenseReportPage.xaml`. 
  
     Bu sayfa, ExpenseItHome.XAML üzerinde seçili kişi için harcama raporunu gösterir. 
  
7. ExpenseReportPage.xaml açın. 
  
8. Ayarlama <xref:System.Windows.Controls.Page.Title%2A> "ExpenseIt - görünüm gider". 
  
     [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Visual Basic'te gibi görünmelidir:  
  
    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]  
  
     Veya bu C#:  
  
    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]  
  
9. ExpenseItHome.xaml.vb ve ExpenseReportPage.xaml.vb veya ExpenseItHome.xaml.cs ve ExpenseReportPage.xaml.cs açın. 
  
     Yeni bir sayfa dosyası oluşturduğunuzda, Visual Studio arka plan kod dosyasından otomatik olarak oluşturur. Bu arka plan kodu dosyaları için kullanıcı girişine yanıt mantığını işler. 
  
     Kodunuzu aşağıdaki gibi görünmelidir. 
  
    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]  
  
    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]  
  
10. Projeye watermark.png adlı bir resim ekleyin. Kendi görüntünüzü oluşturabilir veya örnek koddan dosyasını kopyalayın. Daha fazla bilgi için bkz: [NIB: nasıl yapılır: varolan bir proje öğeleri Ekle](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3). 

## <a name="building-and-running-the-application"></a>Oluşturma ve uygulama çalıştırma  
 Bu bölümde, derleme ve uygulamayı çalıştırın. 
  
1. Derleme ve seçin veya F5 tuşuna basarak uygulamayı çalıştırma **hata ayıklamayı Başlat** gelen **hata ayıklama** menüsü. 
  
     Uygulamayla birlikte aşağıda gösterilmiştir <xref:System.Windows.Navigation.NavigationWindow> düğmeler. 
  
     ![ExpenseIt örnek ekran görüntüsü](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")  
  
2. Geri dönmek için uygulamayı kapatmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]. 
  
## <a name="creating-the-layout"></a>Düzen oluşturma  
 Düzen yerleştirmek için sıralı bir yol sağlar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğeleri ve boyutunu ve konumunu bu öğelerin da yönetir, bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] boyutlandırılır. Genellikle bir düzen aşağıdaki düzen denetimlerinden biri ile oluşturursunuz:  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 Bu düzen denetimlerinin her biri kendi alt öğeleri için özel türde bir düzen destekler. ExpenseIt sayfaları yeniden boyutlandırılabilir ve her sayfanın diğer öğeleri yatay ve dikey olarak düzenlenmiş öğesine sahip. Sonuç olarak, <xref:System.Windows.Controls.Grid> uygulama için ideal Düzen öğesidir. 
  
> [!NOTE]
>  Hakkında daha fazla bilgi için <xref:System.Windows.Controls.Panel> öğeler, bkz [paneller genel bakış](../../../../docs/framework/wpf/controls/panels-overview.md). Düzen hakkında daha fazla bilgi için bkz: [düzeni](../../../../docs/framework/wpf/advanced/layout.md). 
  
 Bölümünde, tek sütunlu bir tablo üç satır ve 10 piksel kenar boşluğu ile sütun ve satır tanımları ekleyerek oluşturduğunuz <xref:System.Windows.Controls.Grid> ExpenseItHome.XAML içinde. 
  
1. ExpenseItHome.xaml açın. 
  
2. Ayarlama <xref:System.Windows.FrameworkElement.Margin%2A> özelliği <xref:System.Windows.Controls.Grid> , sol, üst, sağ ve alt kenar boşlukları için karşılık gelen "10,0,10,10"şeklinde öğesi. 
  
3. Aşağıdakileri ekleyin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arasında <xref:System.Windows.Controls.Grid> satır ve sütun tanımları oluşturmak için etiketler. 
  
    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]  
  
     <xref:System.Windows.Controls.RowDefinition.Height%2A> İki satır kümesine <xref:System.Windows.GridLength.Auto%2A> satırları boyutta olması anlamına temel satırları içerikte. Varsayılan <xref:System.Windows.Controls.RowDefinition.Height%2A> olan <xref:System.Windows.GridUnitType.Star> satır kullanılabilir alan ağırlıklı bir kısmının olacağı anlamına gelir boyutlandırma. Her iki satır yüksekliği varsa, örneğin "*", her kullanılabilir alan yarısıdır yüksekliğe sahip olacaktır.  
  
     <xref:System.Windows.Controls.Grid> Aşağıdaki XAML gibi görünmelidir:  
  
    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]  
  
## <a name="adding-controls"></a>Denetimler ekleme  
 Bu bölümde, giriş sayfası [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kişilerin listesi kullanıcıların seçili kişiler için harcama raporunu göstermek için gösterebileceği olduğunu göstermek üzere güncelleştirilir. Denetimler uygulamanız ile etkileşime girmesine izin veren UI nesneleridir. Daha fazla bilgi için bkz: [denetimleri](../../../../docs/framework/wpf/controls/index.md). 
  
 Bu oluşturmak için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], aşağıdaki öğeleri ExpenseItHome.xaml'e eklenir:  
  
-   <xref:System.Windows.Controls.ListBox>(listesi kişiler için). 
  
-   <xref:System.Windows.Controls.Label>(Liste üstbilgisi için). 
  
-   <xref:System.Windows.Controls.Button>(listede seçilen kişi için harcama raporunu görüntülemek için tıklatın için). 
  
 Her denetim bir satırda yerleştirilir <xref:System.Windows.Controls.Grid> ayarlayarak <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> özelliği eklenmiş. Ekli özellikler hakkında daha fazla bilgi için bkz: [bağlı özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/attached-properties-overview.md). 
  
1. ExpenseItHome.xaml açın. 
  
2. Aşağıdakileri ekleyin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arasında <xref:System.Windows.Controls.Grid> etiketler. 
  
    [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]  
  
3. Derleme ve uygulamayı çalıştırın. 
  
 Aşağıdaki çizim, bu bölümdeki XAML tarafından oluşturulan denetimleri göstermektedir. 
  
 ![ExpenseIt örnek ekran görüntüsü](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")  
  
## <a name="adding-an-image-and-a-title"></a>Görüntüyü ve başlık ekleme  
 Bu bölümde, giriş sayfası [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] resim ve sayfa başlığı ile güncelleştirilir. 
  
1. ExpenseItHome.xaml açın. 
  
2. Başka bir sütuna eklemek <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> bir sabit ile <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 piksel. 
  
    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]  
  
3. Başka bir satır ekleyin <xref:System.Windows.Controls.Grid.RowDefinitions%2A>. 
  
    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]  
  
4. Denetimleri ayarlayarak ikinci sütun taşımak <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> 1. Her denetim artırarak bir satır aşağı taşı <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> 1. 
  
    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]  
  
5. Ayarlama <xref:System.Windows.Controls.Panel.Background%2A> , <xref:System.Windows.Controls.Grid> watermark.png resim dosyası olarak. 
  
    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]  
  
6. Önce <xref:System.Windows.Controls.Border>, ekleme bir <xref:System.Windows.Controls.Label> "Gider sayfanın başlığı olması için raporu görüntüle" içeriğe sahip. 
  
    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]  
  
7. Derleme ve uygulamayı çalıştırın. 
  
 Aşağıdaki çizimde, bu bölümde sonuçlarını gösterir. 
  
 ![ExpenseIt örnek ekran görüntüsü](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")  
  
## <a name="adding-code-to-handle-events"></a>Olayları işlemek için kod ekleme  
  
1. ExpenseItHome.xaml açın. 
  
2. Ekleme bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisine <xref:System.Windows.Controls.Button> öğesi. Daha fazla bilgi için bkz: [nasıl yapılır: basit bir olay işleyicisi oluşturun](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480). 
  
    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]  
  
3. ExpenseItHome.xaml.vb veya ExpenseItHome.xaml.cs açın. 
  
4. Aşağıdaki kodu ekleyin <xref:System.Windows.Controls.Primitives.ButtonBase.Click> ExpenseReportPage.xaml dosyaya gitmek için penceresini neden olan olay işleyicisi. 
  
    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]  
  
## <a name="creating-the-ui-for-expensereportpage"></a>ExpenseReportPage için kullanıcı Arabirimi oluşturma  
 ExpenseReportPage.xaml, ExpenseItHome.XAML üzerinde seçili kişi için harcama raporunu görüntüler. Bu bölümde denetimleri ekler ve oluşturur [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ExpenseReportPage.xaml için. Bu bölümde Ayrıca arka plan ve dolgu renklerini çeşitli ekler [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğeleri. 
  
1. ExpenseReportPage.xaml açın. 
  
2. Aşağıdaki XAML'i ekleyin <xref:System.Windows.Controls.Grid> etiketler. 
  
     Bu UI ExpenseItHome.XAML üzerinde rapor verilerini görüntülenen dışında oluşturulan UI benzer bir <xref:System.Windows.Controls.DataGrid>. 
  
    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]  
  
3. Derleme ve uygulamayı çalıştırın. 
  
    > [!NOTE]
    >  Bir hata alırsanız <xref:System.Windows.Controls.DataGrid> bulunamadı veya olmayabilir, projeniz .NET Framework 4 veya sonrasını hedefleyen emin olun. Daha fazla bilgi için bkz: [nasıl yapılır: .NET Framework sürümü hedef](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework). 
  
4. Tıklatın **Görünüm** düğmesi. 
  
     Harcama Raporu sayfası görüntülenir. 
  
 Aşağıdaki çizimde gösterildiği [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ExpenseReportPage.xaml'e eklenen öğeleri. Geri gezinti düğmesi etkinleştirilir dikkat edin. 
  
 ![ExpenseIt örnek ekran görüntüsü](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")  
  
## <a name="styling-controls"></a>Stil denetimleri  
 Çeşitli öğelerin görünümü genellikle içindeki aynı türden tüm öğeler için aynı olabilir bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]görünümlerin çoklu öğeler arasında yeniden kullanılabilir olması için stilleri kullanır. Kullanılırlığı yardımcı basitleştirmek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] oluşturma ve yönetme. Stilleri hakkında daha fazla bilgi için bkz: [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md). Bu bölümde stilleri önceki adımlarda tanımlanan öğesi başına özniteliklerini değiştirir. 
  
1. Application.XAML veya App.xaml açın. 
  
2. Aşağıdaki XAML'i ekleyin <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> etiketler:  
  
    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]  
  
     Bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aşağıdaki stilleri ekler:  
  
    -  `headerTextStyle`: Sayfa başlığı Biçimlendirilecek <xref:System.Windows.Controls.Label>. 
  
    -  `labelStyle`: Biçimlendirilecek <xref:System.Windows.Controls.Label> kontrol eder. 
  
    -  `columnHeaderStyle`: Biçimlendirilecek <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>. 
  
    -  `listHeaderStyle`: List üstbilgisi Biçimlendirilecek <xref:System.Windows.Controls.Border> kontrol eder. 
  
    -  `listHeaderTextStyle`: List üstbilgisi Biçimlendirilecek <xref:System.Windows.Controls.Label>. 
  
    -  `buttonStyle`: Biçimlendirilecek <xref:System.Windows.Controls.Button> ExpenseItHome.XAML üzerinde. 
  
     Stilleri kaynakları ve alt öğeleri olduğuna dikkat edin <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> özellik öğesi. Bu konumda stiller tüm öğelere uygulanır. Kaynaklarında kullanma örneği için bir [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] uygulama, bkz: [kullanım uygulama kaynakları](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md). 
  
3. ExpenseItHome.xaml açın. 
  
4. Arasındaki her şeyi değiştirin <xref:System.Windows.Controls.Grid> öğeleri aşağıdaki XAML ile. 
  
    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]  
  
     Gibi özellikler <xref:System.Windows.VerticalAlignment> ve <xref:System.Windows.Media.FontFamily> her denetimin görünümünü tanımlamak kaldırılır ve stiller uygulayarak değiştirilir. Örneğin, `headerTextStyle` harcama raporu görünümü"için" uygulanan <xref:System.Windows.Controls.Label>. 
  
5. ExpenseReportPage.xaml açın. 
  
6. Arasındaki her şeyi değiştirin <xref:System.Windows.Controls.Grid> öğeleri aşağıdaki XAML ile. 
  
    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]  
  
     Bu stiller ekler <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.Border> öğeleri. 
  
7. Derleme ve uygulamayı çalıştırın. 
  
     Ekledikten sonra [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stilleri ile güncelleştirilmiş önce yaptığınız gibi bu bölümde, uygulama aynı arar. 
  
## <a name="binding-data-to-a-control"></a>Denetimine veri bağlama  
 Bu bölümde, oluşturduğunuz [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] çeşitli denetimlere bağlı veri. 
  
1. ExpenseItHome.xaml açın. 
  
2. Açtıktan sonra <xref:System.Windows.Controls.Grid> öğesi oluşturmak için aşağıdaki XAML eklemek bir <xref:System.Windows.Data.XmlDataProvider> , her kişi için veriler içerir. 
  
     Veri olarak oluşturulan bir <xref:System.Windows.Controls.Grid> kaynak. Normalde bu dosya olarak yüklenir, ancak kolaylık sağlamak için veriler satır içi eklenir. 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
3. İçinde <xref:System.Windows.Controls.Grid> kaynak, aşağıdakileri ekleyin <xref:System.Windows.DataTemplate>, verilerin nasıl görüntüleneceğini tanımlayan <xref:System.Windows.Controls.ListBox>. Veri şablonları hakkında daha fazla bilgi için bkz: [veri şablonu özeti](../../../../docs/framework/wpf/data/data-templating-overview.md). 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
4. Varolan <xref:System.Windows.Controls.ListBox> aşağıdaki XAML ile. 
  
    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]  
  
     Bu XAML bağlar <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği <xref:System.Windows.Controls.ListBox> veri kaynağı ve veri şablon olarak geçerlidir <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>. 
  
## <a name="connecting-data-to-controls"></a>Verileri denetimlere bağlama  
 Bu bölümde, ExpenseItHome.xaml sayfası üzerindeki kişiler listesinde seçili ve onun oluşturucusunun referansı aktaran güncel öğeyi alan kodu yazma `ExpenseReportPage` örnek oluşturma sırasında. `ExpenseReportPage`hangi denetimlerin ExpenseReportPage.xaml içinde tanımlı olan geçirilen öğe ile veri bağlamını ayarlar bağlayacaksınız. 
  
1. ExpenseReportPage.xaml.vb veya ExpenseReportPage.xaml.cs açın. 
  
2. Seçili kişinin harcama raporu verilerini geçirmek için bir nesne alan bir oluşturucu ekleyin. 
  
    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]  
  
3. ExpenseItHome.xaml.vb veya ExpenseItHome.xaml.cs açın. 
  
4. Değişiklik <xref:System.Windows.Controls.Primitives.ButtonBase.Click> seçili kişinin harcama raporu geçirilen yeni oluşturucuyu çağırmak için olay işleyicisi. 
  
    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]  
  
## <a name="styling-data-with-data-templates"></a>Veri şablonları ile stil verileri  
 Bu bölümde, güncelleştirme [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] veri şablonlarını kullanarak verileri her öğe listelerini bağlı için. 
  
1. ExpenseReportPage.xaml açın. 
  
2. "Name" ve "Departman" içeriğini bağlama <xref:System.Windows.Controls.Label> uygun veri öğelerine kaynak özelliği. Veri bağlama hakkında daha fazla bilgi için bkz: [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md). 
  
    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]  
  
3. Açtıktan sonra <xref:System.Windows.Controls.Grid> öğesi, harcama raporu verilerini görüntülemek nasıl tanımlayan aşağıdaki veri şablonlarını ekleyin.  
    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]  
  
4. Şablonlar için geçerli <xref:System.Windows.Controls.DataGrid> gider gösteren sütunları rapor verileri. 
  
    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]  
  
5. Derleme ve uygulamayı çalıştırın. 
  
6. Bir kişi tıklatıp **Görünüm** düğmesi. 
  
 Aşağıdaki çizimde denetimleri, düzen, stiller, veri bağlama ve uygulanan veri şablonları ile ExpenseIt uygulamasının her iki sayfa gösterir. 
  
 ![ExpenseIt örnek ekran görüntüleri](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")  
  
## <a name="best-practices"></a>Önerilen uygulamalar  
 Bu örnek, belirli bir WPF özelliğini gösterir ve sonuç olarak, uygulama geliştirme en iyi yöntemler izlemez. Kapsamlı için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] uygulama geliştirme en iyi yöntemler, aşağıdaki konulara uygun şekilde bakın:  
  
-   Erişilebilirlik - [en iyi erişilebilirlik uygulamaları](../../../../docs/framework/ui-automation/accessibility-best-practices.md)  
  
-   Güvenlik - [güvenlik](../../../../docs/framework/wpf/security-wpf.md)  
  
-   Yerelleştirme - [WPF Genelleştirme ve yerelleştirme genel bakış](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)  
  
-   Performans - [WPF Uygulama performansı en iyi duruma getirme](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
  
## <a name="whats-next"></a>Sırada ne var?  
 Şimdi oluşturmak için elden en çeşitli teknikler sahip bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kullanarak [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Veri bağlama temel yapı taşlarını geniş bir anlayış şimdi olmalıdır [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] uygulama. Bu konuda halinde kapsamlı, ancak ayrıca artık umarız bazı bu konudaki teknikleri ötesinde kendi keşfedebilirsiniz olasılıklar duygusu vardır. 
  
 WPF mimarisi ve programlama modelleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [WPF Mimarisi](../../../../docs/framework/wpf/advanced/wpf-architecture.md)  
  
-   [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
  
-   [Bağımlılık Özelliklerine Genel Bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
  
-   [Düzen](../../../../docs/framework/wpf/advanced/layout.md)  
  
 Uygulamaları oluşturma hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Uygulama Geliştirme](../../../../docs/framework/wpf/app-development/index.md)  
  
-   [Denetimler](../../../../docs/framework/wpf/controls/index.md)  
  
-   [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
  
-   [Grafikler ve Multimedya](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
  
-   [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Panellere Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Veri Şablonu Oluşturmaya Genel Bakış](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [WPF Uygulaması Derleme](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [Stiller ve Şablonlar](../../../../docs/framework/wpf/controls/styles-and-templates.md)
