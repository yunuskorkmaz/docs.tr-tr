---
title: WCF Hizmet Ana Bilgisayarı (WcfSvcHost.exe)
ms.date: 03/30/2017
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
ms.openlocfilehash: c855fe7cc804fac14348990b7a6f5f84a0956b0c
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802416"
---
# <a name="wcf-service-host-wcfsvchostexe"></a>WCF Hizmet Ana Bilgisayarı (WcfSvcHost.exe)

Windows Communication Foundation (WCF) hizmet ana bilgisayarı (WcfSvcHost. exe), uyguladık bir hizmeti otomatik olarak barındırmak ve test etmek için Visual Studio hata ayıklayıcısını (F5) başlatmanıza olanak tanır. Olası hataları bulmak ve onarmak için WCF test Istemcisi (WcfTestClient. exe) veya kendi istemcinizi kullanarak hizmeti test edebilirsiniz.

## <a name="wcf-service-host"></a>WCF hizmet konağı

WCF hizmet konağı bir WCF Hizmeti projesini Hizmetleri'nde numaralandırır, projenin yapılandırması yükler ve bulduğu her hizmet için bir ana bilgisayar örneği oluşturur. Araç, WCF hizmeti şablonu aracılığıyla Visual Studio ile tümleşiktir ve projenizde hata ayıklamaya başladığınızda çağrılır.

WCF hizmet ana bilgisayarını kullanarak, ek kod yazmadan veya geliştirme sırasında belirli bir konağa işlemeden bir WCF hizmetini (bir WCF hizmet kitaplığı projesinde) barındırabilirsiniz.

> [!NOTE]
> WCF hizmeti ana bilgisayarı kısmi güveni desteklemez. Kısmi güvende bir WCF hizmeti kullanmak istiyorsanız, Visual Studio 'da WCF hizmet kitaplığı proje şablonunu kullanarak hizmetinizi oluşturun. Bunun yerine, WCF hizmeti Web sitesi şablonunu seçerek Visual Studio 'da yeni bir Web sitesi oluşturun ve bu hizmet, WCF kısmi güveninin desteklendiği bir Web sunucusu içinde hizmeti barındırabilir.

## <a name="project-types-hosted-by-wcf-service-host"></a>WCF hizmet ana bilgisayarı tarafından barındırılan proje türleri

WCF hizmet ana bilgisayarı şu WCF hizmet kitaplığı proje türlerini barındırabilir: WCF hizmet kitaplığı, sıralı Iş akışı hizmet kitaplığı, durum makinesi Iş akışı hizmet kitaplığı ve dağıtım hizmeti kitaplığı. WCF hizmet ana makinesi Ayrıca, **öğe Ekle** işlevselliği kullanılarak bir hizmet kitaplığı projesine eklenebilen bu hizmetleri barındırabilir. Buna WCF hizmeti, WF durum makinesi hizmeti, WF sıralı hizmeti, XAML WF durum makinesi hizmeti ve XAML WF sıralı hizmeti dahildir.

Ancak, aracın bir konağı yapılandırmanıza yardımcı olamayacağını unutmayın. Bu görev için App. config dosyasını el ile düzenlemeniz gerekir. Araç, Kullanıcı tanımlı yapılandırma dosyalarını da doğrulamaz.

> [!CAUTION]
> Bu amaçla mühendislik olmadığından, bir üretim ortamında Hizmetleri barındırmak için WCF hizmet konağını kullanmamalısınız.  WCF hizmet ana bilgisayarı, böyle bir ortamın güvenilirlik, güvenlik ve yönetilebilirlik gereksinimlerini desteklemez. Bunun yerine IIS 'yi, üstün güvenilirlik ve izleme özellikleri sağladığından ve barındırma hizmetleri için tercih edilen çözüm olduğundan kullanın. Hizmetlerinizin geliştirilmesi tamamlandıktan sonra, Hizmetleri WCF hizmet ana bilgisayardan IIS 'ye geçirmeniz gerekir.

## <a name="scenarios-for-using-wcf-service-host-inside-visual-studio"></a>Visual Studio içinde WCF hizmeti ana bilgisayarını kullanmaya yönelik senaryolar

