---
title: Yapılandırma Düzenleme Aracı (SvcConfigEditor.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
ms.openlocfilehash: b026524ad9579b2828765bed39b61383987108d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928576"
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a>Yapılandırma Düzenleme Aracı (SvcConfigEditor.exe)
Windows Communication Foundation (WCF) hizmet yapılandırma Düzenleyicisi (SvcConfigEditor. exe), yöneticilerin ve geliştiricilerin bir grafik kullanıcı arabirimi kullanarak WCF Hizmetleri için yapılandırma ayarlarını oluşturmalarına ve değiştirmesine olanak tanır. Bu araçla, XML yapılandırma dosyalarını doğrudan düzenlemeye gerek kalmadan WCF bağlamaları, davranışlar, hizmetler ve Tanılamalar için ayarları yönetebilirsiniz.  
  
 Hizmet yapılandırma Düzenleyicisi, C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin klasöründe bulunabilir.  
  
## <a name="the-wcf-configuration-editor"></a>WCF yapılandırma Düzenleyicisi  
 Hizmet yapılandırma Düzenleyicisi, WCF hizmeti veya istemcisini yapılandırma içindeki tüm adımlarda size rehberlik eden bir sihirbaz ile birlikte gelir. Doğrudan düzenleyici yerine sihirbazı kullanmanız önemle tavsiye edilir.  
  
 Standart System. Configuration şemasına uyan bazı yapılandırma dosyalarınız varsa, Kullanıcı arabirimiyle bağlamalar, davranış, hizmet ve Tanılamalar için belirli ayarları yönetebilirsiniz. Hizmet yapılandırma Düzenleyicisi, mevcut WCF yapılandırma dosyalarının yanı sıra yürütülebilir dosyalar, COM+ Hizmetleri ve Web 'de barındırılan hizmetler için ayarları yönetmenizi sağlar. Hizmet yapılandırma Düzenleyicisi ile Web 'de barındırılan bir hizmet açılırken, hem hizmetin kendi Yapılandırması hem de üst düzey düğümlerin devralınan yapılandırmalar bölümleri gösterilir.  
  
 WCF yapılandırma ayarları yapılandırma dosyasının `<system.serviceModel>` bölümünde bulunduğundan, düzenleyici özel olarak bu öğenin içeriğinde çalışır ve aynı dosyadaki diğer öğelere erişemez. Mevcut yapılandırma dosyalarına doğrudan gidebilir veya hizmet, sanal dizin veya COM+ hizmeti içeren bir derleme seçebilirsiniz. Düzenleyici, söz konusu hizmet için yapılandırma dosyasını yükler ve kullanıcının yapılandırma dosyasının `<system.serviceModel>` bölümünde iç içe geçmiş öğeleri eklemesini veya varolan öğeleri düzenlemesini sağlar.  
  
 Düzenleyici IntelliSense 'i destekler ve şema uyumluluğunu zorlar. Elde edilen çıktının yapılandırma dosyasının şemasıyla uyumlu olması ve sözdizimsel olarak doğru veri değerlerinin olması garanti edilir. Ancak, düzenleyici yapılandırma dosyasının anlam olarak geçerli olduğunu garanti etmez. Diğer bir deyişle, düzenleyici yapılandırma dosyasının yapılandırdığı hizmet ile çalışabileceğini garanti etmez.  
  
> [!CAUTION]
>  Öğe değiştirildikten sonra düzenleyici yapılandırma dosyasından bir yapılandırma öğesini temizlemez. Örneğin, uç nokta adını boş olmayan bir dizeye ayarlamak ve kaydetmek için düzenleyiciyi kullanırsanız, aşağıdaki örnekte gösterildiği gibi yapılandırma dosyası aşağıdaki içeriğe sahiptir.  
>   
>  `<endpoint binding="basicHttpBinding" name="somename" />`  
>   
>  Adı boş bir dizeye ayarlayarak ve dosyayı kaydettikten sonra, aşağıdaki örnekte gösterildiği gibi yapılandırma dosyası yine de `name` özniteliğini içerir.  
>   
>  `<endpoint binding="basicHttpBinding" name="" />`  
>   
>  Özniteliği temizlemek için, başka bir metin düzenleyicisi kullanarak öğeyi el ile düzenlemeniz gerekir.  
>   
>  `clientCredential` Uç nokta davranışının `issueToken` öğesini kullandığınızda bu sorunla özellikle dikkatli olmanız gerekir. Özellikle, `address` `localIssuer` alt öğesinin özniteliği boş bir dize olmamalıdır. Yapılandırma düzenleyicisini kullanarak `address` özniteliği değiştirdiyseniz ve tamamen kaldırmak istiyorsanız, bunu düzenleyici dışında bir araç kullanarak yapmanız gerekir. Aksi takdirde, öznitelik boş bir dize içerir ve uygulamanız bir özel durum oluşturur.  
  
## <a name="using-the-configuration-editor"></a>Yapılandırma düzenleyicisini kullanma  
 Hizmet yapılandırma Düzenleyicisi, aşağıdaki Windows SDK yükleme konumunda bulunabilir:  
  
 C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe  
  
 Hizmet yapılandırma düzenleyicisini başlattıktan sonra, yönetmek istediğiniz hizmet veya derlemeye gitmek için **dosya/açma** menüsünü kullanabilirsiniz. Yapılandırma dosyalarını doğrudan açabilir, WCF/COM + hizmetlerine gözatabilir ve Web 'de barındırılan hizmetler için yapılandırma dosyalarını açabilirsiniz.  
  
 Hizmet yapılandırma düzenleyicisinin Kullanıcı arabirimi aşağıdaki alanlara ayrılmıştır:  
  
- Sol taraftaki bir ağaç yapısında yapılandırma öğelerini görüntüleyen ağaç görünümü bölmesi. Düğümleri sağ tıklayarak ağaçta işlemleri gerçekleştirebilirsiniz.  
  
- Pencerenin sol alt köşesindeki geçerli öğeler için ortak görevleri görüntüleyen görev bölmesi  
  
- Sağ taraftaki ağaç görünümünde seçilen yapılandırma düğümünün ayrıntılı ayarlarını görüntüleyen ayrıntı bölmesi.  
  
### <a name="opening-a-configuration-file"></a>Yapılandırma dosyası açılıyor  
  
1. WCF yükleme konumunuza gitmek için bir komut penceresi kullanarak hizmet yapılandırma düzenleyicisini başlatın ve ardından yazın `SvcConfigEditor.exe`.  
  
2. **Dosya** menüsünde **Aç** ' ı seçin ve yönetmek istediğiniz dosya türüne tıklayın.  
  
3. **Aç** iletişim kutusunda, yönetmek istediğiniz belirli dosyaya gidin ve çift tıklayın.  
  
 Görüntüleyici otomatik olarak yapılandırma birleştirme yolunu izler ve birleştirilmiş yapılandırmanın bir görünümünü oluşturur. Örneğin, barındırılmayan bir hizmetin gerçek yapılandırması Machine. config ve App. config ' in bir birleşimidir. Tüm değişiklikler, SvcConfigEditor 'daki etkin dosyaya uygulanır. Yapılandırma birleştirme yolundaki belirli bir dosyayı düzenlemek istiyorsanız, doğrudan açmanız gerekir.  
  
> [!NOTE]
> Yapılandırma Düzenleyicisi, ikinci olarak düzenleyici dışında değiştirildiğinde, açılmış olan yapılandırma dosyasını yeniden yükler. Bu durumda, düzenleyicinin içine durmayan tüm değişiklikler kaybolur. Yeniden yükleme sürekli gerçekleşse, en olası nedeni yapılandırma dosyasına sürekli erişen, örneğin arka planda çalışan bir virüsten koruma yazılımı olan bir hizmettir. Bu sorunu çözmek için, yapılandırma Düzenleyicisi 'nin açıldığında dosyaya erişebilen tek işlem olduğundan emin olun.  
  
### <a name="services"></a>Hizmetler  
 **Hizmetler** düğümü, yapılandırma dosyasında şu anda atanmış olan tüm hizmetleri görüntüler. Ağaçtaki her alt düğüm, yapılandırma dosyasında <`services`> öğesinin bir alt öğesine karşılık gelir.  
  
 **Hizmetler** düğümüne tıkladığınızda, **Ayrıntılar** bölmesindeki hizmet Özeti sayfasında görevleri görüntüleyebilir veya yapabilirsiniz.  
  
#### <a name="creating-a-new-service-configuration"></a>Yeni bir hizmet yapılandırması oluşturma  
 Aşağıdaki yollarla yeni bir hizmet yapılandırması oluşturabilirsiniz:  
  
- Sihirbaz kullanarak: **Yeni hizmet oluştur bağlantısına tıklayın...** Sihirbazı başlatmak için görev bölmesinde veya Özet sayfasında. **Dosya** menüsündeki > **Yeni öğe Ekle**' de de yapabilirsiniz.  
  
- El ile oluştur: **Hizmetler** düğümüne sağ tıklayıp **yeni hizmet**' i seçebilirsiniz.  
  
#### <a name="creating-a-new-service-endpoint-configuration"></a>Yeni bir hizmet uç noktası yapılandırması oluşturuluyor  
 Aşağıdaki yollarla yeni bir hizmet uç noktası yapılandırması oluşturabilirsiniz:  
  
- Sihirbaz kullanarak oluşturma: **yeni hizmet uç noktası oluştur** bağlantısına tıklayın... Sihirbazı başlatmak için görev bölmesinde veya Özet sayfasında. **Dosya** menüsündeki > **Yeni öğe Ekle**' de de yapabilirsiniz.  
  
- El ile oluştur: Bir hizmet oluşturduktan sonra, **uç noktalar** düğümüne sağ tıklayıp "**yeni hizmet uç noktası**" seçeneğini belirleyebilirsiniz.  
  
#### <a name="editing-a-service-configuration"></a>Hizmet yapılandırmasını düzenle  
  
1. Bir **hizmet** düğümüne tıklayın.  
  
2. Özellik kılavuzlarında ayarları düzenleyin.  
  
#### <a name="editing-a-service-endpoint-configuration"></a>Hizmet uç noktası yapılandırmasını düzenle  
  
1. **Hizmet uç noktası** düğümüne tıklayın.  
  
2. Özellik kılavuzlarında ayarları düzenleyin.  
  
#### <a name="adding-a-base-address"></a>Temel adres ekleme  
  
1. **Ana bilgisayar** düğümüne tıklayın.  
  
2. **Yeni...** öğesine tıklayın. düğmesini **tıklatın** .  
  
3. İletişim kutusuna taban adresi URI 'sini yazın.  
  
4. **Tamam**'ı tıklatın.  
  
> [!NOTE]
> Bu aracın içindeki [ \<baseAddressPrefixFilters >](../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) değerini düzenleyemezsiniz. Bu öğeyi eklemek veya değiştirmek için bir metin Düzenleyicisi veya Visual Studio kullanmanız gerekir.  
  
### <a name="client"></a>İstemci  
 **İstemci** düğümü, yapılandırma dosyasındaki tüm istemci uç noktalarını görüntüler. Ağaçtaki her alt düğüm, yapılandırma dosyasında <`client`> öğesinin bir alt öğesine karşılık gelir.  
  
 **İstemci** düğümüne tıkladığınızda, **Ayrıntılar bölmesindeki**istemci **Özeti sayfasında** görevleri görüntüleyebilir veya yapabilirsiniz.  
  
#### <a name="creating-a-new-client-endpoint-configuration"></a>Yeni Istemci uç noktası yapılandırması oluşturma  
 Aşağıdaki yollarla yeni bir istemci uç noktası yapılandırması oluşturabilirsiniz:  
  
- Sihirbaza göre oluştur: **Yeni Istemci oluştur bağlantısına tıklayın...** Sihirbazı başlatmak için pencerenin sol alt kısmındaki **görev bölmesinde** veya **Özet sayfasında** . **Dosya** menüsündeki > **Yeni öğe Ekle**' de de yapabilirsiniz. Sihirbaz, istemci yapılandırmasının oluşturulduğu hizmet yapılandırmasının konumunu işaret etmesini ister. Daha sonra, bağlanılacak hizmet uç noktasını seçebilirsiniz.  
  
- El ile oluştur: **İstemci**altındaki **uç noktalar** düğümüne sağ tıklayın ve **yeni istemci uç noktası**' nı seçin.  
  
#### <a name="editing-a-client-endpoint-configuration"></a>Istemci uç noktası yapılandırmasını düzenle  
  
1. **Istemci uç noktası** düğümüne tıklayın.  
  
2. Özellik kılavuzlarında ayarları düzenleyin.  
  
### <a name="standard-endpoint"></a>Standart uç nokta  
 Standart uç noktalar, adresin, sözleşmenin ve bağlamanın bir veya daha fazla yönü varsayılan değerlere ayarlanmış olan özel uç noktalardır.  
  
 Bu tür yapılandırma ayarları **standart uç nokta** düğümünde depolanır. **Standart uç nokta** düğümü yapılandırma dosyasındaki tüm standart uç nokta ayarlarını görüntüler. Ağaçtaki her alt düğüm, yapılandırma dosyasındaki `<standardEndpoints>` öğesindeki bir alt öğeye karşılık gelir.  
  
 **Standart uç nokta** düğümüne tıkladığınızda, **Ayrıntılar bölmesindeki**standart uç nokta **Özeti sayfasında** görevleri görüntüleyebilir veya yapabilirsiniz.  
  
#### <a name="creating-a-new-standard-endpoint-configuration"></a>Yeni bir standart uç nokta yapılandırması oluşturma  
 Aşağıdaki yollarla yeni bir standart uç nokta yapılandırması oluşturabilirsiniz:  
  
- **Standart uç nokta** düğümüne sağ tıklayın ve **Yeni standart uç nokta yapılandırması ' nı seçin...** İletişim kutusunda bağlama türünü seçin ve **Tamam**' ı tıklatın.  
  
- **Standart uç nokta** düğümünü seçin ve **Yeni standart uç nokta yapılandırması...** öğesine tıklayın. pencerenin sol alt kısmındaki **görev bölmesinde** .  
  
 **Yeni bir standart uç nokta oluşturma** iletişim kutusu, tüm kayıtlı standart uç nokta türlerini görüntüler ve listeler.  
  
#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a>Standart uç nokta yapılandırmasını görüntüleme ve düzenlemeyle  
 Aşağıdaki yollarla görüntüleme ve düzenlemeyle ilgili standart bir uç nokta yapılandırması açabilirsiniz:  
  
- **Standart uç nokta** düğümünü genişletmek için tıklayın ve ilgili uç nokta alt düğümüne tıklayın.  
  
- **Standart uç nokta** düğümüne tıklayın ve Ayrıntılar bölmesinde ilgili uç noktaya tıklayın.  
  
 Uç nokta öznitelikleri, düzenlemenin sağ bölmesinde gösterilir.  
  
#### <a name="deleting-a-standard-endpoint-configuration"></a>Standart uç nokta yapılandırmasını silme  
 Standart uç nokta yapılandırmasını aşağıdaki yollarla silebilirsiniz:  
  
- **Standart uç nokta** düğümünü genişletmek için tıklayın ve ilgili uç nokta alt düğümüne sağ tıklayın. Uç noktayı silmek için **standart uç nokta yapılandırmasını silme** bağlam komutunu kullanın.  
  
- **Standart uç nokta** düğümüne tıklayın. **Görev** bölmesinde **standart uç nokta yapılandırmasını sil**' e tıklayın.  
  
 Standart uç nokta kullanılıyorsa, onu silmeye çalıştığınızda bir uyarı iletisi görüntülenir: **Standart uç nokta kullanımda. Şimdi silerseniz, lütfen yapılandırmanın diğer bölümlerinde (örneğin, hizmet uç noktası veya istemci uç noktasında) tüm başvurularını sildiğinizden emin olun. Aksi takdirde, yapılandırma geçersiz olur ve bir dahaki sefer açılamaz. Standart uç noktayı silmek istediğinizden emin misiniz? "**  
  
### <a name="binding"></a>Bağlama  
 Bağlama yapılandırması uç noktalarda bağlamaları yapılandırmak için kullanılır. Bu tür yapılandırma ayarları **bağlama** düğümünde depolanır. Ada ve birden çok uç noktaya göre bağlantı yapılandırmaları için uç noktalar tek bir bağlama yapılandırmasına başvurabilir.  
  
 **Bağlamalar** düğümü yapılandırma dosyasındaki tüm bağlama ayarlarını görüntüler. Ağaçtaki her alt düğüm, yapılandırma dosyasındaki <`bindings`> öğesinde bir alt öğeye karşılık gelir.  
  
 **Bağlamalar** düğümüne tıkladığınızda, **Ayrıntılar bölmesindeki**bağlama **Özeti sayfasında** görevleri görüntüleyebilir veya yapabilirsiniz.  
  
#### <a name="creating-a-new-binding-configuration"></a>Yeni bir bağlama yapılandırması oluşturma  
 Aşağıdaki yollarla yeni bir bağlama yapılandırması oluşturabilirsiniz.  
  
- **Bağlamalar** düğümüne sağ tıklayın ve **yeni bağlama yapılandırması**' nı seçin... İletişim kutusunda bağlama türünü seçin ve **Tamam**' ı tıklatın.  
  
- **Bağlamalar** düğümünü seçin ve **yeni bağlama yapılandırması**... öğesine tıklayın. pencerenin sol alt kısmındaki **görev bölmesinde** .  
  
- Hizmet veya istemci Özeti sayfasında, ilgili uç nokta için bir bağlama yapılandırması oluşturmak üzere **bağlama yapılandırması** alanında **oluşturmak için tıklama** ' ye tıklayın.  
  
#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a>Özel bağlamaya bağlama öğesi uzantıları ekleme  
  
1. Uzantı öğesi eklemek istediğiniz bağlamayı seçin.  
  
2. **Ekle**'yi tıklatın.  
  
3. Kullanılabilir uzantılar listesinden eklemek istediğiniz bağlama öğesi uzantısını seçin. Birden çok öğe seçmek için CTRL tuşuna aynı anda basın.  
  
4. **Ekle**'yi tıklatın.  
  
#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a>Özel bağlamadaki uzantı konumunu ayarlama  
 Özel bağlama bir yığın oluşturan bağlama öğelerinin koleksiyonudur. Yığındaki her bağlama öğesinin kendi yapılandırma ayarları vardır. Özel bağlamadaki bağlama öğesi uzantılarının sırası, yığındaki konumlarını gösterir. Yığının en üstünde bulunan öğeler önce uygulanır. Sıralamayı değiştirmek için:  
  
1. Özel bağlama düğümünü seçin.  
  
2. **Bağlama öğesi uzantı konumu** bölümünde bir bağlama uzantı öğesi seçin.  
  
3. Seçili öğenin konumunu değiştirmek için listenin sol tarafındaki **yukarı** veya **aşağı** düğmesini kullanın.  
  
#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a>Özel bağlamadaki bağlama öğesi uzantılarının yapılandırmasını düzenle  
  
1. Ağaçtaki bağlama düğümünü seçin.  
  
2. Düzenlemek istediğiniz öğeyi içeren özel bağlamayı seçin.  
  
3. Düzenlemek istediğiniz bağlama öğesi uzantısını seçin. Öğe ayarları sağ bölmede görünür ve burada düzenlenebilirler.  
  
### <a name="diagnostics"></a>Tanılamalar  
 **Tanılama** düğümü yapılandırma dosyasındaki tüm tanılama ayarlarını görüntüler. Performans sayaçlarını açıp kapamanızı, Windows Yönetim Araçları (WMI) etkinleştirebilir veya devre dışı bırakmanızı, WCF izlemeyi yapılandırmanızı ve WCF ileti günlüğe kaydetmeyi yapılandırmanızı sağlar. **Tanılama** düğümündeki ayarlar`system.diagnostics` ,yapılandırma`<diagnostics>` dosyasında < > bölümüne ve bölümüne karşılıkgelir.`<system.serviceModel>`  
  
 **Tanılama** düğümüne tıkladığınızda, **Ayrıntılar bölmesindeki**tanılama **Özeti sayfasında** görevleri görüntüleyebilir veya yapabilirsiniz.  
  
#### <a name="configuring-performance-counters-and-wmi"></a>Performans sayaçlarını ve WMI 'yi yapılandırma  
  
1. **Tanılama** düğümüne tıklayın.  
  
2. **Performans sayaçlarını aç**' a tıklayın. Performans sayacının üç durumu vardır: Kapalı (varsayılan), ServiceOnly ve ALL. Bağlantıya tıkladığınızda bu üç durum arasındaki ayar geçiş yapar.  
  
#### <a name="configuring-wmi-provider"></a>WMI sağlayıcısını yapılandırma  
  
1. **Tanılama** düğümüne tıklayın.  
  
2. WMI sağlayıcısını etkinleştirmek için **WMI sağlayıcısını etkinleştir** bağlantısına tıklayın.  
  
#### <a name="enabling-wcf-tracing"></a>WCF Izlemeyi etkinleştirme  
 Standart özelliklerle bir WCF izleme dosyası oluşturabilir veya özel bir izleme dosyası ayarlayabilirsiniz.  
  
1. **Tanılama** düğümüne tıklayın.  
  
2. **Izlemeyi etkinleştir**' e tıklayın.  
  
3. İzleme düzeyini ayarlamak için **Izleme düzeyi** bağlantısına tıklayın. Altı izleme düzeyi vardır: Kapalı, kritik, hata, uyarı, bilgi ve ayrıntılı. **Etkinlik izleme** ve **yayma ETKINLIĞI** seçeneği, WCF etkinlik izleme özelliğini kullanmanıza olanak sağlar.  
  
4. İzleme dosyasını ve seçeneklerini belirtmek için izleme dinleyicisi adına tıklayın.  
  
#### <a name="enabling-wcf-logging"></a>WCF günlüğü etkinleştiriliyor  
 Standart özelliklerle bir WCF izleme dosyası oluşturabilir veya özel bir izleme dosyası ayarlayabilirsiniz.  
  
1. **Tanılama** düğümüne tıklayın.  
  
2. **Ileti günlüğe kaydetmeyi etkinleştir**' e tıklayın.  
  
3. Günlük düzeyini ayarlamak için **günlük düzeyi** bağlantısına tıklayın. Üç günlük düzeyi vardır: Hatalı biçimlendirilmiş, hizmet ve aktarım.  
  
4. Günlük dosyasını ve seçeneklerini belirtmek için dinleyici adına tıklayın.  
  
> [!NOTE]
> Uygulamanız kapatıldığında izleme ve ileti günlüklerinin otomatik olarak **temizlenmesi Istiyorsanız otomatik temizleme** seçeneğini etkinleştirin.  
  
 **Tanılama** **Özeti sayfası** , tanılamayı yapılandırırken en sık kullanılan görevleri gerçekleştirmenize olanak sağlar. Ancak, dinleyicileri ve kaynak ayarlarını el ile düzenlemek isterseniz, **Tanılama** düğümünü genişletmeli ve **ileti günlüğe kaydetme**, **dinleyiciler** ve **kaynaklar** düğümündeki ayarları düzenlemelisiniz.  
  
#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a>WCF özel Izleme veya Ileti günlüğe kaydetme etkinleştiriliyor  
  
1. **Tanılama** düğümüne tıklayın ve genişletin.  
  
2. **Dinleyiciler** düğümüne sağ tıklayın ve **Yeni dinleyici**' i seçin.  
  
3. **InitData** alanına izleme dosyası adını yazın. "..." Düğmesine tıklayabilirsiniz bir yola gözatmaya yönelik düğme.  
  
4. **TypeName** satırına tıkladığınızda bir "..." görüntülenir Bu. Zaten yüklü olan önceden yapılandırılmış izleme dinleyicilerini bulmak için kullanabileceğiniz **Izleme dinleyicisi türü tarayıcısını**açmak için bu düğmeye tıklayın.  
  
5. **Kaynak** bölümüne göz önünde edin. Kullanılabilir izleme kaynaklarını listeleyen açılan menü içeren bir iletişim kutusu açmak için bu bölümde **Ekle** ' ye tıklayın. Bir izleme kaynağı seçip **Tamam**' a tıklayın.  
  
6. Ileti günlüğe kaydetme ayarlarını düzenlemek için **Ileti günlüğe kaydetme** düğümüne tıklayın. Özellik kılavuzundaki ayarları düzenleyebilirsiniz.  
  
### <a name="advanced"></a>Gelişmiş  
  
#### <a name="behaviors"></a>Davranışlar  
 **Davranışlar** düğümü, yapılandırma dosyasında şu anda tanımlanan davranışları görüntüler.  
  
 Davranış yapılandırması, uç noktaların ve hizmetlerin davranışlarını yapılandırmak için kullanılır. Bu tür yapılandırma ayarları, **Gelişmiş** düğümde **hizmet davranışları** ve **uç nokta davranışları**altında depolanır. Hizmet davranışları hizmetler tarafından kullanılır; uç nokta davranışları uç noktalara göre.  
  
 Davranışlar, yığın için bir genişletme öğelerinin koleksiyonudur. Yığının en üstünde bulunan öğe önce uygulanır. Her uzantı öğesi kendi yapılandırmasına sahip olabilir.  
  
##### <a name="creating-a-new-behavior-configuration"></a>Yeni davranış yapılandırması oluşturma  
 İki şekilde yeni bir davranış yapılandırması oluşturabilirsiniz.  
  
- Davranış düğümlerinden birine sağ tıklayın ve "**Yeni davranış yapılandırması..** ." seçeneğini belirleyin.  
  
- Davranış düğümlerinden birini seçin ve **Yeni davranış yapılandırmasına**tıklayın... pencerenin sol alt kısmındaki **görev bölmesinde** .  
  
##### <a name="adding-behavior-element-extensions-to-a-behavior"></a>Davranışa davranış öğesi uzantıları ekleme  
  
1. Davranış düğümlerinden birini seçin.  
  
2. Düzenlemek istediğiniz davranışı seçin.  
  
3. **Ekle**'yi tıklatın.  
  
4. Kullanılabilir uzantılar listesinden eklemek istediğiniz davranış öğesi uzantısını seçin.  
  
5. **Ekle**'yi tıklatın.  
  
##### <a name="adjusting-the-extension-position-in-a-behavior"></a>Uzantı konumunu bir davranışta ayarlama  
 Davranışlar, yığın oluşturan öğelerin koleksiyonlarıdır. Yığındaki her bir öğenin kendi yapılandırması vardır. Davranış öğesi uzantılarının bir davranıştaki sırası yığındaki konumlarını gösterir. Yığının en üstünde bulunan öğeler önce uygulanır. Sıralamayı değiştirmek için:  
  
1. Davranış düğümlerinden birini seçin.  
  
2. Düzenlemek istediğiniz davranışı seçin.  
  
3. **Davranış öğesi uzantısı konumu** bölümünde bir davranış uzantısı öğesi seçin.  
  
4. Seçili öğenin konumunu değiştirmek için listenin sol tarafındaki **yukarı** veya **aşağı** düğmesini kullanın.  
  
##### <a name="editing-the-configuration-of-behavior-element-extensions"></a>Davranış öğesi uzantılarının yapılandırmasını düzenle  
  
1. Ağaçtaki davranış düğümlerinden birini seçin.  
  
2. Düzenlemek istediğiniz öğeyi içeren davranışı seçin.  
  
3. Düzenlemek istediğiniz davranış öğesi uzantısını seçin. Öğenin ayarları, düzenlenebilecekleri sağ bölmede görüntülenir.  
  
#### <a name="protocolmapping"></a>ProtocolMapping  
 Bu bölüm, protokol adres şemaları ve olası bağlamalar arasında tanımlı eşleme aracılığıyla http, TCP, MSMQ veya net. pipe gibi farklı protokoller için varsayılan bağlama türlerini ayarlamanıza olanak sağlar. Ayrıca diğer protokollere yeni eşlemeler ekleyebilirsiniz.  
  
#### <a name="extensions"></a>Uzantıları  
 Yeni bağlama uzantıları, bağlama öğesi uzantıları, standart uç nokta uzantıları ve davranış uzantıları, WCF yapılandırmasında kullanılmak üzere kaydedilebilir. Uzantılar ad/tür çiftleridir. Ad, yapılandırmada uzantının adını tanımlar, ancak tür uzantıyı uygular. Dört tür uzantı vardır:  
  
- Bağlama uzantıları, tüm bağlama türünü tanımlar. Örnek: `basicHttpBinding`.  
  
- Bağlama öğesi uzantıları bağlama bir öğesi tanımlar. Örnek: `textMessageEncoding`.  
  
- Standart uç nokta uzantıları tüm standart uç noktayı tanımlar. Örnek: `discoveryEndpoint`.  
  
- Davranış öğesi uzantıları bir davranışın öğesini tanımlar. Örnek: `clientVia`.  
  
 Yapılandırmada kayıtlı olan uzantılar aynı türdeki diğer WCF bileşenleri gibi kullanılabilir.  
  
##### <a name="adding-a-new-extension"></a>Yeni uzantı ekleme  
 Gelişmiş düğümlerdeki uzantı düğümlerinden birini seçin:  
  
1. **Yeni**'yi tıklatın.  
  
2. Bir ad girin ve yazın.  
  
3. **Tamam**'ı tıklatın.  
  
4. Uzantı artık düzenleyicide uygun yerde görüntülenir. Örneğin, bir davranış öğesi uzantısı eklerseniz, kullanılabilir Uzantılar listesinde görünür.  
  
#### <a name="hosting-environment"></a>Barındırma ortamı  
 Bu bölüm, hizmet barındırma ortamı için örnek oluşturma ayarlarını tanımlamanızı sağlar.  
  
### <a name="creating-a-configuration-file-using-the-wizard"></a>Sihirbazı kullanarak yapılandırma dosyası oluşturma  
 Yeni bir yapılandırma dosyası oluşturmanın bir yolu, yeni hizmet öğesi Sihirbazı 'nı kullanmaktır. Sihirbaz, yüklü hizmet türlerini ve bilgisayarda WCF ile uyumlu diğer öğeleri bulur (COM+ ve Web 'de barındırılan sanal dizinler dahil) ve yapılandırmayı çok daha kolay bir şekilde oluşturmak için yükler.  
  
