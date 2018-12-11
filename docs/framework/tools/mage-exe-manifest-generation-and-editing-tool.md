---
title: Mage.exe (Bildirim Üretme ve Düzenleme Aracı)
ms.date: 12/06/2018
helpviewer_keywords:
- Manifest Generation and Editing tool
- Mage.exe
ms.assetid: 77dfe576-2962-407e-af13-82255df725a1
ms.openlocfilehash: 86aec7bbdc7b57b43e9b547aabd36f808d84d05e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53146202"
---
# <a name="mageexe-manifest-generation-and-editing-tool"></a>Mage.exe (Bildirim Üretme ve Düzenleme Aracı)

Bildirim oluşturma ve düzenleme aracı (*Mage.exe*) oluşturma ve düzenleme uygulama ve dağıtım bildirimlerini destekleyen bir komut satırı aracıdır. Bir komut satırı aracı olarak *Mage.exe* hem toplu betiklerden hem de dahil diğer Windows tabanlı uygulamalardan çalıştırılabilir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] uygulamalar.

Ayrıca *MageUI.exe*, bir grafik uygulaması yerine *Mage.exe*. Daha fazla bilgi için [MageUI.exe (bildirim üretme ve düzenleme aracı, grafik istemci)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için Visual Studio için geliştirici Komut İstemi'ni kullanın. Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

İki sürümünü *Mage.exe* ve *MageUI.exe* Visual Studio'ya dahildir. Sürüm bilgileri görmek için şunu çalıştırın *MageUI.exe*seçin **yardımcı**seçip **hakkında**. Bu belge 4.0.x.x sürümünü açıklar *Mage.exe* ve *MageUI.exe*.

## <a name="syntax"></a>Sözdizimi

```console
Mage [commands] [commandOptions]
```

### <a name="parameters"></a>Parametreler

Aşağıdaki tablo tarafından desteklenen komutları gösterir *Mage.exe*. Bu komutlar tarafından desteklenen seçenekleri hakkında daha fazla bilgi için bkz. [New ve Update komut seçenekleri](#new-and-update-command-options) ve [oturum komut seçenekleri](#sign-command-options).

|Komut|Açıklama|
|-------------|-----------------|
|**-cc, ClearApplicationCache**|Tüm yalnızca çevrimiçi uygulamalar için indirilen uygulama önbelleğini temizler.|
|**-n, - yeni** *fileType [newOptions]*|Belirtilen türde yeni bir dosya oluşturur. Geçerli türler şunlardır:<br /><br /> -   `Deployment`: Yeni bir dağıtım bildirimi oluşturur.<br />-   `Application`: Yeni bir uygulama bildirimi oluşturur.<br /><br /> Eğer bu komutla birlikte hiçbir ek parametre belirtmezseniz, uygun türde ve uygun varsayılan etiketlere ve öznitelik değerlerine sahip bir dosya oluşturur.<br /><br /> Kullanım **- ToFile** seçeneğini (aşağıdaki tabloya bakın) yeni dosya yolunu ve dosya adını belirtmek için.<br /><br /> Kullanım **- FromDirectory** seçeneğini (aşağıdaki tabloya bakın) tüm derlemelerin eklenen bir uygulama için bir uygulama bildirimi oluşturmak için \<bağımlılık > bölümüne bildirim.|
|**-u,-güncelleştirme** *[filePath] [updateOptions]*|Bir bildirim dosyasına bir veya daha fazla değişiklik yapar. Düzenlediğiniz dosya türünü belirtmeniz gerekli değildir. Mage.exe, bir buluşsal yöntem kümesi kullanarak dosyayı inceler ve bir dağıtım bildirimi ya da uygulama bildirimi olup olmadığını belirler.<br /><br /> Bir dosyayı bir sertifika ile imzaladıysanız **-güncelleştirme** anahtar imzası bloğunu kaldırır. Bunun nedeni, anahtar imzasının dosyasının bir karmasını içermesi ve dosyayı değiştirmenin karmayı geçersiz kılmasıdır.<br /><br /> Kullanım **- ToFile** seçeneğini (aşağıdaki tabloya bakın) yeni dosya adı ve yolu varolan dosyanın üzerine yazmak yerine belirtmek için.|
|**-s-oturum** `[signOptions]`|Bir dosyayı imzalamak için bir anahtar çifti veya X509 sertifikası kullanır. İmzalar, dosyaların içine XML öğeleri olarak eklenir.<br /><br /> Belirten bir bildirimi imzalarken Internet'e gereken bir **- TimestampUri** değeri.|
|**-ver'dir;-doğrulayın** *[filename bildirimi]*|Bildirim doğru şekilde imzalanmış doğrular. Diğer komutları ile birleştirilemez. <br/><br/>**.NET Framework 4.7 ve sonraki sürümlerinde kullanılabilir.**|
|**-h-?, - yardımcı** *[ayrıntılı]*|Tüm kullanılabilir komutları ve seçeneklerini açıklar. Belirtin `verbose` ayrıntılı yardım almak için.|

## <a name="new-and-update-command-options"></a>Yeni ve Update komutu seçenekleri

Aşağıdaki tablo tarafından desteklenen seçenekleri gösterir `-New` ve `-Update` komutları:

|Seçenekler|Varsayılan Değer|Uygulandığı öğe:|Açıklama|
|-------------|-------------------|----------------|-----------------|
|**-bir,-algoritması**|sha1RSA|Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Bağımlılık özetlerinin oluşturması için kullanılan algoritmayı belirtir. Değer "sha256RSA" veya "sha1RSA" olmalıdır.<br /><br /> "-Update" seçeneğiyle kullanın. Bu seçenek "-Sign" seçeneğini kullanırken yok sayılır.|
|**-appc, - AppCodeBase** `manifestReference`||Dağıtım bildirimleri.|Uygulama bildirim dosyasına bir URL veya dosya yolu başvurusu ekler. Bu değer, uygulama bildiriminin tam yolu olmalıdır.|
|**-appm, - AppManifest** `manifestPath`||Dağıtım bildirimleri.|Bir dağıtım bildirimine, dağıtımın uygulama bildirimindeki bir başvuruyu ekler.<br /><br /> Tarafından belirtilen dosya `manifestPath` mevcut olmalıdır veya *Mage.exe* bir hata verir. Tarafından başvurulan dosya `manifestPath` bir uygulama bildirimi değil *Mage.exe* bir hata verir.|
|**-cf, - CertFile** `filePath`||Tüm dosya türleri.|X X509 konumunu belirten bir bildirim veya lisans dosyasını imzalamak için dijital sertifika. Bu seçeneği ile birlikte kullanılabilir **-parola** sertifikası kişisel bilgi değişimi (PFX) dosyaları için bir parola gerektiriyorsa seçeneği. Dosya bir birleşimi bir özel anahtar içermiyorsa, .NET Framework 4.7 ile başlayan **- CryptoProvider** ve **- Keycontaıner** seçenekleri gereklidir.<br/><br/>.NET Framework 4.6.2, ile başlayarak *Mage.exe* işaretleri, sertifikaları CAPI yanı sıra CNG bildirimleri.|
|**-ch, - CertHash** `hashSignature`||Tüm dosya türleri.|İstemci bilgisayarın kişisel sertifika deposunda tutulan bir dijital sertifikanın karması. Bu, Windows Sertifikaları Konsolu içinde görüntülenen bir dijital sertifikanın Parmak İzi dizesine karşılık gelir.<br /><br /> `hashSignature` ya da büyük harf veya küçük harf ve tek bir dize olarak veya izinin her sekizliğini boşluk ve tırnak işaretleri arasına parmak ayırarak ve parmak izini sağlanabilir olabilir.|
|**-csp, - CryptoProvider** `provider-name`||Tüm dosya türleri.|Özel anahtar kapsayıcısı içeren şifreleme hizmet sağlayıcısı (CSP) adını belirtir. Bu seçenek gerektirir **- Keycontaıner** seçeneği.<br/><br/>Bu seçenek, .NET Framework 4.7 ile başlayan kullanılabilir.|
|**-fd, - FromDirectory** `directoryPath`||Uygulama bildirimleri.|Tüm derlemeleri ve dosyaları bulunan uygulama bildirimini doldurur `directoryPath`, tüm alt dizinleri dahil olmak üzere burada `directoryPath` dağıtmak istediğiniz uygulamayı içeren dizindir. Dizindeki her dosya için *Mage.exe* dosyanın bir derleme veya statik dosya olup olmadığına karar verir. Eğer bir derleme ise, ekler bir `<dependency>` etiketi ve `installFrom` özniteliği uygulamaya derlemenin adı, kod tabanı ve sürüm. Eğer statik bir dosya ise, ekler bir `<file>` etiketi. *Mage.exe* ayrıca uygulamanın temel yürütülebilir dosyasını algılamak için basit bir buluşsal yöntem kümesi kullanır ve onu bildirimde ClickOnce uygulamasının giriş noktası olarak işaretler.<br /><br /> *Mage.exe* hiçbir zaman otomatik olarak işaretle "veri" dosyası olarak bir dosya olacaktır. Bunu elle yapmanız gerekir. Daha fazla bilgi için [nasıl yapılır: Bir ClickOnce uygulamasına bir veri dosyası dahil etme](/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application).<br /><br /> *Mage.exe* ayrıca boyutuna göre her dosya için bir karma oluşturur. ClickOnce bu karmaları kullanarak, bildirim oluşturulduktan sonra dağıtımın dosyaları üzerinde kimsenin değişiklik yapmadığından emin olur. Dağıtımınızdaki dosyalardan herhangi birini değiştirirseniz, çalıştırabileceğiniz *Mage.exe* ile **-güncelleştirme** komut ve **- FromDirectory** seçeneği ve karmalarını ve derleme güncelleştirir başvurulan tüm dosyaların sürümleri.<br /><br /> **-FromDirectory** içinde bulunan tüm alt dizinlerindeki tüm dosyaları içerir `directoryPath`.<br /><br /> Kullanırsanız **- FromDirectory** ile **-güncelleştirme** komutu *Mage.exe* dizinde artık uygulama bildiriminde dosyaları kaldırır.|
|**-IF, - IconFile**  `filePath`||Uygulama bildirimleri.|Bir .ICO simge dosyasının tam yolunu belirtir. Bu simge başlat menüsünde uygulamanızın adının yanında ve Program Ekle/Kaldır girdisinde görünür. Eğer simge sağlanmazsa, varsayılan bir simge kullanılır.|
|**-IP, - IncludeProviderURL**  `url`|true|Dağıtım bildirimleri.|Dağıtım bildirimi ayarlanan güncelleştirme konumunu içerip içermediğini belirten **- ProviderURL**.|
|**-i,-yükleme** `willInstall`|true|Dağıtım bildirimleri.|ClickOnce uygulamasının yerel bilgisayara yüklenip yüklenmeyeceğini veya Web'den çalışıp çalışmayacağını belirtir. Bir uygulamayı yüklemek, bu uygulamayı Windows bulunması verir **Başlat** menüsü. Geçerli değerler "true" veya "t" ve "false" veya "f" değerleridir.<br /><br /> Belirtirseniz **- MinVersion** seçeneği ve bir kullanıcı bir sürümüne sahip küçüktür **- MinVersion** yüklüyse, geçirdiğiniz değerinden bağımsız olarak yüklemek üzere uygulamayı zorlayacak **- Yükleme**.<br /><br /> Bu seçenek kullanılamaz **- BrowserHosted** seçeneği. Aynı bildirimde ikisini de belirtmeyi denemek hata oluşturur.|
|**-kc, - Keycontaıner** `name`||Tüm dosya türleri.|Özel anahtar adını içeren bir anahtar kapsayıcı belirtir. Bu seçenek gerektirir **CyproProvider** seçeneği.<br/><br/>Bu seçenek, .NET Framework 4.7 ile başlayan kullanılabilir.|
|**-mv, - MinVersion**  `[version]`|ClickOnce dağıtım bildirimi tarafından belirtilen sürüm listelenen **-sürüm** bayrağı.|Dağıtım bildirimleri.|Bir kullanıcının çalıştırabileceği bu uygulamanın en düşük sürümü. Bu bayrak uygulamanızın adlandırılmış sürümünü gereken bir güncelleştirme yapar. Eğer ürününüzün bir sürümünü bozucu bir değişiklik veya kritik bir güvenlik açığı için güncelleştirirseniz, bu bayrağı kullanarak bu güncelleştirmenin yüklenmesi gerektiğini ve kullanıcının önceki sürümleri kullanamayacağını belirtebilirsiniz.<br /><br /> `version` bağımsız değişkeni ile aynı semantiğe sahip **-sürüm** bayrağı.|
|**-n, - ad** `nameString`|Dağıt|Tüm dosya türleri.|Uygulamayı tanımlamak için kullanılan ad. ClickOnce, uygulamayı tanımlamak için bu ad kullanacağı **Başlat** (uygulama kendisini yükleyecek şekilde yapılandırılmışsa) menüsünde ve izin yükseltme iletişim kutularında. **Not:**  Varolan bir bildirimi güncelleştiriyorsanız ve bu seçenekle bir yayımcı adı belirtmezseniz, *Mage.exe* bildirimi bilgisayarda tanımlı olan kuruluş adı ile güncelleştirir. Farklı bir ad kullanmak için, bu seçeneği kullanmayı ve istediğiniz yayımcı adını belirtmeyi unutmayın.|
|**-pwd,-parola** `passwd`||Tüm dosya türleri.|Bir bildirimi dijital sertifika ile imzalamak için kullanılan şifre. İle birlikte kullanılmalıdır **- CertFile** seçeneği.|
|**-p, işlemci** `processorValue`|Msil|Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Bu dağıtımın çalışabileceği mikro işlemci mimarisi. Eğer derlemeleri belirli bir mikro işlemci için önceden derlenmiş olan bir veya daha fazla yükleme için hazırlanıyorsanız bu değer gereklidir. Geçerli değerler `msil`, `x86`, `ia64`, ve `amd64`. `msil` Tüm bütünleştirilmiş kodlarınızı platformdan bağımsız ve ortak dil çalışma zamanı (CLR) yalnızca saat olacak anlamına gelir. Ara dil, derleme, bunları, uygulamanız ilk çalıştırma olduğunda Microsoft'tur.|
|**-pu,** **- ProviderURL** `url`||Dağıtım bildirimleri.|ClickOnce'ın uygulama güncelleştirmeleri için inceleyeceği URL'yi belirtir.|
|**-pub,-yayımcı** `publisherName`||Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Dağıtım veya uygulama bildiriminin açıklama öğesine yayımcı adını ekler. Bir uygulama bildiriminde kullanıldığında **- UseManifestForTrust** "true" veya "t" değeriyle de belirtilmesi gerekir aksi halde bu parametre hata oluşturur.|
|**-s, - SupportURL**  `url`||Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|ClickOnce uygulaması için Program Ekle veya Kaldır'da görünen bağlantıyı belirtir.|
|**-Za, - TimestampUri** `uri`||Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Bir dijital zaman damgası hizmetinin URL'si. Bildirimlere zaman damgası koymak, uygulamanızın sonraki sürümünü dağıtmadan önce dijital sertifikanızın süresi dolarsa bildirimleri yeniden imzalamanıza gerek kalmamasını sağlar. Daha fazla bilgi için [Windows kök sertifika programı üyeleri](https://go.microsoft.com/fwlink/?LinkId=159000).|
|**-t, - ToFile** `filePath`|-Yeni:<br />-Dağıtım: deploy.application<br />-Uygulama: application.exe.manifest<br />-Güncelleştirme:<br />-Giriş dosyası.|Tüm dosya türleri.|Oluşturulan veya değiştirilen dosyanın çıkış yolunu belirtir.<br /><br /> Varsa **- ToFile** kullandığınızda sağlanmazsa **-yeni**, çıkış geçerli çalışma dizinine yazılır. Varsa **- ToFile** kullandığınızda sağlanmazsa **-güncelleştirme**, *Mage.exe* dosyayı giriş dosyasına geri yazar.|
|**-tr, - TrustLevel** `level`|Uygulama URL'sinin bulunduğu bölgeyi temel alır.|Uygulama bildirimleri.|İstemci bilgisayarlarda uygulamaya sağlanacak güven düzeyi. Değerler "Internet", "Intranet" ve "FullTrust" değerlerini içerir.|
|**-ümmül, - UseManifestForTrust** `willUseForTrust`|False|Uygulama bildirimleri.|Uygulama bildiriminin dijital imzasının, uygulama istemcide çalışırken güven kararları için kullanılıp kullanılmayacağını belirtir. "true" veya "t" belirtmek uygulama bildiriminin güven kararları için kullanılacağını belirtir. "false" veya "f" belirtmek dağıtım bildiriminin imzasının kullanılacağını belirtir.|
|**-v,-sürüm** `versionNumber`|1.0.0.0|Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Dağıtımın sürümü. Bağımsız değişken geçerli bir sürüm dizesi biçimi olmalıdır "*N.N.N.N*","*N*" imzalanmamış bir 32-bit tamsayı.|
|**-wpf, - WPFBrowserApp**  `isWPFApp`|false|Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Bu bayrağı yalnızca, uygulama Internet Explorer içinde barındırılacak bir Windows Presentation Foundation (WPF) uygulaması ise ve tek başına yürütülebilir dosya değil ise kullanın. Geçerli değerler "true" veya "t" ve "false" veya "f" değerleridir.<br /><br /> Uygulama bildirimleri için ekler `hostInBrowser` altında özniteliği `entryPoint` uygulama bildiriminin öğesi.<br /><br /> Dağıtım bildirimleri için ayarlar `install` özniteliği `deployment` öğesi false ve dağıtım bildirimini bir .xbap uzantısıyla kaydeder. Bu bağımsız değişken ile birlikte belirtme **-yükleme** bağımsız değişkeni, tarayıcıda barındırılan bir uygulama yüklenen, çevrimdışı bir uygulama olamaz çünkü bir hata üretir.|

## <a name="sign-command-options"></a>Sign komut seçenekleri

Aşağıdaki tablo tarafından desteklenen seçenekleri gösterir `-Sign` tüm dosya türleri için geçerli komutu.

|Seçenekler|Açıklama|
|-------------|-----------------|
|**-cf, - CertFile** `filePath`|Bildirim imzalamak için bir dijital sertifikanın konumunu belirtir. Bu seçeneği ile birlikte kullanılabilir **-parola** sertifikası kişisel bilgi değişimi (PFX) dosyaları için bir parola gerektiriyorsa seçeneği. Dosya bir birleşimi bir özel anahtar içermiyorsa, .NET Framework 4.7 ile başlayan **- CryptoProvider** ve **- Keycontaıner** seçenekleri gereklidir.<br/><br/>.NET Framework 4.6.2, ile başlayarak *Mage.exe* işaretleri, sertifikaları CAPI yanı sıra CNG bildirimleri.|
|**-ch, - CertHash** `hashSignature`|İstemci bilgisayarın kişisel sertifika deposunda tutulan bir dijital sertifikanın karması. Bu, Windows Sertifikaları Konsolu içinde görüntülenen bir dijital sertifikanın Parmak İzi özelliğine karşılık gelir.<br /><br /> `hashSignature` ya da büyük harf veya küçük harf ve tek bir dize olarak ya da izinin her sekizliğini boşluk ve tırnak işaretleri arasına parmak ayırarak ve parmak izini sağlanabilir olabilir.|
**-csp, - CryptoProvider** `provider-name`|Özel anahtar kapsayıcısı içeren şifreleme hizmet sağlayıcısı (CSP) adını belirtir. Bu seçenek gerektirir **- Keycontaıner** seçeneği.<br/><br/>Bu seçenek, .NET Framework 4.7 ile başlayan kullanılabilir.|
|**-kc, - Keycontaıner** `name`|Özel anahtar adını içeren bir anahtar kapsayıcı belirtir. Bu seçenek gerektirir **CyproProvider** seçeneği.<br/><br/>Bu seçenek, .NET Framework 4.7 ile başlayan kullanılabilir.|
|**-pwd,-parola** `passwd`|Bir bildirimi dijital sertifika ile imzalamak için kullanılan şifre. İle birlikte kullanılmalıdır **- CertFile** seçeneği.|
|**-t, - ToFile** `filePath`|Oluşturulan veya değiştirilen dosyanın çıkış yolunu belirtir.|

## <a name="remarks"></a>Açıklamalar

Tüm bağımsız değişkenleri *Mage.exe* büyük küçük harf duyarlıdır. Komutlar ve seçenekler bir tire (-) veya eğik çizgi (/) ile belirtilebilir.

Tüm bağımsız değişkenleri ile kullanılan **-oturum** komutu ile herhangi bir zamanda kullanılabilir **-yeni** veya **-güncelleştirme** komutlarıyla da. Aşağıdaki komutlar eşdeğerdir.

```console
mage -Sign c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
```

> [!NOTE]
> .NET Framework 4.6.2 sürümü ile başlayarak, CNG sertifikalarından de desteklenir.

 İmzalama gerçekleştireceğiniz son görevdir; çünkü imzalanmış bir belge, imzanın belge için geçerli olup olmadığını doğrulamak için dosyanın bir karmasını kullanır. Eğer imzalanan dosyada bir değişiklik yaparsanız, yeniden imzalamanız gerekir. Önceden imzalanmış olan bir belgeyi imzalarsanız *Mage.exe* önceki imzayı yenisiyle değiştirir.

 Kullanırken **- AppManifest** bir dağıtım bildirimini doldurmak için seçeneği *Mage.exe* uygulama bildiriminizin dağıtım ile aynı dizinde yer alacağı varsayar bildirim içinde bir alt geçerli dağıtım sürümünün adını ve Dağıtım bildiriminizi uygun şekilde yapılandırın. Uygulama bildiriminizi başka bir yerde bulunuyorsa, kullanın **- AppCodeBase** konumu ayarlamak için seçeneği.

 Uygulamanızı dağıtmadan önce dağıtım ve uygulama belgeleriniz imzalanmalıdır. Bildirimleri imzalama hakkında yönergeler için bkz. [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview).

 **- TrustLevel** seçenek uygulama bildirimleri için uygulamanın gerektirir istemci bilgisayarda çalıştırmak için izin kümesi tanımlar. Varsayılan olarak, uygulamaları temel alan bir güven düzeyi atanır *bölge* URL'LERİNİN bulunduğu. Bir şirket ağında dağıtılan uygulamalar genellikle Intranet bölgesine yerleştirilirken, Internet üzerinden dağıtılan uygulamalar Internet bölgesine yerleştirilir. İki güvenlik bölgesi de uygulamanın yerel kaynaklara erişimine kısıtlamalar koyar, ancak Intranet bölgesi Internet bölgesine göre biraz daha az sınırlayıcıdır. FullTrust bölgesi uygulamalara, bir bilgisayarın yerel kaynakları için tam erişim sağlar. Kullanırsanız **- TrustLevel** bir uygulamayı bu bölgeye yerleştirmek için seçeneğinde, CLR'nin güven yöneticisi bileşeni bu daha yüksek güven düzeyi vermek isteyip istemediğini vermek istemediğini sorar. Eğer uygulamanızı bir şirket ağı üzerinden dağıtıyorsanız, kullanıcıya sormadan uygulamanın güven düzeyini yükseltmek için Güvenilen Uygulama Dağıtımı'nı kullanabilirsiniz.

 Uygulama bildirimleri de özel güven bölümlerini destekler. Bu, uygulamanızın en az izni isteme güvenlik ilkesine uymasına yardımcı olur; çünkü bildirimi, uygulamanın yürütülebilmesi için gereken belirli izinleri isteyecek şekilde yapılandırabilirsiniz. *Mage.exe* doğrudan bir özel güven bölümü eklemeyi desteklemez. Bir metin düzenleyicisi, bir XML Ayrıştırıcısı veya grafik aracını kullanarak bir tane ekleyebilirsiniz *MageUI.exe*. Nasıl kullanılacağı hakkında daha fazla bilgi için *MageUI.exe* özel güven bölümleri eklemek için bkz: [MageUI.exe (bildirim üretme ve düzenleme aracı, grafik istemci)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

Visual Studio 2017 sürümünü 4.6.1 içerir *Mage.exe*. Bu sürümü ile oluşturulan bildirimleri *Mage.exe* hedef .NET Framework 4. .NET Framework'ün eski sürümlerini hedeflemek için önceki bir sürümünü kullanmak *Mage.exe*.

Eklediğinizde veya mevcut bir bildirimden derlemeleri kaldırmak veya varolan bir bildirimi yeniden imzalayın *Mage.exe* bildirimi hedef .NET Framework 4 güncelleştirmez.

Aşağıdaki tablolar bu özellikleri ve kısıtlamaları gösterir:

|Bildirim sürümü|Çalışma|Mage v2.0|Mage v4.0|
|----------------------|---------------|---------------|---------------|
|.NET Framework'ün 2.0 veya 3.x sürümünü hedefleyen uygulamalar için bildirim|Open|Tamam|Tamam|
||Close|Tamam|Tamam|
||Kaydet|Tamam|Tamam|
||Yeniden İmzala|Tamam|Tamam|
||Yeni|Tamam|Desteklenmez|
||Update (aşağıya bakın)|Tamam|Tamam|
|.NET Framework'ün 4 sürümünü hedefleyen uygulamalar için bildirim|Open|Tamam|Tamam|
||Close|Tamam|Tamam|
||Kaydet|Tamam|Tamam|
||Yeniden İmzala|Tamam|Tamam|
||Yeni|Desteklenmez|Tamam|
||Update (aşağıya bakın)|Desteklenmez|Tamam|

|Bildirim sürümü|Update İşlemi Ayrıntıları|Mage v2.0|Mage v4.0|
|----------------------|------------------------------|---------------|---------------|
|.NET Framework'ün 2.0 veya 3.x sürümünü hedefleyen uygulamalar için bildirim|Bir derlemeyi değiştir|Tamam|Tamam|
||Bir derleme ekle|Tamam|Tamam|
||Bir derlemeyi kaldır|Tamam|Tamam|
|.NET Framework'ün 4 sürümünü hedefleyen uygulamalar için bildirim|Bir derlemeyi değiştir|Desteklenmez|Tamam|
||Bir derleme ekle|Desteklenmez|Tamam|
||Bir derlemeyi kaldır|Desteklenmez|Tamam|

 Mage.exe hedefleyen yeni bildirimleri oluşturur [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Hedefleyen ClickOnce uygulamaları [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] ikisinde çalıştırabilirsiniz [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] ve .NET Framework 4'ün tam sürümünü. Uygulamanızı .NET Framework 4 tam sürümünü hedeflerse ve üzerinde çalışamazsa [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)], istemci kaldırma `<framework>` bir metin düzenleyicisi ve ve bildirimi yeniden imzalayın kullanarak öğesi.

Bir örnek verilmiştir `<framework>` hedefleyen öğesi [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]:

```xml
<framework targetVersion="4.0" profile="client" supportedRuntime="4.0.20506" />
```

## <a name="examples"></a>Örnekler

Aşağıdaki örnek Mage için kullanıcı arabirimini açar (*MageUI.exe*).

```console
mage
```

Aşağıdaki örnekler varsayılan bir dağıtım bildirimi ve uygulama bildirimi oluşturur. Bu dosyaların hepsi geçerli çalışma dizininde oluşturulur ve sırasıyla deploy.application ve application.exe.manifest olarak adlandırılır.

```console
mage -New Deployment
mage -New Application
```

Aşağıdaki örnek, tüm Derlemelerle ve kaynak dosyaları geçerli dizindeki doldurulan bir uygulama bildirimi oluşturur.

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

Aşağıdaki örnek, tüm Derlemelerle ve kaynak dosyaları geçerli dizin ve işaretleri ile doldurulan bir uygulama bildirimi oluşturur.

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

Aşağıdaki örnek, geçerli çalışma dizinindeki bir dijital sertifika ve özel anahtarı kullanarak varolan bir dağıtım bildirimini imzalar.

```console
mage -Sign deploy.application -CertFile cert.pfx -KeyContainer keyfile.snk -CryptoProvider "Microsoft Enghanced Cryptographic Provider v1.0"
```

## <a name="see-also"></a>Ayrıca bkz.

- [ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)
- [İzlenecek yol: Bir ClickOnce uygulamasını el ile dağıtma](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Güvenilir Uygulama Dağıtımına Genel Bakış](/visualstudio/deployment/trusted-application-deployment-overview)
- [MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, Grafik İstemci)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
- [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)