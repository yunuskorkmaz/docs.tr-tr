---
title: XAML tarayıcı uygulamalarına genel bakış
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
ms.openlocfilehash: bec7e14ceed867e89c3117efbc245938356b9d78
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742288"
---
# <a name="wpf-xaml-browser-applications-overview"></a>WPF XAML Tarayıcı Uygulamalarına Genel Bakış
<a name="introduction"></a>XAML tarayıcı uygulamaları (XBAP 'ler) hem Web uygulamalarının hem de zengin istemci uygulamalarının özelliklerini birleştirir. Web uygulamaları gibi, XBAP 'ler bir Web sunucusuna dağıtılabilir ve Internet Explorer veya Firefox 'tan başlatılabilir. Zengin istemci uygulamaları gibi, XBAP 'ler WPF 'nin yeteneklerini kullanabilir. XBAP 'lerin geliştirilmesi, zengin istemci geliştirmeye de benzer. Bu konu, XBAP geliştirmeye basit, yüksek düzey bir giriş sağlar ve XBAP geliştirmenin standart zengin istemci geliştirmeden farklı olduğunu açıklar.

 Bu konu aşağıdaki bölümleri içermektedir:

- [Yeni bir XAML tarayıcı uygulaması (XBAP) oluşturma](#creating_a_new_xaml_browser_application_xbap)

- [XBAP dağıtma](#deploying_a_xbap)

- [Ana bilgisayar Web sayfasıyla iletişim kurma](#communicating_with_the_host_web_page)

- [XBAP güvenlik konuları](#xbap_security_considerations)

- [XBAP başlangıç zamanı performans konuları](#xbap_start_time_performance_considerations)

<a name="creating_a_new_xaml_browser_application_xbap"></a>
## <a name="creating-a-new-xaml-browser-application-xbap"></a>Yeni bir XAML tarayıcı uygulaması (XBAP) oluşturma
 Yeni bir XBAP projesi oluşturmanın en kolay yolu Visual Studio ile aynıdır. Yeni bir proje oluştururken, şablonlar listesinden **WPF tarayıcı uygulaması** ' nı seçin. Daha fazla bilgi için bkz. [nasıl yapılır: yenı WPF tarayıcı uygulaması projesi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)).

 XBAP projesi çalıştırdığınızda, tek başına bir pencere yerine bir tarayıcı penceresinde açılır. Visual Studio 'dan XBAP 'yi hata ayıkladığınızda, uygulama Internet bölgesi izniyle çalışır ve bu nedenle, bu izinler aşılırsa güvenlik özel durumları oluşturur. Daha fazla bilgi için bkz. [güvenlik](../security-wpf.md) ve [WPF Kısmi güven güvenliği](../wpf-partial-trust-security.md).

> [!NOTE]
> Visual Studio ile geliştirmiyorsanız veya proje dosyaları hakkında daha fazla bilgi edinmek istiyorsanız bkz. [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md).

<a name="deploying_a_xbap"></a>
## <a name="deploying-an-xbap"></a>XBAP dağıtma
 Bir XBAP oluşturduğunuzda, çıkış aşağıdaki üç dosyayı içerir:

|Dosya|Açıklama|
|----------|-----------------|
|Yürütülebilir (. exe)|Bu, derlenen kodu içerir ve. exe uzantısına sahiptir.|
|Uygulama bildirimi (. manifest)|Bu, uygulamayla ilişkili meta verileri içerir ve bir. manifest uzantısına sahiptir.|
|Dağıtım bildirimi (. XBAP)|Bu dosya, ClickOnce 'ın uygulamayı dağıtmak için kullandığı ve. xbap uzantısına sahip olan bilgileri içerir.|

 XBAP 'yi bir Web sunucusuna (örneğin, Microsoft Internet Information Services (IIS) 5,0 veya sonraki sürümlere dağıtabilirsiniz. .NET Framework Web sunucusuna yüklemek zorunda değilsiniz, ancak WPF çok amaçlı Internet posta uzantıları (MIME) türlerini ve dosya adı uzantılarını kaydetmeniz gerekir. Daha fazla bilgi için bkz. [WPF uygulamalarını dağıtmak IÇIN ııs 5,0 ve ııs 6,0 yapılandırma](how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md).

 XBAP 'yi dağıtıma hazırlamak için. exe ve ilişkili bildirimleri Web sunucusuna kopyalayın. . Xbap uzantısına sahip olan dosya olan dağıtım bildirimini açmak için köprü içeren bir HTML sayfası oluşturun. Kullanıcı. xbap dosyasının bağlantısına tıkladığında, ClickOnce otomatik olarak uygulamayı indirme ve başlatma mekanizması işler. Aşağıdaki örnek kod, bir XBAP 'ye işaret eden bir köprü içeren bir HTML sayfasını gösterir.

```html
<html>
    <head></head>
    <body>
        <a href="XbapEx.xbap">Click this link to launch the application</a>
    </body>
</html>
```

 Bir XBAP 'yi bir Web sayfasının çerçevesinde de barındırabilirsiniz. Bir veya daha fazla çerçeveyle bir Web sayfası oluşturun. Bir çerçevenin kaynak özelliğini dağıtım bildirim dosyası olarak ayarlayın. Barındırma Web sayfası ile XBAP arasında iletişim kurmak için yerleşik mekanizmayı kullanmak istiyorsanız, uygulamayı bir çerçevede barındırmanız gerekir. Aşağıdaki örnek kod, iki kare içeren bir HTML sayfası gösterir, ikinci çerçeve kaynağı bir XBAP olarak ayarlanır.

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

### <a name="clearing-cached-xbaps"></a>Önbelleğe alınmış XBAP temizleniyor
 XBAP 'nizi yeniden oluşturup başlattıktan sonra bazı durumlarda, XBAP 'nin önceki bir sürümünün açık olduğunu fark edebilirsiniz. Örneğin, bu davranış, XBAP derleme sürüm numaranız statikse ve XBAP 'yi komut satırından başlattığınızda meydana gelebilir. Bu durumda, önbelleğe alınmış sürüm (daha önce başlatılmış olan sürüm) arasındaki sürüm numarası ve yeni sürüm aynı kaldığı için, XBAP 'nin yeni sürümü indirilmez. Bunun yerine, önbelleğe alınan sürüm yüklenir.

 Bu durumlarda, komut isteminde **Mage** komutunu (Visual Studio veya Windows SDK ile yüklenir) kullanarak önbelleğe alınmış sürümü kaldırabilirsiniz. Aşağıdaki komut, uygulama önbelleğini temizler.

 ```console
 Mage.exe -cc
 ```

 Bu komut, XBAP 'nizin en son sürümünün başlatılmış olmasını güvence altına alır. Visual Studio 'da uygulamanızda hata ayıklarken, XBAP 'nizin en son sürümü başlatılmalıdır. Genel olarak, her bir yapıda dağıtım sürüm numaranızı güncelleştirmeniz gerekir. Mage hakkında daha fazla bilgi için bkz. [Mage. exe (bildirim oluşturma ve düzenleme aracı)](../../tools/mage-exe-manifest-generation-and-editing-tool.md).

<a name="communicating_with_the_host_web_page"></a>
## <a name="communicating-with-the-host-web-page"></a>Ana bilgisayar Web sayfasıyla iletişim kurma
 Uygulama bir HTML çerçevesinde barındırıldığı zaman, XBAP içeren Web sayfasıyla iletişim kurabilirsiniz. Bunu, <xref:System.Windows.Interop.BrowserInteropHelper><xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> özelliğini alarak yapabilirsiniz. Bu özellik HTML penceresini temsil eden bir betik nesnesi döndürür. Daha sonra normal nokta söz dizimini kullanarak [pencere nesnesindeki](https://go.microsoft.com/fwlink/?LinkId=160274) özelliklere, yöntemlere ve olaylara erişebilirsiniz. Ayrıca, betik yöntemlerine ve genel değişkenlere erişebilirsiniz. Aşağıdaki örnek, komut dosyası nesnesinin nasıl alınacağını ve tarayıcının nasıl kapatılmasını gösterir.

 [!code-csharp[XbapBrowserInterop#10](~/samples/snippets/csharp/VS_Snippets_Wpf/xbapbrowserinterop/cs/page1.xaml.cs#10)]
 [!code-vb[XbapBrowserInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/xbapbrowserinterop/vb/page1.xaml.vb#10)]

### <a name="debugging-xbaps-that-use-hostscript"></a>HostScript kullanan XBAP 'ler hata ayıklaması
 XBAP 'niz HTML penceresiyle iletişim kurmak için <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> nesnesini kullanıyorsa, Visual Studio 'da uygulamayı çalıştırmak ve hata ayıklamak için belirtmeniz gereken iki ayar vardır. Uygulamanın kaynak sitesine erişimi olması gerekir ve uygulamayı XBAP içeren HTML sayfasıyla başlatmanız gerekir. Aşağıdaki adımlarda, bu iki ayarı nasıl denetleyen anlatılmaktadır:

1. Visual Studio 'da proje özelliklerini açın.

2. **Güvenlik** sekmesinde **Gelişmiş**’e tıklayın.

     Gelişmiş güvenlik ayarları iletişim kutusu görüntülenir.

3. **Uygulamanın kaynak sitesine erişimi ver** onay kutusunun işaretli olduğundan emin olun ve ardından **Tamam**' a tıklayın.

4. **Hata Ayıkla** sekmesinde **URL ile tarayıcıyı Başlat** seçeneğini belirleyin ve XBAP 'yi içeren HTML sayfasının URL 'sini belirtin.

5. Internet Explorer 'da **Araçlar** düğmesine tıklayın ve ardından **Internet seçenekleri**' ni seçin.

     Internet Seçenekleri iletişim kutusu görüntülenir.

6. **Gelişmiş** sekmesine tıklayın.

7. **Güvenlik**altındaki **Ayarlar** listesinde, **etkin Içeriğin bilgisayarımdaki dosyalarda çalıştırılmasına izin ver** onay kutusunu işaretleyin.

8. **Tamam**’a tıklayın.

     Internet Explorer 'ı yeniden başlattıktan sonra değişiklikler geçerli olur.

> [!CAUTION]
> Internet Explorer 'da etkin içeriği etkinleştirmek bilgisayarınızı riske alabilir. Internet Explorer güvenlik ayarlarınızı değiştirmek istemiyorsanız, HTML sayfasını bir sunucudan başlatabilir ve Visual Studio hata ayıklayıcısını işleme ekleyebilirsiniz.

<a name="xbap_security_considerations"></a>
## <a name="xbap-security-considerations"></a>XBAP güvenlik konuları
 XBAP 'ler genellikle Internet bölgesi izin kümesiyle kısıtlanmış bir kısmi güven güvenlik korumalı alanı içinde yürütülür. Sonuç olarak, uygulamanız Internet bölgesinde desteklenen WPF öğelerinin alt kümesini desteklemelidir veya uygulamanızın izinlerini yükselmelidir. Daha fazla bilgi için bkz. [güvenlik](../security-wpf.md).

 Uygulamanızda <xref:System.Windows.Controls.WebBrowser> bir denetim kullandığınızda WPF, yerel WebBrowser ActiveX denetimini dahili olarak başlatır. Uygulamanız Internet Explorer 'da çalışan bir kısmi güven XBAP olduğunda, ActiveX denetimi Internet Explorer işleminin özel bir iş parçacığında çalışır. Bu nedenle, aşağıdaki sınırlamalar geçerlidir:

- <xref:System.Windows.Controls.WebBrowser> denetimi, güvenlik kısıtlamaları da dahil olmak üzere, ana bilgisayar tarayıcısına benzer davranış sağlamalıdır. Bu güvenlik kısıtlamalarından bazıları Internet Explorer güvenlik ayarları aracılığıyla denetlenebilir. Daha fazla bilgi için bkz. [güvenlik](../security-wpf.md).

- Bir XBAP bir HTML sayfasında etki alanları arası yüklendiğinde bir özel durum oluşur.

- Giriş, WPF <xref:System.Windows.Controls.WebBrowser>ayrı bir iş parçacığında bulunur, bu nedenle klavye girişi yakalanamaz ve IME durumu paylaşılmaz.

- Farklı bir iş parçacığında çalışan ActiveX denetimi nedeniyle, gezinmenin zamanlaması veya sırası farklı olabilir. Örneğin, bir sayfaya gitme işlemi, başka bir gezinti isteği başlatarak her zaman iptal edilmez.

- WPF uygulaması ayrı bir iş parçacığında çalıştığından, özel bir ActiveX denetimi iletişimle ilgili sorun yaşıyor olabilir.

- <xref:System.Windows.Interop.HwndHost.MessageHook>, <xref:System.Windows.Interop.HwndHost> başka bir iş parçacığında veya işlemde çalışan bir pencerenin alt sınıfını oluşturamıyor.

### <a name="creating-a-full-trust-xbap"></a>Tam güvenle bir XBAP oluşturma
 XBAP 'niz tam güven gerektiriyorsa, bu izni etkinleştirmek için projenizi değiştirebilirsiniz. Aşağıdaki adımlarda tam güvenin nasıl etkinleştirileceği açıklanır:

1. Visual Studio 'da proje özelliklerini açın.

2. **Güvenlik** sekmesinde, **Bu tam güven uygulaması** seçeneğini belirleyin.

 Bu ayar aşağıdaki değişiklikleri yapar:

- Proje dosyasında `<TargetZone>` öğesi değeri `Custom`olarak değiştirilir.

- Uygulama bildiriminde (App. manifest), '<xref:System.Security.PermissionSet> öğesine bir `Unrestricted="true"` özniteliği eklenir.

    ```xml
    <PermissionSet class="System.Security.PermissionSet"
                   version="1"
                   ID="Custom"
                   SameSite="site"
                   Unrestricted="true" />
    ```

### <a name="deploying-a-full-trust-xbap"></a>Tam güvenle bir XBAP dağıtma
 ClickOnce güvenilir dağıtım modelini takip eden tam güvenle bir XBAP dağıttığınızda, Kullanıcı uygulamayı çalıştırdığında davranış güvenlik bölgesine bağlı olur. Bazı durumlarda, Kullanıcı yüklemeyi denediklerinde bir uyarı alır. Kullanıcı devam etmeyi seçebilir veya yüklemeyi iptal edebilir. Aşağıdaki tabloda her güvenlik bölgesi için uygulamanın davranışı ve uygulamanın tam güven alması için yapmanız gerekenler açıklanmaktadır.

|Güvenlik Bölgesi|Davranış|Tam güven alma|
|-------------------|--------------|------------------------|
|Yerel bilgisayar|Otomatik tam güven|Eylem gerekmiyor.|
|Intranet ve güvenilen siteler|Tam güven iste|Kullanıcının istemde kaynağı görmesi için XBAP 'yi bir sertifikayla imzalayın.|
|Internet|"Güven verilmedi" ile başarısız olur|XBAP 'yi bir sertifikayla imzalayın.|

> [!NOTE]
> Önceki tabloda açıklanan davranış, ClickOnce güvenilir dağıtım modelini takip eden tam güvenli XBAP 'ler içindir.

 Tam güvenle bir XBAP dağıtmak için ClickOnce güvenilir dağıtım modelini kullanmanız önerilir. Bu model, Kullanıcı sorulmadan, XBAP 'nize güvenlik bölgesinden bağımsız olarak tam güven verilmesini sağlar. Bu modelin bir parçası olarak, uygulamanızı güvenilir bir yayımcının sertifikası ile imzalamanız gerekir. Daha fazla bilgi için bkz. [Güvenilen uygulama dağıtımına genel bakış](/visualstudio/deployment/trusted-application-deployment-overview) ve [kod imzalamaya giriş](https://go.microsoft.com/fwlink/?LinkId=166327).

<a name="xbap_start_time_performance_considerations"></a>
## <a name="xbap-start-time-performance-considerations"></a>XBAP başlangıç zamanı performans konuları
 XBAP performansının önemli bir yönü başlangıç zamanı olur. Bir XBAP yüklenecek ilk WPF uygulaması ise, *soğuk başlangıç* saati on saniye veya daha fazla olabilir. Bunun nedeni, ilerleme sayfasının WPF tarafından işlenmesi ve CLR ve WPF 'in uygulamayı görüntülemesi için soğuk başlatılmış olması gerekir.

 .NET Framework 3,5 SP1 'den başlayarak, XBAP soğuk başlatma süresi, dağıtım döngüsünün başlarında yönetilmeyen bir ilerleme sayfası görüntülenirken azaltılmaktadır. İlerleme sayfası, uygulama başladıktan hemen sonra görünür, çünkü yerel barındırma kodu tarafından görüntülenir ve HTML olarak işlenir.

 Ayrıca, ClickOnce indirme sırasının geliştirilmiş eşzamanlılığı, başlangıç süresini yüzde on ' a kadar geliştirir. ClickOnce indirildikten ve bildirimleri doğruladıktan sonra, uygulama indirme başlar ve ilerleme çubuğu güncelleştirilmeye başlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Web Hizmeti Çağırmak Amacıyla XAML Tarayıcı Uygulamasında Hata Ayıklamak için Visual Studio'yu Yapılandırma](configure-vs-to-debug-a-xaml-browser-to-call-a-web-service.md)
- [WPF Uygulaması Dağıtma](deploying-a-wpf-application-wpf.md)
