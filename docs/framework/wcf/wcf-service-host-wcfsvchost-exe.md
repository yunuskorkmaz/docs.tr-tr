---
title: WCF Hizmet Ana Bilgisayarı (WcfSvcHost.exe)
ms.date: 03/30/2017
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
ms.openlocfilehash: 7174cac4c07d9011ad4c0744ff7ad6550d832d8b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613251"
---
# <a name="wcf-service-host-wcfsvchostexe"></a>WCF Hizmet Ana Bilgisayarı (WcfSvcHost.exe)
Windows Communication Foundation (WCF) hizmet ana bilgisayarı (WcfSvcHost.exe), Visual Studio hata ayıklayıcıyı otomatik olarak ana bilgisayar ve uyguladıysanız bir hizmeti test etmek için (F5) başlatmak sağlar. Sonra hizmeti bulun ve olası hataları düzeltmek için WCF Test İstemcisi (WcfTestClient.exe) veya kendi istemci kullanarak test edebilirsiniz.  
  
## <a name="wcf-service-host"></a>WCF hizmet konağı  
 WCF hizmet konağı bir WCF Hizmeti projesini Hizmetleri'nde numaralandırır, projenin yapılandırması yükler ve bulduğu her hizmet için bir ana bilgisayar örneği oluşturur. Araç, WCF hizmet şablonu aracılığıyla Visual Studio'da tümleşiktir ve projenizin hatalarını ayıklama başlatıldığında çağrılır.  
  
 WCF hizmet konağı kullanarak ek kod yazmadan veya belirli bir ana bilgisayara geliştirme sırasında yürüten olmadan bir WCF Hizmeti (WCF hizmet kitaplığı projesi) barındırabilir.  
  
> [!NOTE]
>  WCF hizmet konağı, kısmi güven desteklemez. Bir WCF hizmetini kısmi güven kullanmak istiyorsanız, WCF hizmet kitaplığı proje şablonu Visual Studio'da hizmetinizi oluşturmak için kullanmayın. Bunun yerine, WCF kısmi güven, desteklenen bir Web sunucusu hizmeti barındıran WCF Hizmeti Web sitesi şablonunu seçerek Visual Studio'da yeni bir Web sitesi oluşturun.  
  
## <a name="project-types-hosted-by-wcf-service-host"></a>WCF hizmet konağı tarafından barındırılan proje türleri  
 WCF hizmet konağı WCF hizmet kitaplığı projesi türleri barındırabilirsiniz: WCF hizmet kitaplığı, sıralı iş akışı hizmet kitaplığı, Durum makinesi iş akışı hizmet kitaplığı ve dağıtım hizmeti kitaplığı. WCF hizmet konağı bir hizmet kitaplığı kullanarak proje eklenebilmesi için bu hizmetleri de barındırabilir **Öğe Ekle** işlevselliği. Bu, WCF hizmeti, WF Durum makinesi hizmeti, WF sıralı hizmeti, XAML WF Durum makinesi hizmeti ve XAML WF sıralı hizmeti içerir.  
  
 Size, ancak araç, bir konak yapılandırmanıza yardımcı olmayacağı dikkat etmelisiniz. Bu görev için App.config dosyasına el ile düzenlemeniz gerekir. Araç ayrıca kullanıcı tanımlı yapılandırma dosyalarını doğrulamaz.  
  
> [!CAUTION]
>  Bu amaçla mühendislik değil olarak WCF hizmet konağı hizmetlerini barındırmak için bir üretim ortamında kullanmamalısınız.  WCF hizmet konağı, güvenilirlik, güvenlik ve yönetilebilirlik gereksinimleri bu tür bir ortamın desteklemez. Üstün güvenilirlik ve izleme özellikleri sağlar ve barındırma hizmetleri için tercih edilen çözüm olduğundan, bunun yerine, IIS kullanın. Hizmetlerinizi geliştirme tamamlandıktan sonra IIS WCF hizmet ana bilgisayarından Hizmetleri geçirmeniz gerekir.  
  
