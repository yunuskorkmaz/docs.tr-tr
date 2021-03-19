---
title: SignTool.exe (İmza Aracı)
description: Imza aracı SignTool.exe hakkında bilgi edinin. Bu komut satırı aracı, dosyaları dijital olarak imzalar, dosyalardaki imzaları doğrular ve dosyaları zaman damgalarına uygular.
ms.date: 03/30/2017
helpviewer_keywords:
- Sign tool
- SignTool.exe
ms.assetid: 0c25ff6c-bff3-422e-b017-146a3ee86cb9
ms.openlocfilehash: 3b4bfa70ed91f98ae49b6df3a5a29f68b30f1e0a
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653861"
---
# <a name="signtoolexe-sign-tool"></a>SignTool.exe (İmza Aracı)

İmza aracı, dosyaları dijital imzalayan, dosyalardaki imzaları doğrulayan ve dosyalara zaman damgası veren bir komut satırı aracıdır.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için [Visual studio Geliştirici komut istemi veya Visual Studio Geliştirici PowerShell](/visualstudio/ide/reference/command-prompt-powershell)kullanın.

> [!Note]  
> Windows 10 SDK, Windows 10 HLK, Windows 10 WDK ve Windows 10 ADK **derlemeleri 20236 ve üzeri** bir Özet algoritması belirtilmesini gerektirir. SignTool `sign` komutu, `/fd` sırasıyla imzalama ve zaman damgası oluşturma sırasında **Dosya Özet algoritması** ve `/td` **timestamp Özet algoritması** seçeneğinin belirtilmesini gerektirir. `/fd`İmza sırasında belirtilmemişse ve zaman damgası sırasında belirtilmemişse bir uyarı (hata kodu 0, başlangıçta) oluşturulur `/td` . SignTool 'in sonraki sürümlerinde, uyarı bir hata olur. SHA256 önerilir ve sektör tarafından SHA1 'den daha güvenli olarak değerlendirilir.  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
signtool [command] [options] [file_name | ...]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Description|  
|--------------|-----------------|  
|`command`|`catdb` `sign` `Timestamp` `Verify` Bir dosya üzerinde gerçekleştirilecek bir işlemi belirten dört komuttan biri (,, veya). Her bir komutun açıklaması için sonraki tabloya bakın.|  
|`options`|Bir komutu değiştiren seçenek. Genel ve seçeneklere ek olarak `/q` `/v` , her komut benzersiz bir seçenek kümesini destekler.|  
|`file_name`|İmzalanacak dosyanın yolu.|  
  
 Aşağıdaki komutlar İmza Aracı tarafından desteklenir. Her komut, ilgili bölümlerinde listelenen ayrı seçenekler kümesiyle kullanılır.  
  
