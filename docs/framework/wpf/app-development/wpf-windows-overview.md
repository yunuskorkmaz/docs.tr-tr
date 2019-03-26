---
title: WPF Windows'a Genel Bakış
ms.date: 03/30/2017
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
ms.openlocfilehash: ab9b36857e2508190a212844f3c6b53d777c0552
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58466224"
---
# <a name="wpf-windows-overview"></a>WPF Windows'a Genel Bakış
Kullanıcılar, Windows Presentation Foundation (WPF) tek başına uygulamalar windows aracılığıyla etkileşim. Birincil amacı bir pencere, verileri görselleştiren ve verilerle etkileşimde bulunmak kullanıcıların sağlayan konak içerik sağlamaktır. Tek başına [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamaları kullanarak kendi windows sağlamak <xref:System.Windows.Window> sınıfı. Bu konu tanıtır <xref:System.Windows.Window> oluşturma ve yönetme windows tek başına uygulamalarda temellerini kapsayan önce.  
  
> [!NOTE]
>  Tarayıcıda barındırılan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] gibi uygulamaları [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] ve gevşek [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sayfaları, kendi windows sağlamadığınızdan. Windows tarafından sağlanan bunun yerine barındırılan [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]. Bkz: [WPF XAML tarayıcı uygulamalarına genel bakış](wpf-xaml-browser-applications-overview.md).  
  
  
<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a>Pencere sınıfı  
 Aşağıdaki şekilde, pencerenin oluşturan parçaları gösterilmektedir:  
  
 ![Pencere öğeleri gösteren ekran görüntüsü.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 Bir pencere iki alana ayrılır: istemci alanını ve istemci dışı alan.  
  
 *İstemci dışı alan* bir pencerenin tarafından uygulanan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ve aşağıdakiler dahil olmak üzere çoğu windows için ortak olan bir pencere bölümleri içerir:  
  
-   Bir sınırı.  
  
-   Başlık çubuğu.  
  
-   Bir simge.  
  
-   Simge Durumuna Küçült, Ekranı Kapla ve düğmeler geri yükleyin.  
  
-   Bir Kapat düğmesi.  
  
-   En aza indirmek, kullanıcıların menü öğeleri ile bir sistem menüsünü en üst düzeye çıkarmak, geri yükleme, taşıma, yeniden boyutlandırma ve bir penceresini kapatın.  
  
 *İstemci alanını* bir pencerenin alanın bir pencerenin istemci olmayan alanda ve geliştiriciler tarafından menü çubukları, araç çubuklarını ve denetimler gibi uygulamaya özgü içerik eklemek için kullanılır.  
  
 İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], bir pencere yalıtılan <xref:System.Windows.Window> aşağıdakileri yapmak için kullandığınız sınıfı:  
  
-   Bir pencere görüntüler.  
  
-   Boyutunu, konumunu ve görünüm penceresinin yapılandırın.  
  
-   Uygulamaya özgü içerik barındırın.  
  
-   Bir pencere ömrünü yönetmek.  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a>Pencere uygulama  
 Hem görünümünü ve davranışını, uygulama normal bir pencerenin oluşur burada *Görünüm* pencere kullanıcılara nasıl göründüğünü tanımlar ve *davranışı* pencere işlevleri kullanıcıların etkileşimli olarak biçimini tanımlar kendisiyle. İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]görünümünü uygulayabilir ve penceresini kullanarak bir davranış veya kod veya [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme.  
  
 Genel olarak, ancak pencerenin görünümünü kullanılarak uygulanan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işaretleme ve davranışını gerçekleştirilen arka plan, kod kullanarak aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 Etkinleştirmek için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işaretleme dosyasının ve birlikte çalışması için arka plan kod dosyası, aşağıdakiler gereklidir:  
  
-   Biçimlendirme içinde `Window` öğesi içermelidir `x:Class` özniteliği. Ne zaman uygulama oluşturulduğuna göre varlığını `x:Class` işaretlemede dosyası oluşturulmamasını [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] oluşturmak için bir `partial` türetilen sınıf <xref:System.Windows.Window> ve tarafından belirtilen ada sahip `x:Class` özniteliği. Bu eklenmesini gerektiren bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] için ad alanı bildirimi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] şeması ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). Oluşturulan `partial` sınıfının Implements `InitializeComponent` olaylarını kaydetmek ve işaretlemede uygulanan özellikleri ayarlamak için çağrılan yöntem.  
  
-   Arka plan, kod sınıfı olmalıdır bir `partial` sınıfı tarafından belirtilen aynı ada sahip `x:Class` biçimlendirme ve bu öznitelikte türetilmesi gereken <xref:System.Windows.Window>. Bu arka plan kod dosyası ile ilişkili olmasını sağlar `partial` uygulama oluşturulduğunda işaretleme dosyasının için oluşturulan sınıf (bkz [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md)).  
  
