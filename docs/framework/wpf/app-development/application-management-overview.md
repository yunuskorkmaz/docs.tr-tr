---
title: Uygulama Yönetimine Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
ms.openlocfilehash: d0e3ecbfd42d14ea468adf8a99be0f525c5eb39d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040967"
---
# <a name="application-management-overview"></a>Uygulama Yönetimine Genel Bakış

Tüm uygulamalar, uygulama uygulaması ve yönetimi için geçerli olan ortak bir işlev kümesini paylaşma eğilimindedir. Bu konu, <xref:System.Windows.Application> uygulama oluşturma ve yönetme sınıfındaki işlevlere genel bir bakış sağlar.

## <a name="the-application-class"></a>Uygulama sınıfı

WPF 'de, ortak uygulama kapsamlı işlevler <xref:System.Windows.Application> sınıfında kapsüllenir. <xref:System.Windows.Application> Sınıfı aşağıdaki işlevleri içerir:

- Uygulama ömrü ile izleme ve etkileşim kurma.

- Komut satırı parametrelerini alma ve işleme.

- İşlenmeyen özel durumları algılama ve yanıtlama.

- Uygulama kapsamı özelliklerini ve kaynaklarını paylaşma.

- Windows 'ı tek başına uygulamalarda yönetme.

- Gezintiyi izleme ve yönetme.

<a name="The_Application_Class"></a>

## <a name="how-to-perform-common-tasks-using-the-application-class"></a>Uygulama sınıfını kullanarak ortak görevleri gerçekleştirme

<xref:System.Windows.Application> Sınıfın tüm ayrıntılarını ilgilenmiyorsanız aşağıdaki tabloda, için <xref:System.Windows.Application> bazı ortak görevler ve bunların nasıl yapılacağı listelenmektedir. İlgili API ve konuları görüntüleyerek daha fazla bilgi ve örnek kod bulabilirsiniz.

