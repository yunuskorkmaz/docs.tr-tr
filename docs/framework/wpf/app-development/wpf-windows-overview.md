---
title: "WPF Windows'a Genel Bakış"
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
- XAML [WPF], displaying content via
- XAML pages [WPF], displaying
- content [WPF], displaying via XAML
- window objects [WPF]
- hosting [WPF], applications
- managing windows [WPF]
- dialog boxes [WPF]
- Page object [WPF]
- NavigationWindow objects [WPF]
- applications [WPF], hosting
- content [WPF], displaying
- events [WPF]
- content [WPF], displaying via procedural code
- modal windows [WPF]
- procedural code [WPF], displaying content via
- displaying content via procedural code [WPF]
- window management [WPF]
- displaying content [WPF]
- window events [WPF]
- windows [WPF]
- modal dialog boxes [WPF]
- displaying XAML pages [WPF]
ms.assetid: 737d04ec-8861-46c3-8d44-fa11d3528d23
caps.latest.revision: "65"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f9822c61f454f0dd166cfdad7f26798790a5f23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-windows-overview"></a>WPF Windows'a Genel Bakış
Kullanıcıların etkileşimde [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] tek başına uygulamalar windows aracılığıyla. Veri visualizes ve kullanıcıların veri ile etkileşim kurmasına olanak sağlayan içeriği barındırmak için bir pencere birincil amacı budur. Tek başına [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamaları kullanarak kendi windows sağlamak <xref:System.Windows.Window> sınıfı. Bu konu tanıtır <xref:System.Windows.Window> oluşturma ve tek başına uygulamaları Windows'ta yönetme temellerini kapsayan önce.  
  
> [!NOTE]
>  Tarayıcıda barındırılan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] gibi uygulamaları [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] ve gevşek [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sayfaları, kendi windows sağlayan yok. Windows tarafından sağlanan bunun yerine, barındırılan [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]. Bkz: [WPF XAML tarayıcısı uygulamaları genel bakış](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).  
  
  
<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a>Pencere sınıfı  
 Aşağıdaki şekilde pencerenin bağlı parçaları gösterilmektedir.  
  
 ![Pencere öğeleri](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure1.PNG "WindowOverviewFigure1")  
  
 Bir pencere iki alana ayrılır: istemci alanını ve istemci dışı alan.  
  
 *İstemci dışı alan* bir pencerenin tarafından uygulanan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ve aşağıdakiler de dahil olmak üzere çoğu windows için ortak olan pencere bölümleri içerir:  
  
-   Bir sınır.  
  
-   Başlık çubuğu.  
  
-   Bir simge.  
  
-   Simge Durumuna Küçült, Ekranı Kapla ve düğmeleri geri yükleyin.  
  
-   Kapat düğmesi.  
  
-   En aza indirmek kullanıcıların menü öğelerini içeren bir sistem menüsü en üst düzeye çıkarmak, geri yükleme, taşımak, yeniden boyutlandırma ve bir penceresini kapatın.  
  
 *İstemci alanını* bir pencerenin pencerenin istemci dışı alan içinde bir alandır ve geliştiriciler tarafından menü çubukları, araç çubukları ve denetimleri gibi uygulamaya özgü içerik eklemek için kullanılır.  
  
 İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], bir pencere yalıtılan <xref:System.Windows.Window> aşağıdakileri yapmak için kullandığınız sınıfı:  
  
-   Bir pencere görüntüler.  
  
-   Boyut, konum ve görünüm penceresinin yapılandırın.  
  
-   Uygulamaya özgü içerik ana bilgisayar.  
  
-   Bir pencere ömrü yönetin.  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a>Bir pencere uygulama  
 Görünüm ve davranış, tipik bir pencere uyarlamasını oluşur nerede *Görünüm* bir pencere kullanıcılara nasıl göründüğünü tanımlar ve *davranışı* bir pencere işlevleri kullanıcıların etkileşimli olarak biçimini tanımlar kendisiyle. İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], görünüm uygulayabilirsiniz ve penceresini kullanarak davranışı ya da kod veya [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme.  
  
 Genel olarak, ancak bir penceresinin görünümünü kullanarak uygulanan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme ve davranışını arka plan kodu, kullanılarak gerçekleştirilir aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 Etkinleştirmek için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme dosya ve arka plan kodu dosyanın birlikte çalışabilmesi için aşağıdakiler gereklidir:  
  
-   Biçimlendirme içinde `Window` öğesi içermelidir `x:Class` özniteliği. Ne zaman uygulaması oluşturulur, varlığını `x:Class` biçimlendirmede dosya neden olan [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] oluşturmak için bir `partial` öğesinden türetilen sınıf <xref:System.Windows.Window> ve tarafından belirtilen ada sahip `x:Class` özniteliği. Bu eklenmesini gerektirir bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] için ad alanı bildiriminin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] şeması ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). Oluşturulan `partial` uygulayan sınıf `InitializeComponent` olaylarını kaydetmek ve biçimlendirme içinde uygulanan özelliklerini ayarlamak için çağrılan yöntemi.  
  
