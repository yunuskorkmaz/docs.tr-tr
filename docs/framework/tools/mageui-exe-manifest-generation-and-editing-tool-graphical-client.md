---
title: MageUI.exe (Bildirim Üretme ve Düzenleme Aracı, Grafik İstemci)
ms.date: 03/30/2017
helpviewer_keywords:
- Manifest Generation and Editing tool
- MageUI.exe
ms.assetid: f9e130a6-8117-49c4-839c-c988f641dc14
ms.openlocfilehash: 99f522181232d16b9913ba3c55f34274b75d8966
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449405"
---
# <a name="mageuiexe-manifest-generation-and-editing-tool-graphical-client"></a>MageUI.exe (Bildirim Üretme ve Düzenleme Aracı, Grafik İstemci)

MageUI.exe, komut satırı aracı Mage.exe ile aynı işlevselliği, ancak Windows tabanlı kullanıcı arabirimi (UI) ile destekler. Bu araçla, dağıtım ve uygulama bildirimleri oluşturabilir, düzenleyebilir ve imzalayabilirsiniz. MageUI. exe ile oluşturulan yeni bildirimler [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]hedefleyin. Önceki .NET Framework sürümlerini hedeflemek için MageUI.exe'nin önceki sürümleri kullanılmalıdır. Bir bildirimden derleme ekleme veya kaldırma ya da varolan bildirimleri yeniden imzalama sırasında, MageUI. exe bildirimi hedef [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]olarak güncelleştirmez. Daha fazla bilgi için bkz. [Mage. exe (bildirim oluşturma ve düzenleme aracı)](mage-exe-manifest-generation-and-editing-tool.md).

 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).

 Visual Studio 'nun bir bileşeni olarak Mage. exe ve MageUI. exe ' nin iki sürümü dahildir. Sürüm bilgilerini görmek için MageUI. exe ' yi çalıştırın, **Yardım**' ı seçin ve **hakkında**' yı seçin. Bu belge Mage.exe ve MageUI.exe'nin 4.0.x.x sürümünü açıklar.

> [!NOTE]
> MageUI. exe, MageUI. exe kullanılarak bir sertifikayla imzalanmış bir uygulama bildirimini kaydederken [Compatibleçerçeveleri](/visualstudio/deployment/compatibleframeworks-element-clickonce-deployment) öğesini desteklemez. Bunun yerine [Mage. exe](mage-exe-manifest-generation-and-editing-tool.md)kullanmanız gerekir.  
  
## <a name="uielement-list"></a>UIElement Listesi  
 Aşağıdaki tablo, kullanılabilen menü ve araç çubuğu öğelerini listeler.  
  
|Komut|Menü|Kısayol|Açıklama|  
|-------------|----------|--------------|-----------------|  
|**Uygulama bildirimi**|**Dosya, yeni**||Yeni bir uygulama bildirimi oluşturur.|  
|**Dağıtım bildirimi**|**Dosya, yeni**||Yeni bir dağıtım bildirimi oluşturur.|  
|**Açın**|**Dosyasýný**|CTRL+O|Varolan bir dağıtım bildirimini, uygulama bildirimini ya da düzenlemek için güven lisansını açar.|  
|**~Eksik**|**Dosyasýný**|CTRL+F4|Açık bir dosyayı kapatır.<br /><br /> Bir dosyayı kapatmadan önce değiştirirseniz, MageUI.exe dosyayı bir ortak anahtarla, anahtar çiftiyle veya depolanmış bir sertifikayla yeniden imzalamanızı ister.|  
|**Kaydet**|**Dosyasýný**|CTRL+S|Şu anda kullanıcı giriş odağı olan belgeyi diske kaydeder.|  
|**Farklı Kaydet**|**Dosyasýný**||Yeni bir dosya adı ve/veya konum girmenizi sağlayarak bir dosyayı diske kaydeder.|  
|**Tümünü Kaydet**|**Dosyasýný**||MageUI.exe içinde açık durumdaki tüm dosyalarda yapılan değişiklikleri kaydeder.|  
|**Tercihler**|**Dosyasýný**||**Tercihler** iletişim kutusunu açar. Daha fazla bilgi için aşağıdaki bölüme bakın.|  
|**Çıkış**|**Dosyasýný**|ALT+F4|MageUI.exe'den çıkılır.|  
|**Kesildiğinde**|**Düzenle**|CTRL+X|Seçili durumdaki metni uygulamadan kaldırır ve sistem Pano'suna taşır.|  
|**Kopyala**|**Düzenle**|CTRL+C|Seçili durumdaki metni sistem Pano'suna kopyalar.|  
|**Masına**|**Düzenle**|CTRL+V|Sistem Pano'sundaki metni etkin durumdaki metin öğesinin içine yapıştırır.|  
|**Sil**|**Düzenle**||Bir listede seçili olan bir öğeyi, **dağıtım bildirimi** sekmesindeki güven lisansı gibi siler.|  
|**Tümünü Kapat**|**Penceresine**||MageUI.exe'de açık durumdaki tüm dosyaları kapatır. Bir veya daha fazla dosyanın kaydedilmesi gerekiyorsa, gereksinimi MageUI.exe sizden onları kaydetmenizi ister. MageUI.exe ayrıca imzalanmamış veya değiştirilmiş her dosya için bir imzalama anahtarı seçmenizi de ister.|  
|**Bilgi**|**Yardım**||MageUI.exe'nin sürüm ve telif hakkı bilgilerini görüntüler.|  
  