## <a name="scenarios-for-using-wcf-service-host-inside-visual-studio"></a>Visual Studio'da WCF hizmet konağı kullanmaya yönelik senaryolar  
 Tüm parametreleri aşağıdaki tabloda **komut satırı bağımsız değişkenleri** iletişim kutusunda, projenize sağ tıklayarak bulunabilir **Çözüm Gezgini** seçerekVisualStudio'da**Özellikleri**, ardından seçerek **hata ayıklama** sekmesi ve tıklayarak **başlangıç projesi**. Bu parametreleri, WCF hizmet konağı yapılandırma yararlıdır.  
  
|Parametre|Açıklama|  
|---------------|-------------|  
|`/client`|Bir isteğe bağlı parametresi hizmetlerinin barındırıldığı sonra çalıştırılacak bir yürütülebilir dosya yolunu belirtir. Bu WCF Test İstemcisi başlar takip barındırma.|  
|`/clientArg`|Özel istemci uygulamaya geçirilen bağımsız değişken olarak bir dize belirtin.|  
|`/?`|Yardım metni görüntüler.|  
  
#### <a name="using-wcf-test-client"></a>WCF Test İstemcisi'ni kullanma  
 Yeni bir WCF Hizmeti projesi oluşturun ve hata ayıklayıcıyı başlatmak için F5 tuşuna basarak sonra WCF hizmet konağı projenizde bulduğu tüm hizmetleri barındırma başlatır. WCF Test istemcisi otomatik olarak açılır ve hizmet uç noktaları yapılandırma dosyasında tanımlanan bir listesini görüntüler. Ana penceredeki parametreleri test edebilir ve hizmetinizi çağırır.  
  
 WCF Test İstemcisi kullanıldığından emin olmak için projenize sağ tıklayın **Çözüm Gezgini** Visual Studio'da **özellikleri**, ardından **hata ayıklama** sekmesi. Tıklayın **başlangıç projesi** ve aşağıdaki göründüğünden emin olun **komut satırı bağımsız değişkenleri** iletişim kutusu.  
  
 `/client:WcfTestClient.exe`  
  
#### <a name="using-a-custom-client"></a>Özel bir istemci kullanarak  
 Özel bir istemci kullanmak için projenize sağ tıklayın **Çözüm Gezgini** Visual Studio'da **özellikleri**, ardından **hata ayıklama** sekmesi. Tıklayın **başlangıç projesi** ve düzenleme `/client` parametresinde **komut satırı bağımsız değişkenleri** iletişim kutusunda, aşağıdaki örnekte gösterildiği gibi özel istemcinizi işaret edecek şekilde.  
  
 `/client:"path/CustomClient.exe"`  
  
 Hizmeti yeniden başlatmak için F5 tuşuna bastığınızda, hata ayıklayıcıyı başlattığınızda WCF hizmet konağının otomatik olarak özel istemci başlatır.  
  
 Ayrıca `/clientArg:` parametresini kullanarak aşağıdaki örnekte gösterildiği gibi özel istemci uygulamaya geçirilen bağımsız değişken olarak bir dize belirtin.  
  
 `/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`  
  
 Örneğin, dağıtım hizmet kitaplığı şablonu kullanıyorsanız, aşağıdaki komut satırı bağımsız değişkenleri kullanabilirsiniz,  
  
 `/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`  
  
#### <a name="specifying-no-client"></a>Hiçbir istemci belirtme  
 Hiçbir istemci WCF Hizmeti barındırma sonra kullanılacak belirtmek için projenize sağ tıklayın **Çözüm Gezgini** Visual Studio'da **özellikleri**, ardından **hataayıklama** sekmesi. Tıklayın **başlangıç projesi** bırakıp **komut satırı bağımsız değişkenleri** iletişim kutusu boş.  
  
#### <a name="using-a-custom-host"></a>Özel bir ana bilgisayar kullanma  
 Özel bir ana bilgisayar'ı kullanmak için projenize sağ tıklayın **Çözüm Gezgini** Visual Studio'da **özellikleri**, ardından **hata ayıklama** sekmesi. Tıklayın **harici Program Başlat** ve özel ana bilgisayarı için tam yolunu girin. Ayrıca **komut satırı bağımsız değişkenleri** iletişim kutusunun ana bilgisayara geçirilecek bağımsız değişkenleri belirtin.  
  