Aşağıdaki tabloda, Visual Studio 'daki **Çözüm Gezgini** ' nde projenize sağ tıklanarak **Özellikler**' i seçip, ardından **Hata Ayıkla** sekmesini seçip **projeyi Başlat**' a tıklayarak bulunan **komut satırı bağımsız değişkenleri** iletişim kutusundaki tüm parametreler listelenmektedir. Bu parametreler, WCF hizmeti ana bilgisayarını yapılandırmada yararlıdır.

|Parametre|Açıklama|
|---------------|-------------|
|`/client`|Hizmetler barındırıldıktan sonra çalıştırılacak bir çalıştırılabilir dosyanın yolunu belirten isteğe bağlı bir parametre. Bu, barındırma sonrasında WCF test Istemcisini başlatır.|
|`/clientArg`|Özel istemci uygulamasına geçirilen bağımsız değişken olarak bir dize belirtin.|
|`/?`|Yardım metnini görüntüler.|

#### <a name="using-wcf-test-client"></a>WCF test Istemcisi kullanma

Yeni bir WCF hizmeti projesi oluşturduktan ve hata ayıklayıcıyı başlatmak için F5 'e bastıktan sonra, WCF hizmet ana bilgisayarı projenizde bulduğu tüm hizmetleri barındırmaya başlar. WCF test Istemcisi otomatik olarak açılır ve yapılandırma dosyasında tanımlanan hizmet uç noktalarının listesini görüntüler. Ana pencereden, parametreleri test edebilir ve hizmetinizi çağırabilirsiniz.

WCF test Istemcisinin kullanıldığından emin olmak için, Visual Studio 'da **Çözüm Gezgini** ' nde projenize sağ tıklayın, **Özellikler**' i seçin ve ardından **Hata Ayıkla** sekmesini seçin. **projeyi Başlat** ' a tıklayın ve **komut satırı bağımsız değişkenleri** iletişim kutusunda aşağıdakilerin göründüğünden emin olun.

`/client:WcfTestClient.exe`

#### <a name="using-a-custom-client"></a>Özel Istemci kullanma

Özel bir istemci kullanmak için, Visual Studio 'da **Çözüm Gezgini** ' nde projenize sağ tıklayın, **Özellikler**' i seçin ve ardından **Hata Ayıkla** sekmesini seçin. **projeyi Başlat** ' a tıklayın ve **komut satırı bağımsız değişkenleri** iletişim kutusunda `/client` parametresini düzenleyerek aşağıdaki örnekte gösterildiği gibi özel istemcinizi işaret edin.

`/client:"path/CustomClient.exe"`

Hizmeti yeniden başlatmak için F5 tuşuna bastığınızda, hata ayıklayıcıyı başlattığınızda WCF hizmeti ana bilgisayarı otomatik olarak özel istemcinizi başlatır.

Aşağıdaki örnekte gösterildiği gibi, özel istemci uygulamasına geçirilen bir bağımsız değişken olarak bir dize belirtmek için `/clientArg:` parametresini de kullanabilirsiniz.

`/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`

Örneğin, dağıtım hizmeti kitaplık şablonunu kullanıyorsanız, aşağıdaki komut satırı bağımsız değişkenlerini kullanabilirsiniz,

`/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`

#### <a name="specifying-no-client"></a>Istemci belirtme

WCF hizmeti barındırma sonrasında hiçbir istemci kullanılmayacağını belirtmek için, Visual Studio 'da **Çözüm Gezgini** ' nde projenize sağ tıklayın, **Özellikler**' i seçin ve ardından **Hata Ayıkla** sekmesini seçin. **projeyi Başlat** ' a tıklayın ve **komut satırı bağımsız değişkenleri** iletişim kutusunu boş bırakın.

#### <a name="using-a-custom-host"></a>Özel ana bilgisayar kullanma

Özel bir konak kullanmak için, Visual Studio 'da **Çözüm Gezgini** ' nde projenize sağ tıklayın, **Özellikler**' i seçin ve ardından **Hata Ayıkla** sekmesini seçin. **dış program Başlat** ' a tıklayın ve özel konağın tam yolunu girin. Ayrıca, konağa geçirilecek bağımsız değişkenleri belirtmek için **komut satırı bağımsız değişkenleri** iletişim kutusunu da kullanabilirsiniz.

