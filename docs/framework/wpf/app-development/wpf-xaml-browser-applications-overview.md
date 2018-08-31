---
title: WPF XAML Tarayıcı Uygulamalarına Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XBAP [WPF], XAML browser application
- WPF XAML browser applications (XBAP)
- XAML browser applications (XBAP)
- browser-hosted applications [WPF]
ms.assetid: 3a7a86a8-75d5-4898-96b9-73da151e5e16
ms.openlocfilehash: cdd636a1854b891605abadaf31b1667e235eea92
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43253204"
---
# <a name="wpf-xaml-browser-applications-overview"></a>WPF XAML Tarayıcı Uygulamalarına Genel Bakış
<a name="introduction"></a>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] hem Web uygulamaları hem de zengin istemci uygulamaları özelliklerini bir araya getirir. Web uygulamaları gibi XBAP'ler bir Web sunucusuna dağıtılabilir ve Internet Explorer ya da Firefox başlatıldı. Zengin istemci uygulamaları gibi XBAP'ler WPF yeteneklerinden yararlanabilirsiniz. XBAP'ler geliştirme da zengin istemci geliştirme ile benzerdir. Bu konu, XBAP geliştirme basit, yüksek düzeyde bir giriş sağlar ve burada XBAP geliştirme standart zengin istemci geliştirme farklı açıklar.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Yeni bir XAML tarayıcı uygulaması (XBAP) oluşturma](#creating_a_new_xaml_browser_application_xbap)  
  