#### <a name="creating-a-configuration-file"></a>Yapılandırma dosyası oluşturma  
  
1. WCF yükleme konumunuza gitmek için bir komut penceresi kullanarak hizmet yapılandırma düzenleyicisini başlatın ve ardından yazın `SvcConfigEditor.exe`.  
  
2. **Dosya** menüsünde **Aç** ' ı seçin ve ardından, oluşturmak istediğiniz yapılandırma dosyasının türüne bağlı olarak **yürütülebilir**, **com+ hizmeti**veya **webhosted Service**' i tıklatın.  
  
3. **Aç** iletişim kutusunda, bir yapılandırma dosyası oluşturmak istediğiniz belirli dosyaya gidin ve çift tıklayın.  
  
4. **Dosya** menüsünde, **Yeni öğe Ekle** ' nin üzerine gelin ve **hizmet**' e tıklayın. Yeni hizmet öğesi Sihirbazı açılır.  
  
5. Yeni hizmeti oluşturmak için sihirbazdaki adımları izleyin.  
  
> [!NOTE]
> Sihirbaz tarafından oluşturulan yapılandırma dosyasından NetPeerTcpBinding kullanmak istiyorsanız, bir bağlama yapılandırma öğesini el ile eklemeniz ve `mode` `security` öğesinin özniteliğini "none" olarak değiştirmeniz gerekir.  
  
