---
title: WCF Hizmet Konağı (WcfSvcHost.exe)
ms.date: 03/30/2017
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
ms.openlocfilehash: e1e258015adc34edd4a109f3bc5a32b4bf6f0296
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="wcf-service-host-wcfsvchostexe"></a>WCF Hizmet Konağı (WcfSvcHost.exe)
Windows Communication Foundation (WCF) Hizmet Konağı (WcfSvcHost.exe), Visual Studio hata ayıklayıcısı (F5) otomatik olarak ana bilgisayar ve uygulamış olan bir hizmeti test başlatma olanak sağlar. Ardından hizmetini bulun ve olası hataları düzeltmek için WCF Test İstemcisi (WcfTestClient.exe) veya kendi istemci kullanarak test edebilirsiniz.  
  
## <a name="wcf-service-host"></a>WCF hizmet konağı  
 WCF hizmet konağı bir WCF Hizmeti projesini Hizmetleri'nde numaralandırır, projenin yapılandırmayı yükler ve bulduğu her hizmet için bir konak başlatır. Araç Visual Studio'ya WCF Hizmeti şablonu aracılığıyla tümleşiktir ve projenizin hatalarını ayıklama başladığında çağrılır.  
  
 WCF hizmet ana bilgisayarı kullanarak ek kod yazma veya belirli bir ana bilgisayara geliştirme sırasında gerçekleştirmeden olmadan bir WCF Hizmeti (bir WCF Hizmeti kitaplığı projesi) barındırabilir.  
  
> [!NOTE]
>  WCF hizmet ana bilgisayarı, kısmi güven desteklemez. Kısmi güven bir WCF hizmetini kullanmak istiyorsanız, WCF Hizmeti kitaplığı proje şablonu Visual Studio'da hizmet oluşturmak için kullanmayın. Bunun yerine, WCF kısmi güven desteklenen bir Web hizmeti barındırabilir WCF Hizmeti Web sitesi şablonu seçerek Visual Studio'da yeni Web sitesi oluşturun.  
  
## <a name="project-types-hosted-by-wcf-service-host"></a>WCF hizmet ana bilgisayar tarafından barındırılan proje türleri  
 WCF hizmet ana bilgisayarı, aşağıdaki WCF Hizmeti kitaplığı proje türleri barındırabilir: WCF Hizmeti kitaplığı, sıralı iş akışı hizmeti kitaplığı, Durum makinesi iş akışı hizmeti kitaplığı ve dağıtım hizmeti kitaplığı. WCF hizmet ana bilgisayarı ayrıca bir hizmet kitaplığını kullanarak proje eklenebilir bu hizmetlerin konak **Öğe Ekle** işlevselliği. Bu, WCF hizmeti, WF Durum makinesi hizmeti, WF sıralı hizmetini, XAML WF Durum makinesi hizmeti ve XAML WF sıralı hizmetini kapsar.  
  
 Size, ancak, aracı bir ana bilgisayar yapılandırma yardımcı olacak değil, unutmamalısınız. Bu görev için App.config dosyasını el ile düzenlemeniz gerekir. Araç ayrıca kullanıcı tanımlı yapılandırma dosyalarını doğrulamaz.  
  
> [!CAUTION]
>  Bu amaçla mühendislik değil olarak WCF hizmet konağı hizmetlerini barındırmak için bir üretim ortamında kullanmamalısınız.  WCF hizmet ana bilgisayarı, güvenilirlik, güvenlik ve yönetilebilirlik gereksinimleri böyle bir ortamın desteklemez. Bunun yerine, üstün güvenilirliğe ve İzleme özelliklerini sağlar ve barındırma hizmetleri için tercih edilen çözüm beri IIS kullanın. Geliştirme, hizmetlerin tamamlandıktan sonra IIS WCF hizmet ana bilgisayardan Hizmetleri geçirmeniz gerekir.  
  
