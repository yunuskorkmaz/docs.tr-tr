---
title: "Uygulama Yönetimine Genel Bakış"
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
helpviewer_keywords: application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
caps.latest.revision: "56"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09129f2dc2bac2bb17ebacd6d6db020288b6f616
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="application-management-overview"></a>Uygulama Yönetimine Genel Bakış
Tüm uygulamaları, ortak bir uygulama uygulama ve Yönetim için geçerli işlevi sahip olma eğilimi gösterir. Bu konu içinde işlevlerine genel bakış sağlar <xref:System.Windows.Application> oluşturmak ve uygulamaları yönetmek için sınıf.  
   
  
## <a name="the-application-class"></a>Uygulama sınıfı  
 İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], ortak uygulama kapsamlı işlevsellik kapsüllenmiş içinde <xref:System.Windows.Application> sınıfı. <xref:System.Windows.Application> Sınıfı, aşağıdaki işlevleri içerir:  
  
-   İzleme ve uygulama yaşam süresi ile etkileşim.  
  
-   Komut satırı parametreleri işlenirken ve alma.  
  
-   Algılama ve işlenmeyen özel durumlar için yanıt.  
  
-   Uygulama kapsam özellikleri ve kaynakları paylaşma.  
  
-   Bağımsız uygulamalar Windows yönetme.  
  
-   İzleme ve gezinti yönetme.  
  
<a name="The_Application_Class"></a>   
## <a name="how-to-perform-common-tasks-using-the-application-class"></a>Uygulama sınıfı kullanarak ortak görevleri gerçekleştirme  
 Tüm ayrıntılarını ilgilenen değilseniz <xref:System.Windows.Application> sınıfı, aşağıdaki tabloda listelenmektedir bazı ortak görevler için <xref:System.Windows.Application> ve bunların nasıl yapılacağını. İlgili API ve konuları görüntüleyerek, daha fazla bilgi ve örnek kod bulabilirsiniz.  
  
|Görev|Yaklaşım|  
|----------|--------------|  
|Geçerli uygulamanın temsil eden bir nesne Al|Kullanım <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> özelliği.|  
|Uygulama başlangıç ekranı ekleme|Bkz: [WPF uygulaması için bir giriş ekranı eklemek](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).|  
|Uygulama başlatma|Kullanım <xref:System.Windows.Application.Run%2A?displayProperty=nameWithType> yöntemi.|  
|Bir uygulamayı durdurun|Kullanım <xref:System.Windows.Application.Shutdown%2A> yöntemi <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> nesnesi.|  
|Komut satırından bağımsız değişken Al|İşleme <xref:System.Windows.Application.Startup?displayProperty=nameWithType> olay ve kullanım <xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType> özelliği. Bir örnek için bkz: <xref:System.Windows.Application.Startup?displayProperty=nameWithType> olay.|  
|Alma ve uygulama çıkış kodu ayarlama|Ayarlama <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType> özelliğinde <xref:System.Windows.Application.Exit?displayProperty=nameWithType> olay işleyicisi veya çağrı <xref:System.Windows.Application.Shutdown%2A> yöntemi ve tamsayı geçirin.|  
|Algılamak ve işlenmeyen özel durumlar için yanıt|Tanıtıcı <xref:System.Windows.Application.DispatcherUnhandledException> olay.|  
|Alma ve uygulama kapsamlı kaynakları ayarlama|Kullanım <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> özelliği.|  
|Bir uygulama kapsamı kaynak sözlük kullanma|Bkz: [bir uygulama kapsamı kaynak sözlük kullanma](../../../../docs/framework/wpf/app-development/how-to-use-an-application-scope-resource-dictionary.md).|  
|Alma ve uygulama kapsamlı özellikler ayarlama|Kullanım <xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType> özelliği.|  
|Alma ve uygulama durumunu Kaydet|Bkz: [kalıcı hale getirmek ve geri yükleme, uygulama kapsamı özelliklerini uygulama oturumları arasında](../../../../docs/framework/wpf/app-development/persist-and-restore-application-scope-properties.md).|  
|Kaynak dosyaları, içerik dosyaları ve kaynak site dosyaları dahil olmak üzere kod olmayan veri dosyalarını yönetin.|Bkz: [WPF Uygulama kaynağı, içerik ve veri dosyalarını](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).|  
|Bağımsız uygulamalar Windows yönetme|Bkz: [WPF Windows genel bakış](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md).|  
|İzleme ve gezinti yönetme|Bkz: [Gezinti genel bakış](../../../../docs/framework/wpf/app-development/navigation-overview.md).|  
  
