---
title: Mage.exe (Bildirim Üretme ve Düzenleme Aracı)
ms.date: 12/06/2018
helpviewer_keywords:
- Manifest Generation and Editing tool
- Mage.exe
ms.assetid: 77dfe576-2962-407e-af13-82255df725a1
ms.openlocfilehash: b04fda81ae51462d9e686585de1477b4c9af4b26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180386"
---
# <a name="mageexe-manifest-generation-and-editing-tool"></a>Mage.exe (Bildirim Üretme ve Düzenleme Aracı)

Manifesto Oluşturma ve Düzenleme Aracı *(Mage.exe),* uygulama ve dağıtım bildirimlerinin oluşturulmasını ve düzenlenmesini destekleyen bir komut satırı aracıdır. Komut satırı aracı olarak *Mage.exe,* hem toplu komut dosyalarından hem de ASP.NET uygulamaları da dahil olmak üzere diğer Windows tabanlı uygulamalardan çalıştırılabilir.

Ayrıca *MageUI.exe*kullanabilirsiniz , grafik uygulama, *Mage.exe*yerine . Daha fazla bilgi için [MageUI.exe (Manifesto Oluşturma ve Düzenleme Aracı, Grafik İstemci)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)bakın.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için Visual Studio için Geliştirici Komut Komut Ustem'ini kullanın. Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.

*Mage.exe* ve *MageUI.exe'nin* iki versiyonu Visual Studio'ya dahildir. Sürüm bilgilerini görmek için *MageUI.exe'yi*çalıştırın, **Yardım'ı**seçin ve **Hakkında'yı**seçin. Bu dokümantasyon, *Mage.exe ve MageUI.exe* sürüm 4.0.x açıklar. *MageUI.exe*

## <a name="syntax"></a>Sözdizimi

