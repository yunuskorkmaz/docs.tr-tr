---
title: MageUI.exe (Bildirim Üretme ve Düzenleme Aracı, Grafik İstemci)
ms.date: 03/30/2017
helpviewer_keywords:
- Manifest Generation and Editing tool
- MageUI.exe
ms.assetid: f9e130a6-8117-49c4-839c-c988f641dc14
ms.openlocfilehash: 029e4983ef270bb5272ad0bf541ee34febd9399c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920067"
---
# <a name="mageuiexe-manifest-generation-and-editing-tool-graphical-client"></a>MageUI.exe (Bildirim Üretme ve Düzenleme Aracı, Grafik İstemci)

MageUI.exe, komut satırı aracı Mage.exe ile aynı işlevselliği, ancak Windows tabanlı kullanıcı arabirimi (UI) ile destekler. Bu araçla, dağıtım ve uygulama bildirimleri oluşturabilir, düzenleyebilir ve imzalayabilirsiniz. MageUI.exe hedef ile oluşturulan yeni bildirimler [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Önceki .NET Framework sürümlerini hedeflemek için MageUI.exe'nin önceki sürümleri kullanılmalıdır. Ekleme ya da bir bildirim ya da varolan bildirimleri yeniden imzalarken derlemeleri kaldırma MageUI.exe bildirim hedefleyecek şekilde güncelleştirmez [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Daha fazla bilgi için [Mage.exe (bildirim üretme ve düzenleme aracı)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).

 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için Visual Studio (veya Windows 7'de Visual Studio komut istemi) için geliştirici Komut İstemi'ni kullanın. Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

 Mage.exe ve MageUI.exe iki sürümü Visual Studio'nun bir bileşen olarak dahil edilir. Sürüm bilgileri, MageUI.exe çalıştırın, görmek için seçin **yardımcı**seçip **hakkında**. Bu belge Mage.exe ve MageUI.exe'nin 4.0.x.x sürümünü açıklar.

> [!NOTE]
> MageUI.exe desteklemiyor [compatibleFrameworks](/visualstudio/deployment/compatibleframeworks-element-clickonce-deployment) uygulama bildirimini kaydederken zaten MageUI.exe kullanarak bir sertifika ile imzalanmış olan bir öğe. Bunun yerine, kullanmalısınız [Mage.exe](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
## <a name="uielement-list"></a>UIElement Listesi  
 Aşağıdaki tablo, kullanılabilen menü ve araç çubuğu öğelerini listeler.  
  
|Komut|Menü|Kısayol|Açıklama|  
|-------------|----------|--------------|-----------------|  
|**Uygulama bildirimi**|**Yeni dosya**||Yeni bir uygulama bildirimi oluşturur.|  
|**Dağıtım bildirimi**|**Yeni dosya**||Yeni bir dağıtım bildirimi oluşturur.|  
|**açın**|**Dosya**|CTRL+O|Varolan bir dağıtım bildirimini, uygulama bildirimini ya da düzenlemek için güven lisansını açar.|  
|**Kapat**|**Dosya**|CTRL+F4|Açık bir dosyayı kapatır.<br /><br /> Bir dosyayı kapatmadan önce değiştirirseniz, MageUI.exe dosyayı bir ortak anahtarla, anahtar çiftiyle veya depolanmış bir sertifikayla yeniden imzalamanızı ister.|  
|**Kaydet**|**Dosya**|CTRL+S|Şu anda kullanıcı giriş odağı olan belgeyi diske kaydeder.|  
|**Farklı Kaydet**|**Dosya**||Yeni bir dosya adı ve/veya konum girmenizi sağlayarak bir dosyayı diske kaydeder.|  
|**Tümünü Kaydet**|**Dosya**||MageUI.exe içinde açık durumdaki tüm dosyalarda yapılan değişiklikleri kaydeder.|  
|**Tercihler**|**Dosya**||Açılır **tercihleri** iletişim kutusu. Daha fazla bilgi için aşağıdaki bölüme bakın.|  
|**Çıkış**|**Dosya**|ALT+F4|MageUI.exe'den çıkılır.|  
|**Kes**|**Düzenle**|CTRL+X|Seçili durumdaki metni uygulamadan kaldırır ve sistem Pano'suna taşır.|  
|**Kopyala**|**Düzenle**|CTRL+C|Seçili durumdaki metni sistem Pano'suna kopyalar.|  
|**Yapıştır**|**Düzenle**|CTRL+V|Sistem Pano'sundaki metni etkin durumdaki metin öğesinin içine yapıştırır.|  
|**Delete**|**Düzenle**||Şu anda bir güven lisansı gibi bir listedeki seçili öğenin siler **dağıtım bildirimi** sekmesi.|  
|**Tümünü Kapat**|**Pencere**||MageUI.exe'de açık durumdaki tüm dosyaları kapatır. Bir veya daha fazla dosyanın kaydedilmesi gerekiyorsa, gereksinimi MageUI.exe sizden onları kaydetmenizi ister. MageUI.exe ayrıca imzalanmamış veya değiştirilmiş her dosya için bir imzalama anahtarı seçmenizi de ister.|  
|**hakkında**|**Yardım**||MageUI.exe'nin sürüm ve telif hakkı bilgilerini görüntüler.|  
  
## <a name="preferences-dialog-box"></a>Tercihler İletişim Kutusu  
 **Tercihleri** iletişim kutusu aşağıdaki öğeleri içerir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Oturum açık Kaydet**|Bir dosyadaki değişikliklerinizi kaydedeceğiniz her zaman dosyayı imzalamanızı ister.|  
|**Varsayılan imza sertifikasını kullanın**|Girilen anahtarı kullanır **sertifika dosyası** tüm dosyaları imzalamak için metin kutusu. Bu komut isteminde bir dosyayı kaydettiğinizde, genellikle görünen imzalama ortadan kaldırır ve **oturum kaydederken** seçilir. Üç nokta kullanın (**...** ) düğmesinin yanındaki **sertifika dosyası** anahtarı dosyasını seçmek için metin kutusu.|  
|Özet algoritması|Bağımlılık özetlerinin oluşturması için kullanılan algoritmayı belirtir. Değer "sha256RSA" veya "sha1RSA" olmalıdır. Varsayılan olarak SHA1 kullanılır. Hem uygulama hem de dağıtım bildirimlerinde kullanılır. Kullanıcı bildirimi kaydederken bir sertifika sunarsa, bağımlılık özetleri oluşturmak için sertifikadaki algoritmaları kullanır.|  
  
## <a name="signing-options-dialog-box"></a>İmzalama Seçenekleri İletişim Kutusu  
 **İmzalama seçenekleri** iletişim kutusu, ne zaman bir bildirim veya güven lisansını ilk kez kaydederken ya da bir bildirim veya güven lisansını değiştirdiğinizde görüntülenir. Yalnızca görünür **oturum kaydederken** seçeneğini **tercihleri** iletişim kutusu seçilidir. Bir değer belirten bir bildirimi imzalarken Internet'e gerekir **zaman damgası URI'si** metin kutusu.  
  
 Bu iletişim kutusu aşağıdaki öğeleri içerir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Sertifika dosyası ile imzala**|Bildirimi, dosya sisteminde depolanmış bir dijital sertifika ile imzalar.|  
|**Dosya**|Sertifikayı temsil eden .pfx dosyasının yolunu yazmanız için bir alan sağlar.|  
|**...**|Açılır bir **Dosya Seç** varolan bir .pfx dosyasını seçme iletişim kutusu.|  
|**Yeni**|Bir Sertifika Yetkilisi (CA) aracılığıyla doğrulanamayan yeni bir .pfx oluşturur. İmzalama için kullanılan sertifika türleri hakkında daha fazla bilgi için [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] dağıtımlar [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview).|  
|**Parola**|Bu sertifikayla imzalamak için kullanılan parolayı yazmanız için bir alan sağlar. Parola yoksa boş bırakılabilir.|  
|**Depolanmış sertifika ile imzala**|Bilgisayarınızın sertifika deposunda depolanmış dijital sertifikaların seçilebilir bir listesini görüntüler.|  
|**Zaman damgası URI'si**|Dijital zaman damgası hizmeti Tekdüzen Kaynak Konumlandırıcı'yı (URI) görüntüler. Bildirimlere zaman damgası koymak, uygulamanızın sonraki sürümünü dağıtmadan önce dijital sertifikanızın süresi dolarsa bildirimleri yeniden imzalamanıza gerek kalmamasını sağlar. Daha fazla bilgi için [Windows kök sertifika programı üyeleri](https://go.microsoft.com/fwlink/?LinkId=159000) ve [ClickOnce ve Authenticode](/visualstudio/deployment/clickonce-and-authenticode).|  
|**Oturum yok**|Dijital bir sertifikanın imza eklemeden bildirim kaydetmenize izin verir.|  
  
## <a name="tab-and-panel-descriptions"></a>Sekme ve Panel Açıklamaları  
 MageUI.exe ile bir belge açtığınızda, kendi sekme sayfasında görünür. Her sekme bir özellik paneli kümesi içerir. Paneller belgenin verilerinin gruplandırılmış alt kümelerini içerir.  
  
### <a name="application-manifest-tab"></a>Uygulama bildirim sekmesi  
 **Uygulama bildirimi** sekmesi, bir uygulama bildirimi içeriğini görüntüler. Uygulama bildirimi, dağıtıma dahil tüm dosyaları ve uygulamanın istemci üzerinde çalıştırmak gereken izinleri açıklar.  
  
 **Uygulama bildirimi** sekmesinde aşağıdaki sekmeleri içerir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Ad**|Bu dağıtım hakkında tanımlayıcı bilgileri belirtir.|  
|**Açıklama**|Yayımcı, ürün ve Destek belirten bilgi.|  
|**Uygulama Seçenekleri**|Bu tarayıcı uygulaması olan ve bu bildirim güven bilgi kaynağı olup olmadığını belirtir.|  
|**Dosyalar**|Tüm bu dağıtımı oluşturan dosyaları belirtir.|  
|**Gerekli izinler**|Uygulamayı bir istemci üzerinde çalıştırmak için gerekli minimum izin kümesi belirtir.|  
  
### <a name="name-tab"></a>Adı sekmesi  
 **Adı** ilk oluşturduğunuzda veya bir uygulama bildirimi açtığınızda sekmesi görüntülenir. Dağıtım benzersiz olarak tanımlayan ve isteğe bağlı olarak bir geçerli hedef platformu belirtir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Ad**|Gerekli. Uygulama bildiriminin adı. Genellikle dosya adıyla aynı.|  
|**Sürüm**|Gerekli. Dağıtım biçiminde sürüm numarasını *N.N.N.N*. Yalnızca ilk ana derleme numarası gereklidir. Örneğin, bir uygulama 1.0 sürümü, geçerli değerler verilebilir `1`, `1.0`, `1.0.0`, ve `1.0.0.0`.|  
|**İşlemci**|İsteğe bağlı. Bu dağıtımın çalışabileceği makine mimarisi. Varsayılan `msil`, ya da tüm yönetilen derlemeler varsayılan biçimi olan Microsoft Ara dilidir;. Bu alan, uygulamanızda belirli bir mimari için önceden derlenmiş derlemelerde durumunda değiştirin. Önceden derleme hakkında daha fazla bilgi için bkz: [Ngen.exe (yerel Görüntü Oluşturucu)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).|  
|**Kültür**|İsteğe bağlı. Bu uygulamanın çalıştığı iki parçalı ISO ülke ve bölge kodu. Varsayılan, `neutral` değeridir.|  
|**Ortak anahtar belirteci**|İsteğe bağlı. Bu uygulama bildirimi ile imzalanmış ortak anahtarı. Bu yeni veya işaretsiz bir bildirimi ise, bu alan olarak görünür `Unsigned`.|  
  
### <a name="description-tab"></a>Açıklama sekmesi  
 Bu bilgiler genellikle bir dağıtım bildirimi içinde sağlanır. Bu alanlar yalnızca, değiştirilebilir **uygulama bildiriminin güven bilgilerini kullan** onay kutusunun seçili **uygulama seçenekleri** sekmesi.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Publisher**|Kişi veya kuruluş uygulamadan sorumlu adı. Bu değer, Başlat menüsü klasör adı kullanılır.|  
|**Ürün**|Tam ürün adı. Seçtiyseniz **yerel olarak yükleme** için **uygulama türü** öğede **dağıtım seçenekleri** bu ad dağıtım bildirimini sekmesinde görünür ne olur **Başlat** menü bağlantısı ve **Program Ekle veya Kaldır** bu uygulama için.|  
|**Destek konumu**|URL, müşterilerin Yardım alabilir ve uygulama için destek.|  
  
### <a name="application-options-tab"></a>Uygulama Seçenekleri sekmesi  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Windows Presentation Foundation gözatma uygulaması**|Bu bir XAML tarayıcı uygulaması (XBAP) tarayıcıda çalışan bir WPF uygulaması olup olmadığını belirtir.|  
|**Uygulama bildirim güven bilgileri kullanın**|Bu bildirimi güven bilgileri içerip içermediğini belirtir.|  
  
### <a name="files-tab"></a>Dosyalar sekmesi  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Uygulama dizini**|Uygulamanın dosyaların bulunduğu dizin. Üç nokta simgesini kullanın (**...** ) düğmesini dizini seçin.|  
|**Doldur**|Uygulama bildirimine uygulama dizini ve alt dizinleri tüm dosyaları ekler. MageUI.exe dizinde tek bir yürütülebilir dosya bulursa, onu otomatik olarak bu istemcide ClickOnce uygulaması başlatıldığında ilk yürütülen dosya giriş noktası olarak işaretler.|  
|**Uygulama dosyaları**|Tüm uygulama dosyaları listeler. Her dosyanın, aşağıda açıklanan üç düzenlenebilir özniteliği vardır.|  
|**Dosya türü**|Dosya türü, dört değerlerden biri olabilir:<br /><br /> -Yok.<br />-Giriş noktası. Uygulama birincil yürütülebilir. Yalnızca bir yürütülebilir dosya giriş noktası olarak işaretlenebilir.<br />-Veri dosyası. Uygulama veri sağlayan bir XML dosyası gibi bir dosya.<br />-Simge dosyası. Bir uygulama simgesi, masaüstünde veya bir uygulama penceresinin üst köşesindeki gibi görünür.|  
|**Optional**|İsteğe bağlı olarak işaretlenmiş dosyaların ilk yükleme veya güncelleştirme yüklenmez ancak System.Deployment üzerine API'sini kullanarak çalışma zamanında yüklenebilir. Daha fazla bilgi için [izlenecek yol: API tasarımcıyı kullanarak ClickOnce dağıtımı ile isteğe bağlı derlemeleri indirme](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer).|  
|**Grup**|İsteğe bağlı dosya kümesi için bir etiket. Birtakım dosyalarda Grup etiketi uygulamak ve bir dizi tek bir API çağrısı ile dosya indirme için isteğe bağlı API'yi kullanın.|  
  
### <a name="permissions-required-tab"></a>Gerekli izinler sekmesi  
 Kullanım **gerekli izinler** uygulamanızı yerel bilgisayarda varsayılan olarak verilir daha fazla erişimi vermek gerekiyorsa sekmesi. Daha fazla bilgi için [ClickOnce uygulamalarının güvenliğini sağlama](/visualstudio/deployment/securing-clickonce-applications).  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**İzin türünü ayarlama**|İstemci üzerinde çalıştırmak için bu uygulama için gerekli minimum izin kümesi. Bu izin kümeleri açıklamasını ve yapabilir veya talep değil, hangi izinlerin [adlandırılmış izin kümeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).|  
|**Ayrıntılar**|Bir izni temsil etmek için uygulama bildirimi için oluşturulan XML ayarlayın. Uygulama bildirimi XML biçimi iyi bir anlayışa sahip değilseniz bu XML el ile düzenlemeniz değil. Daha fazla bilgi için [ClickOnce Uygulama bildirimi](/visualstudio/deployment/clickonce-application-manifest).|  
  
### <a name="deployment-manifest-tab"></a>Dağıtım bildirim sekmesi  
 **Dağıtım bildirimi** sekmesinde aşağıdaki sekmeleri içerir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Ad**|Bu dağıtım hakkında tanımlayıcı bilgileri belirtir.|  
|**Açıklama**|Yayımcı, ürün ve Destek belirten bilgi.|  
|**Dağıtım seçenekleri**|Uygulama türü ve başlangıç konumu gibi dağıtım hakkında ek bilgileri belirtir.|  
|**Güncelleştirme Seçenekleri**|Ne sıklıkta belirtir [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] uygulama güncelleştirmeleri denetlesin.|  
|**Uygulama başvurusu**|Bu dağıtım için uygulama bildirimini belirtir.|  
  
### <a name="name-tab"></a>Adı sekmesi  
 **Adı** ilk oluşturduğunuzda veya bir dağıtım bildirimini açmak sekmesi görüntülenir. Dağıtım benzersiz olarak tanımlayan ve isteğe bağlı olarak bir geçerli hedef platformu belirtir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Ad**|Gerekli. Dağıtım bildiriminin adı. Genellikle dosya adıyla aynı.|  
|**Sürüm**|Gerekli. Dağıtım biçiminde sürüm numarasını *N.N.N.N*. Yalnızca ilk ana derleme numarası gereklidir. Örneğin, bir uygulama 1.0 sürümü, geçerli değerler verilebilir `1`, `1.0`, `1.0.0`, ve `1.0.0.0`.|  
|**İşlemci**|İsteğe bağlı. Bu dağıtımın çalışabileceği makine mimarisi. Varsayılan `msil`, ya da Microsoft Ara dil, tüm yönetilen derlemeler varsayılan biçimi. Bu alan, uygulamanızda belirli bir mimari için derlemeleri derlediğiniz tıklarsanız.|  
|**Kültür**|İsteğe bağlı. Bu uygulamanın çalıştığı iki parçalı ISO ülke/bölge kodu. Varsayılan, `neutral` değeridir.|  
|**Ortak anahtar belirteci**|İsteğe bağlı. Bu dağıtım bildirimi ile imzalanmış ortak anahtarı. Bu yeni veya işaretsiz bir bildirimi ise, bu alan olarak görünür `Unsigned`.|  
  
### <a name="description-tab"></a>Açıklama sekmesi  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Publisher**|Gerekli. Kişi veya kuruluş uygulamadan sorumlu adı. Bu değer, Başlat menüsü klasör adı kullanılır.|  
|**Ürün**|Gerekli. Tam ürün adı. Seçtiyseniz **yerel olarak yükleme** için **uygulama türü** öğede **dağıtım seçenekleri** sekmesinde, bu adı ne görünür olacaktır **Başlat** menü bağlantısı ve **Program Ekle veya Kaldır** bu uygulama için.|  
|**Destek konumu**|İsteğe bağlı. URL, müşterilerin Yardım alabilir ve uygulama için destek.|  
  
### <a name="deployment-options-tab"></a>Dağıtım Seçenekleri sekmesi  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Uygulama türü**|İsteğe bağlı. Bu uygulama kendisini istemci bilgisayara yükler olup olmadığını belirtir (**yerel olarak yükleme**), çevrimiçi çalışır (**yalnızca çevrimiçi**), veya tarayıcıda çalışan bir WPF uygulaması (**WPF tarayıcısı Uygulama**). Varsayılan değer **yerel olarak yükleme**.|  
|**Başlangıç konumu**|İsteğe bağlı. URL, gerçekte uygulamanın başlatılmalıdır. Uygulamanın kendisini Web'den güncelleştirmelisiniz CD'den dağıtırken yararlıdır.|  
|**Başlangıç konumu (ProviderURL) bildirime dahil**|İsteğe bağlı. URL'sini belirtir, [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] uygulama güncelleştirmeleri için inceleyeceği.|  
|**Yükledikten sonra otomatik olarak Çalıştırma uygulaması**|Gerekli. Belirten [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] uygulama, ilk yüklemenin hemen sonrasında bir URL'den çalışmalı. Onay kutusu seçili varsayılandır.|  
|**Uygulamaya geçirilecek URL parametrelerini izin ver**|Gerekli. Parametre veri aktarımını verir [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] dağıtım bildiriminin URL'ye eklenen sorgu dizesi aracılığıyla uygulama. Onay kutusunun işareti varsayılandır.|  
|**.Deploy dosya uzantısını kullanma**|Gerekli. Bu onay kutusu seçildiğinde, uygulama bildiriminde tüm dosyaları .deploy uzantısını olmalıdır. Onay kutusunun işareti varsayılandır.|  
  
### <a name="update-options-tab"></a>Seçenekler sekmesinde güncelleştir  
 **Güncelleştirme Seçenekleri** sekmesi yalnızca seçenekleri içerir, burada bahsedilen **uygulama türü** seçim kutusunu **adı** sekmesinde ayarlanmış **yerel olarak yükle** .  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Bu uygulama güncelleştirmeleri denetlemeli**|Belirtir olup olmadığını [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] uygulama güncelleştirmeleri denetlesin. Bu onay kutusu seçili değilse, bu program aracılığıyla API'leri kullanarak güncelleştirme sürece uygulama güncelleştirmeleri denetlemeyecek <xref:System.Deployment.Application> ad alanı.|  
|**Uygulamanın güncelleştirmeleri denetleyeceği zamanı seçin**|Güncelleme kontrolleri için iki seçenek sağlar:<br /><br /> -   **Uygulama başlatılmadan önce**. Güncelleştirme denetimi uygulamanın yürütülmesini önce gerçekleştirilir.<br />-   **Uygulama başlatıldıktan sonra**. Güncelleştirme denetimi uygulamanın ana formu başlatıldı ve uygulamayı bir sonraki başlatılışında çalışır sonra başlar.|  
|**Güncelleştirme denetim sıklığı**|Ne sıklıkta belirler [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] güncelleştirmeleri denetlemeniz gerekir:<br /><br /> -   **Uygulama her çalıştırıldığında denetle**. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] Kullanıcı uygulamayı her açtığında bir güncelleştirme kontrolü gerçekleştirir.<br />-   **Denetleme her**: Bir zaman aralığı ve güncelleştirmeleri denetlemeden önce geçmesi gereken bir birimi (saatlik, günlük veya haftalık) seçin.|  
|**Bu uygulama için gerekli en düşük sürüm belirtin**|İsteğe bağlı. Uygulamanızın belirli bir sürümü eski bir sürümüyle çalışamıyor kullanıcılarınız, zorunlu bir yükleme olduğunu belirtir.|  
|**Sürüm**|Gerekli if **bu uygulama için gerekli en düşük sürüm belirtin** onay kutusu seçilidir. Sağlanan sürüm numarası biçiminde olmalıdır *N.N.N.N*. Yalnızca ilk ana derleme numarası gereklidir. Örneğin, bir uygulama 1.0 sürümü, geçerli değerler verilebilir `1`, `1.0`, `1.0.0`, ve `1.0.0.0`.|  
  
### <a name="application-reference-tab"></a>Uygulama başvurusu sekmesi  
 **Uygulama başvurusu** sekmesini içeren aynı alanları **adı** bu konuda daha önce açıklanan sekmesi. Şu alan işlemdir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Bildirimi seçin**|Uygulama bildirimini seçmenize olanak sağlar. Bir uygulama bildirimi seçtiğinizde sayfadaki diğer alanların tümünü doldurur.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)
- [İzlenecek yol: ClickOnce Uygulamasını El ile Dağıtma](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)
