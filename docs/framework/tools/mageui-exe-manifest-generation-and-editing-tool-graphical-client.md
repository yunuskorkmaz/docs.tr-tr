---
title: MageUI.exe (Bildirim Üretme ve Düzenleme Aracı, Grafik İstemci)
ms.date: 03/30/2017
helpviewer_keywords:
- Manifest Generation and Editing tool
- MageUI.exe
ms.assetid: f9e130a6-8117-49c4-839c-c988f641dc14
ms.openlocfilehash: 7d09e1283be8ec75df89957e91f0d8411c125b3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74714455"
---
# <a name="mageuiexe-manifest-generation-and-editing-tool-graphical-client"></a>MageUI.exe (Bildirim Üretme ve Düzenleme Aracı, Grafik İstemci)

MageUI.exe, komut satırı aracı Mage.exe ile aynı işlevselliği, ancak Windows tabanlı kullanıcı arabirimi (UI) ile destekler. Bu araçla, dağıtım ve uygulama bildirimleri oluşturabilir, düzenleyebilir ve imzalayabilirsiniz. MageUI.exe hedef .NET Framework 4 İstemci Profili ile oluşturulan yeni manifestolar. Önceki .NET Framework sürümlerini hedeflemek için MageUI.exe'nin önceki sürümleri kullanılmalıdır. Bir bildirimden derlemeler eklerken veya kaldırırken veya varolan bildirimleri yeniden imzalarken, MageUI.exe bildirimi .NET Framework 4 İstemci Profilini hedef almak üzere güncelleştirmez. Daha fazla bilgi için [Mage.exe (Manifest Generation and Düzenleme Aracı)](mage-exe-manifest-generation-and-editing-tool.md)bakın.

 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.

 Mage.exe ve MageUI.exe'nin iki versiyonu Visual Studio'nun bir bileşeni olarak yer almaktadır. Sürüm bilgilerini görmek için MageUI.exe'yi çalıştırın, **Yardım'ı**seçin ve **Hakkında'yı**seçin. Bu belge Mage.exe ve MageUI.exe'nin 4.0.x.x sürümünü açıklar.

> [!NOTE]
> MageUI.exe, MageUI.exe kullanarak bir sertifika ile imzalanmış bir uygulama bildirimini kaydederken [uyumlu Çerçeveler](/visualstudio/deployment/compatibleframeworks-element-clickonce-deployment) öğesini desteklemez. Bunun yerine, [Mage.exe](mage-exe-manifest-generation-and-editing-tool.md)kullanmalısınız.  
  
## <a name="uielement-list"></a>UIElement Listesi  
 Aşağıdaki tablo, kullanılabilen menü ve araç çubuğu öğelerini listeler.  
  
|Komut|Menü|Kısayol|Açıklama|  
|-------------|----------|--------------|-----------------|  
|**Başvuru Bildirimi**|**Dosya, Yeni**||Yeni bir uygulama bildirimi oluşturur.|  
|**Dağıtım Bildirimi**|**Dosya, Yeni**||Yeni bir dağıtım bildirimi oluşturur.|  
|**Aç**|**Dosya**|CTRL+O|Varolan bir dağıtım bildirimini, uygulama bildirimini ya da düzenlemek için güven lisansını açar.|  
|**Kapat**|**Dosya**|CTRL+F4|Açık bir dosyayı kapatır.<br /><br /> Bir dosyayı kapatmadan önce değiştirirseniz, MageUI.exe dosyayı bir ortak anahtarla, anahtar çiftiyle veya depolanmış bir sertifikayla yeniden imzalamanızı ister.|  
|**Kaydet**|**Dosya**|CTRL+S|Şu anda kullanıcı giriş odağı olan belgeyi diske kaydeder.|  
|**Farklı Kaydet**|**Dosya**||Yeni bir dosya adı ve/veya konum girmenizi sağlayarak bir dosyayı diske kaydeder.|  
|**Tümünü Kaydet**|**Dosya**||MageUI.exe içinde açık durumdaki tüm dosyalarda yapılan değişiklikleri kaydeder.|  
|**Tercihler**|**Dosya**||**Tercihler** iletişim kutusunu açar. Daha fazla bilgi için aşağıdaki bölüme bakın.|  
|**Çıkış**|**Dosya**|ALT+F4|MageUI.exe'den çıkılır.|  
|**Kes**|**Düzenle**|CTRL+X|Seçili durumdaki metni uygulamadan kaldırır ve sistem Pano'suna taşır.|  
|**Kopyala**|**Düzenle**|CTRL+C|Seçili durumdaki metni sistem Pano'suna kopyalar.|  
|**Yapıştır**|**Düzenle**|CTRL+V|Sistem Pano'sundaki metni etkin durumdaki metin öğesinin içine yapıştırır.|  
|**Sil**|**Düzenle**||**Dağıtım Bildirimi** sekmesindeki güven lisansı gibi listede şu anda seçili olan bir öğeyi siler.|  
|**Tümünü Kapat**|**Pencere**||MageUI.exe'de açık durumdaki tüm dosyaları kapatır. Bir veya daha fazla dosyanın kaydedilmesi gerekiyorsa, gereksinimi MageUI.exe sizden onları kaydetmenizi ister. MageUI.exe ayrıca imzalanmamış veya değiştirilmiş her dosya için bir imzalama anahtarı seçmenizi de ister.|  
|**Hakkında**|**Yardım**||MageUI.exe'nin sürüm ve telif hakkı bilgilerini görüntüler.|  
  
