---
title: "MageUI.exe (Bildirim Üretme ve Düzenleme Aracı, Grafik İstemci)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Manifest Generation and Editing tool
- MageUI.exe
ms.assetid: f9e130a6-8117-49c4-839c-c988f641dc14
caps.latest.revision: "38"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1450acd6c4b68be79ad769106dfebc7d89484525
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="mageuiexe-manifest-generation-and-editing-tool-graphical-client"></a>MageUI.exe (Bildirim Üretme ve Düzenleme Aracı, Grafik İstemci)
MageUI.exe, komut satırı aracı Mage.exe ile aynı işlevselliği, ancak Windows tabanlı kullanıcı arabirimi (UI) ile destekler. Bu araçla, dağıtım ve uygulama bildirimleri oluşturabilir, düzenleyebilir ve imzalayabilirsiniz. MageUI.exe hedefle oluşturulan yeni bildirimleri [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Önceki .NET Framework sürümlerini hedeflemek için MageUI.exe'nin önceki sürümleri kullanılmalıdır. Ekleme ya da bir bildirim veya varolan bildirimlerini yeniden imzalama derlemeleri kaldırma MageUI.exe bildirim hedefe güncelleştirmez [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Daha fazla bilgi için bkz: [Mage.exe (bildirim üretme ve düzenleme aracı)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Mage.exe ve MageUI.exe iki sürümü bir bileşeni olarak dahil edilen [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] kurulumu. Sürüm bilgileri, çalışma MageUI.exe görmek için seçin **yardımcı**seçip **hakkında**. Bu belge Mage.exe ve MageUI.exe'nin 4.0.x.x sürümünü açıklar.  
  
> [!NOTE]
>  MageUI.exe desteklemiyor [compatibleFrameworks](/visualstudio/deployment/compatibleframeworks-element-clickonce-deployment) bir uygulama bildirimi kaydetme zaten MageUI.exe kullanarak bir sertifikayla imzalanmış zaman öğesi. Bunun yerine, kullanmanız gereken [Mage.exe](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
## <a name="uielement-list"></a>UIElement Listesi  
 Aşağıdaki tablo, kullanılabilen menü ve araç çubuğu öğelerini listeler.  
  
|Komut|Menü|Kısayol|Açıklama|  
|-------------|----------|--------------|-----------------|  
|**Uygulama bildirimi**|**Dosya, yeni**||Yeni bir uygulama bildirimi oluşturur.|  
|**Dağıtım bildirimi**|**Dosya, yeni**||Yeni bir dağıtım bildirimi oluşturur.|  
|**Açık**|**Dosya**|CTRL+O|Varolan bir dağıtım bildirimini, uygulama bildirimini ya da düzenlemek için güven lisansını açar.|  
|**Kapat**|**Dosya**|CTRL+F4|Açık bir dosyayı kapatır.<br /><br /> Bir dosyayı kapatmadan önce değiştirirseniz, MageUI.exe dosyayı bir ortak anahtarla, anahtar çiftiyle veya depolanmış bir sertifikayla yeniden imzalamanızı ister.|  
|**Kaydet**|**Dosya**|CTRL+S|Şu anda kullanıcı giriş odağı olan belgeyi diske kaydeder.|  
|**Farklı Kaydet**|**Dosya**||Yeni bir dosya adı ve/veya konum girmenizi sağlayarak bir dosyayı diske kaydeder.|  
|**Tümünü Kaydet**|**Dosya**||MageUI.exe içinde açık durumdaki tüm dosyalarda yapılan değişiklikleri kaydeder.|  
|**Tercihleri**|**Dosya**||Açılır **Tercihler** iletişim kutusu. Daha fazla bilgi için aşağıdaki bölüme bakın.|  
|**Çıkış**|**Dosya**|ALT+F4|MageUI.exe'den çıkılır.|  
|**Kes**|**Düzenle**|CTRL+X|Seçili durumdaki metni uygulamadan kaldırır ve sistem Pano'suna taşır.|  
|**Kopyala**|**Düzenle**|CTRL+C|Seçili durumdaki metni sistem Pano'suna kopyalar.|  
|**Yapıştır**|**Düzenle**|CTRL+V|Sistem Pano'sundaki metni etkin durumdaki metin öğesinin içine yapıştırır.|  
|**Sil**|**Düzenle**||Şu anda bir güven lisans gibi bir listesinde seçili öğenin siler **dağıtım bildirimi** sekmesi.|  
|**Tümünü Kapat**|**Pencere**||MageUI.exe'de açık durumdaki tüm dosyaları kapatır. Bir veya daha fazla dosyanın kaydedilmesi gerekiyorsa, gereksinimi MageUI.exe sizden onları kaydetmenizi ister. MageUI.exe ayrıca imzalanmamış veya değiştirilmiş her dosya için bir imzalama anahtarı seçmenizi de ister.|  
|**Hakkında**|**Yardım**||MageUI.exe'nin sürüm ve telif hakkı bilgilerini görüntüler.|  
  
## <a name="preferences-dialog-box"></a>Tercihler İletişim Kutusu  
 **Tercihler** iletişim kutusu aşağıdaki öğeleri içerir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Oturum kaydederken**|Bir dosyadaki değişikliklerinizi kaydedeceğiniz her zaman dosyayı imzalamanızı ister.|  
|**İmzalama sertifikası varsayılan kullanın**|Girilen anahtar kullanan **sertifika dosyası** tüm dosyalarını imzalamak için metin kutusu. Bu komut isteminde bir dosyayı kaydettiğinizde, genellikle görünen imzalama ortadan kaldırır ve **oturum kaydederken** seçilir. Üç nokta kullanın (**...** ) düğmesine **sertifika dosyası** metin kutusuna bir anahtar dosyası seçin.|  
|Özet algoritması|Bağımlılık özetlerinin oluşturması için kullanılan algoritmayı belirtir. Değer "sha256RSA" veya "sha1RSA" olmalıdır. Varsayılan olarak SHA1 kullanılır. Hem uygulama hem de dağıtım bildirimlerinde kullanılır. Kullanıcı bildirimi kaydederken bir sertifika sunarsa, bağımlılık özetleri oluşturmak için sertifikadaki algoritmaları kullanır.|  
  
## <a name="signing-options-dialog-box"></a>İmzalama Seçenekleri İletişim Kutusu  
 **İmzalama seçenekleri** ilk kez bir bildirim veya güven lisans kaydettiğinizde ya da bir bildirim veya güven lisans değiştirdiğinizde iletişim kutusu görüntülenir. Varsa yalnızca görünür **oturum kaydederken** seçeneğini **Tercihler** iletişim kutusu seçilidir. Internet'e bir değer belirten bir bildirim imzalarken bağlanmalıdır **zaman damgası URI** metin kutusu.  
  
 Bu iletişim kutusu aşağıdaki öğeleri içerir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Sertifika dosyasını ile oturum açın**|Bildirimi, dosya sisteminde depolanmış bir dijital sertifika ile imzalar.|  
|**Dosya**|Sertifikayı temsil eden .pfx dosyasının yolunu yazmanız için bir alan sağlar.|  
|**...**|Açılır bir **Dosya Seç** var olan bir .pfx dosyasını seçmek için iletişim kutusu.|  
|**Yeni**|Bir Sertifika Yetkilisi (CA) aracılığıyla doğrulanamayan yeni bir .pfx oluşturur. İmzalama için kullanılan sertifikaları türleri hakkında daha fazla bilgi için [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] dağıtımları bkz [güvenilir uygulama dağıtımına genel bakış](/visualstudio/deployment/trusted-application-deployment-overview).|  
|**Parola**|Bu sertifikayla imzalamak için kullanılan parolayı yazmanız için bir alan sağlar. Parola yoksa boş bırakılabilir.|  
|**Depolanan bir sertifika ile oturum açın**|Bilgisayarınızın sertifika deposunda depolanmış dijital sertifikaların seçilebilir bir listesini görüntüler.|  
|**Zaman damgası URI**|Dijital zaman damgası hizmeti Tekdüzen Kaynak Konumlandırıcı'yı (URI) görüntüler. Bildirimlere zaman damgası koymak, uygulamanızın sonraki sürümünü dağıtmadan önce dijital sertifikanızın süresi dolarsa bildirimleri yeniden imzalamanıza gerek kalmamasını sağlar. Daha fazla bilgi için bkz: [Windows kök sertifika programı üyeleri](http://go.microsoft.com/fwlink/?LinkId=159000) ve [ClickOnce ve Authenticode](/visualstudio/deployment/clickonce-and-authenticode).|  
|**Oturum yok**|Dijital bir sertifikanın imza eklemeden bildirim kaydetmenize izin verir.|  
  
## <a name="tab-and-panel-descriptions"></a>Sekme ve Panel Açıklamaları  
 MageUI.exe ile bir belge açtığınızda, kendi sekme sayfasında görünür. Her sekme bir özellik paneli kümesi içerir. Paneller belgenin verilerinin gruplandırılmış alt kümelerini içerir.  
  
### <a name="application-manifest-tab"></a>Uygulama bildirim sekmesi  
 **Uygulama bildirimi** sekmesi, bir uygulama bildirimi içeriğini görüntüler. Uygulama bildirimini dağıtımla dahil tüm dosyaları ve uygulamanın istemci üzerinde çalıştırmak gereken izinleri açıklar.  
  
 **Uygulama bildirimi** sekmesinde aşağıdaki sekmeleri içerir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Ad**|Bu dağıtım hakkında tanımlayıcı bilgileri belirtir.|  
|**Açıklama**|Yayımcı, ürün ve Destek belirten bilgi.|  
|**Uygulama Seçenekleri**|Bu tarayıcı uygulaması olduğunu ve bu bildirim güven bilgilerin kaynağına ait olup olmadığını belirtir.|  
|**Dosyaları**|Bu dağıtım oluşturan dosyaların tamamını belirtir.|  
|**Gerekli izinler**|Uygulamayı bir istemci üzerinde çalıştırmak için gerekli minimum izin kümesi belirtir.|  
  
### <a name="name-tab"></a>Adı sekmesi  
 **Adı** ilk oluşturduğunuzda veya bir uygulama bildirimi açın sekmesi görüntülenir. Dağıtım benzersiz olarak tanımlayan ve isteğe bağlı olarak geçerli bir hedef platformu belirtir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Ad**|Gerekli. Uygulama bildirimini adı. Genellikle aynı dosya adı.|  
|**Sürüm**|Gerekli. Formda dağıtımın sürüm numarası *N.N.N.N*. Yalnızca ilk ana yapı numarası gereklidir. Örneğin, bir uygulamanın sürümü için 1.0, geçerli değerler arasında `1`, `1.0`, `1.0.0`, ve `1.0.0.0`.|  
|**İşlemci**|İsteğe bağlı. Bu dağıtım çalıştırılabileceği makine mimarisi. Varsayılan değer `msil`, ya da tüm yönetilen derlemeler varsayılan biçimi olan Microsoft Ara dile,. Bu alan, uygulamanızda belirli bir mimari için önceden derlenmiş derlemeler değiştirin. Ön derleme hakkında daha fazla bilgi için bkz: [Ngen.exe (yerel Görüntü Oluşturucu)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).|  
|**Kültür**|İsteğe bağlı. Bu uygulamanın çalıştığı iki parçalı ISO ülke ve bölgeye kodu. Varsayılan, `neutral` değeridir.|  
|**Ortak anahtar belirteci**|İsteğe bağlı. Bu uygulama bildirimi ile imzalanmış ortak anahtarı. Bu yeni ya da imzasız bildirim ise, bu alan olarak görünür `Unsigned`.|  
  
### <a name="description-tab"></a>Açıklama sekmesi  
 Bu bilgileri genellikle dağıtım bildirimi içinde sağlanır. Bu alanlar yalnızca ise değiştirilebilir **uygulama bildirimi güven bilgilerini kullan** onay kutusunun seçili **uygulama seçenekleri** sekmesi.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Yayımcı**|Kişinin veya kuruluşun uygulamadan sorumlu adı. Bu değer Başlat menüsü klasör adı olarak kullanılır.|  
|**Ürün**|Tam ürün adı. Seçtiyseniz **yerel olarak yüklemek** için **uygulama türü** öğede **dağıtım seçenekleri** dağıtım bildirimi, bu ad sekmesinde görünür ne olur **Başlat** menü bağlantısı ve **Program Ekle veya Kaldır** bu uygulama için.|  
|**Destek konumu**|Müşteriler elde edebilirsiniz URL yardımcı olmak ve uygulama için destek.|  
  
### <a name="application-options-tab"></a>Uygulama Seçenekleri sekmesi  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Windows Presentation Foundation tarayıcı uygulaması**|Bu tarayıcıda XAML tarayıcısı uygulaması (XBAP) çalışan bir WPF uygulaması olup olmadığını belirtir.|  
|**Uygulama bildirimi güven bilgilerini kullanın**|Bu bildirimi güven bilgileri içerip içermediğini belirtir.|  
  
### <a name="files-tab"></a>Dosyalar sekmesi  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Uygulama dizini**|Uygulamanın dosyaların bulunduğu dizini. Üç nokta kullanın (**...** ) düğmesine tıklayarak dizini seçin.|  
|**Doldurma**|Uygulama bildirimine uygulama dizini ve alt dizinleri tüm dosyaları ekler. MageUI.exe dizinde tek bir yürütülebilir dosya bulursa, onu otomatik olarak bu istemcide ClickOnce uygulaması başlatıldığında ilk yürütülebilir dosya giriş noktası olarak işaretler.|  
|**Uygulama dosyaları**|Tüm uygulama dosyalarını listeler. Her dosyanın aşağıda açıklanan üç düzenlenebilir özniteliği vardır.|  
|**Dosya türü**|Dosya türü dört değerlerden biri olabilir:<br /><br /> -Yok.<br />-Giriş noktası. Uygulamanın birincil yürütülebilir. Yalnızca bir yürütülebilir dosya giriş noktası olarak işaretlenebilir.<br />-Veri dosyası. Uygulama veri sağlayan bir XML dosyası gibi bir dosya.<br />-Simge dosyası. Bir uygulama simgesi, masaüstünde veya bir uygulamanın penceresinde köşesindeki gibi görünür.|  
|**Optional**|İsteğe bağlı olarak işaretlenmiş dosyaları ilk yükleme veya güncelleştirme yüklenmez ancak System.Deployment'a isteğe bağlı API kullanarak çalışma zamanında indirilebilir. Daha fazla bilgi için bkz: [izlenecek yol: ClickOnce dağıtım API'sini kullanarak Tasarımcısı ile isteğe bağlı derlemeleri indirme](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer).|  
|**Grup**|İsteğe bağlı dosyalar kümesi için bir etiket. Grup etiketi bir dosya kümesine uygulamak ve bir toplu tek bir API çağrısı ile dosyaları indirmek için isteğe bağlı API kullanın.|  
  
### <a name="permissions-required-tab"></a>İzinler gerekli sekmesi  
 Kullanım **gerekli izinler** uygulamanızı yerel bilgisayarda varsayılan olarak verilir daha fazla erişimi vermeniz gerekiyorsa sekmesinde. Daha fazla bilgi için bkz: [ClickOnce uygulamalarının güvenliğini sağlama](/visualstudio/deployment/securing-clickonce-applications).  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Tür izni Ayarla**|Bu uygulamanın istemci üzerinde çalıştırmak için gerekli minimum izin kümesi. Bu izin kümeleri açıklaması ve yapın veya talep değil, hangi izinlerin [NIB: adlı izni ayarlar](http://msdn.microsoft.com/en-us/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).|  
|**Ayrıntıları**|İzni temsil etmek için uygulama bildirimi için oluşturulan XML ayarlayın. Uygulama bildiriminin XML biçimi iyi anlamış olmanız sürece, bu XML el ile düzenleme yapmamanız gerekir. Daha fazla bilgi için bkz: [ClickOnce Uygulama bildirimi](/visualstudio/deployment/clickonce-application-manifest).|  
  
### <a name="deployment-manifest-tab"></a>Dağıtım bildirim sekmesi  
 **Dağıtım bildirimi** sekmesinde aşağıdaki sekmeleri içerir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Ad**|Bu dağıtım hakkında tanımlayıcı bilgileri belirtir.|  
|**Açıklama**|Yayımcı, ürün ve Destek belirten bilgi.|  
|**Dağıtım seçenekleri**|Uygulama türü ve başlangıç konumu gibi dağıtım hakkında ayrıntılı bilgileri belirtir.|  
|**Güncelleştirme Seçenekleri**|Ne sıklıkta belirtir [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] uygulama güncelleştirmelerini denetlemeniz gerekir.|  
|**Uygulama başvurusu**|Bu dağıtım için uygulama bildirimini belirtir.|  
  
### <a name="name-tab"></a>Adı sekmesi  
 **Adı** ilk oluşturduğunuzda veya bir dağıtım bildirimini açın sekmesi görüntülenir. Dağıtım benzersiz olarak tanımlayan ve isteğe bağlı olarak geçerli bir hedef platformu belirtir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Ad**|Gerekli. Dağıtım bildiriminin adı. Genellikle aynı dosya adı.|  
|**Sürüm**|Gerekli. Formda dağıtımın sürüm numarası *N.N.N.N*. Yalnızca ilk ana yapı numarası gereklidir. Örneğin, bir uygulamanın sürümü için 1.0, geçerli değerler arasında `1`, `1.0`, `1.0.0`, ve `1.0.0.0`.|  
|**İşlemci**|İsteğe bağlı. Bu dağıtım çalıştırılabileceği makine mimarisi. Varsayılan değer `msil`, ya da Microsoft Ara dile, tüm yönetilen derlemeler varsayılan biçimi. Bu alan, belirli bir mimari için uygulamanızda derlemeleri derlediğiniz tıklarsanız.|  
|**Kültür**|İsteğe bağlı. Bu uygulamanın çalıştığı iki parçalı ISO ülke/bölge kodu. Varsayılan, `neutral` değeridir.|  
|**Ortak anahtar belirteci**|İsteğe bağlı. Bu dağıtım bildirimi ile imzalanmış ortak anahtarı. Bu yeni ya da imzasız bildirim ise, bu alan olarak görünür `Unsigned`.|  
  
### <a name="description-tab"></a>Açıklama sekmesi  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Yayımcı**|Gerekli. Kişinin veya kuruluşun uygulamadan sorumlu adı. Bu değer Başlat menüsü klasör adı olarak kullanılır.|  
|**Ürün**|Gerekli. Tam ürün adı. Seçtiyseniz **yerel olarak yüklemek** için **uygulama türü** öğede **dağıtım seçenekleri** sekmesinde, bu adı ne görünür olacaktır **Başlat** menü bağlantısı ve **Program Ekle veya Kaldır** bu uygulama için.|  
|**Destek konumu**|İsteğe bağlı. Müşteriler elde edebilirsiniz URL yardımcı olmak ve uygulama için destek.|  
  
### <a name="deployment-options-tab"></a>Dağıtım Seçenekleri sekmesi  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Uygulama türü**|İsteğe bağlı. Bu uygulama kendisini istemci bilgisayara yükler olup olmadığını belirtir (**yerel olarak yüklemek**), çevrimiçi çalışır (**yalnızca çevrimiçi**), veya tarayıcıda çalışan bir WPF uygulaması (**WPF tarayıcı Uygulama**). Varsayılan değer **yerel olarak yüklemek**.|  
|**Başlangıç konumu**|İsteğe bağlı. Hangi uygulamanın gerçekten başlatılması gereken URL'si. Uygulamanın kendisi Web'den güncelleştirmelidir bir CD'den dağıtırken kullanışlıdır.|  
|**Başlangıç konumu (ProviderURL) bildiriminde içerir**|İsteğe bağlı. URL'yi belirtir, [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] uygulama güncelleştirmelerini inceleyeceksiniz.|  
|**Yükledikten sonra otomatik olarak Çalıştırma uygulaması**|Gerekli. Belirleyen [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] uygulama, ilk yüklemenin hemen sonrasında bir URL'den çalışmalı. Onay kutusu seçili varsayılandır.|  
|**Uygulamaya geçirilecek URL parametreleri izin ver**|Gerekli. Parametre veri aktarımını verir [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] dağıtım bildirim URL'ye eklenen sorgu dizesi aracılığıyla uygulama. Onay kutusu işaretli varsayılandır.|  
|**.Deploy dosya uzantısını kullanın**|Gerekli. Seçili olduğunda, uygulama bildiriminde tüm dosyalar .deploy uzantısına sahip olmalıdır. Onay kutusu işaretli varsayılandır.|  
  
### <a name="update-options-tab"></a>Seçenekler sekmesinde güncelleştirme  
 **Güncelleştirme Seçenekleri** sekmesi yalnızca seçenekleri içerir zaman burada sözü edilen **uygulama türü** seçim kutusunu **adı** sekmesini ayarlanmış **yerel olarak yükle** .  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Bu uygulama güncelleştirmeleri denetleyeceğini**|Belirtir olup olmadığını [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] uygulama güncelleştirmelerini denetlemeniz gerekir. Bu onay kutusu seçili değilse, bu program aracılığıyla API'leri kullanarak güncelleştirme sürece uygulama güncelleştirmeleri denetlemez <xref:System.Deployment.Application> ad alanı.|  
|**Uygulama güncelleştirmeleri denetleyeceğini seçin**|Güncelleştirme denetimleri için iki seçenek sunar:<br /><br /> -   **Uygulama başlatılmadan önce**. Uygulamanın yürütülmesini önce güncelleştirme denetimi gerçekleştirilir.<br />-   **Uygulama başlatıldıktan sonra**. Güncelleştirme denetimi, uygulamanın ana form başlatıldı ve uygulamayı bir sonraki başlatılışında çalışır sonra başlar.|  
|**Güncelleştirme denetimi sıklığı**|Ne sıklıkta belirler [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] Güncelleştirmeleri denetle:<br /><br /> -   **Uygulama her çalıştığında denetleyin**. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]Kullanıcı uygulamayı açar her zaman bir güncelleştirme denetimi gerçekleştirir.<br />-   **Denetleme her**: bir zaman aralığı ve güncelleştirmeleri denetlemeden önce geçmesi gereken bir birimi (saat, gün veya hafta) seçin.|  
|**Bu uygulama için gerekli en düşük bir sürüm belirtin**|İsteğe bağlı. Uygulamanızı belirli bir sürümünü daha önceki bir sürümüyle çalışamıyor kullanıcılarınızın gerekli bir yükleme olduğunu belirtir.|  
|**Sürüm**|Gerekli olursa **bu uygulama için gerekli en düşük bir sürüm belirtin** onay kutusu seçilidir. Sağlanan sürüm numarası biçiminde olmalıdır *N.N.N.N*. Yalnızca ilk ana yapı numarası gereklidir. Örneğin, bir uygulamanın sürümü için 1.0, geçerli değerler arasında `1`, `1.0`, `1.0.0`, ve `1.0.0.0`.|  
  
### <a name="application-reference-tab"></a>Uygulama başvuru sekmesi  
 **Uygulama başvurusu** sekmesi içerir aynı alanları **adı** bu konunun önceki bölümlerinde açıklanan sekmesi. Aşağıdaki alan işlemdir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Bildirim seçin**|Uygulama bildirimini seçmenize olanak sağlar. Bir uygulama bildirimi seçtiğinizde, bu sayfada diğer alanların tümünü doldurur.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)  
 [İzlenecek yol: ClickOnce Uygulamasını El ile Dağıtma](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)  
 [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)
