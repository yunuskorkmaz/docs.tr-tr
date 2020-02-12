---
title: Uygulama Yönetimine Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
ms.openlocfilehash: dbc5bd9f699415fb47f21c6a45b1c58cfcff0f33
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124526"
---
# <a name="application-management-overview"></a>Uygulama Yönetimine Genel Bakış

Tüm uygulamalar, uygulama uygulaması ve yönetimi için geçerli olan ortak bir işlev kümesini paylaşma eğilimindedir. Bu konu, uygulamaları oluşturmak ve yönetmek için <xref:System.Windows.Application> sınıfındaki işlevlere genel bir bakış sağlar.

## <a name="the-application-class"></a>Uygulama sınıfı

WPF 'de, yaygın uygulama kapsamlı işlevselliği <xref:System.Windows.Application> sınıfında kapsüllenir. <xref:System.Windows.Application> sınıfı aşağıdaki işlevleri içerir:

- Uygulama ömrü ile izleme ve etkileşim kurma.

- Komut satırı parametrelerini alma ve işleme.

- İşlenmeyen özel durumları algılama ve yanıtlama.

- Uygulama kapsamı özelliklerini ve kaynaklarını paylaşma.

- Windows 'ı tek başına uygulamalarda yönetme.

- Gezintiyi izleme ve yönetme.

<a name="The_Application_Class"></a>

## <a name="how-to-perform-common-tasks-using-the-application-class"></a>Uygulama sınıfını kullanarak ortak görevleri gerçekleştirme

<xref:System.Windows.Application> sınıfının tüm ayrıntılarını ilgilenmiyorsanız, aşağıdaki tabloda <xref:System.Windows.Application> genel görevlerden bazıları ve bunların nasıl yapılacağı listelenmektedir. İlgili API ve konuları görüntüleyerek daha fazla bilgi ve örnek kod bulabilirsiniz.