## <a name="preferences-dialog-box"></a>Tercihler İletişim Kutusu  
 **Tercihler** iletişim kutusu aşağıdaki öğeleri içerir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Kaydedin'de oturum açın**|Bir dosyadaki değişikliklerinizi kaydedeceğiniz her zaman dosyayı imzalamanızı ister.|  
|**Varsayılan imzalama sertifikasını kullanma**|Tüm dosyaları imzalamak için **Sertifika dosyası** metin kutusuna girilen anahtarı kullanır. Bu, bir dosyayı kaydettiğinizde ve **Kaydet'te Oturum Aç** seçildiğinde genellikle görünen imza istemini ortadan kaldırır. Bir anahtar dosyası seçmek için Sertifika **dosyası** metin kutusunun yanındaki elipsis (**...**) düğmesini kullanın.|  
|Özet algoritması|Bağımlılık özetlerinin oluşturması için kullanılan algoritmayı belirtir. Değer "sha256RSA" veya "sha1RSA" olmalıdır. Varsayılan olarak SHA1 kullanılır. Hem uygulama hem de dağıtım bildirimlerinde kullanılır. Kullanıcı bildirimi kaydederken bir sertifika sunarsa, bağımlılık özetleri oluşturmak için sertifikadaki algoritmaları kullanır.|  
  
## <a name="signing-options-dialog-box"></a>İmzalama Seçenekleri İletişim Kutusu  
 **İmzalama Seçenekleri** iletişim kutusu, bir manifesto veya güven lisansını ilk kez kaydettiğinizde veya bir bildirim veya güven lisansını değiştirdiğinizde görüntülenir. Yalnızca **Tercihler** iletişim kutusunda **Kaydet** seçeneği seçilirse görünür. **TimeStamping URI** metin kutusunda bir değer belirten bir bildirim imzalarken Internet'e bağlı olmalısınız.  
  
 Bu iletişim kutusu aşağıdaki öğeleri içerir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Sertifika dosyasıyla imzalama**|Bildirimi, dosya sisteminde depolanmış bir dijital sertifika ile imzalar.|  
