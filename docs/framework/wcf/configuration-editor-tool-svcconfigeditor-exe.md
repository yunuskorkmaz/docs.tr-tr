---
title: Yapılandırma Düzenleme Aracı (SvcConfigEditor.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
ms.openlocfilehash: e2b28ae65c7c5769f3be5c294fc3667b5ba4a651
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64652120"
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a>Yapılandırma Düzenleme Aracı (SvcConfigEditor.exe)
Yöneticiler ve geliştiriciler oluşturmak ve bir grafik kullanıcı arabirimi kullanarak WCF hizmetleri için yapılandırma ayarlarını değiştirmek Windows Communication Foundation (WCF) hizmet yapılandırma Düzenleyicisi'ni (SvcConfigEditor.exe) sağlar. Bu araç ile XML yapılandırma dosyaları doğrudan düzenlemek zorunda kalmadan WCF bağlamaları, davranışları, hizmetleri ve tanılama ayarlarını yönetebilirsiniz.  
  
 Hizmet yapılandırma Düzenleyicisi C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin klasöründe bulunabilir.  
  
## <a name="the-wcf-configuration-editor"></a>WCF yapılandırma Düzenleyicisi  
 Hizmet yapılandırma Düzenleyicisi, tüm adımlar bir WCF hizmeti veya istemci yapılandırmada size rehberlik eden bir sihirbaz ile birlikte gelir. Doğrudan Düzenleyici yerine Sihirbazı'nı kullanmayı kesinlikle önerilir.  
  
 Standart System.Configuration şemasıyla uyumlu bazı yapılandırma dosyaları zaten varsa, belirli bağlamaları, davranışı, hizmetleri ve kullanıcı arabirimi ile tanılama ayarlarını yönetebilirsiniz. Hizmet yapılandırma Düzenleyicisi, var olan WCF yapılandırma dosyalarının yanı sıra yürütülebilir dosyaları, COM + Hizmetleri ve Web barındırılan hizmetler için ayarları yönetmenizi sağlar. Bir Web barındırılan hizmet ile hizmet yapılandırma Düzenleyicisi, her iki hizmet kişinin kendi açılırken yapılandırma ve üst düzey düğüm devralınan yapılandırmaları bölümlerini gösterilir.  
  
 WCF yapılandırma ayarları bulunur çünkü `<system.serviceModel>` Düzenleyicisi yapılandırma dosyasının yalnızca bu öğenin içeriğini üzerinde çalışır ve diğer öğeleri aynı dosyada erişmez. Mevcut yapılandırma dosyaları doğrudan bulun veya bir hizmet, sanal dizin veya COM + hizmet içeren bir bütünleştirilmiş kod seçebilirsiniz. Düzenleyici belirli hizmet yapılandırma dosyasını yükler ve iç içe geçmiş var olan öğeleri düzenleyebilir veya yeni öğeler eklemek kullanıcının verir `<system.serviceModel>` yapılandırma dosyasının.  
  
 Düzenleyicisi IntelliSense'i destekler ve şema uyumluluğu zorlar. Sonuçta çıktı yapılandırma dosyası şeması ile uyumlu olmasını ve sözdizimsel olarak doğru veri değerlerini garanti edilir. Ancak, düzenleyici yapılandırma dosyası anlamsal olarak geçerli olduğunu garantilemez. Diğer bir deyişle, düzenleyici yapılandırma dosyası yapılandırır hizmeti ile çalışabilir garantilemez.  
  
> [!CAUTION]
>  Öğe değiştirdikten sonra Düzenleyici bir yapılandırma öğesini yapılandırma dosyasından temizlenemiyor. Örneğin, uç nokta adı için boş olmayan bir dize ayarlamak ve kaydetmek için Düzenleyicisi'ni kullanırsanız, aşağıdaki örnekte gösterildiği gibi yapılandırma dosyasını aşağıdaki içeriğe sahiptir.  
>   
>  `<endpoint binding="basicHttpBinding" name="somename" />`  
>   
>  Ada göre kaldırma girişimi varsa, boş bir dize ve dosyayı, hala yapılandırma dosyası ayarı `name` özniteliği aşağıdaki örnekte gösterildiği gibi.  
>   
>  `<endpoint binding="basicHttpBinding" name="" />`  
>   
>  Öznitelik temizlemek için başka bir metin düzenleyicisi kullanarak öğesini elle düzenlemeniz gerekir.  
>   
>  Kullandığınızda, bu sorunla özellikle dikkat etmelisiniz `issueToken` öğesinin `clientCredential` uç nokta davranışı. Özellikle, `address` özniteliği kendi `localIssuer` alt öğe boş bir dize olmalıdır. Değiştirdiyseniz, `address` yapılandırma Düzenleyicisi'ni kullanarak öznitelik ve tamamen kaldırmak istiyorsanız, Düzenleyicisi dışında bir aracı kullanarak yapmalısınız. Aksi takdirde boş bir dize özniteliği içeren ve uygulamanızı bir özel durum oluşturur.  
  
## <a name="using-the-configuration-editor"></a>Yapılandırma Düzenleyicisi'ni kullanarak  
 Hizmet yapılandırma Düzenleyicisi, aşağıdaki Windows SDK'sını yükleme konumda bulunabilir:  
  
 C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe  
  
 Hizmet yapılandırma Düzenleyicisi'ni başlattıktan sonra kullanabileceğiniz **açık dosyaya** hizmet veya yönetmek istediğiniz derleme göz atmak için menü. Yapılandırma dosyaları doğrudan WCF /COM+ hizmetlere gözatmak ve Web barındırılan hizmetler için yapılandırma dosyalarını açın açabilirsiniz.  
  
 Hizmet yapılandırma Düzenleyicisi'nin kullanıcı arabirimi aşağıdaki alana ayrılır:  
  
- Ağaç görünümü yapılandırma öğeleri, soldaki ağaç yapısında görüntüler bölme. Düğümlere sağ tıklayarak ağacında işlemleri gerçekleştirebilir.  
  
- Sol alt üzerinde pencerenin geçerli öğeleri için ortak görevleri görüntüleyen görev bölmesi  
  
- Ayrıntı bölmesinde, sağ taraftaki ağaç görünümünde seçilen yapılandırma düğümünün ayrıntılı ayarlarını görüntüler.  
  
### <a name="opening-a-configuration-file"></a>Bir yapılandırma dosyasını açma  
  
1. Hizmet yapılandırma Düzenleyicisi, WCF yükleme konumuna gidin ve ardından yazın, bir komut penceresi kullanarak Başlat `SvcConfigEditor.exe`.  
  
2. Gelen **dosya** menüsünde **açık** ve yönetmek istediğiniz dosya türüne tıklayın.  
  
3. İçinde **açık** iletişim kutusunda, istediğiniz çift tıklayın ve yönetmek için belirli dosyasına gidin.  
  
 Görüntüleyici otomatik olarak yapılandırma birleştirme yolu izler ve yapılandırmanın birleştirilmiş bir görünümünü oluşturur. Örneğin, barındırılan hizmet gerçek yapılandırmasını Machine.config ve App.config oluşur. Herhangi bir değişiklik SvcConfigEditor etkin dosyasında uygulanır. Yapılandırma birleştirme yolu belirli bir dosyayı düzenlemek istiyorsanız, doğrudan açılmalıdır.  
  
> [!NOTE]
>  Yapılandırma Düzenleyicisi ikinci Düzenleyici dışında değiştirilmiş, açık durumdaki yapılandırma dosyasını yeniden yükler. Bu durumda, düzenleyicinin içinde depolanmasına kaydedilmemiş tüm değişiklikler kaybolur. Yeniden tutarlı bir durumda, en olası nedeni yapılandırma dosyası, örneğin, arka planda çalışan bir virüsten koruma yazılımı erişen sürekli bir hizmettir. Bu sorunu çözmek için yapılandırma Düzenleyicisi açıldığında, dosyanın erişebildiği tek bir işlem olduğunu emin olun.  
  
### <a name="services"></a>Hizmetler  
 **Hizmetleri** düğüm yapılandırma dosyasında şu anda atanmış olan tüm hizmetleri görüntüler. Her alt düğümü ağacında bir alt öğeye karşılık gelen <`services`> yapılandırma dosyası öğesi.  
  
 Tıkladığınızda **Hizmetleri** düğümünü görüntülemek veya gerçekleştirmek hizmet görevlerde Özet sayfasında **ayrıntı** bölmesi.  
  
#### <a name="creating-a-new-service-configuration"></a>Yeni bir hizmet yapılandırması oluşturma  
 Yeni bir hizmet yapılandırması aşağıdaki yollarla oluşturabilirsiniz:  
  
- Sihirbaz kullanarak: Bağlantıya tıklayın **yeni bir hizmet oluşturun...** Görev bölmesi veya Özet sayfasında sihirbazını başlatmak için. Ayrıca, bu nedenle yapabilirsiniz **dosya** menü -> **Yeni Öğe Ekle**.  
  
- El ile oluşturun: Sağ tıklayabilirsiniz **Hizmetleri** düğümünü seçip **yeni hizmet**.  
  
#### <a name="creating-a-new-service-endpoint-configuration"></a>Yeni bir hizmet uç noktası yapılandırması oluşturma  
 Yeni bir hizmet uç noktası yapılandırması aşağıdaki yollarla oluşturabilirsiniz:  
  
- Sihirbaz kullanarak oluşturduğunuz: bağlantıya tıklayın **yeni bir hizmet uç noktası oluşturma...** Görev bölmesi veya Özet sayfasında sihirbazını başlatmak için. Ayrıca, bu nedenle yapabilirsiniz **dosya** menü -> **Yeni Öğe Ekle**.  
  
- El ile oluşturun: Hizmet oluşturulduktan sonra sağ tıklayabilirsiniz **uç noktaları** düğümü seçin "**yeni hizmet uç noktası**".  
  
#### <a name="editing-a-service-configuration"></a>Hizmet yapılandırmasını düzenleme  
  
1. ' A tıklayın bir **hizmet** düğümü.  
  
2. Özellik kılavuzları ayarlarını düzenleyin.  
  
#### <a name="editing-a-service-endpoint-configuration"></a>Bir hizmet uç noktası yapılandırmasını düzenleme  
  
1. ' A tıklayın bir **hizmet uç noktası** düğümü.  
  
2. Özellik kılavuzları ayarlarını düzenleyin.  
  
#### <a name="adding-a-base-address"></a>Temel adres ekleme  
  
1. Tıklayın **konak** düğümü.  
  
2. Tıklayın **yeni...** düğmesini **temel adresler** bölümü.  
  
3. İletişim kutusunda URI temel adresini yazın.  
  
4. **Tamam**'ı tıklatın.  
  
> [!NOTE]
>  Değerini düzenleyemezsiniz [ \<baseAddressPrefixFilters >](../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) bu araç içinde. Ekleme veya bu öğeyi değiştirmek için bir metin düzenleyicisi veya Visual Studio kullanmanız gerekir.  
  
### <a name="client"></a>İstemci  
 **İstemci** düğüm tüm istemci uç noktalarını yapılandırma dosyasında görüntüler. Her alt düğümü ağacında bir alt öğeye karşılık gelen <`client`> yapılandırma dosyası öğesi.  
  
 Tıkladığınızda **istemci** düğümünü görüntülemek veya görevleri bir istemcide **özeti sayfasında** içinde **ayrıntı bölmesi**.  
  
#### <a name="creating-a-new-client-endpoint-configuration"></a>Yeni bir istemci uç nokta yapılandırması oluşturma  
 Yeni bir istemci uç nokta yapılandırması aşağıdaki yollarla oluşturabilirsiniz:  
  
- Sihirbaz tarafından oluşturun: Bağlantıya tıklayın **yeni bir istemci oluştur...** üzerinde **görev bölmesi** penceresinin alt sol taraftaki veya **özeti sayfasında** sihirbazını başlatmak için. Ayrıca, bu nedenle yapabilirsiniz **dosya** menü -> **Yeni Öğe Ekle**. Sihirbaz, hizmeti yapılandırmasının istemci yapılandırmasını oluşturulduğu konumunu gösterecek şekilde ister. Daha sonra bağlanmak için hizmet uç noktası seçebilirsiniz.  
  
- El ile oluşturun: Sağ **uç noktaları** düğümünde **istemci**ve **yeni istemci uç noktası**.  
  
#### <a name="editing-a-client-endpoint-configuration"></a>İstemci uç noktası yapılandırmasını düzenleme  
  
1. ' A tıklayın bir **istemci uç noktası** düğümü.  
  
2. Özellik kılavuzları ayarlarını düzenleyin.  
  
### <a name="standard-endpoint"></a>Standart uç noktası  
 Standart uç noktaları varsa özel uç noktaları ya da daha fazla yönlerini, sözleşme bağlamasını ve adresini varsayılan değerlere ayarlayın.  
  
 Bu yapılandırma ayarlarını depolanır **standart uç nokta** düğümü. **Standart uç nokta** düğüm tüm standart uç noktası ayarları yapılandırma dosyasında görüntüler. Her alt düğümü ağacında bir alt öğesinde karşılık gelen `<standardEndpoints>` yapılandırma dosyasındaki öğesi.  
  
 Tıkladığınızda **standart uç nokta** düğümünü görüntüleyebilir veya standart uç noktada görevleri **özeti sayfasında** içinde **ayrıntı bölmesi**.  
  
#### <a name="creating-a-new-standard-endpoint-configuration"></a>Yeni bir standart uç nokta yapılandırması oluşturma  
 Yeni bir standart uç nokta yapılandırması aşağıdaki yollarla oluşturabilirsiniz:  
  
- Sağ **standart uç nokta** düğümünü seçip alt **yeni standart uç nokta yapılandırması...** İletişim kutusundaki bağlama türü seçin ve tıklayın **Tamam**.  
  
- Seçin **standart uç nokta** düğüm ve tıklatın **yeni standart uç nokta yapılandırması...** içinde **görev bölmesi** penceresinin alt sol taraftaki.  
  
 **Yeni standart uç nokta oluşturma** iletişim kutusu görüntüler ve tüm kayıtlı standart uç nokta türleri listeler.  
  
#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a>Görüntüleme ve düzenleme bir standart uç nokta yapılandırması  
 Bir standart uç nokta yapılandırması, görüntüleme ve aşağıdaki yollarla düzenleme için açabilirsiniz:  
  
- Genişletmek için tıklatın **standart uç nokta** düğüm ve ilgili uç noktası alt düğümünü tıklatın.  
  
- Tıklayın **standart uç nokta** düğüm ve ayrıntı bölmesi üzerinde ilgili uç noktaya tıklayın.  
  
 Uç nokta için öznitelikleri düzenlemek için sağ bölmede gösterilir.  
  
#### <a name="deleting-a-standard-endpoint-configuration"></a>Bir standart uç nokta yapılandırması siliniyor  
 Bir standart uç nokta yapılandırması aşağıdaki yollarla silebilirsiniz:  
  
- Genişletmek için tıklatın **standart uç nokta** düğüm ve ilgili uç noktası alt düğümü sağ tıklatın. Bağlam komutunu **standart uç nokta yapılandırması silme** uç nokta silinemedi.  
  
- Tıklayın **standart uç nokta** düğümü. İçinde **görev** bölmesinde tıklayın **standart uç nokta yapılandırması silme**.  
  
 Standart uç noktası kullanılırsa, silmeye çalıştığınızda bir uyarı iletisi görüntülenir: **Standart uç noktası kullanılır. Lütfen şimdi silerseniz, tüm başvuruları yapılandırmada (örneğin, hizmet uç noktası veya istemci uç noktası) diğer bölümlerinde sildiğinizden emin olun. Aksi takdirde, yapılandırma geçersiz olur ve sonraki açılamaz. Standart uç noktayı silmek istediğinizden emin misiniz?"**  
  
### <a name="binding"></a>Bağlama  
 Bağlama yapılandırmaları, uç noktalara bağlamaları yapılandırmak için kullanılır. Bu yapılandırma ayarlarını depolanır **bağlama** düğümü. Uç noktaları bağlama yapılandırmaları ada göre başvuru ve birden fazla uç nokta tek bağlama yapılandırması başvurabilirsiniz.  
  
 **Bağlamaları** düğüm tüm bağlama ayarları yapılandırma dosyasında görüntüler. Her alt düğümü ağacında bir alt öğesinde karşılık gelen <`bindings`> yapılandırma dosyası öğesi.  
  
 Tıkladığınızda **bağlamaları** düğümünü görüntülemek ya da binding üstündeki görevleri **özeti sayfasında** içinde **ayrıntı bölmesi**.  
  
#### <a name="creating-a-new-binding-configuration"></a>Yeni bir bağlama yapılandırmasını oluşturma  
 Yeni bir bağlama yapılandırması aşağıdaki yollarla oluşturabilirsiniz.  
  
- Sağ **bağlamaları** düğümünü seçip alt **yeni bağlama yapılandırma**... İletişim kutusundaki bağlama türü seçin ve tıklayın **Tamam**.  
  
- Seçin **bağlamaları** düğüm ve tıklatın **yeni bağlama yapılandırma**... içinde **görev bölmesi** penceresinin alt sol taraftaki.  
  
- Hizmet veya istemcinin Özet sayfasında tıklatın **için Oluştur'u tıklatın** içinde **bağlama Yapılandırması** karşılık gelen uç noktası için bir bağlama yapılandırmasını oluşturmak için alan.  
  
#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a>Özel bir bağlama öğesi uzantıları bağlaması ekleme  
  
1. Bağlama için bir uzantı öğesi eklemek istediğiniz seçin.  
  
2. **Ekle**'yi tıklatın.  
  
3. Kullanılabilir uzantılar listesinden eklemek istediğiniz bağlama öğesi uzantısı seçin. Birden fazla öğeyi seçmek için CTRL tuşuna aynı anda basın.  
  
4. **Ekle**'yi tıklatın.  
  
#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a>Özel bağlama uzantısı konumu ayarlama  
 Özel bağlama bağlama bir yığını form öğelerinin bir koleksiyondur. Yığındaki her bir bağlama öğesi, kendi yapılandırma ayarları vardır. Özel bağlama bağlama öğesi uzantılarında sırasını yığınında konumlarını gösterir. Yığının en üst öğeler önce uygulanır. Sıralamasını değiştirmek için:  
  
1. Özel bağlama düğümünü seçin.  
  
2. Bir bağlama uzantı öğesi seçin **bağlama öğesi uzantısı konumu** bölümü.  
  
3. Kullanım **yukarı** veya **aşağı** seçili öğenin konumunu değiştirmek için listede sol tarafındaki düğmesi.  
  
#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a>Özel bir bağlama öğesi uzantıları bağlama yapılandırmasını düzenleme  
  
1. Bağlama düğümü ağacında seçin.  
  
2. Düzenlemek istediğiniz öğeyi içeren özel bir bağlama'ı seçin.  
  
3. Düzenlemek istediğiniz bağlama öğesi uzantısı'nı seçin. Öğe ayarlarını nerede düzenlenmeden sağ bölmede görünür.  
  
### <a name="diagnostics"></a>Tanılamalar  
 **Tanılama** düğüm tüm tanılama ayarları yapılandırma dosyasında görüntüler. Performans sayaçları Aç veya Kapat, etkinleştirme veya Windows Yönetim Araçları (WMI) devre dışı bırakmak, WCF izleme yapılandırma ve WCF ileti günlüğe kaydetmeyi yapılandırma olanak tanır. Ayarlarında **tanılama** düğüm karşılık gelir <`system.diagnostics`> bölümünde ve `<diagnostics>` konusundaki `<system.serviceModel>` yapılandırma dosyası.  
  
 Tıkladığınızda **tanılama** düğümünü görüntülemek veya görevleri tanılamayı **özeti sayfasında** içinde **ayrıntı bölmesi**.  
  
#### <a name="configuring-performance-counters-and-wmi"></a>Performans sayaçları ve WMI yapılandırma  
  
1. Tıklayın **tanılama** düğümü.  
  
2. Tıklayın **geçiş performans sayaçları**. Performans sayacı üç durumu vardır: (Varsayılan), kapalı ServiceOnly ve tüm. Bağlantı tıklatıldığında üç bu durumlar arasında ayar yapar.  
  
#### <a name="configuring-wmi-provider"></a>WMI sağlayıcısı yapılandırma  
  
1. Tıklayın **tanılama** düğümü.  
  
2. WMI Sağlayıcısı'nı etkinleştirmek için tıklayın **etkinleştirme WMI sağlayıcısı** bağlantı.  
  
#### <a name="enabling-wcf-tracing"></a>WCF izlemeyi etkinleştirme  
 Özel izleme dosyasını oluştururken ya da standart özelliklere sahip bir WCF izleme dosyası oluşturun.  
  
1. Tıklayın **tanılama** düğümü.  
  
2. Tıklayın **izlemeyi etkinleştirme**.  
  
3. Tıklayın **izleme düzeyini** izleme düzeyini ayarlamak için bağlantı. Altı izleme düzeyi vardır: Kapalı, kritik hata, uyarı, bilgi ve ayrıntılı. **Etkinlik izleme** ve **yaymak etkinlik** seçeneği WCF Etkinlik izleme özelliğini kullanmak etkinleştirin.  
  
4. İzleme dosyası ve seçeneklerini belirlemek için İzleme dinleyicisi adına tıklayın.  
  
#### <a name="enabling-wcf-logging"></a>WCF günlüğünü etkinleştirme  
 Özel izleme dosyasını oluştururken ya da standart özelliklere sahip bir WCF izleme dosyası oluşturun.  
  
1. Tıklayın **tanılama** düğümü.  
  
2. Tıklayın **ileti günlüğe kaydetmeyi etkinleştirme**.  
  
3. Tıklayın **günlük düzeyi** günlük düzeyini ayarlamak için bağlantı. Üç günlük düzeyi vardır: Hatalı biçimlendirilmiş, hizmet ve taşıma.  
  
4. Günlük dosyası ve seçeneklerini belirtmek için dinleyici adına tıklayın.  
  
> [!NOTE]
>  Uygulamanızı kapalı olduğunda otomatik olarak kopyalanması, etkinleştirme izleme ve ileti günlüklerini istiyorsanız **otomatik temizleme** seçeneği.  
  
 **Tanılama** **özeti sayfasında** , tanılama yapılandırmada en yaygın görevleri gerçekleştirmenize olanak sağlar. Ancak, dinleyici ve kaynakları ayarlarını el ile düzenlemek istiyorsanız, genişletmeniz gerekir **tanılama** düğüm ve düzenleme ayarlarında **ileti günlüğe kaydetme**, **dinleyicileri** ve **Kaynakları** düğümü.  
  
#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a>WCF özel izlemeyi etkinleştirme ya da ileti günlüğe kaydetme  
  
1. Tıklayın **tanılama** düğümünü genişletin.  
  
2. Sağ **dinleyicileri** düğümünü seçip alt **yeni dinleyici**.  
  
3. İzleme dosyası adı türü **InitData** alan. Tıklayabilirsiniz "..." bir yolu için Gözat düğmesine.  
  
4. Tıklayarak **TypeName** "..." bir çizgi görüntüler düğmesi. Açmak için bu düğmeye tıklayın **İzleme dinleyicisi türünü tarayıcı**, hangi zaten yüklü olan önceden yapılandırılmış izleme dinleyicilerine bulmak için kullanabilirsiniz.  
  
5. Not **kaynak** bölümü. Tıklayın **Ekle** bir açılır menü ile bir iletişim kutusunu açmak için bu bölümde, kullanılabilir izleme kaynakları listelenir. Bir izleme kaynağı seçin ve tıklayın **Tamam**.  
  
6. İleti günlüğe kaydetme ayarlarını düzenlemek için tıklayın **ileti günlüğe kaydetme** düğümü. Özellik kılavuzunda ayarları düzenleyebilirsiniz.  
  
### <a name="advanced"></a>Gelişmiş  
  
#### <a name="behaviors"></a>Davranışlar  
 **Davranışları** düğümü şu anda yapılandırma dosyasında tanımlanan davranışları gösterir.  
  
 Davranış yapılandırmaları, uç noktaları ve hizmetler davranışlarını yapılandırmak için kullanılır. Bu yapılandırma ayarlarını depolanır **Gelişmiş** düğümünde **hizmet davranışları** ve **uç nokta davranışları**. Hizmet davranışları Hizmetleri tarafından kullanılan; ancak uç noktaları tarafından uç nokta davranışları.  
  
 Davranışları olan uzantı öğelerinin bir koleksiyonunu bir yığın için. Yığının en üst öğe, ilk olarak uygulanır. Her uzantı öğesi kendi yapılandırma olabilir.  
  
##### <a name="creating-a-new-behavior-configuration"></a>Yeni bir davranış yapılandırmasını oluşturma  
 Yeni bir davranış yapılandırma iki şekilde oluşturabilirsiniz.  
  
- Davranış düğümlerinden sağ tıklayıp "**yeni davranış yapılandırması...**  
  
- Davranış düğümlerden birini seçin ve tıklayın **yeni davranış yapılandırmasını**... içinde **görev bölmesi** penceresinin alt sol taraftaki.  
  
##### <a name="adding-behavior-element-extensions-to-a-behavior"></a>Davranış öğesi uzantıları için bir davranış ekleme  
  
1. Davranış düğümlerden birini seçin.  
  
2. Düzenlemek istediğiniz davranışı seçin.  
  
3. **Ekle**'yi tıklatın.  
  
4. Kullanılabilir uzantılar listesinden eklemek istediğiniz davranışı öğesi uzantıyı seçin.  
  
5. **Ekle**'yi tıklatın.  
  
##### <a name="adjusting-the-extension-position-in-a-behavior"></a>Bir davranış uzantısı konumu ayarlama  
 Davranışlar bir yığını form öğelerinin koleksiyonlarıdır. Yığındaki her bir öğe kendi yapılandırmasına sahip. Bir davranış davranış öğesi uzantıları sırasını yığınında konumlarını gösterir. Yığının en üst öğeler önce uygulanır. Sıralamasını değiştirmek için:  
  
1. Davranış düğümlerden birini seçin.  
  
2. Düzenlemek istediğiniz davranışı seçin.  
  
3. Bir davranış uzantısı öğesinde seçin **davranış öğesi uzantısı konumu** bölümü.  
  
4. Kullanım **yukarı** veya **aşağı** seçili öğenin konumunu değiştirmek için listede sol tarafındaki düğmesi.  
  
##### <a name="editing-the-configuration-of-behavior-element-extensions"></a>Davranış öğesi uzantıları yapılandırmasını düzenleme  
  
1. Davranış düğümlerinden ağacında'ı seçin.  
  
2. Düzenlemek istediğiniz öğeyi içeren davranışı seçin.  
  
3. Düzenlemek istediğiniz davranışı öğesi uzantısı'nı seçin. Öğe ayrıntılarını burada düzenlenmeden sağ bölmede görünür.  
  
#### <a name="protocolmapping"></a>protocolMapping  
 Bu bölümde, http, tcp, MSMQ veya protokol adresi şemaları olası bağlamaları arasında tanımlanan eşleme aracılığıyla net.pipe gibi farklı protokoller için bağlama türleri varsayılan ayarlamanıza olanak sağlar. Yeni eşlemeler diğer protokoller için de ekleyebilirsiniz.  
  
#### <a name="extensions"></a>Uzantıları  
 Yeni bağlama uzantıları, bağlama öğesi uzantıları, standart uç nokta uzantıları ve davranış uzantıları, WCF yapılandırma kullanmak için kaydedilebilir. Uzantı adı/türü çiftleridir. Türün uyguladığı uzantı ise adı uzantısının adına sahip yapılandırmada tanımlar. Dört tür uzantılar vardır:  
  
- Bağlama uzantıları tüm bağlama türünü tanımlayın. Örnek: `basicHttpBinding`.  
  
- Bağlama öğesi uzantıları bir bağlama öğesi tanımlar. Örnek: `textMessageEncoding`.  
  
- Standart uç nokta uzantıları tüm standart uç nokta tanımlar. Örnek: `discoveryEndpoint`.  
  
- Davranış öğesi uzantıları bir davranış öğesi tanımlayın. Örnek: `clientVia`.  
  
 Yapılandırmada kayıtlı uzantıları diğer WCF bileşenleri aynı türde gibi kullanılabilir.  
  
##### <a name="adding-a-new-extension"></a>Yeni bir uzantı ekleme  
 Gelişmiş düğümlerin uzantısı düğümlerden birini seçin:  
  
1. **Yeni**'yi tıklatın.  
  
2. Bir ad ve türü girin.  
  
3. **Tamam**'ı tıklatın.  
  
4. Uzantı artık düzenleyicide uygun bir yerde görünür. Örneğin, bir davranış öğesi uzantısı eklerseniz, kullanılabilir uzantıları listesinde görünür.  
  
#### <a name="hosting-environment"></a>Barındırma ortamı  
 Bu bölüm, hizmet barındırma ortamı için örnek oluşturma ayarları tanımlamanıza imkan tanır.  
  
### <a name="creating-a-configuration-file-using-the-wizard"></a>Sihirbazı kullanarak bir yapılandırma dosyası oluşturma  
 Yeni bir yapılandırma dosyası oluşturma yöntemlerinden biri, yeni hizmet öğesi Sihirbazı'nı kullanmaktır. Sihirbazı yüklü hizmet türlerini ve diğer öğeleri COM + ve Web barındırılan sanal dizinleri dahil olmak üzere bilgisayarda, WCF ile uyumlu bulur ve bunları yapmak çok daha rahat bir yapılandırma oluşturmak için yükler.  
  
#### <a name="creating-a-configuration-file"></a>Yapılandırma dosyası oluşturma  
  
1. Hizmet yapılandırma Düzenleyicisi, WCF yükleme konumuna gidin ve ardından yazın, bir komut penceresi kullanarak Başlat `SvcConfigEditor.exe`.  
  
2. Gelen **dosya** menüsünde **açık** tıklatıp **yürütülebilir**, **COM + hizmet**, veya **WebHosted hizmet**oluşturmak istediğiniz yapılandırma dosyasının türüne bağlı olarak.  
  
3. İçinde **açık** iletişim kutusunda, bir yapılandırma dosyası oluşturun ve buna çift tıklayarak istediğiniz belirli dosyasına gidin.  
  
4. İçinde **dosya** menüsünde **Yeni Öğe Ekle** tıklatıp **hizmet**. Yeni hizmet öğesi Sihirbazı açılır.  
  
5. Yeni bir hizmet oluşturmak için sihirbazdaki adımları izleyin.  
  
> [!NOTE]
>  NetPeerTcpBinding sihirbaz tarafından oluşturulan yapılandırma dosyası kullanmak istiyorsanız, el ile bağlama yapılandırma öğesi eklemek ve değiştirmek sahip `mode` özniteliği kendi `security` öğesine "None".  
  
## <a name="configuring-com"></a>COM + yapılandırılıyor  
 Hizmet yapılandırma Düzenleyicisi, mevcut bir COM + uygulama için yeni bir yapılandırma dosyası oluşturun veya var olan bir COM + yapılandırmasını düzenlemek sağlar. **COM sözleşme** düğümü yalnızca görünür olduğunda <`comContract`> bölümü yapılandırma dosyasında yok.  
  
### <a name="creating-a-new-com-configuration"></a>Yeni bir COM + Yapılandırması oluşturma  
 Yeni bir COM + Yapılandırması oluşturmadan önce COM + uygulaması'ndaki Bileşen Hizmetleri yüklü ve Genel Derleme Önbelleği'ne (GAC) kayıtlı olduğunu doğrulayın.  
  
1. Seçin **dosya** menü -> **tümleştir** -> **COM + uygulaması.** Bu işlem, geçerli açık dosya kapatır. Geçerli dosyadaki veri kaydedilmemiş bir Kaydet iletişim kutusu görüntülenir. **COM + tümleştirme sihirbazını** sonra başlatılır.  
  
2. İlk sayfa ağaçtan COM + uygulaması'ı seçin. COM + uygulaması ağacında bulamazsanız, Bileşen Hizmetleri yüklenir ve Genel Derleme Önbelleği'ne (GAC) kayıtlı olduğunu doğrulayın.  
  
3. Sonraki sayfada, WCF hizmetleri kullanıma sunmak istediğiniz hangi yöntemleri seçin. Desteklenen tüm yöntemler COM + uygulaması'nda görüntülenir ve varsayılan olarak seçilidir.  
  
4. Bir barındırma yöntemini seçin.  
  
5. Sihirbazda kılavuzları göre diğer ayarları yapılandırın.  
  
6. Hizmet yapılandırma Düzenleyicisi yapılandırma dosyası oluşturmak için arka planda ComSvcConfig.exe kullanır. Bu tamamlandıktan sonra bir özeti görüntülemek ve sihirbazdan çıkın. Böylece doğrudan düzenleyebilirsiniz oluşturulan yapılandırma dosyası açılır.  
  
### <a name="editing-an-existing-com-configuration"></a>Var olan bir COM + yapılandırmasını düzenleme  
  
1. Seçin **dosya** menü -> **açık** -> **COM + hizmet**...  
  
2. COM + listeden düzenlemek istediğiniz hizmeti seçin.  
  
3. Yapılandırma ayarlarını düzenlemek **COM sözleşmeleri** düğümü.  
  
    > [!NOTE]
    >  Ayrıca doğrudan açın ve COM sözleşmeleri içeren bir yapılandırma dosyasını düzenleyin.  
  
## <a name="security"></a>Güvenlik  
 Yapılandırma Düzenleyicisi tarafından oluşturulan hizmet yapılandırma dosyasını güvenli olmasını garanti edilmez. Lütfen [güvenlik](../../../docs/framework/wcf/feature-details/security.md) , WCF hizmetleri güvenli hale getirme konusunda bilgi edinmek için belgeleri.  
  
 Ayrıca, okuma ve yazma geçerli WCF yapılandırma öğeleri için yapılandırma Düzenleyicisi yalnızca kullanılabilir. Aracı şemayla uyumlu, kullanıcı tarafından tanımlanan öğeleri yok sayar. Ayrıca bu yapılandırma öğelerinden dosya ya da bilinen WCF öğelerde etkilerini Kaldır denemez. Bu öğeleri, uygulama veya sistem için bir tehdit teşkil olup olmadığını belirlemek kullanıcının sorumluluğundadır.