## <a name="preferences-dialog-box"></a>Tercihler İletişim Kutusu  
 **Tercihler** iletişim kutusu aşağıdaki öğeleri içerir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Kaydederken oturum aç**|Bir dosyadaki değişikliklerinizi kaydedeceğiniz her zaman dosyayı imzalamanızı ister.|  
|**Varsayılan imza sertifikasını kullan**|Tüm dosyaları imzalamak için **sertifika dosyası** metin kutusunda girilen anahtarı kullanır. Bu, genellikle bir dosyayı kaydettiğinizde ve **kaydederken oturum** açtığınızda görüntülenen imzalama isteminin seçili olduğunu ortadan kaldırır. Bir anahtar dosyası seçmek için **sertifika dosyası** metin kutusunun yanındaki üç nokta ( **...** ) düğmesini kullanın.|  
|Özet algoritması|Bağımlılık özetlerinin oluşturması için kullanılan algoritmayı belirtir. Değer "sha256RSA" veya "sha1RSA" olmalıdır. Varsayılan olarak SHA1 kullanılır. Hem uygulama hem de dağıtım bildirimlerinde kullanılır. Kullanıcı bildirimi kaydederken bir sertifika sunarsa, bağımlılık özetleri oluşturmak için sertifikadaki algoritmaları kullanır.|  
  
## <a name="signing-options-dialog-box"></a>İmzalama Seçenekleri İletişim Kutusu  
 Bir bildirimi veya güven lisansını ilk kez kaydettiğinizde veya bir bildirimi veya güven lisansını değiştirdiğinizde **Imzalama seçenekleri** iletişim kutusu görüntülenir. Yalnızca **Tercihler** Iletişim kutusunda **kaydetme oturum aç** seçeneği işaretliyse görüntülenir. Zaman **damgası URI 'si** metin kutusunda bir değer belirten bir bildirimi imzalarken Internet 'e bağlı olmanız gerekir.  
  
 Bu iletişim kutusu aşağıdaki öğeleri içerir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Sertifika dosyası ile imzala**|Bildirimi, dosya sisteminde depolanmış bir dijital sertifika ile imzalar.|  