-   Kod arkasında, sınıf olmalıdır bir `partial` sınıfı tarafından belirtilen aynı ada sahip `x:Class` biçimlendirme ve bu içinde öznitelik öğesinden türetilmelidir <xref:System.Windows.Window>. Bu arka plan kodu ile ilişkili dosyaya verir `partial` uygulama yapılandırıldığında biçimlendirme dosyası için oluşturulan sınıf (bkz [WPF uygulaması oluşturma](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)).  
  
-   Kod arka plan, <xref:System.Windows.Window> sınıfı, çağıran bir oluşturucu uygulanmalı `InitializeComponent` yöntemi. `InitializeComponent`uygulanan dosya biçimlendirme tarafından oluşturulan `partial` olaylarını kaydetmek ve biçimlendirme içinde tanımlanan özelliklerini ayarlamak için sınıf.  
  
> [!NOTE]
>  Yeni bir eklediğinizde <xref:System.Windows.Window> kullanarak projenize [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], <xref:System.Windows.Window> biçimlendirme ve arka plan kodu kullanılarak uygulanır ve işaretleme ve arka plan kod dosyaları arasındaki ilişki oluşturmak için gerekli yapılandırmayı içerir burada açıklanmıştır.  
  
 Yerinde bu yapılandırma ile penceresinde görünümünü tanımlayan odaklanabilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme ve kod arkasında davranışını uygulama. Aşağıdaki örnek, uygulanan bir düğme penceresiyle gösterir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme ve düğmenin için bir olay işleyicisi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> kod arkasında uygulanan olay.  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a>Pencere tanım MSBuild için yapılandırma  
 Pencerenizi nasıl uygulayacağınıza nasıl için yapılandırıldığını belirler [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]. Her ikisi de kullanılarak tanımlanan bir pencere için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme ve arka plan kodu:  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]Biçimlendirme dosyaları olarak yapılandırılmış [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` öğeleri.  
  
-   Arka plan kod dosyaları olarak yapılandırılmış [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Compile` öğeleri.  
  
 Bu aşağıda gösterildiği [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] proje dosyası.  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 Oluşturma hakkında bilgi için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar, bkz [WPF uygulaması oluşturma](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a>Pencere Ömrü  
 Herhangi bir sınıf ile bir pencere ilk örneği oluşturulduğunda, başlayan bir ömrü olduğu gibi daha sonra açılan, etkinleştirilir ve devre dışı ve sonunda kapalı.  
  
  
<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a>Bir penceresini açma  
 Bir pencerede açmak için önce aşağıdaki örnekte gösterilen örneği, oluşturun.  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 Bu örnekte, `MarkupAndCodeBehindWindow` uygulama başladığında oluştuğu örneği olduğunda <xref:System.Windows.Application.Startup> olayı oluşturulur.  
  
 Bir pencere örneği oluşturulduğunda bir başvuru tarafından yönetilen windows listesine otomatik olarak eklenir <xref:System.Windows.Application> nesne (bkz: <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>). Ayrıca, örneğinin oluşturulması için ilk penceresinde varsayılan olarak ayarlanır <xref:System.Windows.Application> ana uygulama penceresi olarak (bkz: <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).  
  
 Pencere, son olarak çağırarak açılırsa <xref:System.Windows.Window.Show%2A> yöntemi; sonucu aşağıdaki çizimde gösterilmiştir.  
  
 ![Bir pencere açılır Window.Show çağrısıyla](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure8.png "WindowOverviewFigure8")  
  
 Çağırarak açılan bir pencere <xref:System.Windows.Window.Show%2A> uygulama kullanıcıların diğer windows aynı uygulama etkinleştirmesine izin veren bir modda çalışır anlamı kalıcı olmayan bir penceredir.  
  
> [!NOTE]
>  <xref:System.Windows.Window.ShowDialog%2A>iletişim kutuları gibi Windows kalıcı olarak açmak için çağrılır. Bkz: [iletişim kutularına genel bakış](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md) daha fazla bilgi için.  
  
 Zaman <xref:System.Windows.Window.Show%2A> olan kullanıcı girişi almasına olanak veren altyapı kurmak için gösterilmeden önce adlı bir pencere başlatma çalışma gerçekleştirir. Pencerenin başlatıldığında <xref:System.Windows.Window.SourceInitialized> olayı oluşturulur ve penceresi gösterilir.  
  
 Bir kısayol olarak <xref:System.Windows.Application.StartupUri%2A> bir uygulama başlatıldığında otomatik olarak açılan ilk penceresi belirtmek için ayarlanabilir.  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 Uygulama başladığında değeri tarafından belirtilen pencere <xref:System.Windows.Application.StartupUri%2A> açıldığında modelessly; dahili olarak, pencere çağırarak açılırsa, <xref:System.Windows.Window.Show%2A> yöntemi.  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a>Pencere sahipliği  
 Kullanılarak açılır bir pencere <xref:System.Windows.Window.Show%2A> yöntemi oluşturulduğu penceresi ile örtük bir ilişki yok; kullanıcılar da penceresi aşağıdaki işlemleri yapabilirsiniz anlamına gelir ya da penceresiyle birbirinden, etkileşimli olarak çalışabilir:  
  
-   Diğer kapak (bir windows sürümü olmadığı sürece, <xref:System.Windows.Window.Topmost%2A> özelliğini `true`).  
  
-   , Diğer etkilemeden ekranı kaplamış ve geri yüklenen en aza.  
  
 Bazı windows bunları açılır penceresi ile bir ilişkisi gerektirir. Örneğin, bir [!INCLUDE[TLA#tla_ide](../../../../includes/tlasharptla-ide-md.md)] özelliği windows ve aracı windows, tipik davranıştır kendilerini oluşturan penceresi kapsayacak şekilde uygulamasını açın. Ayrıca, gibi windows her zaman kapatın, en aza indirmek, en üst düzeye çıkarmak ve onları oluşturan penceresi birlikte geri. Bir pencere yaparak bu tür bir ilişki kurulamıyor *kendi* başka bir ve ayarlayarak elde <xref:System.Windows.Window.Owner%2A> özelliği *penceresi ait* başvuru *sahibi Pencere*. Bu, aşağıdaki örnekte gösterilir.  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 Sahipliği kurulduktan sonra:  
  
-   Değerini inceleyerek, sahibi penceresini ait penceresi başvurusu yapabilir, <xref:System.Windows.Window.Owner%2A> özelliği.  
  
-   Sahip pencereyi sahibi değerini inceleyerek tüm windows bulabilir, <xref:System.Windows.Window.OwnedWindows%2A> özelliği.  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a>Pencere etkinleştirme önleme  
 Burada windows Internet messenger stili uygulamanın konuşma windows ya da bir e-posta uygulamasının bildirim windows gibi gösterilen etkinleştirilmesi gereken olmayan senaryolar vardır.  
  
 Uygulamanızı gösterilen etkinleştirilmesi döndürmemelidir bir pencere varsa, ayarlayabileceğiniz kendi <xref:System.Windows.Window.ShowActivated%2A> özelliğine `false` çağırmadan önce <xref:System.Windows.Window.Show%2A> ilk kez yöntemi. Sonuç olarak:  
  
-   Pencerenin etkinleştirilmedi.  
  
-   Pencerenin <xref:System.Windows.Window.Activated> olayı oluşmaz.  
  
-   Etkin pencereyi etkin olarak kalır.  
  
 Kullanıcı istemci veya istemci dışı alan tıklatarak etkinleştirir hemen penceresi, ancak etkin hale. Bu durumda:  
  
-   Pencerenin etkinleştirilir.  
  
-   Pencerenin <xref:System.Windows.Window.Activated> olayı oluşturulur.  
  
-   Daha önce etkinleştirilmiş penceresi devre dışı bırakılır.  
  
-   Pencerenin <xref:System.Windows.Window.Deactivated> ve <xref:System.Windows.Window.Activated> olayları daha sonra kullanıcı eylemlerine beklendiği gibi oluşur.  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a>Pencere etkinleştirme  
 Bir penceresi ilk açıldığında etkin pencereyi olur (ile gösterilen sürece <xref:System.Windows.Window.ShowActivated%2A> kümesine `false`). *Etkin pencereyi* şu anda tuş vuruşlarını ve fare tıklamaları gibi kullanıcı girişi yakalama penceredir. Bir pencere etkin olduğunda başlatır <xref:System.Windows.Window.Activated> olay.  
  
> [!NOTE]
>  Bir penceresi ilk açıldığında <xref:System.Windows.FrameworkElement.Loaded> ve <xref:System.Windows.Window.ContentRendered> olayları ortaya çıkar yalnızca sonra <xref:System.Windows.Window.Activated> olayı oluşturulur. Bu durum dikkate alınarak, bir pencere etkili bir şekilde açıldığında kabul edilebilir <xref:System.Windows.Window.ContentRendered> tetiklenir.  
  
 Bir pencere etkin hale geldikten sonra bir kullanıcı aynı uygulamada başka bir pencere etkinleştirebilir veya başka bir uygulama etkinleştirin. Bu durum oluştuğunda şu anda etkin pencereyi devre dışı olur ve başlatır <xref:System.Windows.Window.Deactivated> olay. Kullanıcı şu anda devre dışı bırakılan penceresinde seçtiğinde, benzer şekilde, pencerenin yeniden etkin hale gelir ve <xref:System.Windows.Window.Activated> tetiklenir.  
  
 İşlemek için ortak bir nedeni <xref:System.Windows.Window.Activated> ve <xref:System.Windows.Window.Deactivated> etkinleştirmek ve bir pencere etkin olduğunda, yalnızca çalıştırabilirsiniz işlevselliği devre dışı bırakın. Örneğin, bazı windows sabit kullanıcı girişi veya oyunlar ve video oynatıcı dahil olmak üzere dikkat gerektiren etkileşimli içerik görüntülenir. Aşağıdaki örnekte nasıl yapılacağını gösteren bir Basitleştirilmiş video oynatıcı olan <xref:System.Windows.Window.Activated> ve <xref:System.Windows.Window.Deactivated> bu davranışı uygulamak için.  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 Bir pencere devre dışı bırakıldığında uygulamalarının diğer türleri kod hala arka planda çalıştırabilir. Örneğin, bir posta istemcisi posta sunucusu kullanıcı diğer uygulamaları kullanırken yoklama devam edebilir. Ana penceresinde devre dışı durumdayken bu gibi uygulamalar genellikle farklı veya ek davranış sağlar. Posta programı göre bu hem gelen kutusuna yeni posta öğe ekleme ve sistem tepsisi bildirimi simgesini ekleme olduğu anlamına gelebilir. Posta penceresi incelenerek belirlenir etkin değilken, bir bildirim simgesi yalnızca görüntülenmesi <xref:System.Windows.Window.IsActive%2A> özelliği.  
  
 Bir arka plan görevi tamamlarsa, bir pencere çağırarak kullanıcıya daha urgently bildirmek isteyebilirsiniz <xref:System.Windows.Window.Activate%2A> yöntemi. Kullanıcı ile etkileşim, başka bir uygulama zaman etkin <xref:System.Windows.Window.Activate%2A> , pencerenin görev çubuğu düğmesi yanıp sönen denir. Bir kullanıcı geçerli bir uygulama ile etkileşim çağrılmadan <xref:System.Windows.Window.Activate%2A> penceresi ön plana getirecek.  
  
> [!NOTE]
>  Uygulama kapsamı etkinleştirme kullanarak işleyebilir <xref:System.Windows.Application.Activated?displayProperty=nameWithType> ve <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> olaylar.  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a>Bir pencereyi kapatma  
 Bir pencere için bir son kullanıcı kapandığında gelen başlar. Aşağıdakiler de dahil olmak üzere istemci olmayan alanında öğeleri kullanarak bir pencere kapatılabilir:  
  
-   **Kapat** öğesinin **sistem** menüsü.  
  
-   ALT + F4 tuşuna basın.  
  
-   Tuşuna basarak **Kapat** düğmesi.  
  
 Bir pencereyi kapatmak için istemci alanını ek mekanizmalarına hangisinin daha fazla ortak şunlar sağlayabilirsiniz:  
  
-   Bir **çıkış** öğesi **dosya** menüsünde, genellikle ana uygulama windows için.  
  
-   A **Kapat** öğesi **dosya** menüsünde, genellikle ikincil uygulama penceresi.  
  
-   A **iptal** düğmesi, genellikle bir modal iletişim kutusu.  
  
-   A **Kapat** düğmesi, genellikle bir kalıcı olmayan iletişim kutusu.  
  
 Bu özel düzeneklerden birini yanıtta bir pencereyi kapatmak için çağırması gerekir <xref:System.Windows.Window.Close%2A> yöntemi. Aşağıdaki örnek seçerek bir pencereyi kapatmak olanağı uygulayan **çıkış** üzerinde **dosya** menüsü.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 Bir pencere kapatıldığında, iki olaylar oluşur: <xref:System.Windows.Window.Closing> ve <xref:System.Windows.Window.Closed>.  
  
 <xref:System.Windows.Window.Closing>penceresi kapanır ve hangi pencere tarafından kapatma engellenebilir bir mekanizma sağlar önce oluşturulur. Pencereyi kapatma önlemek için bir ortak pencere içeriğinin değiştirilen veri içerip içermediğini nedeni. Bu durumda, <xref:System.Windows.Window.Closing> veri kirli olup olmadığını ve bu durumda, kullanıcı ya da verileri kaydetmeden pencereyi devam mı, yoksa penceresini kapatma işlemini iptal için sormak için belirlemek için olay işlenebilir. Aşağıdaki örnek, işleme önemli yönlerini gösterir <xref:System.Windows.Window.Closing>.  
  
 [!code-csharp[WindowClosingSnippets](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  
 
  
 <xref:System.Windows.Window.Closing> Olay işleyicisine geçirilir bir <xref:System.ComponentModel.CancelEventArgs>, hangi uygulayan `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> ayarlamak için özellik `true` bir pencere kapatılmasını önlemek için.  
  
 Varsa <xref:System.Windows.Window.Closing> işlenen değil veya ele ancak iptal, pencere kapanacaktır. Yalnızca bir pencere gerçekte kapanmadan önce <xref:System.Windows.Window.Closed> tetiklenir. Bu noktada, bir pencere kapatılmasını önlenemeyen.  
  
> [!NOTE]
>  Bir uygulamayı otomatik olarak ana uygulama penceresi kapattığı zaman kapatmaya yapılandırılabilir (bkz: <xref:System.Windows.Application.MainWindow%2A>) ya da son penceresi kapanır. Ayrıntılar için bkz <xref:System.Windows.Application.ShutdownMode%2A>.  
  
 Bir pencere istemci ve istemci alanlarında sağlanan bir yolla açıkça kapatılabilir, ancak bir pencere da örtük olarak davranışını uygulamanın diğer bölümlerinde sonucunda kapatılabilir veya [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], aşağıdakiler dahil:  
  
-   Bir kullanıcı oturumu kapattığında ya da kapatıldığında [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)].  
  
-   Pencerenin sahibi kapatır (bkz: <xref:System.Windows.Window.Owner%2A>).  
  
-   Ana uygulama penceresi kapatıldığında ve <xref:System.Windows.Application.ShutdownMode%2A> olan <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
-   <xref:System.Windows.Application.Shutdown%2A>adı verilir.  
  
> [!NOTE]
>  Kapatılan bir pencere açılamaz.  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a>Pencere ömür olayları  
 Aşağıdaki çizimde bir pencere yaşam süresi asıl olaylar dizisini gösterir.  
  
 ![Pencere Ömrü](../../../../docs/framework/wpf/app-development/media/windowlifetimeevents.png "WindowLifetimeEvents")  
  
 Aşağıdaki çizimde asıl olayların sırası etkinleştirmesi olmadan gösterilen bir pencere ömrü gösterir (<xref:System.Windows.Window.ShowActivated%2A> ayarlanır `false` pencere gösterilmeden önce).  
  
 ![Pencere Ömrü &#40; Window.ShowActivated &#61; False &#41; ] (../../../../docs/framework/wpf/app-development/media/windowlifetimenoact.png "WindowLifetimeNoAct")  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a>Pencere konumu  
 Bir penceresi açıkken x ve y konumda sahip boyutlarına Masaüstü göre. Bu konum incelenerek belirlenebilir <xref:System.Windows.Window.Left%2A> ve <xref:System.Windows.Window.Top%2A> özellikleri, sırasıyla. Pencere konumunu değiştirmek için bu özellikleri ayarlayabilirsiniz.  
  
 İlk konumunu belirtmek bir <xref:System.Windows.Window> zaman ilk göründüğü ayarlayarak <xref:System.Windows.Window.WindowStartupLocation%2A> aşağıdakilerden birini özelliğiyle <xref:System.Windows.WindowStartupLocation> numaralandırma değerlerinin:  
  
-   <xref:System.Windows.WindowStartupLocation.CenterOwner>(varsayılan)  
  
-   <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
-   <xref:System.Windows.WindowStartupLocation.Manual>  
  
 Başlangıç konumu olarak belirtilmişse, <xref:System.Windows.WindowStartupLocation.Manual>ve <xref:System.Windows.Window.Left%2A> ve <xref:System.Windows.Window.Top%2A> özellikleri değil ayarlanmış, <xref:System.Windows.Window> ister [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] görünmesi bir konum.  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a>En üstteki Windows ve Z düzeni  
 Bir x ve y konumunu, bir pencere de sahip olmanın yanı sıra diğer windows göre dikey konumunu belirler z boyutundaki bir konum vardır. Bu pencere z düzeni bilinir ve iki tür vardır: normal z düzenini ve en üstteki z düzeni. Bir pencerede konumunu *normal z düzenini* , şu anda etkin olup olmamasına göre belirlenir. Varsayılan olarak, bir pencereyi normal z-sırası içinde bulunur. Bir pencerede konumunu *en üstteki z düzenini* Ayrıca, şu anda etkin olup olmamasına göre belirlenir. Ayrıca, en üstteki z düzenini Windows'da her zaman normal z düzenini Windows'da yukarıda yer alır. Bir pencere ayarlayarak en üstteki z-sırası içinde bulunan kendi <xref:System.Windows.Window.Topmost%2A> özelliğine `true`.  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup2)]  
  
 Her z düzenini içinde şu anda etkin pencereyi yukarıdaki tüm diğer windows aynı z sırada görünür.  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a>Pencere boyutu  
 Masaüstü konumu sahip olmanın yanı sıra bir pencere çeşitli genişlik ve yükseklik özellikleri dahil olmak üzere çeşitli özellikler tarafından belirlenen bir boyutu vardır ve <xref:System.Windows.Window.SizeToContent%2A>.  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, ve <xref:System.Windows.FrameworkElement.MaxWidth%2A> bir pencere yaşam süresi boyunca olabilir ve aşağıdaki örnekte gösterildiği gibi yapılandırıldığını genişlikleri aralığını yönetmek için kullanılır.  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup2)]  
  
 Pencere yüksekliği yönetilir <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, ve <xref:System.Windows.FrameworkElement.MaxHeight%2A>, aşağıdaki örnekte gösterildiği gibi yapılandırılır.  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup2)]  
  
 Çeşitli genişlik ve yükseklik değerleri her bir aralığı belirtmek için genişlik ve yükseklik ilgili boyutu için belirtilen aralık içinde herhangi bir yerde olması için yeniden boyutlandırılabilir penceresinin mümkündür. Geçerli genişlik ve yükseklik algılamak için incelemek <xref:System.Windows.FrameworkElement.ActualWidth%2A> ve <xref:System.Windows.FrameworkElement.ActualHeight%2A>sırasıyla.  
  
 Pencerenizin yüksekliğini ve genişliğini istiyorsanız pencere boyutu için uygun bir boyut için içerik, kullanabileceğiniz <xref:System.Windows.Window.SizeToContent%2A> şu değerleri özelliği:  
  
-   <xref:System.Windows.SizeToContent.Manual>. Hiçbir etkisi (varsayılan).  
  
-   <xref:System.Windows.SizeToContent.Width>. Her ikisi de ayarını aynı etkiye sahip içerik genişliği Sığdır <xref:System.Windows.FrameworkElement.MinWidth%2A> ve <xref:System.Windows.FrameworkElement.MaxWidth%2A> içerik genişliğine.  
  
-   <xref:System.Windows.SizeToContent.Height>. Her ikisi de ayarını aynı etkiye sahip içerik yüksekliğini Sığdır <xref:System.Windows.FrameworkElement.MinHeight%2A> ve <xref:System.Windows.FrameworkElement.MaxHeight%2A> içerik yüksekliğine.  
  
-   <xref:System.Windows.SizeToContent.WidthAndHeight>. İçerik genişlik ve her ikisi de ayarı ile aynı etkiye sahiptir yükseklik Sığdır <xref:System.Windows.FrameworkElement.MinHeight%2A> ve <xref:System.Windows.FrameworkElement.MaxHeight%2A> içeriği hem de ayarı yüksekliğine <xref:System.Windows.FrameworkElement.MinWidth%2A> ve <xref:System.Windows.FrameworkElement.MaxWidth%2A> içerik genişliğine.  
  
 Aşağıdaki örnek bir pencere boyutları, içeriğinin dikey ve yatay olarak, ilk olarak gösterilen zaman sığması için otomatik olarak gösterir.  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup2)]  
  
 Aşağıdaki örnekte nasıl ayarlanacağını gösterir <xref:System.Windows.Window.SizeToContent%2A> özelliği bir pencere içeriğine uyacak şekilde nasıl boyutlandırılacağını belirtmek için kod.
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a>Özellikler boyutlandırma için öncelik sırası  
 Esas olarak, genişlik ve yükseklik yeniden boyutlandırılabilir penceresi için aralığını tanımlamak için bir pencere çeşitli boyutlarda özelliklerini birleştirin. Geçerli bir aralık korunduğu emin olmak için <xref:System.Windows.Window> önceliği aşağıdaki siparişler kullanarak boyutu özelliklerinin değerlerini değerlendirir.  
  
 **Yükseklik özellikleri için:**  
  
1.  <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType> >  
  
2.  <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType> >  
  
3.  <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType> >  
  
4.  <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 **Genişlik özellikleri için:**  
  
1.  <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType> >  
  
2.  <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType> >  
  
3.  <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType> >  
  
4.  <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 Bu, ile yönetilen ekranı olduğunda öncelik sırasını ayrıca bir pencere boyutunu belirleyebilirsiniz <xref:System.Windows.Window.WindowState%2A> özelliği.  
  
<a name="WindowState"></a>   
## <a name="window-state"></a>Pencere durum  
 Yeniden boyutlandırılabilir pencere ömrü boyunca üç durumdan sahip olabilir: normal, simge durumuna küçültülmüş ve ekranı. Bir pencere bir *normal* durumunda bir pencere varsayılan durumu. Bu durum penceresiyle taşıyın ve yeniden boyutlandırılabilir ise bir yeniden boyutlandırma tutamacı veya kenarlık kullanarak yeniden boyutlandırmak sağlar.  
  
 Bir pencere bir *simge durumuna küçültülmüş* durumu varsa, görev çubuğu düğmesi daraltır <xref:System.Windows.Window.ShowInTaskbar%2A> ayarlanır `true`; Aksi takdirde olabilir ve kendisini Masaüstü sol alt köşesindeki yeniden yerleştirir en küçük olası boyutuna daraltır. Ne simge durumuna küçültülmüş pencere türü kenarlık kullanarak yeniden boyutlandırılabilir veya görev çubuğunda gösterilmeyen bir simge durumuna küçültülmüş pencere Masaüstü sürüklenebilir rağmen tutamacı, yeniden boyutlandırma.  
  
 Bir pencere bir *ekranı* durumu genişletir olacağı yalnızca büyüklüğünde maksimum boyutu olabilir, kendi <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, ve <xref:System.Windows.Window.SizeToContent%2A> özellikleri dikte. Bir simge durumuna küçültülmüş pencere gibi bir yeniden boyutlandırma tutamacı kullanarak veya kenarlık sürükleyerek kaplamış boyutlandırılamaz.  
  
> [!NOTE]
>  Değerlerini <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, ve <xref:System.Windows.FrameworkElement.Height%2A> penceresinin özelliklerini bile pencere şu anda ekranı kaplamış olarak simge durumuna küçültülmüş veya normal durum için değerler her zaman temsil.  
  
 Bir pencere durumunu ayarlanarak yapılandırılabilir kendi <xref:System.Windows.Window.WindowState%2A> şunlardan biri olabilir özelliği <xref:System.Windows.WindowState> numaralandırma değerlerinin:  
  
-   <xref:System.Windows.WindowState.Normal>(varsayılan)  
  
-   <xref:System.Windows.WindowState.Maximized>  
  
-   <xref:System.Windows.WindowState.Minimized>  
  
 Aşağıdaki örnek açıldığında tam ekran olarak gösterilen bir pencere oluşturulacağını gösterir.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup2)]  
  
 Genel olarak, ayarlamalısınız <xref:System.Windows.Window.WindowState%2A> bir pencere ilk durumunu yapılandırmak için. Yeniden boyutlandırılabilir penceresinde gösterilen sonra kullanıcılar simge durumuna küçült tuşuna basın, en üst düzeye çıkarmak ve pencere durumunu değiştirmek için pencerenin başlık çubuğunda düğmelerini geri yükleme.  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a>Pencere görünümü  
 Pencere özgü içerik, düğmeleri, etiketler ve metin kutuları gibi ekleyerek istemci alanını penceresinin görünümünü değiştirin. İstemci dışı alan yapılandırmak için <xref:System.Windows.Window> dahil çeşitli özellikler sağlayan <xref:System.Windows.Window.Icon%2A> pencerenin simgesini ve <xref:System.Windows.Window.Title%2A> başlığını ayarlamak için.  
  
 Pencerenin yeniden boyutlandırma modunu, pencere stili yapılandırarak istemci dışı alan kenarlık davranış ve görünümünü de değiştirebilirsiniz ve masaüstü görev çubuğunda bir düğme olarak göründüğü.  
  
  
<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a>Mod yeniden boyutlandırma  
 Bağlı olarak <xref:System.Windows.Window.WindowStyle%2A> özelliği, denetleyebilir nasıl (ve eğer) kullanıcılar pencere yeniden boyutlandırın. Kullanıcı pencereyi kenarlığını fareyle olup sürükleyerek yeniden boyutlandırabilirsiniz olup olmadığını pencere stili seçimi etkiler **simge durumuna küçült**, **Ekranı Kapla**, ve **yeniden boyutlandırma** düğmeleri İstemci dışı alan üzerinde görünür ve göründükleri ise, bunlar etkinleştirilip etkinleştirilmediği.  
  
 Nasıl bir ayarlayarak yeniden boyutlandırır yapılandırabilirsiniz, <xref:System.Windows.Window.ResizeMode%2A> şunlardan biri olabilir özelliği <xref:System.Windows.ResizeMode> numaralandırma değerlerinin:  
  
-   <xref:System.Windows.ResizeMode.NoResize>  
  
-   <xref:System.Windows.ResizeMode.CanMinimize>  
  
-   <xref:System.Windows.ResizeMode.CanResize>(varsayılan)  
  
-   <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 İle <xref:System.Windows.Window.WindowStyle%2A>, büyük olasılıkla ondan ayarlamanız anlamına gelir, yaşam süresi sırasında değiştirmek bir pencere yeniden boyutlandırma modunu düşüktür [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme.  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup2)]  
  
 Bir pencere ekranı olup olmadığını algılayan Not küçültülebilir ya da inceleyerek geri <xref:System.Windows.Window.WindowState%2A> özelliği.  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a>Pencere stili  
 Bir pencere istemci olmayan alanından gösterilen kenarlık çoğu uygulamalar için uygundur. Ancak, farklı kenarlık türü gerekli veya kenarlık yok penceresi türüne bağlı olarak, gerekli olan durumların vardır.  
  
 Bir pencere kenarlığını ne tür denetlemek için alır, ayarladığınız kendi <xref:System.Windows.Window.WindowStyle%2A> özelliği şu değerlerden biri ile <xref:System.Windows.WindowStyle> numaralandırma:  
  
-   <xref:System.Windows.WindowStyle.None>  
  
-   <xref:System.Windows.WindowStyle.SingleBorderWindow>(varsayılan)  
  
-   <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
-   <xref:System.Windows.WindowStyle.ToolWindow>  
  
 Bu pencere stilleri etkisini aşağıdaki çizimde gösterilmiştir.  
  
 ![Pencere stilleri](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure6.PNG "WindowOverviewFigure6")  
  
 Ayarlayabileceğiniz <xref:System.Windows.Window.WindowStyle%2A> kullanarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işaretleme veya kod; bir pencere ömrü boyunca değiştirmek olası olduğundan, büyük olasılıkla kullanarak yapılandıracağınız [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup2)]  
  
#### <a name="non-rectangular-window-style"></a>Dikdörtgen olmayan pencere stili  
 Ayrıca burada kenarlık stilleri, durumlar vardır <xref:System.Windows.Window.WindowStyle%2A> sağlar, sağlamak için yeterli değil. Örneğin, gibi bir dikdörtgen olmayan kenarlık sahip bir uygulama oluşturmak isteyebilirsiniz [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] kullanır.  
  
 Örneğin, aşağıdaki çizimde gösterilen konuşma Kabarcık penceresi göz önünde bulundurun.  
  
 ![Dikdörtgen olmayan pencere](../../../../docs/framework/wpf/app-development/media/nonrectangularwindowfigure.PNG "NonRectangularWindowFigure")  
  
 Bu pencere türü ayarlayarak oluşturulabilir <xref:System.Windows.Window.WindowStyle%2A> özelliğine <xref:System.Windows.WindowStyle.None>ve özel kullanarak destekleyen <xref:System.Windows.Window> saydamlığını sahiptir.  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup2)]  
  
 Bu değerlerin birleşimini tamamen saydam işlemek için penceresini bildirir. Bu durumda pencerenin istemci dışı alan adornments (Kapat menüsü, simge durumuna küçült, Ekranı Kapla ve geri yükleme düğmeleri ve benzeri) kullanılamaz. Sonuç olarak, sağlamanız kendi gerekir.  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a>Görev çubuğu durum  
 Görev çubuğu düğmesi, aşağıdaki şekilde gösterilene benzer bir pencere varsayılan görünümünü içerir.  
  
 ![Görev çubuğu düğmesi penceresiyle](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure7.PNG "WindowOverviewFigure7")  
  
 Görev çubuğu düğmesi, ileti kutuları ve iletişim kutuları gibi bazı windows türleri yok (bkz [iletişim kutularına genel bakış](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)). Bir pencere için görev çubuğu düğmesini ayarlayarak gösterilip gösterilmeyeceğini denetleyebilirsiniz <xref:System.Windows.Window.ShowInTaskbar%2A> özelliği (`true` varsayılan olarak).  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup2)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
 <xref:System.Windows.Window>gerektirir `UnmanagedCode` örneğinin oluşturulması için güvenlik izni. Yüklü ve yerel makineden başlatılan uygulamalar için bu uygulama için verilen izinleri kümesinde döner.  
  
 Ancak, bu Internet veya yerel intranet bölgesine kullanmaktan başlatılan uygulamalara izinler kümesi dışında kalan [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)]. Sonuç olarak, kullanıcılar alacak bir [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] güvenlik uyarısı ve uygulama için tam güven izni yükseltmesine gerekir.  
  
 Ayrıca, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] windows ya da iletişim kutuları varsayılan olarak gösterilemiyor. Tek başına uygulama güvenlik konuları üzerinde bir tartışma için bkz: [WPF güvenlik stratejisi - Platform güvenliği](../../../../docs/framework/wpf/wpf-security-strategy-platform-security.md).  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a>Windows diğer türleri  
 <xref:System.Windows.Navigation.NavigationWindow>gezinebilir içeriği barındırmak için tasarlanmış bir penceredir. Daha fazla bilgi için bkz: [Gezinti genel bakış](../../../../docs/framework/wpf/app-development/navigation-overview.md)).  
  
 İletişim kutusu, genellikle bir işlevi tamamlamak için bir kullanıcıdan bilgi toplamak için kullanılan windows vardır. Örneğin, ne zaman bir kullanıcının istediği bir dosyayı açmaya **Dosya Aç** iletişim kutusu kullanıcıdan dosya adını almak için bir uygulama tarafından genellikle görüntülenir. Daha fazla bilgi için bkz: [iletişim kutularına genel bakış](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Window>  
 <xref:System.Windows.MessageBox>  
 <xref:System.Windows.Navigation.NavigationWindow>  
 <xref:System.Windows.Application>  
 [İletişim Kutularına Genel Bakış](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)  
 [WPF Uygulaması Derleme](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
