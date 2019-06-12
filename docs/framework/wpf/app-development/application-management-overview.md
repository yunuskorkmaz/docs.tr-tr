---
title: Uygulama Yönetimine Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
ms.openlocfilehash: c36de23a6a49e684330fc0f47fc46bd86c55e767
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66834076"
---
# <a name="application-management-overview"></a>Uygulama Yönetimine Genel Bakış
Tüm uygulamalar, ortak bir uygulama uygulamayı ve yönetimi için uygulanan işlevselliği sahip eğilimindedir. Bu konuda işlevleri genel bakışını sağlar <xref:System.Windows.Application> oluşturma ve uygulamaları yönetmek için sınıf.  

## <a name="the-application-class"></a>Uygulama sınıfı  
 WPF içinde ortak uygulama kapsamlı işlevsellik içinde kapsüllenir <xref:System.Windows.Application> sınıfı. <xref:System.Windows.Application> Sınıfı aşağıdaki işlevleri içerir:  
  
- İzleme ve uygulama yaşam süresi ile etkileşim kurma.  
  
- Alma ve işleme komut satırı parametreleri.  
  
- Yakalanamayan özel durumları algılama ve yanıtlama.  
  
- Uygulama kapsamı özelliklerini ve kaynaklarını paylaşma.  
  
- Tek başına uygulamalar Windows yönetme.  
  
- İzleme ve gezinti yönetme.  
  
<a name="The_Application_Class"></a>   
## <a name="how-to-perform-common-tasks-using-the-application-class"></a>Uygulama sınıfı kullanarak ortak görevleri gerçekleştirme  
 Tüm ayrıntılarını ilgilenen değilseniz <xref:System.Windows.Application> sınıfı, aşağıdaki tabloda bazı ortak görevler için listeler <xref:System.Windows.Application> ve bunların nasıl yapılacağını. İlgili API ve konuları görüntüleyerek daha fazla bilgi ve örnek kodu bulabilirsiniz.  
  
|Görev|Yaklaşım|  
|----------|--------------|  
|Geçerli uygulamanın temsil eden bir nesne alma|Kullanım <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> özelliği.|  
|Uygulama giriş ekranı ekleme|Bkz: [WPF uygulamasına giriş ekranı ekleme](how-to-add-a-splash-screen-to-a-wpf-application.md).|  
|Uygulama başlatma|Kullanım <xref:System.Windows.Application.Run%2A?displayProperty=nameWithType> yöntemi.|  
|Bir uygulamayı Durdur|Kullanım <xref:System.Windows.Application.Shutdown%2A> yöntemi <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> nesne.|  
|Komut satırından bağımsız değişkenleri Al|Tanıtıcı <xref:System.Windows.Application.Startup?displayProperty=nameWithType> olay ve kullanım <xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType> özelliği. Bir örnek için bkz <xref:System.Windows.Application.Startup?displayProperty=nameWithType> olay.|  
|GET ve set uygulama çıkış kodu|Ayarlama <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType> özelliğinde <xref:System.Windows.Application.Exit?displayProperty=nameWithType> olay işleyicisi veya çağrı <xref:System.Windows.Application.Shutdown%2A> yöntemi ve bir tamsayı geçirin.|  
|Algılama ve yanıtlama işlenmeyen özel durumlar|Tanıtıcı <xref:System.Windows.Application.DispatcherUnhandledException> olay.|  
|Alma ve uygulama kapsamı kaynak ayarlama|Kullanım <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> özelliği.|  
|Bir uygulama kapsamı kaynak sözlüğü kullanma|Bkz: [bir uygulama kapsamı kaynak sözlüğü kullanma](how-to-use-an-application-scope-resource-dictionary.md).|  
|Alma ve uygulama kapsamlı özelliklerini ayarlama|Kullanım <xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType> özelliği.|  
|Uygulama durumunu Kaydet ve Al|Bkz: [koruma ve uygulama oturumları arasında uygulama kapsamı özelliklerini geri yükleme](persist-and-restore-application-scope-properties.md).|  
|Kod dışı veri dosyaları, kaynak dosyaları, içerik dosyalarını ve kaynak site dosyaları dahil olmak üzere yönetin.|Bkz: [WPF Uygulama kaynağı, içerik ve veri dosyalarını](wpf-application-resource-content-and-data-files.md).|  
|Windows'da tek başına uygulamaları yönetme|Bkz: [WPF Windows genel bakış](wpf-windows-overview.md).|  
|İzleme ve gezinti yönetme|Bkz: [gezintiye genel bakış](navigation-overview.md).|  
  
