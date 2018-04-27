---
title: WCF Hizmet Konağı (WcfSvcHost.exe)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1da8d7a08e7887e8ba3fd50a8f809e2ff551a7fd
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="wcf-service-host-wcfsvchostexe"></a>WCF Hizmet Konağı (WcfSvcHost.exe)
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Hizmet Konağı (WcfSvcHost.exe), Visual Studio hata ayıklayıcısı (F5) otomatik olarak ana bilgisayar ve uygulamış olan bir hizmeti test başlatma olanak sağlar. Hizmetini kullanarak sınayabilir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test İstemcisi (WcfTestClient.exe) ya da kendi istemci bulmak ve olası hataları düzeltmek için.  
  
## <a name="wcf-service-host"></a>WCF hizmet konağı  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hizmet ana bilgisayarı numaralandırır Hizmetleri'nde bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmeti projesi, projenin yapılandırmayı yükler ve bulduğu her hizmet için bir konak başlatır. Aracı, Visual Studio ile tümleştirilmiş [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet şablonu ve projenizin hatalarını ayıklama başladığında çağrılır.  
  
 Kullanarak [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet konağı barındırabilir bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet (içinde bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet kitaplığı projesi) ek kod yazma veya belirli bir ana bilgisayara geliştirme sırasında gerçekleştirmeden olmadan.  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hizmet ana bilgisayarı, kısmi güven desteklemez. Kullanmak istiyorsanız bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kısmi güven, hizmeti kullanmayın [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmetinizi oluşturmak için Visual Studio'da hizmet kitaplığı proje şablonu. Bunun yerine, yeni Web sitesi seçerek Visual Studio'da oluşturma [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] , bir Web hizmeti barındırabilir Hizmet Web sitesi şablonu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kısmi güven desteklenir.  
  
## <a name="project-types-hosted-by-wcf-service-host"></a>WCF hizmet ana bilgisayar tarafından barındırılan proje türleri  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hizmet ana bilgisayarı, aşağıdaki barındırabilir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet kitaplığı proje türleri: [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet kitaplığı, sıralı iş akışı hizmeti kitaplığı, Durum makinesi iş akışı hizmeti kitaplığı ve dağıtım hizmeti kitaplığı. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hizmet ana bilgisayarı ayrıca bir hizmet kitaplığını kullanarak proje eklenebilir bu hizmetlerin konak **Öğe Ekle** işlevselliği. Bu içerir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmeti, WF Durum makinesi hizmeti, WF sıralı hizmet, XAML WF Durum makinesi hizmeti ve XAML WF sıralı hizmet.  
  
 Size, ancak, aracı bir ana bilgisayar yapılandırma yardımcı olacak değil, unutmamalısınız. Bu görev için App.config dosyasını el ile düzenlemeniz gerekir. Araç ayrıca kullanıcı tanımlı yapılandırma dosyalarını doğrulamaz.  
  
> [!CAUTION]
>  Kullanılamaz [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet konağı barındırmak için hizmetleri bir üretim ortamında, bu amaçla mühendislik değil olarak.  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hizmet ana bilgisayarı, güvenilirlik, güvenlik ve yönetilebilirlik gereksinimleri böyle bir ortamın desteklemez. Bunun yerine, üstün güvenilirliğe ve İzleme özelliklerini sağlar ve barındırma hizmetleri için tercih edilen çözüm beri IIS kullanın. Geliştirme hizmetlerinizin tamamlandıktan sonra hizmetleri geçirmelisiniz [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] IIS hizmeti ana bilgisayarı.  
  
## <a name="scenarios-for-using-wcf-service-host-inside-visual-studio"></a>WCF hizmet konağı Visual Studio içinde kullanma senaryoları  
 Aşağıdaki tabloda, tüm parametreleri listeler **komut satırı bağımsız değişkenleri** projenize sağ tıklayarak bulunabilir iletişim kutusu, **Çözüm Gezgini** seçerekVisualStudio**Özellikleri**, ardından seçerek **hata ayıklama** sekmesi ve tıklayarak **başlangıç projesi**. Bu parametreler yapılandırmada yararlı [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet ana bilgisayarı.  
  
|Parametre|Açıklama|  
|---------------|-------------|  
|`/client`|Barındırılan hizmetlere sonra çalışacak bir yürütülebilir dosya yolunu belirtir. isteğe bağlı bir parametre. Bu başlatır [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test barındırma aşağıdaki istemci.|  
|`/clientArg`|Özel istemci uygulamaya geçirilen bağımsız değişken olarak bir dize belirtin.|  
|`/?`|Yardım metni görüntüler.|  
  
#### <a name="using-wcf-test-client"></a>WCF Test İstemcisi kullanma  
 Yeni bir oluşturduktan sonra [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet projesi ve hata ayıklayıcı başlatmak için F5 tuşuna basarak [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet ana bilgisayarı başlatır barındırma projenizde bulduğu tüm hizmetleri. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test istemcisi otomatik olarak açar ve yapılandırma dosyasında tanımlanmış hizmet uç noktaları listesini görüntüler. Ana penceresinden parametreleri test edin ve hizmetinizi çağırma.  
  
 Emin olmak için [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test İstemcisi kullanıldığında, projenize sağ **Çözüm Gezgini** Visual Studio'da seçin **özellikleri**seçeneğini belirleyip **hataayıklama**sekmesi. Tıklatın **başlangıç projesi** ve aşağıdaki olarak göründüğünden emin olun **komut satırı bağımsız değişkenleri** iletişim kutusu.  
  
 `/client:WcfTestClient.exe`  
  
#### <a name="using-a-custom-client"></a>Özel bir istemci kullanma  
 Özel bir istemci kullanmak için projenize sağ **Çözüm Gezgini** Visual Studio'da seçin **özellikleri**seçeneğini belirleyip **hata ayıklama** sekmesi. Tıklatın **başlangıç projesi** ve düzenleme `/client` parametresinde **komut satırı bağımsız değişkenleri** aşağıdaki örnekte gösterildiği gibi özel istemciniz işaret edecek şekilde iletişim kutusu.  
  
 `/client:"path/CustomClient.exe"`  
  
 Hizmeti yeniden başlatmak için F5 tuşuna bastığınızda [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet ana bilgisayarı hata ayıklayıcı başlattığında, özel istemci otomatik olarak başlar.  
  
 Aynı zamanda `/clientArg:` parametresini kullanarak aşağıdaki örnekte gösterildiği gibi özel istemci uygulamaya geçirilen bağımsız değişken olarak bir dize belirtin.  
  
 `/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`  
  
 Örneğin, dağıtım hizmeti kitaplığı şablon kullanıyorsanız, aşağıdaki komut satırı bağımsız değişkenleri kullanabilirsiniz,  
  
 `/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`  
  
#### <a name="specifying-no-client"></a>Hiçbir istemci belirtme  
 Hiçbir istemci sonra kullanılacak belirtmek için [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet barındırma, projenize sağ **Çözüm Gezgini** Visual Studio'da seçin **özellikleri**seçeneğini belirleyip  **Hata ayıklama** sekmesi. Tıklatın **başlangıç projesi** bırakıp **komut satırı bağımsız değişkenleri** iletişim kutusu boş.  
  
#### <a name="using-a-custom-host"></a>Özel bir ana bilgisayar kullanarak  
 Özel bir ana bilgisayar kullanmak için projenize sağ **Çözüm Gezgini** Visual Studio'da seçin **özellikleri**seçeneğini belirleyip **hata ayıklama** sekmesi. Tıklatın **Başlat Dış Program** ve özel ana bilgisayar için tam yolunu girin. Aynı zamanda **komut satırı bağımsız değişkenleri** ana bilgisayara geçirilecek bağımsız değişkenler belirtmek için iletişim kutusu.  
  
## <a name="wcf-service-host-user-interface"></a>WCF hizmet ana kullanıcı arabirimi  
 Başlangıçta çağırma zaman [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (tuşlarına basarak Visual Studio içinde F5), hizmet konağı **WCF hizmet konağı** penceresi otomatik olarak açılır. Zaman [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet ana bilgisayarı çalıştığından, bildirim alanında programın simgesi görünür. Açmak için simgesini çift **WCF hizmet konağı** penceresi  
  
 Barındırma hizmeti sırasında hatalar ortaya çıktığında [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ilgili bilgileri görüntülemek için hizmet ana bilgisayarı iletişim kutusu açılır.  
  
 **WCF hizmet konağı** ana penceresi iki menüleri içerir:  
  
-   **Dosya**: içeren **Kapat** ve **çıkış** komutları. Tıkladığınızda **Kapat**, **WCF hizmet konağı** iletişim kutusu kapanır ancak Hizmetleri barındırılması devam eder. Tıkladığınızda **çıkış**, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmeti ana bilgisayarı ayrıca kapatıldı. Bu aynı zamanda barındırılan tüm hizmetleri durdurur.  
  
-   **Yardım**: içeren **hakkında** sürüm bilgilerini içeren komutu. Ayrıca içerdiği **yardımcı** Yardım dosyasını açabilirsiniz komutu.  
  
 Ana **WCF hizmet konağı** penceresi iki alanları içerir:  
  
-   İlk alan **hizmet**. Tüm hizmetlerin temel bilgileri görüntüleyen bir listesini içerir. Bilgileri içerir:  
  
    -   **Hizmet**: tüm hizmetleri listeler.  
  
    -   **Durum**: Hizmet durumunu listeler. Geçerli değerler "Başlatıldı", "Durduruldu" ve "Error" dir.  
  
    -   **Meta veri adresi**: meta veri adresi hizmetleri görüntüler.  
  
-   İkinci alanı **ek bilgi**. Belirli bir hizmet satırı seçildiğinde hizmet durumunun ayrıntılı bir açıklama görüntüler **hizmet** alan. Hata durumundaysa, tam hata iletisi ekranda görüntüleyebilirsiniz.  
  
## <a name="stopping-wcf-service-host"></a>WCF hizmet ana bilgisayarı durduruluyor  
 Bilgisayarı Kapat [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aşağıdaki dört farklı şekilde hizmet ana bilgisayarı:  
  
-   Visual Studio'da hata ayıklama oturumu durdurun.  
  
-   Seçin **çıkış** gelen **dosya** menüde **WCF hizmet konağı** penceresi.  
  
-   Seçin **çıkış** bağlam menüsünden [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sistem bildirim alanında hizmet ana bilgisayarı Tepsi simgesi.  
  
-   Çıkış [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test kullanılmakta ise, istemci.  
  
## <a name="using-service-host-without-administrator-privilege"></a>Hizmet ana bilgisayarı yönetici ayrıcalığı kullanma  
 Geliştirmek için yönetici ayrıcalığı olmayan kullanıcıların etkinleştirmek için [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hizmetleri, bir ACL (erişim denetim listesi) için ad alanı oluşturulur "http://+:8731/Design_Time_Addresses" Visual Studio yüklemesi sırasında. ACL hangi makineye oturum açmış etkileşimli kullanıcıların tümünü içerir (UI) ayarlanır. Yöneticiler eklemek veya bu ACL'den kaldırmasına veya ek bağlantı noktalarını açın. Bu ACL kullanıcıların kullanmasını sağlayan [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet otomatik yönetici ayrıcalıklarını verme olmadan Konağı (wcfSvcHost.exe).  
  
 Erişim netsh.exe aracını kullanarak değiştirebilirsiniz [!INCLUDE[wv](../../../includes/wv-md.md)] yükseltilmiş yönetici hesabı altında. Netsh.exe kullanmaya ilişkin bir örnek verilmiştir.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Netsh.exe hakkında daha fazla bilgi için bkz: "[Netsh.exe aracı ve komut satırı anahtarları nasıl kullanılacağını](http://go.microsoft.com/fwlink/?LinkId=97877)".  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Test İstemcisi (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
