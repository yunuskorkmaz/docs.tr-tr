---
title: Sn.exe (Tanımlayıcı Ad Aracı)
description: Güçlü ad aracını Sn.exe kullanmaya başlayın. Derlemeleri tanımlayıcı adlarla imzalayın. Anahtarları yönetin ve imzaları oluşturun ve doğrulayın.
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
ms.openlocfilehash: 8f10dab9b395640e46cb9bf3ca468b8f6bb2bc1b
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517197"
---
# <a name="snexe-strong-name-tool"></a>Sn.exe (Tanımlayıcı Ad Aracı)
Tanımlayıcı ad Aracı (Sn.exe), derlemelerin [güçlü adlarla](../../standard/assembly/strong-named.md)imzalanmanıza yardımcı olur. Sn.exe; temel yönetim, imza oluşturma ve imza doğrulaması için seçenekler sağlar.  
  
> [!WARNING]
> Güvenlik için tanımlayıcı adlara güvenmeyin. Yalnızca benzersiz bir kimlik sağlarlar.

 Tanımlayıcı adlandırma ve tanımlayıcı adlı derlemeler hakkında daha fazla bilgi için bkz. Strong [-adlandırılmış derlemeler](../../standard/assembly/strong-named.md) ve [nasıl yapılır: bir derlemeyi güçlü bir adla imzalama](../../standard/assembly/sign-strong-name.md).  
  
 Tanımlayıcı Ad aracı Visual Studio ile birlikte otomatik olarak yüklenir. Aracı başlatmak için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).  