```console
Mage [commands] [commandOptions]
```

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda *Mage.exe*tarafından desteklenen komutlar gösterilmektedir. Bu komutlar tarafından desteklenen seçenekler hakkında daha fazla bilgi için [Yeni ve Güncelleştir komut seçenekleri](#new-and-update-command-options) ve İşaret komut [seçeneklerine](#sign-command-options)bakın.

|Komut|Açıklama|
|-------------|-----------------|
|**-cc, ClearApplicationÖnbellek**|Tüm yalnızca çevrimiçi uygulamalar için indirilen uygulama önbelleğini temizler.|
|**-n, -Yeni** *fileType [newOptions]*|Belirtilen türde yeni bir dosya oluşturur. Geçerli türler şunlardır:<br /><br /> -   `Deployment`: Yeni bir dağıtım bildirimi oluşturur.<br />-   `Application`: Yeni bir uygulama bildirimi oluşturur.<br /><br /> Eğer bu komutla birlikte hiçbir ek parametre belirtmezseniz, uygun türde ve uygun varsayılan etiketlere ve öznitelik değerlerine sahip bir dosya oluşturur.<br /><br /> Yeni dosyanın dosya adını ve yolunu belirtmek için **-ToFile** seçeneğini (aşağıdaki tabloya bakın) kullanın.<br /><br /> **-FromDirectory** seçeneğini (aşağıdaki tabloya bakın) kullanarak, bildirimin \<bağımlılık> bölümüne eklenen bir uygulama için tüm derlemelerle birlikte bir uygulama bildirimi oluşturun.|
|**-u, -Update** *[filePath] [updateOptions]*|Bir bildirim dosyasına bir veya daha fazla değişiklik yapar. Düzenlediğiniz dosya türünü belirtmeniz gerekli değildir. Mage.exe, bir buluşsal yöntem kümesi kullanarak dosyayı inceler ve bir dağıtım bildirimi ya da uygulama bildirimi olup olmadığını belirler.<br /><br /> Sertifikaiçeren bir dosyayı zaten imzaladıysanız, **-Güncelleştirme** anahtar imza bloğunu kaldırır. Bunun nedeni, anahtar imzasının dosyasının bir karmasını içermesi ve dosyayı değiştirmenin karmayı geçersiz kılmasıdır.<br /><br /> Varolan dosyanın üzerine yazmak yerine yeni bir dosya adı ve yol belirtmek için **-ToFile** seçeneğini (aşağıdaki tabloya bakın) kullanın.|
|**-ler, -İşaret**`[signOptions]`|Bir dosyayı imzalamak için bir anahtar çifti veya X509 sertifikası kullanır. İmzalar, dosyaların içine XML öğeleri olarak eklenir.<br /><br /> **-TimestampUri** değeri belirten bir bildirim imzalarken Internet'e bağlı olmalısınız.|
|**-ver, -Doğrula** *[manifest-filename]*|Bildirimin doğru imzalanmış olduğunu doğrular. Diğer komutlarla birleştirilemez. <br/><br/>**.NET Framework 4.7 ve sonraki sürümlerde mevcuttur.**|
|**-h, -?, -Yardım** *[verbose]*|Tüm kullanılabilir komutları ve seçeneklerini açıklar. Ayrıntılı `verbose` yardım almak için belirtin.|

## <a name="new-and-update-command-options"></a>Yeni ve Güncelleştir komut seçenekleri

Aşağıdaki tabloda, komutlar `-New` tarafından `-Update` desteklenen seçenekler gösterilmektedir:

|Seçenekler|Varsayılan Değer|Uygulanan Öğe|Açıklama|
|-------------|-------------------|----------------|-----------------|
|**-a, -Algoritma**|sha1RSA|Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Bağımlılık özetlerinin oluşturması için kullanılan algoritmayı belirtir. Değer "sha256RSA" veya "sha1RSA" olmalıdır.<br /><br /> "-Update" seçeneğiyle kullanın. Bu seçenek "-Sign" seçeneğini kullanırken yok sayılır.|
|**-appc, -AppCodeBase**`manifestReference`||Dağıtım bildirimleri.|Uygulama bildirim dosyasına bir URL veya dosya yolu başvurusu ekler. Bu değer, uygulama bildiriminin tam yolu olmalıdır.|
|**-appm, -AppManifest**`manifestPath`||Dağıtım bildirimleri.|Bir dağıtım bildirimine, dağıtımın uygulama bildirimindeki bir başvuruyu ekler.<br /><br /> Tarafından `manifestPath` belirtilen dosya var olmalıdır veya *Mage.exe* bir hata yayımlar. Başvurulan `manifestPath` dosya bir uygulama bildirimi değilse, *Mage.exe* bir hata yayımlar.|
|**-cf, -CertFile**`filePath`||Tüm dosya türleri.|Bir bildirim veya lisans dosyasını imzalamak için X509 dijital sertifikanın konumunu belirtir. Sertifika Kişisel Bilgi Alışverişi (PFX) dosyaları için bir parola gerektiriyorsa, bu seçenek **-Parola** seçeneğiyle birlikte kullanılabilir. .NET Framework 4.7 ile başlayarak, dosya özel bir anahtar içermiyorsa, **-CryptoProvider** ve **-KeyContainer** seçeneklerinin bir kombinasyonu gereklidir.<br/><br/>.NET Framework 4.6.2 ile başlayan *Mage.exe* işaretleri CNG ve CAPI sertifikaları ile birlikte ortaya çıkar.|
|**-ch, -CertHash**`hashSignature`||Tüm dosya türleri.|İstemci bilgisayarın kişisel sertifika deposunda tutulan bir dijital sertifikanın karması. Bu, Windows Sertifikaları Konsolu içinde görüntülenen bir dijital sertifikanın Parmak İzi dizesine karşılık gelir.<br /><br /> `hashSignature`büyük veya küçük harfli olabilir ve tek bir dize olarak veya Thumbprint'in her sekizlisi boşluklarla ve tüm Thumbprint'in tırnak işaretleriyle birlikte ayrılmasıyla birlikte sağlanabilir.|
|**-csp, -CryptoProvider**`provider-name`||Tüm dosya türleri.|Özel anahtar kapsayıcısını içeren bir şifreleme hizmet sağlayıcısının (CSP) adını belirtir. Bu seçenek **-KeyContainer** seçeneğini gerektirir.<br/><br/>Bu seçenek .NET Framework 4.7 ile başlayarak kullanılabilir.|
|**-fd, -FromDirectory**`directoryPath`||Uygulama bildirimleri.|Tüm alt dizinler de dahil olmak üzere `directoryPath`bulunan tüm derlemeler ve `directoryPath` dosyaların açıklamaları ile uygulama bildirimini doldurur, dağıtmak istediğiniz uygulamayı içeren dizin nerede. Dizindeki her dosya için *Mage.exe,* dosyanın derleme mi yoksa statik dosya mı olduğuna karar verir. Bir derleme ise, bir `<dependency>` etiket `installFrom` ve derleme adı, kod tabanı ve sürümü ile uygulamaya öznitelik ekler. Statik bir dosyaysa, bir `<file>` etiket ekler. *Mage.exe* ayrıca uygulama için ana yürütülebilir algılamak için sezgisel basit bir dizi kullanır ve bildirimde ClickOnce uygulamagiriş noktası olarak işaretleyecek.<br /><br /> *Mage.exe* hiçbir dosyayı otomatik olarak "veri" dosyası olarak işaretlemez. Bunu elle yapmanız gerekir. Daha fazla bilgi için [bkz: ClickOnce Uygulamasına Veri Dosyası Ekleme](/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application).<br /><br /> *Mage.exe* ayrıca her dosya için boyutuna göre bir karma oluşturur. ClickOnce bu karmaları kullanarak, bildirim oluşturulduktan sonra dağıtımın dosyaları üzerinde kimsenin değişiklik yapmadığından emin olur. Dağıtımınızdaki dosyalardan herhangi biri değişirse, *Mage.exe'yi* **-Update** komutu ve **-FromDirectory** seçeneğiyle çalıştırabilirsiniz ve başvurulan tüm dosyaların iş ve derleme sürümlerini güncelleştirebilirsiniz.<br /><br /> **-FromDirectory** içinde `directoryPath`bulunan tüm alt dizinlerde tüm dosyaları içerecektir.<br /><br /> **-Update** komutu yla **-FromDirectory** kullanıyorsanız, *Mage.exe* uygulama bildiriminde artık dizinde bulunmayan dosyaları kaldırır.|
|**-if, -IconFile**  `filePath`||Uygulama bildirimleri.|Bir .ICO simge dosyasının tam yolunu belirtir. Bu simge başlat menüsünde uygulamanızın adının yanında ve Program Ekle/Kaldır girdisinde görünür. Eğer simge sağlanmazsa, varsayılan bir simge kullanılır.|
|**-ip, -IncludeProviderURL**  `url`|true|Dağıtım bildirimleri.|Dağıtım bildiriminin **-ProviderURL**tarafından ayarlanan güncelleştirme konum değerini içerip içermediğini gösterir.|
|**-i, -Yükle**`willInstall`|true|Dağıtım bildirimleri.|ClickOnce uygulamasının yerel bilgisayara yüklenip yüklenmeyeceğini veya Web'den çalışıp çalışmayacağını belirtir. Bir uygulamayı yüklemek, bu uygulamaya Windows **Başlat** menüsünde bir varlık sağlar. Geçerli değerler "true" veya "t" ve "false" veya "f" değerleridir.<br /><br /> **-MinVersion** seçeneğini belirtirseniz ve bir kullanıcının **-MinVersion** yüklü sürümünden daha az bir sürümü varsa, **-Install'a**geçtiğiniz değerden bağımsız olarak uygulamayı yüklemeye zorlar.<br /><br /> Bu seçenek **-BrowserHosted** seçeneği ile kullanılamaz. Aynı bildirimde ikisini de belirtmeyi denemek hata oluşturur.|
|**-kc, -KeyContainer**`name`||Tüm dosya türleri.|Özel anahtarın adını içeren anahtar kapsayıcısını belirtir. Bu seçenek **CryptoProvider** seçeneğini gerektirir.<br/><br/>Bu seçenek .NET Framework 4.7 ile başlayarak kullanılabilir.|
|**-mv, -MinVersiyon**  `[version]`|ClickOnce dağıtım bildiriminde listelenen sürüm **-Sürüm** bayrağı tarafından belirtilir.|Dağıtım bildirimleri.|Bir kullanıcının çalıştırabileceği bu uygulamanın en düşük sürümü. Bu bayrak uygulamanızın adlandırılmış sürümünü gereken bir güncelleştirme yapar. Eğer ürününüzün bir sürümünü bozucu bir değişiklik veya kritik bir güvenlik açığı için güncelleştirirseniz, bu bayrağı kullanarak bu güncelleştirmenin yüklenmesi gerektiğini ve kullanıcının önceki sürümleri kullanamayacağını belirtebilirsiniz.<br /><br /> `version`**-Sürüm** bayrağının bağımsız değişkeni ile aynı anlambilime sahiptir.|
|**-n, -İsim**`nameString`|Dağıtma|Tüm dosya türleri.|Uygulamayı tanımlamak için kullanılan ad. ClickOnce, **Başlat** menüsündeki (uygulama kendisini yüklemek üzere yapılandırılırsa) ve İzin Yüksekliği iletişim kutularındaki uygulamayı tanımlamak için bu adı kullanır. **Not:**  Varolan bir bildirimi güncelliyorsanız ve bu seçenekle bir yayımcı adı belirtmiyorsanız, *Mage.exe* bildirimi bilgisayarda tanımlanan kuruluş adıyla güncelleştirir. Farklı bir ad kullanmak için, bu seçeneği kullanmayı ve istediğiniz yayımcı adını belirtmeyi unutmayın.|
|**-pwd, -Şifre**`passwd`||Tüm dosya türleri.|Bir bildirimi dijital sertifika ile imzalamak için kullanılan şifre. **-CertFile** seçeneği ile birlikte kullanılmalıdır.|
|**-p, İşlemci**`processorValue`|Msil|Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Bu dağıtımın çalışabileceği mikro işlemci mimarisi. Eğer derlemeleri belirli bir mikro işlemci için önceden derlenmiş olan bir veya daha fazla yükleme için hazırlanıyorsanız bu değer gereklidir. Geçerli değerler `msil` `x86`, `ia64`, `amd64`, ve . `msil`Microsoft ara dilidir, bu da tüm derlemelerinizin platformdan bağımsız olduğu anlamına gelir ve ortak dil çalışma süresi (CLR) uygulamanız ilk çalıştırıldığında bunları tam zamanında derler.|
|**-pu,** **-SağlayıcıURL**`url`||Dağıtım bildirimleri.|ClickOnce'ın uygulama güncelleştirmeleri için inceleyeceği URL'yi belirtir.|
|**-pub, -Yayıncı**`publisherName`||Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Dağıtım veya uygulama bildiriminin açıklama öğesine yayımcı adını ekler. Bir uygulama bildiriminde kullanıldığında, **-UseManifestForTrust** da "true" veya "t" değeriile belirtilmelidir; aksi takdirde, bu parametre bir hata yükseltir.|
|**-ler, -SupportURL**  `url`||Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|ClickOnce uygulaması için Program Ekle veya Kaldır'da görünen bağlantıyı belirtir.|
|**-ti, -TimestampUri**`uri`||Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Bir dijital zaman damgası hizmetinin URL'si. Bildirimlere zaman damgası koymak, uygulamanızın sonraki sürümünü dağıtmadan önce dijital sertifikanızın süresi dolarsa bildirimleri yeniden imzalamanıza gerek kalmamasını sağlar. Daha fazla bilgi için [Windows kök sertifika programı üyelerine](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11))bakın.|
|**-t, -ToFile**`filePath`|- Yeni:<br />- Deployment: deploy.application<br />- Uygulama: application.exe.manifest<br />- Güncelleme:<br />- Giriş dosyası.|Tüm dosya türleri.|Oluşturulan veya değiştirilen dosyanın çıkış yolunu belirtir.<br /><br /> **-ToFile'ı** kullandığınızda sağlanmazsa **-Yeni,** çıktı geçerli çalışma dizinine yazılır. **-ToFile'ı** kullandığınızda sağlanmazsa **-Update**, *Mage.exe* dosyayı giriş dosyasına geri yazar.|
|**-tr, -TrustLevel**`level`|Uygulama URL'sinin bulunduğu bölgeyi temel alır.|Uygulama bildirimleri.|İstemci bilgisayarlarda uygulamaya sağlanacak güven düzeyi. Değerler "Internet", "Intranet" ve "FullTrust" değerlerini içerir.|
|**-um, -UseManifestForTrust**`willUseForTrust`|False|Uygulama bildirimleri.|Uygulama bildiriminin dijital imzasının, uygulama istemcide çalışırken güven kararları için kullanılıp kullanılmayacağını belirtir. "true" veya "t" belirtmek uygulama bildiriminin güven kararları için kullanılacağını belirtir. "false" veya "f" belirtmek dağıtım bildiriminin imzasının kullanılacağını belirtir.|
|**-v, -Sürüm**`versionNumber`|1.0.0.0|Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Dağıtımın sürümü. Bağımsız değişken, "*N.N.N.N*" biçiminin geçerli bir sürüm dizesi olmalıdır, burada "*N*" imzasız 32 bit tamsayıdır.|
|**-wpf, -WPFBrowserApp**  `isWPFApp`|yanlış|Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Bu bayrağı yalnızca, uygulama Internet Explorer içinde barındırılacak bir Windows Presentation Foundation (WPF) uygulaması ise ve tek başına yürütülebilir dosya değil ise kullanın. Geçerli değerler "true" veya "t" ve "false" veya "f" değerleridir.<br /><br /> Uygulama bildirimleri için, özniteliği uygulama `entryPoint` bildiriminin öğesinin altına ekler. `hostInBrowser`<br /><br /> Dağıtım bildirimleri için, `install` `deployment` öğedeki özniteliği yanlış olarak ayarlar ve dağıtım bildirimini .xbap uzantısı ile kaydeder. Tarayıcı tarafından barındırılan bir uygulama yüklü, çevrimdışı bir uygulama olamayacağından, **-Install** bağımsız değişkeni ile birlikte bu bağımsız değişkeni belirtmek bir hata üretir.|

## <a name="sign-command-options"></a>Komut seçeneklerini imzala

Aşağıdaki tablo, tüm dosya türleri `-Sign` için geçerli olan komut tarafından desteklenen seçenekleri gösterir.

|Seçenekler|Açıklama|
|-------------|-----------------|
|**-cf, -CertFile**`filePath`|Bildirim imzalamak için bir dijital sertifikanın konumunu belirtir. Sertifika Kişisel Bilgi Alışverişi (PFX) dosyaları için bir parola gerektiriyorsa, bu seçenek **-Parola** seçeneğiyle birlikte kullanılabilir. .NET Framework 4.7 ile başlayarak, dosya özel bir anahtar içermiyorsa, **-CryptoProvider** ve **-KeyContainer** seçeneklerinin bir kombinasyonu gereklidir.<br/><br/>.NET Framework 4.6.2 ile başlayan *Mage.exe* işaretleri CNG ve CAPI sertifikaları ile birlikte ortaya çıkar.|
|**-ch, -CertHash**`hashSignature`|İstemci bilgisayarın kişisel sertifika deposunda tutulan bir dijital sertifikanın karması. Bu, Windows Sertifikaları Konsolu içinde görüntülenen bir dijital sertifikanın Parmak İzi özelliğine karşılık gelir.<br /><br /> `hashSignature`büyük veya küçük harfli olabilir ve tek bir dize olarak veya boşluklarla ayrılan Parmak İzi'nin her sekizlisi ve tırnak işaretleriyle eklenen tüm Thumbprint ile birlikte sağlanabilir.|
**-csp, -CryptoProvider**`provider-name`|Özel anahtar kapsayıcısını içeren bir şifreleme hizmet sağlayıcısının (CSP) adını belirtir. Bu seçenek **-KeyContainer** seçeneğini gerektirir.<br/><br/>Bu seçenek .NET Framework 4.7 ile başlayarak kullanılabilir.|
|**-kc, -KeyContainer**`name`|Özel anahtarın adını içeren anahtar kapsayıcısını belirtir. Bu seçenek **CryptoProvider** seçeneğini gerektirir.<br/><br/>Bu seçenek .NET Framework 4.7 ile başlayarak kullanılabilir.|
|**-pwd, -Şifre**`passwd`|Bir bildirimi dijital sertifika ile imzalamak için kullanılan şifre. **-CertFile** seçeneği ile birlikte kullanılmalıdır.|
|**-t, -ToFile**`filePath`|Oluşturulan veya değiştirilen dosyanın çıkış yolunu belirtir.|

## <a name="remarks"></a>Açıklamalar

*Mage.exe'deki* tüm argümanlar duyarsız. Komutlar ve seçenekler bir tire (-) veya eğik çizgi (/) ile belirtilebilir.

**-Sign** komutu ile kullanılan tüm bağımsız değişkenler, **-Yeni** **veya-Güncelleştir** komutları ile de herhangi bir zamanda kullanılabilir. Aşağıdaki komutlar eşdeğerdir.

```console
mage -Sign c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
```

> [!NOTE]
> .NET Framework sürümü 4.6.2 ile başlayarak CNG sertifikaları da desteklenir.

 İmzalama gerçekleştireceğiniz son görevdir; çünkü imzalanmış bir belge, imzanın belge için geçerli olup olmadığını doğrulamak için dosyanın bir karmasını kullanır. Eğer imzalanan dosyada bir değişiklik yaparsanız, yeniden imzalamanız gerekir. Daha önce imzalanmış bir belgeyi imzalarsanız, *Mage.exe* eski imzayı yeniyle değiştirir.

 Bir dağıtım bildirimini doldurmak için **-AppManifest** seçeneğini kullandığınızda, *Mage.exe* uygulama bildiriminizin geçerli dağıtım sürümünden sonra bir alt dizinde dağıtım bildirimiyle aynı dizinde yer alacaktır ve dağıtım bildiriminizi uygun şekilde yapılandıracaktır. Uygulama bildiriminiz başka bir yerde kalacaksa, alternatif konumu ayarlamak için **-AppCodeBase** seçeneğini kullanın.

 Uygulamanızı dağıtmadan önce dağıtım ve uygulama belgeleriniz imzalanmalıdır. İmzalama bildirimleri hakkında bilgi için [bkz.](/visualstudio/deployment/trusted-application-deployment-overview)

 -Uygulama bildirimleri için **-TrustLevel** seçeneği, bir uygulamanın istemci bilgisayarda çalıştırılması için gereken izin kümesini açıklar. Varsayılan olarak, uygulamalara URL'lerinin bulunduğu *bölgeye* göre bir güven düzeyi atanır. Bir şirket ağında dağıtılan uygulamalar genellikle Intranet bölgesine yerleştirilirken, Internet üzerinden dağıtılan uygulamalar Internet bölgesine yerleştirilir. İki güvenlik bölgesi de uygulamanın yerel kaynaklara erişimine kısıtlamalar koyar, ancak Intranet bölgesi Internet bölgesine göre biraz daha az sınırlayıcıdır. FullTrust bölgesi uygulamalara, bir bilgisayarın yerel kaynakları için tam erişim sağlar. Bir uygulamayı bu bölgeye yerleştirmek için **-TrustLevel** seçeneğini kullanırsanız, CLR'nin Güven Yöneticisi bileşeni kullanıcıdan bu yüksek düzeyde güven vermek isteyip istemediklerine karar vermesini ister. Eğer uygulamanızı bir şirket ağı üzerinden dağıtıyorsanız, kullanıcıya sormadan uygulamanın güven düzeyini yükseltmek için Güvenilen Uygulama Dağıtımı'nı kullanabilirsiniz.

 Uygulama bildirimleri de özel güven bölümlerini destekler. Bu, uygulamanızın en az izni isteme güvenlik ilkesine uymasına yardımcı olur; çünkü bildirimi, uygulamanın yürütülebilmesi için gereken belirli izinleri isteyecek şekilde yapılandırabilirsiniz. *Mage.exe* doğrudan özel bir güven bölümü eklemeyi desteklemez. Bir metin düzenleyicisi, bir XML ayrıştırıcı veya grafik aracı *MageUI.exe*kullanarak ekleyebilirsiniz. Özel güven bölümleri eklemek için *MageUI.exe'nin* nasıl kullanılacağı hakkında daha fazla bilgi için Bkz. [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

Visual Studio 2017 *Mage.exe*sürümü 4.6.1 içerir. *Mage.exe* target .NET Framework 4'ün bu sürümüyle oluşturulan manifestolar. .NET Framework'ün eski sürümlerini hedeflemek için *Mage.exe'nin*önceki bir sürümünü kullanın.

Derlemeleri varolan bir bildirimden eklediğinizde veya kaldırdığınızda veya varolan bir manifestoyu yeniden imzaladığınızda, *Mage.exe* bildirimi .NET Framework 4'ü hedeflemek üzere güncelleştirmez.

Aşağıdaki tablolarda bu özellikler ve kısıtlamalar göster:

|Bildirim sürümü|İşlem|Mage v2.0|Mage v4.0|
|----------------------|---------------|---------------|---------------|
|.NET Framework'ün 2.0 veya 3.x sürümünü hedefleyen uygulamalar için bildirim|Open|Tamam|Tamam|
||Kapat|Tamam|Tamam|
||Kaydet|Tamam|Tamam|
||Yeniden İmzala|Tamam|Tamam|
||Yeni|Tamam|Desteklenmiyor|
||Update (aşağıya bakın)|Tamam|Tamam|
|.NET Framework'ün 4 sürümünü hedefleyen uygulamalar için bildirim|Open|Tamam|Tamam|
||Kapat|Tamam|Tamam|
||Kaydet|Tamam|Tamam|
||Yeniden İmzala|Tamam|Tamam|
||Yeni|Desteklenmiyor|Tamam|
||Update (aşağıya bakın)|Desteklenmiyor|Tamam|

|Bildirim sürümü|Update İşlemi Ayrıntıları|Mage v2.0|Mage v4.0|
|----------------------|------------------------------|---------------|---------------|
|.NET Framework'ün 2.0 veya 3.x sürümünü hedefleyen uygulamalar için bildirim|Bir derlemeyi değiştir|Tamam|Tamam|
||Bir derleme ekle|Tamam|Tamam|
||Bir derlemeyi kaldır|Tamam|Tamam|
|.NET Framework'ün 4 sürümünü hedefleyen uygulamalar için bildirim|Bir derlemeyi değiştir|Desteklenmiyor|Tamam|
||Bir derleme ekle|Desteklenmiyor|Tamam|
||Bir derlemeyi kaldır|Desteklenmiyor|Tamam|

 Mage.exe ,.NET Framework 4 İstemci Profilini hedefleyen yeni bildirimler oluşturur. .NET Framework 4 İstemci Profilini hedefleyen clickOnce uygulamaları hem .NET Framework 4 İstemci Profili'nde hem de .NET Framework 4'ün tam sürümünde çalıştırılabilir. Uygulamanız .NET Framework 4'ün tam sürümünü hedefliyorsa ve .NET Framework 4 `<framework>` İstemci Profili'nde çalıştırılamıyorsa, bir metin düzenleyicisi kullanarak istemci öğesini kaldırın ve bildirimi yeniden imzalayın.

Aşağıda .NET `<framework>` Framework 4 İstemci Profilini hedefleyen bir örnek öğesi ver:

```xml
<framework targetVersion="4.0" profile="client" supportedRuntime="4.0.20506" />
```

## <a name="examples"></a>Örnekler

Aşağıdaki örnek, Mage *(MageUI.exe)* için kullanıcı arabirimini açar.

```console
mage
```

Aşağıdaki örnekler varsayılan bir dağıtım bildirimi ve uygulama bildirimi oluşturur. Bu dosyaların hepsi geçerli çalışma dizininde oluşturulur ve sırasıyla deploy.application ve application.exe.manifest olarak adlandırılır.

```console
mage -New Deployment
mage -New Application
```

Aşağıdaki örnek, geçerli dizindeki tüm derlemeler ve kaynak dosyalarıyla dolu bir uygulama bildirimi oluşturur.

```console
mage -New Application -FromDirectory . -Version 1.0.0.0
```

Aşağıdaki örnek önceki örneği devam ettirerek dağıtım adımı ve hedef mikro işlemciyi belirtir. Ayrıca ClickOnce'ın güncelleştirmeler için denetleyeceği bir URL belirtir.

```console
mage -New Application -FromDirectory . -Name "Hello, World! Application" -Version 1.0.0.0 -Processor "x86" -ProviderUrl http://internalserver/HelloWorld/
```

Aşağıdaki örnek, Internet Explorer'da barındırılacak bir WPF uygulamasını dağıtmak için bir bildirim çiftinin nasıl oluşturulacağını gösterir.

```console
mage -New Application -FromDirectory . -Version 1.0.0.0 -WPFBrowserApp true
mage -New Deployment -AppManifest 1.0.0.0\application.manifest -WPFBrowserApp true
```

Aşağıdaki örnek, geçerli dizin ve işaretlerden tüm derlemeler ve kaynak dosyalarıyla dolu bir uygulama bildirimi oluşturur.

```console
mage -New Application -FromDirectory . -Version 1.0.0.0 -KeyContainer keypair.snk -CryptoProvider "Microsoft Enhanced Cryptographic Provider v1.0"
```

Aşağıdaki örnek dağıtım bildirimini bir uygulama bildirimindeki bilgiyle güncelleştirir, ve uygulama bildiriminin konumu için kod temelini ayarlar.

```console
mage -Update HelloWorld.deploy -AppManifest 1.0.0.0\application.manifest -AppCodeBase http://internalserver/HelloWorld.deploy
```

Aşağıdaki örnek dağıtım bildirimini düzenleyerek kullanıcının yüklü sürümünün zorla güncelleştirilmesini sağlar.

```console
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -MinVersion 1.1.0.0
```

Aşağıdaki örnek dağıtım bildiriminin uygulama bildirimini ayrı bir dizinden almasını sağlar.

```console
mage -Update HelloWorld.deploy -AppCodeBase http://anotherserver/HelloWorld/1.1.0.0/
```

Aşağıdaki örnek geçerli çalışma dizinindeki bir dijital sertifikayı kullanarak varolan bir dağıtım bildirimini imzalar.

```console
mage -Sign deploy.application -CertFile cert.pfx -Password <passwd>
```

Aşağıdaki örnek, geçerli çalışma dizininde dijital sertifika ve özel anahtar kullanarak varolan bir dağıtım bildirimini imzalar.

```console
mage -Sign deploy.application -CertFile cert.pfx -KeyContainer keyfile.snk -CryptoProvider "Microsoft Enhanced Cryptographic Provider v1.0"
```

## <a name="see-also"></a>Ayrıca bkz.

- [ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)
- [İzlenecek yol: ClickOnce Uygulamasını El ile Dağıtma](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Güvenilir Uygulama Dağıtımına Genel Bakış](/visualstudio/deployment/trusted-application-deployment-overview)
- [MageUI.exe (Bildirim Üretme ve Düzenleme Aracı, Grafik İstemci)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
