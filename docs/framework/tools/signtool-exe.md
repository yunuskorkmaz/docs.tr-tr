---
title: "SignTool.exe (İmza Aracı)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Sign tool
- SignTool.exe
ms.assetid: 0c25ff6c-bff3-422e-b017-146a3ee86cb9
caps.latest.revision: "33"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 326b952b742dc3400b7a84ba35594b61aeaabb6c
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2018
---
# <a name="signtoolexe-sign-tool"></a>SignTool.exe (İmza Aracı)
İmza aracı, dosyaları dijital imzalayan, dosyalardaki imzaları doğrulayan ve dosyalara zaman damgası veren bir komut satırı aracıdır.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
signtool [command] [options] [file_name | ...]  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|`command`|Dört komutlarından birini (`catdb`, `sign`, `Timestamp`, veya `Verify`) bir dosyada gerçekleştirmek için bir işlemi belirtir. Her bir komutun açıklaması için sonraki tabloya bakın.|  
|`options`|Bir komutu değiştiren seçenek. Genel ek `/q` ve `/v` seçenekleri, her komutun benzersiz bir seçenek kümesini destekler.|  
|`file_name`|İmzalanacak dosyanın yolu.|  
  
 Aşağıdaki komutlar İmza Aracı tarafından desteklenir. Her komut, ilgili bölümlerinde listelenen ayrı seçenekler kümesiyle kullanılır.  
  