|**Dosya**|Sertifikayı temsil eden .pfx dosyasının yolunu yazmanız için bir alan sağlar.|  
|**...**|Varolan bir .pfx dosyayı seçmek için **Dosya** Seç iletişim kutusunu açar.|  
|**Yeni**|Bir Sertifika Yetkilisi (CA) aracılığıyla doğrulanamayan yeni bir .pfx oluşturur. ClickOnce dağıtımlarını imzalamak için kullanılan sertifika türleri hakkında daha fazla bilgi [için](/visualstudio/deployment/trusted-application-deployment-overview)bkz.|  
|**Parola**|Bu sertifikayla imzalamak için kullanılan parolayı yazmanız için bir alan sağlar. Parola yoksa boş bırakılabilir.|  
|**Depolanmış sertifikaile imzalama**|Bilgisayarınızın sertifika deposunda depolanmış dijital sertifikaların seçilebilir bir listesini görüntüler.|  
|**TimeStamping URI**|Dijital zaman damgası hizmeti Tekdüzen Kaynak Konumlandırıcı'yı (URI) görüntüler. Bildirimlere zaman damgası koymak, uygulamanızın sonraki sürümünü dağıtmadan önce dijital sertifikanızın süresi dolarsa bildirimleri yeniden imzalamanıza gerek kalmamasını sağlar. Daha fazla bilgi için [Windows kök sertifika programı üyelerine](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)) ve [ClickOnce ve Authenticode'a](/visualstudio/deployment/clickonce-and-authenticode)bakın.|  
|**İmzalamayın**|Dijital bir sertifikanın imza eklemeden bildirim kaydetmenize izin verir.|  
  
## <a name="tab-and-panel-descriptions"></a>Sekme ve Panel Açıklamaları  
 MageUI.exe ile bir belge açtığınızda, kendi sekme sayfasında görünür. Her sekme bir özellik paneli kümesi içerir. Paneller belgenin verilerinin gruplandırılmış alt kümelerini içerir.  
  
### <a name="application-manifest-tab"></a>Uygulama Bildirimi Sekmesi  
 **Uygulama Bildirimi** sekmesi bir uygulama bildiriminin içeriğini görüntüler. Uygulama bildirimi, dağıtımla birlikte verilen tüm dosyaları ve uygulamanın istemcide çalışması için gereken izinleri açıklar.  
  
 **Uygulama Bildirimi** sekmesi aşağıdaki sekmeleri içerir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Adı**|Bu dağıtımla ilgili bilgileri tanımlar.|  
|**Açıklama**|Yayımcı, ürün ve destek bilgilerini belirtir.|  
|**Uygulama Seçenekleri**|Bunun bir tarayıcı uygulaması olup olmadığını ve bu bildirimin güven bilgilerinin kaynağı olup olmadığını belirtir.|  
|**Dosyaları**|Bu dağıtımı oluşturan tüm dosyaları belirtir.|  
|**Gerekli İzinler**|Uygulamanın istemcide çalışması için gereken minimum izin kümesini belirtir.|  
  
### <a name="name-tab"></a>Ad Sekmesi  
 Bir uygulama bildirimini ilk oluşturduğunuzda veya açtığınızda **Ad** sekmesi görüntülenir. Dağıtımı benzersiz bir şekilde tanımlar ve isteğe bağlı olarak geçerli bir hedef platform belirtir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Adı**|Gereklidir. Uygulama bildiriminin adı. Genellikle dosya adı ile aynıdır.|  
|**Sürüm**|Gereklidir. The version number of the deployment in the form *N.N.N.N*. Yalnızca ilk büyük yapı numarası gereklidir. Örneğin, bir uygulamanın sürüm 1.0 için `1`geçerli `1.0` `1.0.0`değerler `1.0.0.0`, , , ve .|  
|**İşlemci**|İsteğe bağlı. Bu dağıtımın çalıştırılabildiği makine mimarisi. Varsayılan, `msil`yönetilen tüm derlemelerin varsayılan biçimi olan Microsoft Ara Dili'dir. Belirli bir mimari için uygulamanızdaki derlemeleri önceden derlediyseniz bu alanı değiştirin. Ön derleme hakkında daha fazla bilgi için [Ngen.exe (Native Image Generator) (Native Image Generator)](ngen-exe-native-image-generator.md)bakın.|  
|**Kültür**|İsteğe bağlı. Bu uygulamanın çalıştığı iki parçalı ISO ülke ve bölge kodu. Varsayılan değer: `neutral`.|  
|**Ortak anahtar belirteci**|İsteğe bağlı. Bu başvuru bildiriminin imzalandığı ortak anahtar. Bu yeni veya imzalanmamış bir bildirimse, `Unsigned`bu alan .|  
  
