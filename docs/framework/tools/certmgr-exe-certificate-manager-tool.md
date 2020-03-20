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
ms.openlocfilehash: 06fe3a78d0b19720d4f83111980b88806312205f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73129870"
---
# <a name="certmgrexe-certificate-manager-tool"></a>Certmgr.exe (Sertifika Yönetim Aracı)
Sertifika Yöneticisi aracı (Certmgr.exe) sertifikaları, sertifika güven listelerini (CTL) ve sertifika iptal listelerini (CRL) yönetir.  
  
 Sertifika Yöneticisi Visual Studio ile birlikte otomatik olarak yüklenir. Aracı başlatmak için [Komut İstemleri'ni](developer-command-prompt-for-vs.md)kullanın.  
  
> [!NOTE]
> Sertifika Yöneticisi aracı (Certmgr.exe) bir komut satırı aracıyken, Sertifikalar (Certmgr.msc) bir Microsoft Yönetim Konsolu (MMC) ek bileşenidir. Certmgr.msc genellikle Windows System dizininde bulunduğundan, `certmgr` komut satırına girmek, Visual Studio için Geliştirici Komut Komut Ustemkomutu Komut Istemi'ni açmış olsanız bile MMC sertifikalarını yükleyebilir. Bu, PATH ortam değişkeninde ek bileşene olan yol Sertifika Yöneticisi aracına olan yoldan önce geldiği için gerçekleşir. Eğer bu sorunla karşılaşırsanız, çalıştırılabilir öğenin yolunu belirterek Certmgr.exe komutlarını yürütebilirsiniz.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.  
  
 X.509 sertifikalarına genel bakış için [bkz.](../wcf/feature-details/working-with-certificates.md)  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*sourceStorename*|Eklenecek, silinecek, kaydedilecek veya görüntülenecek varolan sertifikaları, CTL'leri veya CRL'leri içeren sertifika deposu. Bu bir depo dosyası veya sistem deposu olabilir.|  
|*hedefMağazaname*|Çıktı sertifika deposu veya dosyası.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/ekle**|Bir sertifika deposuna sertifikalar, CTL'ler ve CRL'ler ekler.|  
|**/tümü**|/ekle ile kullanıldığında tüm girişleri **ekler.** **/del**ile kullanıldığında tüm girişleri siler. **/ekle** veya **/del** seçenekleri olmadan kullanıldığında tüm girişleri görüntüler. **/tümü** seçeneği **/put**ile kullanılamaz.|  
|**/c**|**/ekle ile**kullanıldığında sertifika ekler. **/del**ile kullanıldığında sertifikaları siler. **/put**ile kullanıldığında sertifikaları kaydeder. **/ekle**, **/del**, veya **/put** seçeneği olmadan kullanıldığında sertifikaları görüntüler.|  
|**/CRL**|**/ekle ile**kullanıldığında CRL ekler. **/del**ile kullanıldığında CRL'leri siler. **/put**ile kullanıldığında CRL'leri kaydeder. **/add**, **/del**, veya **/put** seçeneği olmadan kullanıldığında CRL'leri görüntüler.|  
|**/CTL**|**/ekle ile**kullanıldığında CTL ekler. **/del**ile kullanıldığında CTL'leri siler. **/put**ile kullanıldığında CTL'leri kaydeder. **/add**, **/del**, veya **/put** seçeneği olmadan kullanıldığında CTL'leri görüntüler.|  
|**/del**|Bir sertifika deposundan sertifikaları, CTL'leri ve CRL'leri siler.|  
|**/e** *kodlamaTürü*|Sertifika kodlama türünü belirtir. Varsayılan değer: `X509_ASN_ENCODING`.|  
|**/f** *dwBayraklar*|Depo açık bayrağını belirtir. Bu **CertOpenStore**geçirilen *dwFlags* parametresi. Varsayılan değer CERT_SYSTEM_STORE_CURRENT_USER değeridir. Bu seçenek yalnızca **/y** seçeneği kullanılırsa kabul edilir.|  
|**/h**[**elp**]|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/n** *nam*|Eklenecek, silinecek veya kaydedilecek sertifika için ortak adı belirtir. Bu seçenek yalnızca sertifikalarla kullanılabilir; CTL'ler veya CRL'ler ile kullanılamaz.|  
|**/koymak**|Bir sertifika deposundan bir X.509 sertifikasını, CTL'yi veya CRL'yi dosyaya kaydeder. Dosya X.509 biçiminde kaydedilir. Dosyayı PKCS #7 formatında kaydetmek için **/put** seçeneği ile **/7** seçeneğini kullanabilirsiniz. **/put** seçeneği **/c**, **/CTL**, veya **/CRL**tarafından izlenmelidir. **/tümü** seçeneği **/put**ile kullanılamaz.|  
|**/r** *konumu*|Sistem deposu için kayıt defteri konumunu tanımlar. Bu seçenek yalnızca **/s** seçeneğini belirtirseniz kabul edilir. *konum* aşağıdakilerden biri olmalıdır:<br /><br /> -   `currentUser`sertifika deposunun HKEY_CURRENT_USER anahtarının altında olduğunu gösterir. Bu varsayılandır.<br />-   `localMachine`sertifika deposunun HKEY_LOCAL_MACHINE anahtarının altında olduğunu gösterir.|  
|**/s**|Sertifika deposunun bir sistem deposu olduğunu gösterir. Bu seçeneği belirtmezseniz, mağaza **StoreFile**olarak kabul edilir.|  
|**/sha1** *sha1Hash*|Eklenecek, silinecek veya kaydedilecek sertifikanın, CTL'nin veya CRL'nin SHA1 karmasını belirtir.|  
|**/v**|Ayrıntılı modu belirtir; sertifikalar, CTL'ler ve CRL'ler hakkında ayrıntılı bilgi görüntüler. Bu seçenek **/add**, **/del**, veya **/put** seçenekleriyle kullanılamaz.|  
|**/y** *sağlayıcı*|Depo sağlayıcısı adını sağlar.|  
|**/7**|Hedef depoyu bir PKCS #7 nesnesi olarak kaydeder.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Certmgr.exe aşağıdaki temel işlevleri gerçekleştirir:  
  
- Sertifikaları, CTL'leri ve CRL'leri konsolda görüntüler.  
  
- Bir sertifika deposuna sertifikalar, CTL'ler ve CRL'ler ekler.  
  
- Bir sertifika deposundan sertifikaları, CTL'leri ve CRL'leri siler.  
  
- Bir sertifika deposundan bir X.509 sertifikasını, CTL'yi veya CRL'yi dosyaya kaydeder.  
  
 Certmgr.exe iki tür sertifika deposuyla çalışır: **StoreFile** ve sistem mağazası. Sertifika deposu türünü belirtmek gerekli değildir: Certmgr.exe depo türünü tanımlayarak uygun işlemleri gerçekleştirebilir.  
  
 Certmgr.exe'yi hiçbir seçenek olmadan belirtmek, komut satırından kullanılabilen sertifika yönetim görevlerine yardımcı olan bir GUI'ye sahip certmgr.msc ek bileşenini yönetir. GUI; sertifikaları, CTL'leri ve CRL'leri diskinizden bir sertifika deposuna kopyalayan bir içeri aktarma sihirbazı sağlar.  
  
 Aşağıdaki kodu derleyip çalıştırarak X509Certificate `destinationStorename` depolarının adlarını ve parametreleri `sourceStorename` bulabilirsiniz.  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 Sertifikalar hakkında daha fazla bilgi için [bkz.](../wcf/feature-details/working-with-certificates.md)  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, ayrıntılı çıktı `my` ile adlandırılan varsayılan bir sistem deposu görüntüler.  
  
```console  
certmgr /v /s my  
```  
  
 Aşağıdaki komut, adı verilen `myFile.ext` `newFile.ext`yeni bir dosyaya çağrılan bir dosyadaki tüm sertifikaları ekler.  
  
```console  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 Aşağıdaki komut, sertifikayı sistem `testcert.cer` deposuna `my` adlı bir dosyaya ekler.  
  
```console  
certmgr /add /c testcert.cer /s my  
```  
  
 Aşağıdaki komut, sertifikayı kök `TrustedCert.cer` sertifika deposuna adlı bir dosyaya ekler.  
  
```console  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 Aşağıdaki komut, `myCert` `my` sistem deposunda ortak adı olan bir sertifikayı . `newCert.cer`  
  
```console  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 Aşağıdaki komut, sistem deposundaki `my` tüm CTL'leri siler ve ortaya `newStore.str`çıkan depoyu .  
  
```console  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 Aşağıdaki komut, dosyadaki `my` `newFile`sistem deposunda bir sertifika kaydeder. Koymak için sertifika numarasını `my` girmeniz `newFile`istenir.  
  
```console  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Makecert.exe (Sertifika Oluşturma Aracı)](/windows/desktop/SecCrypto/makecert)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