|**Dosyasýný**|Sertifikayı temsil eden .pfx dosyasının yolunu yazmanız için bir alan sağlar.|  
|**...**|Varolan bir. pfx dosyasını seçmek için **Dosya Seç** iletişim kutusunu açar.|  
|**Yeni**|Bir Sertifika Yetkilisi (CA) aracılığıyla doğrulanamayan yeni bir .pfx oluşturur. ClickOnce dağıtımlarını imzalamak için kullanılan sertifika türleri hakkında daha fazla bilgi için bkz. [Güvenilen uygulama dağıtımına genel bakış](/visualstudio/deployment/trusted-application-deployment-overview).|  
|**Parolayı**|Bu sertifikayla imzalamak için kullanılan parolayı yazmanız için bir alan sağlar. Parola yoksa boş bırakılabilir.|  
|**Depolanan sertifikayla imzala**|Bilgisayarınızın sertifika deposunda depolanmış dijital sertifikaların seçilebilir bir listesini görüntüler.|  
|**Zaman damgası URI 'SI**|Dijital zaman damgası hizmeti Tekdüzen Kaynak Konumlandırıcı'yı (URI) görüntüler. Bildirimlere zaman damgası koymak, uygulamanızın sonraki sürümünü dağıtmadan önce dijital sertifikanızın süresi dolarsa bildirimleri yeniden imzalamanıza gerek kalmamasını sağlar. Daha fazla bilgi için bkz. [Windows kök sertifika programı üyeleri](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)) ve [ClickOnce ve Authenticode](/visualstudio/deployment/clickonce-and-authenticode).|  
|**Imzalama**|Dijital bir sertifikanın imza eklemeden bildirim kaydetmenize izin verir.|  
  
## <a name="tab-and-panel-descriptions"></a>Sekme ve Panel Açıklamaları  
 MageUI.exe ile bir belge açtığınızda, kendi sekme sayfasında görünür. Her sekme bir özellik paneli kümesi içerir. Paneller belgenin verilerinin gruplandırılmış alt kümelerini içerir.  
  
### <a name="application-manifest-tab"></a>Uygulama bildirim sekmesi  
 **Uygulama bildirimi** sekmesi bir uygulama bildiriminin içeriğini görüntüler. Uygulama bildirimi, dağıtıma dahil edilen tüm dosyaları ve uygulamanın istemcide çalışması için gerekli izinleri açıklar.  
  
 **Uygulama bildirimi** sekmesi aşağıdaki sekmeleri içerir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Ad**|Bu dağıtım hakkındaki bilgileri tanımlamayı belirtir.|  
|**Açıklama**|Yayımcı, ürün ve destek bilgilerini belirtir.|  
|**Uygulama seçenekleri**|Bunun bir tarayıcı uygulaması olup olmadığını ve bu bildirimin güven bilgisi kaynağı olup olmadığını belirtir.|  
|**Dosyalar**|Bu dağıtımı oluşturan tüm dosyaları belirtir.|  
|**Gerekli izinler**|Uygulamanın bir istemcide çalışması için gereken en düşük izin kümesini belirtir.|  
  
### <a name="name-tab"></a>Ad sekmesi  
 **Ad** sekmesi, ilk olarak bir uygulama bildirimi oluşturduğunuzda veya açtığınızda görüntülenir. Dağıtımı benzersiz bir şekilde tanımlar ve isteğe bağlı olarak geçerli bir hedef platform belirtir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Ad**|Gerekli. Uygulama bildiriminin adı. Genellikle dosya adıyla aynıdır.|  
|**Sürüm**|Gerekli. *N. n. n. n*biçimindeki dağıtımın sürüm numarası. Yalnızca ilk ana yapı numarası gereklidir. Örneğin, bir uygulamanın 1,0 sürümü için geçerli değerler `1`, `1.0`, `1.0.0`ve `1.0.0.0`içerebilir.|  
|**İsiyle**|İsteğe bağlı. Bu dağıtımın çalıştırılabileceği makine mimarisi. Varsayılan değer, tüm yönetilen derlemelerin varsayılan biçimi olan `msil`veya Microsoft ara dildir. Uygulamanızda belirli bir mimari için derlemeleri önceden derlediğiniz takdirde bu alanı değiştirin. Ön derleme hakkında daha fazla bilgi için bkz. [Ngen. exe (yerel görüntü Oluşturucu)](ngen-exe-native-image-generator.md).|  
|**Ayarı**|İsteğe bağlı. Bu uygulamanın çalıştığı iki bölümlü ISO ülkesi ve bölge kodu. Varsayılan, `neutral` değeridir.|  
|**Ortak anahtar belirteci**|İsteğe bağlı. Bu uygulama bildiriminin imzalandığı ortak anahtar. Bu yeni veya imzasız bir bildirimidir, bu alan `Unsigned`olarak görünür.|  
  