-   Arka plan, kod içinde <xref:System.Windows.Window> sınıfı çağıran bir oluşturucu uygulanmalı `InitializeComponent` yöntemi. `InitializeComponent` uygulanan tarafından işaretleme dosyasının üretilmiş `partial` olaylarını kaydetmek ve biçimlendirme içinde tanımlanan özelliklerini ayarlamak için sınıf.  
  
> [!NOTE]
>  Yeni bir eklediğinizde <xref:System.Windows.Window> kullanarak projenize [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], <xref:System.Windows.Window> biçimlendirme hem de arka plan kod kullanılarak uygulanır ve işaretleme ve arka plan kod dosyaları arasındaki ilişki oluşturmak için gerekli yapılandırmayı içerir burada açıklanmıştır.  
  
 Bu yapılandırmayla yerinde penceresinde görünümünü tanımlama üzerinde odaklanabilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işaretleme ve kod arkasında davranışını uygulama. Aşağıdaki örnek, uygulanan bir düğme içeren bir pencere gösterir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işaretleme ve düğme için bir olay işleyicisi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> kod arkasında uygulanan olayı.  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a>MSBuild için bir pencere tanımını yapılandırma  
 Pencereniz nasıl uygulayacağınıza nasıl için yapılandırıldığını belirler [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]. Her ikisini de kullanarak tanımlanan pencere [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işaretleme ve arka plan kod:  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Biçimlendirme dosyaları olarak yapılandırılmış [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` öğeleri.  
  
-   Arka plan kod dosyaları olarak yapılandırılmış [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Compile` öğeleri.  
  
 Aşağıda gösterilen [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] proje dosyası.  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 Yapı hakkında bilgi için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamaları, [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md).  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a>Yaşam süresi  
 Herhangi bir sınıf bir pencere ilk örneği oluşturulduğunda başlayan bir ömrü olduğu gibi sonra açıldı, etkinleştirilir ve devre dışı bırakıldı ve sonunda kapatıldı.  
  
  
<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a>Bir penceresini açma  
 Bir pencere açmak için önce aşağıdaki örnekte gösterildiği bir örneği, oluşturun.  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 Bu örnekte, `MarkupAndCodeBehindWindow` örneği uygulama başladığında gerçekleştiği zaman <xref:System.Windows.Application.Startup> olayı oluşturulur.  
  
 Bir pencere örneği oluşturulduğunda, ona bir başvuru tarafından yönetilen windows listesine otomatik olarak eklenir <xref:System.Windows.Application> nesne (bkz <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>). Ayrıca, oluşturulacak ilk penceresi varsayılan olarak ayarlanır <xref:System.Windows.Application> ana uygulama penceresini olarak (bkz <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).  
  
 Pencere, son olarak çağırarak açılırsa <xref:System.Windows.Window.Show%2A> yöntemi; sonuç aşağıdaki şekilde gösterilir.  
  
 ![Window.Show çağırarak bir pencere açılır](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 Çağırarak açılan bir pencere <xref:System.Windows.Window.Show%2A> uygulama kullanıcıların diğer windows aynı uygulama etkinleştirmesine izin veren bir modunda çalıştığı anlamına gelir bir geçici pencere.  
  
> [!NOTE]
>  <xref:System.Windows.Window.ShowDialog%2A> iletişim kutuları gibi Windows kalıcı olarak açmak için çağrılır. Bkz: [iletişim kutularına genel bakış](dialog-boxes-overview.md) daha fazla bilgi için.  
  
 Zaman <xref:System.Windows.Window.Show%2A> olan kullanıcı girişi almasına izin veren altyapı kurabilmek için gösterilmeden önce çağırılır, bir pencere başlatma işini gerçekleştirir. Pencerenin başlatıldığında <xref:System.Windows.Window.SourceInitialized> olayı oluşturulur ve penceresi gösterilir.  
  
 Bir kısayol olarak <xref:System.Windows.Application.StartupUri%2A> bir uygulama başlatıldığında otomatik olarak açılır pencere ilk belirtmek için ayarlanabilir.  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 Uygulama başlatıldığında, değeri tarafından belirtilen pencere <xref:System.Windows.Application.StartupUri%2A> açıldığında modelessly; dahili olarak, pencerenin çağırarak açıldığında, <xref:System.Windows.Window.Show%2A> yöntemi.  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a>Pencere sahipliği  
 Kullanılarak açılan bir pencere <xref:System.Windows.Window.Show%2A> yöntemi örtülü bir ilişki oluşturulduğu penceresiyle yok; kullanıcılar, yani herhangi bir pencereye aşağıdaki işlemleri yapabilirsiniz ya da penceresiyle birbirinden, etkileşim kurabilir:  
  
-   Diğer kapsar (windows birine sahip olmadığı sürece, <xref:System.Windows.Window.Topmost%2A> özelliğini `true`).  
  
-   , Diğer planı etkilemeden ekranı kaplamış ve geri yüklenen küçültülmesine.  
  
 Bazı windows bunları açılır penceresi ile bir ilişki gerektirir. Örneğin, bir [!INCLUDE[TLA#tla_ide](../../../../includes/tlasharptla-ide-md.md)] özelliği windows ve araç pencerelerini, normal davranış kendilerini oluşturan pencerenin kapsar, uygulamayı açmak. Ayrıca, gibi windows her zaman kapatın, en aza indirmek, en üst düzeye çıkarmak ve IPP penceresiyle oluşturuldukları geri yükleme. Bir pencere yaparak tür bir ilişkiye kurulabilir *kendi* başka bir ve ayarlayarak elde <xref:System.Windows.Window.Owner%2A> özelliği *penceresi ait* başvurusuyla *sahibi Pencere*. Bu, aşağıdaki örnekte gösterilir.  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 Sahipliği kurulduktan sonra:  
  
-   Sahip olunan pencerenin değerini inceleyerek, sahip penceresine başvurabilirsiniz kendi <xref:System.Windows.Window.Owner%2A> özelliği.  
  
-   Sahip penceresi sahip değerini inceleyerek windows bulabilir, <xref:System.Windows.Window.OwnedWindows%2A> özelliği.  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a>Pencere etkinleştirme önleme  
 Burada windows Internet messenger stili uygulamanın konuşma windows ya da bir e-posta uygulamasının bildirim windows gibi gösterilen etkinleştirilmesi gereken olmayan senaryolar vardır.  
  
 Uygulamanızın gösterilen etkinleştirilmesi karakteri bir pencere varsa ayarlayabileceğiniz kendi <xref:System.Windows.Window.ShowActivated%2A> özelliğini `false` çağırmadan önce <xref:System.Windows.Window.Show%2A> ilk kez yöntemi. Sonuç olarak:  
  
-   Pencerenin etkin değil.  
  
-   Pencerenin <xref:System.Windows.Window.Activated> olayı oluşmaz.  
  
-   Etkin pencere etkin olarak kalır.  
  
 Kullanıcı istemci veya istemci dışı alan tıklayarak etkinleştirir hemen sonra penceresi, ancak etkin hale. Bu durumda:  
  
-   Pencerenin etkin hale gelir.  
  
-   Pencerenin <xref:System.Windows.Window.Activated> olayı oluşturulur.  
  
-   Daha önce etkinleştirilmiş penceresi devre dışı bırakılır.  
  
-   Pencerenin <xref:System.Windows.Window.Deactivated> ve <xref:System.Windows.Window.Activated> olayları daha sonra kullanıcı eylemlerine beklendiği gibi oluşturulur.  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a>Pencere etkinleştirme  
 Bir pencere ilk kez açıldığında etkin pencere olur (ile gösterilen sürece <xref:System.Windows.Window.ShowActivated%2A> kümesine `false`). *Etkin pencere* tuş vuruşlarını ve fare tıklama gibi kullanıcı girişi şu anda yakaladığı penceredir. Bir pencere etkin olduğunda bilmemektedir <xref:System.Windows.Window.Activated> olay.  
  
> [!NOTE]
>  Bir pencere ilk kez açıldığında <xref:System.Windows.FrameworkElement.Loaded> ve <xref:System.Windows.Window.ContentRendered> olayları yalnızca sonra oluştuğunda <xref:System.Windows.Window.Activated> olayı oluşturulur. Bunu göz önünde bir pencere etkili bir şekilde açıldığında kabul edilebilir <xref:System.Windows.Window.ContentRendered> tetiklenir.  
  
 Bir pencere etkin olduktan sonra bir kullanıcı aynı uygulamada başka bir pencere etkinleştirmek veya başka bir uygulamayı etkinleştirin. Bu durum oluştuğunda, şu andaki etkin pencere devre dışı olur ve başlatır <xref:System.Windows.Window.Deactivated> olay. Kullanıcı şu anda devre dışı bırakılmış bir pencere seçtiğinde, benzer şekilde, pencereyi tekrar etkin hale gelir ve <xref:System.Windows.Window.Activated> tetiklenir.  
  
 İşlemek için yaygın nedenlerinden biri <xref:System.Windows.Window.Activated> ve <xref:System.Windows.Window.Deactivated> etkinleştirmek ve bir pencere etkin olduğunda, yalnızca çalıştırabilirsiniz işlevini devre dışı bırakın. Örneğin, bazı windows sabit kullanıcı girişini veya oyun ve video oynatıcılar dahil olmak üzere, dikkat gerektiren etkileşimli içeriği görüntüler. Aşağıdaki örnek, üstesinden nasıl gelineceğini gösterir basitleştirilmiş bir video oynatıcı <xref:System.Windows.Window.Activated> ve <xref:System.Windows.Window.Deactivated> bu davranışı uygulamak için.  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 Bir pencere devre dışı bırakıldığında diğer uygulama türleri arka planda kod yine de çalıştırabilir. Örneğin, bir posta istemcisi posta sunucusu kullanıcı diğer uygulamaları kullanırken yoklama devam edebilir. Ana pencereyi devre dışı durumdayken bunlar gibi uygulamalar genellikle farklı veya ek davranış sağlar. Posta program göre bu gelen kutunuza yeni posta öğe ekleme ve bir bildirim simgesi sistem tepsisine ekleme anlamına gelebilir. Posta pencerenin inceleyerek belirlenen etkin değilken, bir bildirim simgesi yalnızca görüntülenmesi <xref:System.Windows.Window.IsActive%2A> özelliği.  
  
 Çağırarak daha Acil kullanıcıya bildirmek bir pencere bir arka plan görevi tamamlanırsa isteyebilirsiniz <xref:System.Windows.Window.Activate%2A> yöntemi. Kullanıcı ile etkileşim kurma, başka bir uygulamanın ne zaman etkin <xref:System.Windows.Window.Activate%2A> , pencerenin görev çubuğu düğmesinin yanıp çağrılır. Bir kullanıcının geçerli uygulamayla etkileşim kurma, çağırma <xref:System.Windows.Window.Activate%2A> penceresini öne getirmek.  
  
> [!NOTE]
>  Uygulama kapsamı etkinleştirme kullanarak işleyebilir <xref:System.Windows.Application.Activated?displayProperty=nameWithType> ve <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> olayları.  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a>Bir pencereyi kapatma  
 Bir pencere kullanıcı kapattığında sona yakında başlar. Bir pencere aşağıdakiler dahil olmak üzere istemci olmayan alanda öğe kullanarak kapalı olabilir:  
  
-   **Kapat** öğesi **sistem** menüsü.  
  
-   ALT + F4 tuşuna basın.  
  
-   Tuşuna basarak **Kapat** düğmesi.  
  
 Bir pencereyi kapatmak için istemci alanını ek mekanizmalarına biri daha fazla ortak şunlardır sağlayabilirsiniz:  
  
-   Bir **çıkış** öğesi **dosya** menüsünde, genellikle ana uygulama windows için.  
  
-   A **Kapat** öğesi **dosya** menüsünde, genellikle ikincil uygulama penceresi.  
  
-   A **iptal** düğmesi, genellikle kalıcı bir iletişim kutusu.  
  
-   A **Kapat** düğmesi, genellikle modsuz iletişim kutusu.  
  
 Yanıt olarak özel Bu mekanizmaların birini pencereyi kapatmak için çağırmak gereken <xref:System.Windows.Window.Close%2A> yöntemi. Aşağıdaki örnek seçerek bir pencereyi özelliği uygulayan **çıkış** üzerinde **dosya** menüsü.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 Bir pencere kapandığında iki olaylar oluşur: <xref:System.Windows.Window.Closing> ve <xref:System.Windows.Window.Closed>.  
  
 <xref:System.Windows.Window.Closing> pencereyi kapatır ve hangi penceresi kapatma engellenebilir bir mekanizma sağlar önce oluşturulur. Pencerenin kapatılmasını engelleyecek yaygın nedenlerinden biri, pencere içeriğinin değiştirilen veri içeriyorsa, ' dir. Bu durumda <xref:System.Windows.Window.Closing> olay verileri olumsuz olup olmadığını ve bu durumda, kullanıcı verileri kaydetmeden pencereyi kapatma ya da devam mı, yoksa pencerenin kapatılmasını engelleyecek şekilde sormak belirlemek için işlenebilir. Aşağıdaki örnek, işleme önemli yönlerini gösterir <xref:System.Windows.Window.Closing>.  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  
 
  
 <xref:System.Windows.Window.Closing> Olay işleyicisine geçirilen bir <xref:System.ComponentModel.CancelEventArgs>, uygulayan `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> ayarlamak için özellik `true` pencere kapatılmasını engelleyecek.  
  
 Varsa <xref:System.Windows.Window.Closing> işlenmiyor, veya ele ancak iptal, pencere kapanacaktır. Yalnızca bir pencere gerçekten kapanmadan önce <xref:System.Windows.Window.Closed> tetiklenir. Bu noktada, bir pencere kapatmaktan men önlenemeyen.  
  
> [!NOTE]
>  Bir uygulamayı otomatik olarak ana uygulama penceresini kapattığı zaman kapatmak için yapılandırılabilir (bkz <xref:System.Windows.Application.MainWindow%2A>) veya son pencereyi kapatır. Ayrıntılar için bkz <xref:System.Windows.Application.ShutdownMode%2A>.  
  
 Bir pencere açıkça istemci olmayan ve istemci bölümlerinde sağlanan mekanizmaları yoluyla kapatılabilir, ancak pencere örtük olarak davranışını uygulamanın diğer kısımlarını sonucunda kapatılabilir veya [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], aşağıdakiler dahil:  
  
-   Bir kullanıcı oturumu sonlandırdığında veya Windows kapatır.  
  
-   Bir pencerenin sahibini kapatır (bkz <xref:System.Windows.Window.Owner%2A>).  
  
-   Ana uygulama penceresi kapatıldığında ve <xref:System.Windows.Application.ShutdownMode%2A> olduğu <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
-   <xref:System.Windows.Application.Shutdown%2A> çağrılır.  
  
> [!NOTE]
>  Pencere kapatılır sonra açılamaz.  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a>Pencere ömür olayları  
 Aşağıdaki çizimde, pencerenin yaşam süresi asıl olayların sırasını gösterir:  
  
 ![Bir pencerenin yaşam süresi olayları gösteren diyagram.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 Aşağıdaki çizimde asıl olayların sırası etkinleştirme gösterilen bir pencere ömrü gösterir (<xref:System.Windows.Window.ShowActivated%2A> ayarlanır `false` pencere gösterilmeden önce):  
  
 ![Bir pencerenin etkin kalma süresi olmadan etkinleştirme olayları gösteren diyagram.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a>Pencere konumu  
 Bir penceresi açıkken, x ve y konumu sahip boyutlarına göre Masaüstü. Bu konum, inceleyerek belirlenebilir <xref:System.Windows.Window.Left%2A> ve <xref:System.Windows.Window.Top%2A> özellikleri, sırasıyla. Pencerenin konumunu değiştirmek için bu özellikleri ayarlayabilirsiniz.  
  
 İlk konumunu belirtebilirsiniz bir <xref:System.Windows.Window> zaman ilk göründüğü ayarlayarak <xref:System.Windows.Window.WindowStartupLocation%2A> aşağıdakilerden birini özelliğiyle <xref:System.Windows.WindowStartupLocation> sabit listesi değerleri:  
  
-   <xref:System.Windows.WindowStartupLocation.CenterOwner> (varsayılan)  
  
-   <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
-   <xref:System.Windows.WindowStartupLocation.Manual>  
  
 Başlangıç konumu olarak belirtilmişse <xref:System.Windows.WindowStartupLocation.Manual>ve <xref:System.Windows.Window.Left%2A> ve <xref:System.Windows.Window.Top%2A> değil ayarlandığını, <xref:System.Windows.Window> görünmesini Windows için bir konum ister.  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a>En üstteki Windows ve Z düzeni  
 X ve y konumu, bir pencere ayrıca sahip olmanın yanı sıra diğer windows göre dikey konumunu belirler z boyutundaki bir konum vardır. Bu pencerenin z düzeni bilinir ve iki tür vardır: normal z düzenini ve en üst z düzeni. Pencerenin konumu *normal z düzenini* , şu anda etkin olup olmamasına göre belirlenir. Varsayılan olarak, bir pencere normal z düzeninde bulunur. Pencerenin konumu *üstteki z düzenini* Ayrıca, şu anda etkin olup olmamasına göre belirlenir. Ayrıca, en üst z düzeninde windows her zaman windows normal z düzeninde üstünde bulunur. Bir pencere ayarlayarak en üst z düzeninde bulunan kendi <xref:System.Windows.Window.Topmost%2A> özelliğini `true`.  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 Her z düzenini içinde şu andaki etkin pencere tüm diğer pencerelerin aynı z düzeninde görüntülenir.  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a>Pencere boyutu  
 Bir masaüstü konuma sahip olmanın yanı sıra, bir pencere çeşitli genişlik ve yükseklik özellikleri dahil olmak üzere çeşitli özellikler tarafından belirlenen bir boyutu vardır ve <xref:System.Windows.Window.SizeToContent%2A>.  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, ve <xref:System.Windows.FrameworkElement.MaxWidth%2A> pencere yaşam süresi boyunca olabilir ve aşağıdaki örnekte gösterildiği gibi yapılandırılmış genişlikleri aralığını yönetmek için kullanılır.  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 Pencere yüksekliği yönetilir <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, ve <xref:System.Windows.FrameworkElement.MaxHeight%2A>ve aşağıdaki örnekte gösterilen şekilde yapılandırılır.  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 Çeşitli genişliği değerlerini ve yükseklik değerleri aralığını belirtmek için herhangi bir ilgili boyut için belirtilen aralıkta olacak şekilde yeniden boyutlandırılabilir pencere yüksekliğini ve genişliğini mümkündür. Geçerli genişlik ve yükseklik algılamak için inceleyin <xref:System.Windows.FrameworkElement.ActualWidth%2A> ve <xref:System.Windows.FrameworkElement.ActualHeight%2A>sırasıyla.  
  
 Genişlik ve yükseklik pencerenizin isterseniz penceresi boyutuna en uygun bir boyut için içerik, kullanabileceğiniz <xref:System.Windows.Window.SizeToContent%2A> özelliği aşağıdaki değerlere sahip:  
  
-   <xref:System.Windows.SizeToContent.Manual>. Etki yok (varsayılan).  
  
-   <xref:System.Windows.SizeToContent.Width>. Her ikisi de ayarını aynı etkiye sahip içerik genişliği Sığdır <xref:System.Windows.FrameworkElement.MinWidth%2A> ve <xref:System.Windows.FrameworkElement.MaxWidth%2A> içerik genişliğine.  
  
-   <xref:System.Windows.SizeToContent.Height>. Her ikisi de ayarını aynı etkiye sahip içerik yüksekliği Sığdır <xref:System.Windows.FrameworkElement.MinHeight%2A> ve <xref:System.Windows.FrameworkElement.MaxHeight%2A> yüksekliğine içeriği.  
  
-   <xref:System.Windows.SizeToContent.WidthAndHeight>. İçerik genişliği ve her ikisi de ayarı aynı etkiye sahip yüksekliği Sığdır <xref:System.Windows.FrameworkElement.MinHeight%2A> ve <xref:System.Windows.FrameworkElement.MaxHeight%2A> içeriği ve ayarı hem yüksekliğine <xref:System.Windows.FrameworkElement.MinWidth%2A> ve <xref:System.Windows.FrameworkElement.MaxWidth%2A> içerik genişliğine.  
  
 Aşağıdaki örnek bir pencere otomatik olarak ilk göründüğü içeriğini, dikey ve yatay olarak, uygun boyutları gösterir.  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:System.Windows.Window.SizeToContent%2A> kod nasıl bir içeriği sığdırmak için yeniden boyutlandırır belirtmek için bir özellik.
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a>Boyutlandırma özelliklerini için öncelik sırası  
 Aslında, genişlik ve yükseklik yeniden boyutlandırılabilir pencere aralığını tanımlamak için bir pencere çeşitli boyutlarda özelliklerini birleştirin. Geçerli bir aralık korunduğu emin olmak için <xref:System.Windows.Window> öncelik aşağıdaki sıralardan kullanarak boyutu özelliklerin değerlerini değerlendirir.  
  
 **Yükseklik özellikleri için:**  
  
1.  <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2.  <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3.  <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4.  <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 **Genişlik özellikleri için:**  
  
1.  <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2.  <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3.  <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4.  <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 Bu, ile yönetilen büyütüldüğünde öncelik sırasını pencere boyutunu da belirleyebilirsiniz <xref:System.Windows.Window.WindowState%2A> özelliği.  
  
<a name="WindowState"></a>   
## <a name="window-state"></a>Pencere durumu  
 Yeniden boyutlandırılabilir bir pencere ömrü boyunca üç duruma sahip olabilir: normal, küçültülmüş ve ekranı. Bir pencere bir *normal* pencere varsayılan durumuna bir durumdur. Bu durum içeren bir pencere, taşıma ve yeniden boyutlandırılabilir ise boyutlandırma tutamacı ya da kenarlığını kullanarak yeniden boyutlandırın açmasına olanak sağlar.  
  
 İçeren bir pencere bir *simge durumuna küçültülmüş* durumu varsa, görev çubuğu düğmesinin için daraltır <xref:System.Windows.Window.ShowInTaskbar%2A> ayarlanır `true`; Aksi takdirde, olabilir ve masaüstünde sol alt köşesindeki kendisi yeniden yerleştirir en küçük olası boyuta daraltır. Ne tür simge durumuna küçültülmüş pencerenin kenarlık kullanarak yeniden boyutlandırılabilir veya masaüstü görev çubuğuna gösterilmeyen bir simge durumuna küçültülmüş pencereyi sürüklenebilir rağmen tutamacı, yeniden boyutlandırma.  
  
 Bir pencere bir *ekranı* durumu genişletilir yalnızca büyüklüğünde olur en fazla boyutu olabilir, kendi <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, ve <xref:System.Windows.Window.SizeToContent%2A> özellikleri dikte. Bir simge durumuna küçültülmüş pencereyi gibi kaplamış boyutlandırma tutamacı kullanarak veya kenarlığı sürükleyerek yeniden boyutlandırılamıyor.  
  
> [!NOTE]
>  Değerlerini <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, ve <xref:System.Windows.FrameworkElement.Height%2A> penceresinin özellikler veya olsa bile pencere şu anda ekranı simge durumuna küçültülmüş normal durumu değerlerini her zaman gösterir.  
  
 Bir pencerenin durumunu ayarlanarak yapılandırılabilir kendi <xref:System.Windows.Window.WindowState%2A> aşağıdakilerden biri olabilir özelliği <xref:System.Windows.WindowState> sabit listesi değerleri:  
  
-   <xref:System.Windows.WindowState.Normal> (varsayılan)  
  
-   <xref:System.Windows.WindowState.Maximized>  
  
-   <xref:System.Windows.WindowState.Minimized>  
  
 Aşağıdaki örnek, açıldığında, tam ekran olarak gösterilen bir pencere oluşturma işlemi gösterilmektedir.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 Genel olarak, ayarlamalısınız <xref:System.Windows.Window.WindowState%2A> bir pencerenin başlangıç durumunu yapılandırmak için. Yeniden boyutlandırılabilir penceresinde gösterilen sonra kullanıcılar simge durumuna küçült tuşuna basın, en üst düzeye çıkarmak ve pencere durumu değiştirmek için pencerenin başlık çubuğundaki düğmelere geri yükleme.  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a>Görünüm penceresi  
 Bir pencerenin istemci alanının görünümü, penceresine özgü içerik, düğmeler, etiketler ve metin kutuları gibi ekleyerek değiştirin. İstemci olmayan alanın yapılandırmak için <xref:System.Windows.Window> dahil çeşitli özellikler sağlar <xref:System.Windows.Window.Icon%2A> bir pencerenin simgesini ve <xref:System.Windows.Window.Title%2A> başlığını ayarlamak için.  
  
 Bir pencerenin yeniden boyutlandırma modu, pencere stili yapılandırarak istemci dışı alan kenarlık davranışını ve görünümünü de değiştirebilirsiniz ve masaüstü görev çubuğuna bir düğme olarak görülüyor.  
  
  
<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a>Modu yeniden boyutlandırma  
 Yapılandırmanıza bağlı olarak <xref:System.Windows.Window.WindowStyle%2A> özelliğini denetleyebilirsiniz nasıl (ve eğer) kullanıcılar penceresini yeniden boyutlandırın. Bir kullanıcı olup olmadığını kenarlığını fare ile sürükleyerek pencereyi boyutlandırabilirsiniz olmadığını styl okna seçimi etkiler **simge durumuna küçült**, **Ekranı Kapla**, ve **yeniden boyutlandırma** düğmeleri İstemci olmayan alanın görünür ve görünüyorlarsa, bunlar etkinleştirilip etkinleştirilmediği.  
  
 Nasıl bir pencereyi yeniden boyutlandırır ayarlayarak yapılandırabilirsiniz, <xref:System.Windows.Window.ResizeMode%2A> aşağıdakilerden biri olabilir özelliği <xref:System.Windows.ResizeMode> sabit listesi değerleri:  
  
-   <xref:System.Windows.ResizeMode.NoResize>  
  
-   <xref:System.Windows.ResizeMode.CanMinimize>  
  
-   <xref:System.Windows.ResizeMode.CanResize> (varsayılan)  
  
-   <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 Olduğu gibi <xref:System.Windows.Window.WindowStyle%2A>, yeniden boyutlandırma modunu pencerenin, büyük olasılıkla ondan ayarlarsınız, yani ömrü boyunca değişme olasılığı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme.  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 Bir pencere ekranı olup olmadığını algılayan Not küçültülebilir ya da inceleyerek geri <xref:System.Windows.Window.WindowState%2A> özelliği.  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a>Pencere stili  
 Bir pencerenin istemci olmayan alanından sunulur kenarlık, çoğu uygulama için uygundur. Ancak, nerede farklı kenarlık türü gereklidir veya hiçbir kenarlık penceresi türüne bağlı olarak, gerekli koşullar vardır.  
  
 Bir pencere kenarlığını ne tür denetlemek için alır, ayarladığınız kendi <xref:System.Windows.Window.WindowStyle%2A> aşağıdaki değerlerden birini özelliğiyle <xref:System.Windows.WindowStyle> sabit listesi:  
  
-   <xref:System.Windows.WindowStyle.None>  
  
-   <xref:System.Windows.WindowStyle.SingleBorderWindow> (varsayılan)  
  
-   <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
-   <xref:System.Windows.WindowStyle.ToolWindow>  
  
 Bu pencere stilleri etkisini aşağıdaki resimde gösterilmektedir:  
  
 ![Pencere sınır stillerini gösterimi.](./media/wpf-windows-overview/window-border-styles.png)  
  
 Ayarlayabileceğiniz <xref:System.Windows.Window.WindowStyle%2A> kullanarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işaretleme veya kod; bir pencere ömrü boyunca değişme olasılığı olduğu için büyük olasılıkla kullanarak yapılandıracağınız [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>Dikdörtgen olmayan pencere stili  
 Burada kenarlık stilleri, durumlar da vardır <xref:System.Windows.Window.WindowStyle%2A> sağlayan sahip olmanız yeterli değildir. Örneğin, benzer olmayan bir kenarlığa sahip bir uygulama oluşturmak isteyebilirsiniz [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] kullanır.  
  
 Örneğin, aşağıdaki şekilde gösterilen konuşma Kabarcık penceresi göz önünde bulundurun:  
  
 ![Sürükleme Me. bildiren bir konuşma Kabarcık penceresi](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 Bu tür bir pencerede ayarlayarak oluşturulabilir <xref:System.Windows.Window.WindowStyle%2A> özelliğini <xref:System.Windows.WindowStyle.None>ve özel'i kullanarak destekleyen <xref:System.Windows.Window> saydamlık için.  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 Bu değerlerin birleşimini, tamamen saydam işlemek için pencerenin bildirir. Bu durumda, pencerenin istemci olmayan alan Kenarlıklar (menüyü Kapat, Küçült, Ekranı Kapla ve geri düğmeleri ve benzeri) kullanılamaz. Sonuç olarak, size sağlamak kendi gerekir.  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a>Görev çubuğu durum  

Varsayılan görünüm penceresinin aşağıdaki şekilde gösterilene benzer bir görev çubuğu düğme içerir:

 ![Bir pencere ile görev çubuğunu gösteren ekran görüntüsü.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 İleti kutuları ve iletişim kutuları gibi bir görev çubuğu düğmesinin windows bazı türleri yok (bkz [iletişim kutularına genel bakış](dialog-boxes-overview.md)). Bir pencere için görev çubuğu düğmesinin ayarlayarak gösterilip gösterilmeyeceğini denetleyen <xref:System.Windows.Window.ShowInTaskbar%2A> özelliği (`true` varsayılan olarak).  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
 <xref:System.Windows.Window> gerektirir `UnmanagedCode` güvenlik izni oluşturulacak. Yüklü ve yerel makineden başlatılan uygulamalar için bu uygulamaya verilen izinleri kümesi içinde döner.  
  
 Ancak, bu Internet veya yerel intranet bölgesi kullanımından başlatılan uygulamalara izinler kümesini dışında kalan [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)]. Sonuç olarak, kullanıcılar alır bir [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] güvenlik uyarısı ve uygulama tam güven için ayarlanmış izin yükseltmesine gerekir.  
  
 Ayrıca, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] windows veya iletişim kutularında, varsayılan olarak gösteremez. Tek başına uygulama güvenlik konuları hakkında bir tartışma için bkz. [WPF güvenlik stratejisi - Platform güvenliği](../wpf-security-strategy-platform-security.md).  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a>Diğer Windows türleri  
 <xref:System.Windows.Navigation.NavigationWindow> gezinilebilir içeriği barındırmak için tasarlanmış bir penceredir. Daha fazla bilgi için [gezintiye genel bakış](navigation-overview.md)).  
  
 Genellikle bir işlev tamamlamak için bir kullanıcıdan bilgi toplamak için kullanılan bir windows iletişim kutularıdır. Örneğin, ne zaman bir kullanıcının istediği bir dosyayı açmaya **Dosya Aç** iletişim kutusu kullanıcıdan dosya adını almak için bir uygulama tarafından genellikle görüntülenir. Daha fazla bilgi için [iletişim kutularına genel bakış](dialog-boxes-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [İletişim Kutularına Genel Bakış](dialog-boxes-overview.md)
- [WPF Uygulaması Derleme](building-a-wpf-application-wpf.md)
