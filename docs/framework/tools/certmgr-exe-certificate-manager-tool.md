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
ms.openlocfilehash: 716513bdcf3ac1b8a2b2b29b23a8dc25a86a0d1c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044805"
---
# <a name="certmgrexe-certificate-manager-tool"></a>Certmgr.exe (Sertifika Yönetim Aracı)
Sertifika Yöneticisi aracı (Certmgr.exe) sertifikaları, sertifika güven listelerini (CTL) ve sertifika iptal listelerini (CRL) yönetir.  
  
 Sertifika Yöneticisi Visual Studio ile birlikte otomatik olarak yüklenir. Aracı başlatmak için [komut istemlerini](developer-command-prompt-for-vs.md)kullanın.  
  
> [!NOTE]
> Sertifika Yöneticisi aracı (Certmgr.exe) bir komut satırı aracıyken, Sertifikalar (Certmgr.msc) bir Microsoft Yönetim Konsolu (MMC) ek bileşenidir. Certmgr. msc genellikle Windows sistem dizininde bulunduğu için, komut satırına girildiğinde `certmgr` , Visual Studio için geliştirici komut istemi açmış olsanız bile Sertifikalar MMC ek bileşenini yükleyebilirsiniz. Bu, PATH ortam değişkeninde ek bileşene olan yol Sertifika Yöneticisi aracına olan yoldan önce geldiği için gerçekleşir. Eğer bu sorunla karşılaşırsanız, çalıştırılabilir öğenin yolunu belirterek Certmgr.exe komutlarını yürütebilirsiniz.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).  
  
 X. 509.440 sertifikalarına genel bakış için bkz. [sertifikalarla çalışma](../wcf/feature-details/working-with-certificates.md).  
  
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
|*destinationStorename*|Çıktı sertifika deposu veya dosyası.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/Add**|Bir sertifika deposuna sertifikalar, CTL'ler ve CRL'ler ekler.|  
|**/All**|**/Add**ile kullanıldığında tüm girdileri ekler. **/Del&lt**ile kullanıldığında tüm girdileri siler. **/Add** veya **/del&lt** seçenekleri olmadan kullanıldığında tüm girişleri görüntüler. **/All** seçeneği **/PUT**ile kullanılamaz.|  
|**/c**|**/Add**ile kullanıldığında sertifikaları ekler. **/Del&lt**ile kullanıldığında sertifikaları siler. , **/PUT**ile kullanıldığında sertifikaları kaydeder. **/Add**, **/del&lt**veya **/PUT** seçeneği olmadan kullanıldığında sertifikaları görüntüler.|  
|**/CRL**|**/Add**Ile kullanıldığında CRL 'leri ekler. **/Del&lt**Ile kullanıldığında CRL 'leri siler. , **/PUT**Ile kullanıldığında CRL 'leri kaydeder. **/Add**, **/del&lt**veya **/PUT** seçeneği olmadan kullanıldığında CRL 'leri görüntüler.|  
|**/CTL**|**/Add**Ile kullanıldığında CTL ekler. **/Del&lt**Ile kullanıldığında CTL 'leri siler. **/PUT**Ile kullanıldığında CTL 'leri kaydeder. **/Add**, **/del&lt**veya **/PUT** seçeneği olmadan kullanıldığında CTL 'leri görüntüler.|  
|**/del&lt**|Bir sertifika deposundan sertifikaları, CTL'leri ve CRL'leri siler.|  
|**/e** *EncodingType*|Sertifika kodlama türünü belirtir. Varsayılan, `X509_ASN_ENCODING` değeridir.|  
|**/f** *dwFlags*|Depo açık bayrağını belirtir. Bu, **CertOpenStore**'A geçirilen *dwFlags* parametresidir. Varsayılan değer CERT_SYSTEM_STORE_CURRENT_USER değeridir. Bu seçenek yalnızca **/y** seçeneği kullanılırsa değerlendirilir.|  
|**/h** [**ELP**]|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/n** *Nam*|Eklenecek, silinecek veya kaydedilecek sertifika için ortak adı belirtir. Bu seçenek yalnızca sertifikalarla kullanılabilir; CTL'ler veya CRL'ler ile kullanılamaz.|  
|**/Put**|Bir sertifika deposundan bir X.509 sertifikasını, CTL'yi veya CRL'yi dosyaya kaydeder. Dosya X.509 biçiminde kaydedilir. Dosyayı PKCS #7 biçiminde kaydetmek için **/PUT** seçeneğiyle birlikte **/7** seçeneğini kullanabilirsiniz. **/PUT** seçeneğinin arkasından **/c**, **/CTL**veya **/CRL**gelmelidir. **/All** seçeneği **/PUT**ile kullanılamaz.|  
|**/r** *konum*|Sistem deposu için kayıt defteri konumunu tanımlar. Bu seçenek yalnızca **/s** seçeneğini belirtirseniz değerlendirilir. *konum* aşağıdakilerden biri olmalıdır:<br /><br /> -   `currentUser`sertifika deposunun HKEY_CURRENT_USER anahtarı altında olduğunu gösterir. Bu varsayılandır.<br />-   `localMachine`sertifika deposunun HKEY_LOCAL_MACHINE anahtarı altında olduğunu gösterir.|  
|**/s**|Sertifika deposunun bir sistem deposu olduğunu gösterir. Bu seçeneği belirtmezseniz, mağaza bir **StoreFile**olarak kabul edilir.|  
|**/SHA1** *sha1Hash*|Eklenecek, silinecek veya kaydedilecek sertifikanın, CTL'nin veya CRL'nin SHA1 karmasını belirtir.|  
|**çıktıda**|Ayrıntılı modu belirtir; sertifikalar, CTL'ler ve CRL'ler hakkında ayrıntılı bilgi görüntüler. Bu seçenek **/Add**, **/del&lt**veya **/PUT** seçenekleriyle birlikte kullanılamaz.|  
|**/y** *sağlayıcı*|Depo sağlayıcısı adını sağlar.|  
|**/7**|Hedef depoyu bir PKCS #7 nesnesi olarak kaydeder.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Certmgr.exe aşağıdaki temel işlevleri gerçekleştirir:  
  