### <a name="description-tab"></a>Açıklama sekmesi  
 Bu bilgiler genellikle dağıtım bildirimi içinde sağlanır. Bu alanlar yalnızca **uygulama seçenekleri** sekmesinde **uygulama bildirimi güven bilgileri kullan** onay kutusu seçiliyse değiştirilebilir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**'In**|Uygulamadan sorumlu kişinin veya kuruluşun adı. Bu değer, Başlat menüsü klasör adı olarak kullanılır.|  
|**Ürünüyle**|Tam ürün adı. Dağıtım bildiriminin **dağıtım seçenekleri** sekmesinde **uygulama türü** öğesi için **yerel olarak yüklemeyi** seçtiyseniz, bu ad, bu uygulama Için **Başlat** menüsü bağlantısında ve **Program Ekle/Kaldır** 'da görünür.|  
|**Destek konumu**|Müşterilerin uygulama için yardım ve destek alabileceği URL.|  
  
### <a name="application-options-tab"></a>Uygulama seçenekleri sekmesi  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Windows Presentation Foundation tarayıcı uygulaması**|Bu, tarayıcıda bir XAML tarayıcı uygulaması (XBAP) olarak çalışan bir WPF uygulaması olup olmadığını belirtir.|  
|**Uygulama bildirimi güven bilgilerini kullan**|Bu bildirimin güven bilgileri içerip içermediğini belirtir.|  
  