## <a name="wcf-service-host-user-interface"></a>WCF hizmet konağı kullanıcı arabirimi  
 Başlangıçta çağırdığınızda WCF hizmet Konağı (Visual Studio'da F5 tuşuna basarak), **WCF hizmet konağı** penceresi otomatik olarak açılır. WCF hizmet konağı çalışırken, bildirim alanında program simgesi görünür. Açmak için simgesini çift tıklatın **WCF hizmet konağı** penceresi  
  
 Barındırma hizmeti sırasında hatalar oluştuğunda, ilgili bilgileri görüntülemek için WCF hizmet konağı iletişim kutusu açılır.  
  
 **WCF hizmet konağı** ana penceresi iki menüleri içerir:  
  
- **Dosya**: İçeren **Kapat** ve **çıkış** komutları. Tıkladığınızda **Kapat**, **WCF hizmet konağı** iletişim kutusu kapanır, ancak barındırılan hizmetler devam. Tıkladığınızda **çıkış**, WCF hizmet konağı aynı zamanda kapatılır. Bu, tüm barındırılan hizmetlerin de durdurulur.  
  
- **Yardım**: İçeren **hakkında** sürüm bilgisi içeren komutu. Ayrıca içerdiği **yardımcı** Yardım dosyasını açabilirsiniz komutu.  
  
 Ana **WCF hizmet konağı** penceresi iki alanları içerir:  
  
- İlk alan **hizmet**. Tüm hizmetlerin temel bilgileri görüntüleyen bir listesini içerir. Bilgileri içerir:  
  
    - **Hizmet**: Tüm hizmetler listelenir.  
  
    - **Durum**: Hizmet durumunu listeler. Geçerli değerler şunlardır: "Başlatıldı", "Stopped" ve "Error".  
  
    - **Meta veri adresi**: Meta veri adresi hizmetleri görüntüler.  
  
- İkinci alanı **ek bilgi**. Belirli bir hizmet satırı seçildiğinde hizmet durumunu ayrıntılı bir açıklama görüntüler **hizmet** alan. Durum hatası ise, ekrandaki tüm hata iletilerini görüntüleyebilirsiniz.  
  
## <a name="stopping-wcf-service-host"></a>WCF hizmet konağı durduruluyor  
 WCF hizmet konağı dört aşağıdaki şekilde kapatabilirsiniz:  
  
- Visual Studio'da hata ayıklama oturumunu durdurun.  
  
- Seçin **çıkış** gelen **dosya** menüde **WCF hizmet konağı** penceresi.  
  
- Seçin **çıkış** bağlam menüsünden sistem bildirim alanında WCF hizmet konağı Tepsi simgesi.  
  
- WCF Test istemcisi, kullanılıyorsa çıkın.  
  
## <a name="using-service-host-without-administrator-privilege"></a>Hizmet ana bilgisayarı yönetici ayrıcalığı kullanma  
 WCF hizmetleri geliştirmek yönetici ayrıcalığı olmayan kullanıcıların etkinleştirmek için bir ACL (erişim denetim listesi) için ad alanı oluşturulan "http://+:8731/Design_Time_Addresses" Visual Studio yüklemesi sırasında. ACL makinede oturum açan tüm etkileşimli kullanıcılar içerir (UI) için ayarlanır. Yöneticiler ekleyin veya bu ACL'SİNDEN kaldırmasına veya ek bağlantı noktalarını açın. Bu ACL kullanıcıların yönetici ayrıcalıkları vermeden WCF hizmet otomatik ana bilgisayarı (wcfSvcHost.exe) kullanmasını sağlar.  
  
 İçinde netsh.exe aracını kullanarak erişimi değiştirebilirsiniz [!INCLUDE[wv](../../../includes/wv-md.md)] yükseltilmiş yönetici hesabı altında. Netsh.exe kullanmaya bir örnek verilmiştir.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Netsh.exe hakkında daha fazla bilgi için bkz. "[Netsh.exe aracı ve komut satırı anahtarları nasıl kullanılacağını](https://go.microsoft.com/fwlink/?LinkId=97877)".  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Test İstemcisi (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