|Görev|Yaklaşım|
|----------|--------------|
|Geçerli uygulamayı temsil eden bir nesne al|<xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> özelliğini kullanın.|
|Uygulamaya başlangıç ekranı ekleme|Bkz. [WPF uygulamasına giriş ekranı ekleme](how-to-add-a-splash-screen-to-a-wpf-application.md).|
|Uygulama başlatma|<xref:System.Windows.Application.Run%2A?displayProperty=nameWithType> yöntemini kullanın.|
|Bir uygulamayı durdur|<xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> nesnesinin <xref:System.Windows.Application.Shutdown%2A> yöntemini kullanın.|
|Komut satırından bağımsız değişkenleri al|<xref:System.Windows.Application.Startup?displayProperty=nameWithType> olayını işleyin ve <xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType> özelliğini kullanın. Bir örnek için <xref:System.Windows.Application.Startup?displayProperty=nameWithType> olayına bakın.|
|Uygulama çıkış kodunu al ve ayarla|<xref:System.Windows.Application.Exit?displayProperty=nameWithType> olay işleyicisindeki <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType> özelliğini ayarlayın veya <xref:System.Windows.Application.Shutdown%2A> metodunu çağırın ve bir tamsayı olarak geçirin.|
|İşlenmeyen özel durumları Algıla ve Yanıtla|<xref:System.Windows.Application.DispatcherUnhandledException> olayı işleyin.|
|Uygulama kapsamındaki kaynakları edinme ve ayarlama|<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> özelliğini kullanın.|
|Uygulama kapsamı kaynak sözlüğü kullanma|Bkz. [uygulama kapsamı kaynak sözlüğü kullanma](how-to-use-an-application-scope-resource-dictionary.md).|
|Uygulama kapsamlı özellikleri al ve ayarla|<xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType> özelliğini kullanın.|
|Uygulamanın durumunu al ve Kaydet|Bkz. uygulama [oturumları arasında uygulama kapsamı özelliklerini kalıcı ve geri yükleme](persist-and-restore-application-scope-properties.md).|
|Kaynak dosyaları, içerik dosyaları ve kaynak yeri dosyaları dahil olmak üzere kod olmayan veri dosyalarını yönetin.|Bkz. [WPF uygulama kaynağı, içerik ve veri dosyaları](wpf-application-resource-content-and-data-files.md).|
|Tek başına uygulamalardaki pencereleri yönetme|Bkz. [WPF Windows 'A genel bakış](wpf-windows-overview.md).|
|Gezintiyi izleme ve yönetme|Bkz. [gezintiye genel bakış](navigation-overview.md).|

<a name="The_Application_Definition"></a>

## <a name="the-application-definition"></a>Uygulama tanımı

<xref:System.Windows.Application> sınıfının işlevlerini kullanmak için bir uygulama tanımı uygulamanız gerekir. WPF uygulama tanımı, <xref:System.Windows.Application> türetilen ve özel bir MSBuild ayarıyla yapılandırılan bir sınıftır.

### <a name="implementing-an-application-definition"></a>Uygulama tanımı uygulama

Tipik bir WPF uygulama tanımı hem biçimlendirme hem de arka plan kodu kullanılarak uygulanır. Bu, uygulama özelliklerini, kaynakları ve olayları işlemeyi ve olayları işlerken ve arka plan kod içinde uygulamaya özgü davranışı uygulamayı bir arada ayarlamak için biçimlendirme kullanmanıza olanak sağlar.

Aşağıdaki örnek, hem biçimlendirme hem de arka plan kodu kullanarak bir uygulama tanımının nasıl uygulanacağını gösterir:

[!code-xaml[ApplicationSnippets#ApplicationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]

[!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
[!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]

Biçimlendirme dosyası ve arka plan kod dosyasının birlikte çalışmasına izin vermek için aşağıdakiler olması gerekir:

- Biçimlendirme ' de `Application` öğesi `x:Class` özniteliğini içermelidir. Uygulama oluşturulduğunda, biçimlendirme dosyasında `x:Class` bulunması MSBuild 'in <xref:System.Windows.Application> türetilen ve `x:Class` özniteliği tarafından belirtilen ada sahip bir `partial` sınıfı oluşturmasına neden olur. Bu, XAML şeması (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`) için bir XML ad alanı bildiriminin eklenmesini gerektirir.

- Arka plan kod içinde, sınıf, biçimlendirme içindeki `x:Class` özniteliğiyle belirtilen aynı ada sahip `partial` bir sınıf olmalıdır ve <xref:System.Windows.Application>türetmelidir. Bu, arka plan kod dosyasının, uygulama oluşturulduğunda işaretleme dosyası için oluşturulan `partial` sınıfıyla ilişkilendirilmesine izin verir (bkz. [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md)).

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

Elde edilen kod, uygulama tanımınızı `Main`giriş noktası yöntemini içeren ek altyapı kodu ile genişlettiğini. <xref:System.STAThreadAttribute> özniteliği, WPF uygulaması için ana UI iş parçacığının WPF uygulamaları için gerekli olan bir STA iş parçacığı olduğunu göstermek için `Main` yöntemine uygulanır. Çağrıldığında, `Main` olayları kaydetmek ve biçimlendirmede uygulanan özellikleri ayarlamak için `InitializeComponent` yöntemini çağırmadan önce `App` yeni bir örneğini oluşturur. Sizin için `InitializeComponent` oluşturulduğundan, <xref:System.Windows.Controls.Page> ve <xref:System.Windows.Window> uygulamalarında yaptığınız gibi bir uygulama tanımından `InitializeComponent` açıkça çağırmanız gerekmez. Son olarak, uygulamayı başlatmak için <xref:System.Windows.Application.Run%2A> yöntemi çağırılır.

<a name="Getting_the_Current_Application"></a>

## <a name="getting-the-current-application"></a>Geçerli uygulama alınıyor

<xref:System.Windows.Application> sınıfının işlevselliği bir uygulama genelinde paylaşıldığından, <xref:System.AppDomain>başına <xref:System.Windows.Application> sınıfının yalnızca bir örneği olabilir. Bunu zorlamak için <xref:System.Windows.Application> sınıfı tek bir sınıf olarak uygulanır [(bkz C#. tek bir ](https://docs.microsoft.com/previous-versions/msp-n-p/ff650316(v=pandp.10))örneğini oluşturur) ve buna `static`<xref:System.Windows.Application.Current%2A> özelliği ile paylaşılan erişim sağlar.

Aşağıdaki kod, geçerli <xref:System.AppDomain>için <xref:System.Windows.Application> nesnesine nasıl bir başvuru alınacağını göstermektedir.

[!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
[!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]

<xref:System.Windows.Application.Current%2A>, <xref:System.Windows.Application> sınıfının bir örneğine bir başvuru döndürür. <xref:System.Windows.Application> türetilmiş sınıfa bir başvuru isterseniz, aşağıdaki örnekte gösterildiği gibi <xref:System.Windows.Application.Current%2A> özelliğinin değerini atamalısınız.

[!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
[!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]

<xref:System.Windows.Application.Current%2A> değerini, bir <xref:System.Windows.Application> nesnesinin kullanım ömrü boyunca herhangi bir noktada inceleyebilirsiniz. Ancak dikkatli olmanız gerekir. <xref:System.Windows.Application> sınıfı örneği oluşturulduktan sonra, <xref:System.Windows.Application> nesnesinin durumunun tutarsız olduğu bir nokta vardır. Bu süre boyunca <xref:System.Windows.Application>, kodunuzu çalıştırmak için gereken, uygulama altyapısını oluşturma, özellikleri ayarlama ve olayları kaydetme gibi çeşitli başlatma görevlerini gerçekleştiriyor. Bu süre içinde <xref:System.Windows.Application> nesnesini kullanmaya çalışırsanız, özellikle de ayarlanan çeşitli <xref:System.Windows.Application> özelliklerine bağlı ise, kodunuz beklenmedik sonuçlara neden olabilir.

<xref:System.Windows.Application> başlatma işini tamamladığında, ömrü gerçekten başlar.

<a name="Application_Lifetime"></a>

## <a name="application-lifetime"></a>Uygulama ömrü

WPF uygulamasının yaşam süresi, uygulamanızın başlatıldığı zaman etkinleştirilmiş ve devre dışı bırakılmış ve kapatılmış olduğunu bilmeniz için <xref:System.Windows.Application> tarafından oluşturulan birkaç olay tarafından işaretlenir.

<a name="Splash_Screen"></a>

### <a name="splash-screen"></a>Giriş Ekranı

.NET Framework 3,5 SP1 'den başlayarak, bir başlangıç penceresinde veya *Giriş ekranında*kullanılacak bir görüntü belirtebilirsiniz. <xref:System.Windows.SplashScreen> sınıfı, uygulamanız yüklenirken bir başlangıç penceresini görüntülemeyi kolaylaştırır. <xref:System.Windows.SplashScreen> pencere oluşturulur ve <xref:System.Windows.Application.Run%2A> çağrılmadan önce gösterilir. Daha fazla bilgi için bkz. [uygulama başlangıç süresi](../advanced/application-startup-time.md) ve [bir WPF uygulamasına giriş ekranı ekleme](how-to-add-a-splash-screen-to-a-wpf-application.md).

<a name="Starting_an_Application"></a>

### <a name="starting-an-application"></a>Uygulama başlatma

<xref:System.Windows.Application.Run%2A> çağrıldıktan ve uygulama başlatıldıktan sonra, uygulama çalıştırılmaya hazırdır. <xref:System.Windows.Application.Startup> olay ortaya çıktığında bu süre belirlenir:

[!code-csharp[Startup-event](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs?range=3-11,31-33)]
[!code-vb[Startup-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb?range=5-11,30-32)]

Uygulamanın ömrü olan bu noktada, en sık yapılacak şey bir kullanıcı arabirimi göstermedir.

<a name="Showing_a_User_Interface"></a>

### <a name="showing-a-user-interface"></a>Kullanıcı arabirimini gösterme

Tek başına Windows uygulamaları çalışmaya başladıklarında bir <xref:System.Windows.Window> açar. <xref:System.Windows.Application.Startup> olay işleyicisi, aşağıdaki kodda gösterildiği gibi bunu yapabileceğiniz bir konumdur.

[!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]

[!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
[!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]

> [!NOTE]
> Tek başına bir uygulamada örnek olarak oluşturulacak ilk <xref:System.Windows.Window>, varsayılan olarak ana uygulama penceresi olur. Bu <xref:System.Windows.Window> nesnesine <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> özelliği tarafından başvuruluyor. <xref:System.Windows.Application.MainWindow%2A> özelliğinin değeri, ilk örneklenmiş <xref:System.Windows.Window> farklı bir pencere, ana pencere olması halinde programlama yoluyla değiştirilebilir.

Bir XBAP ilk kez başladığında, büyük olasılıkla bir <xref:System.Windows.Controls.Page>gidecektir. Bu, aşağıdaki kodda gösterilmiştir.

[!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]

[!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
[!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]

Yalnızca bir <xref:System.Windows.Window> açmak ya da bir <xref:System.Windows.Controls.Page>gitmek için <xref:System.Windows.Application.Startup> işleyin, biçimlendirme içinde `StartupUri` özniteliğini ayarlayabilirsiniz.

Aşağıdaki örnek, bir <xref:System.Windows.Window>açmak için tek başına uygulamadan <xref:System.Windows.Application.StartupUri%2A> nasıl kullanacağınızı gösterir.

[!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]

Aşağıdaki örnek, bir <xref:System.Windows.Controls.Page>gitmek için bir XBAP 'tan <xref:System.Windows.Application.StartupUri%2A> nasıl kullanacağınızı gösterir.

[!code-xaml[PageSnippets#XBAPStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]

Bu biçimlendirme, bir pencere açmak için önceki kodla aynı etkiye sahiptir.

> [!NOTE]
> Gezinti hakkında daha fazla bilgi için bkz. [gezintiye genel bakış](navigation-overview.md).

Parametresiz bir Oluşturucu kullanarak örneğini oluşturmanız gerekiyorsa veya onu göstermeden önce özelliklerini ayarlamanız veya olaylarına abone olmanız ya da uygulamanın başlatıldığı sırada sağlanan tüm komut satırı bağımsız değişkenlerini işlemeniz gerekiyorsa, <xref:System.Windows.Window> açmak için <xref:System.Windows.Application.Startup> olayını işlemeniz gerekir.

<a name="Processing_Command_Line_Arguments"></a>

### <a name="processing-command-line-arguments"></a>Komut satırı bağımsız değişkenlerini işleme

Windows 'da tek başına uygulamalar, bir komut isteminden veya masaüstünden başlatılabilir. Her iki durumda da, komut satırı bağımsız değişkenleri uygulamaya geçirilebilir. Aşağıdaki örnek tek bir komut satırı bağımsız değişkeniyle başlatılan bir uygulamayı gösterir, "/Startküçültülmüş":

`wpfapplication.exe /StartMinimized`

Uygulama başlatma sırasında WPF, komut satırı bağımsız değişkenlerini işletim sisteminden alır ve <xref:System.Windows.StartupEventArgs> parametresinin <xref:System.Windows.StartupEventArgs.Args%2A> özelliği aracılığıyla bunları <xref:System.Windows.Application.Startup> olay işleyicisine geçirir. Aşağıdaki gibi bir kod kullanarak komut satırı bağımsız değişkenlerini alabilir ve kaydedebilirsiniz.

[!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]

[!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
[!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]

Kod, **/Startküçültülmüş** komut satırı bağımsız değişkeninin sağlandığını denetlemek için <xref:System.Windows.Application.Startup> işler. Bu durumda, <xref:System.Windows.WindowState.Minimized><xref:System.Windows.WindowState> ana pencereyi açar. <xref:System.Windows.Window.WindowState%2A> özelliğinin programlı olarak ayarlanması gerektiğinden, ana <xref:System.Windows.Window> açıkça kodda açık olması gerekir.

XBAP 'ler ClickOnce dağıtımı kullanılarak başlatıldıklarından komut satırı bağımsız değişkenlerini alamıyor ve işleyemez (bkz. [WPF uygulaması dağıtma](deploying-a-wpf-application-wpf.md)). Ancak, sorgu dizesi parametrelerini bunları başlatmak için kullanılan URL 'lerden alıp işleyebilir.

<a name="Application_Activation_and_Deactivation"></a>

### <a name="application-activation-and-deactivation"></a>Uygulama etkinleştirme ve devre dışı bırakma

Windows, kullanıcıların uygulamalar arasında geçiş yapmasına olanak tanır. En yaygın yol, ALT + TAB tuş birleşimini kullanmaktır. Bir uygulama yalnızca kullanıcının seçebileceğiniz görünür bir <xref:System.Windows.Window> varsa öğesine geçiş yapılabilir. Şu anda seçili olan <xref:System.Windows.Window> *etkin pencere* ( *ön plan penceresi*olarak da bilinir) ve Kullanıcı girişini alan <xref:System.Windows.Window>. Etkin pencere olan uygulama, *etkin uygulama* (veya *ön plan uygulaması*). Bir uygulama, aşağıdaki durumlarda etkin uygulama olur:

- Başlatılır ve bir <xref:System.Windows.Window>gösterir.

- Kullanıcı, uygulamada bir <xref:System.Windows.Window> seçerek başka bir uygulamadan geçer.

<xref:System.Windows.Application.Activated?displayProperty=nameWithType> olayını işleyerek bir uygulamanın etkin hale geldiğini tespit edebilirsiniz.

Benzer şekilde, bir uygulama aşağıdaki koşullarda etkin değil olabilir:

- Kullanıcı geçerli bir uygulamaya başka bir uygulamaya geçer.

- Uygulama kapandığında.

<xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> olayını işleyerek bir uygulamanın ne zaman devre dışı duruma geldiğini tespit edebilirsiniz.

Aşağıdaki kod, bir uygulamanın etkin olup olmadığını anlamak için <xref:System.Windows.Application.Activated> ve <xref:System.Windows.Application.Deactivated> olaylarının nasıl işleneceğini gösterir.

[!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]

[!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
[!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]

<xref:System.Windows.Window> Ayrıca etkinleştirilebilir ve devre dışı bırakılabilir. Daha fazla bilgi için bkz. <xref:System.Windows.Window.Activated?displayProperty=nameWithType> ve <xref:System.Windows.Window.Deactivated?displayProperty=nameWithType>.

> [!NOTE]
> XBAP 'ler için ne <xref:System.Windows.Application.Activated?displayProperty=nameWithType> ne de <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> oluşturulmaz.

<a name="Application_Shutdown"></a>

### <a name="application-shutdown"></a>Uygulama kapanıyor

Bir uygulamanın yaşam süresi kapatıldığında sona erer, bu durum aşağıdaki nedenlerden kaynaklanabilir:

- Kullanıcı her <xref:System.Windows.Window>kapatır.

- Kullanıcı ana <xref:System.Windows.Window>kapatır.

- Kullanıcı, oturum kapatarak veya kapatarak Windows oturumunu sonlandırır.

- Uygulamaya özgü bir koşul karşılandı.

Uygulama kapatılmasını yönetmenize yardımcı olmak için <xref:System.Windows.Application> <xref:System.Windows.Application.Shutdown%2A> yöntemi, <xref:System.Windows.Application.ShutdownMode%2A> özelliğini ve <xref:System.Windows.Application.SessionEnding> ve <xref:System.Windows.Application.Exit> olaylarını sağlar.

> [!NOTE]
> <xref:System.Windows.Application.Shutdown%2A>, yalnızca <xref:System.Security.Permissions.UIPermission>olan uygulamalardan çağrılabilir. Tek başına WPF uygulamaları her zaman bu izne sahiptir. Ancak, Internet bölgesi kısmi güven güvenlik korumalı alanı içinde çalışan XBAP 'ler değildir.

#### <a name="shutdown-mode"></a>Kapalı modu

Çoğu uygulama, tüm pencereler kapandıktan ya da ana pencere kapatıldığında kapanır. Ancak, bazı durumlarda, uygulamaya özgü diğer koşullar bir uygulamanın ne zaman kapandığını tespit edebilir. Aşağıdaki <xref:System.Windows.ShutdownMode> sabit listesi değerlerinden biriyle <xref:System.Windows.Application.ShutdownMode%2A> ayarlayarak uygulamanız kapatılacak koşulları belirtebilirsiniz:

- <xref:System.Windows.ShutdownMode.OnLastWindowClose>

- <xref:System.Windows.ShutdownMode.OnMainWindowClose>

- <xref:System.Windows.ShutdownMode.OnExplicitShutdown>

Varsayılan <xref:System.Windows.Application.ShutdownMode%2A> değeri <xref:System.Windows.ShutdownMode.OnLastWindowClose>, yani uygulamadaki son pencere Kullanıcı tarafından kapatıldığında uygulamanın otomatik olarak kapanması anlamına gelir. Ancak, ana pencere kapalıyken uygulamanız kapatıldıysa, <xref:System.Windows.Application.ShutdownMode%2A> <xref:System.Windows.ShutdownMode.OnMainWindowClose>olarak ayarlarsanız WPF otomatik olarak bunu yapar. Bu, aşağıdaki örnekte gösterilir.

[!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]

Uygulamaya özgü kapatılma koşullarınız olduğunda <xref:System.Windows.Application.ShutdownMode%2A> <xref:System.Windows.ShutdownMode.OnExplicitShutdown>olarak ayarlarsınız. Bu durumda, <xref:System.Windows.Application.Shutdown%2A> yöntemini açıkça çağırarak bir uygulamayı kapatmak sizin sorumluluğunuzdadır. Aksi takdirde, tüm pencereler kapansa bile uygulamanız çalışmaya devam edecektir. <xref:System.Windows.Application.Shutdown%2A>, <xref:System.Windows.Application.ShutdownMode%2A> <xref:System.Windows.ShutdownMode.OnLastWindowClose> ya da <xref:System.Windows.ShutdownMode.OnMainWindowClose>olduğunda örtük olarak çağrıldığını unutmayın.

> [!NOTE]
> <xref:System.Windows.Application.ShutdownMode%2A> bir XBAP 'den ayarlanabilir, ancak yok sayılır; bir XBAP, bir tarayıcıdan veya XBAP 'yi barındıran tarayıcı kapatıldığında her zaman kapanır. Daha fazla bilgi için bkz. [gezintiye genel bakış](navigation-overview.md).

#### <a name="session-ending"></a>Oturum sonlandırılıyor

<xref:System.Windows.Application.ShutdownMode%2A> özelliği tarafından açıklanan kapalı koşullar bir uygulamaya özeldir. Ancak, bazı durumlarda, bir dış koşulun sonucu olarak bir uygulama kapatılabilir. En yaygın dış koşul, bir Kullanıcı Windows oturumunu aşağıdaki eylemler ile bitiyorsa oluşur:

- Oturumu kapatma

- Kapanıyor

- Yeniden başlatılıyor

- Beklet

Bir Windows oturumunun ne zaman sona ereceğini algılamak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Windows.Application.SessionEnding> olayını işleyebilirsiniz.

[!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]

[!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
[!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]

Bu örnekte kod, Windows oturumunun nasıl sona erdirmekte olduğunu belirlemek için <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> özelliğini inceler. Kullanıcıya bir onay iletisi göstermek için bu değeri kullanır. Kullanıcı oturumun bitmesini istemiyor, Windows oturumunun bitmesini engellemek için kod <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> `true` olarak ayarlanır.

> [!NOTE]
> <xref:System.Windows.Application.SessionEnding> XBAP 'ler için çıkarılmadı.

#### <a name="exit"></a>Çık

Bir uygulama kapandığında, kalıcı uygulama durumu gibi bazı son işlemler gerçekleştirmek gerekebilir. Bu durumlar için, `App_Exit` olay işleyicisi aşağıdaki örnekte olduğu gibi <xref:System.Windows.Application.Exit> olayını işleyebilirsiniz. *App. xaml* dosyasında bir olay işleyicisi olarak tanımlanır. Uygulaması *app.xaml.cs* ve *Application. xaml. vb* dosyalarında vurgulanır.

[!code-xaml[Defining-the-Exit-event-handler](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]

[!code-csharp[Handling-the-Exit-event](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=42-55)]
[!code-vb[Handling-the-Exit-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=34-45)]

Tam örnek için bkz. uygulama [oturumları arasında uygulama kapsamı özelliklerini kalıcı ve geri yükleme](persist-and-restore-application-scope-properties.md).

<xref:System.Windows.Application.Exit>, hem tek başına uygulamalar hem de XBAP 'ler tarafından işlenebilir. XBAP 'ler için <xref:System.Windows.Application.Exit> aşağıdaki durumlarda oluşturulur:

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

Çıkış kodunu değiştirmek için, çıkış kodu olarak bir tamsayı bağımsız değişkeni kabul eden <xref:System.Windows.Application.Shutdown%28System.Int32%29> aşırı yüklemeyi çağırabilirsiniz:

[!code-csharp[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
[!code-vb[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]

Çıkış kodunun değerini tespit edebilir ve <xref:System.Windows.Application.Exit> olayını işleyerek değiştirebilirsiniz. <xref:System.Windows.Application.Exit> olay işleyicisine <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> özelliği ile çıkış koduna erişim sağlayan bir <xref:System.Windows.ExitEventArgs> geçirilir. Daha fazla bilgi için bkz. <xref:System.Windows.Application.Exit>.

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

Bu desteğin uygulanması, işlenmemiş özel durumları algılamadığınıza bağlıdır. Bu, <xref:System.Windows.Application.DispatcherUnhandledException> olayının oluşturulduğu şeydir.

[!code-xaml[detecting-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]

[!code-csharp[code-to-detect-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs)]
[!code-vb[code-to-detect-unhandled-exceptions](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb)]

<xref:System.Windows.Application.DispatcherUnhandledException> olay işleyicisine, özel durumun kendisi (<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>) dahil olmak üzere, işlenmeyen özel durumla ilgili bağlamsal bilgiler içeren bir <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> parametresi iletilir. Özel durumun nasıl işleneceğini öğrenmek için bu bilgileri kullanabilirsiniz.

<xref:System.Windows.Application.DispatcherUnhandledException>işlerken, <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType> özelliğini `true`; olarak ayarlamanız gerekir. Aksi halde, WPF özel durumu işlenmemiş olarak kabul eder ve daha önce açıklanan varsayılan davranışa geri döner. İşlenmemiş bir özel durum ortaya çıkar ve <xref:System.Windows.Application.DispatcherUnhandledException> olayı işlenmezse ya da olay işlenirse ve <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> `false`olarak ayarlandıysa, uygulama hemen kapanır. Ayrıca, başka bir <xref:System.Windows.Application> olayı oluşturulmaz. Sonuç olarak, uygulamanızın uygulama kapatılmadan önce çalışması gereken bir kodu varsa <xref:System.Windows.Application.DispatcherUnhandledException> işlemeniz gerekir.

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
- [Uygulama modeli: nasıl yapılır konuları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms749013(v=vs.100))
- [Uygulama Geliştirme](index.md)