|Görev|Yaklaşım|
|----------|--------------|
|Geçerli uygulamayı temsil eden bir nesne al|<xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> Özelliğini kullanın.|
|Uygulamaya başlangıç ekranı ekleme|Bkz. [WPF uygulamasına giriş ekranı ekleme](how-to-add-a-splash-screen-to-a-wpf-application.md).|
|Uygulama başlatma|<xref:System.Windows.Application.Run%2A?displayProperty=nameWithType> Yöntemini kullanın.|
|Bir uygulamayı durdur|<xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> Nesnesinin <xref:System.Windows.Application.Shutdown%2A> yöntemini kullanın.|
|Komut satırından bağımsız değişkenleri al|Olayı işleyin ve <xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType> özelliğini kullanın. <xref:System.Windows.Application.Startup?displayProperty=nameWithType> Bir örnek için, <xref:System.Windows.Application.Startup?displayProperty=nameWithType> olayına bakın.|
|Uygulama çıkış kodunu al ve ayarla|Olayişleyicisindeki<xref:System.Windows.Application.Exit?displayProperty=nameWithType>özelliğiayarlayınveya <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType> yöntemiçağırınvebir<xref:System.Windows.Application.Shutdown%2A> tamsayı olarak geçirin.|
|İşlenmeyen özel durumları Algıla ve Yanıtla|<xref:System.Windows.Application.DispatcherUnhandledException> Olayı işleyin.|
|Uygulama kapsamındaki kaynakları edinme ve ayarlama|<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> Özelliğini kullanın.|
|Uygulama kapsamı kaynak sözlüğü kullanma|Bkz. [uygulama kapsamı kaynak sözlüğü kullanma](how-to-use-an-application-scope-resource-dictionary.md).|
|Uygulama kapsamlı özellikleri al ve ayarla|<xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType> Özelliğini kullanın.|
|Uygulamanın durumunu al ve Kaydet|Bkz. uygulama [oturumları arasında uygulama kapsamı özelliklerini kalıcı ve geri yükleme](persist-and-restore-application-scope-properties.md).|
|Kaynak dosyaları, içerik dosyaları ve kaynak yeri dosyaları dahil olmak üzere kod olmayan veri dosyalarını yönetin.|Bkz. [WPF uygulama kaynağı, içerik ve veri dosyaları](wpf-application-resource-content-and-data-files.md).|
|Tek başına uygulamalardaki pencereleri yönetme|Bkz. [WPF Windows 'A genel bakış](wpf-windows-overview.md).|
|Gezintiyi izleme ve yönetme|Bkz. [gezintiye genel bakış](navigation-overview.md).|

<a name="The_Application_Definition"></a>

## <a name="the-application-definition"></a>Uygulama tanımı

<xref:System.Windows.Application> Sınıfının işlevselliğini kullanmak için, bir uygulama tanımı uygulamanız gerekir. WPF uygulama tanımı, ' den <xref:System.Windows.Application> türetilen ve özel bir MSBuild ayarıyla yapılandırılan bir sınıftır.

### <a name="implementing-an-application-definition"></a>Uygulama tanımı uygulama

Tipik bir WPF uygulama tanımı hem biçimlendirme hem de arka plan kodu kullanılarak uygulanır. Bu, uygulama özelliklerini, kaynakları ve olayları işlemeyi ve olayları işlerken ve arka plan kod içinde uygulamaya özgü davranışı uygulamayı bir arada ayarlamak için biçimlendirme kullanmanıza olanak sağlar.

Aşağıdaki örnek, hem biçimlendirme hem de arka plan kodu kullanarak bir uygulama tanımının nasıl uygulanacağını gösterir:

[!code-xaml[ApplicationSnippets#ApplicationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]

[!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
[!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]

Biçimlendirme dosyası ve arka plan kod dosyasının birlikte çalışmasına izin vermek için aşağıdakiler olması gerekir:

- Biçimlendirme ' de, `Application` öğesi `x:Class` özniteliğini içermelidir. Uygulama oluşturulduğunda, biçimlendirme `x:Class` dosyasında bulunması MSBuild 'in `x:Class` özniteliği tarafından belirtilen adı ve ' dan <xref:System.Windows.Application> türetilen bir `partial` sınıf oluşturmasına neden olur. Bu, XAML şeması (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`) için bir XML ad alanı bildiriminin eklenmesini gerektirir.

- Arka plan kod içinde, sınıf, `partial` <xref:System.Windows.Application>biçimlendirme içindeki `x:Class` özniteliği tarafından belirtilen aynı ada sahip bir sınıf olmalıdır ve türevi olmalıdır. Bu, arka plan kod dosyasının, uygulama oluşturulduğunda biçimlendirme dosyası için `partial` oluşturulan sınıfla ilişkilendirilmesini sağlar (bkz. [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md)).

> [!NOTE]
> Visual Studio kullanarak yeni bir WPF uygulama projesi veya WPF tarayıcı uygulaması projesi oluşturduğunuzda, varsayılan olarak bir uygulama tanımı dahil edilir ve hem biçimlendirme hem de arka plan kodu kullanılarak tanımlanır.

Bu kod, uygulama tanımı uygulamak için gereken en düşük gereksinimdir. Ancak, uygulamayı oluşturmadan ve çalıştırmadan önce uygulama tanımına ek bir MSBuild yapılandırması yapılması gerekir.

### <a name="configuring-the-application-definition-for-msbuild"></a>MSBuild için uygulama tanımını yapılandırma

Tek başına uygulamalar ve XAML tarayıcı uygulamaları (XBAP 'ler), çalıştırılmadan önce belirli bir altyapı düzeyinin uygulanmasını gerektirir. Bu altyapının en önemli bölümü giriş noktasıdır. Bir uygulama bir kullanıcı tarafından başlatıldığında, işletim sistemi, uygulamaları başlatmak için iyi bilinen bir işlev olan giriş noktasını çağırır.

Geleneksel olarak, geliştiricilerin teknolojiye bağlı olarak bu kodun bir kısmını veya tamamını yazması gerekir. Ancak WPF, aşağıdaki MSBuild proje dosyasında gösterildiği gibi, uygulama tanımınızın işaretleme dosyası bir MSBuild `ApplicationDefinition` öğesi olarak yapılandırıldığında, bu kodu sizin için oluşturur:

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

Arka plan kod dosyası kod içerdiğinden, normal olarak bir MSBuild `Compile` öğesi olarak işaretlenir.

Bu MSBuild yapılandırmalarının, bir uygulama tanımının biçimlendirme ve arka plan kod dosyalarına uygulaması, MSBuild 'in aşağıdakine benzer bir kod oluşturmasına neden olur:

[!code-csharp[auto-generated-code](~/samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs)]
[!code-vb[auto-generated-code](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb)]

Elde edilen kod, uygulama tanımınızı, giriş noktası yöntemini `Main`içeren ek altyapı kodu ile genişlettiğini. Özniteliği, WPF uygulaması için ana `Main` UI iş parçacığının WPF uygulamaları için gerekli olan bir STA iş parçacığı olduğunu göstermek üzere yöntemine uygulanır. <xref:System.STAThreadAttribute> Çağrıldığında, `Main` olayları kaydetmek ve biçimlendirmede uygulanan özellikleri `App` ayarlamak için `InitializeComponent` yöntemini çağırmadan önce yeni bir örneğini oluşturur. Sizin için oluşturulduğundan, `InitializeComponent` <xref:System.Windows.Controls.Page> ve<xref:System.Windows.Window> uygulamaları gibi bir uygulama tanımından açıkça çağrı yapmanız gerekmez. `InitializeComponent` Son olarak, <xref:System.Windows.Application.Run%2A> yöntemi uygulamayı başlatmak için çağırılır.

<a name="Getting_the_Current_Application"></a>

## <a name="getting-the-current-application"></a>Geçerli uygulama alınıyor

<xref:System.Windows.Application> Sınıfın işlevselliği bir uygulama genelinde paylaşıldığından, <xref:System.Windows.Application> sınıfının başına <xref:System.AppDomain>yalnızca bir örneği olabilir. Bunu zorlamak için, <xref:System.Windows.Application> sınıfı tek bir sınıf olarak uygulanır (bkz [ C# ](https://go.microsoft.com/fwlink/?LinkId=100567). tek bir örneğini oluşturur) ve <xref:System.Windows.Application.Current%2A> özelliği ile `static` buna paylaşılan erişim sağlar.

Aşağıdaki kod, geçerli <xref:System.Windows.Application> <xref:System.AppDomain>için nesnesine nasıl bir başvuru alınacağını göstermektedir.

[!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
[!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]

<xref:System.Windows.Application.Current%2A><xref:System.Windows.Application> sınıfının bir örneğine bir başvuru döndürür. <xref:System.Windows.Application> Türetilmiş sınıfınız için bir başvuru isterseniz, aşağıdaki örnekte gösterildiği gibi <xref:System.Windows.Application.Current%2A> özelliğin değerini atamalısınız.

[!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
[!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]

<xref:System.Windows.Application.Current%2A> Bir<xref:System.Windows.Application> nesnenin kullanım ömrü içinde herhangi bir noktada değerini inceleyebilirsiniz. Ancak dikkatli olmanız gerekir. Sınıf örneği oluşturulduktan sonra, <xref:System.Windows.Application> nesnenin durumunun tutarsız olduğu bir nokta vardır. <xref:System.Windows.Application> Bu süre boyunca, <xref:System.Windows.Application> kodunuzun çalışması için gereken, uygulama altyapısını oluşturma, özellikleri ayarlama ve olayları kaydetme gibi çeşitli başlatma görevlerini gerçekleştiriyor. Bu süre içinde <xref:System.Windows.Application> nesneyi kullanmaya çalışırsanız, özellikle de ayarlanan çeşitli <xref:System.Windows.Application> özelliklere bağımlıysa, kodunuz beklenmedik sonuçlara neden olabilir.

Başlatma <xref:System.Windows.Application> işini tamamladığında, ömrü gerçekten başlar.

<a name="Application_Lifetime"></a>

## <a name="application-lifetime"></a>Uygulama ömrü

Bir WPF uygulamasının ömrü, uygulamanızın başlatıldığı zaman etkinleştirilmiş ve devre dışı bırakılmış ve kapatılmış <xref:System.Windows.Application> olduğunu bilmeniz için tarafından oluşturulan birkaç olay tarafından işaretlenir.

<a name="Splash_Screen"></a>

### <a name="splash-screen"></a>Giriş Ekranı

.NET Framework 3,5 SP1 'den başlayarak, bir başlangıç penceresinde veya *Giriş ekranında*kullanılacak bir görüntü belirtebilirsiniz. Sınıfı <xref:System.Windows.SplashScreen> , uygulamanız yüklenirken bir başlangıç penceresini görüntülemeyi kolaylaştırır. Pencere oluşturulur ve çağrılmadan önce <xref:System.Windows.Application.Run%2A> gösterilir. <xref:System.Windows.SplashScreen> Daha fazla bilgi için bkz. [uygulama başlangıç süresi](../advanced/application-startup-time.md) ve [bir WPF uygulamasına giriş ekranı ekleme](how-to-add-a-splash-screen-to-a-wpf-application.md).

<a name="Starting_an_Application"></a>

### <a name="starting-an-application"></a>Uygulama başlatma

Çağrıldıktan <xref:System.Windows.Application.Run%2A> ve uygulama başlatıldıktan sonra, uygulama çalıştırılmaya hazırdır. Bu, <xref:System.Windows.Application.Startup> olay ortaya çıktığında Şu anda belirlenir:

[!code-csharp[Startup-event](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs?range=3-11,31-33)]
[!code-vb[Startup-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb?range=5-11,30-32)]

Uygulamanın ömrü olan bu noktada, en sık yapılacak şey bir kullanıcı arabirimi göstermedir.

<a name="Showing_a_User_Interface"></a>

### <a name="showing-a-user-interface"></a>Kullanıcı arabirimini gösterme

Tek başına Windows uygulamaları çalışmaya başladıklarında bir <xref:System.Windows.Window> açılır. <xref:System.Windows.Application.Startup> Olay işleyicisi, aşağıdaki kodda gösterildiği gibi bunu yapabileceğiniz bir konumdur.

[!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]

[!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
[!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]

> [!NOTE]
> Tek başına <xref:System.Windows.Window> bir uygulamada örneği oluşturulan ilk, varsayılan olarak ana uygulama penceresi olur. Bu <xref:System.Windows.Window> nesneye <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> özelliği tarafından başvuruluyor. İlk örneği oluşturulmuş <xref:System.Windows.Window> olandan <xref:System.Windows.Application.MainWindow%2A> farklı bir pencere ana pencere olmalıdır özelliğinin değeri program aracılığıyla değiştirilebilir.

Bir XBAP ilk kez başladığında, büyük olasılıkla bir ' a <xref:System.Windows.Controls.Page>gidecektir. Bu, aşağıdaki kodda gösterilmiştir.

[!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]

[!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
[!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]

Yalnızca bir <xref:System.Windows.Window> ' ı açmak veya bir <xref:System.Windows.Controls.Page>öğesine gitmek istiyorsanız, bunun yerine biçimlendirme içindeki `StartupUri` özniteliği ayarlayabilirsiniz. <xref:System.Windows.Application.Startup>

Aşağıdaki örnek, <xref:System.Windows.Application.StartupUri%2A> bir <xref:System.Windows.Window>tek başına uygulamasından öğesini açmak için nasıl kullanacağınızı gösterir.

[!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]

Aşağıdaki örnek, bir XBAP 'den ' <xref:System.Windows.Application.StartupUri%2A> a <xref:System.Windows.Controls.Page>gitmek için nasıl kullanılacağını gösterir.

[!code-xaml[PageSnippets#XBAPStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]

Bu biçimlendirme, bir pencere açmak için önceki kodla aynı etkiye sahiptir.

> [!NOTE]
> Gezinti hakkında daha fazla bilgi için bkz. [gezintiye genel bakış](navigation-overview.md).

Parametresiz bir <xref:System.Windows.Application.Startup> <xref:System.Windows.Window> Oluşturucu kullanarak örneğini oluşturmanız gerekiyorsa veya onu göstermeden önce özelliklerini ayarlamanız veya olaylarına abone olmanız ya da herhangi bir komut satırı bağımsız değişkenini işlemeniz gerekiyorsa, bunu açmak için olayı işlemeniz gerekir Bu, uygulama başlatıldığında sağlanmış.

<a name="Processing_Command_Line_Arguments"></a>

### <a name="processing-command-line-arguments"></a>Komut satırı bağımsız değişkenlerini işleme

Windows 'da tek başına uygulamalar, bir komut isteminden veya masaüstünden başlatılabilir. Her iki durumda da, komut satırı bağımsız değişkenleri uygulamaya geçirilebilir. Aşağıdaki örnek tek bir komut satırı bağımsız değişkeniyle başlatılan bir uygulamayı gösterir, "/Startküçültülmüş":

`wpfapplication.exe /StartMinimized`

Uygulama başlatma sırasında WPF, komut satırı bağımsız değişkenlerini işletim sisteminden alır ve <xref:System.Windows.Application.Startup> <xref:System.Windows.StartupEventArgs> parametresini parametresinin <xref:System.Windows.StartupEventArgs.Args%2A> özelliği aracılığıyla olay işleyicisine geçirir. Aşağıdaki gibi bir kod kullanarak komut satırı bağımsız değişkenlerini alabilir ve kaydedebilirsiniz.

[!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]

[!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
[!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]

Kod, **/startküçültülmüş** komut satırı bağımsız değişkeninin sağlandığını denetlemek için işler <xref:System.Windows.WindowState> <xref:System.Windows.Application.Startup> ; bu durumda, ile ana <xref:System.Windows.WindowState.Minimized>pencereyi açar. <xref:System.Windows.Window.WindowState%2A> Özelliğin programlı olarak ayarlanması gerektiğinden, Main <xref:System.Windows.Window> 'in doğrudan kodda açık olması gerektiğini unutmayın.

XBAP 'ler ClickOnce dağıtımı kullanılarak başlatıldıklarından komut satırı bağımsız değişkenlerini alamıyor ve işleyemez (bkz. [WPF uygulaması dağıtma](deploying-a-wpf-application-wpf.md)). Ancak, sorgu dizesi parametrelerini bunları başlatmak için kullanılan URL 'lerden alıp işleyebilir.

<a name="Application_Activation_and_Deactivation"></a>

### <a name="application-activation-and-deactivation"></a>Uygulama etkinleştirme ve devre dışı bırakma

Windows, kullanıcıların uygulamalar arasında geçiş yapmasına olanak tanır. En yaygın yol, ALT + TAB tuş birleşimini kullanmaktır. Bir uygulama yalnızca kullanıcının seçim yaptığı bir görünür <xref:System.Windows.Window> durumdaysa öğesine geçiş yapılabilir. Şu anda seçili <xref:System.Windows.Window> olan *etkin pencere* ( <xref:System.Windows.Window> *ön plan penceresi*olarak da bilinir) ve Kullanıcı girişini alır. Etkin pencere olan uygulama, *etkin uygulama* (veya *ön plan uygulaması*). Bir uygulama, aşağıdaki durumlarda etkin uygulama olur:

- Başlatılır ve bir <xref:System.Windows.Window>gösterir.

- Kullanıcı, uygulamada bir <xref:System.Windows.Window> seçerek başka bir uygulamadan geçiş yapar.

<xref:System.Windows.Application.Activated?displayProperty=nameWithType> Olayı işleyerek bir uygulamanın etkin hale geldiğini tespit edebilirsiniz.

Benzer şekilde, bir uygulama aşağıdaki koşullarda etkin değil olabilir:

- Kullanıcı geçerli bir uygulamaya başka bir uygulamaya geçer.

- Uygulama kapandığında.

<xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> Olayı işleyerek bir uygulamanın ne zaman etkin hale geldiğini tespit edebilirsiniz.

Aşağıdaki kod, <xref:System.Windows.Application.Activated> bir uygulamanın etkin olup olmadığını belirlemede <xref:System.Windows.Application.Deactivated> ve olaylarının nasıl işleneceğini gösterir.

[!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]

[!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
[!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]

Ayrıca <xref:System.Windows.Window> , etkinleştirilebilir ve devre dışı bırakılabilir. Daha <xref:System.Windows.Window.Activated?displayProperty=nameWithType> fazla <xref:System.Windows.Window.Deactivated?displayProperty=nameWithType> bilgi için bkz. ve.

> [!NOTE]
> XBAP <xref:System.Windows.Application.Activated?displayProperty=nameWithType> 'ler <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> için ne de oluşturulmaz.

<a name="Application_Shutdown"></a>

### <a name="application-shutdown"></a>Uygulama kapanıyor

Bir uygulamanın yaşam süresi kapatıldığında sona erer, bu durum aşağıdaki nedenlerden kaynaklanabilir:

- Kullanıcı her <xref:System.Windows.Window>bir kapatır.

- Kullanıcı Main <xref:System.Windows.Window>'i kapatır.

- Kullanıcı, oturum kapatarak veya kapatarak Windows oturumunu sonlandırır.

- Uygulamaya özgü bir koşul karşılandı.

Uygulama kapatılmasını <xref:System.Windows.Application> yönetmenize yardımcı olmak için <xref:System.Windows.Application.Shutdown%2A> yöntemi, <xref:System.Windows.Application.ShutdownMode%2A> özelliği ve <xref:System.Windows.Application.SessionEnding> ve <xref:System.Windows.Application.Exit> olaylarını sağlar.

> [!NOTE]
> <xref:System.Windows.Application.Shutdown%2A>yalnızca, olan <xref:System.Security.Permissions.UIPermission>uygulamalardan çağrılabilir. Tek başına WPF uygulamaları her zaman bu izne sahiptir. Ancak, Internet bölgesi kısmi güven güvenlik korumalı alanı içinde çalışan XBAP 'ler değildir.

#### <a name="shutdown-mode"></a>Kapalı modu

Çoğu uygulama, tüm pencereler kapandıktan ya da ana pencere kapatıldığında kapanır. Ancak, bazı durumlarda, uygulamaya özgü diğer koşullar bir uygulamanın ne zaman kapandığını tespit edebilir. <xref:System.Windows.Application.ShutdownMode%2A> Aşağıdaki<xref:System.Windows.ShutdownMode> sabit listesi değerlerinden biriyle, uygulamanız tarafından kapatılacak koşulları belirtebilirsiniz:

- <xref:System.Windows.ShutdownMode.OnLastWindowClose>

- <xref:System.Windows.ShutdownMode.OnMainWindowClose>

- <xref:System.Windows.ShutdownMode.OnExplicitShutdown>

Varsayılan değeri <xref:System.Windows.Application.ShutdownMode%2A> <xref:System.Windows.ShutdownMode.OnLastWindowClose>,, uygulamadaki son pencere Kullanıcı tarafından kapatıldığında uygulamanın otomatik olarak kapanması anlamına gelir. Ancak, ana pencere kapalıyken uygulamanız kapatıldıysa, olarak ayarlarsanız <xref:System.Windows.Application.ShutdownMode%2A> <xref:System.Windows.ShutdownMode.OnMainWindowClose>WPF otomatik olarak bunu yapar. Bu, aşağıdaki örnekte gösterilir.

[!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]

Uygulamaya özgü kapatılma koşullarınız olduğunda, olarak <xref:System.Windows.Application.ShutdownMode%2A> <xref:System.Windows.ShutdownMode.OnExplicitShutdown>ayarlanır. Bu durumda, <xref:System.Windows.Application.Shutdown%2A> yöntemi açıkça çağırarak bir uygulamayı kapatmak sizin sorumluluğunuzdadır; Aksi takdirde, tüm pencereler kapansa bile uygulamanız çalışmaya devam edecektir. Ya da olduğunda örtük <xref:System.Windows.Application.ShutdownMode%2A>olarakçağırılır. <xref:System.Windows.ShutdownMode.OnLastWindowClose> <xref:System.Windows.Application.Shutdown%2A> <xref:System.Windows.ShutdownMode.OnMainWindowClose>

> [!NOTE]
> <xref:System.Windows.Application.ShutdownMode%2A>bir XBAP 'den ayarlanabilir ancak yok sayılır; bir XBAP, bir tarayıcıdan veya XBAP 'yi barındıran tarayıcı kapatıldığında her zaman kapanır. Daha fazla bilgi için bkz. [gezintiye genel bakış](navigation-overview.md).

#### <a name="session-ending"></a>Oturum sonlandırılıyor

<xref:System.Windows.Application.ShutdownMode%2A> Özelliği tarafından tanımlanan kapatılma koşulları bir uygulamaya özeldir. Ancak, bazı durumlarda, bir dış koşulun sonucu olarak bir uygulama kapatılabilir. En yaygın dış koşul, bir Kullanıcı Windows oturumunu aşağıdaki eylemler ile bitiyorsa oluşur:

- Oturumu kapatma

- Kapanıyor

- Başlamasını

- Beklet

Bir Windows oturumunun ne zaman sona ereceğini algılamak için, aşağıdaki <xref:System.Windows.Application.SessionEnding> örnekte gösterildiği gibi olayını işleyebilirsiniz.

[!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]

[!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
[!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]

Bu örnekte, kod, Windows oturumunun nasıl <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> sona erdirmekte olduğunu belirlemek için özelliğini inceler. Kullanıcıya bir onay iletisi göstermek için bu değeri kullanır. Kullanıcı oturumun bitmesini istemiyor, Windows oturumunun bitmesini engellemek için kod kümesi olarak <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> `true` ayarlanır.

> [!NOTE]
> <xref:System.Windows.Application.SessionEnding>XBAP 'ler için çıkarılmadı.

#### <a name="exit"></a>Çık

Bir uygulama kapandığında, kalıcı uygulama durumu gibi bazı son işlemler gerçekleştirmek gerekebilir. Bu durumlar için olay işleyicisi aşağıdaki örnekte <xref:System.Windows.Application.Exit> `App_Exit` olduğu gibi olayını işleyebilirsiniz. *App. xaml* dosyasında bir olay işleyicisi olarak tanımlanır. Uygulaması *app.xaml.cs* ve *Application. xaml. vb* dosyalarında vurgulanır.

[!code-xaml[Defining-the-Exit-event-handler](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]

[!code-csharp[Handling-the-Exit-event](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=42-55)]
[!code-vb[Handling-the-Exit-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=34-45)]

Tam örnek için bkz. uygulama [oturumları arasında uygulama kapsamı özelliklerini kalıcı ve geri yükleme](persist-and-restore-application-scope-properties.md).

<xref:System.Windows.Application.Exit>, hem tek başına uygulamalar hem de XBAP 'ler tarafından işlenebilir. XBAP 'ler için <xref:System.Windows.Application.Exit> , aşağıdaki durumlarda oluşturulur:

- Bir XBAP üzerinden gezinilebilir.

- Internet Explorer 'da, XBAP 'yi barındıran sekme kapalı olduğunda.

- Tarayıcı kapatıldığında.

#### <a name="exit-code"></a>Çıkış kodu

Uygulamalar, genellikle bir kullanıcı isteğine yanıt olarak işletim sistemi tarafından başlatılır. Ancak, bir uygulama belirli bir görevi gerçekleştirmek için başka bir uygulama tarafından başlatılabilir. Başlatılan uygulama kapandığında, başlatılan uygulama, başlatılmış uygulamanın hangi koşullarda kapandığını bilmesini isteyebilir. Bu durumlarda, Windows, uygulamaların kapatılırken bir uygulama çıkış kodu döndürmesini sağlar. WPF uygulamaları varsayılan olarak 0 çıkış kodu değeri döndürür.

> [!NOTE]
> Visual Studio 'da hata ayıklarken uygulama çıkış kodu, uygulama kapandığında **Çıkış** penceresinde görüntülenir ve aşağıdakine benzer bir ileti gönderilir:
>
> `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`
>
> **Görünüm** menüsünde **Çıkış** ' a tıklayarak **Çıkış** penceresini açarsınız.

Çıkış kodunu değiştirmek için, çıkış kodu olarak bir tamsayı <xref:System.Windows.Application.Shutdown%28System.Int32%29> bağımsız değişkeni kabul eden aşırı yüklemeyi çağırabilirsiniz:

[!code-csharp[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
[!code-vb[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]

Çıkış kodunun değerini tespit edebilir ve <xref:System.Windows.Application.Exit> olayı işleyerek değiştirebilirsiniz. Olay işleyicisi, <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> özelliği ile çıkış <xref:System.Windows.ExitEventArgs> koduna erişim sağlayan bir öğesine geçirilir. <xref:System.Windows.Application.Exit> Daha fazla bilgi için bkz. <xref:System.Windows.Application.Exit>.

> [!NOTE]
> Çıkış kodunu hem tek başına uygulamalarda hem de XBAP 'lerde ayarlayabilirsiniz. Ancak, XBAP 'ler için çıkış kodu değeri yok sayılır.

<a name="Unhandled_Exceptions"></a>

### <a name="unhandled-exceptions"></a>İşlenmemiş özel durumlar

Bazen, beklenmeyen bir özel durum oluştuğunda bir uygulama anormal koşullar altında kapatılabilir. Bu durumda, uygulama özel durumu tespit etmek ve işlemek için koda sahip olmayabilir. Bu tür özel durum işlenmeyen bir özel durumdur; Aşağıdaki şekilde gösterilene benzer bir bildirim, uygulama kapatılmadan önce görüntülenir.

![İşlenmemiş bir özel durum bildirimi gösteren ekran görüntüsü.](./media/application-management-overview/unhandled-exception-notification.png)

Kullanıcı deneyimi perspektifinden, aşağıdakilerden bazılarını veya tümünü yaparak bir uygulamanın bu varsayılan davranışı önlemek daha iyidir:

- Kullanıcı dostu bilgileri görüntüleme.

- Bir uygulamayı çalışır durumda tutmaya çalışılıyor.

- Ayrıntılı, geliştirici kullanımı kolay özel durum bilgilerini Windows olay günlüğü 'nde kaydetme.

Bu desteğin uygulanması, işlenmemiş özel durumları algılamadığınıza bağlıdır. Bu, için <xref:System.Windows.Application.DispatcherUnhandledException> olayın oluşturulduğu şeydir.

[!code-xaml[detecting-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]

[!code-csharp[code-to-detect-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs)]
[!code-vb[code-to-detect-unhandled-exceptions](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb)]

Olay işleyicisi, özel durumun kendisi <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> (<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>) dahil olmak üzere işlenmeyen özel durumla ilgili bağlamsal bilgiler içeren bir parametre geçirdi. <xref:System.Windows.Application.DispatcherUnhandledException> Özel durumun nasıl işleneceğini öğrenmek için bu bilgileri kullanabilirsiniz.

' İ İşleseniz <xref:System.Windows.Application.DispatcherUnhandledException>, <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType> özelliğini olarak `true`ayarlamalısınız; Aksi takdirde WPF, özel durumu işlenmemiş olarak kabul eder ve daha önce açıklanan varsayılan davranışa geri döner. İşlenmeyen bir özel durum ortaya çıkar ve <xref:System.Windows.Application.DispatcherUnhandledException> olay işlenmezse ya da olay işlenirse ve <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> olarak `false`ayarlanırsa, uygulama hemen kapanır. Ayrıca, başka <xref:System.Windows.Application> hiçbir olay oluşturulmaz. Sonuç olarak, uygulamanızın uygulama kapatılmadan <xref:System.Windows.Application.DispatcherUnhandledException> önce çalıştırılması gereken bir kodu varsa uygulamanız gerekir.

Bir uygulama işlenmeyen bir özel durum nedeniyle kapatılabilir olsa da, bir uygulama bir sonraki bölümde anlatıldığı gibi bir kullanıcı isteğine yanıt olarak genellikle kapanır.

<a name="Application_Lifetime_Events"></a>

### <a name="application-lifetime-events"></a>Uygulama ömür olayları

Tek başına uygulamalar ve XBAP 'ler tam olarak aynı ömürleri içermez. Aşağıdaki şekilde, tek başına bir uygulamanın yaşam süresi boyunca önemli olaylar gösterilmektedir ve bunların oluşturulma sırası gösterilmektedir.

![Tek başına &#45; uygulama uygulaması nesne olayları](./media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")

Benzer şekilde, aşağıdaki şekilde, bir XBAP 'nin kullanım ömrü boyunca önemli olaylar gösterilmektedir ve bunların hangi sırayla ortaya çıkarıldığını gösterir.

![XBAP &#45; uygulama nesnesi olayları](./media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Application>
- [WPF Windows'a Genel Bakış](wpf-windows-overview.md)
- [Gezintiye Genel Bakış](navigation-overview.md)
- [WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları](wpf-application-resource-content-and-data-files.md)
- [WPF İçinde URI'leri Paketleme](pack-uris-in-wpf.md)
- [Uygulama modeli: Nasıl yapılır konuları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms749013(v=vs.100))
- [Uygulama Geliştirme](index.md)