- Sertifikaları, CTL'leri ve CRL'leri konsolda görüntüler.  
  
- Bir sertifika deposuna sertifikalar, CTL'ler ve CRL'ler ekler.  
  
- Bir sertifika deposundan sertifikaları, CTL'leri ve CRL'leri siler.  
  
- Bir sertifika deposundan bir X.509 sertifikasını, CTL'yi veya CRL'yi dosyaya kaydeder.  
  
 Certmgr. exe iki tür sertifika deposu ile birlikte kullanılabilir: **StoreFile** ve sistem deposu. Sertifika deposu türünü belirtmek gerekli değildir: Certmgr.exe depo türünü tanımlayarak uygun işlemleri gerçekleştirebilir.  
  
 Certmgr.exe'yi hiçbir seçenek olmadan belirtmek, komut satırından kullanılabilen sertifika yönetim görevlerine yardımcı olan bir GUI'ye sahip certmgr.msc ek bileşenini yönetir. GUI; sertifikaları, CTL'leri ve CRL'leri diskinizden bir sertifika deposuna kopyalayan bir içeri aktarma sihirbazı sağlar.  
  
 Aşağıdaki kodu derleyerek ve çalıştırarak, `sourceStorename` ve `destinationStorename` parametreleri için X509Certificate mağazaların adlarını bulabilirsiniz.  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 Sertifikalar hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](../wcf/feature-details/working-with-certificates.md).  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, ayrıntılı çıktıyla çağrılan `my` bir varsayılan sistem deposunu görüntüler.  
  
```console  
certmgr /v /s my  
```  
  
 Aşağıdaki komut adlı bir dosyadaki `myFile.ext` tüm sertifikaları adlı `newFile.ext`yeni bir dosyaya ekler.  
  
```console  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 Aşağıdaki komut, sertifikayı `testcert.cer` `my` sistem deposuna adlı bir dosyaya ekler.  
  
```console  
certmgr /add /c testcert.cer /s my  
```  
  
 Aşağıdaki komut, sertifikayı Kök sertifika deposuna adlı `TrustedCert.cer` bir dosyaya ekler.  
  
```console  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 Aşağıdaki komut, `myCert` `my` sistem deposunda ortak ada sahip bir sertifikayı adlı `newCert.cer`bir dosyaya kaydeder.  
  
```console  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 Aşağıdaki komut, `my` sistem deposundaki tüm CTL 'leri siler ve elde edilen depoyu adlı `newStore.str`bir dosyaya kaydeder.  
  
```console  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 Aşağıdaki komut, bir sertifikayı `my` dosyadaki `newFile`sistem deposuna kaydeder. `my` İçine`newFile`koymak için sertifika numarasını girmeniz istenir.  
  
```console  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [MakeCert. exe (sertifika oluşturma aracı)](/windows/desktop/SecCrypto/makecert)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
