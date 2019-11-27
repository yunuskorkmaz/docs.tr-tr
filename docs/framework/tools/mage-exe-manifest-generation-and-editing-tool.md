---
title: Mage.exe (Bildirim Üretme ve Düzenleme Aracı)
ms.date: 12/06/2018
helpviewer_keywords:
- Manifest Generation and Editing tool
- Mage.exe
ms.assetid: 77dfe576-2962-407e-af13-82255df725a1
ms.openlocfilehash: aa2ad9222460f8732397f8b1c72e36085bbe4a21
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449426"
---
# <a name="mageexe-manifest-generation-and-editing-tool"></a>Mage.exe (Bildirim Üretme ve Düzenleme Aracı)

Bildirim Oluşturma ve Düzenleme Aracı (*Mage. exe*), uygulama ve dağıtım bildirimlerinin oluşturulmasını ve düzenlemesini destekleyen bir komut satırı aracıdır. Komut satırı aracı olarak *Mage. exe* , ASP.NET uygulamaları da dahil olmak üzere hem toplu betiklerden hem de diğer Windows tabanlı uygulamalardan çalıştırılabilir.

*Mage. exe*yerine bir grafik uygulama olan *MageUI. exe*' yi de kullanabilirsiniz. Daha fazla bilgi için bkz. [MageUI. exe (bildirim oluşturma ve düzenleme aracı, grafik istemci)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).

Visual Studio 'da *Mage. exe* ve *MageUI. exe* ' nin iki sürümü dahildir. Sürüm bilgilerini görmek için *MageUI. exe*' yi çalıştırın, **Yardım**' ı seçin ve **hakkında**' yı seçin. Bu belgelerde *Mage. exe* ve *MageUI. exe*' nin 4.0. x. x sürümü açıklanmaktadır.

## <a name="syntax"></a>Sözdizimi

