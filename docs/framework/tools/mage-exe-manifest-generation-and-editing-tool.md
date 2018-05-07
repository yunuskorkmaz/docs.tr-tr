---
title: Mage.exe (Bildirim Üretme ve Düzenleme Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- Manifest Generation and Editing tool
- Mage.exe
ms.assetid: 77dfe576-2962-407e-af13-82255df725a1
ms.openlocfilehash: 551173a7ed8d60ca1870159cd7e533720275bd20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="mageexe-manifest-generation-and-editing-tool"></a>Mage.exe (Bildirim Üretme ve Düzenleme Aracı)
Bildirim Oluşturma ve Düzenleme Aracı (Mage.exe), uygulama ve dağıtım bildirimlerinin oluşturulmasını ve düzenlenmesini destekleyen bir komut satırı aracıdır. Bir komut satırı aracı Mage.exe hem toplu komut dosyaları hem de dahil olmak üzere diğer Windows tabanlı uygulamalar çalıştırılabilir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] uygulamalar.  
  
 Mage.exe yerine ayrıca bir grafik uygulaması olan MageUI.exe'yi de kullanabilirsiniz. Daha fazla bilgi için bkz: [MageUI.exe (bildirim üretme ve düzenleme aracı, grafik istemci)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Mage.exe ve MageUI.exe iki sürümü bir bileşeni olarak dahil edilen [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] kurulumu. Sürüm bilgileri, çalışma MageUI.exe görmek için seçin **yardımcı**seçip **hakkında**. Bu belge Mage.exe ve MageUI.exe'nin 4.0.x.x sürümünü açıklar.  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Mage [commands] [commandOptions]  