<a name="The_Application_Definition"></a>   
## <a name="the-application-definition"></a>Uygulama tanımı  
 Faydalanmak için <xref:System.Windows.Application> sınıfı, bir uygulama tanımı uygulamalıdır. A [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama tanımıdır türeyen bir sınıf <xref:System.Windows.Application> ve bir özel ile yapılandırılmış [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] ayarı.  
  
### <a name="implementing-an-application-definition"></a>Uygulama tanımı uygulama  
 Tipik bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama tanımını markup ve arka plan kodu kullanılarak gerçekleştirilir. Bu, bildirimli olarak uygulama özellikleri, kaynaklar, ayarlayın ve olayları işleme ve uygulamaya özgü davranış kod arkasında uygulama çalışırken olayları kaydetmek için işaretleme kullanmanıza olanak sağlar.  
  
 Aşağıdaki örnek, biçimlendirme ve arka plan kodu kullanarak bir uygulama tanımının uygulamak gösterilmektedir:  
  
 [!code-xaml[ApplicationSnippets#ApplicationXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]  
  
 [!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
 [!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]  
  
 Biçimlendirme dosyası ve arka plan kodu dosyanın birlikte çalışabilmesi için aşağıdaki izin vermek için gerçekleşmesi gerekir:  
  
-   Biçimlendirme içinde `Application` öğesi içermelidir `x:Class` özniteliği. Ne zaman uygulaması oluşturulur, varlığını `x:Class` biçimlendirmede dosya neden olan [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] oluşturmak için bir `partial` öğesinden türetilen sınıf <xref:System.Windows.Application> ve tarafından belirtilen ada sahip `x:Class` özniteliği. Bu eklenmesini gerektirir bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] için ad alanı bildiriminin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] şeması ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).  
  
-   Kod arkasında, sınıf olmalıdır bir `partial` sınıfı tarafından belirtilen aynı ada sahip `x:Class` özniteliği biçimlendirme ve öğesinden türetilmelidir <xref:System.Windows.Application>. Bu arka plan kodu ile ilişkili dosyaya verir `partial` uygulama yapılandırıldığında biçimlendirme dosyası için oluşturulan sınıf (bkz [WPF uygulaması oluşturma](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)).  
  
> [!NOTE]
>  Yeni bir WPF uygulama projesi veya kullanarak WPF tarayıcı uygulaması projesi oluşturduğunuzda [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], uygulama tanımı varsayılan olarak dahil edilir ve biçimlendirme ve arka plan kodu kullanılarak tanımlanır.  
  
 Bu kod, bir uygulama tanımının uygulamak için gereken en düşük gereksinimdir. Ancak, ek bir [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] yapılandırma derleme ve uygulamayı çalıştırmadan önce uygulama tanımı için yapılması gerekir.  
  
### <a name="configuring-the-application-definition-for-msbuild"></a>Uygulama tanımı MSBuild için yapılandırma  
 Bağımsız uygulamalar ve [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] çalıştırabilmeniz için önce belirli bir düzeyde altyapı uygulaması gerektirir. Bu altyapı en önemli bir parçası giriş noktasıdır. Bir kullanıcı tarafından bir uygulama başlatıldığında, işletim sistemi uygulamaları başlatma için iyi bilinen bir işlevi olduğunu giriş noktası çağırır.  
  
 Geleneksel olarak, geliştiricilerin bazılarını veya tümünü bu kodu kendileri için teknolojisine bağlı olarak yazmak gerekli. Ancak, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , uygulama tanımının biçimlendirme dosya olarak yapılandırıldığında, bu kod sizin için oluşturur bir [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `ApplicationDefinition` , aşağıda gösterildiği gibi öğesi [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] proje dosyası:  
  
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
  
 Arka plan kod dosyası kod içerdiğinden olarak işaretlenmiş bir [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Compile` öğesi, normal olduğu gibi.  
  
 Bu uygulama [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] uygulama tanımı biçimlendirme ve arka plan kodu dosyaları için yapılandırmaları neden [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] aşağıdaki gibi kod oluşturmak için:  
  
 [!code-csharp[AppDefAugSnippets#AppDefAugCODE1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs#appdefaugcode1)]
 [!code-vb[AppDefAugSnippets#AppDefAugCODE1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb#appdefaugcode1)]  
[!code-csharp[AppDefAugSnippets#AppDefAugCODE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs#appdefaugcode2)]
[!code-vb[AppDefAugSnippets#AppDefAugCODE2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb#appdefaugcode2)]  
  
 Giriş noktası yöntemi içeren ek altyapı kodu ile uygulama tanımının Sonuç kodu güçlendirir `Main`. <xref:System.STAThreadAttribute> Özniteliği uygulanan `Main` yöntemi belirtmek için ana [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] için iş parçacığı [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamasıdır için gerekli olan bir STA iş parçacığı [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar. Çağrıldığında, `Main` yeni bir örneğini oluşturur `App` çağırmadan önce `InitializeComponent` olaylarını kaydetmek ve özelliklerini ayarlamak için yöntem biçimlendirme içinde uygulanır. Çünkü `InitializeComponent` oluşturulur, açıkça çağırın gerekmez `InitializeComponent` yaptığınız gibi bir uygulama tanımından <xref:System.Windows.Controls.Page> ve <xref:System.Windows.Window> uygulamaları. Son olarak, <xref:System.Windows.Application.Run%2A> yöntemi, uygulamayı başlatmak için çağrılır.  
  
<a name="Getting_the_Current_Application"></a>   
## <a name="getting-the-current-application"></a>Geçerli uygulamanın alma  
 Çünkü işlevselliğini <xref:System.Windows.Application> sınıfı bir uygulama arasında paylaşılan, yalnızca bir örneği olabilir <xref:System.Windows.Application> başına sınıf <xref:System.AppDomain>. Bu, zorlamak için <xref:System.Windows.Application> sınıfı bir singleton sınıfı uygulanan (bkz [uygulama Singleton C#](http://go.microsoft.com/fwlink/?LinkId=100567)), kendisini tek bir örneğini oluşturur ve sağlar ile erişimi paylaşılan `static` <xref:System.Windows.Application.Current%2A> özellik.  
  
 Aşağıdaki kod, bir başvuru edinmeye gösterilmektedir <xref:System.Windows.Application> nesnesi için geçerli <xref:System.AppDomain>.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]  
  
 <xref:System.Windows.Application.Current%2A>örneği için bir başvuru döndürür <xref:System.Windows.Application> sınıfı. Bir başvuru istiyorsanız, <xref:System.Windows.Application> türetilmiş sınıf değerini cast gerekir <xref:System.Windows.Application.Current%2A> aşağıdaki örnekte gösterildiği gibi özelliği.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]  
  
 Değerini inceleyebilirsiniz <xref:System.Windows.Application.Current%2A> ömrü herhangi bir noktada bir <xref:System.Windows.Application> nesnesi. Ancak, dikkatli olmanız gerekir. Sonra <xref:System.Windows.Application> sınıf örneği, bir dönemde durumunu <xref:System.Windows.Application> nesnesi tutarsız. Bu süre boyunca <xref:System.Windows.Application> uygulama altyapısını oluşturma, özelliklerini ayarlama ve olayları kaydetme gibi kodunuz tarafından çalıştırmak için gerekli olan çeşitli başlatma görevlerini gerçekleştirme. Kullanmayı denerseniz <xref:System.Windows.Application> nesne bu süre boyunca kodunuzu olabilir özellikle çeşitli bağımlı olması durumunda beklenmeyen sonuçlara <xref:System.Windows.Application> ayarlanan özellikleri.  
  
 Zaman <xref:System.Windows.Application> başlatma işini tamamlayıncaya yaşam gerçekten başlar.  
  
<a name="Application_Lifetime"></a>   
## <a name="application-lifetime"></a>Uygulama yaşam süresi  
 Yaşam süresi bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama tarafından gerçekleştirilen çeşitli olaylar tarafından işaretlenmiş <xref:System.Windows.Application> uygulamanızı ne zaman başlatıldığını, size bildirmek için olduğundan etkin ve devre dışı ve kapatıldı.  
  
  
<a name="Splash_Screen"></a>   
### <a name="splash-screen"></a>Giriş ekranı  
 İtibariyle [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], başlangıç penceresinde, kullanılacak bir görüntü belirtebilirsiniz veya *ekranı*. <xref:System.Windows.SplashScreen> Sınıfı, uygulama yüklenirken bir başlangıç penceresini görüntülemek kolaylaştırır. <xref:System.Windows.SplashScreen> Penceresi oluşturulur ve önce gösterilen <xref:System.Windows.Application.Run%2A> olarak adlandırılır. Daha fazla bilgi için bkz: [uygulama başlangıç zamanı](../../../../docs/framework/wpf/advanced/application-startup-time.md) ve [WPF uygulaması için bir giriş ekranı eklemek](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
<a name="Starting_an_Application"></a>   
### <a name="starting-an-application"></a>Uygulama başlatma  
 Sonra <xref:System.Windows.Application.Run%2A> olarak adlandırılır ve uygulama başlatılır, uygulamayı çalıştırmak hazır. Şu anda zaman belirtilir <xref:System.Windows.Application.Startup> olayı oluşturulur:  
  
 [!code-csharp[ApplicationStartupSnippets#StartupCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#startupcodebehind1)]
 [!code-vb[ApplicationStartupSnippets#StartupCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#startupcodebehind1)]  
[!code-csharp[ApplicationStartupSnippets#StartupCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#startupcodebehind2)]
[!code-vb[ApplicationStartupSnippets#StartupCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#startupcodebehind2)]  
  
 Bu noktada bir uygulamanın yaşam süresi yapmak için en yaygın göstermek için şeydir bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Showing_a_User_Interface"></a>   
### <a name="showing-a-user-interface"></a>Bir kullanıcı arabirimi gösterme  
 Çoğu tek başına [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] açık uygulamaları bir <xref:System.Windows.Window> zaman başlamak çalışıyor. <xref:System.Windows.Application.Startup> Olay işleyicisi aşağıdaki kodda gösterildiği gibi bunu yapabilirsiniz, tek bir konumda olduğundan.  
  
 [!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]  
  
 [!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
 [!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]  
  
> [!NOTE]
>  İlk <xref:System.Windows.Window> uygulama tek başına örneğinin oluşturulması için varsayılan olarak ana uygulama penceresi olur. Bu <xref:System.Windows.Window> nesnesi tarafından başvurulan <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> özelliği. Değeri <xref:System.Windows.Application.MainWindow%2A> özellik değiştirilebilir programlı olarak farklı bir pencere için değil, ilk örneği <xref:System.Windows.Window> ana penceresi olması gerekir.  
  
 Zaman bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ilk başlar, bunu büyük olasılıkla gidin bir <xref:System.Windows.Controls.Page>. Bu aşağıdaki kodda gösterilir.  
  
 [!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]  
  
 [!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
 [!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]  
  
 İşleme, <xref:System.Windows.Application.Startup> yalnızca açmak için bir <xref:System.Windows.Window> veya gitmek bir <xref:System.Windows.Controls.Page>, ayarlayabileceğiniz `StartupUri` biçimlendirme yerine özniteliği.  
  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Application.StartupUri%2A> açmak için bir tek başına uygulamasından bir <xref:System.Windows.Window>.  
  
 [!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]  
  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Application.StartupUri%2A> gelen bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] gitmek için bir <xref:System.Windows.Controls.Page>.  
  
 [!code-xaml[PageSnippets#XBAPStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]  
  
 Bu biçimlendirme bir pencerede açmak için önceki kod aynı etkiye sahiptir.  
  
> [!NOTE]
>  Gezinti hakkında daha fazla bilgi için bkz: [Gezinti genel bakış](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
 Ele almanız gerekir <xref:System.Windows.Application.Startup> olayı açmak için bir <xref:System.Windows.Window> varsayılan olmayan bir Oluşturucu kullanarak örneği oluşturmak gereken veya özelliklerini ayarlamak veya gösterilmeden önce kendi olaylarına abone olmak gereken veya herhangi bir komut satırı bağımsız değişkeni işlemek ihtiyacınız varsa, uygulama başlatıldığında sağlanmadı.  
  
<a name="Processing_Command_Line_Arguments"></a>   
### <a name="processing-command-line-arguments"></a>Komut satırı bağımsız değişkenleri işleme  
 İçinde [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)], bir komut istemi veya masaüstünden bağımsız uygulamalar başlatılabilir. Her iki durumda da, komut satırı bağımsız değişkenleri uygulamaya gönderilir. Tek bir komut satırı bağımsız değişkeniyle başlatılan bir uygulama aşağıdaki örnekte "/ StartMinimized":  
  
 `wpfapplication.exe /StartMinimized`  
  
 Uygulama başlatma sırasında [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] işletim sisteminden komut satırı bağımsız değişkenleri alır ve bunları geçirir <xref:System.Windows.Application.Startup> olay işleyicisi aracılığıyla <xref:System.Windows.StartupEventArgs.Args%2A> özelliği <xref:System.Windows.StartupEventArgs> parametresi. Almak ve aşağıdaki gibi kod kullanarak komut satırı bağımsız değişkenleri saklayın.  
  
 [!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]  
  
 [!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
 [!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]  
  
 Kod tanıtıcıları <xref:System.Windows.Application.Startup> denetlemek için olup olmadığını **/StartMinimized** komut satırı bağımsız değişkeni sağlanmadığından; bu durumda, ana penceresi açar bir <xref:System.Windows.WindowState> , <xref:System.Windows.WindowState.Minimized>. Çünkü unutmayın <xref:System.Windows.Window.WindowState%2A> özelliği ayarlanmalıdır programlı olarak, ana <xref:System.Windows.Window> kodda açıkça açılması gerekir.  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]alamaz ve kullanarak başlatılmaları olduğundan komut satırı bağımsız değişkenleri işleme [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] dağıtım (bkz [WPF uygulaması dağıtma](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)). Ancak, almak ve bunları başlatmak için kullanılan URL'leri sorgu dizesi parametreleri işlem.  
  
<a name="Application_Activation_and_Deactivation"></a>   
### <a name="application-activation-and-deactivation"></a>Uygulama etkinleştirme ve devre dışı bırakma  
 [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)]uygulamalar arasında geçiş yapmak kullanıcıların sağlar. En yaygın yolu ALT + SEKME tuş bileşimini kullanmaktır. Bir görünür varsa, uygulamanın yalnızca olarak değiştirilebilir <xref:System.Windows.Window> , bir kullanıcı seçebilirsiniz. Şu anda seçili <xref:System.Windows.Window> olan *etkin pencereyi* (olarak da bilinen *ön plan penceresi*) ve <xref:System.Windows.Window> kullanıcı girişini alır. Etkin pencereyi ile uygulama *etkin uygulama* (veya *ön plan uygulama*). Bir uygulama, aşağıdaki durumlarda etkin uygulama olur:  
  
-   Başlatılır ve gösteren bir <xref:System.Windows.Window>.  
  
-   Bir kullanıcı başka bir uygulamadan seçerek anahtarları bir <xref:System.Windows.Window> uygulamadaki.  
  
 Bir uygulama tarafından işleme etkin olduğunda algılayabilir <xref:System.Windows.Application.Activated?displayProperty=nameWithType> olay.  
  
 Benzer şekilde, bir uygulama, aşağıdaki durumlarda etkin hale gelebilir:  
  
-   Bir kullanıcı başka bir uygulama için geçerli makineden geçer.  
  
-   Uygulama zaman kapanır.  
  
 Bir uygulama tarafından işleme etkin olmadığında algılayabilir <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> olay.  
  
 Aşağıdaki kodu nasıl işleneceğini gösterir <xref:System.Windows.Application.Activated> ve <xref:System.Windows.Application.Deactivated> uygulama etkin olup olmadığını belirlemek için olaylar.  
  
 [!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]  
  
 [!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
 [!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]  
  
 A <xref:System.Windows.Window> da etkin ve devre dışı bırakıldı. Bkz: <xref:System.Windows.Window.Activated?displayProperty=nameWithType> ve <xref:System.Windows.Window.Deactivated?displayProperty=nameWithType> daha fazla bilgi için.  
  
> [!NOTE]
>  Ne <xref:System.Windows.Application.Activated?displayProperty=nameWithType> ya da <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> için tetiklenir [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Application_Shutdown"></a>   
### <a name="application-shutdown"></a>Uygulama kapatma  
 Aşağıdaki nedenlerle oluşabilen aşağı kapatıldığında uygulama ömrü sona erer:  
  
-   Bir kullanıcı kapatır her <xref:System.Windows.Window>.  
  
-   Bir kullanıcının ana kapattığı <xref:System.Windows.Window>.  
  
-   Bir kullanıcı sona [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] oturumu kapatmadan veya kapatılıyor.  
  
-   Bir uygulamaya özgü koşul karşılanır.  
  
 Uygulama kapatma yönetmenize yardımcı olmak için <xref:System.Windows.Application> sağlar <xref:System.Windows.Application.Shutdown%2A> yöntemi, <xref:System.Windows.Application.ShutdownMode%2A> özelliği ve <xref:System.Windows.Application.SessionEnding> ve <xref:System.Windows.Application.Exit> olaylar.  
  
> [!NOTE]
>  <xref:System.Windows.Application.Shutdown%2A>yalnızca sahip uygulamalardan çağrılabilir <xref:System.Security.Permissions.UIPermission>. Tek başına [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar her zaman bu izne sahip. Ancak, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] Internet bölgesi kısmi güven güvenlik korumalı alanda çalışan yapın.  
  
#### <a name="shutdown-mode"></a>Kapatma modu  
 Çoğu uygulama tüm windows kapatıldığı veya ana penceresi kapatıldığında aşağı kapatın. Bazı durumlarda, ancak diğer uygulamaya özgü koşulları ne zaman bir uygulama kapanır belirleyebilir. Altında uygulamanız kapatma ayarlayarak koşulları belirtebilirsiniz <xref:System.Windows.Application.ShutdownMode%2A> aşağıdakilerden biriyle <xref:System.Windows.ShutdownMode> numaralandırma değerlerinin:  
  
-   <xref:System.Windows.ShutdownMode.OnLastWindowClose>  
  
-   <xref:System.Windows.ShutdownMode.OnMainWindowClose>  
  
-   <xref:System.Windows.ShutdownMode.OnExplicitShutdown>  
  
 Varsayılan değer olan <xref:System.Windows.Application.ShutdownMode%2A> olan <xref:System.Windows.ShutdownMode.OnLastWindowClose>, uygulamanın son penceresinde kullanıcı tarafından kapatıldığında, bir uygulamanın otomatik olarak kapanması anlamına gelir. Ancak, uygulamanızın kapatılmalıdır varsa ne zaman ana penceresi kapatıldığında, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ayarlarsanız, otomatik olarak yapar <xref:System.Windows.Application.ShutdownMode%2A> için <xref:System.Windows.ShutdownMode.OnMainWindowClose>. Bu, aşağıdaki örnekte gösterilir.  
  
 [!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]  
  
 Uygulamaya özgü kapatma koşulları sahip olduğunuzda, ayarladığınız <xref:System.Windows.Application.ShutdownMode%2A> için <xref:System.Windows.ShutdownMode.OnExplicitShutdown>. Bu durumda, açıkça çağırarak bir uygulamayı kapatmak için sizin sorumluluğunuzdadır olan <xref:System.Windows.Application.Shutdown%2A> yöntemi; Aksi halde, uygulamanız tüm windows kapalı olsa bile çalışmaya devam edecek. Unutmayın <xref:System.Windows.Application.Shutdown%2A> örtük olarak ne zaman çağrıldığını <xref:System.Windows.Application.ShutdownMode%2A> ya <xref:System.Windows.ShutdownMode.OnLastWindowClose> veya <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
> [!NOTE]
>  <xref:System.Windows.Application.ShutdownMode%2A>ayarlanabilir bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], ancak göz ardı edilir; bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] her zaman, onu bir tarayıcı veya tarayıcı barındırdığında çıkıldığında zaman kapatılır [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kapalı. Daha fazla bilgi için bkz: [Gezinti genel bakış](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
#### <a name="session-ending"></a>Oturum bitiş  
 Tarafından açıklanan kapatma koşulları <xref:System.Windows.Application.ShutdownMode%2A> özelliği bir uygulamaya özgü. Bazı durumlarda, yine de bir uygulama sonucu olarak bir dış koşulu kapatılabilir. Bir kullanıcı sona erdiğinde en yaygın dış durum meydana gelir [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] oturumu aşağıdaki eylemleri tarafından:  
  
-   Oturum kapatma  
  
-   Kapatılıyor  
  
-   Yeniden başlatma  
  
-   Hazırda bekleme  
  
 Ne zaman algılamak için bir [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] oturumu sona erdiğinde işleyebilir <xref:System.Windows.Application.SessionEnding> aşağıdaki örnekte gösterildiği gibi olay.  
  
 [!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]  
  
 [!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
 [!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]  
  
 Bu örnekte, kodunu inceler <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> belirlemek için özellik nasıl [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] oturumu sona eren. Kullanıcıya bir onay iletisi görüntülemek için bu değeri kullanır. Kullanıcı oturumunu sona erdirmek için istemiyorsa kod ayarlar <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> için `true` önlemek için [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] bitiş oturumundan.  
  
> [!NOTE]
>  <xref:System.Windows.Application.SessionEnding>için oluşmaz [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
#### <a name="exit"></a>Çık  
 Bir uygulama kapatıldığında kalıcı uygulama durumu gibi bazı son işlemler gerçekleştirmek gerekebilir. Bu durumlarda, işleyebilir <xref:System.Windows.Application.Exit> olay.  
  
 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml#persistrestoreappscopepropertiesxaml1)]  
[!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml#persistrestoreappscopepropertiesxaml2)]  
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs#persistappscopepropertiescodebehind1)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistappscopepropertiescodebehind1)]  
[!code-csharp[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs#persistappscopepropertiescodebehind2)]
[!code-vb[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistappscopepropertiescodebehind2)]  
  
 Tam bir örnek için bkz: [kalan ve geri yükleme uygulama kapsam özellikleri arasında uygulama oturumları](../../../../docs/framework/wpf/app-development/persist-and-restore-application-scope-properties.md).  
  
 <xref:System.Windows.Application.Exit>Her iki tek başına uygulamalar tarafından yönetilebilir ve [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. İçin [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], <xref:System.Windows.Application.Exit> olduğunda aşağıdaki durumlarda tetiklenir:  
  
-   Bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] sayfadan çıkıldığında.  
  
-   İçinde [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)], barındıran sekmesini [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kapalı.  
  
-   Tarayıcı kapatıldığında.  
  
#### <a name="exit-code"></a>Çıkış kodu  
 Uygulamaları, genellikle bir kullanıcı isteğine yanıt olarak işletim sistemi tarafından başlatılır. Ancak, bir uygulamanın belirli bir görevi gerçekleştirmek için başka bir uygulama tarafından başlatılabilir. Başlatılan uygulama kapatıldığında başlatan uygulamanın altında başlatılan uygulama kapatma koşul bilmek isteyebilirsiniz. Bu gibi durumlarda [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] kapanışında uygulama çıkış kodu döndürülecek uygulamaları sağlar. Varsayılan olarak, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamaları 0 çıkış kodu değerini döndürür.  
  
> [!NOTE]
>  Debug zaman [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], uygulama çıkış kodu görüntülenir **çıkış** uygulama, aşağıdaki gibi görünen bir ileti kapatır zaman penceresi:  
>   
>  `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`  
>   
>  Açtığınız **çıkış** tıklatarak penceresi **çıkış** üzerinde **Görünüm** menüsü.  
  
 Çıkış kodu değiştirmek için çağırabilirsiniz <xref:System.Windows.Application.Shutdown%28System.Int32%29> aşırı yükleme, hangi çıkış kodu olacak şekilde bir tamsayı bağımsız değişkeni kabul eder:  
  
 [!code-csharp[ApplicationExitSnippets#AppExitCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
 [!code-vb[ApplicationExitSnippets#AppExitCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]  
  
 Çıkış kodu değerini algılayabilir ve işleyerek değiştirmek <xref:System.Windows.Application.Exit> olay. <xref:System.Windows.Application.Exit> Olay işleyicisine geçirilir bir <xref:System.Windows.ExitEventArgs> çıkış kodu ile erişim sağlayan <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> özelliği. Daha fazla bilgi için bkz. <xref:System.Windows.Application.Exit>.  
  
> [!NOTE]
>  Çıkış kodu her iki tek başına uygulamaları olarak ayarlayın ve [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Ancak, çıkış kodu değerini için göz ardı edilir [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Unhandled_Exceptions"></a>   
### <a name="unhandled-exceptions"></a>İşlenmeyen özel durumlar  
 Bazen bir uygulamanın ne zaman bir beklenmeyen özel durum gibi aşağı altında anormal koşullar kapatın. Bu durumda, uygulama algılama ve özel durum işleme için kodu olmayabilir. Bu özel durum işlenmeyen bir özel durum türüdür; Uygulama kapatılmadan önce aşağıdaki resimde gösterilen benzer bir bildirim görüntülenir.  
  
 ![İşlenmeyen özel durum bildirimini](../../../../docs/framework/wpf/app-development/media/applicationmanagementoverviewfigure2.png "ApplicationManagementOverviewFigure2")  
  
 Kullanıcı deneyimi açısından daha iyi bir uygulamanın bazı veya tüm birini yaparak bu varsayılan davranışı önlemek:  
  
-   Kullanıcı dostu bilgilerini görüntüleme.  
  
-   Çalışan bir uygulamaya devam etme girişimi.  
  
-   Ayrıntılı, geliştirici dostu, özel durum bilgileri kaydı [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] olay günlüğü.  
  
 Bu destek uygulama bağlıdır işlenmeyen özel durumları algılayabilir olan ne olduğu <xref:System.Windows.Application.DispatcherUnhandledException> olayı için oluşturulur.  
  
 [!code-xaml[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]  
  
 [!code-csharp[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs#handledispatcherunhandledexceptioncodebehind1)]
 [!code-vb[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb#handledispatcherunhandledexceptioncodebehind1)]  
[!code-csharp[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs#handledispatcherunhandledexceptioncodebehind2)]
[!code-vb[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb#handledispatcherunhandledexceptioncodebehind2)]  
  
 <xref:System.Windows.Application.DispatcherUnhandledException> Olay işleyicisine geçirilir bir <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> özel durum kendisi de dahil olmak üzere işlenmeyen özel durumla ilgili bağlamsal bilgileri içeren parametre (<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>). Özel durumun ne yapılacağını belirlemek için bu bilgileri kullanın.  
  
 Ne zaman işleneceğini <xref:System.Windows.Application.DispatcherUnhandledException>, ayarlamanız gerekir <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType> özelliğine `true`; Aksi halde, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] hala işlenmemiş olması için özel durum olarak değerlendirir ve daha önce açıklanan varsayılan davranışa geri döner. İşlenmeyen bir özel durum oluşursa ve her iki <xref:System.Windows.Application.DispatcherUnhandledException> olay işlenmiyor veya olay işlenir ve <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> ayarlanır `false`, uygulama hemen kapatılır. Ayrıca, başka <xref:System.Windows.Application> olayları ortaya çıkar. Sonuç olarak, işlemek gereken <xref:System.Windows.Application.DispatcherUnhandledException> uygulamanızın uygulama kapatılmadan önce çalıştırmanız gereken kodu varsa.  
  
 Bir uygulama işlenmeyen bir özel durum nedeniyle kapanabilir rağmen uygulama genellikle bir kullanıcı isteğine yanıt olarak sonraki bölümde açıklandığı gibi kapanır.  
  
<a name="Application_Lifetime_Events"></a>   
### <a name="application-lifetime-events"></a>Uygulama yaşam süresi olayları  
 Bağımsız uygulamalar ve [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] tam olarak aynı yaşam süresi yok. Aşağıdaki şekilde bir tek başına uygulama yaşam süresi anahtar olayları gösterir ve ortaya çıkar dizisini gösterir.  
  
 ![Tek başına uygulama &#45; Uygulama nesnesi olayları](../../../../docs/framework/wpf/app-development/media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")  
  
 Benzer şekilde, aşağıdaki şekilde yaşam süresi anahtar olayları gösterilmektedir bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]ve bunlar yükseltilmiş gösterilir.  
  
 ![XBAP &#45; Uygulama nesnesi olayları](../../../../docs/framework/wpf/app-development/media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Application>  
 [WPF Windows genel bakış](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md)  
 [Gezinti genel bakış](../../../../docs/framework/wpf/app-development/navigation-overview.md)  
 [WPF Uygulama kaynağı, içerik ve veri dosyaları](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)  
 [WPF içinde URI'leri paketleme](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Uygulama modeli: Nasıl Yapılır Konuları](http://msdn.microsoft.com/en-us/76771b09-3688-4d1c-8818-9b3f4cf39a30)  
 [Uygulama geliştirme](../../../../docs/framework/wpf/app-development/index.md)