### <a name="files-tab"></a>Dosyalar Sekmesi  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Uygulama dizini**|Uygulamanın dosyalarının bulunduğu dizin. Dizini seçmek için üç nokta ( **...** ) düğmesini kullanın.|  
|**Veriyle**|Uygulama dizinindeki tüm dosyaları ve alt dizinleri uygulama bildirimine ekler. MageUI. exe dizinde tek bir yürütülebilir dosya bulursa, bunu otomatik olarak giriş noktası olarak işaretler, bu dosya, istemci üzerinde ClickOnce uygulaması başlatıldığında ilk yürütülür.|  
|**Uygulama dosyaları**|Uygulamadaki tüm dosyaları listeler. Her dosyanın aşağıda ele alınan üç düzenlenebilir özniteliği vardır.|  
|**Dosya türü**|Dosya türü dört değerden biri olabilir:<br /><br /> Seçim.<br />-Giriş noktası. Uygulamanın birincil yürütülebilir dosyası. Giriş noktası olarak yalnızca bir yürütülebilir dosya işaretlenebilir.<br />-Veri dosyası. Uygulamaya veri sağlayan bir XML dosyası gibi bir dosya.<br />-Simge dosyası. Masaüstünde veya bir uygulama penceresinin köşesinde görünen gibi bir uygulama simgesi.|  
|**Optional**|İsteğe bağlı olarak işaretlenen Dosyalar ilk yüklemede veya güncelleştirmesinde indirilmez, ancak System. Deployment Isteğe bağlı API kullanılarak çalışma zamanında indirilebilir. Daha fazla bilgi için bkz. [Izlenecek yol: Tasarımcıyı kullanarak ClickOnce dağıtım API 'si Ile isteğe bağlı derlemeleri indirme](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer).|  
|**Grubu**|İsteğe bağlı dosyalar kümesi için bir etiket. Bir dosya kümesine bir grup etiketi uygulayabilir ve tek bir API çağrısıyla bir toplu dosya indirmek için Isteğe bağlı API 'yi kullanabilirsiniz.|  
  
### <a name="permissions-required-tab"></a>Gerekli izinler sekmesi  
 Uygulamanıza varsayılan olarak verilen yerel bilgisayara daha fazla erişim vermeniz gerekiyorsa, **gerekli izinler** sekmesini kullanın. Daha fazla bilgi için bkz. [ClickOnce uygulamalarının güvenliğini sağlama](/visualstudio/deployment/securing-clickonce-applications).  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**İzin kümesi türü**|Bu uygulamanın istemcide çalışması için gereken en düşük izin kümesi. Bu izin kümelerinin açıklaması ve ne yaptıkları veya talep verilmeyen izinler için bkz. [adlandırılmış Izin kümeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).|  
|**Bilgileri**|İzin kümesini temsil etmesi için uygulama bildirimi için oluşturulan XML. Uygulama bildirimi XML biçimi hakkında iyi bir fikir sahibi değilseniz, bu XML 'i el ile düzenlememelisiniz. Daha fazla bilgi için bkz. [ClickOnce uygulama bildirimi](/visualstudio/deployment/clickonce-application-manifest).|  
  
### <a name="deployment-manifest-tab"></a>Dağıtım bildirimi sekmesi  
 **Dağıtım bildirimi** sekmesi aşağıdaki sekmeleri içerir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Ad**|Bu dağıtım hakkındaki bilgileri tanımlamayı belirtir.|  
|**Açıklama**|Yayımcı, ürün ve destek bilgilerini belirtir.|  
|**Dağıtım seçenekleri**|Dağıtım hakkındaki uygulama türü ve başlangıç konumu gibi ek bilgileri belirtir.|  
|**Güncelleştirme seçenekleri**|ClickOnce 'ın uygulama güncelleştirmelerini denetlemesi gereken sıklığı belirtir.|  
|**Uygulama başvurusu**|Bu dağıtım için uygulama bildirimini belirtir.|  
  
### <a name="name-tab"></a>Ad sekmesi  
 Önce bir dağıtım bildirimi oluşturduğunuzda veya açtığınızda **ad** sekmesi görüntülenir. Dağıtımı benzersiz bir şekilde tanımlar ve isteğe bağlı olarak geçerli bir hedef platform belirtir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Ad**|Gerekli. Dağıtım bildiriminin adı. Genellikle dosya adıyla aynıdır.|  
|**Sürüm**|Gerekli. *N. n. n. n*biçimindeki dağıtımın sürüm numarası. Yalnızca ilk ana yapı numarası gereklidir. Örneğin, bir uygulamanın 1,0 sürümü için geçerli değerler `1`, `1.0`, `1.0.0`ve `1.0.0.0`içerebilir.|  
|**İsiyle**|İsteğe bağlı. Bu dağıtımın çalıştırılabileceği makine mimarisi. Varsayılan olarak, tüm yönetilen derlemelerin varsayılan biçimi `msil`veya Microsoft ara dildir. Uygulamanızda belirli bir mimari için derlemeleri derlediğiniz takdirde bu alanı değiştirin.|  
|**Ayarı**|İsteğe bağlı. Bu uygulamanın çalıştığı iki bölümlü ISO ülke/bölge kodu. Varsayılan, `neutral` değeridir.|  
|**Ortak anahtar belirteci**|İsteğe bağlı. Bu dağıtım bildiriminin imzalandığı ortak anahtar. Bu yeni veya imzasız bir bildirimidir, bu alan `Unsigned`olarak görünür.|  
  
### <a name="description-tab"></a>Açıklama sekmesi  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**'In**|Gerekli. Uygulamadan sorumlu kişinin veya kuruluşun adı. Bu değer, Başlat menüsü klasör adı olarak kullanılır.|  
|**Ürünüyle**|Gerekli. Tam ürün adı. **Dağıtım seçenekleri** sekmesindeki **uygulama türü** öğesi için **yerel olarak yüklemeyi** seçtiyseniz, bu ad, bu uygulama Için **Başlat** menüsü bağlantısında ve **Program Ekle/Kaldır** bölümünde görüntülenmeyecektir.|  
|**Destek konumu**|İsteğe bağlı. Müşterilerin uygulama için yardım ve destek alabileceği URL.|  
  
### <a name="deployment-options-tab"></a>Dağıtım seçenekleri sekmesi  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Uygulama türü**|İsteğe bağlı. Bu uygulamanın kendisini istemci bilgisayara (**yerel olarak yükleme**) yükleyip yüklemediğinden, çevrimiçi (**yalnızca çevrimiçi**) çalışan veya tarayıcıda çalışan bir WPF uygulaması (**WPF tarayıcı uygulaması**) olduğunu belirtir. Varsayılan değer **yerel olarak yüklenir**.|  
|**Başlangıç konumu**|İsteğe bağlı. Uygulamanın gerçekten başlatılması gereken URL. Kendisini Web 'den güncelleştiren bir CD 'den bir uygulama dağıttığınızda faydalıdır.|  
|**Bildirimde başlangıç konumunu (ProviderURL) dahil et**|İsteğe bağlı. ClickOnce'ın uygulama güncelleştirmeleri için inceleyeceği URL'yi belirtir.|  
|**Yükledikten sonra otomatik olarak uygulama Çalıştır**|Gerekli. ClickOnce uygulamasının bir URL 'den ilk yüklemesinden hemen sonra çalışacağını belirtir. Onay kutusu varsayılan olarak seçilidir.|  
|**URL parametrelerinin uygulamaya geçirilmesine izin ver**|Gerekli. Parametre verilerinin, dağıtım bildiriminin URL 'sine eklenen bir sorgu dizesi aracılığıyla ClickOnce uygulamasına aktarılmasına izin verir. Onay kutusunun işareti varsayılan olarak silinir.|  
|**. Deploy dosya uzantısını kullan**|Gerekli. Seçildiğinde, uygulama bildirimindeki tüm dosyalar. deploy uzantısına sahip olmalıdır. Onay kutusunun işareti varsayılan olarak silinir.|  
  
### <a name="update-options-tab"></a>Güncelleştirme seçenekleri sekmesi  
 **Güncelleştirme seçenekleri** sekmesi yalnızca **ad** sekmesindeki **uygulama türü** seçim kutusu **yerel olarak yüklenmek**üzere ayarlandığında burada bahsedilen seçenekleri içerir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Bu uygulama güncelleştirmeleri denetlemelidir**|ClickOnce 'ın uygulama güncelleştirmelerini denetleyip denetmeyeceğini belirtir. Bu onay kutusu seçili değilse, <xref:System.Deployment.Application> ad alanındaki API 'Leri kullanarak program aracılığıyla güncelleştirmediğiniz takdirde uygulama güncelleştirmeleri denetetmez.|  
|**Uygulamanın güncelleştirmeleri ne zaman denetlemesi gerektiğini seçin**|Güncelleştirme denetimleri için iki seçenek sunar:<br /><br /> **uygulama başlamadan önce**-   . Güncelleştirme denetimi, uygulama yürütmeden önce gerçekleştirilir.<br />**uygulama başladıktan sonra**-   . Güncelleştirme denetimi, uygulamanın ana formu başlatıldıktan sonra başlar ve uygulama bir sonraki sefer başlatıldığında çalışır.|  
|**Güncelleştirme Denetim sıklığı**|ClickOnce 'ın güncelleştirmeleri ne sıklıkta denetleyeceğini belirler:<br /><br /> **uygulama her çalıştığında denetim**-   . Kullanıcı uygulamayı her açtığında ClickOnce bir güncelleştirme denetimi yapar.<br />-   **Denetim sıklığı**: güncelleştirmeleri denetlemeden önce geçmesi gereken bir zaman aralığı ve birim (saat, gün veya hafta) seçin.|  
|**Bu uygulama için gerekli en düşük sürümü belirtin**|İsteğe bağlı. Uygulamanızın belirli bir sürümünün gerekli bir yükleme olduğunu belirtir ve kullanıcılarınızın daha önceki bir sürümle çalışmasını önler.|  
|**Sürüm**|**Bu uygulama için gerekli en düşük sürümü belirtirseniz** onay kutusu seçilidir. Sağlanan sürüm numarası *n. n. n. n*biçiminde olmalıdır. Yalnızca ilk ana yapı numarası gereklidir. Örneğin, bir uygulamanın 1,0 sürümü için geçerli değerler `1`, `1.0`, `1.0.0`ve `1.0.0.0`içerebilir.|  
  
### <a name="application-reference-tab"></a>Uygulama başvurusu sekmesi  
 **Uygulama başvurusu** sekmesi, bu konuda daha önce açıklanan **ad** sekmesi ile aynı alanları içerir. Bir özel durum aşağıdaki alandır.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Bildirim Seç**|Uygulama bildirimini seçmenizi sağlar. Uygulama bildirimini seçtiğinizde, bu sayfadaki diğer tüm alanlar doldurulur.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)
- [İzlenecek yol: ClickOnce Uygulamasını El ile Dağıtma](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](mage-exe-manifest-generation-and-editing-tool.md)