### <a name="description-tab"></a>Açıklama Sekmesi  
 Bu bilgiler genellikle dağıtım bildirimi içinde sağlanır. Bu alanlar yalnızca **Uygulama Seçenekleri** sekmesinde Uygulama Bildirimi Güven **Bilgilerini Kullan** onay kutusu seçilirse değiştirilebilir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Yayımcı**|Uygulamadan sorumlu kişi veya kuruluşun adı. Bu değer Başlat menüsü klasör adı olarak kullanılır.|  
|**Ürün**|Tam ürün adı. Dağıtım bildiriminin **Dağıtım Seçenekleri** sekmesinde **Uygulama Türü** öğesi için Yerel Olarak **Yükle'yi** seçtiyseniz, bu ad **Başlat** menüsü bağlantısında ve bu uygulama için Programlar Ekle **veya Kaldır'da** görünen ad olacaktır.|  
|**Destek Konumu**|Müşterilerin uygulama için yardım ve destek alabilecekleri URL.|  
  
### <a name="application-options-tab"></a>Uygulama Seçenekleri Sekmesi  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Windows Sunum Temel Tarayıcı Uygulaması**|Bunun tarayıcıda XAML tarayıcı uygulaması (XBAP) olarak çalışan bir WPF uygulaması olup olmadığını belirtir.|  
|**Uygulama Bildirimi Güven Bilgilerini Kullanma**|Bu bildirimin güven bilgileri içerip içermediğini belirtir.|  
  
### <a name="files-tab"></a>Dosyalar Sekmesi  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Uygulama dizini**|Uygulama dosyalarının bulunduğu dizin. Dizin seçmek için elips (**...**) düğmesini kullanın.|  
|**Doldurmak**|Uygulama dizinindeki tüm dosyaları ve alt dizinleri uygulama bildirimine ekler. MageUI.exe dizinde tek bir yürütülebilir dosya bulursa, bunu otomatik olarak Giriş Noktası olarak işaretler ve bu dosya, ClickOnce uygulaması istemcide başlatıldığında ilk kez yürütülen dosyadır.|  
|**Başvuru Dosyaları**|Uygulamadaki tüm dosyaları listeler. Her dosya, aşağıda tartışılan üç editable öznitelikleri vardır.|  
|**Dosya Türü**|Dosya Türü dört değerden biri olabilir:<br /><br /> - Yok.<br />- Giriş Noktası. Uygulama birincil yürütülebilir. Yalnızca bir yürütülebilir dosya giriş noktası olarak işaretlenebilir.<br />- Veri Dosyası. Uygulamaya veri sağlayan XML dosyası gibi bir dosya.<br />- Simge Dosyası. Masaüstünde veya uygulama penceresinin köşesinde görünen bir uygulama simgesi.|  
|**Isteğe bağlı**|İsteğe bağlı olarak işaretlenen dosyalar ilk yükleme veya güncelleştirmede karşıdan yüklenmez, ancak System.Deployment On-Demand API kullanılarak çalışma zamanında indirilebilir. Daha fazla bilgi için [Bkz. Walkthrough: ClickOnce Dağıtım API'si ile İsteğe Bağlı Derlemeleri İndirme Tasarımcıyı Kullanarak](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer).|  
|**Grup**|İsteğe bağlı dosyalar kümesi için bir etiket. Bir Grup etiketini bir dosya kümesine uygulayabilir ve tek bir API çağrısı içeren bir dosya toplu dosyasını indirmek için İsteğe Bağlı API'yi kullanabilirsiniz.|  
  
### <a name="permissions-required-tab"></a>Gerekli İzinler Sekmesi  
 Uygulamanız varsayılan olarak verilenden daha fazla yerel bilgisayara erişim izni vermek gerekiyorsa **Gerekli İzinler** sekmesini kullanın. Daha fazla bilgi için [ClickOnce Uygulamalarını Güvence Altına Alma'ya](/visualstudio/deployment/securing-clickonce-applications)bakın.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**İzin kümesi türü**|İstemci üzerinde çalışması için bu uygulama tarafından gerekli minimum izin kümesi. Bu izin kümelerinin ve hangi izinleri yaptıklarının veya talep etmedikleri bir açıklama için [Adlandırılmış İzin Kümeleri'ne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100))bakın.|  
