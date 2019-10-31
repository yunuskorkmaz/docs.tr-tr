---
title: SignTool.exe (İmza Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- Sign tool
- SignTool.exe
ms.assetid: 0c25ff6c-bff3-422e-b017-146a3ee86cb9
ms.openlocfilehash: cb0aca3b527c16a7abf984952795a673948775dd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104639"
---
# <a name="signtoolexe-sign-tool"></a>SignTool.exe (İmza Aracı)
İmza aracı, dosyaları dijital imzalayan, dosyalardaki imzaları doğrulayan ve dosyalara zaman damgası veren bir komut satırı aracıdır.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
signtool [command] [options] [file_name | ...]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|`command`|Bir dosya üzerinde gerçekleştirilecek bir işlemi belirten dört komuttan biri (`catdb`, `sign`, `Timestamp`veya `Verify`). Her bir komutun açıklaması için sonraki tabloya bakın.|  
|`options`|Bir komutu değiştiren seçenek. Genel `/q` ve `/v` seçeneklerine ek olarak, her komut benzersiz bir seçenek kümesini destekler.|  
|`file_name`|İmzalanacak dosyanın yolu.|  
  
 Aşağıdaki komutlar İmza Aracı tarafından desteklenir. Her komut, ilgili bölümlerinde listelenen ayrı seçenekler kümesiyle kullanılır.  
  
|Komut|Açıklama|  
|-------------|-----------------|  
|`catdb`|Katalog veritabanına bir katalog dosyası ekler veya katalog veritabanından katalog dosyasını kaldırır. Katalog veritabanları, katalog dosyalarının otomatik araması için kullanılır ve GUID ile tanımlanır. `catdb` komutu tarafından desteklenen seçeneklerin bir listesi için, bkz. [CATDB komut seçenekleri](signtool-exe.md#catdb).|  
|`sign`|Dosyaları dijital olarak imzalar. Dijital imzalar, dosyaları izinsiz kullanıma karşı korur ve kullanıcıların bir imza sertifikası temelinde imzalayanı doğrulamasına olanak sağlar. `sign` komutu tarafından desteklenen seçeneklerin bir listesi için bkz. [Sign komut Options](signtool-exe.md#sign).|  
|`Timestamp`|Zaman damgaları dosyaları. `TimeStamp` komutu tarafından desteklenen seçeneklerin bir listesi için bkz. [timestamp komut Options](signtool-exe.md#TimeStamp).|  
|`Verify`|İmzalama sertifikasının güvenilir bir yetkili tarafından verilmiş, imzalama sertifikasının iptal edilmiş ve isteğe bağlı olarak imzalama sertifikasının belirli bir ilke için geçerli olup olmadığını belirleyerek dosyaların dijital imzasını doğrular. `Verify` komutu tarafından desteklenen seçeneklerin bir listesi için bkz. [komut seçeneklerini doğrulama](signtool-exe.md#Verify).|  
  
 Aşağıdaki seçenekler bütün İmza Aracı komutlarına uygulanır.  
  
|Genel seçenek|Açıklama|  
|-------------------|-----------------|  
|**anahtarın**|Komut başarıyla çalışırsa bir çıktı görüntülemez ve komut başarısız olursa en az çıktı görüntüler.|  
|**çıktıda**|Komutun başarıyla çalıştırıldığına veya başarısız olduğuna bakılmaksızın ayrıntılı çıktıyı görüntüler ve uyarı iletilerini görüntüler.|  
|**/debug**|Hata ayıklama bilgisini görüntüler.|  
  
<a name="catdb"></a>   
## <a name="catdb-command-options"></a>catdb Komut Seçenekleri  
 Aşağıdaki tabloda `catdb` komutuyla kullanılabilecek seçenekler listelenmektedir.  
  
|Catdb seçeneği|Açıklama|  
|------------------|-----------------|  
|`/d`|Varsayılan katalog veritabanının güncellendiğini belirtir. Ne `/d` ne de `/g` seçeneği kullanılırsa, Imza aracı sistem bileşenini ve sürücü veritabanını güncelleştirir.|  
|`/g` *GUID*|Genel benzersiz tanımlayıcı *GUID 'si* tarafından tanımlanan katalog veritabanının güncellenmediğini belirtir.|  
|`/r`|Belirtilen katalogları katalog veritabanından kaldırır. Bu seçenek belirtilmezse, İmza Aracı belirtilen katalogları katalog veritabanına ekler.|  
|`/u`|Benzersiz bir adın eklenen katalog dosyaları için otomatik olarak oluşturulduğunu belirtir. Gerekirse, katalog dosyaları var olan katalog dosyaları ile ad çakışmalarını önlemek için yeniden adlandırılır. Bu seçenek belirtilmezse, İmza Aracı eklenmekte olan katalogla aynı ada sahip tüm var olan katalogların üzerine yazar.|  
  
<a name="sign"></a>   
## <a name="sign-command-options"></a>imza Komut Seçenekleri  
 Aşağıdaki tabloda `sign` komutuyla kullanılabilecek seçenekler listelenmektedir.  
  
|imza komut seçenekleri|Açıklama|  
|-------------------------|-----------------|  
|`/a`|En iyi imzalama sertifikasını otomatik olarak seçer. İmza Aracı, tüm belirtilen koşulları karşılayan tüm geçerli sertifikaları bulur ve en uzun süre geçerli olanı seçer. Bu seçenek yoksa, İmza Aracı yalnızca geçerli bir imza sertifikası bulmayı bekler.|  
|`/ac`*dosyası*|*Dosyadan* imza bloğuna ek bir sertifika ekler.|  
|`/as`|Bu imzayı ekler. Birincil bir imza yoksa, bunun yerine bu imza birincil imza yapılır.|  
|*Certtemplatename* `/c`|İmzalama sertifikasının Sertifika Şablon Adını (Microsoft uzantılı) belirtir.|  
|`/csp`*Cspname*|Özel anahtar kapsayıcısı içeren şifreleme hizmet sağlayıcısını (CSP) belirtir.|  
|`/d`*DESC*|İmzalı içeriğin açıklamasını belirtir.|  
|`/du`*URL 'si*|İmzalanmış içeriğin genişletilmiş açıklaması için Tek Düzen Kaynak Konum Belirleyicisi (URL) belirtir.|  
|`/f`*Signsertifikadosyası*|Bir dosyadaki imza sertifikanı belirtir. Dosya kişisel bilgi değişimi (PFX) biçimindeyse ve bir parolayla korunuyorsa, parolayı belirtmek için `/p` seçeneğini kullanın. Dosya özel anahtarlar içermiyorsa, CSP ve özel anahtar kapsayıcısı adını belirtmek için `/csp` ve `/kc` seçeneklerini kullanın.|  
|`/fd`|Dosya imzalarını oluşturmak için kullanılacak dosya özet algoritmasını belirtir. Varsayılan, SHA1 değeridir.|  
|`/i`*IssuerName*|İmzalayan sertifikayı verenin adını belirtir. Bu değer, tam yayınlayıcı adının bir alt dizesi olabilir.|  
|`/kc`*Prıkeycontainername*|Özel anahtar kapsayıcısı adını belirtir.|  
|`/n`*SubjectName*|İmzalayan sertifika konusunun adını belirtir. Bu değer, tam konu adının bir alt dizesi olabilir.|  
|`/nph`|Destekleniyorsa, yürütülebilir dosyalar için sayfa karmalarını gizler. Varsayılan, wintrust.dll sürümü ve SIGNTOOL_PAGE_HASHES ortam değişkeni tarafından belirlenir. PE olmayan dosyalar için bu seçenek göz ardı edilir.|  
|`/p`*parolası*|PFX dosyası açılırken kullanılacak parolayı belirtir. (Bir PFX dosyası belirtmek için `/f` seçeneğini kullanın.)|  
|`/p7` *yolu*|Bir Ortak Anahtar Şifreleme Standartları (PKCS) #7 dosyasının belirtilen her içerik dosyası için üretildiğini belirtir. PKCS #7 dosyaları\\*filename*. P7 adlı *yoldur* .|  
|`/p7ce` *değeri*|İmzalanmış PKCS #7 içeriği için seçenekleri belirtir. İmzalı içeriği PKCS #7 dosyasına eklemek için *değeri* "Embedded" ya da ayrılmış bir PKCS #7 dosyasının imzalı veri bölümünü üretmek Için "DetachedSignedData" olarak ayarlayın. `/p7ce` seçeneği kullanılmazsa, imzalanmış içerik varsayılan olarak katıştırılır.|  
|`/p7co` *\<oıd >*|İmzalanmış PKCS #7 içeriğini tanımlayan nesne tanımlayıcısını (OID) belirtir.|  
|`/ph`|Destekleniyorsa, yürütülebilir dosyalar için sayfa karmaları oluşturur.|  
|`/r`*Rootsubjectname*|İmzalama sertifikasının bağlanması gerektiği kök sertifikası konusunun adını belirtir. Bu değer, kök sertifikasının tam konu adının bir alt dizesi olabilir.|  
|`/s`*StoreName*|Sertifika için arama yaparken açılacak depoyu belirtir. Bu seçenek belirtilmezse, `My` deposu açılır.|  
|`/sha1`*karması*|İmza sertifikanın SHA1 karmasını belirtir. Kalan anahtarlar tarafından belirtilen ölçütlere uygun birden çok sertifika olduğunda genellikle SHA1 karması belirtilir.|  
|`/sm`|Bir kullanıcı deposu yerine, makine deposu kullanıldığını belirtir.|  
|`/t`*URL 'si*|Zaman damgası sunucusunun URL'sini belirtir. Bu seçenek (veya `/tr`) yoksa, imzalanmış dosya zaman damgalı olmayacaktır. Zaman damgası başarısız olduğunda bir uyarı üretilir. Bu seçenek `/tr` seçeneğiyle kullanılamaz.|  
|`/td`*alg*|RFC 3161 zaman damgası sunucusu tarafından kullanılan bir Özet algoritması istemek için `/tr` seçeneği ile birlikte kullanılır.|  
|`/tr`*URL 'si*|RFC 3161 zaman damgası sunucusunun URL'sini belirtir. Bu seçenek (veya `/t`) yoksa, imzalanmış dosya zaman damgalı olmayacaktır. Zaman damgası başarısız olduğunda bir uyarı üretilir. Bu seçenek `/t` seçeneğiyle kullanılamaz.|  
|`/u`*kullanımı*|İmzalama sertifikasında hazır olması gereken gelişmiş anahtar kullanımını (EKU) belirtir. Kullanım değeri, OID veya dize ile belirtilebilir. "Kod İmzalama" varsayılan kullanım miktarıdır. (1.3.6.1.5.5.7.3.3).|  
|`/uw`|"Windows Sistem Bileşeni Doğrulaması" kullanımını belirtir. (1.3.6.1.4.1.311.10.3.6).|  
  
 Kullanım örnekleri için bkz. [dosyayı imzalamak Için SignTool kullanma](/windows/desktop/SecCrypto/using-signtool-to-sign-a-file).  
  
<a name="TimeStamp"></a>   
## <a name="timestamp-command-options"></a>TimeStamp Komut Seçenekleri  
 Aşağıdaki tabloda `TimeStamp` komutuyla kullanılabilecek seçenekler listelenmektedir.  
  
|Zaman Damgası seçeneği|Açıklama|  
|----------------------|-----------------|  
|`/p7`|Zaman damgaları PKCS #7 dosyaları.|  
|`/t`*URL 'si*|Zaman damgası sunucusunun URL'sini belirtir. Zaman damgası vurulan dosyanın önceden imzalanmış olması gerekir. `/t` ya da `/tr` seçeneği gereklidir.|  
|`/td`*alg*|RFC 3161 zaman damgası sunucusu tarafından kullanılan bir özet algoritması ister. `/td`, `/tr` seçeneğiyle kullanılır.|  
|`/tp` *dizini*|Zaman damgası *dizindeki*imza.|  
|`/tr`*URL 'si*|RFC 3161 zaman damgası sunucusunun URL'sini belirtir. Zaman damgası vurulan dosyanın önceden imzalanmış olması gerekir. `/tr` ya da `/t` seçeneği gereklidir.|  
  
 Kullanım örneği için, bkz. [önceden Imzalanmış dosyalara zaman damgaları ekleme](/windows/desktop/SecCrypto/adding-time-stamps-to-previously-signed-files).  
  
<a name="Verify"></a>   
## <a name="verify-command-options"></a>Komut Seçeneklerini Doğrulama  
  
|Seçeneği doğrulama|Açıklama|  
|-------------------|-----------------|  
|`/a`|Tüm yöntemlerin dosyayı doğrulamak için kullanılabileceğini belirtir. İlk olarak, dosyanın bir katalogda imzalanmış olup olmadığını belirlemek için katalog veritabanları aranır. Dosya herhangi bir katalogda imzalanmamışsa, İmza Aracı dosyanın katıştırılmış imzasını doğrulamayı dener. Katalogda oturum açmış veya açmamış dosyalar doğrulanırken bu seçenek önerilir. Bu dosyaların örnekleri arasında Windows dosyaları veya sürücüleri yer alır.|  
|`/ad`|Varsayılan katalog veritabanını kullanarak kataloğu bulur.|  
|`/ag` *Catdbguid*|Katalog veritabanında, *Catdbguid*tarafından tanımlanan kataloğu bulur.|  
|`/all`|Birden çok imza içeren bir dosyadaki tüm imzaları doğrular.|  
|`/as`|Sistem bileşeni (sürücü) katalog veritabanını kullanarak kataloğu bulur.|  
|`/c` *Catfile*|Katalog dosyası adını belirtir.|  
|`/d`|İmza Aracı'nın açıklama ve açıklama URL'sini yazdırması gerektiğini belirtir.|  
|`/ds`*dizini*|Belirtilen bir konumda imzayı doğrular.|  
|`/hash` (`SHA1`&#124;`SHA256`)|Katalogdaki bir dosya ararken kullanmak için bir isteğe bağlı karma algoritmasını belirtir.|  
|`/kp`|Çekirdek modu sürücü imzalama ilkesi ile doğrulama gerçekleştirilmesi gerektiğini belirtir.|  
|`/ms`|Birden çok doğrulama mantığı kullanır. Bu, [!INCLUDE[win8](../../../includes/win8-md.md)] ve üzeri bir [WinVerifyTrust](/windows/desktop/api/wintrust/nf-wintrust-winverifytrust) çağrısının varsayılan davranışıdır.|  
|`/o` *sürümü*|İşletim sistemi sürümüne göre dosyayı doğrular. *Sürüm* şu biçimdedir: *PlatformID*:*Verana*. *Küçük*. *BuildNumber*. *PlatformID* , bir <xref:System.PlatformID> numaralandırma üyesinin temel değerini temsil eder. **Önemli:**  `/o` anahtarın kullanımı önerilir. `/o` belirtilmezse, SignTool. exe beklenmeyen sonuçlar döndürebilir. Örneğin, `/o` anahtarını eklemezseniz, daha eski bir işletim sisteminde doğru şekilde doğrulayan sistem katalogları, daha yeni bir işletim sisteminde doğru şekilde doğrulanmayabilir.|  
|`/p7`|PKCS #7 dosyalarını doğrular. Varolan ilkeler PKCS #7 doğrulaması için kullanılmaz. İmza denetlenir ve imzalama sertifikası zincir oluşturulur.|  
|`/pa`|Varsayılan Authenticode Doğrulama İlkesi kullanılması gerektiğini belirtir. `/pa` seçeneği belirtilmezse, Imza aracı Windows sürücü doğrulama Ilkesi 'ni kullanır. Bu seçenek `catdb` seçenekleriyle kullanılamaz.|  
|`/pg` *Policyguid*|GUID'ye göre doğrulama ilkesi belirtir. *PolicyGUID* , doğrulama Ilkesinin ActionId 'sine karşılık gelir. Bu seçenek `catdb` seçenekleriyle kullanılamaz.|  
|`/ph`|İmza Aracı'nın sayfa karma değerlerini yazdırması ve doğrulaması gerektiğini belirtir.|  
|`/r` *Rootsubjectname*|İmzalama sertifikasının bağlanması gerektiği kök sertifikası konusunun adını belirtir. Bu değer, kök sertifikasının tam konu adının bir alt dizesi olabilir.|  
|`/tw`|İmza zaman damgalı değilse bir uyarı oluşturulacağını belirtir.|  
  
 Kullanım örnekleri için bkz. [Dosya Imzasını doğrulamak Için SignTool kullanma](/windows/desktop/SecCrypto/using-signtool-to-verify-a-file-signature).  
  
## <a name="return-value"></a>Dönüş Değeri  
 İmza Aracı, sonlandırıldığında aşağıdaki çıkış kodlarından birini döndürür.  
  
|Çıkış kodu|Açıklama|  
|---------------|-----------------|  
|0|Yürütme başarılı oldu.|  
|1\.|Yürütme başarısız oldu.|  
|2|Yürütme uyarılarla tamamlandı.|  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, MyCatalogFileName.cat katalog dosyasını sistem bileşeni ve sürücü veritabanına ekler. `/u` seçeneği, `MyCatalogFileName.cat`adlı mevcut bir katalog dosyasının değiştirilmesini engellemek için gerekliyse benzersiz bir ad üretir.  
  
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
  
 Aşağıdaki komut, `My Company Certificate`konu adına sahip `My` deposunda bulunan bir sertifikayı kullanarak bir dosyayı imzalar.  
  
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
  
 Aşağıdaki komut, `MyCatalog.cat`adlı bir katalogda imzalı bir sistem dosyasını doğrular.  
  
```console  
signtool verify /c MyCatalog.cat SystemFile.dll  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
