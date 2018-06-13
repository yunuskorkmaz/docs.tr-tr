---
title: Yapılandırma Düzenleme Aracı (SvcConfigEditor.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
ms.openlocfilehash: 75657786135fd13222c6c7edd5acfa122cc72e52
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809881"
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a>Yapılandırma Düzenleme Aracı (SvcConfigEditor.exe)
Yöneticiler ve geliştiriciler oluşturmak ve bir grafik kullanıcı arabirimini kullanarak WCF hizmetleri için yapılandırma ayarlarını değiştirmek Windows Communication Foundation (WCF) hizmetini yapılandırma Düzenleyicisi (SvcConfigEditor.exe) sağlar. Bu aracı kullanarak doğrudan XML yapılandırma dosyalarını düzenlemek zorunda kalmadan WCF bağlamaları, davranışları, hizmetleri ve tanılama ayarlarını yönetebilirsiniz.  
  
 Hizmet yapılandırma Düzenleyicisi C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin klasöründe bulunabilir.  
  
## <a name="the-wcf-configuration-editor"></a>WCF yapılandırma Düzenleyicisi  
 Hizmet yapılandırma Düzenleyicisi bir WCF hizmeti veya istemci yapılandırmada tüm adımlarda size yol gösterir bir sihirbaz ile birlikte gelir. Sihirbazı doğrudan yerine Düzenleyicisi'ni kullanmak için kesinlikle önerilir.  
  
 Standart System.Configuration şemasıyla uyumlu bazı yapılandırma dosyaları zaten varsa, bağlamaları, davranışı, hizmetleri ve kullanıcı arabirimi ile tanılama için belirli ayarları yönetebilirsiniz. Hizmet yapılandırma Düzenleyicisi, var olan WCF yapılandırma dosyalarını yanı sıra yürütülebilir dosyaları, COM + hizmetlerinin ve Web barındırılan hizmetleri ayarlarını yönetmek sağlar. Bir Web barındırılan hizmet ile hizmet yapılandırma Düzenleyicisi, her iki hizmet 's kendi açarken yapılandırması ve üst düzey düğüm devralınan yapılandırmaları bölümlerini gösterilir.  
  
 WCF yapılandırma ayarlarını bulunduğundan `<system.serviceModel>` Düzenleyicisi yapılandırma dosyasının yalnızca bu öğenin içeriğini üzerinde çalışır ve diğer öğeleri aynı dosyada erişmez. Var olan yapılandırma dosyalarını doğrudan gidebilirsiniz veya, bir hizmet, sanal dizin veya COM + hizmet içeren bütünleştirilmiş seçebilirsiniz. Düzenleyici, belirli bir hizmet için yapılandırma dosyasını yükler ve yeni öğeler eklemek veya iç içe geçmiş var olan öğeleri düzenleyebilir olanak tanır. `<system.serviceModel>` yapılandırma dosyasının.  
  
 Düzenleyici, IntelliSense destekler ve şema uyumluluk zorlar. Sonuçta çıktı yapılandırma dosyası şeması ile uyumlu olmasını ve sözdizimsel olarak doğru veri değerleri garanti edilmez. Ancak, Düzenleyicisi yapılandırma dosyası anlamsal olarak geçerli garanti değil. Diğer bir deyişle, düzenleyici yapılandırma dosyası yapılandırır hizmeti ile çalışabilirsiniz garanti etmez.  
  
> [!CAUTION]
>  Öğesi değiştirdikten sonra Düzenleyici bir yapılandırma öğesi yapılandırma dosyasından temizleyemezsiniz. Örneğin, uç nokta adı boş dize olarak ayarlayın ve kaydetmek için Düzenleyicisi'ni kullanırsanız, aşağıdaki örnekte gösterildiği gibi yapılandırma dosyasını aşağıdaki içeriğe sahiptir.  
>   
>  `<endpoint binding="basicHttpBinding" name="somename" />`  
>   
>  Ada göre kaldırma girişimi varsa, boş bir dize için ve hala yapılandırma dosyası dosyayı ayarlama `name` , aşağıdaki örnekte gösterildiği gibi özniteliği.  
>   
>  `<endpoint binding="basicHttpBinding" name="" />`  
>   
>  Öznitelik temizlemek için el ile başka bir metin düzenleyicisi kullanarak öğesi düzenlemeniz gerekir.  
>   
>  Kullandığınızda, bu sorun özellikle dikkatli olmalıdır `issueToken` öğesinin `clientCredential` uç noktası davranışı. Özellikle, `address` özniteliği kendi `localIssuer` alt öğe boş bir dize olmamalıdır. Değiştirdiyseniz `address` yapılandırma Düzenleyicisi'ni kullanarak özniteliği ve tamamen kaldırmak istiyorsanız, Düzenleyicisi dışında bir aracı kullanarak yapmalısınız. Aksi durumda, boş bir dize özniteliği içeren ve uygulamanızı bir özel durum oluşturur.  
  
## <a name="using-the-configuration-editor"></a>Yapılandırma Düzenleyicisi'ni kullanarak  
 Hizmet yapılandırma Düzenleyicisi'ni aşağıdaki Windows SDK yükleme konumda bulunabilir:  
  
 C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe  
  
 Hizmet yapılandırma Düzenleyicisi'ni başlattıktan sonra kullanabileceğiniz **açık dosyaya** hizmeti veya derleme yönetmek istediğiniz göz atmak için menüsü. Dosyaları doğrudan, WCF /COM+ Hizmetleri için göz atın ve Web barındırılan hizmetler için yapılandırma dosyalarını açmak yapılandırma açabilirsiniz.  
  
 Hizmet yapılandırma Düzenleyicisi'nin kullanıcı arabirimi, aşağıdaki alana ayrılır:  
  
-   Ağaç görünümü, soldaki ağaç yapısındaki yapılandırma öğelerini görüntüler bölmesinde. Düğümleri sağ tıklayarak ağacında işlemler gerçekleştirebilirsiniz.  
  
-   Pencerenin alt-sol tarafta geçerli öğeler için ortak görevler görüntüler görev bölmesi  
  
-   Ayrıntı bölmesinde, sağdaki ağaç görünümünde seçilen yapılandırma düğümünün ayrıntılı ayarlarını görüntüler.  
  
### <a name="opening-a-configuration-file"></a>Bir yapılandırma dosyası açma  
  
1.  WCF yükleme konumuna gidin ve ardından türü için bir komut penceresi kullanarak hizmet yapılandırma Düzenleyicisi'ni başlatın `SvcConfigEditor.exe`.  
  
2.  Gelen **dosya** menüsünde, select **açık** ve yönetmek istediğiniz dosya türünü tıklatın.  
  
3.  İçinde **açık** iletişim kutusunda, istediğiniz çift tıklayın ve yönetmek için belirli dosyasına gidin.  
  
 Görüntüleyici otomatik olarak yapılandırma birleştirme yolu izler ve birleştirilmiş yapılandırma bir görünümünü oluşturur. Örneğin, gerçek bir olmayan barındırılan hizmetin Machine.config ve App.config bileşimini yapılandırmadır. Herhangi bir değişiklik SvcConfigEditor etkin dosyasında uygulanır. Yapılandırma birleştirme yolu belirli bir dosyayı düzenlemek istiyorsanız, bunu doğrudan açmanız gerekir.  
  
> [!NOTE]
>  İkinci Düzenleyicisi dışında değiştirildiğinde yapılandırma Düzenleyicisi açılmış yapılandırma dosyasını yeniden yükler. Bu gerçekleştiğinde, işlemi içinde Düzenleyicisi kaydedilmez tüm değişiklikler kaybolur. Yeniden tutarlı bir durumda, en olası nedeni yapılandırma dosyası, örneğin, arka planda çalışan bir virüsten koruma yazılımı erişen sürekli bir hizmettir. Bu sorunu çözmek için yapılandırma Düzenleyicisi açıldığında dosya erişebilmeniz için yalnızca işlem olmasını sağlayın.  
  
### <a name="services"></a>Hizmetler  
 **Hizmetleri** düğümünde tüm yapılandırma dosyasında şu anda atanmış hizmetleri görüntüler. Her alt ağacı düğümünde bir alt öğesine karşılık gelen <`services`> yapılandırma dosyası öğesi.  
  
 Tıkladığınızda **Hizmetleri** düğümünü görüntülemek veya gerçekleştirmek hizmet görevlerde Özet sayfasında **ayrıntı** bölmesi.  
  
#### <a name="creating-a-new-service-configuration"></a>Yeni bir hizmet yapılandırması oluşturma  
 Yeni bir hizmet yapılandırması aşağıdaki yollarla oluşturabilirsiniz:  
  
-   Sihirbaz kullanarak: bağlantıya tıklayın **yeni bir hizmet oluştur...** Görev bölmesi veya Özet sayfasında sihirbazını başlatmak için. Ayrıca, bu nedenle yapabilirsiniz **dosya** menüsünde **Yeni Öğe Ekle**.  
  
-   El ile oluşturun: sağ tıklayarak **Hizmetleri** düğümü seçin **yeni hizmet**.  
  
#### <a name="creating-a-new-service-endpoint-configuration"></a>Yeni bir hizmet uç noktası yapılandırması oluşturma  
 Yeni bir hizmet uç noktası yapılandırması aşağıdaki yollarla oluşturabilirsiniz:  
  
-   Sihirbaz kullanarak oluşturduğunuz: bağlantıya tıklayın **yeni bir hizmet uç noktası oluştur...** Görev bölmesi veya Özet sayfasında sihirbazını başlatmak için. Ayrıca, bu nedenle yapabilirsiniz **dosya** menüsünde **Yeni Öğe Ekle**.  
  
-   El ile oluşturun: bir hizmet oluşturduktan sonra sağ tıklayarak **uç noktaları** düğümü seçin "**yeni hizmet uç noktası**".  
  
#### <a name="editing-a-service-configuration"></a>Bir hizmet yapılandırması düzenleme  
  
1.  Tıklatın bir **hizmet** düğümü.  
  
2.  Özellik kılavuzları ayarları düzenleyin.  
  
#### <a name="editing-a-service-endpoint-configuration"></a>Bir hizmet uç noktası yapılandırması düzenleme  
  
1.  Tıklatın bir **Hizmeti uç noktası** düğümü.  
  
2.  Özellik kılavuzları ayarları düzenleyin.  
  
#### <a name="adding-a-base-address"></a>Temel adres ekleme  
  
1.  Tıklatın **konak** düğümü.  
  
2.  Tıklatın **yeni...** düğmesini **temel adresleri** bölümü.  
  
3.  Temel adres URI iletişim kutusuna yazın.  
  
4.  **Tamam**'ı tıklatın.  
  
> [!NOTE]
>  Değeri düzenleyemezsiniz [ \<baseAddressPrefixFilters >](../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) bu aracı içinde. Eklemek veya bu öğe değiştirmek için bir metin düzenleyicisi veya Visual Studio kullanmanız gerekir.  
  
### <a name="client"></a>İstemci  
 **İstemci** düğüm tüm istemci uç noktalarını yapılandırma dosyasında görüntüler. Her alt ağacı düğümünde bir alt öğesine karşılık gelen <`client`> yapılandırma dosyası öğesi.  
  
 Tıkladığınızda **istemci** düğümü, görüntüleyebilir veya istemcide görevleri **Özet sayfası** içinde **ayrıntı bölmesinde**.  
  
#### <a name="creating-a-new-client-endpoint-configuration"></a>Yeni bir istemci uç nokta yapılandırması oluşturma  
 Yeni bir istemci uç nokta yapılandırması aşağıdaki yollarla oluşturabilirsiniz:  
  
-   Oluştur Sihirbazı tarafından: bağlantıya tıklayın **yeni bir istemci oluştur...** üzerinde **görev bölmesi** penceresinin alt soldaki veya **Özet sayfası** sihirbazını başlatmak için. Ayrıca, bu nedenle yapabilirsiniz **dosya** menüsünde **Yeni Öğe Ekle**. Sihirbaz, istemci yapılandırması oluşturulduğu hizmet yapılandırmasının konumunu gösterecek şekilde ister. Ardından bağlanmak için hizmet uç noktası seçebilirsiniz.  
  
-   El ile oluşturun: sağ **uç noktaları** düğümü altında **istemci**ve seçin **yeni istemci uç noktası**.  
  
#### <a name="editing-a-client-endpoint-configuration"></a>Bir istemci uç nokta yapılandırması düzenleme  
  
1.  Tıklatın bir **istemci uç nokta** düğümü.  
  
2.  Özellik kılavuzları ayarları düzenleyin.  
  
### <a name="standard-endpoint"></a>Standart uç noktası  
 Standart uç noktaları varsa özel uç noktaları ya da daha fazla adres ve sözleşme bağlama yönlerini varsayılan değerlere ayarlayın.  
  
 Gibi yapılandırma ayarlarını depolanmış **standart Endpoint** düğümü. **Standart Endpoint** düğümü tüm standart bitiş noktası ayarlarını yapılandırma dosyasında görüntüler. Her alt düğüm ağacında bir alt öğesi içinde karşılık gelen `<standardEndpoints>` yapılandırma dosyası öğesi.  
  
 Tıkladığınızda **standart Endpoint** düğümü, görüntüleyebilir veya standart noktadaki görevleri **Özet sayfası** içinde **ayrıntı bölmesinde**.  
  
#### <a name="creating-a-new-standard-endpoint-configuration"></a>Yeni bir standart uç nokta yapılandırması oluşturma  
 Yeni bir standart uç nokta yapılandırması aşağıdaki yollarla oluşturabilirsiniz:  
  
-   Sağ **standart Endpoint** düğümü ve select **yeni standart uç nokta yapılandırması...** İletişim kutusunda bağ türünü seçin ve'ı tıklatın **Tamam**.  
  
-   Seçin **standart Endpoint** düğümü ve tıklatın **yeni standart uç nokta yapılandırması...** içinde **görev bölmesi** penceresinin alt soldaki.  
  
 **Yeni bir standart uç noktası oluşturma** iletişim kutusu görüntüler ve tüm kayıtlı standart uç nokta türleri listelenmektedir.  
  
#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a>Görüntüleme ve standart uç nokta yapılandırması düzenleme  
 Bir standart uç nokta yapılandırması görüntüleme ve aşağıdaki yollarla düzenleme için açabilirsiniz:  
  
-   Genişletmek için tıklatın **standart Endpoint** düğümü ve ilgili uç nokta alt düğümü tıklatın.  
  
-   Tıklatın **standart Endpoint** düğümü ve ayrıntı bölmesinde ilgili uç noktasına tıklayın.  
  
 Uç noktası için öznitelikleri düzenlemek için sağ bölmede gösterilir.  
  
#### <a name="deleting-a-standard-endpoint-configuration"></a>Standart uç nokta yapılandırması siliniyor  
 Standart uç nokta yapılandırması aşağıdaki yollarla silebilirsiniz:  
  
-   Genişletmek için tıklatın **standart Endpoint** düğümü ve ilgili uç nokta alt düğümünü sağ tıklatın. Bağlam komutunu **silmek standart uç nokta Yapılandırması** uç noktasını silmek için.  
  
-   Tıklatın **standart Endpoint** düğümü. İçinde **görev** bölmesinde tıklatın **silmek standart uç nokta Yapılandırması**.  
  
 Standart uç noktası kullanılıyorsa, silmeye çalıştığınızda bir uyarı iletisi görüntülenir: **standart uç noktası kullanılıyor. Lütfen şimdi silerseniz, tüm diğer bölümlerinde yapılandırmada (örneğin, hizmet uç noktası veya istemci uç noktası) da başvurularından biri sildiğinizden emin olun. Aksi takdirde, yapılandırma geçersiz hale gelir ve sonraki açılamıyor. Standart uç noktasını silmek istediğinizden emin misiniz?"**  
  
### <a name="binding"></a>Bağlama  
 Bağlama yapılandırmaları uç noktalarda bağlamalar yapılandırmak için kullanılır. Gibi yapılandırma ayarlarını depolanmış **bağlama** düğümü. Uç noktaları bağlama yapılandırmalarını adına göre başvuru ve birden çok uç nokta tek bağlama yapılandırması başvuruda bulunabilir.  
  
 **Bağlamaları** düğümü tüm bağlama ayarlarını yapılandırma dosyasında görüntüler. Her alt düğüm ağacında bir alt öğesi içinde karşılık gelen <`bindings`> yapılandırma dosyası öğesi.  
  
 Tıkladığınızda **bağlamaları** düğümü görüntülemek veya görevleri bağlamada **Özet sayfası** içinde **ayrıntı bölmesinde**.  
  
#### <a name="creating-a-new-binding-configuration"></a>Yeni bir bağlama yapılandırması oluşturma  
 Yeni bir bağlama yapılandırması aşağıdaki yollarla oluşturabilirsiniz.  
  
-   Sağ **bağlamaları** düğümü ve select **yeni bağlama yapılandırma**... İletişim kutusunda bağ türünü seçin ve'ı tıklatın **Tamam**.  
  
-   Seçin **bağlamaları** düğümü ve tıklatın **yeni bağlama yapılandırma**... içinde **görev bölmesi** penceresinin alt soldaki.  
  
-   Hizmet veya istemci Özet sayfasında, tıklatın **için Oluştur'u tıklatın** içinde **bağlama Yapılandırması** karşılık gelen uç noktası için bir bağlama yapılandırması oluşturmak için alan.  
  
#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a>Öğe uzantısı için özel bağlama bağlama ekleme  
  
1.  Bir uzantı öğesi eklemek istediğiniz bağlama seçin.  
  
2.  **Ekle**'yi tıklatın.  
  
3.  Kullanılabilir uzantılar listesinden eklemek istediğiniz bağlama öğesi uzantısı seçin. Birden çok öğe seçmek için CTRL tuşuna aynı anda basın.  
  
4.  **Ekle**'yi tıklatın.  
  
#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a>Özel bağlama uzantısı konumu ayarlama  
 Özel bağlama bağlama yığın form öğelerinin bir koleksiyondur. Her bağlama öğesi yığında kendi yapılandırma ayarları vardır. Özel bağlama bağlama öğesi uzantılarında sırasını konumlarına yığınında gösterir. Yığının en üst öğeler önce uygulanır. Sıralamasını değiştirmek için:  
  
1.  Özel bağlama düğümünü seçin.  
  
2.  Bir bağlama uzantısı öğesinde seçin **bağlama öğesi uzantısı konumu** bölümü.  
  
3.  Kullanım **yukarı** veya **aşağı** seçili öğenin konumunu değiştirmek için listedeki sol tarafında düğme.  
  
#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a>İçinde özel bağlama öğesi uzantısı bağlama yapılandırmasını düzenleme  
  
1.  Bağlama düğüm ağaçta seçin.  
  
2.  Düzenlemek istediğiniz öğeyi içeren özel bağlama seçin.  
  
3.  Düzenlemek istediğiniz bağlama öğesi uzantısı seçin. Öğenin ayarları, bunlar burada düzenlenebilir sağ bölmede görüntülenir.  
  
### <a name="diagnostics"></a>Tanılamalar  
 **Tanılama** düğümü tüm tanılama ayarlarını yapılandırma dosyasında görüntüler. Performans sayaçları Aç veya Kapat, etkinleştirme veya Windows Yönetim Araçları (WMI) devre dışı bırakmak, WCF izlemeyi yapılandırmak ve WCF ileti günlüğe kaydetme yapılandırma sağlar. Ayarlarında **tanılama** düğümü karşılık <`system.diagnostics`> bölümünde ve `<diagnostics>` bölümüne `<system.serviceModel>` yapılandırma dosyası.  
  
 Tıkladığınızda **tanılama** düğümü görüntülemek veya üzerinde tanılama görevleri **Özet sayfası** içinde **ayrıntı bölmesinde**.  
  
#### <a name="configuring-performance-counters-and-wmi"></a>Performans sayaçları ve WMI yapılandırma  
  
1.  Tıklatın **tanılama** düğümü.  
  
2.  Tıklatın **geçiş performans sayaçları**. Üç durumlu performans sayacı vardır: (varsayılan), devre dışı ServiceOnly ve tüm. Bağlantı tıklatıldığında ayarı bu üç durumları arasında geçiş yapar.  
  
#### <a name="configuring-wmi-provider"></a>WMI sağlayıcısı yapılandırma  
  
1.  Tıklatın **tanılama** düğümü.  
  
2.  WMI sağlayıcısı etkinleştirmek için **etkinleştirme WMI sağlayıcısı** bağlantı.  
  
#### <a name="enabling-wcf-tracing"></a>WCF izlemeyi etkinleştirme  
 Özel izleme dosyasını oluştururken ya da standart özelliklere sahip bir WCF izleme dosyası oluşturun.  
  
1.  Tıklatın **tanılama** düğümü.  
  
2.  Tıklatın **izlemeyi etkinleştirmek**.  
  
3.  Tıklatın **izleme düzeyi** bağlantı için izleme düzeyini ayarlayın. Altı izleme düzeyi vardır: kapalı, kritik, hata, uyarı, bilgi ve ayrıntılı. **Etkinlik izleme** ve **yayılması etkinlik** seçeneği WCF Etkinlik izleme özelliğini kullanmak etkinleştirin.  
  
4.  İzleme dosyası ve seçeneklerini belirtmek için İzleme dinleyicisi adını tıklatın.  
  
#### <a name="enabling-wcf-logging"></a>WCF günlüğünü etkinleştirme  
 Özel izleme dosyasını oluştururken ya da standart özelliklere sahip bir WCF izleme dosyası oluşturun.  
  
1.  Tıklatın **tanılama** düğümü.  
  
2.  Tıklatın **ileti günlüğe kaydetmeyi etkinleştirmek**.  
  
3.  Tıklatın **günlük düzeyi** günlük düzeyini ayarlamak için bağlantı. Üç günlük düzeyleri vardır: hatalı biçimlendirilmiş, hizmet ve taşıma.  
  
4.  Günlük dosyası ve seçeneklerini belirtmek için dinleyici adına tıklayın.  
  
> [!NOTE]
>  Uygulamanızı kapalı olduğunda otomatik olarak kopyalanması, etkinleştirmek için izleme ve ileti günlüklerini istiyorsanız **otomatik temizleme** seçeneği.  
  
 **Tanılama** **Özet sayfası** tanılama yapılandırmada en yaygın görevleri gerçekleştirmenize olanak sağlar. Ancak, el ile dinleyicileri ve kaynakları ayarlarını düzenlemek istiyorsanız, genişletmeniz gerekir **tanılama** düğümü ve düzenleme ayarlarında **ileti günlüğe kaydetme**, **dinleyicileri** ve **Kaynakları** düğümü.  
  
#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a>WCF özel izlemeyi etkinleştirme ya da ileti günlüğe kaydetme  
  
1.  Tıklatın **tanılama** düğümünü genişletin.  
  
2.  Sağ **dinleyicileri** düğümü ve select **yeni dinleyici**.  
  
3.  İzleme dosya adı yazın **InitData** alan. Bir yoluna göz atmak için "..." düğmesini tıklatabilirsiniz.  
  
4.  Tıklatarak **TypeName** satırı bir "..." düğmesi görüntüler. Açmak için bu düğmeye tıklayın **İzleme dinleyicisi türü tarayıcı**, hangi yüklü olan önceden yapılandırılmış izleme dinleyicileri bulmak için kullanabilirsiniz.  
  
5.  Not **kaynak** bölümü. Tıklatın **Ekle** açılır menü ile iletişim kutusunu açmak için bu bölümde, kullanılabilir izleme kaynaklarını listelerinin. İzleme kaynağını seçin ve tıklatın **Tamam**.  
  
6.  İleti günlüğe kaydetme ayarlarını düzenlemek için tıklatın **ileti günlüğe kaydetme** düğümü. Özellik kılavuzunda ayarları düzenleyebilirsiniz.  
  
### <a name="advanced"></a>Gelişmiş  
  
#### <a name="behaviors"></a>Davranışlar  
 **Davranışları** düğümü yapılandırma dosyasında şu anda tanımlı davranışları görüntüler.  
  
 Davranış yapılandırmaları uç noktaları ve hizmetler davranışlarını yapılandırmak için kullanılır. Gibi yapılandırma ayarlarını depolanmış **Gelişmiş** düğümü altında **hizmet davranışları** ve **Endpoint davranışları**. Hizmet davranışları hizmetler tarafından kullanılan; ancak uç noktaları tarafından endpoint davranışları.  
  
 Davranışları genişletme öğeleri koleksiyonu olan bir yığın için. Yığının en üst öğede önce uygulanır. Her uzantı öğesi kendi yapılandırma olabilir.  
  
##### <a name="creating-a-new-behavior-configuration"></a>Yeni bir davranış yapılandırması oluşturma  
 Yeni bir davranış yapılandırması iki yolla oluşturabilirsiniz.  
  
-   Davranış düğümlerinden biri sağ tıklayın ve "**yeni davranış yapılandırması...**  
  
-   Davranış düğümlerden birini seçin ve'ı tıklatın **yeni davranış yapılandırma**... içinde **görev bölmesi** penceresinin alt soldaki.  
  
##### <a name="adding-behavior-element-extensions-to-a-behavior"></a>Bir davranış davranışı öğesi uzantılar ekleme  
  
1.  Davranış düğümlerden birini seçin.  
  
2.  Düzenlemek istediğiniz davranışı seçin.  
  
3.  **Ekle**'yi tıklatın.  
  
4.  Kullanılabilir uzantılar listesinden eklemek istediğiniz davranış öğesi uzantısı seçin.  
  
5.  **Ekle**'yi tıklatın.  
  
##### <a name="adjusting-the-extension-position-in-a-behavior"></a>Bir davranış uzantısı konumu ayarlama  
 Davranışları bir yığın form öğelerinin koleksiyonlarıdır. Her öğe yığında kendi yapılandırmasına sahip. Bir davranış davranışı öğesi uzantılarının sırasını konumlarına yığınında gösterir. Yığının en üst öğeler önce uygulanır. Sıralamasını değiştirmek için:  
  
1.  Davranış düğümlerden birini seçin.  
  
2.  Düzenlemek istediğiniz davranışı seçin.  
  
3.  Bir davranış uzantısı öğesinde seçin **davranışı öğe uzantısı konumunu** bölümü.  
  
4.  Kullanım **yukarı** veya **aşağı** seçili öğenin konumunu değiştirmek için listedeki sol tarafında düğme.  
  
##### <a name="editing-the-configuration-of-behavior-element-extensions"></a>Davranış öğesi uzantıları yapılandırmasını düzenleme  
  
1.  Davranış düğümlerinden biri ağacında seçin.  
  
2.  Düzenlemek istediğiniz öğeyi içeren davranışı seçin.  
  
3.  Düzenlemek istediğiniz davranışı öğesi uzantısı seçin. Öğenin ayarları, bunlar burada düzenlenebilir sağ bölmede görüntülenir.  
  
#### <a name="protocolmapping"></a>ProtocolMapping  
 Bu bölümde, bağlama türü http, tcp, MSMQ veya protokolü adres düzenleri ve olası bağlamaları arasında tanımlanan eşleme aracılığıyla net.pipe gibi farklı protokoller için varsayılan ayarlamanızı sağlar. Yeni eşlemeler diğer protokoller için de ekleyebilirsiniz.  
  
#### <a name="extensions"></a>Uzantıları  
 Yeni bağlama uzantıları, bağlama öğesi uzantıları, standart endpoint uzantıları ve davranış uzantıları WCF yapılandırmasında kullanılması için kaydedilebilir. Ad/tür çiftleri uzantılarıdır. Uzantı türü uygulayan ancak adı yapılandırmada uzantısının adını tanımlar. Dört tür uzantılar şunlardır:  
  
-   Bağlama uzantıları tüm bağlama türünü tanımlayın. Örnek: `basicHttpBinding`.  
  
-   Bağlama öğesi uzantıları öğenin bağlaması tanımlayın. Örnek: `textMessageEncoding`.  
  
-   Standart uç nokta uzantıları tüm standart son nokta tanımlayın. Örnek: `discoveryEndpoint`.  
  
-   Öğenin bir davranış davranışı öğesi uzantılarını tanımlayın. Örnek: `clientVia`.  
  
 Yapılandırmada kayıtlı uzantıları diğer WCF bileşenleri aynı türde gibi kullanılabilir.  
  
##### <a name="adding-a-new-extension"></a>Yeni bir uzantı ekleme  
 Gelişmiş düğümlerin uzantısı düğümlerden birini seçin:  
  
1.  **Yeni**'yi tıklatın.  
  
2.  Ad ve tür girin.  
  
3.  **Tamam**'ı tıklatın.  
  
4.  Uzantısı uygun yere Düzenleyicisi'nde görüntülenir. Örneğin, bir davranış öğesi uzantısı eklerseniz, kullanılabilir uzantıları listesinde görüntülenir.  
  
#### <a name="hosting-environment"></a>Barındırma ortamı  
 Bu bölümde, barındırma ortamı hizmeti örnek oluşturma ayarlarını tanımlamanızı sağlar.  
  
### <a name="creating-a-configuration-file-using-the-wizard"></a>Sihirbazı'nı kullanarak bir yapılandırma dosyası oluşturma  
 Yeni bir yapılandırma dosyası oluşturmak için bir yolu, yeni hizmet öğesi Sihirbazı'nı kullanmaktır. Sihirbaz yüklü hizmet türlerini ve diğer öğeleri COM + ve Web barındırılan sanal dizinler de dahil olmak üzere bilgisayarda WCF ile uyumlu bulur ve çok daha verimli yapılandırması oluşturma yapmalarına yükler.  
  
#### <a name="creating-a-configuration-file"></a>Bir yapılandırma dosyası oluşturma  
  
1.  WCF yükleme konumuna gidin ve ardından türü için bir komut penceresi kullanarak hizmet yapılandırma Düzenleyicisi'ni başlatın `SvcConfigEditor.exe`.  
  
2.  Gelen **dosya** menüsünde, select **açık** tıklatıp **yürütülebilir**, **COM + hizmet**, veya **WebHosted hizmet**oluşturmak istediğiniz yapılandırma dosyasının türüne bağlı olarak.  
  
3.  İçinde **açık** iletişim kutusunda, istediğiniz bir yapılandırma dosyası oluşturma ve buna çift tıklayarak belirli dosyasına gidin.  
  
4.  İçinde **dosya** menüsündeki **Yeni Öğe Ekle** tıklatıp **hizmet**. Yeni hizmet öğesi Sihirbazı'nı açar.  
  
5.  Yeni bir hizmet oluşturmak için sihirbazdaki adımları izleyin.  
  
> [!NOTE]
>  Sihirbaz tarafından oluşturulan yapılandırma dosyasından NetPeerTcpBinding kullanmak istiyorsanız, el ile bir bağlama yapılandırma öğesi ekleme ve değiştirme sahip `mode` özniteliği kendi `security` öğesi "None".  
  
## <a name="configuring-com"></a>COM + yapılandırılıyor  
 Hizmet yapılandırma Düzenleyicisi, varolan bir COM + uygulaması için yeni bir yapılandırma dosyası oluşturmak veya var olan COM + yapılandırmasını düzenlemek sağlar. **COM sözleşme** düğümü yalnızca görünür zaman <`comContract`> bölümüne yapılandırma dosyasında yok.  
  
### <a name="creating-a-new-com-configuration"></a>Yeni bir COM + Yapılandırması oluşturma  
 Yeni bir COM + Yapılandırması oluşturmadan önce COM + uygulaması'ndaki Bileşen Hizmetleri yüklü ve Genel Derleme Önbelleği'ne (GAC) kayıtlı olduğundan emin olun.  
  
1.  Seçin **dosya** menüsünde **tümleştir** -> **COM + uygulaması.** Bu işlem, geçerli açılan dosyayı kapatır. Geçerli dosyasındaki verilerin kaydedilmemiş var. bir Kaydet iletişim kutusu görüntülenir. **COM + Tümleştirme Sihirbazı** sonra başlatılır.  
  
2.  İlk sayfa ağacından COM + uygulamasını seçin. COM + uygulaması ağacında bulamazsanız, Bileşen Hizmetleri yüklenir ve Genel Derleme Önbelleği'ne (GAC) kayıtlı olduğunu doğrulayın.  
  
3.  Sonraki sayfada, WCF hizmetleri kullanıma sunmak istediğiniz hangi yöntemlerini seçin. COM + uygulaması'deki tüm desteklenen yöntemleri görüntülenir ve varsayılan olarak seçilidir.  
  
4.  Barındırma için bir yöntem seçin.  
  
5.  Sihirbazda kılavuzları göre diğer ayarları yapılandırın.  
  
6.  Hizmet yapılandırma Düzenleyicisi'ni yapılandırma dosyası oluşturmak için arka planda ComSvcConfig.exe kullanır. Bu tamamlandıktan sonra bir özeti görüntülemek ve sihirbazdan çıkın. Böylece doğrudan düzenleyebilirsiniz oluşturulan yapılandırma dosyası açılır.  
  
### <a name="editing-an-existing-com-configuration"></a>Var olan COM + yapılandırmasını düzenleme  
  
1.  Seçin **dosya** menüsünde **açık** -> **COM + hizmet**...  
  
2.  COM + listeden düzenlemek istediğiniz hizmeti seçin.  
  
3.  Yapılandırma ayarları düzenleyin **COM sözleşmeleri** düğümü.  
  
    > [!NOTE]
    >  Doğrudan da açın ve COM sözleşmeleri içeren bir yapılandırma dosyasını düzenleyin.  
  
## <a name="security"></a>Güvenlik  
 Yapılandırma Düzenleyicisi tarafından oluşturulan bir hizmet yapılandırma dosyası güvenli olması garanti edilmez. Lütfen [güvenlik](../../../docs/framework/wcf/feature-details/security.md) , WCF hizmetleri güvenli hale getirmek nasıl öğrenmek için belgeleri.  
  
 Ayrıca, yapılandırma Düzenleyicisi'ni okuyup geçerli WCF yapılandırma öğeleri yazmak için yalnızca kullanılabilir. Aracı şeması uyumlu, kullanıcı tanımlı öğeleri yok sayar. Ayrıca bu öğeleri yapılandırmasından dosya veya bilinen WCF öğelerde etkilerini belirlemek Kaldır denemez. Bu öğeleri uygulama veya sistem için bir tehdit teşkil olup olmadığını belirlemek kullanıcının sorumluluğundadır.