## <a name="configuring-com"></a>COM+ yapılandırılıyor  
 Hizmet yapılandırma Düzenleyicisi, var olan bir COM+ uygulaması için yeni bir yapılandırma dosyası oluşturmanızı veya mevcut bir COM+ yapılandırmasını düzenlemenizi sağlar. **Com sözleşmesi** düğümü yalnızca yapılandırma dosyasında <`comContract`> bölümü varsa görünür.  
  
### <a name="creating-a-new-com-configuration"></a>Yeni COM+ Yapılandırması Oluşturma  
 Yeni bir COM+ Yapılandırması oluşturmadan önce, COM+ uygulamanızın Bileşen Hizmetleri 'nde yüklü olduğundan ve genel derleme önbelleği 'ne (GAC) kayıtlı olduğundan emin olun.  
  
1. **Dosya** menüsünü seçin-> -> **com+ uygulamasını tümleştirin.** Bu işlem, geçerli açılan dosyayı kapatır. Geçerli dosyada kaydedilmemiş veriler varsa, bir Kaydet iletişim kutusu görüntülenir. Ardından **com+ Tümleştirme Sihirbazı** başlatılır.  
  
2. İlk sayfada, ağaçtan COM+ uygulamasını seçin. COM+ uygulamanızı ağaçta bulamıyorsanız bileşen hizmetlerinde yüklü olduğunu ve genel derleme önbelleği 'ne (GAC) kayıtlı olduğunu doğrulayın.  
  