```console
Mage [commands] [commandOptions]
```

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda *Mage. exe*tarafından desteklenen komutlar gösterilmektedir. Bu komutlar tarafından desteklenen seçenekler hakkında daha fazla bilgi için, bkz. [yeni ve güncelleştirme komut seçenekleri](#new-and-update-command-options) ve [imza komutu seçenekleri](#sign-command-options).

|Komut|Açıklama|
|-------------|-----------------|
|**-CC, ClearApplicationCache**|Tüm yalnızca çevrimiçi uygulamalar için indirilen uygulama önbelleğini temizler.|
|**-n,-yeni** *filetype [newoptions]*|Belirtilen türde yeni bir dosya oluşturur. Geçerli türler şunlardır:<br /><br /> -   `Deployment`: yeni bir dağıtım bildirimi oluşturur.<br />-   `Application`: yeni bir uygulama bildirimi oluşturur.<br /><br /> Eğer bu komutla birlikte hiçbir ek parametre belirtmezseniz, uygun türde ve uygun varsayılan etiketlere ve öznitelik değerlerine sahip bir dosya oluşturur.<br /><br /> Yeni dosyanın dosya adını ve yolunu belirtmek için **-ToFile** seçeneğini (aşağıdaki tabloda bakın) kullanın.<br /><br /> Bildirimin \<bağımlılık > bölümüne eklenen bir uygulamanın tüm Derlemeleriyle bir uygulama bildirimi oluşturmak için **-FromDirectory** seçeneğini kullanın (aşağıdaki tabloda bulunan).|
|**-u,-Update** *[filepath] [UpdateOptions]*|Bir bildirim dosyasına bir veya daha fazla değişiklik yapar. Düzenlediğiniz dosya türünü belirtmeniz gerekli değildir. Mage.exe, bir buluşsal yöntem kümesi kullanarak dosyayı inceler ve bir dağıtım bildirimi ya da uygulama bildirimi olup olmadığını belirler.<br /><br /> Zaten bir sertifikayı olan bir dosyayı imzaladıysanız **-güncelleştirme** , anahtar imza bloğunu kaldırır. Bunun nedeni, anahtar imzasının dosyasının bir karmasını içermesi ve dosyayı değiştirmenin karmayı geçersiz kılmasıdır.<br /><br /> Mevcut dosyanın üzerine yazmak yerine yeni bir dosya adı ve yolu belirtmek için **-ToFile** seçeneğini (aşağıdaki tabloda bakın) kullanın.|
|**-s,-Sign** `[signOptions]`|Bir dosyayı imzalamak için bir anahtar çifti veya X509 sertifikası kullanır. İmzalar, dosyaların içine XML öğeleri olarak eklenir.<br /><br /> Bir **-timestampuri** değeri belirten bir bildirimi imzalarken Internet 'e bağlı olmanız gerekir.|
|**-ver,-Doğrula** *[bildirim-dosya adı]*|Bildirimin doğru şekilde imzalandığını doğrular. Diğer komutlarla birleştirilemez. <br/><br/>**.NET Framework 4,7 ve sonraki sürümlerde kullanılabilir.**|
|**-h,-?,-yardımı** *[verbose]*|Tüm kullanılabilir komutları ve seçeneklerini açıklar. Ayrıntılı yardım almak için `verbose` belirtin.|

## <a name="new-and-update-command-options"></a>Yeni ve güncelleştirme komutu seçenekleri

Aşağıdaki tabloda `-New` ve `-Update` komutlarının desteklediği seçenekler gösterilmektedir:

|Seçenekler|Varsayılan Değer|Uygulanan Öğe|Açıklama|
|-------------|-------------------|----------------|-----------------|
|**-a,-algoritması**|sha1RSA|Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Bağımlılık özetlerinin oluşturması için kullanılan algoritmayı belirtir. Değer "sha256RSA" veya "sha1RSA" olmalıdır.<br /><br /> "-Update" seçeneğiyle kullanın. Bu seçenek "-Sign" seçeneğini kullanırken yok sayılır.|
|**-APPC,-AppCodeBase** `manifestReference`||Dağıtım bildirimleri.|Uygulama bildirim dosyasına bir URL veya dosya yolu başvurusu ekler. Bu değer, uygulama bildiriminin tam yolu olmalıdır.|
|**-appı,-AppManifest** `manifestPath`||Dağıtım bildirimleri.|Bir dağıtım bildirimine, dağıtımın uygulama bildirimindeki bir başvuruyu ekler.<br /><br /> `manifestPath` tarafından belirtilen dosya var olmalı veya *Mage. exe* bir hata verecek. `manifestPath` tarafından başvurulan dosya bir uygulama bildirimi değilse, *Mage. exe* bir hata verecek.|
|**-CF,-sertifikadosyası** `filePath`||Tüm dosya türleri.|Bir bildirim veya lisans dosyasını imzalamak için x509 dijital sertifikasının konumunu belirtir. Sertifika, kişisel bilgi değişimi (PFX) dosyaları için bir parola gerektiriyorsa, bu seçenek **-Password** seçeneğiyle birlikte kullanılabilir. .NET Framework 4,7 ' den başlayarak, dosya bir özel anahtar içermiyorsa, **-CryptoProvider** ve **-keycontainer** seçeneklerinin bir birleşimi gereklidir.<br/><br/>.NET Framework 4.6.2 ile başlayarak, *Mage. exe* bildirimleri CNG ve CAPI sertifikaları ile imzalar.|
|**-ch,-sunucunuzda certhash** `hashSignature`||Tüm dosya türleri.|İstemci bilgisayarın kişisel sertifika deposunda tutulan bir dijital sertifikanın karması. Bu, Windows Sertifikaları Konsolu içinde görüntülenen bir dijital sertifikanın Parmak İzi dizesine karşılık gelir.<br /><br /> `hashSignature` büyük veya küçük harf olabilir ve tek bir dize olarak ya da her bir parmak Izine ait her sekizli ile, boşluk ve tüm Parmak Izi tırnak işareti içine alınmış olarak sağlanabilir.|
|**-CSP,-CryptoProvider** `provider-name`||Tüm dosya türleri.|Özel anahtar kapsayıcısını içeren bir şifreleme hizmeti sağlayıcısının (CSP) adını belirtir. Bu seçenek **-keycontainer** seçeneğini gerektirir.<br/><br/>Bu seçenek .NET Framework 4,7 ' den başlayarak kullanılabilir.|
|**-FD,-FromDirectory** `directoryPath`||Uygulama bildirimleri.|Uygulama bildirimini tüm alt dizinler de dahil olmak üzere tüm derlemelerin ve `directoryPath`bulunan dosyaların açıklamalarıyla doldurur. burada `directoryPath`, dağıtmak istediğiniz uygulamayı içeren dizindir. Dizindeki her dosya için, *Mage. exe* dosyanın bir derleme mi yoksa statik bir dosya mı olduğuna karar verir. Bir derlemedir, derleme adı, kod tabanı ve sürümü ile uygulamaya bir `<dependency>` Tag ve `installFrom` özniteliği ekler. Statik bir dosya ise, bir `<file>` etiketi ekler. *Mage. exe* Ayrıca uygulamanın ana yürütülebilir dosyasını tespit etmek için basit bir buluşsal yöntem kümesi kullanacaktır ve bunu bildirimde ClickOnce uygulamasının giriş noktası olarak işaretleyecek.<br /><br /> *Mage. exe* hiçbir dosyayı "veri" dosyası olarak hiçbir şekilde otomatik olarak işaretlemez. Bunu elle yapmanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: bir ClickOnce uygulamasına veri dosyası ekleme](/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application).<br /><br /> *Mage. exe* Ayrıca boyutuna bağlı olarak her dosya için bir karma üretir. ClickOnce bu karmaları kullanarak, bildirim oluşturulduktan sonra dağıtımın dosyaları üzerinde kimsenin değişiklik yapmadığından emin olur. Dağıtımınızdaki dosyalardan herhangi biri değiştiğinde, *Mage. exe* ' yi **-Update** komutuyla ve **-FromDirectory** seçeneğiyle çalıştırabilir ve başvurulan tüm dosyaların karmalarını ve derleme sürümlerini güncelleştirir.<br /><br /> **-FromDirectory** , `directoryPath`içinde bulunan tüm alt dizinlerdeki tüm dosyaları içerir.<br /><br /> \- **Update** komutuyla **-FromDirectory** kullanırsanız, *Mage. exe* uygulama bildiriminde artık dizinde bulunmayan tüm dosyaları kaldırır.|
|**-IF,-IconFile**`filePath`||Uygulama bildirimleri.|Bir .ICO simge dosyasının tam yolunu belirtir. Bu simge başlat menüsünde uygulamanızın adının yanında ve Program Ekle/Kaldır girdisinde görünür. Eğer simge sağlanmazsa, varsayılan bir simge kullanılır.|
|**-ip,-ıncludeproviderurl**`url`|true|Dağıtım bildirimleri.|Dağıtım bildiriminin, **-providerUrl**tarafından ayarlanan güncelleştirme konumu değerini içerip içermediğini gösterir.|
|**-i,-ınstall** `willInstall`|true|Dağıtım bildirimleri.|ClickOnce uygulamasının yerel bilgisayara yüklenip yüklenmeyeceğini veya Web'den çalışıp çalışmayacağını belirtir. Bir uygulamayı yüklemek, bu uygulamaya Windows **Başlat** menüsünde bir varlık sağlar. Geçerli değerler "true" veya "t" ve "false" veya "f" değerleridir.<br /><br /> **-MinVersion** seçeneğini belirtirseniz ve bir kullanıcının sürümü **-MinVersion** ' dan daha az yüklüyse, **yüklemeyi**geçirdiğiniz değere bakılmaksızın uygulamayı yüklemeye zorlayacaktır.<br /><br /> Bu seçenek **-BrowserHosted** seçeneğiyle birlikte kullanılamaz. Aynı bildirimde ikisini de belirtmeyi denemek hata oluşturur.|
|**-KC,-KeyContainer** `name`||Tüm dosya türleri.|Özel anahtarın adını içeren anahtar kapsayıcısını belirtir. Bu seçenek **CryptoProvider** seçeneğini gerektirir.<br/><br/>Bu seçenek .NET Framework 4,7 ' den başlayarak kullanılabilir.|
|**-MV,-MinVersion**`[version]`|**-Version** bayrağı tarafından belirtilen şekilde ClickOnce dağıtım bildiriminde listelenen sürüm.|Dağıtım bildirimleri.|Bir kullanıcının çalıştırabileceği bu uygulamanın en düşük sürümü. Bu bayrak uygulamanızın adlandırılmış sürümünü gereken bir güncelleştirme yapar. Eğer ürününüzün bir sürümünü bozucu bir değişiklik veya kritik bir güvenlik açığı için güncelleştirirseniz, bu bayrağı kullanarak bu güncelleştirmenin yüklenmesi gerektiğini ve kullanıcının önceki sürümleri kullanamayacağını belirtebilirsiniz.<br /><br /> `version`, **-Version** bayrağıyla bağımsız değişkenle aynı semantiğe sahip.|
|**-n,-adı** `nameString`|Dağıt|Tüm dosya türleri.|Uygulamayı tanımlamak için kullanılan ad. ClickOnce **Başlangıç** menüsünde uygulamayı tanımlamak için bu adı kullanır (uygulama kendisi yüklenmek üzere yapılandırılmışsa) ve izin yükseltme iletişim kutularında. **Note:**  Var olan bir bildirimi güncelleştiriyorsanız ve bu seçenekle bir yayımcı adı belirtmezseniz, *Mage. exe* bildirimi bilgisayarda tanımlanan kuruluş adıyla güncelleştirir. Farklı bir ad kullanmak için, bu seçeneği kullanmayı ve istediğiniz yayımcı adını belirtmeyi unutmayın.|
|**-PWD,-Password** `passwd`||Tüm dosya türleri.|Bir bildirimi dijital sertifika ile imzalamak için kullanılan şifre. **-SertifikaDosyası** seçeneğiyle birlikte kullanılmalıdır.|
|**-p, işlemci** `processorValue`|Msil|Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Bu dağıtımın çalışabileceği mikro işlemci mimarisi. Eğer derlemeleri belirli bir mikro işlemci için önceden derlenmiş olan bir veya daha fazla yükleme için hazırlanıyorsanız bu değer gereklidir. Geçerli değerler şunlardır `msil`, `x86`, `ia64`ve `amd64`. `msil`, tüm derlemelerinizin platformdan bağımsız olduğu ve ortak dil çalışma zamanı (CLR), uygulamanız ilk çalıştırıldığında onları tek bir kez derleyeceği anlamına gelen Microsoft ara dilidir.|
|**-PU,** **-providerUrl** `url`||Dağıtım bildirimleri.|ClickOnce'ın uygulama güncelleştirmeleri için inceleyeceği URL'yi belirtir.|
|**-pub,-Publisher** `publisherName`||Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Dağıtım veya uygulama bildiriminin açıklama öğesine yayımcı adını ekler. Uygulama bildiriminde kullanıldığında, **-useManifestForTrust** Ayrıca "true" veya "t" değeriyle birlikte belirtilmelidir; Aksi takdirde, bu parametre bir hata oluşturacak.|
|**-s,-SupportURL**`url`||Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|ClickOnce uygulaması için Program Ekle veya Kaldır'da görünen bağlantıyı belirtir.|
|**-ti,-TimestampUri** `uri`||Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Bir dijital zaman damgası hizmetinin URL'si. Bildirimlere zaman damgası koymak, uygulamanızın sonraki sürümünü dağıtmadan önce dijital sertifikanızın süresi dolarsa bildirimleri yeniden imzalamanıza gerek kalmamasını sağlar. Daha fazla bilgi için bkz. [Windows kök sertifika programı üyeleri](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)).|
|**-t,-ToFile** `filePath`|Yeni<br />-Dağıtım: Deploy. Application<br />-Application: Application. exe. manifest<br />Update<br />-Giriş dosyası.|Tüm dosya türleri.|Oluşturulan veya değiştirilen dosyanın çıkış yolunu belirtir.<br /><br /> **-New**kullandığınızda, **Çıkış, geçerli** çalışma dizinine yazılır. **-Update**kullandığınızda- **ToFile** sağlanmazsa, *Mage. exe* dosyayı giriş dosyasına geri yazar.|
|**-tr,-TrustLevel** `level`|Uygulama URL'sinin bulunduğu bölgeyi temel alır.|Uygulama bildirimleri.|İstemci bilgisayarlarda uygulamaya sağlanacak güven düzeyi. Değerler "Internet", "Intranet" ve "FullTrust" değerlerini içerir.|
|**-um,-UseManifestForTrust** `willUseForTrust`|False|Uygulama bildirimleri.|Uygulama bildiriminin dijital imzasının, uygulama istemcide çalışırken güven kararları için kullanılıp kullanılmayacağını belirtir. "true" veya "t" belirtmek uygulama bildiriminin güven kararları için kullanılacağını belirtir. "false" veya "f" belirtmek dağıtım bildiriminin imzasının kullanılacağını belirtir.|
|**-v,-sürüm** `versionNumber`|1.0.0.0|Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Dağıtımın sürümü. Bağımsız değişken, "*n. n. n. n*" biçiminde geçerli bir sürüm dizesi olmalıdır; burada "*n*" işaretsiz 32 bitlik bir tamsayıdır.|
|**-WPF,-WPFBrowserApp**`isWPFApp`|false|Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Bu bayrağı yalnızca, uygulama Internet Explorer içinde barındırılacak bir Windows Presentation Foundation (WPF) uygulaması ise ve tek başına yürütülebilir dosya değil ise kullanın. Geçerli değerler "true" veya "t" ve "false" veya "f" değerleridir.<br /><br /> Uygulama bildirimleri için, uygulama bildiriminin `entryPoint` öğesinin altına `hostInBrowser` özniteliğini ekler.<br /><br /> Dağıtım bildirimleri için, `deployment` öğesindeki `install` özniteliğini false olarak ayarlar ve dağıtım bildirimini bir. xbap uzantısıyla kaydeder. Bu bağımsız değişkeni **-Install** bağımsız değişkeniyle birlikte belirtmek bir hata oluşturur, çünkü tarayıcıda barındırılan bir uygulama yüklü, çevrimdışı bir uygulama olamaz.|