## <a name="scenarios-for-using-wcf-service-host-inside-visual-studio"></a>WCF hizmet konağı Visual Studio içinde kullanma senaryoları  
 Aşağıdaki tabloda, tüm parametreleri listeler **komut satırı bağımsız değişkenleri** projenize sağ tıklayarak bulunabilir iletişim kutusu, **Çözüm Gezgini** seçerekVisualStudio**Özellikleri**, ardından seçerek **hata ayıklama** sekmesi ve tıklayarak **başlangıç projesi**. Bu parametreler, WCF hizmet ana bilgisayarı yapılandırmada faydalıdır.  
  
|Parametre|Açıklama|  
|---------------|-------------|  
|`/client`|Barındırılan hizmetlere sonra çalışacak bir yürütülebilir dosya yolunu belirtir. isteğe bağlı bir parametre. Bu WCF Test İstemcisi başlatır aşağıdaki barındırma.|  
|`/clientArg`|Özel istemci uygulamaya geçirilen bağımsız değişken olarak bir dize belirtin.|  
|`/?`|Yardım metni görüntüler.|  
  
#### <a name="using-wcf-test-client"></a>WCF Test İstemcisi kullanma  
 Yeni bir WCF Hizmeti projesi oluşturun ve hata ayıklayıcısı başlatmak için F5 tuşuna basarak sonra barındırma projenizde bulduğu tüm hizmetleri WCF hizmet ana bilgisayarı başlatır. WCF Test istemcisi otomatik olarak açar ve yapılandırma dosyasında tanımlanmış hizmet uç noktaları listesini görüntüler. Ana penceresinden parametreleri test edin ve hizmetinizi çağırma.  
  
 WCF Test İstemcisi kullanıldığından emin olmak için projenize sağ **Çözüm Gezgini** Visual Studio'da seçin **özellikleri**seçeneğini belirleyip **hata ayıklama** sekmesi. Tıklatın **başlangıç projesi** ve aşağıdaki olarak göründüğünden emin olun **komut satırı bağımsız değişkenleri** iletişim kutusu.  
  
 `/client:WcfTestClient.exe`  
  
#### <a name="using-a-custom-client"></a>Özel bir istemci kullanma  
 Özel bir istemci kullanmak için projenize sağ **Çözüm Gezgini** Visual Studio'da seçin **özellikleri**seçeneğini belirleyip **hata ayıklama** sekmesi. Tıklatın **başlangıç projesi** ve düzenleme `/client` parametresinde **komut satırı bağımsız değişkenleri** aşağıdaki örnekte gösterildiği gibi özel istemciniz işaret edecek şekilde iletişim kutusu.  
  
 `/client:"path/CustomClient.exe"`  
  
 Hizmeti yeniden başlatmak için F5 tuşuna bastığınızda, hata ayıklayıcı başlattığında WCF hizmet ana bilgisayarı özel istemci otomatik olarak başlar.  
  
 Aynı zamanda `/clientArg:` parametresini kullanarak aşağıdaki örnekte gösterildiği gibi özel istemci uygulamaya geçirilen bağımsız değişken olarak bir dize belirtin.  
  
 `/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`  
  
 Örneğin, dağıtım hizmeti kitaplığı şablon kullanıyorsanız, aşağıdaki komut satırı bağımsız değişkenleri kullanabilirsiniz,  
  
 `/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`  
  
#### <a name="specifying-no-client"></a>Hiçbir istemci belirtme  
 Hiçbir istemci WCF Hizmeti barındırma sonra kullanılacak belirtmek için projenize sağ **Çözüm Gezgini** Visual Studio'da seçin **özellikleri**seçeneğini belirleyip **hataayıklama** sekmesi. Tıklatın **başlangıç projesi** bırakıp **komut satırı bağımsız değişkenleri** iletişim kutusu boş.  
  
#### <a name="using-a-custom-host"></a>Özel bir ana bilgisayar kullanarak  
 Özel bir ana bilgisayar kullanmak için projenize sağ **Çözüm Gezgini** Visual Studio'da seçin **özellikleri**seçeneğini belirleyip **hata ayıklama** sekmesi. Tıklatın **Başlat Dış Program** ve özel ana bilgisayar için tam yolunu girin. Aynı zamanda **komut satırı bağımsız değişkenleri** ana bilgisayara geçirilecek bağımsız değişkenler belirtmek için iletişim kutusu.  
  