|Komut|Açıklama|  
|-------------|-----------------|  
|`catdb`|Katalog veritabanına bir katalog dosyası ekler veya katalog veritabanından katalog dosyasını kaldırır. Katalog veritabanları, katalog dosyalarının otomatik araması için kullanılır ve GUID ile tanımlanır. Tarafından desteklenen seçeneklerinin bir listesi için `catdb` komutu, bkz: [catdb komut seçenekleri](../../../docs/framework/tools/signtool-exe.md#catdb).|  
|`sign`|Dosyaları dijital olarak imzalar. Dijital imzalar, dosyaları izinsiz kullanıma karşı korur ve kullanıcıların bir imza sertifikası temelinde imzalayanı doğrulamasına olanak sağlar. Tarafından desteklenen seçeneklerinin bir listesi için `sign` komutu, bkz: [komut seçenekleri oturum](../../../docs/framework/tools/signtool-exe.md#sign).|  
|`Timestamp`|Zaman damgaları dosyaları. Tarafından desteklenen seçeneklerinin bir listesi için `TimeStamp` komutu, bkz: [zaman damgası komut seçenekleri](../../../docs/framework/tools/signtool-exe.md#TimeStamp).|  
|`Verify`|İmzalama sertifikasının güvenilir bir yetkili tarafından verilmiş, imzalama sertifikasının iptal edilmiş ve isteğe bağlı olarak imzalama sertifikasının belirli bir ilke için geçerli olup olmadığını belirleyerek dosyaların dijital imzasını doğrular. Tarafından desteklenen seçeneklerinin bir listesi için `Verify` komutu, bkz: [doğrulayın komut seçenekleri](../../../docs/framework/tools/signtool-exe.md#Verify).|  
  
 Aşağıdaki seçenekler bütün İmza Aracı komutlarına uygulanır.  
  
|Genel seçenek|Açıklama|  
|-------------------|-----------------|  
|**/q**|Komut başarıyla çalışırsa bir çıktı görüntülemez ve komut başarısız olursa en az çıktı görüntüler.|  
|**/v**|Komutun başarıyla çalıştırıldığına veya başarısız olduğuna bakılmaksızın ayrıntılı çıktıyı görüntüler ve uyarı iletilerini görüntüler.|  
|**/debug**|Hata ayıklama bilgisini görüntüler.|  
  
<a name="catdb"></a>   
## <a name="catdb-command-options"></a>catdb Komut Seçenekleri  
 Aşağıdaki tabloda kullanılabilir seçenekleri listeler `catdb` komutu.  
  
|Catdb seçeneği|Açıklama|  
|------------------|-----------------|  
|`/d`|Varsayılan katalog veritabanının güncellendiğini belirtir. Ne `/d` veya `/g` seçeneği kullanıldığında, imza aracı sistem bileşeni ve sürücü veritabanını güncelleştirir.|  
|`/g`*GUID*|Katalog veritabanına genel benzersiz tanımlayıcı tarafından tanımlanan belirtir *GUID* güncelleştirilir.|  
|`/r`|Belirtilen katalogları katalog veritabanından kaldırır. Bu seçenek belirtilmezse, İmza Aracı belirtilen katalogları katalog veritabanına ekler.|  
|`/u`|Benzersiz bir adın eklenen katalog dosyaları için otomatik olarak oluşturulduğunu belirtir. Gerekirse, katalog dosyaları var olan katalog dosyaları ile ad çakışmalarını önlemek için yeniden adlandırılır. Bu seçenek belirtilmezse, İmza Aracı eklenmekte olan katalogla aynı ada sahip tüm var olan katalogların üzerine yazar.|  
  
<a name="sign"></a>   
## <a name="sign-command-options"></a>imza Komut Seçenekleri  
 Aşağıdaki tabloda kullanılabilir seçenekleri listeler `sign` komutu.  
  
|imza komut seçenekleri|Açıklama|  
|-------------------------|-----------------|  
|`/a`|En iyi imzalama sertifikasını otomatik olarak seçer. İmza Aracı, tüm belirtilen koşulları karşılayan tüm geçerli sertifikaları bulur ve en uzun süre geçerli olanı seçer. Bu seçenek yoksa, İmza Aracı yalnızca geçerli bir imza sertifikası bulmayı bekler.|  
|`/ac`  *Dosya*|Ek bir sertifikadan ekler *dosya* imza bloğunu için.|  
|`/as`|Bu imzayı ekler. Birincil bir imza yoksa, bunun yerine bu imza birincil imza yapılır.|  
|`/c`  *CertTemplateName*|İmzalama sertifikasının Sertifika Şablon Adını (Microsoft uzantılı) belirtir.|  
|`/csp`  *CSPAdı*|Özel anahtar kapsayıcısı içeren şifreleme hizmet sağlayıcısını (CSP) belirtir.|  
|`/d`  *Desc*|İmzalı içeriğin açıklamasını belirtir.|  
|`/du`  *URL*|İmzalanmış içeriğin genişletilmiş açıklaması için Tek Düzen Kaynak Konum Belirleyicisi (URL) belirtir.|  
|`/f`  *SignCertFile*|Bir dosyadaki imza sertifikanı belirtir. Dosya kişisel bilgi değişimi (PFX) biçiminde ve bir parolayla korunan, kullanın `/p` seçeneği parolayı belirtin. Dosyayı özel anahtar içermiyor kullanırsanız `/csp` ve `/kc` CSP ve özel anahtar kapsayıcı adı belirtmek için Seçenekler.|  
|`/fd`|Dosya imzalarını oluşturmak için kullanılacak dosya özet algoritmasını belirtir. Varsayılan, SHA1 değeridir.|  
|`/i`  *IssuerName*|İmzalayan sertifikayı verenin adını belirtir. Bu değer, tam yayınlayıcı adının bir alt dizesi olabilir.|  
|`/kc`  *PrivKeyContainerName*|Özel anahtar kapsayıcısı adını belirtir.|  
|`/n`  *SubjectName*|İmzalayan sertifika konusunun adını belirtir. Bu değer, tam konu adının bir alt dizesi olabilir.|  
|`/nph`|Destekleniyorsa, yürütülebilir dosyalar için sayfa karmalarını gizler. Varsayılan, wintrust.dll sürümü ve SIGNTOOL_PAGE_HASHES ortam değişkeni tarafından belirlenir. PE olmayan dosyalar için bu seçenek göz ardı edilir.|  
|`/p`  *Parola*|PFX dosyası açılırken kullanılacak parolayı belirtir. (Kullanım `/f` seçeneği bir PFX dosyası belirtin.)|  
|`/p7`*Yolu*|Bir Ortak Anahtar Şifreleme Standartları (PKCS) #7 dosyasının belirtilen her içerik dosyası için üretildiğini belirtir. PKCS #7 dosyaları adlı *yolu*\\*filename*.p7.|  
|`/p7ce`*Değeri*|İmzalanmış PKCS #7 içeriği için seçenekleri belirtir. Ayarlama *değeri* imzalanmış içerik PKCS #7 dosyası eklemek için "katıştırılmış" veya "ayrılmış bir PKCS #7 dosyası imzalı veri bölümü üretmek için DetachedSignedData". Varsa `/p7ce` seçeneği kullanılmaz, imzalanmış içerik varsayılan olarak katıştırılır.|  
|`/p7co` *\<OID >*|İmzalanmış PKCS #7 içeriğini tanımlayan nesne tanımlayıcısını (OID) belirtir.|  
|`/ph`|Destekleniyorsa, yürütülebilir dosyalar için sayfa karmaları oluşturur.|  
|`/r`  *RootSubjectName*|İmzalama sertifikasının bağlanması gerektiği kök sertifikası konusunun adını belirtir. Bu değer, kök sertifikasının tam konu adının bir alt dizesi olabilir.|  
|`/s`  *StoreName*|Sertifika için arama yaparken açılacak depoyu belirtir. Bu seçenek belirtilmezse, `My` deposu açılır.|  
|`/sha1`  *Karma*|İmza sertifikanın SHA1 karmasını belirtir. Kalan anahtarlar tarafından belirtilen ölçütlere uygun birden çok sertifika olduğunda genellikle SHA1 karması belirtilir.|  
|`/sm`|Bir kullanıcı deposu yerine, makine deposu kullanıldığını belirtir.|  
|`/t`  *URL*|Zaman damgası sunucusunun URL'sini belirtir. Varsa bu seçeneği (veya `/tr`) olan mevcut değil, imzalanmış dosya zaman damgalı olmaz. Zaman damgası başarısız olduğunda bir uyarı üretilir. Bu seçenek kullanılamaz `/tr` seçeneği.|  
|`/td`  *algoritma*|İle kullanılan `/tr` RFC 3161 zaman damgası sunucusu tarafından kullanılan bir Özet algoritması istemek için seçeneği.|  
|`/tr`  *URL*|RFC 3161 zaman damgası sunucusunun URL'sini belirtir. Varsa bu seçeneği (veya `/t`) olan mevcut değil, imzalanmış dosya zaman damgalı olmaz. Zaman damgası başarısız olduğunda bir uyarı üretilir. Bu seçenek kullanılamaz `/t` seçeneği.|  
|`/u`  *Kullanım*|İmzalama sertifikasında hazır olması gereken gelişmiş anahtar kullanımını (EKU) belirtir. Kullanım değeri, OID veya dize ile belirtilebilir. "Kod İmzalama" varsayılan kullanım miktarıdır. (1.3.6.1.5.5.7.3.3).|  
|`/uw`|"Windows Sistem Bileşeni Doğrulaması" kullanımını belirtir. (1.3.6.1.4.1.311.10.3.6).|  
  
 Kullanım örnekleri için bkz: [kullanarak bir dosyayı imzalamak için SignTool](http://msdn.microsoft.com/library/windows/desktop/aa388170.aspx).  
  
<a name="TimeStamp"></a>   
## <a name="timestamp-command-options"></a>TimeStamp Komut Seçenekleri  
 Aşağıdaki tabloda kullanılabilir seçenekleri listeler `TimeStamp` komutu.  
  
|Zaman Damgası seçeneği|Açıklama|  
|----------------------|-----------------|  
|`/p7`|Zaman damgaları PKCS #7 dosyaları.|  
|`/t`  *URL*|Zaman damgası sunucusunun URL'sini belirtir. Zaman damgası vurulan dosyanın önceden imzalanmış olması gerekir. Ya da `/t` veya `/tr` seçeneği gereklidir.|  
|`/td`  *algoritma*|RFC 3161 zaman damgası sunucusu tarafından kullanılan bir özet algoritması ister. `/td`ile birlikte kullanılan `/tr` seçeneği.|  
|`/tp`*dizini*|Zaman damgaları İmza *dizin*.|  
|`/tr`  *URL*|RFC 3161 zaman damgası sunucusunun URL'sini belirtir. Zaman damgası vurulan dosyanın önceden imzalanmış olması gerekir. Ya da `/tr` veya `/t` seçeneği gereklidir.|  
  
 Bir kullanım örnek için bkz: [ekleme zaman damgaları daha önce imzalanmış dosyalar için](http://msdn.microsoft.com/library/windows/desktop/aa375542.aspx).  
  
<a name="Verify"></a>   
## <a name="verify-command-options"></a>Komut Seçeneklerini Doğrulama  
  
|Seçeneği doğrulama|Açıklama|  
|-------------------|-----------------|  
|`/a`|Tüm yöntemlerin dosyayı doğrulamak için kullanılabileceğini belirtir. İlk olarak, dosyanın bir katalogda imzalanmış olup olmadığını belirlemek için katalog veritabanları aranır. Dosya herhangi bir katalogda imzalanmamışsa, İmza Aracı dosyanın katıştırılmış imzasını doğrulamayı dener. Katalogda oturum açmış veya açmamış dosyalar doğrulanırken bu seçenek önerilir. Bu dosyaların örnekleri arasında Windows dosyaları veya sürücüleri yer alır.|  
|`/ad`|Varsayılan katalog veritabanını kullanarak kataloğu bulur.|  
|`/ag`*CatDBGUID*|Tarafından tanımlanan katalog veritabanındaki katalog bulur *CatDBGUID*.|  
|`/all`|Birden çok imza içeren bir dosyadaki tüm imzaları doğrular.|  
|`/as`|Sistem bileşeni (sürücü) katalog veritabanını kullanarak kataloğu bulur.|  
|`/c`*CatFile*|Katalog dosyası adını belirtir.|  
|`/d`|İmza Aracı'nın açıklama ve açıklama URL'sini yazdırması gerektiğini belirtir.|  
|`/ds`  *Dizin*|Belirtilen bir konumda imzayı doğrular.|  
|`/hash` (`SHA1`&#124;`SHA256`)|Katalogdaki bir dosya ararken kullanmak için bir isteğe bağlı karma algoritmasını belirtir.|  
|`/kp`|Çekirdek modu sürücü imzalama ilkesi ile doğrulama gerçekleştirilmesi gerektiğini belirtir.|  
|`/ms`|Birden çok doğrulama mantığı kullanır. Bu, varsayılan davranıştır bir [WinVerifyTrust](http://msdn.microsoft.com/library/windows/desktop/aa388208.aspx) çağırmak [!INCLUDE[win8](../../../includes/win8-md.md)] ve üstü.|  
|`/o`*Sürüm*|İşletim sistemi sürümüne göre dosyayı doğrular. *Sürüm* aşağıdaki biçime sahiptir: *sistemi PlatformId*:*VerMajor*. *VerMinor*. *BuildNumber*. *Sistemi PlatformId* alttaki değerini temsil eden bir <xref:System.PlatformID> numaralandırma üyesi. **Önemli:** kullanımını `/o` anahtar önerilir. Varsa `/o` belirtilmezse, SignTool.exe beklenmeyen sonuçlar döndürebilir. Örneğin, dahil `/o` anahtar, daha eski bir işletim sisteminde doğru doğrulamak sistem kataloglarında doğrulanmadı doğru daha yeni bir işletim sisteminde.|  
|`/p7`|PKCS #7 dosyalarını doğrular. Varolan ilkeler PKCS #7 doğrulaması için kullanılmaz. İmza denetlenir ve imzalama sertifikası zincir oluşturulur.|  
|`/pa`|Varsayılan Authenticode Doğrulama İlkesi kullanılması gerektiğini belirtir. Varsa `/pa` seçeneği belirtilmezse, imza aracı Windows sürücü doğrulama İlkesi kullanır. Bu seçenek kullanılamaz `catdb` seçenekleri.|  
|`/pg`*PolicyGUID*|GUID'ye göre doğrulama ilkesi belirtir. *PolicyGUID* doğrulama İlkesi ActionId için karşılık gelir. Bu seçenek kullanılamaz `catdb` seçenekleri.|  
|`/ph`|İmza Aracı'nın sayfa karma değerlerini yazdırması ve doğrulaması gerektiğini belirtir.|  
|`/r`*RootSubjectName*|İmzalama sertifikasının bağlanması gerektiği kök sertifikası konusunun adını belirtir. Bu değer, kök sertifikasının tam konu adının bir alt dizesi olabilir.|  
|`/tw`|İmza zaman damgalı değilse bir uyarı oluşturulacağını belirtir.|  
  
 Kullanım örnekleri için bkz: [kullanarak bir dosya imzayı doğrulamak için SignTool](http://msdn.microsoft.com/library/windows/desktop/aa388171.aspx).  
  
## <a name="return-value"></a>Dönüş Değeri  
 İmza Aracı, sonlandırıldığında aşağıdaki çıkış kodlarından birini döndürür.  
  
|Çıkış kodu|Açıklama|  
|---------------|-----------------|  
|0|Yürütme başarılı oldu.|  
|1.|Yürütme başarısız oldu.|  
|2|Yürütme uyarılarla tamamlandı.|  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, MyCatalogFileName.cat katalog dosyasını sistem bileşeni ve sürücü veritabanına ekler. `/u` Seçeneği oluşturursa benzersiz bir ad adlı dosya var olan değiştirilmesini önlemek için gereken katalog `MyCatalogFileName.cat`.  
  
```  
signtool catdb /v /u MyCatalogFileName.cat  
```  
  
 Aşağıdaki komut en iyi sertifikayı kullanarak bir dosyayı otomatik olarak imzalar.  
  
```  
signtool sign /a MyFile.exe  
```  
  
 Aşağıdaki komut parola korumalı bir PFX dosyasında depolanan bir sertifika kullanarak bir dosyayı dijital olarak imzalar.  
  
```  
signtool sign /f MyCert.pfx /p MyPassword MyFile.exe  
```  
  
 Aşağıdaki komut bir dosyayı dijital olarak imzalar ve zaman damgası oluşturur. Dosyayı imzalamak için kullanılan sertifika bir PFX dosyasında saklanır.  
  
```  
signtool sign /f MyCert.pfx /t http://timestamp.verisign.com/scripts/timstamp.dll MyFile.exe  
```  
  
 Aşağıdaki komutu, içinde bulunan bir sertifika kullanarak bir dosya oturum açtığında `My` bir konu adına sahip deposu `My Company Certificate`.  
  
```  
signtool sign /n "My Company Certificate" MyFile.exe  
```  
  
 Aşağıdaki komut bir ActiveX denetimini imzalar ve kullanıcıdan denetimi yüklemesi istendiğinde Internet Explorer tarafından görüntülenen bilgileri sağlar.  
  
```  
Signtool sign /f MyCert.pfx /d: "MyControl" /du http://www.example.com/MyControl/info.html MyControl.exe  
```  
  
 Aşağıdaki komut zaten dijital olarak imzalanmış bir dosya için zaman damgası oluşturur.  
  
```  
signtool timestamp /t http://timestamp.verisign.com/scripts/timstamp.dll MyFile.exe  
```  
  
 Aşağıdaki komut bir dosyanın imzalandığını doğrular.  
  
```  
signtool verify MyFile.exe  
```  
  
 Aşağıdaki komut bir katalogda imzalanmış olabilecek bir sistem dosyasını doğrular.  
  
```  
signtool verify /a SystemFile.dll  
```  
  
 Aşağıdaki komutu adlı bir katalogda imzalı bir sistem dosyası doğrular `MyCatalog.cat`.  
  
```  
signtool verify /c MyCatalog.cat SystemFile.dll  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araçlar](../../../docs/framework/tools/index.md)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
