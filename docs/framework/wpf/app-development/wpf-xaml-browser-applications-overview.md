---
title: "WPF XAML Tarayıcı Uygulamalarına Genel Bakış"
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
- XBAP [WPF], XAML browser application
- WPF XAML browser applications (XBAP)
- XAML browser applications (XBAP)
- browser-hosted applications [WPF]
ms.assetid: 3a7a86a8-75d5-4898-96b9-73da151e5e16
caps.latest.revision: "47"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f4f410f0f6c209dbc43642a15ae85a788390f4a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="wpf-xaml-browser-applications-overview"></a>WPF XAML Tarayıcı Uygulamalarına Genel Bakış
<a name="introduction"></a>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]Web uygulamaları ve zengin istemci uygulamaları özelliklerini bir araya getirir. Web uygulamaları gibi XBAP bir Web sunucusuna dağıtılır ve Internet Explorer ya da Firefox başlatıldı. Zengin istemci uygulamaları gibi yararlanabilir özelliklerini XBAP [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. XBAP geliştirme de zengin istemci geliştirme benzer. Bu konu XBAP geliştirme basit, üst düzey bir giriş sağlar ve burada XBAP geliştirme standart zengin istemci geliştirme farklı açıklar.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Yeni bir XAML tarayıcısı uygulaması (XBAP) oluşturuluyor](#creating_a_new_xaml_browser_application_xbap)  
  
-   [Bir XBAP dağıtma](#deploying_a_xbap)  
  
-   [Ana bilgisayar Web sayfası ile iletişim](#communicating_with_the_host_web_page)  
  
-   [XBAP güvenlik konuları](#xbap_security_considerations)  
  
-   [XBAP başlangıç zamanı performans etkenleri](#xbap_start_time_performance_considerations)  
  
<a name="creating_a_new_xaml_browser_application_xbap"></a>   
## <a name="creating-a-new-xaml-browser-application-xbap"></a>Yeni bir XAML tarayıcısı uygulaması (XBAP) oluşturuluyor  
 Yeni bir XBAP projesi oluşturmak için en basit yolu [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)]. Yeni bir proje oluştururken seçin **WPF tarayıcı uygulaması** şablonları listesinden. Daha fazla bilgi için bkz: [nasıl yapılır: yeni bir WPF tarayıcı uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/72ef4d90-e163-42a1-8df0-ea7ccfd1901f).  
  
 XBAP proje çalıştırdığınızda, tek başına bir pencere yerine bir tarayıcı penceresinde açar. Debug zaman gelen XBAP [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], uygulama Internet bölgesi izniyle çalıştırır ve bu nedenle bu izinleri aşılırsa güvenlik özel durumları durum oluşturur. Daha fazla bilgi için bkz: [güvenlik](../../../../docs/framework/wpf/security-wpf.md) ve [WPF kısmi güven güvenlik](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
> [!NOTE]
>  İle geliştirmiyorsanız [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] veya istediğiniz proje dosyaları hakkında daha fazla bilgi için bkz: [WPF uygulaması oluşturma](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).  
  
<a name="deploying_a_xbap"></a>   
## <a name="deploying-an-xbap"></a>Bir XBAP dağıtma  
 Bir XBAP derlerken çıkış aşağıdaki üç dosyalarını içerir:  
  
|Dosya|Açıklama|  
|----------|-----------------|  
|Yürütülebilir dosyanın (.exe)|Bu derlenmiş kodunu içerir ve .exe uzantısına sahip.|  
|Uygulama bildirimi (.manifest)|Bu uygulama ile ilişkili meta verileri içerir ve bir .manifest uzantısına sahiptir.|  
|Dağıtım bildirimi (.xbap)|Bu dosya bilgilerini içerir, [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] uygulamayı dağıtmak için kullanır ve .xbap uzantısına sahiptir.|  
  
 XBAP Web sunucusuna, örneğin dağıttığınız [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] veya sonraki sürümler. Yükleme gerekmez [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] Web sunucusu, ancak sahip kaydetmek [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] türlerini ve dosya adı uzantıları. Daha fazla bilgi için bkz: [yapılandırma IIS 5.0 ve IIS 6. 0'wpf uygulamaları dağıtmak için](../../../../docs/framework/wpf/app-development/how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md).  
  
 XBAP'ınız dağıtımına hazırlanmak için .exe ve ilişkili bildirimleri Web sunucusuna kopyalayın. .Xbap uzantısına sahip olan dosya dağıtım bildirimini açmak için köprü içeren bir HTML sayfası oluşturun. Kullanıcı .xbap dosyasını bağlantısını tıklattığında [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] otomatik olarak karşıdan yükleme ve uygulamayı başlatmayı mekanizması işler. Aşağıdaki örnek kod bir XBAP işaret eden bir köprü içeren bir HTML sayfası gösterilir.  
  
```html
<html>   
    <head></head>  
    <body>   
        <a href="XbapEx.xbap">Click this link to launch the application</a>  
    </body>   
</html>  
```  
  
 Ayrıca, bir Web sayfasının çerçevesinde bir XBAP barındırabilir. Bir Web sayfası bir veya daha fazla çerçeveler ile oluşturun. Bir çerçeve kaynak özelliğini dağıtım bildirim dosyası ayarlayın. Barındırma Web sayfası ve XBAP arasında iletişim kurmak için yerleşik mekanizmasını kullanmak istiyorsanız, uygulama bir çerçeve içinde ana bilgisayar gerekir. Aşağıdaki kod örneği, ikinci çerçevesi kaynağı bir XBAP ayarlanır iki çerçeve içeren bir HTML sayfası gösterir.  
  
```html
<html>   
    <head>
        <title>A page with frames</title>
    </head>  
    <frameset cols="50%,50%">   
        <frame src="introduction.htm">   
        <frame src="XbapEx.xbap">   
    </frameset>   
</html>  
```  
  
### <a name="clearing-cached-xbaps"></a>XBAP temizleme önbelleğe  
 Yeniden oluşturma ve başlatma, XBAP sonra bazı durumlarda, XBAP önceki bir sürümünü açıldığında bulabilirsiniz. Örneğin, bu davranış, XBAP derleme sürüm numarası statik olduğunda ve XBAP komut satırından başlatmak ortaya çıkabilir. Bu durumda, önbelleğe alınan sürüm (daha önce başlatıldı sürüm) ve yeni sürümü arasında sürüm numarası aynı kalır çünkü XBAP yeni sürümünü indirilmez. Bunun yerine, önbelleğe alınan sürümü yüklenir.  
  
 Bu durumlarda, önbelleğe alınan sürüm kullanarak kaldırabilirsiniz **Mage** komutu (Visual Studio ile yüklü veya [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)]) komut isteminde. Aşağıdaki komut, uygulama önbelleği temizler.  
  
 ```console
 Mage.exe -cc
 ```
  
 Bu komut, XBAP en son sürümünü başlatıldığını güvence altına alır. Uygulamanızda hata ayıklama zaman, [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], en son sürümünü, XBAP başlatılmalıdır. Genel olarak, her bir yapı ile dağıtım sürüm numarasını güncelleştirmeniz gerekir. Mage hakkında daha fazla bilgi için bkz: [Mage.exe (bildirim üretme ve düzenleme aracı)](../../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
<a name="communicating_with_the_host_web_page"></a>   
## <a name="communicating-with-the-host-web-page"></a>Ana bilgisayar Web sayfası ile iletişim  
 Uygulama bir HTML çerçevesinde barındırıldığında XBAP içeren Web sayfasını ile iletişim kurabilir. Alarak bunu <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> özelliği <xref:System.Windows.Interop.BrowserInteropHelper>. Bu özellik HTML pencereyi temsil eden bir komut dosyası nesnesi döndürür. Üzerinde özellikleri, yöntemleri ve olayları daha sonra erişebilirsiniz [pencere nesnesi](http://go.microsoft.com/fwlink/?LinkId=160274) normal nokta sözdizimini kullanarak. Komut dosyası yöntemleri ve genel değişkenler de erişebilirsiniz. Aşağıdaki örnekte, komut dosyası nesnesi almak ve tarayıcıyı kapatın gösterilmektedir.  
  
 [!code-csharp[XbapBrowserInterop#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/xbapbrowserinterop/cs/page1.xaml.cs#10)]
 [!code-vb[XbapBrowserInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/xbapbrowserinterop/vb/page1.xaml.vb#10)]  
  
### <a name="debugging-xbaps-that-use-hostscript"></a>HostScript kullanmak XBAP hata ayıklama  
 XBAP'ınız kullanıyorsa <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> iletişim kurmak için HTML penceresiyle belirtmeniz gerekir iki ayarı vardır nesne çalıştırmak ve uygulamada hata ayıklama için [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]. Uygulama kaynağı, kendi sitesine erişiminiz olmalıdır ve uygulama XBAP içeren HTML sayfası ile başlamalıdır. Aşağıdaki adımlar, bu iki ayar denetlemek açıklanmaktadır:  
  
1.  Visual Studio Proje özelliklerini açın.  
  
2.  Üzerinde **güvenlik** sekmesini tıklatın, **Gelişmiş**.  
  
     Gelişmiş Güvenlik Ayarları iletişim kutusu görüntülenir.  
  
3.  Olduğundan emin olun **kaynak siteye uygulama erişim** kutunun işaretli denetleyin ve ardından **Tamam**.  
  
4.  Üzerinde **hata ayıklama** sekmesine **başlangıç tarayıcı URL ile** seçeneği ve XBAP içeren HTML sayfası URL'si belirtin.  
  
5.  Internet Explorer'daki **Araçları** düğmesine tıklayın ve ardından **Internet Seçenekleri**.  
  
     Internet Seçenekleri iletişim kutusu görüntülenir.  
  
6.  Tıklatın **Gelişmiş** sekmesi.  
  
7.  İçinde **ayarları** altında listesinde **güvenlik**, denetleyin **etkin içeriğin Bilgisayarım üzerindeki dosyalarda çalışmasına izin** onay kutusu.  
  
8.  **Tamam**'ı tıklatın.  
  
     Internet Explorer'ı yeniden sonra değişiklikler etkili.  
  
> [!CAUTION]
>  Internet Explorer'da etkin içerik etkinleştirme bilgisayarınızı riske atabilir. Daha fazla bilgi için bkz: [Internet Explorer güvenlik ve gizlilik özelliklerini](http://go.microsoft.com/fwlink/?LinkId=179286). Internet Explorer güvenlik ayarlarınızı değiştirmek istemiyorsanız, bir sunucudan HTML sayfası başlatın ve attach [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] hata ayıklayıcı işlem.  
  
<a name="xbap_security_considerations"></a>   
## <a name="xbap-security-considerations"></a>XBAP güvenlik konuları  
 XBAP genellikle Internet bölgesi izin kümesi kısıtlı bir kısmi güven güvenlik sandbox yürütün. Sonuç olarak, uygulamanızı alt kümesini desteklemelidir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Internet bölgesi veya, desteklenen öğeleri uygulamanızın izinlerini yükseltmesine gerekir. Daha fazla bilgi için bkz: [güvenlik](../../../../docs/framework/wpf/security-wpf.md).  
  
 Kullandığınızda, bir <xref:System.Windows.Controls.WebBrowser> WPF uygulamanızı denetiminde dahili olarak yerel WebBrowser ActiveX denetimini başlatır. Uygulamanızı Internet Explorer'da çalışmasını kısmi güven XBAP olduğunda, ActiveX denetimini Internet Explorer işlemi adanmış iş parçacığı içinde çalışır. Bu nedenle, aşağıdaki sınırlamalar uygulanır:  
  
-   <xref:System.Windows.Controls.WebBrowser> Denetim davranış güvenlik kısıtlamaları da dahil olmak üzere ana tarayıcıya benzer temin etmelidir. Bu güvenlik kısıtlamaları bazıları aracılığıyla Internet Explorer güvenlik ayarlarını denetlenebilir. Daha fazla bilgi için bkz: [güvenlik](../../../../docs/framework/wpf/security-wpf.md).  
  
-   Bir XBAP yüklenen etki alanları arası bir HTML sayfasında olduğunda özel durum oluşur.  
  
-   WPF ayrı bir iş parçacığından açıktır giriş <xref:System.Windows.Controls.WebBrowser>, böylece klavye girişi olamaz ele ve IME durumu paylaşılmaz.  
  
-   Zamanlama veya gezinme sırasını başka bir iş parçacığı üzerinde çalışan ActiveX denetimini nedeniyle farklı olabilir. Örneğin, bir sayfasına giderek her zaman başka bir gezinti isteğini başlatarak iptal değil.  
  
-   WPF uygulaması ayrı bir iş parçacığı çalıştığından özel bir ActiveX denetimi ile iletişim sorunlarla karşılaşabilirsiniz.  
  
-   <xref:System.Windows.Interop.HwndHost.MessageHook>çünkü gerçekleşmedi <xref:System.Windows.Interop.HwndHost> başka bir iş parçacığı veya işlem çalıştıran bir pencereyi alt sınıf olamaz.  
  
### <a name="creating-a-full-trust-xbap"></a>Tam güven XBAP oluşturma  
 XBAP'ınız tam güven gerektiriyorsa, bu izni etkinleştirmek için projenizi değiştirebilirsiniz. Aşağıdaki adımlar, tam güven etkinleştirmek açıklanmaktadır:  
  
1.  Visual Studio Proje özelliklerini açın.  
  
2.  Üzerinde **güvenlik** sekmesine **tam güven uygulamasıdır** seçeneği.  
  
 Bu ayar, aşağıdaki değişiklikleri yapar:  
  
-   Proje dosyasında `<TargetZone>` öğe değeri değiştirildi `Custom`.  
  
-   (App.manifest), uygulama bildiriminde bir `Unrestricted="true"` özniteliği eklenir `PermissionSet` öğesi.  
  
    ```xml
    <PermissionSet class="System.Security.PermissionSet"   
                   version="1"   
                   ID="Custom"   
                   SameSite="site"   
                   Unrestricted="true" />  
    ```  
  
### <a name="deploying-a-full-trust-xbap"></a>Tam güven XBAP dağıtma  
 ClickOnce güvenilen dağıtım modeli izlemez tam güven XBAP dağıttığınızda, kullanıcı uygulamayı çalıştırdığında davranışı güvenlik bölgesine bağlı olacaktır. Yüklemeye çalıştığınızda bazı durumlarda, kullanıcı bir uyarı alırsınız. Kullanıcı, yükleme devam etmek seçebilirsiniz. Aşağıdaki tabloda her güvenlik bölgesi ve uygulama tam güven almak yapmanız gereken uygulamanın davranışını tanımlar.  
  
|Güvenlik Bölgesi|Davranış|Tam güven alma|  
|-------------------|--------------|------------------------|  
|Yerel bilgisayar|Otomatik tam güven|Eylem gerekmiyor.|  
|İntranet ve Güvenilen siteler|Tam güven istemi|Kullanıcı istemi kaynağında görebilmesi için XBAP bir sertifika ile oturum açın.|  
|Internet|"Güven yazma izni" ile başarısız oluyor|XBAP bir sertifika ile oturum açın.|  
  
> [!NOTE]
>  Yukarıdaki tabloda açıklanan ClickOnce güvenilen dağıtım modeli izlemeyin tam güven XBAP davranıştır.  
  
 Tam güven XBAP dağıtmak için ClickOnce güvenilen dağıtım modeli kullanmanız önerilir. Böylece kullanıcıdan istekte bulunulmaz XBAP'ınız tam güven otomatik olarak güvenlik bölgesi'ne olursa olsun verilebilmesi bu modeli sağlar. Bu modelin bir parçası olarak, bir sertifika ile uygulamanızı güvenilir bir yayımcıdan oturum açmanız gerekir. Daha fazla bilgi için bkz: [güvenilir uygulama dağıtımına genel bakış](/visualstudio/deployment/trusted-application-deployment-overview) ve [kod imzalama giriş](http://go.microsoft.com/fwlink/?LinkId=166327).  
  
<a name="xbap_start_time_performance_considerations"></a>   
## <a name="xbap-start-time-performance-considerations"></a>XBAP başlangıç zamanı performans etkenleri  
 Bir önemli XBAP performans başlangıç saatinden yönüdür. Bir XBAP yüklemek için ilk WPF uygulaması ise *cold start* zaman on saniye veya daha fazla olabilir. İlerleme durumu sayfası WPF tarafından işlenir ve CLR ve WPF soğuk-uygulamayı görüntülemek için başlatılması gerekir çünkü budur.  
  
 İtibariyle [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], XBAP soğuk başlangıç zamanı dağıtım döngüsünde erken bir yönetilmeyen ilerleme durumu sayfası görüntüleyerek getirdiği. İlerleme durumu sayfası hemen görünür olduğundan ve yerel barındırma kodu tarafından görüntülenen HTML olarak işlenen uygulamanın başlatılmasından sonra.  
  
 Ayrıca, eşzamanlılığı geliştirilmiş [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] yükleme sırası yüzde on tarafından başlangıç zamanı artırır. Sonra [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] indirir ve bildirimleri, uygulama yükleme başlar ve güncelleştirmek için ilerleme çubuğu başlatır doğrular.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Web Hizmeti Çağırmak Amacıyla XAML Tarayıcı Uygulamasında Hata Ayıklamak için Visual Studio'yu Yapılandırma](../../../../docs/framework/wpf/app-development/configure-vs-to-debug-a-xaml-browser-to-call-a-web-service.md)  
 [WPF Uygulaması Dağıtma](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)