-   [Bir XBAP dağıtma](#deploying_a_xbap)  
  
-   [Konak Web sayfası ile iletişim kurma](#communicating_with_the_host_web_page)  
  
-   [XBAP güvenlik konuları](#xbap_security_considerations)  
  
-   [XBAP başlangıç zamanı performans konuları](#xbap_start_time_performance_considerations)  
  
<a name="creating_a_new_xaml_browser_application_xbap"></a>   
## <a name="creating-a-new-xaml-browser-application-xbap"></a>Yeni bir XAML tarayıcı uygulaması (XBAP) oluşturma  
 Microsoft Visual Studio ile yeni bir XBAP projesi oluşturmak için en basit yoludur. Yeni bir proje oluştururken **WPF tarayıcı uygulaması** şablonları listesinden. Daha fazla bilgi için [nasıl yapılır: yeni bir WPF tarayıcı uygulaması projesi oluşturma](http://msdn.microsoft.com/library/72ef4d90-e163-42a1-8df0-ea7ccfd1901f).  
  
 XBAP projesinin çalıştırdığınızda, tek başına bir pencereyi yerine bir tarayıcı penceresinde açılır. XBAP Visual Studio'dan hata ayıklaması yaparken uygulama Internet bölgesi izinle çalışır ve bu nedenle bu izinleri aşılırsa güvenlik özel durum oluşturur. Daha fazla bilgi için [güvenlik](../../../../docs/framework/wpf/security-wpf.md) ve [WPF kısmi güven güvenliği](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
> [!NOTE]
>  Visual Studio ya da proje dosyaları hakkında daha fazla bilgi edinmek istiyorsanız ile geliştirmiyorsanız bkz [WPF uygulaması oluşturma](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).  
  
<a name="deploying_a_xbap"></a>   
## <a name="deploying-an-xbap"></a>Bir XBAP dağıtma  
 Çıkış, bir XBAP yapılandırdığınızda, aşağıdaki üç dosyayı içerir:  
  
|Dosya|Açıklama|  
|----------|-----------------|  
|Yürütülebilir (.exe)|Bu, derlenmiş kodunu içerir ve .exe uzantısına sahiptir.|  
|Uygulama bildirimi (.manifest)|Bu uygulama ile ilişkili meta verileri içerir ve bir .manifest uzantısına sahiptir.|  
|Dağıtım bildirimi (.xbap)|Bu dosya, ClickOnce uygulamayı dağıtmak için kullanır ve .xbap uzantısı olan bilgileri içerir.|  
  
 XBAP'ler için bir Web sunucusu, örneğin dağıttığınız [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] veya sonraki sürümler. .NET Framework Web sunucusuna yüklemeniz gerekmez, ancak kaydetmek zorunda [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] türlerini ve dosya adı uzantıları. Daha fazla bilgi için [yapılandırma IIS 5.0 ve IIS 6. 0'wpf uygulamalarını dağıtmak için](../../../../docs/framework/wpf/app-development/how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md).  
  
 Bir XBAP dağıtımına hazırlanmak için .exe ve ilişkili bildirimler Web sunucusuna kopyalayın. .Xbap uzantılı dosya dağıtım bildirimini açmak için bir köprü içeren bir HTML sayfası oluşturun. Kullanıcı .xbap dosyasına bağlantıyı tıklattığında, ClickOnce, indirme ve uygulama başlatılırken mekanizması otomatik olarak işler. Aşağıdaki kod örneği, bir XBAP için işaret eden bir köprü içeren bir HTML sayfası gösterilir.  
  
```html
<html>   
    <head></head>  
    <body>   
        <a href="XbapEx.xbap">Click this link to launch the application</a>  
    </body>   
</html>  
```  
  
 Ayrıca, bir XBAP çerçevesinde bir Web sayfasının barındırabilirsiniz. Bir veya daha fazla çerçeve ile bir Web sayfası oluşturun. Source özelliği bir çerçeve, dağıtım bildirimi dosyası ayarlayın. Barındırma Web sayfası ve XBAP arasında iletişim kurmak için yerleşik bir mekanizma kullanmak istiyorsanız, uygulama bir çerçeve içinde barındırması gerekir. Aşağıdaki kod örneği ikinci çerçevesi için kaynak bir XBAP için ayarlanmış bir HTML sayfasına iki çerçevelerle gösterir.  
  
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
  
### <a name="clearing-cached-xbaps"></a>Temizleme XBAP'ler önbelleğe alınır.  
 Yeniden oluşturma ve başlatma, bir XBAP sonra bazı durumlarda, XBAP önceki bir sürümünü açıldığını fark edebilirsiniz. Örneğin, bu davranış, XBAP derleme sürüm numarası statiktir ve komut satırından XBAP başlattığınız ortaya çıkabilir. Bu durumda, önbelleğe alınmış sürümünü (daha önce başlatıldı sürüm) ve yeni sürümü arasında sürüm numarası aynı kaldığından XBAP yeni sürümü yüklenmedi. Bunun yerine, önbelleğe alınan sürümü yüklenir.  
  
 Bu durumda, önbelleğe alınmış sürümünü kullanarak kaldırabilirsiniz **Mage** komut isteminde (Visual Studio veya Windows SDK'sı ile yüklenen) komutu. Aşağıdaki komut, uygulama önbelleğini temizler.  
  
 ```console
 Mage.exe -cc
 ```
  
 Bu komut, bir XBAP en son sürümünü başlatıldığını garanti eder. Uygulamanızı Visual Studio'da hata ayıklaması yaparken, bir XBAP en son sürümünü başlatılmalıdır. Genel olarak, her derleme ile dağıtım sürüm numaranızı güncelleştirmeniz gerekir. Görüntü hakkında daha fazla bilgi için bkz: [Mage.exe (bildirim üretme ve düzenleme aracı)](../../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
<a name="communicating_with_the_host_web_page"></a>   
## <a name="communicating-with-the-host-web-page"></a>Konak Web sayfası ile iletişim kurma  
 Uygulama bir HTML çerçeve içinde barındırıldığında, XBAP içeren Web sayfasını ile iletişim kurabilir. Alarak bunu <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> özelliği <xref:System.Windows.Interop.BrowserInteropHelper>. Bu özellik için HTML pencereyi temsil eden bir komut dosyası nesnesi döndürür. Üzerinde özelliklerini, yöntemlerini ve olaylarını daha sonra erişebilirsiniz [pencere nesnesi](http://go.microsoft.com/fwlink/?LinkId=160274) normal nokta sözdizimini kullanarak. Betik yöntemleri ve genel değişkenler de erişebilirsiniz. Aşağıdaki örnek komut dosyası nesnesi alma ve tarayıcıyı kapatın gösterir.  
  
 [!code-csharp[XbapBrowserInterop#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/xbapbrowserinterop/cs/page1.xaml.cs#10)]
 [!code-vb[XbapBrowserInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/xbapbrowserinterop/vb/page1.xaml.vb#10)]  
  
### <a name="debugging-xbaps-that-use-hostscript"></a>HostScript kullanan Xbap'lerde hata ayıklama  
 Bir XBAP kullanıyorsa <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> nesne iletişim kurmak için HTML penceresiyle çalıştırmak ve Visual Studio'da uygulamada hata ayıklamak için belirtmeniz gereken iki ayar vardır. Uygulama erişimi gulamaya için olmalıdır ve uygulama XBAP içeren HTML sayfası ile başlamalıdır. Aşağıdaki adımlar bu iki ayar denetlemek nasıl açıklanmaktadır:  
  
1.  Visual Studio'da proje özelliklerini açın.  
  
2.  Üzerinde **güvenlik** sekmesinde **Gelişmiş**.  
  
     Gelişmiş Güvenlik Ayarları iletişim kutusu görüntülenir.  
  
3.  Emin olun **gulamaya erişim izni** kutunun işaretli denetleyin ve ardından **Tamam**.  
  
4.  Üzerinde **hata ayıklama** sekmesinde **Başlat tarayıcı URL ile** seçenek ve XBAP içeren HTML sayfasının URL'sini belirtin.  
  
5.  Internet Explorer'da tıklayın **Araçları** düğmesine ve ardından **Internet Seçenekleri**.  
  
     Internet Seçenekleri iletişim kutusu görüntülenir.  
  
6.  Tıklayın **Gelişmiş** sekmesi.  
  
7.  İçinde **ayarları** altında listesinde **güvenlik**, kontrol **Bilgisayarım dosyalarda çalıştırmak etkin içeriğe izin ver** onay kutusu.  
  
8.  **Tamam**'ı tıklatın.  
  
     Internet Explorer'ı yeniden sonra değişiklikler geçerli olacaktır.  
  
> [!CAUTION]
>  Internet Explorer'da etkin içerik etkinleştirme bilgisayarınızı riske atabilir. Internet Explorer güvenlik ayarlarınızı değiştirmek istemiyorsanız, bir sunucudan HTML sayfasını başlatmak ve Visual Studio hata ayıklayıcısını İliştir.  
  
<a name="xbap_security_considerations"></a>   
## <a name="xbap-security-considerations"></a>XBAP güvenlik konuları  
 XBAP'ler genellikle Internet bölgesi izin kümesi için kısıtlı bir kısmi güven güvenliği korumalı yürütün. Sonuç olarak, uygulamanızı Internet bölgesine desteklenen WPF öğeleri kümesini desteklemelidir veya uygulamanızın izinleri yükseltmesine gerekir. Daha fazla bilgi için [güvenlik](../../../../docs/framework/wpf/security-wpf.md).  
  
 Kullandığınızda, bir <xref:System.Windows.Controls.WebBrowser> uygulamanızın, WPF denetiminde dahili olarak yerel WebBrowser ActiveX denetimi oluşturur. Uygulamanızı Internet Explorer'ı çalıştıran bir kısmi güven XBAP olduğunda, Internet Explorer işlemi adanmış bir dizi ActiveX denetimi çalıştırır. Bu nedenle, aşağıdaki sınırlamalar geçerlidir:  
  
-   <xref:System.Windows.Controls.WebBrowser> Denetimi, güvenlik kısıtlamaları da dahil olmak üzere konak tarayıcıya benzer bir davranış sağlamalıdır. Bu güvenlik kısıtlamaları bazıları, Internet Explorer güvenlik ayarları denetlenebilir. Daha fazla bilgi için [güvenlik](../../../../docs/framework/wpf/security-wpf.md).  
  
-   Yüklenen etki alanları arası bir HTML sayfasında bir XBAP olduğunda, bir özel durum oluşturulur.  
  
-   Wpf'den ayrı bir iş parçacığı üzerinde giriştir <xref:System.Windows.Controls.WebBrowser>, klavye girişi kullanılamaz kesildi ve IME durumu paylaşılmaz.  
  
-   Zamanlama veya gezinti sırasını başka bir iş parçacığında çalıştıran ActiveX denetimi nedeniyle farklı olabilir. Örneğin, bir sayfaya giden her zaman başka gezinme isteği başlatarak iptal edilmedi.  
  
-   WPF uygulaması ayrı bir iş parçacığı olarak çalıştığından özel bir ActiveX denetimi ile iletişim sorunlarla karşılaşabilirsiniz.  
  
-   <xref:System.Windows.Interop.HwndHost.MessageHook> çünkü gerçekleşmedi <xref:System.Windows.Interop.HwndHost> başka bir iş parçacığı veya işlem çalışan bir pencere öğesinin alt sınıfı olamaz.  
  
### <a name="creating-a-full-trust-xbap"></a>Tam güven XBAP oluşturma  
 Bir XBAP tam güven gerektirir, bu izni etkinleştirmek için projenizi değiştirebilirsiniz. Aşağıdaki adımlar, tam güven etkinleştirme açıklanmaktadır:  
  
1.  Visual Studio'da proje özelliklerini açın.  
  
2.  Üzerinde **güvenlik** sekmesinde **tam güven uygulamasıdır** seçeneği.  
  
 Bu ayar, aşağıdaki değişiklikleri yapar:  
  
-   Proje dosyasında `<TargetZone>` öğe değeri değiştiğinde `Custom`.  
  
-   Uygulama bildiriminde (app.manifest) bir `Unrestricted="true"` özniteliği eklenir `PermissionSet` öğesi.  
  
    ```xml
    <PermissionSet class="System.Security.PermissionSet"   
                   version="1"   
                   ID="Custom"   
                   SameSite="site"   
                   Unrestricted="true" />  
    ```  
  
### <a name="deploying-a-full-trust-xbap"></a>Tam güven XBAP dağıtma  
 ClickOnce güvenilir dağıtım modeline izlemez bir tam güven XBAP dağıttığınızda, kullanıcı uygulamayı çalıştırdığında davranışı güvenlik bölgesine bağlıdır. Bazı durumlarda, kullanıcı, yüklemeye çalıştığınızda bir uyarı alırsınız. Kullanıcı yüklemeyi iptal devam etmek seçebilirsiniz. Aşağıdaki tabloda her güvenlik bölgesi ve hangi uygulama tam güven almak yapmanız gereken uygulama davranışını açıklar.  
  
|Güvenlik Bölgesi|Davranış|Tam güven alma|  
|-------------------|--------------|------------------------|  
|Yerel bilgisayar|Otomatik tam güven|Eylem gerekmiyor.|  
|İntranet ve Güvenilen siteler|İçin tam güven istemi|Kullanıcı istemi kaynakta görebilmesi için XBAP bir sertifika ile oturum açın.|  
|Internet|"Güven verilmeyen" ile başarısız oluyor|XBAP bir sertifika ile oturum açın.|  
  
> [!NOTE]
>  Önceki tabloda açıklanan güvenilen ClickOnce dağıtım modeline izlemeyin tam güven XBAP'ler için bir davranıştır.  
  
 Tam güven XBAP dağıtmak için ClickOnce güvenilir dağıtım modelini kullanmanız önerilir. Kullanıcıdan istenmemesi için bu model, tam güven güvenlik bölgesi ne olursa olsun, otomatik olarak verilmesi, bir XBAP sağlar. Bu modelin bir parçası olarak, uygulamanızı bir sertifika ile güvenilir bir yayımcı oturum açmanız gerekir. Daha fazla bilgi için [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview) ve [kod imzalama giriş](http://go.microsoft.com/fwlink/?LinkId=166327).  
  
<a name="xbap_start_time_performance_considerations"></a>   
## <a name="xbap-start-time-performance-considerations"></a>XBAP başlangıç zamanı performans konuları  
 XBAP performansının önemli bir yönü, başlangıç zamanıdır. Bir XBAP yüklemek için ilk WPF uygulaması ise *hazırlıksız başlatma* zaman on saniye veya daha fazla olabilir. İlerleme durumu sayfası WPF tarafından işlenir ve CLR ve WPF soğuk-uygulamayı görüntülemek için başlatılması gerekir çünkü budur.  
  
 İtibariyle [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], XBAP soğuk başlangıç zamanı dağıtım döngüsünde erken bir yönetilmeyen ilerleme durumu sayfası görüntüleyerek azaltılabilir. İlerleme durumu sayfası hemen görünür olduğundan ve yerel barındırma kodu tarafından görüntülenen HTML olarak işlenen uygulamanın başlatılmasından sonra.  
  
 Ayrıca, geliştirilmiş eşzamanlılık ClickOnce yükleme sırasının en fazla on oranında başlangıç süresini artırır. ClickOnce yüklemeleri ve doğrulama sonra bildirimleri, uygulama yükleme başlar ve ilerleme çubuğu başlar güncelleştirilecek.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Web Hizmeti Çağırmak Amacıyla XAML Tarayıcı Uygulamasında Hata Ayıklamak için Visual Studio'yu Yapılandırma](../../../../docs/framework/wpf/app-development/configure-vs-to-debug-a-xaml-browser-to-call-a-web-service.md)  
 [WPF Uygulaması Dağıtma](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)
