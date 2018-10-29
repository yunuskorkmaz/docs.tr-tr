---
title: Certmgr.exe (Sertifika Yönetim Aracı)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates, managing
- CRLs
- certificate trust lists
- Certmgr.exe
- Certificate Manager tool
- CTLs
- certificate revocation lists
ms.assetid: 7e953b43-1374-4bbc-814f-53ca1b6b52bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ad1cbd9da3a6b55dbb23eaf97c10e6090077fd8
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198490"
---
# <a name="certmgrexe-certificate-manager-tool"></a>Certmgr.exe (Sertifika Yönetim Aracı)
Sertifika Yöneticisi aracı (Certmgr.exe) sertifikaları, sertifika güven listelerini (CTL) ve sertifika iptal listelerini (CRL) yönetir.  
  
 Sertifika Yöneticisi Visual Studio ile birlikte otomatik olarak yüklenir. Aracı'nı başlatmak için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
> [!NOTE]
>  Sertifika Yöneticisi aracı (Certmgr.exe) bir komut satırı aracıyken, Sertifikalar (Certmgr.msc) bir Microsoft Yönetim Konsolu (MMC) ek bileşenidir. Certmgr.msc genellikle Windows sistem dizininde bulduğundan girme `certmgr` Visual Studio komut istemi açmış olsanız bile sertifikalar MMC ek bileşenini komut satırında yükleyebilir. Bu, PATH ortam değişkeninde ek bileşene olan yol Sertifika Yöneticisi aracına olan yoldan önce geldiği için gerçekleşir. Eğer bu sorunla karşılaşırsanız, çalıştırılabilir öğenin yolunu belirterek Certmgr.exe komutlarını yürütebilirsiniz.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 X.509 sertifikalarına genel bakış için bkz. [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*sourceStorename*|Eklenecek, silinecek, kaydedilecek veya görüntülenecek varolan sertifikaları, CTL'leri veya CRL'leri içeren sertifika deposu. Bu bir depo dosyası veya sistem deposu olabilir.|  
|*destinationStorename*|Çıktı sertifika deposu veya dosyası.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/ add**|Bir sertifika deposuna sertifikalar, CTL'ler ve CRL'ler ekler.|  
|**/ all**|İle kullanıldığında tüm girdileri ekler **/ add**. İle kullanıldığında tüm girdileri siler **/del**. Olmadan kullanıldığında tüm girdileri görüntüler **/ add** veya **/del** seçenekleri. **/All** seçeneği ile kullanılamaz **/put**.|  
|**/c**|İle kullanıldığında sertifikaları ekler **/ add**. İle kullanıldığında sertifikaları siler **/del**. İle kullanıldığında sertifikaları kaydeder **/put**. Görüntüler olmadan kullanıldığında sertifikaları **/ add**, **/del**, veya **/put** seçeneği.|  
|**/ CRL**|İle kullanıldığında CRL'leri ekler **/ add**. İle kullanıldığında CRL'leri siler **/del**. İle kullanıldığında CRL'leri kaydeder **/put**. Görüntüler olmadan kullanıldığında CRL'leri **/ add**, **/del**, veya **/put** seçeneği.|  
|**/ CTL**|İle kullanıldığında CTL'leri ekler **/ add**. İle kullanıldığında CTL'leri siler **/del**. İle kullanıldığında CTL'leri kaydeder **/put**. Görüntüler olmadan kullanıldığında CTL'leri **/ add**, **/del**, veya **/put** seçeneği.|  
|**/ DEL**|Bir sertifika deposundan sertifikaları, CTL'leri ve CRL'leri siler.|  
|**/e** *encodingType*|Sertifika kodlama türünü belirtir. Varsayılan, `X509_ASN_ENCODING` değeridir.|  
|**/f** *CertOpenStore*|Depo açık bayrağını belirtir. Bu *CertOpenStore* geçirilen **Dwflags**. Varsayılan değer CERT_SYSTEM_STORE_CURRENT_USER değeridir. Bu seçenek yalnızca değerlendirilir **/y** seçeneği kullanılır.|  
|**/h**[**elp**]|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/n** *adı*|Eklenecek, silinecek veya kaydedilecek sertifika için ortak adı belirtir. Bu seçenek yalnızca sertifikalarla kullanılabilir; CTL'ler veya CRL'ler ile kullanılamaz.|  
|**/ put**|Bir sertifika deposundan bir X.509 sertifikasını, CTL'yi veya CRL'yi dosyaya kaydeder. Dosya X.509 biçiminde kaydedilir. Kullanabileceğiniz **/7** seçeneğini **/put** dosyayı PKCS #7 biçiminde kaydetmek için seçeneği. **/Put** seçeneği tarafından gelmelidir **/c**, **/CTL**, veya **/CRL**. **/All** seçeneği ile kullanılamaz **/put**.|  
|**/r** *konumu*|Sistem deposu için kayıt defteri konumunu tanımlar. Bu seçenek yalnızca belirtirseniz değerlendirilir **/s** seçeneği. *Konum* aşağıdakilerden biri olmalıdır:<br /><br /> -   `currentUser` Sertifika deposunun HKEY_CURRENT_USER anahtarı altında olduğunu gösterir. Bu varsayılandır.<br />-   `localMachine` Sertifika deposunun HKEY_LOCAL_MACHINE anahtarı altında olduğunu gösterir.|  
|**/s**|Sertifika deposunun bir sistem deposu olduğunu gösterir. Bu seçeneği belirtmezseniz, depo olarak kabul edilir bir **StoreFile**.|  
|**{1** *sha1Hash*|Eklenecek, silinecek veya kaydedilecek sertifikanın, CTL'nin veya CRL'nin SHA1 karmasını belirtir.|  
|**/v**|Ayrıntılı modu belirtir; sertifikalar, CTL'ler ve CRL'ler hakkında ayrıntılı bilgi görüntüler. Bu seçenek kullanılamaz **/ add**, **/del**, veya **/put** seçenekleri.|  
|**/y** *sağlayıcısı*|Depo sağlayıcısı adını sağlar.|  
|**/7**|Hedef depoyu bir PKCS #7 nesnesi olarak kaydeder.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Certmgr.exe aşağıdaki temel işlevleri gerçekleştirir:  
  
-   Sertifikaları, CTL'leri ve CRL'leri konsolda görüntüler.  
  
-   Bir sertifika deposuna sertifikalar, CTL'ler ve CRL'ler ekler.  
  
-   Bir sertifika deposundan sertifikaları, CTL'leri ve CRL'leri siler.  
  
-   Bir sertifika deposundan bir X.509 sertifikasını, CTL'yi veya CRL'yi dosyaya kaydeder.  
  
 Certmgr.exe iki tür sertifika ile çalışır: **StoreFile** ve sistem deposu. Sertifika deposu türünü belirtmek gerekli değildir: Certmgr.exe depo türünü tanımlayarak uygun işlemleri gerçekleştirebilir.  
  
 Certmgr.exe'yi hiçbir seçenek olmadan belirtmek, komut satırından kullanılabilen sertifika yönetim görevlerine yardımcı olan bir GUI'ye sahip certmgr.msc ek bileşenini yönetir. GUI; sertifikaları, CTL'leri ve CRL'leri diskinizden bir sertifika deposuna kopyalayan bir içeri aktarma sihirbazı sağlar.  
  
 İçin X509Certificate depolarının adlarını bulabilirsiniz `sourceStorename` ve `destinationStorename` derleyerek ve aşağıdaki kodu çalıştırarak parametreleri.  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 Sertifikalar hakkında daha fazla bilgi için bkz. [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut adı verilen bir varsayılan sistem deposunu görüntüler `my` ayrıntılı çıktıyla.  
  
```  
certmgr /v /s my  
```  
  
 Aşağıdaki komut, tüm sertifikaları adlı bir dosyaya ekler. `myFile.ext` adlı yeni bir dosyaya `newFile.ext`.  
  
```  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 Aşağıdaki komut, adlı dosyadaki sertifikayı ekler `testcert.cer` için `my` sistem deposu.  
  
```  
certmgr /add /c testcert.cer /s my  
```  
  
 Aşağıdaki komut, adlı dosyadaki sertifikayı ekler `TrustedCert.cer` kök sertifika deposuna.  
  
```  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 Aşağıdaki komut ortak adına sahip bir sertifika kaydeder `myCert` içinde `my` adlı bir dosyaya sistem deposu `newCert.cer`.  
  
```  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 Aşağıdaki komut, tüm CTL'leri siler `my` sistem deposu ve adlı bir dosya elde edilen depoyu kaydeder `newStore.str`.  
  
```  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 Aşağıdaki komutu bir sertifikada kaydeder `my` sistem deposu dosyasındaki `newFile`. Sertifika numarasını girmeniz istenir `my` yerleştirmek için `newFile`.  
  
```  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araçlar](../../../docs/framework/tools/index.md)  
 [MakeCert.exe (sertifika oluşturma aracı)](/windows/desktop/SecCrypto/makecert)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
