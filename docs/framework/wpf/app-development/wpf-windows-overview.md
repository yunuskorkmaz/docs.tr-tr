---
title: Windows'a genel bakış
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
ms.openlocfilehash: b06afb56f43a874815cf9f679f1f7fefbdfd4565
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145546"
---
# <a name="wpf-windows-overview"></a>WPF Windows'a Genel Bakış
Kullanıcılar Windows Presentation Foundation (WPF) bağımsız uygulamaları yla windows üzerinden etkileşimde bulunuyor. Bir pencerenin birincil amacı, verileri görselleştiren ve kullanıcıların verilerle etkileşimkurmasını sağlayan içeriği barındırmaktır. Bağımsız WPF uygulamaları <xref:System.Windows.Window> sınıfı kullanarak kendi pencerelerini sağlar. Bu konu, <xref:System.Windows.Window> bağımsız uygulamalarda pencere oluşturma ve yönetme temellerini kapsayan önce tanıtır.  
  
> [!NOTE]
> XAML tarayıcı uygulamaları (XBAP'ler) ve gevşek [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sayfalar da dahil olmak üzere tarayıcı tarafından barındırılan WPF uygulamaları kendi pencerelerini sağlamaz. Bunun yerine, Windows Internet Explorer tarafından sağlanan pencerelerde barındırılır. Bkz. [WPF XAML Tarayıcı Uygulamaları Genel Bakış.](wpf-xaml-browser-applications-overview.md)  

<a name="TheWindowClass"></a>
## <a name="the-window-class"></a>Pencere Sınıfı  
 Aşağıdaki şekil, bir pencerenin kurucu bölümlerini gösterir:  
  
 ![Pencere öğelerini gösteren ekran görüntüsü.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 Bir pencere iki alana ayrılır: istemci olmayan alan ve istemci alanı.  
  
 Pencerenin *istemci olmayan alanı* WPF tarafından uygulanır ve aşağıdakiler de dahil olmak üzere çoğu pencerede ortak olan pencere bölümlerini içerir:  
  
- Bir sınır.  
  
- Bir başlık çubuğu.  
  
- Bir simge.  
  
- Düğmeleri En Aza Indirin, En Üst Düzeye Çıkarın ve Geri Yükleyin.  
  
- Kapat düğmesi.  
  
- Kullanıcıların bir pencereyi en aza indirmesine, en üst düzeye çıkarmasına, geri yüklemesine, taşımasına, yeniden boyutlandırmasına ve kapatmasına olanak tanıyan menü öğeleriiçeren bir Sistem menüsü.  
  
 Pencerenin *istemci alanı,* pencerenin istemci olmayan alanı içindeki alandır ve geliştiriciler tarafından menü çubukları, araç çubukları ve denetimler gibi uygulamaya özgü içerik eklemek için kullanılır.  
  
 WPF'de, bir pencere aşağıdakileri <xref:System.Windows.Window> yapmak için kullandığınız sınıf tarafından kapsüllenir:  
  
- Bir pencere görüntüleyin.  
  
- Bir pencerenin boyutunu, konumunu ve görünümünü yapılandırın.  
  
- Uygulamaya özgü içeriği barındırın.  
  
- Bir pencerenin ömrünü yönetin.  
  
<a name="DefiningAWindow"></a>
## <a name="implementing-a-window"></a>Pencere Uygulama  
 Tipik bir pencerenin uygulanması, *görünümün* kullanıcılara nasıl göründüğünü tanımladığı hem görünüm hem de davranışiçerir ve *davranış,* kullanıcılar la etkileşim de dahil olmak üzere pencerenin işlevlerini tanımlar. WPF'de, kod veya biçimlendirme kullanarak bir pencerenin görünümünü ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] davranışını uygulayabilirsiniz.  
  
 Ancak genel olarak, bir pencerenin görünümü [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme kullanılarak uygulanır ve davranışı aşağıdaki örnekte gösterildiği gibi kod arkası kullanılarak uygulanır.  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 Biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyasının ve kod arkası dosyanın birlikte çalışmasını sağlamak için aşağıdakiler gereklidir:  
  
- Biçimlendirmede, `Window` öğe özniteliği `x:Class` içermelidir. Uygulama `x:Class` oluşturulduğunda, biçimlendirme dosyasındaki varlığı Microsoft build engine (MSBuild) `partial` türeyen <xref:System.Windows.Window> ve öznitelik tarafından `x:Class` belirtilen adı taşıyan bir sınıf oluşturmak için neden olur. Bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] şema için bir XML ad alanı bildirimi `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` eklenmesini gerektirir ( ). Oluşturulan `partial` sınıf, olayları `InitializeComponent` kaydetmek ve biçimlendirmede uygulanan özellikleri ayarlamak için çağrılan yöntemi uygular.  
  
- Kod arkasında, sınıf biçimlendirmeözdeki öznitelik tarafından `partial` `x:Class` belirtilen aynı ada sahip bir sınıf olmalı <xref:System.Windows.Window>ve 'den türemesi gerekir. Bu, kod arkası dosyasının, uygulama `partial` oluşturulduğunda biçimlendirme dosyası için oluşturulan sınıfla ilişkilendirilmesine izin verir [(bkz.](building-a-wpf-application-wpf.md)  
  
- Kod arkasında, <xref:System.Windows.Window> sınıf `InitializeComponent` yöntemi çağıran bir oluşturucu uygulamalıdır. `InitializeComponent`olayları kaydetmek ve biçimlendirmede tanımlanan `partial` özellikleri ayarlamak için biçimlendirme dosyasının oluşturulan sınıfı tarafından uygulanır.  
  
> [!NOTE]
> Visual Studio'yu <xref:System.Windows.Window> kullanarak projenize yeni bir <xref:System.Windows.Window> ekleme yaptığınızda, biçim hem biçimlendirme hem de kod arkası kullanılarak uygulanır ve burada açıklandığı gibi biçimlendirme ve kod arkası dosyaları arasındaki ilişkilendirme oluşturmak için gerekli yapılandırmayı içerir.  
  
 Bu yapılandırma yerinde olduğu için, biçimlendirmede [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pencerenin görünümünü tanımlamaya ve davranışını kod arkasında uygulamaya odaklanabilirsiniz. Aşağıdaki örnekte, biçimlendirmede [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulanan düğmeli bir pencere ve kod arkasında uygulanan <xref:System.Windows.Controls.Primitives.ButtonBase.Click> düğmeolayı için bir olay işleyicisi gösterilmektedir.  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>
## <a name="configuring-a-window-definition-for-msbuild"></a>MSBuild için Pencere Tanımı Nı Yapılandırma  
 Pencerenizi nasıl uyguladığınız, pencerenin MSBuild için nasıl yapılandırılacağını belirler. Hem biçimlendirme hem de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kod arkası kullanılarak tanımlanan bir pencere için:  
  
- XAML biçimlendirme dosyaları MSBuild `Page` öğeleri olarak yapılandırılır.  
  
- Kod arkası dosyalar MSBuild `Compile` öğeleri olarak yapılandırılır.  
  
 Bu, aşağıdaki MSBuild proje dosyasında gösterilir.  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 WPF uygulamaları oluşturma hakkında daha fazla bilgi için [wpf uygulaması oluşturma](building-a-wpf-application-wpf.md)bilgisine bakın.  
  
<a name="WindowLifetime"></a>
## <a name="window-lifetime"></a>Pencere Ömrü  
 Herhangi bir sınıfta olduğu gibi, bir pencerenin de ilk anında başlatıldıktan sonra açılan, etkinleştirilen ve devre dışı bırakılan ve sonunda kapandığı bir ömrü vardır.  

<a name="Opening_a_Window"></a>
### <a name="opening-a-window"></a>Pencere Açma  
 Bir pencereyi açmak için, önce aşağıdaki örnekte gösterilen bir örnek oluşturursunuz.  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 Bu örnekte, `MarkupAndCodeBehindWindow` <xref:System.Windows.Application.Startup> uygulama başlatıldığında anlık olarak, olay yükseltildiğinde oluşur.  
  
 Bir pencere anında olduğunda, bu pencereye yapılan bir başvuru otomatik olarak nesne tarafından <xref:System.Windows.Application> yönetilen <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>bir pencere listesine eklenir (bkz. Ayrıca, anlık olarak ayarlanacak ilk pencere varsayılan <xref:System.Windows.Application> olarak ana uygulama penceresi olarak <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>ayarlanır (bkz.  
  
 Pencere sonunda <xref:System.Windows.Window.Show%2A> yöntemi arayarak açılır; sonuç aşağıdaki şekilde gösterilmiştir.  
  
 ![Window.Show'u arayarak Açılan Pencere](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 Arayarak <xref:System.Windows.Window.Show%2A> açılan pencere, moduz bir penceredir, bu da uygulamanın kullanıcıların aynı uygulamadaki diğer pencereleri etkinleştirmesine olanak tanıyan bir modda çalıştığı anlamına gelir.  
  
> [!NOTE]
> <xref:System.Windows.Window.ShowDialog%2A>iletişim kutuları gibi pencereleri modally açmak için çağrılır. Daha fazla bilgi için [İletişim Kutularına Genel Bakış'a](dialog-boxes-overview.md) bakın.  
  
 Çağrıldığında, <xref:System.Windows.Window.Show%2A> bir pencere, kullanıcı girişi almasına izin veren altyapıyı oluşturmak için gösterilmeden önce başlatma çalışması gerçekleştirir. Pencere başharfe çarptırıldığında, <xref:System.Windows.Window.SourceInitialized> olay yükseltilir ve pencere gösterilir.  
  
 Kısayol olarak, <xref:System.Windows.Application.StartupUri%2A> bir uygulama başlatıldığında otomatik olarak açılan ilk pencereyi belirtmek için ayarlanabilir.  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 Uygulama başladığında, değeri <xref:System.Windows.Application.StartupUri%2A> ile belirtilen pencere modelessly açılır; dahili olarak, pencere yöntemini <xref:System.Windows.Window.Show%2A> çağırarak açılır.  
  
<a name="Ownership"></a>
#### <a name="window-ownership"></a>Pencere Sahipliği  
 <xref:System.Windows.Window.Show%2A> Yöntem kullanılarak açılan pencerenin, onu oluşturan pencereyle örtülü bir ilişkisi yoktur; kullanıcılar diğerpencereden bağımsız olarak her iki pencereyle de etkileşimkurabilir, bu da her iki pencerenin de aşağıdakileri yapabileceği anlamına gelir:  
  
- Diğerini kapatın (pencerelerden biri <xref:System.Windows.Window.Topmost%2A> özelliği `true`ayarlı değilse).  
  
- Diğerini etkilemeden en aza indirilme, en üst düzeye çıkarma ve geri yükleme.  
  
 Bazı pencereler, onları açan pencereyle ilişki gerektirir. Örneğin, Tümleşik Geliştirme Ortamı (IDE) uygulaması, tipik davranışı bunları oluşturan pencereyi kapsayacak şekilde özellik pencerelerini ve araç pencerelerini açabilir. Ayrıca, bu tür pencereler her zaman kapanmalı, en aza indirilmeli, en üst düzeye çıkarmalı ve onları oluşturan pencereyle uyumlu olarak geri yüklemelidir. Böyle bir ilişki bir pencerenin başka bir *penceresinin sahibine ait* hale getirilerek kurulabilir ve sahip <xref:System.Windows.Window.Owner%2A> *penceresinin* *özelliğini*sahip penceresine bir başvuruyla ayarlayarak elde edilir. Bu, aşağıdaki örnekte gösterilir.  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 Mülkiyet kurulduktan sonra:  
  
- Sahip olunan pencere, <xref:System.Windows.Window.Owner%2A> mülkünün değerini inceleyerek sahibinin penceresine başvurulabilir.  
  
- Sahip penceresi, <xref:System.Windows.Window.OwnedWindows%2A> sahip olduğu tüm pencereleri mülkünün değerini inceleyerek keşfedebilir.  
  
<a name="Preventing"></a>
#### <a name="preventing-window-activation"></a>Pencere Etkinleştirmesini Önleme  
 Gösterildiğinde, Internet messenger tarzı bir uygulamanın konuşma pencereleri veya bir e-posta uygulamasının bildirim pencereleri gibi pencerelerin etkinleştirilmemesi gereken senaryolar vardır.  
  
 Uygulamanızın gösterildiğinde etkinleştirilmemesi gereken bir penceresi varsa, yöntemi <xref:System.Windows.Window.ShowActivated%2A> ilk `false` kez <xref:System.Windows.Window.Show%2A> aramadan önce özelliğini ayarlayabilirsiniz. Sonuç olarak:  
  
- Pencere etkinleştirilmedi.  
  
- Pencerenin <xref:System.Windows.Window.Activated> olayı yükseltilmez.  
  
- Şu anda etkinleştirilen pencere etkinleştirilmez.  
  
 Ancak, kullanıcı istemci veya istemci olmayan alanı tıklatarak pencere etkinleştirir etkinleştirmez pencere etkinleştirilir. Bu durumda:  
  
- Pencere etkinleştirildi.  
  
- Pencerenin <xref:System.Windows.Window.Activated> olayı yükseltilir.  
  
- Önceden etkinleştirilen pencere devre dışı bırakılır.  
  
- Pencerenin <xref:System.Windows.Window.Deactivated> ve <xref:System.Windows.Window.Activated> olayların ardından kullanıcı eylemlerine yanıt olarak beklendiği gibi yükseltilir.  
  
<a name="Window_Activation"></a>
### <a name="window-activation"></a>Pencere Etkinleştirme  
 Bir pencere ilk açıldığında, etkin pencere olur (ayarlı <xref:System.Windows.Window.ShowActivated%2A> olarak `false`gösterilmedikçe). *Etkin pencere,* tuş vuruşları ve fare tıklamaları gibi kullanıcı girişlerini yakalayan penceredir. Bir pencere etkin hale geldiğinde, <xref:System.Windows.Window.Activated> olayı yükseltir.  
  
> [!NOTE]
> Bir pencere ilk açıldığında, <xref:System.Windows.FrameworkElement.Loaded> <xref:System.Windows.Window.ContentRendered> olaylar ancak <xref:System.Windows.Window.Activated> olay yükseltildikten sonra yükseltilir. Bunu göz önünde bulundurarak, bir pencere <xref:System.Windows.Window.ContentRendered> etkili bir şekilde açıldığında açılabilir.  
  
 Bir pencere etkin hale geldikten sonra, kullanıcı aynı uygulamada başka bir pencereyi etkinleştirebilir veya başka bir uygulamayı etkinleştirebilir. Bu durumda, şu anda etkin olan <xref:System.Windows.Window.Deactivated> pencere devre dışı bırakılır ve olayı yükseltir. Aynı şekilde, kullanıcı şu anda devre dışı bırakılmış bir <xref:System.Windows.Window.Activated> pencere seçtiğinde, pencere yeniden etkin olur ve yükseltilir.  
  
 Yalnızca <xref:System.Windows.Window.Activated> bir pencere <xref:System.Windows.Window.Deactivated> etkin olduğunda çalıştırılabilen işlevselliği etkinleştirmek ve devre dışı etmek yaygın bir nedendir. Örneğin, bazı pencereler, oyunlar ve video oynatıcılar da dahil olmak üzere sürekli kullanıcı girişi veya dikkat gerektiren etkileşimli içerik görüntüler. Aşağıdaki örnek, bu davranışın nasıl işleyeceğini <xref:System.Windows.Window.Activated> ve <xref:System.Windows.Window.Deactivated> uygulanacağını gösteren basitleştirilmiş bir video oynatıcıdır.  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 Diğer uygulama türleri, bir pencere devre dışı bırakıldığında arka planda kod çalıştırmaya devam edebilir. Örneğin, kullanıcı diğer uygulamaları kullanırken bir posta istemcisi posta sunucusunu yoklamaya devam edebilir. Bu gibi uygulamalar genellikle ana pencere devre dışı bırakılırken farklı veya ek davranış sağlar. Posta programıyla ilgili olarak, bu hem gelen kutusuna yeni posta öğesi nin eklenmesi hem de sistem tepsisine bir bildirim simgesi eklenmesi anlamına gelebilir. Bildirim simgesinin yalnızca posta penceresi etkin olmadığında görüntülenmesi gerekir ve bu <xref:System.Windows.Window.IsActive%2A> simge özelliği inceleyerek belirlenebilir.  
  
 Arka plan görevi tamamlanırsa, bir pencere <xref:System.Windows.Window.Activate%2A> arama yöntemini daha acil bir şekilde kullanıcıya bildirmek isteyebilir. Kullanıcı çağrıldığında <xref:System.Windows.Window.Activate%2A> etkinleştirilen başka bir uygulamayla etkileşim halindeyse, pencerenin görev çubuğu düğmesi yanıp söner. Bir kullanıcı geçerli uygulamayla etkileşim de <xref:System.Windows.Window.Activate%2A> bulunuyorsa, arama penceresi ön plana çıkarır.  
  
> [!NOTE]
> Uygulama kapsamı etkinleştirme <xref:System.Windows.Application.Activated?displayProperty=nameWithType> ve <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> olayları kullanarak işleyebilirsiniz.  
  
<a name="Closing_a_Window"></a>
### <a name="closing-a-window"></a>Pencereyi Kapatma  
 Bir pencerenin ömrü, kullanıcı kapatıldığında sona ermeye başlar. Bir pencere, aşağıdakiler de dahil olmak üzere istemci olmayan alandaki öğeler kullanılarak kapatılabilir:  
  
- **Sistem** menüsünün **Kapat** öğesi.  
  
- ALT+F4 tuşuna basArak.  
  
- **Kapat** düğmesine basın.  
  
 Bir pencereyi kapatmak için istemci alanına ek mekanizmalar sağlayabilirsiniz, bunlardan daha yaygın olan aşağıdakileri içerir:  
  
- Genellikle ana uygulama pencereleri için **Dosya** menüsündeki bir **Çıkış** öğesi.  
  
- **Dosya** menüsündeki **bir öğeyi genellikle** ikincil bir uygulama penceresinde kapat.  
  
- Genellikle modal iletişim kutusunda bir **İptal** düğmesi.  
  
- Genellikle modeless iletişim kutusunda **Kapat** düğmesi.  
  
 Bu özel mekanizmalardan birine yanıt olarak bir pencereyi <xref:System.Windows.Window.Close%2A> kapatmak için yöntemi aramanız gerekir. Aşağıdaki örnek, **Dosya** menüsünde **Çıkış'ı** seçerek pencereyi kapatma özelliğini uygular.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 Bir pencere kapandığında, iki olay <xref:System.Windows.Window.Closing> <xref:System.Windows.Window.Closed>yükselir: ve .  
  
 <xref:System.Windows.Window.Closing>pencere kapanmadan önce yükseltilir ve pencere kapanmasının önlenebileceği bir mekanizma sağlar. Pencere kapanmasını önlemenin yaygın nedenlerinden biri, pencere içeriğinin değiştirilmiş veriler içermesidir. Bu durumda, <xref:System.Windows.Window.Closing> olay verilerin kirli olup olmadığını belirlemek ve eğer öyleyse, kullanıcıya verileri kaydetmeden pencereyi kapatmaya devam edip etmeyeceğini sormak veya pencere kapatmayı iptal etmek için işlenebilir. Aşağıdaki örnek, işlemenin <xref:System.Windows.Window.Closing>temel yönlerini gösterir.  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <xref:System.Windows.Window.Closing> Olay işleyicisi, <xref:System.ComponentModel.CancelEventArgs>bir pencerenin `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> kapanmasını önlemek `true` için ayarladığınız özelliği uygulayan bir , geçti.  
  
 Ele <xref:System.Windows.Window.Closing> alınmaz veya işlenir ancak iptal edilmezse, pencere kapanır. Bir pencere kapanmadan hemen <xref:System.Windows.Window.Closed> önce, yükseltilir. Bu noktada, bir pencerenin kapanması engellenemez.  
  
> [!NOTE]
> Ana uygulama penceresi kapandığında (bakınız) <xref:System.Windows.Application.MainWindow%2A>veya son pencere kapandığında bir uygulama otomatik olarak kapatılacak şekilde yapılandırılabilir. Ayrıntılar için bkz. <xref:System.Windows.Application.ShutdownMode%2A>.  
  
 Bir pencere istemci olmayan ve istemci olmayan alanlarda sağlanan mekanizmalar aracılığıyla açıkça kapatılabilir, ancak aşağıdakiler de dahil olmak üzere uygulamanın veya Windows'un diğer bölümlerindeki davranışın bir sonucu olarak bir pencere de örtülü olarak kapatılabilir:  
  
- Bir kullanıcı Windows'u kapatır veya kapatır.  
  
- Pencerenin sahibi kapanır (bkz. <xref:System.Windows.Window.Owner%2A>).  
  
- Ana uygulama penceresi kapalıdır ve <xref:System.Windows.Application.ShutdownMode%2A> <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
- <xref:System.Windows.Application.Shutdown%2A>denir.  
  
> [!NOTE]
> Pencere kapatıldıktan sonra yeniden açılamaz.  
  
<a name="Window_Lifetime_Events"></a>
### <a name="window-lifetime-events"></a>Pencere Ömrü Etkinlikleri  
 Aşağıdaki resimde, bir pencerenin ömrü boyunca temel olayların sırasını gösterilmektedir:  
  
 ![Bir pencerenin ömründeki olayları gösteren diyagram.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 Aşağıdaki resimde etkinleştirme olmadan gösterilen bir pencerenin ömrü boyunca temel<xref:System.Windows.Window.ShowActivated%2A> olayların sırasını gösterir (pencere gösterilmeden `false` önce ayarlanır):  
  
 ![Etkinleştirme olmadan bir pencerenin ömründeki olayları gösteren diyagram.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>
## <a name="window-location"></a>Pencere Konumu  
 Bir pencere açıkken, masaüstüne göre x ve y boyutlarında bir konuma sahiptir. Bu konum, sırasıyla <xref:System.Windows.Window.Left%2A> <xref:System.Windows.Window.Top%2A> ve özellikleri inceleyerek belirlenebilir. Bu özellikleri pencerenin konumunu değiştirecek şekilde ayarlayabilirsiniz.  
  
 Ayrıca, <xref:System.Windows.Window.WindowStartupLocation%2A> özelliği aşağıdaki <xref:System.Windows.WindowStartupLocation> numaralandırma <xref:System.Windows.Window> değerlerinden biriyle ayarlayarak bir kişinin ilk görüntülendiğindeki ilk konumunu da belirtebilirsiniz:  
  
- <xref:System.Windows.WindowStartupLocation.CenterOwner>(varsayılan)  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 Başlangıç <xref:System.Windows.WindowStartupLocation.Manual>konumu olarak belirtilirse <xref:System.Windows.Window.Left%2A> ve <xref:System.Windows.Window.Top%2A> özellikler ayarlanmamışsa, <xref:System.Windows.Window> Windows'dan bir konumun görünmesini ister.  
  
<a name="Topmost_Windows_and_Z_Order"></a>
### <a name="topmost-windows-and-z-order"></a>En Üstte Windows ve Z-Order  
 X ve y konumuna sahip olmasının yanı sıra, bir pencerenin z boyutunda diğer pencerelere göre dikey konumunu belirleyen bir konumu da vardır. Bu pencerenin z sırası olarak bilinir ve iki türü vardır: normal z sırası ve en üstteki z-sırası. Normal *z düzenindeki* bir pencerenin konumu, şu anda etkin olup olmadığına göre belirlenir. Varsayılan olarak, bir pencere normal z-sırada yer alır. En *üstteki z-düzenindeki* pencerenin konumu da şu anda etkin olup olmadığına göre belirlenir. Ayrıca, en üstteki z-sıralı pencereler her zaman normal z-sırasına göre pencerelerin üzerinde yer alır. Bir pencere, özelliğini <xref:System.Windows.Window.Topmost%2A> . `true`  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 Her z-sırası içinde, şu anda etkin olan pencere aynı z-order'daki diğer tüm pencerelerin üzerinde görünür.  
  
<a name="WindowSize"></a>
## <a name="window-size"></a>Pencere Boyutu  
 Bir masaüstü konumuna sahip olmanın yanı sıra, bir pencere çeşitli genişlik ve <xref:System.Windows.Window.SizeToContent%2A>yükseklik özellikleri ve dahil olmak üzere çeşitli özellikleri tarafından belirlenen bir boyuta sahiptir.  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A> ve bir pencerenin ömrü boyunca sahip olabileceği genişlik aralığını yönetmek için kullanılır ve aşağıdaki örnekte gösterildiği gibi yapılandırılır.  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 Pencere yüksekliği , <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>ve , tarafından yönetilir ve aşağıdaki örnekte gösterildiği gibi yapılandırılır.  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 Çeşitli genişlik değerleri ve yükseklik değerleri her bir aralık belirtir, çünkü genişlik ve yeniden boyutlandırılabilir bir pencerenin yüksekliği için ilgili boyut için belirtilen aralık içinde herhangi bir yerde olması mümkündür. Geçerli genişliğini ve yüksekliğini <xref:System.Windows.FrameworkElement.ActualWidth%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A>algılamak için sırasıyla ve  
  
 Pencerenizin genişliğinin ve yüksekliğinin pencereiçeriğinin boyutuna uygun bir boyuta sahip olmasını istiyorsanız, <xref:System.Windows.Window.SizeToContent%2A> aşağıdaki değerlere sahip özelliği kullanabilirsiniz:  
  
- <xref:System.Windows.SizeToContent.Manual>. Hiçbir etkisi (varsayılan).  
  
- <xref:System.Windows.SizeToContent.Width>. İçerik genişliğine sığdır, bu da <xref:System.Windows.FrameworkElement.MinWidth%2A> hem <xref:System.Windows.FrameworkElement.MaxWidth%2A> ayarı hem de içeriğin genişliğiyle aynı etkiye sahiptir.  
  
- <xref:System.Windows.SizeToContent.Height>. Hem ayarı hem de <xref:System.Windows.FrameworkElement.MinHeight%2A> içeriğin yüksekliğiyle <xref:System.Windows.FrameworkElement.MaxHeight%2A> aynı etkiye sahip içerik yüksekliğine sığdırın.  
  
- <xref:System.Windows.SizeToContent.WidthAndHeight>. Hem <xref:System.Windows.FrameworkElement.MinHeight%2A> içerik hem de içeriğin yüksekliğini ayarlamakla <xref:System.Windows.FrameworkElement.MaxHeight%2A> aynı etkiye sahip olan <xref:System.Windows.FrameworkElement.MinWidth%2A> içerik <xref:System.Windows.FrameworkElement.MaxWidth%2A> genişliğine ve yüksekliğe ve içeriğin hem de genişliğine ayar.  
  
 Aşağıdaki örnekte, ilk gösterildiğinde hem dikey hem de yatay olarak içeriğine uyacak şekilde otomatik olarak boyutlandırılabilen bir pencere gösterilmektedir.  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Window.SizeToContent%2A> pencerenin içeriğine uyacak şekilde nasıl yeniden boyutlandırıldığını belirtmek için özelliğin kod olarak nasıl ayarlanır.
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>
## <a name="order-of-precedence-for-sizing-properties"></a>Boyutlandırma Özellikleri için Öncelik Sırası  
 Esasen, bir pencerenin çeşitli boyutözellikleri, yeniden boyutlandırılabilir bir pencere için genişlik ve yükseklik aralığını tanımlamak için birleştirir. Geçerli bir aralığın tutulmasını <xref:System.Windows.Window> sağlamak için, aşağıdaki öncelik emirlerini kullanarak boyut özelliklerinin değerlerini değerlendirir.  
  
 **Yükseklik Özellikleri için:**  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 **Genişlik Özellikleri için:**  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 Öncelik sırası, <xref:System.Windows.Window.WindowState%2A> özellik ile yönetilen en üst düzeye çıktığında bir pencerenin boyutunu da belirleyebilir.  
  
<a name="WindowState"></a>
## <a name="window-state"></a>Pencere Durumu  
 Yeniden boyutlandırılabilir bir pencerenin ömrü boyunca, üç durum olabilir: normal, en aza indirgenmiş ve en üst düzeye çıkarılabilir. *Normal* durumu olan bir pencere, pencerenin varsayılan durumudur. Bu duruma sahip bir pencere, yeniden boyutlandırılabilirse, yeniden boyutlandırma kavramasını veya kenarlığı kullanarak kullanıcının onu hareket ettirmesine ve yeniden boyutlandırmasına olanak tanır.  
  
 En aza *indirgenen* durumu olan bir pencere, <xref:System.Windows.Window.ShowInTaskbar%2A> ayarlanmışsa görev çubuğu düğmesine `true`çöker; aksi takdirde, mümkün olan en küçük boyuta çöker ve masaüstünün sol alt köşesine taşınır. Görev çubuğunda gösterilmeyen simge durumuna küçültülmüş bir pencere masaüstünde sürüncemede edilse de, kenarlık veya yeniden boyutlandırma kavrama kullanılarak en aza indirgenmiş pencere türü de yeniden boyutlandırılamaz.  
  
 *Maksimize bir* durum ile bir pencere olabilir maksimum boyutuna genişletir, <xref:System.Windows.FrameworkElement.MaxWidth%2A>hangi <xref:System.Windows.FrameworkElement.MaxHeight%2A>sadece <xref:System.Windows.Window.SizeToContent%2A> onun kadar büyük olacak , ve özellikleri dikte. Simge durumuna küçültülmüş bir pencere gibi, en üst düzeye çıkarılmış bir pencere yeniden boyutlandırma kavrama kullanılarak veya kenarlığı sürükleyerek yeniden boyutlandırılamaz.  
  
> [!NOTE]
> Pencere nin <xref:System.Windows.Window.Top%2A>değerleri <xref:System.Windows.Window.Left%2A> <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A> , , ve bir pencerenin özellikleri, pencere şu anda en üst düzeye çıkarıldığında veya en aza indirilmiş olsa bile, her zaman normal durum değerlerini temsil eder.  
  
 Bir pencerenin durumu, aşağıdaki <xref:System.Windows.Window.WindowState%2A> <xref:System.Windows.WindowState> numaralandırma değerlerinden birine sahip olabilecek özelliğini ayarlayarak yapılandırılabilir:  
  
- <xref:System.Windows.WindowState.Normal>(varsayılan)  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 Aşağıdaki örnek, açıldığında en üst düzey olarak gösterilen bir pencerenin nasıl oluşturulacak olduğunu gösterir.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 Genel olarak, bir <xref:System.Windows.Window.WindowState%2A> pencerenin ilk durumunu yapılandırmak için ayarlamanız gerekir. Yeniden boyutlandırılabilir bir pencere gösterildikten sonra, kullanıcılar pencere durumunu değiştirmek için pencerenin başlık çubuğundaki simge durumuna getirin, en üst düzeye çıkarabilir ve düğmeleri geri yükleyebilir.  
  
<a name="WindowAppearance"></a>
## <a name="window-appearance"></a>Pencere Görünümü  
 Düğmeler, etiketler ve metin kutuları gibi pencereye özgü içerik ekleyerek pencerenin istemci alanının görünümünü değiştirirsiniz. İstemci olmayan alanı yapılandırmak için, <xref:System.Windows.Window> bir <xref:System.Windows.Window.Icon%2A> pencere simgesini ayarlamak <xref:System.Windows.Window.Title%2A> ve başlığını ayarlamak için dahil olmak üzere çeşitli özellikler sağlar.  
  
 Ayrıca, pencerenin yeniden boyutlandırma modunu, pencere stilini ve masaüstü görev çubuğunda bir düğme olarak görünüp görünmediğini yapılandırarak istemci olmayan alan kenarlığı görünümünü ve davranışını değiştirebilirsiniz.  

<a name="Resize_Mode"></a>
### <a name="resize-mode"></a>Modu Yeniden Boyutlandırma  
 <xref:System.Windows.Window.WindowStyle%2A> Özelliğine bağlı olarak, kullanıcıların pencereyi nasıl (ve varsa) nasıl yeniden boyutlandırabileceğini denetleyebilirsiniz. Pencere stili seçimi, kullanıcının kenarlığını fareyle sürükleyerek pencereyi yeniden boyutlandırıp yeniden boyutlandıramayacağını, **Simge durumuna küçült,** Üst **düzeye çıkar**ve yeniden **boyutlandırma** düğmelerinin istemci olmayan alanda görünüp görünmediğini ve görünürlerse etkin olup olmadıklarını etkiler.  
  
 Aşağıdaki numaralandırma değerlerinden biri olabilecek özelliğini <xref:System.Windows.Window.ResizeMode%2A> ayarlayarak bir pencerenin <xref:System.Windows.ResizeMode> nasıl yeniden boyutlandırılabildiğini yapılandırabilirsiniz:  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <xref:System.Windows.ResizeMode.CanResize>(varsayılan)  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 Olduğu <xref:System.Windows.Window.WindowStyle%2A>gibi, bir pencerenin yeniden boyutlandırma modu nun kullanım ömrü boyunca değişmesi olası [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] değildir, bu da büyük olasılıkla onu biçimlendirmeden ayarladığınız anlamına gelir.  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 Bir pencerenin en üst düzeye çıkarılıp küçültülmediğini, simge <xref:System.Windows.Window.WindowState%2A> durumuna küçültülmediğini veya özelliği inceleyerek geri yüklenip geri yüklenmediğini tespit edebilirsiniz.  
  
<a name="Window_Style"></a>
### <a name="window-style"></a>Pencere Stili  
 Bir pencerenin istemci olmayan alanından açığa çıkan kenarlık çoğu uygulama için uygundur. Ancak, pencere türüne bağlı olarak farklı sınır türlerine ihtiyaç duyulduğu veya hiç kenarlık gerekmeden gerek olmadığı durumlar vardır.  
  
 Bir pencerenin ne tür kenarlık aldığını <xref:System.Windows.Window.WindowStyle%2A> denetlemek için, özelliğini <xref:System.Windows.WindowStyle> aşağıdaki numaralandırma değerlerinden biriyle ayarlarsınız:  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <xref:System.Windows.WindowStyle.SingleBorderWindow>(varsayılan)  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 Bu pencere stillerinin etkisi aşağıdaki şekilde gösterilmiştir:  
  
 ![Pencere kenarlığı stillerinin çizimi.](./media/wpf-windows-overview/window-border-styles.png)  
  
 Biçimlendirme veya kodu kullanarak ayarlayabilirsiniz; <xref:System.Windows.Window.WindowStyle%2A> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir pencerenin ömrü boyunca değişme olasılığı düşük olduğundan, büyük olasılıkla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme kullanarak yapılandıracaktır.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>Dikdörtgen Olmayan Pencere Stili  
 Sahip olmak için izin veren <xref:System.Windows.Window.WindowStyle%2A> sınır stilleri yeterli olmadığı durumlar da vardır. Örneğin, Microsoft Windows Media Player'ın kullandığı gibi dikdörtgen olmayan kenarlıklı bir uygulama oluşturmak isteyebilirsiniz.  
  
 Örneğin, aşağıdaki şekilde gösterilen konuşma balonu penceresini göz önünde bulundurun:  
  
 ![Beni Sürükley in yazan bir konuşma kabarcığı penceresi.](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 Bu tür bir pencere <xref:System.Windows.Window.WindowStyle%2A> <xref:System.Windows.WindowStyle.None>özelliği ayarlayarak ve saydamlık için <xref:System.Windows.Window> özel destek kullanılarak oluşturulabilir.  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 Bu değerler birleşimi, pencerenin tamamen saydam hale getirilmesini sağlar. Bu durumda, pencerenin istemci olmayan alan süslemeleri (Kapat menüsü, Simge durumuna Küçült ve Geri Yükle düğmeleri vb.) kullanılamaz. Sonuç olarak, kendi sağlamak gerekir.  
  
<a name="Task_Bar_Presence"></a>
### <a name="task-bar-presence"></a>Görev Çubuğu Varlığı  

Pencerenin varsayılan görünümü, aşağıdaki şekilde gösterilen gibi bir görev çubuğu düğmesi içerir:

 ![Görev çubuğu düğmesi olan bir pencereyi gösteren ekran görüntüsü.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 Bazı pencere türlerinin ileti kutuları ve iletişim kutuları gibi görev çubuğu düğmesi yoktur (bkz. [İletişim Kutuları Genel Bakış).](dialog-boxes-overview.md) Pencere için görev çubuğu düğmesinin <xref:System.Windows.Window.ShowInTaskbar%2A> özelliği (varsayılan`true` olarak) ayarlayarak gösterip gösterilmediğini denetleyebilirsiniz.  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations"></a>Güvenlikle İlgili Dikkat Edilmesi Gerekenler  
 <xref:System.Windows.Window>anlık `UnmanagedCode` olarak güvenlik izni gerektirir. Yerel makineye yüklenen ve başlatılan uygulamalar için bu, uygulamaya verilen izinler kümesiiçinde yer eder.  
  
 Ancak bu, ClickOnce kullanarak Internet veya Yerel intranet bölgesinden başlatılan uygulamalara verilen izinler kümesinin dışında kalır. Sonuç olarak, kullanıcılar bir ClickOnce güvenlik uyarısı alır ve uygulama için izin kümesini tam güvene yükseltmesi gerekir.  
  
 Ayrıca, XBAP'lar varsayılan olarak pencereleri veya iletişim kutularını gösteremez. Bağımsız uygulama güvenliği yle ilgili bir tartışma için [WPF Güvenlik Stratejisi - Platform Güvenliği'ne](../wpf-security-strategy-platform-security.md)bakın.  
  
<a name="Other_Types_of_Windows"></a>
## <a name="other-types-of-windows"></a>Diğer Windows Türleri  
 <xref:System.Windows.Navigation.NavigationWindow>gezilebilir içeriği barındırmak için tasarlanmış bir penceredir. Daha fazla bilgi için [Gezintiye Genel Bakış'a](navigation-overview.md)bakın).  
  
 İletişim kutuları, bir işlevi tamamlamak için genellikle kullanıcıdan bilgi toplamak için kullanılan pencerelerdir. Örneğin, bir kullanıcı bir dosyayı açmak istediğinde, **Dosyayı Aç** iletişim kutusu genellikle dosya adını kullanıcıdan almak için bir uygulama tarafından görüntülenir. Daha fazla bilgi için İletişim [Kutularına Genel Bakış'a](dialog-boxes-overview.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [İletişim Kutularına Genel Bakış](dialog-boxes-overview.md)
- [WPF Uygulaması Derleme](building-a-wpf-application-wpf.md)