3. Sonraki sayfada, WCF Hizmetleri olarak göstermek istediğiniz yöntemi seçin. COM+ uygulamasındaki tüm desteklenen yöntemler varsayılan olarak görüntülenir ve seçilir.  
  
4. Bir barındırma yöntemi seçin.  
  
5. Sihirbazdaki kılavuzlara göre diğer ayarları yapılandırın.  
  
6. Hizmet yapılandırma Düzenleyicisi, yapılandırma dosyası oluşturmak için arka planda ComSvcConfig. exe ' yi kullanır. Bu tamamlandıktan sonra bir özeti görüntüleyebilir ve sihirbazdan çıkabilirsiniz. Oluşturulan yapılandırma dosyası, doğrudan düzenleyebilmeniz için açılır.  
  
### <a name="editing-an-existing-com-configuration"></a>Var olan bir COM+ yapılandırmasını düzenle  
  
1. **Dosya** menüsünü seçin->**com+ hizmetini** **açın** -> ...  
  
2. Listeden düzenlemek istediğiniz COM+ hizmetini seçin.  
  
3. **Com sözleşmeleri** düğümündeki yapılandırma ayarlarını düzenleyin.  
  
    > [!NOTE]
    > Ayrıca, COM sözleşmeleri içeren bir yapılandırma dosyasını doğrudan açabilir ve düzenleyebilirsiniz.  
  
## <a name="security"></a>Güvenlik  
 Yapılandırma Düzenleyicisi tarafından oluşturulan bir hizmet yapılandırma dosyasının güvenli olması garanti edilmez. WCF hizmetlerinizi güvenli hale getirme hakkında bilgi edinmek için lütfen [güvenlik](../../../docs/framework/wcf/feature-details/security.md) belgelerine bakın.  
  
 Ayrıca, yapılandırma Düzenleyicisi yalnızca geçerli WCF yapılandırma öğelerini okumak ve yazmak için kullanılabilir. Araç, şema uyumlu, Kullanıcı tanımlı öğeleri yoksayar. Ayrıca, bu öğeleri yapılandırma dosyasından kaldırmayı veya bilinen WCF öğelerinde etkilerini belirlemeyi denemez. Bu öğelerin uygulama veya sistem için tehdit oluşturmadığını belirleme kullanıcının sorumluluğundadır.