|**Şey**|İzin kümesini temsil etmek üzere uygulama bildirimi için oluşturulan XML. Uygulama bildirimi XML biçimini iyi bir şekilde anlamadığınız sürece, bu XML'i el ile delememelisiniz. Daha fazla bilgi için [ClickOnce Uygulama Bildirimi'ne](/visualstudio/deployment/clickonce-application-manifest)bakın.|  
  
### <a name="deployment-manifest-tab"></a>Dağıtım Bildirimi Sekmesi  
 **Dağıtım Bildirimi** sekmesi aşağıdaki sekmeleri içerir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Adı**|Bu dağıtımla ilgili bilgileri tanımlar.|  
|**Açıklama**|Yayımcı, ürün ve destek bilgilerini belirtir.|  
|**Dağıtım Seçenekleri**|Uygulama türü ve başlangıç konumu gibi dağıtım la ilgili ek bilgiler belirtir.|  
|**Güncelleştirme Seçenekleri**|ClickOnce'nin uygulama güncelleştirmelerini ne sıklıkta denetlemesi gerektiğini belirtir.|  
|**Başvuru Başvurusu**|Bu dağıtım için uygulama bildirimini belirtir.|  
  
### <a name="name-tab"></a>Ad Sekmesi  
 Bir dağıtım bildirimini ilk oluşturduğunuzda veya açtığınızda **Ad** sekmesi görüntülenir. Dağıtımı benzersiz bir şekilde tanımlar ve isteğe bağlı olarak geçerli bir hedef platform belirtir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Adı**|Gereklidir. Dağıtım bildiriminin adı. Genellikle dosya adı ile aynıdır.|  
|**Sürüm**|Gereklidir. The version number of the deployment in the form *N.N.N.N*. Yalnızca ilk büyük yapı numarası gereklidir. Örneğin, bir uygulamanın sürüm 1.0 için `1`geçerli `1.0` `1.0.0`değerler `1.0.0.0`, , , ve .|  
|**İşlemci**|İsteğe bağlı. Bu dağıtımın çalıştırılabildiği makine mimarisi. Varsayılan, `msil`yönetilen tüm derlemelerin varsayılan biçimi olan Microsoft Ara Dili'dir. Belirli bir mimari için uygulamanızdaki derlemeleri derlediyseniz bu alanı değiştirin.|  
|**Kültür**|İsteğe bağlı. Bu uygulamanın çalıştığı iki parçalı ISO ülke/bölge kodu. Varsayılan değer: `neutral`.|  
|**Ortak anahtar belirteci**|İsteğe bağlı. Bu dağıtım bildiriminin imzalandığı ortak anahtar. Bu yeni veya imzalanmamış bir bildirimse, `Unsigned`bu alan .|  
  
### <a name="description-tab"></a>Açıklama Sekmesi  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Yayımcı**|Gereklidir. Uygulamadan sorumlu kişi veya kuruluşun adı. Bu değer Başlat menüsü klasör adı olarak kullanılır.|  
|**Ürün**|Gereklidir. Tam ürün adı. **Dağıtım Seçenekleri** sekmesinde **Uygulama Türü** öğesi için Yerel **Olarak Yükle'yi** seçtiyseniz, bu ad **Başlat** menüsü bağlantısında ve bu uygulama için Programlar Ekle **veya Kaldır'da** görünen ad olacaktır.|  
|**Destek Konumu**|İsteğe bağlı. Müşterilerin uygulama için yardım ve destek alabilecekleri URL.|  
  