## <a name="sign-command-options"></a>İmza komut seçenekleri

Aşağıdaki tablo, tüm dosya türlerine uygulanan `-Sign` komutu tarafından desteklenen seçenekleri gösterir.

|Seçenekler|Açıklama|
|-------------|-----------------|
|**-CF,-sertifikadosyası** `filePath`|Bildirim imzalamak için bir dijital sertifikanın konumunu belirtir. Sertifika, kişisel bilgi değişimi (PFX) dosyaları için bir parola gerektiriyorsa, bu seçenek **-Password** seçeneğiyle birlikte kullanılabilir. .NET Framework 4,7 ' den başlayarak, dosya bir özel anahtar içermiyorsa, **-CryptoProvider** ve **-keycontainer** seçeneklerinin bir birleşimi gereklidir.<br/><br/>.NET Framework 4.6.2 ile başlayarak, *Mage. exe* bildirimleri CNG ve CAPI sertifikaları ile imzalar.|
|**-ch,-sunucunuzda certhash** `hashSignature`|İstemci bilgisayarın kişisel sertifika deposunda tutulan bir dijital sertifikanın karması. Bu, Windows Sertifikaları Konsolu içinde görüntülenen bir dijital sertifikanın Parmak İzi özelliğine karşılık gelir.<br /><br /> `hashSignature` büyük veya küçük harf olabilir ve tek bir dize olarak ya da her bir parmak Izine ait her sekizli ile boşluk ve tüm Parmak Izi tırnak işareti içine alınmış olarak sağlanabilir.|
**-CSP,-CryptoProvider** `provider-name`|Özel anahtar kapsayıcısını içeren bir şifreleme hizmeti sağlayıcısının (CSP) adını belirtir. Bu seçenek **-keycontainer** seçeneğini gerektirir.<br/><br/>Bu seçenek .NET Framework 4,7 ' den başlayarak kullanılabilir.|
|**-KC,-KeyContainer** `name`|Özel anahtarın adını içeren anahtar kapsayıcısını belirtir. Bu seçenek **CryptoProvider** seçeneğini gerektirir.<br/><br/>Bu seçenek .NET Framework 4,7 ' den başlayarak kullanılabilir.|
|**-PWD,-Password** `passwd`|Bir bildirimi dijital sertifika ile imzalamak için kullanılan şifre. **-SertifikaDosyası** seçeneğiyle birlikte kullanılmalıdır.|
|**-t,-ToFile** `filePath`|Oluşturulan veya değiştirilen dosyanın çıkış yolunu belirtir.|