```  
  
#### <a name="parameters"></a>Parametreler  
 Aşağıdaki tablo Mage.exe tarafından desteklenen komutları gösterir. Bu komutları tarafından desteklenen seçenekleri hakkında daha fazla bilgi için bkz: [yeni ve güncelleştirme komut seçenekleri](#NewUpdate) ve [oturum komut seçenekleri](#Sign).  
  
|Komut|Açıklama|  
|-------------|-----------------|  
|**-cc, ClearApplicationCache**|Tüm yalnızca çevrimiçi uygulamalar için indirilen uygulama önbelleğini temizler.|  
|**-n, - yeni** *dosya türü [newOptions]*|Belirtilen türde yeni bir dosya oluşturur. Geçerli türler şunlardır:<br /><br /> -   `Deployment`: Yeni bir dağıtım bildirimi oluşturur.<br />-   `Application`: Yeni bir uygulama bildirimi oluşturur.<br /><br /> Eğer bu komutla birlikte hiçbir ek parametre belirtmezseniz, uygun türde ve uygun varsayılan etiketlere ve öznitelik değerlerine sahip bir dosya oluşturur.<br /><br /> Kullanım **- ToFile** seçeneği (aşağıdaki tabloda yer alan bakın) yeni dosyasının yolu ve dosya adını belirtmek için.<br /><br /> Kullanım **- FromDirectory** seçeneği (aşağıdaki tabloda yer alan bakın) tüm derlemelerin eklenecek bir uygulama için bir uygulama bildirimi oluşturmak için \<bağımlılık > bildirim bölümü.|  
|**-u-güncelleştirme** *[filePath] [updateOptions]*|Bir bildirim dosyasına bir veya daha fazla değişiklik yapar. Düzenlediğiniz dosya türünü belirtmeniz gerekli değildir. Mage.exe, bir buluşsal yöntem kümesi kullanarak dosyayı inceler ve bir dağıtım bildirimi ya da uygulama bildirimi olup olmadığını belirler.<br /><br /> Bir dosyayı bir sertifika ile oturum açmış **-güncelleştirme** anahtar imza bloğunu kaldırır. Bunun nedeni, anahtar imzasının dosyasının bir karmasını içermesi ve dosyayı değiştirmenin karmayı geçersiz kılmasıdır.<br /><br /> Kullanım **- ToFile** seçeneği (aşağıdaki tabloda yer alan bakın) yeni bir dosya adı ve yolu varolan bir dosyanın üzerine yerine belirtmek için.|  
|**-s-oturum** `[signOptions]`|Bir dosyayı imzalamak için bir anahtar çifti veya X509 sertifikası kullanır. İmzalar, dosyaların içine XML öğeleri olarak eklenir.<br /><br /> Internet'e belirten bir bildirim imzalarken bağlanmalıdır bir **- TimestampUri** değeri.|  
|**-h-?-Yardım** *[verbose]*|Tüm kullanılabilir komutları ve seçeneklerini açıklar. Belirtin `verbose` ayrıntılı yardım almak için.|  
  
<a name="NewUpdate"></a>   
## <a name="new-and-update-command-options"></a>New ve Update Komutu Seçenekleri  
 Tarafından desteklenen seçenekleri aşağıdaki tabloda gösterilmektedir `-New` ve `-Update` komutları.  
  
|Seçenekler|Varsayılan Değer|Uygulandığı öğe:|Açıklama|  
|-------------|-------------------|----------------|-----------------|  
|**-a,-algoritması**|sha1RSA|Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Bağımlılık özetlerinin oluşturması için kullanılan algoritmayı belirtir. Değer "sha256RSA" veya "sha1RSA" olmalıdır.<br /><br /> "-Update" seçeneğiyle kullanın. Bu seçenek "-Sign" seçeneğini kullanırken yok sayılır.|  
|**-appc, - AppCodeBase** `manifestReference`||Dağıtım bildirimleri.|Uygulama bildirim dosyasına bir URL veya dosya yolu başvurusu ekler. Bu değer, uygulama bildiriminin tam yolu olmalıdır.|  
|**-appm, - AppManifest** `manifestPath`||Dağıtım bildirimleri.|Bir dağıtım bildirimine, dağıtımın uygulama bildirimindeki bir başvuruyu ekler.<br /><br /> Dosyanın belirtilen tarafından `manifestPath` mevcut olmalıdır veya bir hata sorun Mage.exe olacaktır. Dosya tarafından başvurulan `manifestPath` bir uygulama değildir bildirim, Mage.exe hata da gönderirsiniz.|  
|**-cf, - SertifikaDosyası** `filePath`||Tüm dosya türleri.|Bildirim imzalamak için bir X509 dijital sertifikasının konumunu belirtir. Bu seçenek ile birlikte kullanılan **-parola** sertifika bir parola gerektiriyorsa seçeneği.|  
|**-ch, - CertHash** `hashSignature`||Tüm dosya türleri.|İstemci bilgisayarın kişisel sertifika deposunda tutulan bir dijital sertifikanın karması. Bu, Windows Sertifikaları Konsolu içinde görüntülenen bir dijital sertifikanın Parmak İzi dizesine karşılık gelir.<br /><br /> `hashSignature` büyük veya küçük harf hem tek dize olarak ya da her sekizli alanları ve tırnak işaretleri içine tüm parmak izi ile ayrılmış parmak izi ile sağlanan olabilir.|  
|**-fd, - FromDirectory** `directoryPath`||Uygulama bildirimleri.|Uygulama bildirimini tüm derlemeleri ve bulunan dosyaları açıklamalarını doldurur `directoryPath`, tüm alt dizinler de dahil olmak üzere burada `directoryPath` dağıtmak istediğiniz uygulamayı içeren dizindir. Dizindeki her dosya için, Mage.exe dosyanın bir derleme veya statik dosya olup olmadığına karar verir. Derlemenin doğruysa ekler bir `<dependency>` etiketi ve `installFrom` uygulama derlemenin adı, kod temeli ve sürümü ile özniteliği. Ekler, statik bir dosya olup olmadığını, bir `<file>` etiketi. Mage.exe ayrıca uygulamanızın temel yürütülebilir dosyasını algılamak için basit bir buluşsal yöntem kümesi kullanır, ve onu bildirimde ClickOnce uygulamasının giriş noktası olarak işaretler.<br /><br /> Mage.exe bir dosyayı asla otomatik olarak bir "veri" dosyası şeklinde işaretlemez. Bunu elle yapmanız gerekir. Daha fazla bilgi için bkz: [nasıl yapılır: ClickOnce uygulamasına bir veri dosyası dahil](/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application).<br /><br /> Mage.exe ayrıca her dosya için boyutuna göre bir karma oluşturur. ClickOnce bu karmaları kullanarak, bildirim oluşturulduktan sonra dağıtımın dosyaları üzerinde kimsenin değişiklik yapmadığından emin olur. Dağıtımınızda bulunan dosyalardan herhangi birini değiştirirseniz, Mage.exe ile çalıştırabilirsiniz **-güncelleştirme** komut ve **- FromDirectory** seçeneği ve karmaları ve tüm başvurulan dosyaların derleme sürümlerini güncelleştirir.<br /><br /> **-FromDirectory** tüm dosyaları içinde bulunan tüm alt dizinler içerecektir `directoryPath`.<br /><br /> Kullanırsanız **- FromDirectory** ile **-güncelleştirme** komutunu Mage.exe artık dizininde mevcut uygulama bildiriminde herhangi bir dosya kaldırılır.|  
|**-Eğer, - IconFile**  `filePath`||Uygulama bildirimleri.|Bir .ICO simge dosyasının tam yolunu belirtir. Bu simge başlat menüsünde uygulamanızın adının yanında ve Program Ekle/Kaldır girdisinde görünür. Eğer simge sağlanmazsa, varsayılan bir simge kullanılır.|  
|**-IP, - IncludeProviderURL**  `url`|true|Dağıtım bildirimleri.|Dağıtım bildirimi tarafından belirlenen güncelleştirme konum değeri içerip içermediğini gösterir **- ProviderURL**.|  
|**-i-yükleyin** `willInstall`|true|Dağıtım bildirimleri.|ClickOnce uygulamasının yerel bilgisayara yüklenip yüklenmeyeceğini veya Web'den çalışıp çalışmayacağını belirtir. Bir varlığı Windows sağlar, uygulamanın bir uygulama yükleme **Başlat** menüsü. Geçerli değerler "true" veya "t" ve "false" veya "f" değerleridir.<br /><br /> Belirtirseniz **- MinVersion** seçeneği ve bir kullanıcı bir sürüme sahip değerinden **- MinVersion** yüklüyse, bu uygulamayı yüklemek için geçirdiğiniz değerinden bağımsız şekilde zorlar **- Yükleme**.<br /><br /> Bu seçenek kullanılamaz **- BrowserHosted** seçeneği. Aynı bildirimde ikisini de belirtmeyi denemek hata oluşturur.|  
|**-mv, - MinVersion**  `[version]`|ClickOnce dağıtım bildirimi tarafından belirtilen sürüm listelenen **-sürüm** bayrağı.|Dağıtım bildirimleri.|Bir kullanıcının çalıştırabileceği bu uygulamanın en düşük sürümü. Bu bayrak uygulamanızın adlandırılmış sürümünü gereken bir güncelleştirme yapar. Eğer ürününüzün bir sürümünü bozucu bir değişiklik veya kritik bir güvenlik açığı için güncelleştirirseniz, bu bayrağı kullanarak bu güncelleştirmenin yüklenmesi gerektiğini ve kullanıcının önceki sürümleri kullanamayacağını belirtebilirsiniz.<br /><br /> `version` bağımsız değişkeni olarak aynı semantiklerine sahip **-sürüm** bayrağı.|  
|**-n, - adı** `nameString`|Dağıt|Tüm dosya türleri.|Uygulamayı tanımlamak için kullanılan ad. ClickOnce uygulamasında tanımlamak için bu ad kullanacağınız **Başlat** (uygulama kendisini yüklemek için yapılandırılmışsa) menü ve izin yükseltme iletişim kutularında. **Not:** varolan bildiriminde güncelleştirdiğiniz ve bu seçenekle bir yayımcı adı belirtmezseniz, Mage.exe bilgisayarda tanımlanmış kuruluş adı ile bildirim güncelleştirir. Farklı bir ad kullanmak için, bu seçeneği kullanmayı ve istediğiniz yayımcı adını belirtmeyi unutmayın.|  
|**-pwd,-parola** `passwd`||Tüm dosya türleri.|Bir bildirimi dijital sertifika ile imzalamak için kullanılan şifre. İle birlikte kullanılmalıdır **- SertifikaDosyası** seçeneği.|  
|**-p, işlemci** `processorValue`|Msil|Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Bu dağıtımın çalışabileceği mikro işlemci mimarisi. Eğer derlemeleri belirli bir mikro işlemci için önceden derlenmiş olan bir veya daha fazla yükleme için hazırlanıyorsanız bu değer gereklidir. Geçerli değerler arasında `msil`, `x86`, `ia64`, ve `amd64`. `msil` derlemeleriniz platformdan bağımsız tümü ve ortak dil çalışma zamanı (CLR) olacak yalnızca saat anlamına gelir Ara dile derleme, bunları, uygulamanızın ilk çalıştırma olduğunda Microsoft eder.|  
|**-pu,** **- ProviderURL** `url`||Dağıtım bildirimleri.|ClickOnce'ın uygulama güncelleştirmeleri için inceleyeceği URL'yi belirtir.|  
|**-pub,-yayımcı** `publisherName`||Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Dağıtım veya uygulama bildiriminin açıklama öğesine yayımcı adını ekler. Bir uygulama bildirimi kullanıldığında **- UseManifestForTrust** "true" veya "t"; bir değer de belirtilmesi gerekir aksi takdirde, bu parametre bir hata yükseltirsiniz.|  
|**-s - SupportURL**  `url`||Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|ClickOnce uygulaması için Program Ekle veya Kaldır'da görünen bağlantıyı belirtir.|  
|**-Za, - TimestampUri** `uri`||Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Bir dijital zaman damgası hizmetinin URL'si. Bildirimlere zaman damgası koymak, uygulamanızın sonraki sürümünü dağıtmadan önce dijital sertifikanızın süresi dolarsa bildirimleri yeniden imzalamanıza gerek kalmamasını sağlar. Daha fazla bilgi için bkz: [Windows kök sertifika programı üyeleri](http://go.microsoft.com/fwlink/?LinkId=159000).|  
|**-t - ToFile** `filePath`|-Yeni:<br />-Dağıtım: deploy.application<br />-Uygulama: application.exe.manifest<br />-Güncelleştirme:<br />-Giriş dosyası.|Tüm dosya türleri.|Oluşturulan veya değiştirilen dosyanın çıkış yolunu belirtir.<br /><br /> Varsa **- ToFile** kullandığınızda sağlanmayan **-yeni**, çıktı geçerli çalışma dizini yazılır. Varsa **- ToFile** kullandığınızda sağlanmayan **-güncelleştirme**, Mage.exe yazacak dosyayı geri giriş dosyası.|  
|**-tr, - TrustLevel** `level`|Uygulama URL'sinin bulunduğu bölgeyi temel alır.|Uygulama bildirimleri.|İstemci bilgisayarlarda uygulamaya sağlanacak güven düzeyi. Değerler "Internet", "Intranet" ve "FullTrust" değerlerini içerir.|  
|**-um, - UseManifestForTrust** `willUseForTrust`|False|Uygulama bildirimleri.|Uygulama bildiriminin dijital imzasının, uygulama istemcide çalışırken güven kararları için kullanılıp kullanılmayacağını belirtir. "true" veya "t" belirtmek uygulama bildiriminin güven kararları için kullanılacağını belirtir. "false" veya "f" belirtmek dağıtım bildiriminin imzasının kullanılacağını belirtir.|  
|**-v-sürüm** `versionNumber`|1.0.0.0|Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Dağıtımın sürümü. Bağımsız değişkeni geçerli bir sürüm dizesi biçimi olmalıdır "*N.N.N.N*", burada"*N*" işaretsiz bir 32 bit tamsayıdır.|  
|**-wpf, - WPFBrowserApp**  `isWPFApp`|false|Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Bu bayrağı yalnızca, uygulama Internet Explorer içinde barındırılacak bir Windows Presentation Foundation (WPF) uygulaması ise ve tek başına yürütülebilir dosya değil ise kullanın. Geçerli değerler "true" veya "t" ve "false" veya "f" değerleridir.<br /><br /> Uygulama bildirimleri için ekler `hostInBrowser` altında öznitelik `entryPoint` uygulama bildirimi öğesidir.<br /><br /> Dağıtım bildirimleri için ayarlar `install` özniteliği `deployment` öğesi false ve dağıtım bildirimi .xbap uzantısı ile kaydeder. Bu bağımsız değişkeni ile birlikte belirtme **-yükleme** bağımsız değişkeni, tarayıcı tarafından barındırılan bir uygulama yüklü, çevrimdışı uygulama olamayacağı için bir hata oluşturur.|  
  
<a name="Sign"></a>   
## <a name="sign-command-options"></a>İmza Komut Seçenekleri  
 Tarafından desteklenen seçenekleri aşağıdaki tabloda gösterilmektedir `-Sign` tüm dosya türleri için geçerli komutu.  
  
|Seçenekler|Açıklama|  
|-------------|-----------------|  
|**-cf, - SertifikaDosyası** `filePath`|Bildirim imzalamak için bir dijital sertifikanın konumunu belirtir. Bu seçenek ile birlikte kullanılan **-parola** seçeneği.|  
|**-ch, - CertHash** `hashSignature`|İstemci bilgisayarın kişisel sertifika deposunda tutulan bir dijital sertifikanın karması. Bu, Windows Sertifikaları Konsolu içinde görüntülenen bir dijital sertifikanın Parmak İzi özelliğine karşılık gelir.<br /><br /> `hashSignature` büyük veya küçük harf hem tek dize olarak veya her sekizli alanları ve tırnak işaretleri içine tüm parmak izi ile ayrılmış parmak izi ile sağlanan olabilir.|  
|**-pwd,-parola** `passwd`|Bir bildirimi dijital sertifika ile imzalamak için kullanılan şifre. İle birlikte kullanılmalıdır **- SertifikaDosyası** seçeneği.|  
|**-t - ToFile** `filePath`|Oluşturulan veya değiştirilen dosyanın çıkış yolunu belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Mage.exe için tüm bağımsız değişkenler büyük küçük harfe duyarsızdır. Komutlar ve seçenekler bir tire (-) veya eğik çizgi (/) ile belirtilebilir.  
  
 Tüm bağımsız değişkenleri ile kullanılan **-oturum** komutu ile herhangi bir zamanda kullanılabilir **-yeni** veya **-güncelleştirme** komutları da. Aşağıdaki komutlar eşdeğerdir.  
  
```  
mage -Sign c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx  
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx  
```  
  
> [!NOTE]
>  .NET Framework 4.6.2 sürüm ile başlayarak, CNG sertifikalarından de desteklenir.  
  
 İmzalama gerçekleştireceğiniz son görevdir; çünkü imzalanmış bir belge, imzanın belge için geçerli olup olmadığını doğrulamak için dosyanın bir karmasını kullanır. Eğer imzalanan dosyada bir değişiklik yaparsanız, yeniden imzalamanız gerekir. Eğer önceden imzalanmış olan bir dosyayı imzalarsanız, Mage.exe önceki imzayı yenisiyle değiştirir.  
  
 Kullandığınızda **- AppManifest** dağıtım bildirimi doldurmak için seçenek, Mage.exe, uygulama bildiriminizi dağıtımı ile aynı dizinde yer alacağı olmadığını varsayar sonra geçerli adlı bir alt içinde bildirim Dağıtım sürüm ve Dağıtım bildiriminizi uygun şekilde yapılandırın. Uygulama bildiriminizi başka bir yerde bulunan kullanırsanız **- AppCodeBase** alternatif konumu ayarlamak için seçeneği.  
  
 Uygulamanızı dağıtmadan önce dağıtım ve uygulama belgeleriniz imzalanmalıdır. Bildirimleri imzalama hakkında yönergeler için bkz [güvenilir uygulama dağıtımına genel bakış](/visualstudio/deployment/trusted-application-deployment-overview).  
  
 **- TrustLevel** seçeneği uygulama bildirimleri için bir uygulama gerektirir istemci bilgisayarda çalıştırmak için izni açıklar. Varsayılan olarak, uygulamaların temel bir güven düzeyi atanan *bölge* URL'LERİNİ bulunduğu içinde. Bir şirket ağında dağıtılan uygulamalar genellikle Intranet bölgesine yerleştirilirken, Internet üzerinden dağıtılan uygulamalar Internet bölgesine yerleştirilir. İki güvenlik bölgesi de uygulamanın yerel kaynaklara erişimine kısıtlamalar koyar, ancak Intranet bölgesi Internet bölgesine göre biraz daha az sınırlayıcıdır. FullTrust bölgesi uygulamalara, bir bilgisayarın yerel kaynakları için tam erişim sağlar. Kullanırsanız **- TrustLevel** bu bölgede uygulamanın yerleştirileceği seçeneği, CLR güven yöneticisi bileşeninin çözemiyorsa bu daha yüksek güven düzeyi vermek isteyip istemediğini karar vermek için kullanıcıyı uyarır. Eğer uygulamanızı bir şirket ağı üzerinden dağıtıyorsanız, kullanıcıya sormadan uygulamanın güven düzeyini yükseltmek için Güvenilen Uygulama Dağıtımı'nı kullanabilirsiniz.  
  
 Uygulama bildirimleri de özel güven bölümlerini destekler. Bu, uygulamanızın en az izni isteme güvenlik ilkesine uymasına yardımcı olur; çünkü bildirimi, uygulamanın yürütülebilmesi için gereken belirli izinleri isteyecek şekilde yapılandırabilirsiniz. Mage.exe doğrudan özel bir güven bölümü eklemeyi desteklemez. Bir metin düzenleyicisi, bir XML ayrıştırıcısı veya MageUI.exe grafik aracını kullanarak bir özel güven bölümü ekleyebilirsiniz. MageUI.exe özel güven bölüm eklemek için nasıl kullanılacağı hakkında daha fazla bilgi için bkz: [MageUI.exe (bildirim üretme ve düzenleme aracı, grafik istemci)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
 İle birlikte Mage.exe 4 sürümü ile oluşturulan yeni bildirimleri [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], hedef [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. .NET Framework'ün önceki sürümlerini hedeflemek için, Mage.exe'nin önceki bir sürümünü kullanmanız gerekir. Ekleme ya da mevcut bir bildirim veya varolan bir bildirimi yeniden imzalama derlemeleri kaldırma Mage.exe bildirim hedefe güncelleştirmez [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Aşağıdaki tablolar bu özellikleri ve kısıtlamaları gösterir.  
  
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
  
 Mage.exe hedefleyen yeni bildirimleri oluşturur [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Hedef ClickOnce uygulamalarını [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] hem de çalıştırabilirsiniz [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] ve tam sürümünü [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Uygulamanız tam sürümünü hedefliyorsa [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ve çalışamaz [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)], istemci kaldırma `<framework>` bir metin Düzenleyicisi'ni ve bildirim'yeniden oturum kullanarak öğesi. Bir örnek verilmiştir `<framework>` hedefler öğesi [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)].  
  
```xml  
<framework targetVersion="4.0" profile="client" supportedRuntime="4.0.20506" />  
```  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki örnek Mage için kullanıcı arabirimini (MageUI.exe) açar.  
  
```  
mage  
```  
  
 Aşağıdaki örnekler varsayılan bir dağıtım bildirimi ve uygulama bildirimi oluşturur. Bu dosyaların hepsi geçerli çalışma dizininde oluşturulur ve sırasıyla deploy.application ve application.exe.manifest olarak adlandırılır.  
  
```  
mage -New Deployment  
mage -New Application  
```  
  
 Aşağıdaki örnek, tüm kaynak dosyaları MoveFirst dizinden ve derlemeler ile doldurulan bir uygulama bildirimi oluşturur.  
  
```  
mage -New Application -FromDirectory . -Version 1.0.0.0  
```  
  
 Aşağıdaki örnek önceki örneği devam ettirerek dağıtım adımı ve hedef mikro işlemciyi belirtir. Ayrıca ClickOnce'ın güncelleştirmeler için denetleyeceği bir URL belirtir.  
  
```  
mage -New Application -FromDirectory . -Name "Hello, World! Application" -Version 1.0.0.0 -Processor "x86" -ProviderUrl http://internalserver/HelloWorld/  
```  
  
 Aşağıdaki örnek, Internet Explorer'da barındırılacak bir WPF uygulamasını dağıtmak için bir bildirim çiftinin nasıl oluşturulacağını gösterir.  
  
```  
mage -New Application -FromDirectory . -Version 1.0.0.0 -WPFBrowserApp true  
mage -New Deployment -AppManifest 1.0.0.0\application.manifest -WPFBrowserApp true  
```  
  
 Aşağıdaki örnek dağıtım bildirimini bir uygulama bildirimindeki bilgiyle güncelleştirir, ve uygulama bildiriminin konumu için kod temelini ayarlar.  
  
```  
mage -Update HelloWorld.deploy -AppManifest 1.0.0.0\application.manifest -AppCodeBase http://internalserver/HelloWorld.deploy  
```  
  
 Aşağıdaki örnek dağıtım bildirimini düzenleyerek kullanıcının yüklü sürümünün zorla güncelleştirilmesini sağlar.  
  
```  
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -MinVersion 1.1.0.0  
```  
  
 Aşağıdaki örnek dağıtım bildiriminin uygulama bildirimini ayrı bir dizinden almasını sağlar.  
  
```  
mage -Update HelloWorld.deploy -AppCodeBase http://anotherserver/HelloWorld/1.1.0.0/  
```  
  
 Aşağıdaki örnek geçerli çalışma dizinindeki bir dijital sertifikayı kullanarak varolan bir dağıtım bildirimini imzalar.  
  
```  
mage -Sign deploy.application -CertFile cert.pfx -Password <passwd>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)  
 [İzlenecek yol: ClickOnce Uygulamasını El ile Dağıtma](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)  
 [Güvenilir Uygulama Dağıtımına Genel Bakış](/visualstudio/deployment/trusted-application-deployment-overview)  
 [MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, Grafik İstemci)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
