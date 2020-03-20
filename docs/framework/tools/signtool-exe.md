---
title: SignTool.exe (İmza Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- Sign tool
- SignTool.exe
ms.assetid: 0c25ff6c-bff3-422e-b017-146a3ee86cb9
ms.openlocfilehash: 8ce31b1399700906d6d6e2a369dcfc4b61fe9646
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180319"
---
# <a name="signtoolexe-sign-tool"></a>SignTool.exe (İmza Aracı)
İmza aracı, dosyaları dijital imzalayan, dosyalardaki imzaları doğrulayan ve dosyalara zaman damgası veren bir komut satırı aracıdır.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
signtool [command] [options] [file_name | ...]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|`command`|Bir dosyaüzerinde gerçekleştirecek `Timestamp`bir `Verify`işlemi belirten dört komuttan biri (,`catdb` `sign`, , veya ) Her bir komutun açıklaması için sonraki tabloya bakın.|  
|`options`|Bir komutu değiştiren seçenek. Genel `/q` ve `/v` seçeneklere ek olarak, her komut benzersiz bir seçenek kümesini destekler.|  
|`file_name`|İmzalanacak dosyanın yolu.|  
  
 Aşağıdaki komutlar İmza Aracı tarafından desteklenir. Her komut, ilgili bölümlerinde listelenen ayrı seçenekler kümesiyle kullanılır.  
  
|Komut|Açıklama|  
|-------------|-----------------|  
|`catdb`|Katalog veritabanına bir katalog dosyası ekler veya katalog veritabanından katalog dosyasını kaldırır. Katalog veritabanları, katalog dosyalarının otomatik araması için kullanılır ve GUID ile tanımlanır. `catdb` Komut tarafından desteklenen seçeneklerin listesi için [catdb Komut Seçenekleri'ne](signtool-exe.md#catdb)bakın.|  
|`sign`|Dosyaları dijital olarak imzalar. Dijital imzalar, dosyaları izinsiz kullanıma karşı korur ve kullanıcıların bir imza sertifikası temelinde imzalayanı doğrulamasına olanak sağlar. `sign` Komut tarafından desteklenen seçeneklerin listesi için [komut seçenekleri'ni işaretleyin.](signtool-exe.md#sign)|  
|`Timestamp`|Zaman damgaları dosyaları. Komut tarafından desteklenen seçeneklerin listesi `TimeStamp` için [TimeStamp Komut Seçenekleri'ne](signtool-exe.md#TimeStamp)bakın.|  
|`Verify`|İmzalama sertifikasının güvenilir bir yetkili tarafından verilmiş, imzalama sertifikasının iptal edilmiş ve isteğe bağlı olarak imzalama sertifikasının belirli bir ilke için geçerli olup olmadığını belirleyerek dosyaların dijital imzasını doğrular. `Verify` Komut tarafından desteklenen seçeneklerin listesi için [bkz.](signtool-exe.md#Verify)|  
  
 Aşağıdaki seçenekler bütün İmza Aracı komutlarına uygulanır.  
  
|Genel seçenek|Açıklama|  
|-------------------|-----------------|  
|**/q**|Komut başarıyla çalışırsa bir çıktı görüntülemez ve komut başarısız olursa en az çıktı görüntüler.|  
|**/v**|Komutun başarıyla çalıştırıldığına veya başarısız olduğuna bakılmaksızın ayrıntılı çıktıyı görüntüler ve uyarı iletilerini görüntüler.|  
|**/hata ayıklama**|Hata ayıklama bilgisini görüntüler.|  
  
<a name="catdb"></a>
## <a name="catdb-command-options"></a>catdb Komut Seçenekleri  
 Aşağıdaki tabloda komutla kullanılabilecek seçenekler `catdb` listelenilir.  
  
|Catdb seçeneği|Açıklama|  
|------------------|-----------------|  
|`/d`|Varsayılan katalog veritabanının güncellendiğini belirtir. Ne `/d` seçenek ne `/g` de kullanılmazsa, Sign Tool sistem bileşenini ve sürücü veritabanını güncelleştirir.|  
|`/g`*REHBER*|Genel olarak benzersiz tanımlayıcı *GUID* tarafından tanımlanan katalog veritabanının güncelleştirilmelerini belirtir.|  
|`/r`|Belirtilen katalogları katalog veritabanından kaldırır. Bu seçenek belirtilmezse, İmza Aracı belirtilen katalogları katalog veritabanına ekler.|  
|`/u`|Benzersiz bir adın eklenen katalog dosyaları için otomatik olarak oluşturulduğunu belirtir. Gerekirse, katalog dosyaları var olan katalog dosyaları ile ad çakışmalarını önlemek için yeniden adlandırılır. Bu seçenek belirtilmezse, İmza Aracı eklenmekte olan katalogla aynı ada sahip tüm var olan katalogların üzerine yazar.|  
  
<a name="sign"></a>
## <a name="sign-command-options"></a>imza Komut Seçenekleri  
 Aşağıdaki tabloda komutla kullanılabilecek seçenekler `sign` listelenilir.  
  
|imza komut seçenekleri|Açıklama|  
|-------------------------|-----------------|  
|`/a`|En iyi imzalama sertifikasını otomatik olarak seçer. İmza Aracı, tüm belirtilen koşulları karşılayan tüm geçerli sertifikaları bulur ve en uzun süre geçerli olanı seçer. Bu seçenek yoksa, İmza Aracı yalnızca geçerli bir imza sertifikası bulmayı bekler.|  
|`/ac`  *Dosya*|İmza bloğuna *dosyadan* ek bir sertifika ekler.|  
|`/as`|Bu imzayı ekler. Birincil bir imza yoksa, bunun yerine bu imza birincil imza yapılır.|  
|`/c`  *CertTemplateName*|İmzalama sertifikasının Sertifika Şablon Adını (Microsoft uzantılı) belirtir.|  
|`/csp`  *CSPName*|Özel anahtar kapsayıcısı içeren şifreleme hizmet sağlayıcısını (CSP) belirtir.|  
|`/d`  *Desc*|İmzalı içeriğin açıklamasını belirtir.|  
|`/du`  *Url*|İmzalanmış içeriğin genişletilmiş açıklaması için Tek Düzen Kaynak Konum Belirleyicisi (URL) belirtir.|  
|`/f`  *SignCertFile*|Bir dosyadaki imza sertifikanı belirtir. Dosya Kişisel Bilgi Alışverişi (PFX) biçimindeyse ve bir `/p` parolayla korunuyorsa, parolayı belirtme seçeneğini kullanın. Dosya özel anahtarlar içermiyorsa, CSP `/csp` ve özel anahtar kapsayıcı adını belirtmek için seçenekleri `/kc` kullanın.|  
|`/fd`|Dosya imzalarını oluşturmak için kullanılacak dosya özet algoritmasını belirtir. Varsayılan, SHA1 değeridir.|  
|`/i`  *ıssuername*|İmzalayan sertifikayı verenin adını belirtir. Bu değer, tam yayınlayıcı adının bir alt dizesi olabilir.|  
|`/kc`  *PrivkeyContainerName*|Özel anahtar kapsayıcısı adını belirtir.|  
|`/n`  *Subjectname*|İmzalayan sertifika konusunun adını belirtir. Bu değer, tam konu adının bir alt dizesi olabilir.|  
|`/nph`|Destekleniyorsa, yürütülebilir dosyalar için sayfa karmalarını gizler. Varsayılan, wintrust.dll sürümü ve SIGNTOOL_PAGE_HASHES ortam değişkeni tarafından belirlenir. PE olmayan dosyalar için bu seçenek göz ardı edilir.|  
|`/p`  *Parola*|PFX dosyası açılırken kullanılacak parolayı belirtir. (PFX `/f` dosyasını belirtme seçeneğini kullanın.)|  
|`/p7`*Yol*|Bir Ortak Anahtar Şifreleme Standartları (PKCS) #7 dosyasının belirtilen her içerik dosyası için üretildiğini belirtir. PKCS #7 dosyaları *yol*\\*dosya adı*.p7 olarak adlandırılır.|  
|`/p7ce`*Değer*|İmzalanmış PKCS #7 içeriği için seçenekleri belirtir. İmzalanan içeriği PKCS #7 dosyasına yerleştirmek için *Değer'i* "Gömülü" olarak veya ayrılmış bir PKCS #7 dosyasının imzalı veri bölümünü oluşturmak için "Müstakil İmzalı Veriler"e ayarlayın. Seçenek `/p7ce` kullanılmazsa, imzalanan içerik varsayılan olarak katıştırılır.|  
|`/p7co`* \<OID>*|İmzalanmış PKCS #7 içeriğini tanımlayan nesne tanımlayıcısını (OID) belirtir.|  
|`/ph`|Destekleniyorsa, yürütülebilir dosyalar için sayfa karmaları oluşturur.|  
|`/r`  *RootSubjectName*|İmzalama sertifikasının bağlanması gerektiği kök sertifikası konusunun adını belirtir. Bu değer, kök sertifikasının tam konu adının bir alt dizesi olabilir.|  
|`/s`  *Storename*|Sertifika için arama yaparken açılacak depoyu belirtir. Bu seçenek belirtilmemişse, `My` mağaza açılır.|  
|`/sha1`  *Karma*|İmza sertifikanın SHA1 karmasını belirtir. Kalan anahtarlar tarafından belirtilen ölçütlere uygun birden çok sertifika olduğunda genellikle SHA1 karması belirtilir.|  
|`/sm`|Bir kullanıcı deposu yerine, makine deposu kullanıldığını belirtir.|  
|`/t`  *Url*|Zaman damgası sunucusunun URL'sini belirtir. Bu seçenek (veya) `/tr`yoksa, imzalanan dosya zaman damgalı olmayacaktır. Zaman damgası başarısız olduğunda bir uyarı üretilir. Bu seçenek `/tr` seçeneği ile kullanılamaz.|  
|`/td`  *alg*|RFC `/tr` 3161 zaman damgası sunucusu tarafından kullanılan bir özet algoritması istemek seçeneği ile kullanılır.|  
|`/tr`  *Url*|RFC 3161 zaman damgası sunucusunun URL'sini belirtir. Bu seçenek (veya) `/t`yoksa, imzalanan dosya zaman damgalı olmayacaktır. Zaman damgası başarısız olduğunda bir uyarı üretilir. Bu seçenek `/t` seçeneği ile kullanılamaz.|  
|`/u`  *Kullanım*|İmzalama sertifikasında hazır olması gereken gelişmiş anahtar kullanımını (EKU) belirtir. Kullanım değeri, OID veya dize ile belirtilebilir. "Kod İmzalama" varsayılan kullanım miktarıdır. (1.3.6.1.5.5.7.3.3).|  
|`/uw`|"Windows Sistem Bileşeni Doğrulaması" kullanımını belirtir. (1.3.6.1.4.1.311.10.3.6).|  
  
 Kullanım örnekleri için, [Dosyayı İmzalamak için SignTool'u kullanma'ya](/windows/desktop/SecCrypto/using-signtool-to-sign-a-file)bakın.  
  
<a name="TimeStamp"></a>
## <a name="timestamp-command-options"></a>TimeStamp Komut Seçenekleri  
 Aşağıdaki tabloda komutla kullanılabilecek seçenekler `TimeStamp` listelenilir.  
  
|Zaman Damgası seçeneği|Açıklama|  
|----------------------|-----------------|  
|`/p7`|Zaman damgaları PKCS #7 dosyaları.|  
|`/t`  *Url*|Zaman damgası sunucusunun URL'sini belirtir. Zaman damgası vurulan dosyanın önceden imzalanmış olması gerekir. Ya `/t` da `/tr` seçenek gereklidir.|  
|`/td`  *alg*|RFC 3161 zaman damgası sunucusu tarafından kullanılan bir özet algoritması ister. `/td``/tr` seçeneği ile kullanılır.|  
|`/tp`*dizin*|Zaman, *indeksteki*imzayı damgalar.|  
|`/tr`  *Url*|RFC 3161 zaman damgası sunucusunun URL'sini belirtir. Zaman damgası vurulan dosyanın önceden imzalanmış olması gerekir. Ya `/tr` da `/t` seçenek gereklidir.|  
  
 Kullanım örneği için bkz: [Daha Önce İmzalanmış Dosyalara Zaman Damgaları Ekleme.](/windows/desktop/SecCrypto/adding-time-stamps-to-previously-signed-files)  
  
<a name="Verify"></a>
## <a name="verify-command-options"></a>Komut Seçeneklerini Doğrulama  
  
|Seçeneği doğrulama|Açıklama|  
|-------------------|-----------------|  
|`/a`|Tüm yöntemlerin dosyayı doğrulamak için kullanılabileceğini belirtir. İlk olarak, dosyanın bir katalogda imzalanmış olup olmadığını belirlemek için katalog veritabanları aranır. Dosya herhangi bir katalogda imzalanmamışsa, İmza Aracı dosyanın katıştırılmış imzasını doğrulamayı dener. Katalogda oturum açmış veya açmamış dosyalar doğrulanırken bu seçenek önerilir. Bu dosyaların örnekleri arasında Windows dosyaları veya sürücüleri yer alır.|  
|`/ad`|Varsayılan katalog veritabanını kullanarak kataloğu bulur.|  
|`/ag`*CatDBGUID*|*CatDBGUID*tarafından tanımlanan katalog veritabanında kataloğu bulur.|  
|`/all`|Birden çok imza içeren bir dosyadaki tüm imzaları doğrular.|  
|`/as`|Sistem bileşeni (sürücü) katalog veritabanını kullanarak kataloğu bulur.|  
|`/c`*CatFile*|Katalog dosyası adını belirtir.|  
|`/d`|İmza Aracı'nın açıklama ve açıklama URL'sini yazdırması gerektiğini belirtir.|  
|`/ds`  *Dizin oluşturma*|Belirtilen bir konumda imzayı doğrular.|  
|`/hash`(`SHA1` `SHA256`&#124;)|Katalogdaki bir dosya ararken kullanmak için bir isteğe bağlı karma algoritmasını belirtir.|  
|`/kp`|Çekirdek modu sürücü imzalama ilkesi ile doğrulama gerçekleştirilmesi gerektiğini belirtir.|  
|`/ms`|Birden çok doğrulama mantığı kullanır. Bu, Windows 8 ve üzeri bir [WinVerifyTrust](/windows/desktop/api/wintrust/nf-wintrust-winverifytrust) çağrısının varsayılan davranışıdır.|  
|`/o`*Sürüm*|İşletim sistemi sürümüne göre dosyayı doğrular. *Sürüm* aşağıdaki formu vardır: *PlatformID*:*VerMajor*. *Verminor*. *Yapı Numarası*. *PlatformID,* numaralandırma <xref:System.PlatformID> üyesinin temel değerini temsil eder. **Önemli:**  `/o` Anahtarın kullanılması önerilir. `/o` Belirtilmemişse SignTool.exe beklenmeyen sonuçlar döndürebilir. Örneğin, `/o` anahtarı eklemezseniz, eski bir işletim sisteminde doğru doğru doğru doğrulayan sistem katalogları yeni bir işletim sisteminde doğru doğru doğrulamayabilir.|  
|`/p7`|PKCS #7 dosyalarını doğrular. Varolan ilkeler PKCS #7 doğrulaması için kullanılmaz. İmza denetlenir ve imzalama sertifikası zincir oluşturulur.|  
|`/pa`|Varsayılan Authenticode Doğrulama İlkesi kullanılması gerektiğini belirtir. `/pa` Seçenek belirtilmemişse, Oturum Açma Aracı Windows Sürücü Doğrulama İlkesi'ni kullanır. Bu seçenek `catdb` seçeneklerle kullanılamaz.|  
|`/pg`*PolitikaGUID*|GUID'ye göre doğrulama ilkesi belirtir. *İlke GUID* doğrulama ilkesinin ActionID'sine karşılık gelir. Bu seçenek `catdb` seçeneklerle kullanılamaz.|  
|`/ph`|İmza Aracı'nın sayfa karma değerlerini yazdırması ve doğrulaması gerektiğini belirtir.|  
|`/r`*RootSubjectName*|İmzalama sertifikasının bağlanması gerektiği kök sertifikası konusunun adını belirtir. Bu değer, kök sertifikasının tam konu adının bir alt dizesi olabilir.|  
|`/tw`|İmza zaman damgalı değilse bir uyarı oluşturulacağını belirtir.|  
  
 Kullanım örnekleri için, [Dosya İmzasını Doğrulamak için SignTool kullanma'ya](/windows/desktop/SecCrypto/using-signtool-to-verify-a-file-signature)bakın.  
  
## <a name="return-value"></a>Dönüş Değeri  
 İmza Aracı, sonlandırıldığında aşağıdaki çıkış kodlarından birini döndürür.  
  
|Çıkış kodu|Açıklama|  
|---------------|-----------------|  
|0|Yürütme başarılı oldu.|  
|1|Yürütme başarısız oldu.|  
|2|Yürütme uyarılarla tamamlandı.|  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, MyCatalogFileName.cat katalog dosyasını sistem bileşeni ve sürücü veritabanına ekler. Seçenek, `/u` '' adlı `MyCatalogFileName.cat`varolan bir katalog dosyasının değiştirilmesini önlemek için gerekirse benzersiz bir ad oluşturur.  
  
```console  
signtool catdb /v /u MyCatalogFileName.cat  
```  
  
 Aşağıdaki komut en iyi sertifikayı kullanarak bir dosyayı otomatik olarak imzalar.  
  
```console  
signtool sign /a MyFile.exe  
```  
  
 Aşağıdaki komut parola korumalı bir PFX dosyasında depolanan bir sertifika kullanarak bir dosyayı dijital olarak imzalar.  
  
```console  
signtool sign /f MyCert.pfx /p MyPassword MyFile.exe  
```  
  
 Aşağıdaki komut bir dosyayı dijital olarak imzalar ve zaman damgası oluşturur. Dosyayı imzalamak için kullanılan sertifika bir PFX dosyasında saklanır.  
  
```console  
signtool sign /f MyCert.pfx /t http://timestamp.digicert.com MyFile.exe  
```  
  
 Aşağıdaki komut, `My` mağazada bulunan ve özne adı `My Company Certificate`olan bir sertifika kullanarak bir dosyayı imzalar.  
  
```console  
signtool sign /n "My Company Certificate" MyFile.exe  
```  
  
 Aşağıdaki komut bir ActiveX denetimini imzalar ve kullanıcıdan denetimi yüklemesi istendiğinde Internet Explorer tarafından görüntülenen bilgileri sağlar.  
  
```console  
Signtool sign /f MyCert.pfx /d: "MyControl" /du http://www.example.com/MyControl/info.html MyControl.exe  
```  
  
 Aşağıdaki komut zaten dijital olarak imzalanmış bir dosya için zaman damgası oluşturur.  
  
```console  
signtool timestamp /t http://timestamp.digicert.com MyFile.exe  
```  
  
 Aşağıdaki komut bir dosyanın imzalandığını doğrular.  
  
```console  
signtool verify MyFile.exe  
```  
  
 Aşağıdaki komut bir katalogda imzalanmış olabilecek bir sistem dosyasını doğrular.  
  
```console  
signtool verify /a SystemFile.dll  
```  
  
 Aşağıdaki komut, . `MyCatalog.cat`  
  
```console  
signtool verify /c MyCatalog.cat SystemFile.dll  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