## <a name="wcf-service-host-user-interface"></a>WCF hizmet Konağı Kullanıcı arabirimi

WCF hizmeti ana bilgisayarını ilk kez çağırdığınızda (Visual Studio içinde F5 tuşuna basarak), **WCF hizmeti ana bilgisayar** penceresi otomatik olarak açılır. WCF hizmeti ana bilgisayarı çalışırken, bildirim alanında programın simgesi görüntülenir. **WCF hizmeti ana bilgisayar** penceresini açmak için simgeye çift tıklayın

Hizmet barındırma sırasında hatalar oluştuğunda, ilgili bilgileri göstermek için WCF hizmeti ana bilgisayarı iletişim kutusu açılır.

**WCF hizmet ana bilgisayarı** ana penceresi iki menü içerir:

- **Dosya**: **Close** ve **Exit** komutlarını içerir. **Kapat**' a tıkladığınızda, **WCF hizmet ana bilgisayarı** iletişim kutusu kapanır, ancak hizmetler barındırılmasına devam eder. **Çıkış**' a tıkladığınızda, WCF hizmeti ana bilgisayarı da kapanır. Bu ayrıca tüm barındırılan hizmetleri de sonlandırır.

- **Yardım**: sürüm bilgilerini içeren **hakkında** komutunu içerir. Ayrıca bir yardım dosyası açabilme **Yardım** komutunu da içerir.

Ana **WCF hizmeti ana bilgisayar** penceresi iki alan içerir:

- İlk alan **hizmettir**. Tüm hizmetlerin temel bilgilerini görüntüleyen bir liste içerir. Bilgiler şunları içerir:

  - **Hizmet**: tüm hizmetleri listeler.

  - **Durum**: hizmetin durumunu listeler. Geçerli değerler şunlardır "başlatıldı", "durduruldu" ve "hata".

  - **Meta veri adresi**: hizmetlerin meta veri adresini görüntüler.

- İkinci alan **ek bilgi**. **Hizmet alanında belirli** bir hizmet satırı seçildiğinde hizmet durumunun ayrıntılı bir açıklamasını görüntüler. Durum hata ise, ekranda tam hata iletisini görebilirsiniz.

## <a name="stopping-wcf-service-host"></a>WCF hizmet ana bilgisayarı durduruluyor

Aşağıdaki dört şekilde WCF hizmet konağını kapatabilirsiniz:

- Visual Studio 'da hata ayıklama oturumunu durdurun.

- **WCF hizmeti ana bilgisayar** penceresindeki **Dosya** menüsünden **Çıkış** ' ı seçin.

- Sistem bildirim alanındaki WCF hizmeti ana bilgisayar tepsisi simgesinin bağlam menüsünden **Çıkış** ' ı seçin.

- Kullanılıyorsa WCF test Istemcisinden çıkın.

## <a name="using-service-host-without-administrator-privilege"></a>Hizmet ana bilgisayarını yönetici ayrıcalığı olmadan kullanma

Yönetici ayrıcalıkları olmayan kullanıcıların WCF Hizmetleri geliştirmesine olanak tanımak için, Visual Studio yüklemesi sırasında "http://+:8731/Design_Time_Addresses" ad alanı için bir ACL (Access Control listesi) oluşturulur. ACL, makinede oturum açmış tüm etkileşimli kullanıcıları içeren (UI) olarak ayarlanır. Yöneticiler bu ACL 'ye kullanıcı ekleyebilir veya kaldırabilir veya ek bağlantı noktaları açabilir. Bu ACL, kullanıcıların, yönetici ayrıcalıkları vermeden WCF hizmeti otomatik ana bilgisayarını (wcfSvcHost. exe) kullanmasına olanak sağlar.

Erişimi, yükseltilmiş yönetici hesabı altındaki [!INCLUDE[wv](../../../includes/wv-md.md)] Netsh. exe aracını kullanarak değiştirebilirsiniz. Netsh. exe ' nin kullanılmasına bir örnek aşağıda verilmiştir.

```console
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>
```

Netsh. exe hakkında daha fazla bilgi için "[netsh. exe aracını ve komut satırı anahtarlarını kullanma](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10))" konusuna bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Test İstemcisi (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