> [!NOTE]
> 64 bit bilgisayarlarda, Visual Studio x64 Win64 komut Istemi kullanarak Visual Studio Geliştirici Komut İstemi ve 64 bit sürümünü kullanarak Sn.exe 32 bit sürümünü çalıştırın.
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
sn [-quiet][option [parameter(s)]]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`-a identityKeyPairFile signaturePublicKeyFile`|<xref:System.Reflection.AssemblySignatureKeyAttribute>Kimlik anahtarını bir dosyadan imza anahtarına geçirmek için veri üretir.|  
|`-ac identityPublicKeyFile identityKeyPairContainer signaturePublicKeyFile`|<xref:System.Reflection.AssemblySignatureKeyAttribute>Kimlik anahtarını bir anahtar kapsayıcısından imza anahtarına geçirmek için veri üretir.|  
|`-c [csp]`|Tanımlayıcı ad imzası için kullanılacak varsayılan şifreleme hizmeti sağlayıcısı (CSP) ayarlar. Bu ayar tüm bilgisayara uygulanır. Bir CSP adı belirtmezseniz, Sn.exe geçerli ayarı temizler.|  
|`-d container`|Belirtilen anahtar kapsayıcısını tanımlayıcı ad CSP'sinden siler.|  
|`-D assembly1 assembly2`|İki derlemenin yalnızca imza farkı olduğunu doğrular. Bu çoğunlukla, bir derleme farklı bir anahtar çifti ile yeniden imzalandıktan sonra denetim olarak kullanılır.|  
|`-e assembly outfile`|*Derlemeden* ortak anahtarı ayıklar ve çıkışdosyası içinde depolar *.*|  
|`-h`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|`-i infile container`|Belirtilen anahtar kapsayıcısındaki *INFILE* 'dan anahtar çiftini yükleme. Anahtar kapsayıcısı, tanımlayıcı ad CSP'sinde bulunur.|  
|`-k [keysize] outfile`|<xref:System.Security.Cryptography.RSACryptoServiceProvider>Belirtilen boyutta yeni bir anahtar oluşturur ve belirtilen dosyaya yazar.  Hem ortak hem de özel anahtar dosyaya yazılır.<br /><br /> Bir anahtar boyutu belirtmezseniz, makinenizde Microsoft gelişmiş şifreleme sağlayıcısı yüklü ise varsayılan olarak 1,024-bit bir anahtar oluşturulur, yüklü değilse 512-bit anahtar oluşturulur.<br /><br /> Microsoft Gelişmiş şifreleme sağlayıcısı yüklüyse, *KeySize* parametresi, 384 bitten 16.384 bite kadar, 8 bitten oluşan anahtar uzunluklarını destekler.  Makinenizde Microsoft temel şifreleme sağlayıcısı yüklüyse, 8 bitlik artışlarla 384 bit'ten 512 bit'e kadar olan anahtar uzunluklarını destekler.|  
|`-m [y|n]`|Anahtar kapsayıcılarının bilgisayara özgü mi yoksa kullanıcıya özgü mü olduğunu belirtir. *Y*belirtirseniz, anahtar kapsayıcıları bilgisayara özgüdür. *N*belirtirseniz, anahtar kapsayıcıları kullanıcıya özeldir.<br /><br /> y ne n öğelerinden hiçbirini belirtmezseniz, bu seçenek geçerli ayarı görüntüler.|  
|`-o infile [outfile]`|*Indosyadan* ortak anahtarı ayıklar ve bir. csv dosyasında depolar. Ortak anahtarın her baytı virgülle ayrılır. Bu biçim, kaynak kodunda başlatılmış diziler olarak anahtarlara ilişkin sabit kodlama başvuruları için yararlıdır. Bir *çıkışdosyası*belirtmezseniz, bu seçenek çıktıyı panoya yerleştirir. **Note:**  Bu seçenek, girişin yalnızca bir ortak anahtar olduğunu doğrulamaz. `infile`Özel anahtarı olan bir anahtar çifti içeriyorsa, özel anahtar de ayıklanır.|  
|`-p infile outfile [hashalg]`|Ortak anahtarı *InFile* içindeki anahtar çiftinden ayıklar ve isteğe bağlı olarak *HashAlg*tarafından belirtilen RSA algoritmasını kullanarak bu dosyayı *çıkışdosyası*içinde depolar. Bu ortak anahtar, derleme bağlayıcının **/delaysign +** ve **/keyfile** seçeneklerini kullanarak bir derlemeyi gecikmeli imzalamak için kullanılabilir [(Al.exe)](al-exe-assembly-linker.md). Derleme gecikmeli imzalanmış olduğunda, yalnızca ortak anahtar derleme zamanında ayarlanır ve özel anahtarı bulunduğunda, daha sonra eklenecek bir imza için dosyada alan ayrılır.|  
|`-pc container outfile [hashalg]`|*Kapsayıcıda* anahtar çiftinden ortak anahtarı ayıklar ve *çıkışdosyası*içinde depolar. *HashAlg* seçeneğini KULLANıRSANıZ, RSA algoritması ortak anahtarı ayıklamak için kullanılır.|  
|`-Pb [y|n]`|Tanımlayıcı ad atlama ilkesinin uygulatılıp uygulatılmayacağı belirtir. *Y*belirtirseniz, tam güven derlemeleri için tanımlayıcı adlar tam güvene yüklendiğinde doğrulanmaz <xref:System.AppDomain> . *N*belirtirseniz, tanımlayıcı adlar doğruluk için onaylanır, ancak belirli bir tanımlayıcı ad için desteklenmez. <xref:System.Security.Permissions.StrongNameIdentityPermission>Tam güvenle derlemeler üzerinde hiçbir etkiye sahip değildir. Bir tanımlayıcı ad eşleştirmesi için kendi denetiminizi gerçekleştirmeniz gerekir.<br /><br /> Ne `y` de `n` belirtilmemişse, bu seçenek geçerli ayarı görüntüler. Varsayılan değer: `y`. **Note:**  64 bit bilgisayarlarda, bu parametreyi hem 32 bit hem de Sn.exe 64-bit örneklerinde ayarlamanız gerekir.|  
|`-q[uiet]`|Sessiz mod kullanılacağını belirtir; başarı iletilerinin görüntülenmesini engeller.|  
|`-R[a] assembly infile`|Önceden imzalanmış veya gecikmeli imzalanmış bir derlemeyi *InFile*içindeki anahtar çifti ile yeniden imzalar.<br /><br /> **-Ra** kullanılıyorsa, karmalar derlemedeki tüm dosyalar için yeniden hesaplanır.|  
|`-Rc[a] assembly container`|Önceden imzalanmış veya gecikmeli imzalanmış bir derlemeyi *kapsayıcıda*anahtar çifti ile yeniden imzalar.<br /><br /> **-RCA** kullanılıyorsa, karmalar derlemedeki tüm dosyalar için yeniden hesaplanır.|  
|`-Rh assembly`|Derlemedeki tüm dosyaların karma değerlerini yeniden hesaplar.|  
|`-t[p] infile`|*InFile*içinde depolanan ortak anahtar belirtecini görüntüler. *InFile* içeriğinin, daha önce **-p**kullanan bir anahtar çifti dosyasından oluşturulmuş bir ortak anahtar olması gerekir.  Belirteci doğrudan bir anahtar çifti dosyasından ayıklamak için **-t [p]** seçeneğini kullanmayın.<br /><br /> Sn.exe, ortak anahtardan bir karma işlevini kullanarak belirteci hesaplar. Alandan kazanmak için, ortak dil çalışma zamanı, tanımlayıcı bir ada sahip derlemeye bağımlılık kaydederken ortak anahtar belirteçlerini başka bir derlemenin başvurusunun parçası olarak bildirimde depolar. **-TP** seçeneği, belirtece ek olarak ortak anahtarı görüntüler. <xref:System.Reflection.AssemblySignatureKeyAttribute>Özniteliği derlemeye uygulanmışsa, belirteç kimlik anahtarına, karma algoritmanın adına ve kimlik anahtarına göre gösterilir.<br /><br /> Bu seçeneğin derleme imzasını doğrulamadığını ve güven kararları vermek için kullanılmaması gerektiğini unutmayın.  Bu seçenek yalnızca ham ortak anahtar belirteci verilerini görüntüler.|  
|`-T[p] assembly`|Derleme için ortak anahtar belirtecini görüntüler *.* *Derleme* , derleme bildirimi içeren bir dosyanın adı olmalıdır.<br /><br /> Sn.exe, ortak anahtardan bir karma işlevini kullanarak belirteci hesaplar. Alandan kazanmak için, çalışma zamanı, tanımlayıcı bir ada sahip derlemeye bağımlılık kaydederken ortak anahtar belirteçlerini başka bir derlemenin başvurusunun parçası olarak bildirimde depolar. **-TP** seçeneği, belirtece ek olarak ortak anahtarı görüntüler. <xref:System.Reflection.AssemblySignatureKeyAttribute>Özniteliği derlemeye uygulanmışsa, belirteç kimlik anahtarına, karma algoritmanın adına ve kimlik anahtarına göre gösterilir.<br /><br /> Bu seçeneğin derleme imzasını doğrulamadığını ve güven kararları vermek için kullanılmaması gerektiğini unutmayın.  Bu seçenek yalnızca ham ortak anahtar belirteci verilerini görüntüler.|  
|`-TS assembly infile`|İmzalı veya kısmen imzalı *derlemeyi* *InFile*içindeki anahtar çiftiyle test edin.|  
|`-TSc assembly container`|Test-imzalanmış veya kısmen imzalı *derlemeyi* anahtar kapsayıcısı *kapsayıcısında*anahtar çiftiyle imzalar.|
|`-v assembly`|*Derlemede tanımlayıcı adı doğrular; burada* *derleme* , derleme bildirimi içeren bir dosyanın adıdır.|  
|`-vf assembly`|Derlemede tanımlayıcı adı doğrular *.* - **V** seçeneğinin aksine- **VF** , **-VR** seçeneği kullanılarak devre dışı bırakılmış olsa bile doğrulamayı zorlar.|  
|`-Vk regfile.reg assembly [userlist] [infile]`|Doğrulamayı atlama için belirtilen derlemeyi kaydetmek üzere kullanabileceğiniz bir kayıt girdileri (.reg) dosyası oluşturur. **-VR** seçeneğine uygulanan derleme adlandırmayla ilgili kurallar, **– VK** için de geçerlidir. *UserList* ve *InFile* seçenekleri hakkında daha fazla bilgi için **– VR** seçeneğine bakın.|  
|`-Vl`|Bu bilgisayardaki tanımlayıcı ad doğrulamasının geçerli ayarlarını listeler.|  
|`-Vr  assembly [userlist] [infile]`|Doğrulama atlama için *bütünleştirilmiş kodu* kaydeder. İsteğe bağlı olarak, doğrulama atlamanın geçerli olacağı kullanıcı adlarının virgülle ayrılmış listesini belirtebilirsiniz. *InFile*belirtirseniz, doğrulama etkin kalır ancak doğrulama işlemlerinde *InFile* içindeki ortak anahtar kullanılır. *Derlemeyi* * \* ,* belirtilen tanımlayıcı ada sahip tüm derlemeleri kaydetmek için formunda belirtebilirsiniz. *StrongName*için, ortak anahtarın simgeleştirilmiş biçimini temsil eden onaltılık basamakların dizesini belirtin. Ortak anahtar belirtecini görüntülemek için **-t** ve **-t** seçeneklerine bakın. **Dikkat:**  Bu seçeneği yalnızca geliştirme sırasında kullanın. Doğrulama atlama listesine bir derleme eklemek güvenlik açığı oluşturur. Kötü amaçlı bir derleme, kimliğini gizlemek için doğrulama atlama listesine eklenmiş derlemenin tam olarak belirtilmiş derleme adını (derleme adı, sürüm, kültür ve ortak anahtar belirteci) kullanabilir. Bu, kötü amaçlı derlemenin de doğrulamayı atlamasına izin verir.|  
|||  
|`-Vu  assembly`|Doğrulama atlama için *bütünleştirilmiş kodun* kaydını siler. **-VR** ' ye uygulanan derleme adlandırması için aynı kurallar **-vu & lt**için geçerlidir.|  
|`-Vx`|Doğrulama atlama girişlerinin tümünü kaldırır.|  
|`-?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
> [!NOTE]
> Tüm Sn.exe seçenekler büyük/küçük harfe duyarlıdır ve araç tarafından tanınması için tam olarak gösterildiği gibi yazılmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 **-R** ve **– RC** seçenekleri, gecikmeli imzalanmış Derlemelerle yararlı olur. Bu senaryoda, derleme zamanında yalnızca ortak anahtar ayarlanmıştır, imzalama ise daha sonra, özel anahtar tanındığında yapılır.  
  
> [!NOTE]
> Kayıt defteri gibi korumalı kaynaklara yazılan parametreler (örneğin, –**VR)** için, SN.exe yönetici olarak çalıştırın.  
  
Tanımlayıcı ad Aracı, ortak/özel anahtar çiftlerinin algoritma tanımlayıcısı ile oluşturulduğunu varsayar `AT_SIGNATURE` . Algoritmayla oluşturulan ortak/özel anahtar çiftleri `AT_KEYEXCHANGE` bir hata oluşturur.

## <a name="examples"></a>Örnekler  
 Aşağıdaki komut yeni, rastgele bir anahtar çifti oluşturur ve içinde depolar `keyPair.snk` .  
  
```console  
sn -k keyPair.snk  
```  
  
 Aşağıdaki komut, içindeki anahtarını `keyPair.snk` `MyContainer` tanımlayıcı ad CSP içindeki kapsayıcıda depolar.  
  
```console  
sn -i keyPair.snk MyContainer  
```  
  
 Aşağıdaki komut, öğesinden ortak anahtarı ayıklar `keyPair.snk` ve içinde depolar `publicKey.snk` .  
  
```console  
sn -p keyPair.snk publicKey.snk  
```  
  
 Aşağıdaki komut, içinde bulunan ortak anahtar için ortak anahtarı ve belirteci görüntüler `publicKey.snk` .  
  
```console  
sn -tp publicKey.snk  
```  
  
 Aşağıdaki komut derlemeyi doğrular `MyAsm.dll` .  
  
```console  
sn -v MyAsm.dll  
```  
  
 Aşağıdaki komut `MyContainer` Varsayılan CSP 'den silinir.  
  
```console  
sn -d MyContainer  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Al.exe (bütünleştirilmiş kod bağlayıcı)](al-exe-assembly-linker.md)
- [Tanımlayıcı adlı derlemeler](../../standard/assembly/strong-named.md)
- [Komut Istemleri](developer-command-prompt-for-vs.md)