### <a name="deployment-options-tab"></a>Dağıtım Seçenekleri Sekmesi  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Uygulama Türü**|İsteğe bağlı. Bu uygulamanın kendisini istemci bilgisayara yükleyip yüklemediğini belirtir **(Yerel Olarak Yükle),** çevrimiçi çalışır **(Yalnızca Çevrimiçi**), veya tarayıcıda çalışan bir WPF uygulamasıdır **(WPF Tarayıcı Uygulaması).** Varsayılan, **Yerel olarak yükledir.**|  
|**Başlangıç Konumu**|İsteğe bağlı. Uygulamanın gerçekten başlatılması gereken URL. Web'den kendisini güncelleştirmesi gereken bir CD'den bir uygulama dağıtılırken kullanışlıdır.|  
|**Bildirime Başlangıç Konumu (ProviderURL) ekleme**|İsteğe bağlı. ClickOnce'ın uygulama güncelleştirmeleri için inceleyeceği URL'yi belirtir.|  
|**Yükledikten sonra uygulamayı otomatik olarak çalıştırın**|Gereklidir. ClickOnce uygulamasının ilk yüklemeden hemen sonra bir URL'den çalışması gerektiğini belirtir. Varsayılan onay kutusu seçilir.|  
|**URL parametrelerinin uygulamaya geçirilmesine izin ver**|Gereklidir. Dağıtım bildiriminin URL'sine eklenen bir sorgu dizesi aracılığıyla parametre verilerinin ClickOnce uygulamasına aktarılmasına izin verir. Varsayılan olarak onay kutusu temizlenir.|  
|**.deploy dosya uzantısını kullanma**|Gereklidir. Seçildiğinde, uygulama bildirimindeki tüm dosyaların .deploy uzantısı olmalıdır. Varsayılan olarak onay kutusu temizlenir.|  
  
### <a name="update-options-tab"></a>Seçenekler Sekmesini Güncelleştir  
 **Güncelleştirme Seçenekleri** sekmesi yalnızca **Ad** sekmesindeki **Uygulama Türü** seçim kutusu Yerel **olarak yüklenir'** olarak ayarlandığında burada belirtilen seçenekleri içerir.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Bu uygulama güncelleştirmeleri denetlemek gerekir**|ClickOnce'nin uygulama güncelleştirmelerini denetlemesi gerekip gerekmediğini belirtir. Bu onay kutusu seçili değilse, <xref:System.Deployment.Application> ad alanındaki API'leri kullanarak programlı olarak güncelleştirmediğiniz sürece uygulama güncelleştirmeleri denetlemez.|  
|**Uygulamanın güncelleştirmeleri ne zaman denetlemesi gerektiğini seçin**|Güncelleştirme denetimleri için iki seçenek sağlar:<br /><br /> -   **Uygulama başlamadan önce**. Güncelleştirme denetimi uygulama yürütmeden önce gerçekleştirilir.<br />-   **Uygulama başladıktan sonra**. Güncelleştirme denetimi, uygulamanın ana formu başlatıldıktan sonra başlar ve uygulama bir sonraki başlatılında çalışır.|  
|**Denetim sıklığını güncelleştir**|ClickOnce'nin güncelleştirmeleri ne sıklıkta denetlemesi gerektiğini belirler:<br /><br /> -   **Uygulama her çalıştığında kontrol edin.** ClickOnce, kullanıcı uygulamayı her açtığında bir güncelleştirme denetimi gerçekleştirecektir.<br />-   **Her birini denetleyin**: Güncelleştirmeleri kontrol etmeden önce süresi geçen bir zaman aralığı ve bir birim (saatler, günler veya haftalar) seçin.|  
|**Bu uygulama için gerekli minimum sürümü belirtin**|İsteğe bağlı. Uygulamanızın belirli bir sürümünün, kullanıcılarınızın önceki bir sürümle çalışmasını engelleyen gerekli bir yükleme olduğunu belirtir.|  
|**Sürüm**|Bu uygulama onay kutusu **için gerekli en az sürümü belirtin'in** seçilmesi gerekir. The version number supplied must be of the form *N.N.N.N*. Yalnızca ilk büyük yapı numarası gereklidir. Örneğin, bir uygulamanın sürüm 1.0 için `1`geçerli `1.0` `1.0.0`değerler `1.0.0.0`, , , ve .|  
  
### <a name="application-reference-tab"></a>Başvuru Başvuru Sekmesi  
 **Uygulama Başvurusu** sekmesi, bu konuda daha önce açıklanan **Ad** sekmesiyle aynı alanları içerir. Bir istisna aşağıdaki alandır.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Manifesto'yı Seçin**|Uygulama bildirimini seçmenize olanak tanır. Bir uygulama bildirimi seçtiğinizde, bu sayfadaki diğer tüm alanların doldurulacaktır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)
- [İzlenecek yol: ClickOnce Uygulamasını El ile Dağıtma](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](mage-exe-manifest-generation-and-editing-tool.md)