|Komut|Açıklama|  
|-------------|-----------------|  
|`catdb`|Katalog veritabanına bir katalog dosyası ekler veya katalog veritabanından katalog dosyasını kaldırır. Katalog veritabanları, katalog dosyalarının otomatik araması için kullanılır ve GUID ile tanımlanır. Komutu tarafından desteklenen seçeneklerin bir listesi için `catdb` bkz. [CATDB komut seçenekleri](signtool-exe.md#catdb).|  
|`sign`|Dosyaları dijital olarak imzalar. Dijital imzalar, dosyaları izinsiz kullanıma karşı korur ve kullanıcıların bir imza sertifikası temelinde imzalayanı doğrulamasına olanak sağlar. Komutu tarafından desteklenen seçeneklerin bir listesi için `sign` bkz. [Imza komutu seçenekleri](signtool-exe.md#sign).|  
|`Timestamp`|Zaman damgaları dosyaları. Komutu tarafından desteklenen seçeneklerin bir listesi için `TimeStamp` bkz. [timestamp komut Options](signtool-exe.md#TimeStamp).|  
|`Verify`|İmzalama sertifikasının güvenilir bir yetkili tarafından verilmiş, imzalama sertifikasının iptal edilmiş ve isteğe bağlı olarak imzalama sertifikasının belirli bir ilke için geçerli olup olmadığını belirleyerek dosyaların dijital imzasını doğrular. Komutu tarafından desteklenen seçeneklerin bir listesi için `Verify` bkz. [komut seçeneklerini doğrulama](signtool-exe.md#Verify).|  
  
 Aşağıdaki seçenekler bütün İmza Aracı komutlarına uygulanır.  
  
|Genel seçenek|Description|  
|-------------------|-----------------|  
|**anahtarın**|Komut başarıyla çalışırsa bir çıktı görüntülemez ve komut başarısız olursa en az çıktı görüntüler.|  
|**çıktıda**|Komutun başarıyla çalıştırıldığına veya başarısız olduğuna bakılmaksızın ayrıntılı çıktıyı görüntüler ve uyarı iletilerini görüntüler.|  
|**komutun**|Hata ayıklama bilgisini görüntüler.|  
  
<a name="catdb"></a>

## <a name="catdb-command-options"></a>catdb Komut Seçenekleri  

 Aşağıdaki tabloda, komutuyla kullanılabilecek seçenekler listelenmektedir `catdb` .  
  
|Catdb seçeneği|Description|  
|------------------|-----------------|  
|`/d`|Varsayılan katalog veritabanının güncellendiğini belirtir. `/d`Ne ne de `/g` seçenek kullanılırsa, imza aracı sistem bileşenini ve sürücü veritabanını güncelleştirir.|  
|`/g`*GUID*|Genel benzersiz tanımlayıcı *GUID 'si* tarafından tanımlanan katalog veritabanının güncellenmediğini belirtir.|  
|`/r`|Belirtilen katalogları katalog veritabanından kaldırır. Bu seçenek belirtilmezse, İmza Aracı belirtilen katalogları katalog veritabanına ekler.|  
|`/u`|Benzersiz bir adın eklenen katalog dosyaları için otomatik olarak oluşturulduğunu belirtir. Gerekirse, katalog dosyaları var olan katalog dosyaları ile ad çakışmalarını önlemek için yeniden adlandırılır. Bu seçenek belirtilmezse, İmza Aracı eklenmekte olan katalogla aynı ada sahip tüm var olan katalogların üzerine yazar.|  
  
<a name="sign"></a>

## <a name="sign-command-options"></a>imza Komut Seçenekleri  

 Aşağıdaki tabloda, komutuyla kullanılabilecek seçenekler listelenmektedir `sign` .  
  
|imza komut seçenekleri|Description|  
|-------------------------|-----------------|  
|`/a`|En iyi imzalama sertifikasını otomatik olarak seçer. İmza Aracı, tüm belirtilen koşulları karşılayan tüm geçerli sertifikaları bulur ve en uzun süre geçerli olanı seçer. Bu seçenek yoksa, İmza Aracı yalnızca geçerli bir imza sertifikası bulmayı bekler.|  
|`/ac`  *dosyasýný*|*Dosyadan* imza bloğuna ek bir sertifika ekler.|  
|`/as`|Bu imzayı ekler. Birincil bir imza yoksa, bunun yerine bu imza birincil imza yapılır.|  
|`/c`  *CertTemplateName*|İmzalama sertifikasının Sertifika Şablon Adını (Microsoft uzantılı) belirtir.|  
|`/csp`  *CSPName*|Özel anahtar kapsayıcısı içeren şifreleme hizmet sağlayıcısını (CSP) belirtir.|  
|`/d`  *Kümesinde*|İmzalı içeriğin açıklamasını belirtir.|  
|`/du`  *URL*|İmzalanmış içeriğin genişletilmiş açıklaması için Tek Düzen Kaynak Konum Belirleyicisi (URL) belirtir.|  
|`/f`  *Signsertifikadosyası*|Bir dosyadaki imza sertifikanı belirtir. Dosya kişisel bilgi değişimi (PFX) biçimindeyse ve bir parolayla korunuyorsa, `/p` parolayı belirtmek için seçeneğini kullanın. Dosya özel anahtarlar içermiyorsa, `/csp` `/kc` CSP ve özel anahtar kapsayıcısı adını belirtmek için ve seçeneklerini kullanın.|  
|`/fd`|Dosya imzalarını oluşturmak için kullanılacak dosya özet algoritmasını belirtir. </br> **Note:** `/fd` İmza sırasında anahtar sağlanmazsa bir uyarı oluşturulur. Varsayılan algoritma SHA1, ancak SHA256 önerilir.|
|`/fd`  *Sunucunuzda certhash*|*Sunucunuzda certhash* dizesinin belirtilmesi, İmza sertifikasında kullanılan algoritmaya varsayılan olarak uygulanır. </br> **Note:** Yalnızca Windows 10 Kit derleme 20236 ve üzeri sürümlerde kullanılabilir.|  
|`/i`  *IssuerName*|İmzalayan sertifikayı verenin adını belirtir. Bu değer, tam yayınlayıcı adının bir alt dizesi olabilir.|  
|`/kc`  *Prıkeycontainername*|Özel anahtar kapsayıcısı adını belirtir.|  
|`/n`  *SubjectName*|İmzalayan sertifika konusunun adını belirtir. Bu değer, tam konu adının bir alt dizesi olabilir.|  
|`/nph`|Destekleniyorsa, yürütülebilir dosyalar için sayfa karmalarını gizler. Varsayılan, wintrust.dll sürümü ve SIGNTOOL_PAGE_HASHES ortam değişkeni tarafından belirlenir. PE olmayan dosyalar için bu seçenek göz ardı edilir.|  
|`/p`  *Parola*|PFX dosyası açılırken kullanılacak parolayı belirtir. ( `/f` BIR pfx dosyası belirtmek için seçeneğini kullanın.)|  
|`/p7` *Yol*|Bir Ortak Anahtar Şifreleme Standartları (PKCS) #7 dosyasının belirtilen her içerik dosyası için üretildiğini belirtir. PKCS #7 dosyaları  \\ *filename*. P7 olarak adlandırılır.|  
|`/p7ce` *Değer*|İmzalanmış PKCS #7 içeriği için seçenekleri belirtir. İmzalı içeriği PKCS #7 dosyasına eklemek için *değeri* "Embedded" ya da ayrılmış bir PKCS #7 dosyasının imzalı veri bölümünü üretmek Için "DetachedSignedData" olarak ayarlayın. `/p7ce`Seçenek kullanılmazsa, imzalanmış içerik varsayılan olarak katıştırılır.|  
|`/p7co` *\<OID>*|İmzalanmış PKCS #7 içeriğini tanımlayan nesne tanımlayıcısını (OID) belirtir.|  
|`/ph`|Destekleniyorsa, yürütülebilir dosyalar için sayfa karmaları oluşturur.|  
|`/r`  *RootSubjectName*|İmzalama sertifikasının bağlanması gerektiği kök sertifikası konusunun adını belirtir. Bu değer, kök sertifikasının tam konu adının bir alt dizesi olabilir.|  
|`/s`  *StoreName*|Sertifika için arama yaparken açılacak depoyu belirtir. Bu seçenek belirtilmemişse `My` mağaza açılır.|  
|`/sha1`  *Yla*|İmza sertifikanın SHA1 karmasını belirtir. Kalan anahtarlar tarafından belirtilen ölçütlere uygun birden çok sertifika olduğunda genellikle SHA1 karması belirtilir.|  
|`/sm`|Bir kullanıcı deposu yerine, makine deposu kullanıldığını belirtir.|  
|`/t`  *URL*|Zaman damgası sunucusunun URL'sini belirtir. Bu seçenek (veya `/tr` ) yoksa, imzalanmış dosya zaman damgalı olmayacaktır. Zaman damgası başarısız olduğunda bir uyarı üretilir. Bu seçenek, seçeneğiyle birlikte kullanılamaz `/tr` .|  
|`/td`  *doğrulama*|`/tr`RFC 3161 zaman damgası sunucusu tarafından kullanılan bir Özet algoritması isteme seçeneğiyle birlikte kullanılır. </br> **Note:** Zaman `/td` damgalama sırasında anahtar sağlanmazsa bir uyarı oluşturulur. Varsayılan algoritma SHA1 'dir, ancak SHA256 önerilir. <br/> `/td`Anahtar, `/tr` öncesinde değil, anahtardan sonra bildirilmelidir. `/td`Anahtar anahtardan önce bildirilirse `/tr` , döndürülen zaman DAMGASı amaçlanan SHA256 ALGORITMASı yerine SHA1 algoritmasından olur. |
|`/tr`  *URL*|RFC 3161 zaman damgası sunucusunun URL'sini belirtir. Bu seçenek (veya `/t` ) yoksa, imzalanmış dosya zaman damgalı olmayacaktır. Zaman damgası başarısız olduğunda bir uyarı üretilir. Bu seçenek, seçeneğiyle birlikte kullanılamaz `/t` .|
|`/u`  *Kullanım*|İmzalama sertifikasında hazır olması gereken gelişmiş anahtar kullanımını (EKU) belirtir. Kullanım değeri, OID veya dize ile belirtilebilir. "Kod İmzalama" varsayılan kullanım miktarıdır. (1.3.6.1.5.5.7.3.3).|  
|`/uw`|"Windows Sistem Bileşeni Doğrulaması" kullanımını belirtir. (1.3.6.1.4.1.311.10.3.6).|  
  
 Kullanım örnekleri için bkz. [dosyayı imzalamak Için SignTool kullanma](/windows/desktop/SecCrypto/using-signtool-to-sign-a-file).  
  
<a name="TimeStamp"></a>

## <a name="timestamp-command-options"></a>TimeStamp Komut Seçenekleri  

 Aşağıdaki tabloda, komutuyla kullanılabilecek seçenekler listelenmektedir `TimeStamp` .  
  
|Zaman Damgası seçeneği|Description|  
|----------------------|-----------------|  
|`/p7`|Zaman damgaları PKCS #7 dosyaları.|  
|`/t`  *URL*|Zaman damgası sunucusunun URL'sini belirtir. Zaman damgası vurulan dosyanın önceden imzalanmış olması gerekir. Ya da `/t` `/tr` seçeneği gereklidir.|  
|`/td`  *doğrulama*|`/tr`RFC 3161 zaman damgası sunucusu tarafından kullanılan bir Özet algoritması isteme seçeneğiyle birlikte kullanılır. </br> **Note:** Zaman `/td` damgalama sırasında anahtar sağlanmazsa bir uyarı oluşturulur. Varsayılan algoritma SHA1 'dir, ancak SHA256 önerilir. <br/> `/td`Anahtar, `/tr` öncesinde değil, anahtardan sonra bildirilmelidir. `/td`Anahtar anahtardan önce bildirilirse `/tr` , döndürülen zaman DAMGASı amaçlanan SHA256 ALGORITMASı yerine SHA1 algoritmasından olur. |
|`/tp`*Dizin*|Zaman damgası *dizindeki* imza.|  
|`/tr`  *URL*|RFC 3161 zaman damgası sunucusunun URL'sini belirtir. Zaman damgası vurulan dosyanın önceden imzalanmış olması gerekir. Ya da `/tr` `/t` seçeneği gereklidir.|  
  
 Kullanım örneği için, bkz. [önceden Imzalanmış dosyalara zaman damgaları ekleme](/windows/desktop/SecCrypto/adding-time-stamps-to-previously-signed-files).  
  
<a name="Verify"></a>

## <a name="verify-command-options"></a>Komut Seçeneklerini Doğrulama  
  
|Seçeneği doğrulama|Description|  
|-------------------|-----------------|  
|`/a`|Tüm yöntemlerin dosyayı doğrulamak için kullanılabileceğini belirtir. İlk olarak, dosyanın bir katalogda imzalanmış olup olmadığını belirlemek için katalog veritabanları aranır. Dosya herhangi bir katalogda imzalanmamışsa, İmza Aracı dosyanın katıştırılmış imzasını doğrulamayı dener. Katalogda oturum açmış veya açmamış dosyalar doğrulanırken bu seçenek önerilir. Bu dosyaların örnekleri arasında Windows dosyaları veya sürücüleri yer alır.|  
|`/ad`|Varsayılan katalog veritabanını kullanarak kataloğu bulur.|  
|`/ag`*Catdbguid*|Katalog veritabanında, *Catdbguid* tarafından tanımlanan kataloğu bulur.|  
|`/all`|Birden çok imza içeren bir dosyadaki tüm imzaları doğrular.|  
|`/as`|Sistem bileşeni (sürücü) katalog veritabanını kullanarak kataloğu bulur.|  
|`/c`*Catfile*|Katalog dosyası adını belirtir.|  
|`/d`|İmza Aracı'nın açıklama ve açıklama URL'sini yazdırması gerektiğini belirtir.|  
|`/ds`  *Dizin oluşturma*|Belirtilen bir konumda imzayı doğrular.|  
|`/hash` ( `SHA1`&#124;`SHA256` )|Katalogdaki bir dosya ararken kullanmak için bir isteğe bağlı karma algoritmasını belirtir.|  
|`/kp`|Çekirdek modu sürücü imzalama ilkesi ile doğrulama gerçekleştirilmesi gerektiğini belirtir.|  
|`/ms`|Birden çok doğrulama mantığı kullanır. Bu, Windows 8 ve üzeri üzerinde bir [WinVerifyTrust](/windows/desktop/api/wintrust/nf-wintrust-winverifytrust) çağrısının varsayılan davranışıdır.|  
|`/o` *Sürüm*|İşletim sistemi sürümüne göre dosyayı doğrular. *Sürüm* şu biçimdedir: *PlatformID*:*Verana*. *Küçük*. *BuildNumber*. *PlatformID* , bir numaralandırma üyesinin temel değerini temsil eder <xref:System.PlatformID> . **Önemli:**  `/o` Anahtarın kullanımı önerilir. `/o`Belirtilmezse, SignTool.exe beklenmeyen sonuçlar döndürebilir. Örneğin, `/o` anahtarı eklemezseniz, daha eski bir işletim sisteminde doğru şekilde doğrulayan sistem katalogları, daha yeni bir işletim sisteminde doğru şekilde doğrulanmayabilir.|  
|`/p7`|PKCS #7 dosyalarını doğrular. Varolan ilkeler PKCS #7 doğrulaması için kullanılmaz. İmza denetlenir ve imzalama sertifikası zincir oluşturulur.|  
|`/pa`|Varsayılan Authenticode Doğrulama İlkesi kullanılması gerektiğini belirtir. `/pa`Seçenek belirtilmemişse, Imza aracı Windows sürücü doğrulama ilkesi 'ni kullanır. Bu seçenek seçeneklerle birlikte kullanılamaz `catdb` .|  
|`/pg`*Policyguid*|GUID'ye göre doğrulama ilkesi belirtir. *PolicyGUID* , doğrulama Ilkesinin ActionId 'sine karşılık gelir. Bu seçenek seçeneklerle birlikte kullanılamaz `catdb` .|  
|`/ph`|İmza Aracı'nın sayfa karma değerlerini yazdırması ve doğrulaması gerektiğini belirtir.|  
|`/r`*Rootsubjectname*|İmzalama sertifikasının bağlanması gerektiği kök sertifikası konusunun adını belirtir. Bu değer, kök sertifikasının tam konu adının bir alt dizesi olabilir.|  
|`/tw`|İmza zaman damgalı değilse bir uyarı oluşturulacağını belirtir.|  
  
 Kullanım örnekleri için bkz. [Dosya Imzasını doğrulamak Için SignTool kullanma](/windows/desktop/SecCrypto/using-signtool-to-verify-a-file-signature).  
  
## <a name="return-value"></a>Dönüş Değeri  

 İmza Aracı, sonlandırıldığında aşağıdaki çıkış kodlarından birini döndürür.  
  
|Çıkış kodu|Açıklama|  
|---------------|-----------------|  
|0|Yürütme başarılı oldu.|  
|1|Yürütme başarısız oldu.|  
|2|Yürütme uyarılarla tamamlandı.|  

## <a name="examples"></a>Örnekler  

 Aşağıdaki komut, MyCatalogFileName.cat katalog dosyasını sistem bileşeni ve sürücü veritabanına ekler. Bu `/u` seçenek, adlı mevcut bir katalog dosyasının değiştirilmesini engellemek için gerekliyse benzersiz bir ad oluşturur `MyCatalogFileName.cat` .  
  
```console  
signtool catdb /v /u MyCatalogFileName.cat  
```  
  
 Aşağıdaki komut en iyi sertifikayı kullanarak bir dosyayı otomatik olarak imzalar.  
  
```console
signtool sign /a /fd SHA256 MyFile.exe
```

 Aşağıdaki komut parola korumalı bir PFX dosyasında depolanan bir sertifika kullanarak bir dosyayı dijital olarak imzalar.  
  
```console  
signtool sign /f MyCert.pfx /p MyPassword /fd SHA256 MyFile.exe
```  
  
 Aşağıdaki komut bir dosyayı dijital olarak imzalar ve zaman damgası oluşturur. Dosyayı imzalamak için kullanılan sertifika bir PFX dosyasında saklanır.  
  
```console  
signtool sign /f MyCert.pfx /t http://timestamp.digicert.com /fd SHA256 MyFile.exe
```  
  
 Aşağıdaki komut, konu adı olan depoda bulunan bir sertifikayı kullanarak bir dosyayı imzalar `My` `My Company Certificate` .  
  
```console  
signtool sign /n "My Company Certificate" /fd SHA256 MyFile.exe
```  
  
 Aşağıdaki komut bir ActiveX denetimini imzalar ve kullanıcıdan denetimi yüklemesi istendiğinde Internet Explorer tarafından görüntülenen bilgileri sağlar.  
  
```console  
Signtool sign /f MyCert.pfx /d: "MyControl" /du http://www.example.com/MyControl/info.html /fd SHA256 MyControl.exe
```  
  
 Aşağıdaki komut zaten dijital olarak imzalanmış bir dosya için zaman damgası oluşturur.  
  
```console  
signtool timestamp /t http://timestamp.digicert.com MyFile.exe
```  

Aşağıdaki komut, RFC 3161 zaman damgası sunucusu kullanarak bir dosyayı bir dosya damgasıdır.  
  
```console  
signtool timestamp /tr http://timestamp.digicert.com /td SHA256 MyFile.exe
```  
  
 Aşağıdaki komut bir dosyanın imzalandığını doğrular.  
  
```console  
signtool verify MyFile.exe  
```  
  
 Aşağıdaki komut bir katalogda imzalanmış olabilecek bir sistem dosyasını doğrular.  
  
```console  
signtool verify /a SystemFile.dll  
```  
  
 Aşağıdaki komut adlı bir katalogda imzalı bir sistem dosyasını doğrular `MyCatalog.cat` .  
  
```console  
signtool verify /c MyCatalog.cat SystemFile.dll  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Geliştirici komut satırı kabukları](/visualstudio/ide/reference/command-prompt-powershell)