## <a name="wcf-service-host-user-interface"></a>WCF hizmet ana kullanıcı arabirimi  
 Ne zaman, başlangıçta çağırma WCF hizmet Konağı (Visual Studio içinde F5'e basarak), **WCF hizmet konağı** penceresi otomatik olarak açılır. WCF hizmet konağı çalışırken programın simgesi bildirim alanında görüntülenir. Açmak için simgesini çift **WCF hizmet konağı** penceresi  
  
 Barındırma hizmeti sırasında hatalar oluştuğunda, ilgili bilgileri görüntülemek için WCF hizmet konağı iletişim kutusu açılır.  
  
 **WCF hizmet konağı** ana penceresi iki menüleri içerir:  
  
-   **Dosya**: içeren **Kapat** ve **çıkış** komutları. Tıkladığınızda **Kapat**, **WCF hizmet konağı** iletişim kutusu kapanır ancak Hizmetleri barındırılması devam eder. Tıkladığınızda **çıkış**, WCF hizmet ana bilgisayarı ayrıca kapatıldı. Bu aynı zamanda barındırılan tüm hizmetleri durdurur.  
  
-   **Yardım**: içeren **hakkında** sürüm bilgilerini içeren komutu. Ayrıca içerdiği **yardımcı** Yardım dosyasını açabilirsiniz komutu.  
  
 Ana **WCF hizmet konağı** penceresi iki alanları içerir:  
  
-   İlk alan **hizmet**. Tüm hizmetlerin temel bilgileri görüntüleyen bir listesini içerir. Bilgileri içerir:  
  
    -   **Hizmet**: tüm hizmetleri listeler.  
  
    -   **Durum**: Hizmet durumunu listeler. Geçerli değerler "Başlatıldı", "Durduruldu" ve "Error" dir.  
  
    -   **Meta veri adresi**: meta veri adresi hizmetleri görüntüler.  
  
-   İkinci alanı **ek bilgi**. Belirli bir hizmet satırı seçildiğinde hizmet durumunun ayrıntılı bir açıklama görüntüler **hizmet** alan. Hata durumundaysa, tam hata iletisi ekranda görüntüleyebilirsiniz.  
  
## <a name="stopping-wcf-service-host"></a>WCF hizmet ana bilgisayarı durduruluyor  
 WCF hizmet konağı aşağıdaki dört yollarla kapatabilirsiniz:  
  
-   Visual Studio'da hata ayıklama oturumu durdurun.  
  
-   Seçin **çıkış** gelen **dosya** menüde **WCF hizmet konağı** penceresi.  
  
-   Seçin **çıkış** WCF hizmet konağı Tepsi simgesi sistem bildirim alanında bağlam menüsünden.  
  
-   Kullanılmakta ise, WCF Test İstemcisi çıkın.  
  
## <a name="using-service-host-without-administrator-privilege"></a>Hizmet ana bilgisayarı yönetici ayrıcalığı kullanma  
 WCF hizmetlerini geliştirmek yönetici ayrıcalığı olmayan kullanıcıların etkinleştirmek için bir ACL (erişim denetim listesi) ad alanı için oluşturulan "http://+:8731/Design_Time_Addresses" Visual Studio yüklemesi sırasında. ACL hangi makineye oturum açmış etkileşimli kullanıcıların tümünü içerir (UI) ayarlanır. Yöneticiler eklemek veya bu ACL'den kaldırmasına veya ek bağlantı noktalarını açın. Bu ACL kullanıcıların yönetici ayrıcalıklarını verme olmadan WCF hizmeti otomatik ana bilgisayarı (wcfSvcHost.exe) kullanmasını sağlar.  
  
 Erişim netsh.exe aracını kullanarak değiştirebilirsiniz [!INCLUDE[wv](../../../includes/wv-md.md)] yükseltilmiş yönetici hesabı altında. Netsh.exe kullanmaya ilişkin bir örnek verilmiştir.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Netsh.exe hakkında daha fazla bilgi için bkz: "[Netsh.exe aracı ve komut satırı anahtarları nasıl kullanılacağını](http://go.microsoft.com/fwlink/?LinkId=97877)".  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Test İstemcisi (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
