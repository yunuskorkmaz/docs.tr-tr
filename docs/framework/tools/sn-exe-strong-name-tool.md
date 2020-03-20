---
title: Sn.exe (Tanımlayıcı Ad Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- public keys, signing files
- Strong Name tool
- Sn.exe
- assemblies [.NET Framework], signing
- signing files
- strong-named assemblies, signing files
- key pairs for signing files
ms.assetid: c1d2b532-1b8e-4c7a-8ac5-53b801135ec6
ms.openlocfilehash: b5eee15a08dcae42263e06939c197ec0848816a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180311"
---
# <a name="snexe-strong-name-tool"></a>Sn.exe (Tanımlayıcı Ad Aracı)
Güçlü Ad aracı (Sn.exe) güçlü [adlara](../../standard/assembly/strong-named.md)sahip derlemeleri imzalamaya yardımcı olur. Sn.exe; temel yönetim, imza oluşturma ve imza doğrulaması için seçenekler sağlar.  
  
> [!WARNING]
> Güvenlik için güçlü isimlere güvenmeyin. Yalnızca benzersiz bir kimlik sağlarlar.

 Güçlü adlandırma ve güçlü adlandırılmış derlemeler hakkında daha fazla bilgi için Bkz. [Güçlü Adlandırılmış Derlemeler](../../standard/assembly/strong-named.md) ve [Nasıl Adlandırılır: Güçlü Bir İsimli Bir Meclis'i İmzalayın.](../../standard/assembly/sign-strong-name.md)  
  
 Tanımlayıcı Ad aracı Visual Studio ile birlikte otomatik olarak yüklenir. To start the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.  

> [!NOTE]
> 64 bit bilgisayarlarda Visual Studio için Geliştirici Komut Komut Ustem komutunu ve Visual Studio x64 Win64 Komut Istemi'ni kullanarak 64 bit sürümünü kullanarak Sn.exe'nin 32 bit sürümünü çalıştırın.
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
sn [-quiet][option [parameter(s)]]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`-a identityKeyPairFile signaturePublicKeyFile`|Kimlik <xref:System.Reflection.AssemblySignatureKeyAttribute> anahtarını bir dosyadan imza anahtarına geçirmek için veri üretir.|  
|`-ac identityPublicKeyFile identityKeyPairContainer signaturePublicKeyFile`|Kimlik <xref:System.Reflection.AssemblySignatureKeyAttribute> anahtarını anahtar kapsayıcısından imza anahtarına geçirmek için veri üretir.|  
|`-c [csp]`|Tanımlayıcı ad imzası için kullanılacak varsayılan şifreleme hizmeti sağlayıcısı (CSP) ayarlar. Bu ayar tüm bilgisayara uygulanır. Bir CSP adı belirtmezseniz, Sn.exe geçerli ayarı temizler.|  
|`-d container`|Belirtilen anahtar kapsayıcısını tanımlayıcı ad CSP'sinden siler.|  
|`-D assembly1 assembly2`|İki derlemenin yalnızca imza farkı olduğunu doğrular. Bu çoğunlukla, bir derleme farklı bir anahtar çifti ile yeniden imzalandıktan sonra denetim olarak kullanılır.|  
|`-e assembly outfile`|Ortak anahtarı *montajdan* ayıklar ve *dış dosyada saklar.*|  
|`-h`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|`-i infile container`|Belirtilen anahtar kapsayıcısında *infile* gelen anahtar çifti yükler. Anahtar kapsayıcısı, tanımlayıcı ad CSP'sinde bulunur.|  
|`-k [keysize] outfile`|Belirtilen boyutta <xref:System.Security.Cryptography.RSACryptoServiceProvider> yeni bir anahtar oluşturur ve belirtilen dosyaya yazar.  Hem ortak hem de özel anahtar dosyaya yazılır.<br /><br /> Bir anahtar boyutu belirtmezseniz, makinenizde Microsoft gelişmiş şifreleme sağlayıcısı yüklü ise varsayılan olarak 1,024-bit bir anahtar oluşturulur, yüklü değilse 512-bit anahtar oluşturulur.<br /><br /> *Anahtar boyutu* parametresi, Microsoft gelişmiş şifreleme sağlayıcısı yüklüyse, 384 bitten 16.384 bit'e kadar olan anahtar uzunluklarını 8 bitlik artışlarla destekler.  Makinenizde Microsoft temel şifreleme sağlayıcısı yüklüyse, 8 bitlik artışlarla 384 bit'ten 512 bit'e kadar olan anahtar uzunluklarını destekler.|  
|`-m [y|n]`|Anahtar kapsayıcılarının bilgisayara özgü mi yoksa kullanıcıya özgü mü olduğunu belirtir. *Y*, anahtar kapsayıcıları bilgisayara özgü olarak belirtirseniz. *n,* anahtar kapsayıcıları kullanıcıya özgü olarak belirtirseniz.<br /><br /> y ne n öğelerinden hiçbirini belirtmezseniz, bu seçenek geçerli ayarı görüntüler.|  
|`-o infile [outfile]`|Ortak anahtarı *dosyadan* ayıklar ve .csv dosyasında saklar. Ortak anahtarın her baytı virgülle ayrılır. Bu biçim, kaynak kodunda başlatılmış diziler olarak anahtarlara ilişkin sabit kodlama başvuruları için yararlıdır. Bir *dış dosya*belirtmezseniz, bu seçenek çıktıyı Pano'ya yerleştirir. **Not:**  Bu seçenek, girişin yalnızca ortak bir anahtar olduğunu doğrulamaz. Özel `infile` anahtara sahip bir anahtar çifti içeriyorsa, özel anahtar da ayıklanır.|  
|`-p infile outfile [hashalg]`|Ortak anahtarı *dosyadaki* anahtar çiftinden ayıklar ve *hashalg*tarafından belirtilen RSA algoritmasını isteğe bağlı olarak kullanarak *dış dosyada*saklar. Bu ortak anahtar, [Derleme Bağlayıcısı'nın (Al.exe)](al-exe-assembly-linker.md) **/delaysign+** ve **/keyfile** seçeneklerini kullanarak bir derlemeyi geciktirmek için kullanılabilir. Derleme gecikmeli imzalanmış olduğunda, yalnızca ortak anahtar derleme zamanında ayarlanır ve özel anahtarı bulunduğunda, daha sonra eklenecek bir imza için dosyada alan ayrılır.|  
|`-pc container outfile [hashalg]`|Ortak anahtarı *kapsayıcıdaki* anahtar çiftinden ayıklar ve *dış dosyada*saklar. *Hashalg* seçeneğini kullanırsanız, ortak anahtarı ayıklamak için RSA algoritması kullanılır.|  
|`-Pb [y|n]`|Tanımlayıcı ad atlama ilkesinin uygulatılıp uygulatılmayacağı belirtir. *Y*belirtirseniz, tam güven derlemeleri için güçlü adlar tam güvene <xref:System.AppDomain>yüklendiğinde doğrulanmaz. *N*belirtirseniz, güçlü adlar doğruluk için doğrulanır, ancak belirli bir güçlü ad için doğrulanmaz. Tam <xref:System.Security.Permissions.StrongNameIdentityPermission> güven meclisleri üzerinde hiçbir etkisi yoktur. Bir tanımlayıcı ad eşleştirmesi için kendi denetiminizi gerçekleştirmeniz gerekir.<br /><br /> Ne `y` de `n` belirtilmişse, bu seçenek geçerli ayarı görüntüler. Varsayılan değer: `y`. **Not:**  64 bit bilgisayarlarda, bu parametreyi hem 32 bit hem de Sn.exe'nin 64 bit örneklerinde ayarlamanız gerekir.|  
|`-q[uiet]`|Sessiz mod kullanılacağını belirtir; başarı iletilerinin görüntülenmesini engeller.|  
|`-R[a] assembly infile`|Daha önce imzalanmış veya gecikmeyle imzalanmış bir derlemeyi *dosyadaki*anahtar çiftiyle yeniden imzalar.<br /><br /> **-Ra** kullanılırsa, derlemedeki tüm dosyalar için hashes yeniden hesaplanır.|  
|`-Rc[a] assembly container`|Daha önce imzalanmış veya gecikme imzalı bir derlemeyi *konteynerdeki*anahtar çiftiyle yeniden imzalar.<br /><br /> **-Rca** kullanılırsa, derlemedeki tüm dosyalar için hashes yeniden hesaplanır.|  
|`-Rh assembly`|Derlemedeki tüm dosyaların karma değerlerini yeniden hesaplar.|  
|`-t[p] infile`|*Dosyada*depolanan ortak anahtarın belirteci görüntülenir. *Dosya* içeriği daha önce bir anahtar çifti dosyasından **-p**kullanarak oluşturulan ortak bir anahtar olmalıdır.  Belirteci doğrudan anahtar çifti dosyasından ayıklamak için **-t[p]** seçeneğini kullanmayın.<br /><br /> Sn.exe, ortak anahtardan bir karma işlevini kullanarak belirteci hesaplar. Alandan kazanmak için, ortak dil çalışma zamanı, tanımlayıcı bir ada sahip derlemeye bağımlılık kaydederken ortak anahtar belirteçlerini başka bir derlemenin başvurusunun parçası olarak bildirimde depolar. **-tp** seçeneği belirteci ek olarak ortak anahtarı görüntüler. <xref:System.Reflection.AssemblySignatureKeyAttribute> Öznitelik derlemeye uygulandıysa, belirteç kimlik anahtarı içindir ve karma algoritmanın adı ve kimlik anahtarı görüntülenir.<br /><br /> Bu seçeneğin derleme imzasını doğrulamadığını ve güven kararları vermek için kullanılmaması gerektiğini unutmayın.  Bu seçenek yalnızca ham ortak anahtar belirteci verilerini görüntüler.|  
|`-T[p] assembly`|Derleme için ortak anahtar belirteci *görüntüler.* *Derleme,* derleme bildirimi içeren bir dosyanın adı olmalıdır.<br /><br /> Sn.exe, ortak anahtardan bir karma işlevini kullanarak belirteci hesaplar. Alandan kazanmak için, çalışma zamanı, tanımlayıcı bir ada sahip derlemeye bağımlılık kaydederken ortak anahtar belirteçlerini başka bir derlemenin başvurusunun parçası olarak bildirimde depolar. **-Tp** seçeneği belirteci ek olarak ortak anahtarı görüntüler. <xref:System.Reflection.AssemblySignatureKeyAttribute> Öznitelik derlemeye uygulandıysa, belirteç kimlik anahtarı içindir ve karma algoritmanın adı ve kimlik anahtarı görüntülenir.<br /><br /> Bu seçeneğin derleme imzasını doğrulamadığını ve güven kararları vermek için kullanılmaması gerektiğini unutmayın.  Bu seçenek yalnızca ham ortak anahtar belirteci verilerini görüntüler.|  
|`-TS assembly infile`|Dosyadaki anahtar çifti ile imzalı veya kısmen imzalanmış *derlemeyi* test *eder.*|  
|`-TSc assembly container`|Anahtar *kapsayıcı*kapsayıcısında anahtar çifti ile imzalı veya kısmen imzalanmış *montaj* test imzalar.|
|`-v assembly`|*Derleme, derleme* bildirimi içeren bir dosyanın adı olduğu *derlemedeki*güçlü adı doğrular.|  
|`-vf assembly`|*Derlemedeki* güçlü adı doğrular. **-v** seçeneğinin **aksine-vf-** **Vr** seçeneği kullanılarak devre dışı bırakılmış olsa bile doğrulamayı zorlar.|  
|`-Vk regfile.reg assembly [userlist] [infile]`|Doğrulamayı atlama için belirtilen derlemeyi kaydetmek üzere kullanabileceğiniz bir kayıt girdileri (.reg) dosyası oluşturur. **-Vr** seçeneği için geçerli olan montaj adlandırma kuralları **-Vk** için de geçerlidir. *Kullanıcı listesi* ve *dosya seçenekleri* hakkında bilgi için **–Vr** seçeneğine bakın.|  
|`-Vl`|Bu bilgisayardaki tanımlayıcı ad doğrulamasının geçerli ayarlarını listeler.|  
|`-Vr  assembly [userlist] [infile]`|Doğrulama atlama için *montaj* kaydeder. İsteğe bağlı olarak, doğrulama atlamanın geçerli olacağı kullanıcı adlarının virgülle ayrılmış listesini belirtebilirsiniz. *Dosya yı*belirtirseniz, doğrulama etkin kalır, ancak *infiledeki* ortak anahtar doğrulama işlemlerinde kullanılır. Belirtilen güçlü ada sahip tüm derlemeleri kaydetmek için * \*, güçlü ad* şeklinde *montaj* belirtebilirsiniz. *Strongname*için, ortak anahtarın belirteç biçimini temsil eden hexadecimal basamaklar dizesini belirtin. Ortak anahtar belirteci görüntülemek için **-t** ve **-T** seçeneklerine bakın. **Dikkat:**  Bu seçeneği yalnızca geliştirme sırasında kullanın. Doğrulama atlama listesine bir derleme eklemek güvenlik açığı oluşturur. Kötü amaçlı bir derleme, kimliğini gizlemek için doğrulama atlama listesine eklenmiş derlemenin tam olarak belirtilmiş derleme adını (derleme adı, sürüm, kültür ve ortak anahtar belirteci) kullanabilir. Bu, kötü amaçlı derlemenin de doğrulamayı atlamasına izin verir.|  
|||  
|`-Vu  assembly`|Doğrulama atlama için *derlemeyi* unregisters. **-Vr** için geçerli olan montaj adlandırma için aynı kurallar **-Vu**için geçerlidir.|  
|`-Vx`|Doğrulama atlama girişlerinin tümünü kaldırır.|  
|`-?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
> [!NOTE]
> Tüm Sn.exe seçenekler büyük/küçük harfe duyarlıdır ve araç tarafından tanınması için tam olarak gösterildiği gibi yazılmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 **-R** ve **-Rc** seçenekleri, gecikme imzalı derlemeler için yararlıdır. Bu senaryoda, derleme zamanında yalnızca ortak anahtar ayarlanmıştır, imzalama ise daha sonra, özel anahtar tanındığında yapılır.  
  
> [!NOTE]
> Kayıt defteri gibi korumalı kaynaklara yazan parametreler (örneğin, –**Vr)** için SN.exe'yi yönetici olarak çalıştırın.  
  
Güçlü Ad aracı, `AT_SIGNATURE` ortak/özel anahtar çiftleri algoritma tanımlayıcısı ile oluşturulur varsayar. `AT_KEYEXCHANGE` Algoritma yla oluşturulan ortak/özel anahtar çiftleri bir hata oluşturur.

## <a name="examples"></a>Örnekler  
 Aşağıdaki komut yeni, rasgele bir anahtar çifti `keyPair.snk`oluşturur ve onu .  
  
```console  
sn -k keyPair.snk  
```  
  
 Aşağıdaki komut, anahtarı `keyPair.snk` güçlü ad `MyContainer` CSP'de kapsayıcıda saklar.  
  
```console  
sn -i keyPair.snk MyContainer  
```  
  
 Aşağıdaki komut ortak anahtarı ayıklar `keyPair.snk` ve `publicKey.snk`'de saklar.  
  
```console  
sn -p keyPair.snk publicKey.snk  
```  
  
 Aşağıdaki komut, ortak anahtarı ve 'de bulunan ortak `publicKey.snk`anahtarın belirteci'ni görüntüler.  
  
```console  
sn -tp publicKey.snk  
```  
  
 Aşağıdaki komut derlemeyi `MyAsm.dll`doğrular.  
  
```console  
sn -v MyAsm.dll  
```  
  
 Aşağıdaki komut varsayılan `MyContainer` CSP'den silinir.  
  
```console  
sn -d MyContainer  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](al-exe-assembly-linker.md)
- [Tanımlayıcı Adlı Derlemeler](../../standard/assembly/strong-named.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