## <a name="remarks"></a>Açıklamalar

*Mage. exe* için tüm bağımsız değişkenler büyük/küçük harfe duyarlıdır. Komutlar ve seçenekler bir tire (-) veya eğik çizgi (/) ile belirtilebilir.

**-Sign** komutuyla kullanılan bağımsız değişkenlerin tümü, **-New** veya **-Update** komutlarıyla birlikte her zaman kullanılabilir. Aşağıdaki komutlar eşdeğerdir.

```console
mage -Sign c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
```

> [!NOTE]
> .NET Framework sürüm 4.6.2 başlayarak, CNG sertifikaları da desteklenir.

 İmzalama gerçekleştireceğiniz son görevdir; çünkü imzalanmış bir belge, imzanın belge için geçerli olup olmadığını doğrulamak için dosyanın bir karmasını kullanır. Eğer imzalanan dosyada bir değişiklik yaparsanız, yeniden imzalamanız gerekir. Daha önce imzalanmış bir belgeyi imzaladıysanız, *Mage. exe* eski imzayı yeni ile değiştirir.

 Bir dağıtım bildirimini doldurmak için **-AppManifest** seçeneğini kullandığınızda *Mage. exe* , uygulama bildirimin geçerli dağıtım sürümünden sonra adlı bir alt dizin içindeki dağıtım bildirimiyle aynı dizinde yer alacağı ve Dağıtım bildiriminizi uygun şekilde yapılandıracağı varsayacaktır. Uygulama bildiriminiz başka bir yerde yer alabiliyorsanız, alternatif konumu ayarlamak için **-AppCodeBase** seçeneğini kullanın.

 Uygulamanızı dağıtmadan önce dağıtım ve uygulama belgeleriniz imzalanmalıdır. Bildirimleri imzalama hakkında rehberlik için bkz. [Güvenilen uygulama dağıtımına genel bakış](/visualstudio/deployment/trusted-application-deployment-overview).

 Uygulama bildirimleri için **-TrustLevel** seçeneği, bir uygulamanın istemci bilgisayarda çalıştırılması gereken izin kümesini açıklar. Varsayılan olarak, uygulamalara URL 'sinin bulunduğu *bölgeyi* temel alan bir güven düzeyi atanır. Bir şirket ağında dağıtılan uygulamalar genellikle Intranet bölgesine yerleştirilirken, Internet üzerinden dağıtılan uygulamalar Internet bölgesine yerleştirilir. İki güvenlik bölgesi de uygulamanın yerel kaynaklara erişimine kısıtlamalar koyar, ancak Intranet bölgesi Internet bölgesine göre biraz daha az sınırlayıcıdır. FullTrust bölgesi uygulamalara, bir bilgisayarın yerel kaynakları için tam erişim sağlar. Bir uygulamayı bu bölgeye yerleştirmek için **-TrustLevel** seçeneğini KULLANıRSANıZ, clr 'Nin güven Yöneticisi bileşeni kullanıcıdan bu yüksek düzeyde güven sağlamak isteyip istemediğini karar vermesini ister. Eğer uygulamanızı bir şirket ağı üzerinden dağıtıyorsanız, kullanıcıya sormadan uygulamanın güven düzeyini yükseltmek için Güvenilen Uygulama Dağıtımı'nı kullanabilirsiniz.

 Uygulama bildirimleri de özel güven bölümlerini destekler. Bu, uygulamanızın en az izni isteme güvenlik ilkesine uymasına yardımcı olur; çünkü bildirimi, uygulamanın yürütülebilmesi için gereken belirli izinleri isteyecek şekilde yapılandırabilirsiniz. *Mage. exe* özel güven bölümü eklemeyi doğrudan desteklemez. Bir metin Düzenleyicisi, XML Ayrıştırıcısı veya grafik aracı *MageUI. exe*' yi kullanarak bir tane ekleyebilirsiniz. Özel güven bölümleri eklemek için *MageUI. exe* ' nin nasıl kullanılacağı hakkında daha fazla bilgi için, bkz. [MageUI. exe (bildirim oluşturma ve düzenleme aracı, grafik istemci)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

Visual Studio 2017, *Mage. exe*' nin 4.6.1 sürümünü içerir. Bu *Mage. exe* hedefinin bu sürümüyle oluşturulan bildirimler .NET Framework 4. .NET Framework eski sürümlerini hedeflemek için *Mage. exe*' nin önceki bir sürümünü kullanın.

Var olan bir bildirime derlemeleri ekler veya var olan bir bildirimi yeniden imzaladığınızda, *Mage. exe* bildirimi .NET Framework 4 ' ü hedefleyecek şekilde güncelleştirmez.

Aşağıdaki tablolarda bu özellikler ve kısıtlamalar gösterilmektedir:

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

 Mage. exe [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]hedefleyen yeni bildirimler oluşturur. [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] hedefleyen ClickOnce uygulamaları hem [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] hem de .NET Framework 4 ' ün tam sürümünde çalıştırılabilir. Uygulamanız .NET Framework 4 ' ün tam sürümünü hedefliyorsa ve [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]üzerinde çalıştıralemezse, bir metin düzenleyicisi kullanarak istemci `<framework>` öğesini kaldırın ve bildirimi yeniden imzalayın.

Aşağıda, [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]hedefleyen bir örnek `<framework>` öğesi verilmiştir:

```xml
<framework targetVersion="4.0" profile="client" supportedRuntime="4.0.20506" />
```

## <a name="examples"></a>Örnekler

Aşağıdaki örnek, Mage için Kullanıcı arabirimini açar (*MageUI. exe*).

```console
mage
```

Aşağıdaki örnekler varsayılan bir dağıtım bildirimi ve uygulama bildirimi oluşturur. Bu dosyaların hepsi geçerli çalışma dizininde oluşturulur ve sırasıyla deploy.application ve application.exe.manifest olarak adlandırılır.

```console
mage -New Deployment
mage -New Application
```

Aşağıdaki örnek, geçerli dizindeki derlemelerle ve kaynak dosyalarıyla doldurulan bir uygulama bildirimi oluşturur.

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

Aşağıdaki örnek, geçerli dizinden alınan tüm derlemeler ve kaynak dosyaları ile doldurulmuş bir uygulama bildirimi oluşturur ve imzalar.

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

Aşağıdaki örnek, geçerli çalışma dizininde bir dijital sertifika ve özel anahtar kullanarak mevcut bir dağıtım bildirimini imzalar.

```console
mage -Sign deploy.application -CertFile cert.pfx -KeyContainer keyfile.snk -CryptoProvider "Microsoft Enhanced Cryptographic Provider v1.0"
```

## <a name="see-also"></a>Ayrıca bkz.

- [ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)
- [İzlenecek yol: ClickOnce Uygulamasını El ile Dağıtma](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Güvenilir Uygulama Dağıtımına Genel Bakış](/visualstudio/deployment/trusted-application-deployment-overview)
- [MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, Grafik İstemci)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