<a name="The_Application_Definition"></a>   
## <a name="the-application-definition"></a>Uygulama tanımı  
 İşlevselliğini kullanmaya <xref:System.Windows.Application> sınıfı, bir uygulama tanımı uygulamalıdır. Bir WPF uygulaması tanımı, türetilen sınıftır <xref:System.Windows.Application> ve özel bir MSBuild ayarı ile yapılandırılır.  

### <a name="implementing-an-application-definition"></a>Uygulama tanımı uygulama  
 Tipik bir WPF uygulaması tanımı, biçimlendirme ve arka plan kod hem kullanılarak uygulanır. Bu, uygulama özellikleri, kaynakları bildirimli olarak ve olayları işleme ve uygulamaya özgü davranış gerideki kod uygulama çalışırken olayları kaydetme biçimlendirme kullanmanıza olanak sağlar.  
  
 Aşağıdaki örnek, biçimlendirme hem de arka plan kod kullanarak bir uygulama tanımı uygulamak gösterilmektedir:  
  
 [!code-xaml[ApplicationSnippets#ApplicationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]  
  
 [!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
 [!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]  
  
 İşaretleme dosyasının ve birlikte çalışması için arka plan kod dosyasında, aşağıdaki izin vermek için yapılması gerekir:  
  
- Biçimlendirme içinde `Application` öğesi içermelidir `x:Class` özniteliği. Ne zaman uygulama oluşturulduğuna göre varlığını `x:Class` işaretlemede dosyası oluşturmak MSBuild neden olur. bir `partial` türetilen sınıf <xref:System.Windows.Application> ve tarafından belirtilen ada sahip `x:Class` özniteliği. Bu XAML şema için bir XML ad alanı bildirimi eklenmesini gerektirir (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`).
  
- Arka plan, kod sınıfı olmalıdır bir `partial` sınıfı tarafından belirtilen aynı ada sahip `x:Class` öznitelik, biçimlendirmede ve öğesinden türetilmelidir <xref:System.Windows.Application>. Bu arka plan kod dosyası ile ilişkili olmasını sağlar `partial` uygulama oluşturulduğunda işaretleme dosyasının için oluşturulan sınıf (bkz [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md)).  
  
> [!NOTE]
>  Yeni bir WPF uygulaması veya Visual Studio kullanarak WPF tarayıcı uygulaması projesi oluşturduğunuzda, uygulama tanımı varsayılan olarak dahil edilir ve biçimlendirme hem de arka plan kod kullanılarak tanımlanır.  
  
 Bu kod, bir uygulama tanımı uygulamak için gereken en düşük gereksinimdir. Ancak, ek bir MSBuild yapılandırma oluşturmak ve uygulamayı çalıştırmadan önce uygulama tanımına yapılması gerekir.  
  
### <a name="configuring-the-application-definition-for-msbuild"></a>MSBuild için uygulama tanımını yapılandırma  
 Çalıştırılmadan önce tek başına uygulamalar ve XAML tarayıcı uygulamaları (XBAP) belirli bir düzeyde altyapısının uygulaması gerektirir. Bu altyapı en önemli parçası giriş noktasıdır. Bir kullanıcı tarafından bir uygulama başlatıldığında, işletim sistemi uygulamaları başlatma için iyi bilinen bir işlev, giriş noktası çağırır.  
  
 Geleneksel olarak, geliştiriciler kendileri için teknolojisine bağlı olarak, bazılarını veya tümünü bu kod yazmak gerekli sahip. Uygulama tanımınız'ın işaretleme dosyasının bir MSBuild yapılandırıldığında ancak WPF Bu kod sizin için oluşturur `ApplicationDefinition` aşağıdaki MSBuild proje dosyasında gösterildiği gibi öğe:  
  
```xml  
<Project   
  DefaultTargets="Build"  
                        xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  ...  
  <ApplicationDefinition Include="App.xaml" />  
  <Compile Include="App.xaml.cs" />  
  ...  
</Project>  
```  
  
 Arka plan kod dosyası kod içerdiği için bir MSBuild işaretlenmiş `Compile` öğesi, olarak normal bir durumdur.  
  
 Uygulama tanımı biçimlendirme ve arka plan kod dosyaları için bu MSBuild yapılandırmalarını uygulama aşağıdaki gibi bir kod oluşturmak MSBuild neden olur:  
  
 [!code-csharp[auto-generated-code](~/samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs)]
 [!code-vb[auto-generated-code](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb)]  
  
 Giriş noktası yöntemi içeren ek altyapı kod ile uygulama tanımının sonuç kodunu artırmaktadır `Main`. <xref:System.STAThreadAttribute> Özniteliği uygulandığı `Main` WPF uygulaması için ana kullanıcı Arabirimi iş parçacığı WPF uygulamaları için gerekli olan bir STA iş parçacığı olduğunu belirtmek için yöntemi. Çağrıldığında, `Main` yeni bir örneğini oluşturur `App` çağırmadan önce `InitializeComponent` olayları kaydedin ve bu özellikleri ayarlamak için yöntemi, biçimlendirme içinde uygulanır. Çünkü `InitializeComponent` oluşturulur, açıkça çağırmanız gerekmez `InitializeComponent` yaptığınız gibi bir uygulama tanımından <xref:System.Windows.Controls.Page> ve <xref:System.Windows.Window> uygulamaları. Son olarak, <xref:System.Windows.Application.Run%2A> yöntemi, uygulamayı başlatmak için çağrılır.  
  
<a name="Getting_the_Current_Application"></a>   
## <a name="getting-the-current-application"></a>Geçerli uygulamanın başlama  
 Çünkü işlevselliğini <xref:System.Windows.Application> sınıfı bir uygulama arasında paylaşılan, yalnızca bir örneği olabilir <xref:System.Windows.Application> başına sınıfı <xref:System.AppDomain>. Bunu zorlamak için <xref:System.Windows.Application> sınıfı bir singleton sınıfı uygulanır (bkz [C# uygulama tekil](https://go.microsoft.com/fwlink/?LinkId=100567)), tek bir örneğini oluşturur ve sunar ile erişimi paylaşılan `static` <xref:System.Windows.Application.Current%2A> özellik.  
  
 Aşağıdaki kod, bir başvuru almak gösterilmektedir <xref:System.Windows.Application> geçerli nesne <xref:System.AppDomain>.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]  
  
 <xref:System.Windows.Application.Current%2A> örneğine bir başvuru döndürür <xref:System.Windows.Application> sınıfı. Bir başvuru istiyorsanız, <xref:System.Windows.Application> türetilmiş sınıf değerini cast gerekir <xref:System.Windows.Application.Current%2A> özelliği, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]  
  
 Değerini inceleyebilirsiniz <xref:System.Windows.Application.Current%2A> ömrünü herhangi bir noktada bir <xref:System.Windows.Application> nesne. Ancak, dikkatli olmanız gerekir. Sonra <xref:System.Windows.Application> sınıf örneği, bir dönemde durumunu <xref:System.Windows.Application> nesnesi tutarsız. Bu süre boyunca <xref:System.Windows.Application> uygulama altyapısı oluşturma, özellikleri ayarlama ve olayları kaydetme gibi tarafından kodunuzu çalıştırmak için gereken çeşitli başlatma görevleri gerçekleştirme. Kullanmayı denerseniz <xref:System.Windows.Application> nesne bu dönemde kodunuzu olabilir beklenmeyen sonuçlara, özellikle çeşitli bağımlı olması durumunda <xref:System.Windows.Application> ayarlanan özellikler.  
  
 Zaman <xref:System.Windows.Application> başlatma işini tamamlayıncaya ömrü gerçekten başlar.  
  
<a name="Application_Lifetime"></a>   
## <a name="application-lifetime"></a>Uygulama ömrü  
 WPF uygulaması ömrünü tarafından gerçekleştirilen çeşitli olayları tarafından işaretlenen <xref:System.Windows.Application> uygulamanızın ne zaman başlayıp, size bildirmek için etkin ve devre dışı ve kapatıldı.  

<a name="Splash_Screen"></a>   
### <a name="splash-screen"></a>Giriş Ekranı  
 .NET Framework 3.5 SP1'de başlayarak, bir başlangıç penceresinde, kullanılacak bir görüntü belirtebilirsiniz veya *giriş ekranı*. <xref:System.Windows.SplashScreen> Sınıfı, uygulama yüklenirken bir başlangıç penceresini görüntülemek kolaylaştırır. <xref:System.Windows.SplashScreen> Penceresi oluşturulur ve önce gösterilen <xref:System.Windows.Application.Run%2A> çağrılır. Daha fazla bilgi için [uygulama başlangıç zamanı](../advanced/application-startup-time.md) ve [WPF uygulamasına giriş ekranı ekleme](how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
<a name="Starting_an_Application"></a>   
### <a name="starting-an-application"></a>Uygulama başlatma  
 Sonra <xref:System.Windows.Application.Run%2A> çağrılır ve uygulama başlatılır, uygulama çalıştırmak hazır olur. Şu zaman miktarlara <xref:System.Windows.Application.Startup> olayı oluşturulur:  
  
[!code-csharp[Startup-event](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs?range=3-11,31-33)]
[!code-vb[Startup-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb?range=5-11,30-32)]
  
 Bu noktada, bir uygulamanın yaşam yapmak için en yaygın bir uygulamanın UI göstermesi için şeydir.  
  
<a name="Showing_a_User_Interface"></a>
### <a name="showing-a-user-interface"></a>Bir kullanıcı arabirimi gösterme  
 Çoğu tek başına Windows uygulamalarını bir <xref:System.Windows.Window> çalışmaya başladığında çalışıyor. <xref:System.Windows.Application.Startup> Olay işleyicisi, aşağıdaki kodda gösterildiği gibi bunu yapabilirsiniz, tek bir konumda olduğundan.  
  
 [!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]  
  
 [!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
 [!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]  
  
> [!NOTE]
>  İlk <xref:System.Windows.Window> uygulama içinde tek başına bir örneği için varsayılan olarak ana uygulama penceresini olur. Bu <xref:System.Windows.Window> nesne tarafından başvurulan <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> özelliği. Değerini <xref:System.Windows.Application.MainWindow%2A> özelliği değiştirilebilir programlı olarak farklı bir pencere, ilk örneği <xref:System.Windows.Window> ana pencereyi olmalıdır.  
  
 Bir XBAP ilk kez başlatıldığında, büyük olasılıkla gider bir <xref:System.Windows.Controls.Page>. Bu aşağıdaki kod gösterilmektedir.  
  
 [!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]  
  
 [!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
 [!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]  
  
 İşliyorsanız <xref:System.Windows.Application.Startup> yalnızca açmak için bir <xref:System.Windows.Window> veya gidin bir <xref:System.Windows.Controls.Page>, ayarlayabileceğiniz `StartupUri` işaretlemede yerine özniteliği.  
  
 Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Application.StartupUri%2A> açmak için bir tek başına uygulamasından bir <xref:System.Windows.Window>.  
  
 [!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]  
  
 Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Application.StartupUri%2A> gitmek için bir XBAP gelen bir <xref:System.Windows.Controls.Page>.  
  
 [!code-xaml[PageSnippets#XBAPStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]  
  
 Bu işaretleme, önceki kod bir pencerede açmak için aynı etkiye sahiptir.  
  
> [!NOTE]
>  Gezinti hakkında daha fazla bilgi için bkz. [gezintiye genel bakış](navigation-overview.md).  
  
 İşlemeniz gereken <xref:System.Windows.Application.Startup> olayı açmak için bir <xref:System.Windows.Window> varsayılan olmayan bir Oluşturucu kullanarak örneği oluşturmak ihtiyacınız özelliklerini ayarlayın veya onu göstermeden önce olaylara abone olması veya herhangi bir komut satırı bağımsız değişkeni işlemek için ihtiyacınız varsa, uygulama başlatıldığında sağlandı.  
  
<a name="Processing_Command_Line_Arguments"></a>   
### <a name="processing-command-line-arguments"></a>Komut satırı bağımsız değişkenleri işleme  
 Bir komut istemi veya masaüstü, Windows tek başına uygulamalar başlatılabilir. Her iki durumda da, komut satırı bağımsız değişkenleri uygulamaya geçirilebilir. Aşağıdaki örnek, tek bir komut satırı bağımsız değişkeniyle başlatılır bir uygulama gösterir. "/ StartMinimized":  
  
 `wpfapplication.exe /StartMinimized`  
  
 Uygulama başlatma sırasında WPF işletim sisteminden komut satırı bağımsız değişkenleri alır ve bunları geçirmeden <xref:System.Windows.Application.Startup> aracılığıyla olay işleyicisi <xref:System.Windows.StartupEventArgs.Args%2A> özelliği <xref:System.Windows.StartupEventArgs> parametresi. Alabilir ve aşağıdaki gibi bir kod kullanarak komut satırı bağımsız değişkenleri depolayın.  
  
 [!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]  
  
 [!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
 [!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]  
  
 Kod tutamaçları <xref:System.Windows.Application.Startup> denetlemek için olup olmadığını **/StartMinimized** komut satırı bağımsız değişkeni belirtildi; bu durumda, ana penceresi açılır. bir <xref:System.Windows.WindowState> , <xref:System.Windows.WindowState.Minimized>. Dikkat edin çünkü <xref:System.Windows.Window.WindowState%2A> özelliği ayarlanmalıdır programlı olarak ana <xref:System.Windows.Window> kodda açıkça açılması gerekir.  
  
 XBAP'ler almak ve ClickOnce dağıtımını kullanarak tasarlandıkça olduğundan işlem komut satırı bağımsız değişkenleri (bkz [bir WPF uygulamasını dağıtma](deploying-a-wpf-application-wpf.md)). Ancak, almak ve bunları başlatmak için kullanılan URL sorgu dizesi parametreleri işlem.  
  
<a name="Application_Activation_and_Deactivation"></a>   
### <a name="application-activation-and-deactivation"></a>Uygulama etkinleştirme ve devre dışı bırakma  
 Windows uygulamaları arasında geçiş yapmak kullanıcıların sağlar. En yaygın yolu, ALT + SEKME tuş bileşimini kullanmaktır. Görünür bir varsa uygulamanın yalnızca olarak değiştirilebilir <xref:System.Windows.Window> , bir kullanıcı seçebilirsiniz. Şu anda seçili <xref:System.Windows.Window> olduğu *etkin pencere* (olarak da bilinen *ön plan penceresi*) ve <xref:System.Windows.Window> , kullanıcı girişini alır. Uygulama etkin pencere ile *etkin uygulama* (veya *ön plan uygulama*). Bir uygulamayı uygulamanın aşağıdaki durumlarda olur:  
  
- Başlatılır ve gösteren bir <xref:System.Windows.Window>.  
  
- Bir kullanıcı başka bir uygulamadan seçerek anahtarları bir <xref:System.Windows.Window> uygulama.  
  
 Bir uygulama tarafından işleme etkin olduğunda algılayabilir <xref:System.Windows.Application.Activated?displayProperty=nameWithType> olay.  
  
 Benzer şekilde, bir uygulama aşağıdaki durumlarda etkin hale gelebilir:  
  
- Bir kullanıcı başka bir uygulamaya geçerli olandan geçer.  
  
- Ne zaman uygulama kapanır.  
  
 Bir uygulama işleme tarafından devre dışı olunca algılayabilir <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> olay.  
  
 Aşağıdaki kod nasıl işleneceğini gösterir <xref:System.Windows.Application.Activated> ve <xref:System.Windows.Application.Deactivated> olayları uygulama etkin olup olmadığını belirlemek için.  
  
 [!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]  
  
 [!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
 [!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]  
  
 A <xref:System.Windows.Window> de etkin ve devre dışı bırakıldı. Bkz: <xref:System.Windows.Window.Activated?displayProperty=nameWithType> ve <xref:System.Windows.Window.Deactivated?displayProperty=nameWithType> daha fazla bilgi için.  
  
> [!NOTE]
>  Ne <xref:System.Windows.Application.Activated?displayProperty=nameWithType> ya da <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> XBAP'ler için tetiklenir.  
  
<a name="Application_Shutdown"></a>   
### <a name="application-shutdown"></a>Uygulama kapatma  
 Bilgisayarı, aşağıdaki nedenlerle ortaya çıkabilir, bir uygulamanın ömrü sona erer:  
  
- Bir kullanıcı kapatır her <xref:System.Windows.Window>.  
  
- Bir kullanıcının ana kapattığı <xref:System.Windows.Window>.  
  
- Bir kullanıcı oturumu kapatmadan veya kapatılıyor Windows oturumu sona erer.  
  
- Bir uygulamaya özel durumu karşılandığından.  
  
 Uygulama kapatma yönetmenize yardımcı olmak için <xref:System.Windows.Application> sağlar <xref:System.Windows.Application.Shutdown%2A> yöntemi <xref:System.Windows.Application.ShutdownMode%2A> özelliği ve <xref:System.Windows.Application.SessionEnding> ve <xref:System.Windows.Application.Exit> olayları.  
  
> [!NOTE]
>  <xref:System.Windows.Application.Shutdown%2A> yalnızca sahip uygulamalardan çağrılabilen <xref:System.Security.Permissions.UIPermission>. Tek başına WPF uygulamaları her zaman bu izne sahip. Bununla birlikte Internet bölgesi kısmi güven güvenliği korumalı alanında çalışan XBAP'ler yoktur.  
  
#### <a name="shutdown-mode"></a>Kapatma  
 Çoğu uygulama, tüm windows kapatıldığı veya ana penceresi kapatıldığında aşağı kapatın. Bazı durumlarda, ancak diğer uygulamaya özgü koşulları ne zaman bir uygulama kapanırken belirleyebilirsiniz. Koşullar altında uygulamanızın kapatma ayarlayarak belirtebilirsiniz <xref:System.Windows.Application.ShutdownMode%2A> aşağıdakilerden biriyle <xref:System.Windows.ShutdownMode> sabit listesi değerleri:  
  
- <xref:System.Windows.ShutdownMode.OnLastWindowClose>  
  
- <xref:System.Windows.ShutdownMode.OnMainWindowClose>  
  
- <xref:System.Windows.ShutdownMode.OnExplicitShutdown>  
  
 Varsayılan değer olan <xref:System.Windows.Application.ShutdownMode%2A> olduğu <xref:System.Windows.ShutdownMode.OnLastWindowClose>, uygulamanın son penceresinde kullanıcı tarafından kapatıldığında, bir uygulama otomatik olarak kapanır anlamına gelir. Ana pencere kapatıldığında, uygulamanızın kapatılmalıdır, ayarlarsanız ancak WPF otomatik olarak yapar <xref:System.Windows.Application.ShutdownMode%2A> için <xref:System.Windows.ShutdownMode.OnMainWindowClose>. Bu, aşağıdaki örnekte gösterilir.  
  
 [!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]  
  
 Uygulamaya özgü kapatma koşullar varsa, ayarladığınız <xref:System.Windows.Application.ShutdownMode%2A> için <xref:System.Windows.ShutdownMode.OnExplicitShutdown>. Bu durumda, onu açıkça çağırarak bir uygulamayı kapatmak için sizin sorumluluğunuzdur <xref:System.Windows.Application.Shutdown%2A> yöntemi; Aksi halde, uygulamanız tüm pencereler kapatılırsa bile çalışmaya devam edecek. Unutmayın <xref:System.Windows.Application.Shutdown%2A> örtük olarak çağırılamaz zaman <xref:System.Windows.Application.ShutdownMode%2A> ya da <xref:System.Windows.ShutdownMode.OnLastWindowClose> veya <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
> [!NOTE]
>  <xref:System.Windows.Application.ShutdownMode%2A> bir XBAP ayarlanabilir, ancak göz ardı edilir; Bunu bir tarayıcıda veya XBAP barındıran tarayıcı kapatıldığında çıkıldığında, bir XBAP her zaman kapatılır. Daha fazla bilgi için [gezintiye genel bakış](navigation-overview.md).  
  
#### <a name="session-ending"></a>Oturum sonlandırılıyor  
 Tarafından açıklanan kapatma koşulları <xref:System.Windows.Application.ShutdownMode%2A> özelliği uygulamaya özeldir. Bazı durumlarda, yine de bir uygulama sonucu olarak bir dış koşul kapatılabilir. Bir kullanıcı Windows oturumu şu eylemleri sona erdiğinde en yaygın dış durum meydana gelir:  
  
- Oturum kapatma  
  
- Kapatılıyor  
  
- Yeniden başlatma  
  
- Hazırda bekleme  
  
 Windows oturumu sona erdiğinde algılamak için işleyebilirsiniz <xref:System.Windows.Application.SessionEnding> aşağıdaki örnekte gösterildiği gibi olay.  
  
 [!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]  
  
 [!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
 [!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]  
  
 Bu örnekte, kodu inceler <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> nasıl Windows oturumu sona belirlemek için özellik. Kullanıcıya bir onay iletisi göstermek için bu değeri kullanır. Kullanıcı oturumunu sona erdirmek için istemezse, kod ayarlar <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> için `true` bitiş'den Windows oturumu önlemek için.  
  
> [!NOTE]
>  <xref:System.Windows.Application.SessionEnding> XBAP'ler için oluşmaz.

#### <a name="exit"></a>Çık  
 Bir uygulama kapatıldığında, kalıcı bir uygulama durumu gibi son işlemleri gerçekleştirmek gerekebilir. Bu durumlarda, işleyebilirsiniz <xref:System.Windows.Application.Exit> olayı olarak `App_Exit` aşağıdaki örnekte olay işleyicisi yok. Olay işleyicisinde olarak tanımlanan *App.xaml* dosya. Uygulaması vurgulanan *App.xaml.cs* ve *Application.xaml.vb* dosyaları.
  
[!code-xaml[Defining-the-Exit-event-handler](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]  
  
 [!code-csharp[Handling-the-Exit-event](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=42-55)]
 [!code-vb[Handling-the-Exit-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=34-45)]  
  
 Tam bir örnek için bkz. [kalan ve geri yükleme uygulama kapsamı özellikleri arasında uygulama oturumları](persist-and-restore-application-scope-properties.md).  
  
 <xref:System.Windows.Application.Exit> tek başına uygulamalar ve XBAP'ler tarafından işlenebilir. XBAP'ler için <xref:System.Windows.Application.Exit> , aşağıdaki koşullarda ortaya çıkar:  
  
- Sayfadan bir XBAP çıkıldığında.  
  
- İçinde [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)], XBAP barındırma sekmesini kapalı olduğunda.  
  
- Tarayıcı kapatıldığında.  
  
#### <a name="exit-code"></a>Çıkış kodu  
 Uygulamalar genellikle bir kullanıcı isteğine yanıt olarak işletim sistemi tarafından başlatılabilir. Ancak, bir uygulama belirli bir görevi gerçekleştirmek için başka bir uygulama tarafından başlatılabilir. Başlatılan uygulamalar kapatıldığında başlatılırken uygulama altında başlatılan uygulama kapatma koşul bilmek isteyebilir. Bu durumda, Windows uygulamaların kapatma sırasında bir uygulama çıkış kodu iade izin verir. Varsayılan olarak, WPF uygulamaları bir çıkış kodu 0 değerini döndürür.  
  
> [!NOTE]
>  Visual Studio'dan hata ayıklaması yaparken uygulama çıkış kodu görüntülenen **çıkış** uygulama, aşağıdaki gibi görünen bir ileti kapatır zaman penceresi:  
>   
>  `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`  
>   
>  Açtığınız **çıkış** tıklayarak penceresi **çıkış** üzerinde **görünümü** menüsü.  
  
 Çıkış kodu değiştirmek için çağırabilirsiniz <xref:System.Windows.Application.Shutdown%28System.Int32%29> çıkış kodu olacak tamsayı bağımsız değişken kabul eden aşırı yükleme:  
  
 [!code-csharp[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
 [!code-vb[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]  
  
 Çıkış kodu değerini algılamak ve değiştirmesini işleyerek <xref:System.Windows.Application.Exit> olay. <xref:System.Windows.Application.Exit> Olay işleyicisine geçirilen bir <xref:System.Windows.ExitEventArgs> çıkış kodu ile erişimi sağlayan <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> özelliği. Daha fazla bilgi için bkz. <xref:System.Windows.Application.Exit>.  
  
> [!NOTE]
>  Çıkış kodu, hem tek başına uygulamalar hem de XBAP'ler ayarlayabilirsiniz. Ancak, çıkış kodu değerini XBAP'ler için göz ardı edilir.  
  
<a name="Unhandled_Exceptions"></a>   
### <a name="unhandled-exceptions"></a>İşlenmeyen özel durumları  
 Bazen bir uygulama gibi beklenmeyen özel durum oluştuğunda aşağı altında anormal koşullar kapatın. Bu durumda, uygulama algılama ve özel durumu işlemek için kod olmayabilir. Bu özel durum işlenmemiş bir özel durum türüdür; Uygulama kapatılmadan hemen önce aşağıdaki şekilde gösterilen benzer bir bildirim görüntülenir.  
  
 ![İşlenmeyen özel durum bildirimi gösteren ekran görüntüsü.](./media/application-management-overview/unhandled-exception-notification.png)  
  
 Kullanıcı deneyimi açısından daha iyi bir uygulamanın bazı veya tüm aşağıdakileri yaparak bu varsayılan davranışı önlemek:  
  
- Kullanıcı dostu bilgilerini görüntüleme.  
  
- Çalışan bir uygulama tutmak çalışılıyor.  
  
- Ayrıntılı, geliştirici dostu özel durum bilgilerini ve Windows olay günlüğüne kaydetme.  
  
 Bu destek uygulama bağlıdır işlenmeyen özel durumlar, korumakta üzerinde ne olduğu <xref:System.Windows.Application.DispatcherUnhandledException> olayı için oluşturulur.  
  
[!code-xaml[detecting-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]  
  
[!code-csharp[code-to-detect-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs)]
[!code-vb[code-to-detect-unhandled-exceptions](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb)]  
  
 <xref:System.Windows.Application.DispatcherUnhandledException> Olay işleyicisine geçirilen bir <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> durum da dahil olmak üzere işlenmeyen özel durumla ilgili bağlamsal bilgileri içeren bir parametre (<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>). Özel durumu işlemek nasıl belirlemek için bu bilgileri kullanabilirsiniz.  
  
 Ne zaman işleneceğini <xref:System.Windows.Application.DispatcherUnhandledException>, ayarlamalısınız <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType> özelliğini `true`; Aksi takdirde, WPF hala özel durum işlenmemiş olarak değerlendirir ve daha önce açıklanan varsayılan davranışa geri döner. İşlenmeyen bir özel durum oluşturulursa ve her iki <xref:System.Windows.Application.DispatcherUnhandledException> olay işlenmez veya olay işlenir ve <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> ayarlanır `false`, uygulamayı hemen kapanıyorsa öyle kapanır. Ayrıca, başka hiçbir <xref:System.Windows.Application> olayları ortaya çıkar. Sonuç olarak, işlemeniz gereken <xref:System.Windows.Application.DispatcherUnhandledException> uygulamanızın uygulama kapatılmadan önce çalışmalıdır kodu varsa.  
  
 İşlenmeyen bir özel durum sonucu olarak bir uygulama kapanabilir olsa da, bir uygulama genellikle bir kullanıcı isteğine yanıt olarak sonraki bölümde açıklandığı gibi kapanır.  
  
<a name="Application_Lifetime_Events"></a>   
### <a name="application-lifetime-events"></a>Uygulama yaşam süresi olayları  
 Tek başına uygulamalar ve XBAP'ler tam olarak aynı yaşam süresi yok. Aşağıdaki şekilde, bir tek başına uygulama kullanım ömrü içinde anahtar olayları gösterir ve bunlar yükseltilir dizisini gösterir.  
  
 ![Tek başına uygulama &#45; uygulama nesnesi olayları](./media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")  
  
 Benzer şekilde, aşağıdaki şekilde bir XBAP ömrünü anahtar olayları gösterir ve bunlar yükseltilir dizisini gösterir.  
  
 ![XBAP &#45; uygulama nesnesi olayları](./media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Application>
- [WPF Windows'a Genel Bakış](wpf-windows-overview.md)
- [Gezintiye Genel Bakış](navigation-overview.md)
- [WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları](wpf-application-resource-content-and-data-files.md)
- [WPF İçinde URI'leri Paketleme](pack-uris-in-wpf.md)
- [Uygulama modeli: Nasıl Yapılır Konuları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms749013(v=vs.100))
- [Uygulama Geliştirme](index.md)
