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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24a8c7ce090b286db9d86e0fc6c54ae33e7e2d5e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61919509"
---
# <a name="snexe-strong-name-tool"></a>Sn.exe (Tanımlayıcı Ad Aracı)
Tanımlayıcı ad Aracı (Sn.exe) derlemeleri ile oturum yardımcı [güçlü adlar](../../../docs/framework/app-domains/strong-named-assemblies.md). Sn.exe; temel yönetim, imza oluşturma ve imza doğrulaması için seçenekler sağlar.  
  
> [!WARNING]
> Güvenlik için tanımlayıcı adlar güvenmeyin. Benzersiz bir kimliğe sağlarlar.

 Tanımlayıcı adlandırma ve tanımlayıcı adlı derlemeler hakkında daha fazla bilgi için bkz. [Strong-Named derlemeleri](../../../docs/framework/app-domains/strong-named-assemblies.md) ve [nasıl yapılır: Bir derlemeyi katı bir adla imzalamak](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
 Tanımlayıcı Ad aracı Visual Studio ile birlikte otomatik olarak yüklenir. Aracı'nı başlatmak için geliştirici komut istemi (veya Windows 7'de Visual Studio komut istemi) kullanın. Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  

> [!NOTE]
>  64-bit bilgisayarlarda, geliştirici komut istemi Visual Studio ve 64-bit sürümü için Visual Studio x64 Win64 komut istemi kullanarak Sn.exe 32-bit sürümünü çalıştırın. 
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
sn [-quiet][option [parameter(s)]]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**-a** *identityKeyPairFile* *signaturePublicKeyFile*|Oluşturur <xref:System.Reflection.AssemblySignatureKeyAttribute> kimlik anahtarını bir dosyadan imza anahtarına geçirmek için veri.|  
|**-ac** *identityPublicKeyFile* *identityKeyPairContainer* *signaturePublicKeyFile*|Oluşturur <xref:System.Reflection.AssemblySignatureKeyAttribute> kimlik anahtarını bir anahtar kapsayıcısından imza anahtarına geçirmek için veri.|  
|**-c** [*csp*]|Tanımlayıcı ad imzası için kullanılacak varsayılan şifreleme hizmeti sağlayıcısı (CSP) ayarlar. Bu ayar tüm bilgisayara uygulanır. Bir CSP adı belirtmezseniz, Sn.exe geçerli ayarı temizler.|  
|**-d** *kapsayıcı*|Belirtilen anahtar kapsayıcısını tanımlayıcı ad CSP'sinden siler.|  
|**-D** *assembly1 assembly2*|İki derlemenin yalnızca imza farkı olduğunu doğrular. Bu çoğunlukla, bir derleme farklı bir anahtar çifti ile yeniden imzalandıktan sonra denetim olarak kullanılır.|  
|**-e** *derleme outfile*|Öğesinden ortak anahtarı ayıklar *derleme* ve depolar *outfile.*|  
|**-h**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**-i** *infile container*|Dan anahtar çifti yükler *infile* belirtilen anahtar kapsayıcısında. Anahtar kapsayıcısı, tanımlayıcı ad CSP'sinde bulunur.|  
|**-k** [*keysize*] *outfile*|Yeni bir dizi oluşturur <xref:System.Security.Cryptography.RSACryptoServiceProvider> belirtilen boyutta anahtar ve onu belirtilen dosyaya yazar.  Hem ortak hem de özel anahtar dosyaya yazılır.<br /><br /> Bir anahtar boyutu belirtmezseniz, makinenizde Microsoft gelişmiş şifreleme sağlayıcısı yüklü ise varsayılan olarak 1,024-bit bir anahtar oluşturulur, yüklü değilse 512-bit anahtar oluşturulur.<br /><br /> *Keysize* parametresi yüklü Microsoft Gelişmiş şifreleme sağlayıcısı yüklüyse bu 384 bitten 16.384 bit'e kadar olan anahtar uzunluklarını 8 bitlik artışlarla destekler.  Makinenizde Microsoft temel şifreleme sağlayıcısı yüklüyse, 8 bitlik artışlarla 384 bit'ten 512 bit'e kadar olan anahtar uzunluklarını destekler.|  
|**-m** [**y** *&#124;* **n**]|Anahtar kapsayıcılarının bilgisayara özgü mi yoksa kullanıcıya özgü mü olduğunu belirtir. Belirtirseniz *y*, anahtar kapsayıcıları bilgisayara özgü. Belirtirseniz *n*, anahtar kapsayıcıları kullanıcıya özgü.<br /><br /> y ne n öğelerinden hiçbirini belirtmezseniz, bu seçenek geçerli ayarı görüntüler.|  
|**-o**  *infile* [*outfile*]|Öğesinden ortak anahtarı ayıklar *infile* ve bir .csv dosyasına depolar. Ortak anahtarın her baytı virgülle ayrılır. Bu biçim, kaynak kodunda başlatılmış diziler olarak anahtarlara ilişkin sabit kodlama başvuruları için yararlıdır. Belirtmezseniz, bir *outfile*, bu seçenek çıktıyı Pano'ya yerleştirir. **Not:**  Bu seçenek girdinin yalnızca bir ortak anahtar olduğunu doğrulamaz. Varsa `infile` anahtar çiftini içeren özel bir anahtarla özel anahtar da ayıklanır.|  
|**-p** *infile outfile* [*hashalg*]|İçindeki anahtar çiftinden ortak anahtarı ayıklar *infile* ve depolar *outfile*, isteğe bağlı olarak tarafından belirtilen RSA algoritması kullanarak *hashalg*. Bu ortak anahtar kullanarak bir derlemeyi Gecikmeli imzalamak için kullanılan **/delaysign+** ve **/keyfile** seçenekleri [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Derleme gecikmeli imzalanmış olduğunda, yalnızca ortak anahtar derleme zamanında ayarlanır ve özel anahtarı bulunduğunda, daha sonra eklenecek bir imza için dosyada alan ayrılır.|  
|**-pc**  *kapsayıcı* *outfile* [*hashalg*]|İçindeki anahtar çiftinden ortak anahtarı ayıklar *kapsayıcı* ve depolar *outfile*. Kullanırsanız *hashalg* seçeneği, RSA algoritması ortak anahtarı ayıklamak için kullanılır.|  
|**-Pb** [**y** *&#124;* **n**]|Tanımlayıcı ad atlama ilkesinin uygulatılıp uygulatılmayacağı belirtir. Belirtirseniz *y*güçlü tam güvene yüklendiğinde tam güven derlemeleri doğrulanmaz için adları <xref:System.AppDomain>. Belirtirseniz *n*, doğruluk, ancak belirli bir tanımlayıcı adı için tanımlayıcı adlar doğrulanır. <xref:System.Security.Permissions.StrongNameIdentityPermission> Tam güvenle çalışan derlemelere etkisi yoktur. Bir tanımlayıcı ad eşleştirmesi için kendi denetiminizi gerçekleştirmeniz gerekir.<br /><br /> Kullanılmazsa `y` ya da `n` belirtilirse, bu seçenek geçerli ayarı görüntüler. Varsayılan, `y` değeridir. **Not:**  64 bit bilgisayarlarda, bu parametreyi hem 32-bit hem de 64-bit Sn.exe örneklerinde ayarlamanız gerekir.|  
|**-q**[**uiet**]|Sessiz mod kullanılacağını belirtir; başarı iletilerinin görüntülenmesini engeller.|  
|**-R**[**a**] *assembly* *infile*|Daha önce imzalanmış veya gecikmeli imzalanmış bir derleme içindeki anahtar çifti ile yeniden imzalar *infile*.<br /><br /> Varsa **-Ra** olan kullanılırsa, derlemedeki tüm dosyalar için karmalar hesaplanır.|  
|**-Rc**[**bir**] *derleme kapsayıcısı*|Daha önce imzalanmış veya gecikmeli imzalanmış bir derleme içindeki anahtar çifti ile yeniden imzalar *kapsayıcı*.<br /><br /> Varsa **- Rca** olan kullanılırsa, derlemedeki tüm dosyalar için karmalar hesaplanır.|  
|**-Rh** *derleme*|Derlemedeki tüm dosyaların karma değerlerini yeniden hesaplar.|  
|**-t**[**p**] *infile*|İçinde depolanan ortak anahtarın belirtecini görüntüler *infile*. İçeriğini *infile* kullanarak bir anahtar çifti dosyasını daha önce oluşturulmuş bir ortak anahtar olmalıdır **-p**.  Kullanmayın **-t [p]** belirteci doğrudan bir anahtar çifti dosyasından ayıklamak için seçeneği.<br /><br /> Sn.exe, ortak anahtardan bir karma işlevini kullanarak belirteci hesaplar. Alandan kazanmak için, ortak dil çalışma zamanı, tanımlayıcı bir ada sahip derlemeye bağımlılık kaydederken ortak anahtar belirteçlerini başka bir derlemenin başvurusunun parçası olarak bildirimde depolar. **- Tp** seçeneği belirtece ek olarak ortak anahtarı görüntüler. Varsa <xref:System.Reflection.AssemblySignatureKeyAttribute> derlemeye özniteliği uygulandı, belirteç kimlik anahtarı içindir ve karma algoritması ve kimlik anahtarı adı görüntülenir.<br /><br /> Bu seçeneğin derleme imzasını doğrulamadığını ve güven kararları vermek için kullanılmaması gerektiğini unutmayın.  Bu seçenek yalnızca ham ortak anahtar belirteci verilerini görüntüler.|  
|**-T**[**p**] *assembly*|Genel anahtar belirtecini görüntüler *derleme.* *Derleme* bir derleme bildirimi içeren dosyanın adı olmalıdır.<br /><br /> Sn.exe, ortak anahtardan bir karma işlevini kullanarak belirteci hesaplar. Alandan kazanmak için, çalışma zamanı, tanımlayıcı bir ada sahip derlemeye bağımlılık kaydederken ortak anahtar belirteçlerini başka bir derlemenin başvurusunun parçası olarak bildirimde depolar. **- Tp** seçeneği belirtece ek olarak ortak anahtarı görüntüler. Varsa <xref:System.Reflection.AssemblySignatureKeyAttribute> derlemeye özniteliği uygulandı, belirteç kimlik anahtarı içindir ve karma algoritması ve kimlik anahtarı adı görüntülenir.<br /><br /> Bu seçeneğin derleme imzasını doğrulamadığını ve güven kararları vermek için kullanılmaması gerektiğini unutmayın.  Bu seçenek yalnızca ham ortak anahtar belirteci verilerini görüntüler.|  
|`-TS` `assembly` `infile`|Test imzası uygular imzalanmış veya kısmen imzalanmış `assembly` içindeki anahtar çifti ile `infile`.|  
|-`TSc` `assembly` `container`|Test imzası uygular imzalanmış veya kısmen imzalanmış `assembly` anahtar kapsayıcısı içindeki anahtar çifti ile `container`.|  
|**-v** *derleme*|İçindeki tanımlayıcı adı doğrular *derleme*burada *derleme* bir derleme bildirimi içeren dosyanın adıdır.|  
|**-vf**  *derleme*|İçindeki tanımlayıcı adı doğrular *derleme.* Farklı **- v** seçeneği **-vf** kullanarak devre dışı olsa bile doğrulama zorlar **- Vr** seçeneği.|  
|**-Vk**  *regfile.reg* *derleme* [*userlist*] [*infile*]|Doğrulamayı atlama için belirtilen derlemeyi kaydetmek üzere kullanabileceğiniz bir kayıt girdileri (.reg) dosyası oluşturur. İçin geçerli olan derleme adlandırma kurallarını **- Vr** seçeneğini uygulamak için **– Vk** de. Hakkında bilgi için *userlist* ve *infile* seçeneklerini görmek **– Vr** seçeneği.|  
|**-Vl**|Bu bilgisayardaki tanımlayıcı ad doğrulamasının geçerli ayarlarını listeler.|  
|**-Vr**  *derleme* [*userlist*] [*infile*]|Kayıtları *derleme* doğrulama atlama için. İsteğe bağlı olarak, doğrulama atlamanın geçerli olacağı kullanıcı adlarının virgülle ayrılmış listesini belirtebilirsiniz. Belirtirseniz *infile*, doğrulama etkin kalır, ancak ortak anahtar *infile* doğrulama işlemlerinde kullanılır. Belirtebileceğiniz *derleme* biçiminde  *\*, strongname* tüm derlemeleri belirtilen tanımlayıcı adla kaydettirmek için. İçin *strongname*, ortak anahtarın simgeleştirilmiş formunu temsil eden onaltı basamaklı dizeyi belirtin. Bkz: **-t** ve **-T** ortak anahtar belirtecini görüntülemek için Seçenekler. **Dikkat:**  Yalnızca geliştirme sırasında bu seçeneği kullanın. Doğrulama atlama listesine bir derleme eklemek güvenlik açığı oluşturur. Kötü amaçlı bir derleme, kimliğini gizlemek için doğrulama atlama listesine eklenmiş derlemenin tam olarak belirtilmiş derleme adını (derleme adı, sürüm, kültür ve ortak anahtar belirteci) kullanabilir. Bu, kötü amaçlı derlemenin de doğrulamayı atlamasına izin verir.|  
|||  
|**-Vu**  *derleme*|Kaydını siler *derleme* doğrulama atlama için. İçin de geçerlidir derleme adlandırma kurallarının aynıları **- Vr** uygulamak **- Vu**.|  
|**-Vx**|Doğrulama atlama girişlerinin tümünü kaldırır.|  
|**-?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
> [!NOTE]
>  Tüm Sn.exe seçenekler büyük/küçük harfe duyarlıdır ve araç tarafından tanınması için tam olarak gösterildiği gibi yazılmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 **-R** ve **– Rc** seçenekleri gecikmeli imzalanmış derlemelerde yararlıdır. Bu senaryoda, derleme zamanında yalnızca ortak anahtar ayarlanmıştır, imzalama ise daha sonra, özel anahtar tanındığında yapılır.  
  
> [!NOTE]
>  Parametreler için (örneğin, –**Vr)** SN.exe yönetici olarak çalıştırın, kayıt defteri gibi korumalı kaynaklara yazma.  
  
Tanımlayıcı ad aracı ortak/özel anahtar çifti ile oluşturulan varsayar `AT_SIGNATURE` algoritma tanımlayıcısı. Ortak/özel anahtar çifti ile oluşturulan `AT_KEYEXCHANGE` algoritması bir hata oluşturur. 

## <a name="examples"></a>Örnekler  
 Aşağıdaki komut yeni, rastgele bir anahtar çifti oluşturur ve depolar `keyPair.snk`.  
  
```  
sn -k keyPair.snk  
```  
  
 Aşağıdaki komut anahtarı depolar `keyPair.snk` kapsayıcısında `MyContainer` tanımlayıcı ad CSP'SİNDEKİ.  
  
```  
sn -i keyPair.snk MyContainer  
```  
  
 Aşağıdaki komut ortak anahtarı ayıklar `keyPair.snk` ve depolar `publicKey.snk`.  
  
```  
sn -p keyPair.snk publicKey.snk  
```  
  
 Aşağıdaki komut ortak anahtarı ve içindeki ortak anahtar belirtecini görüntüler `publicKey.snk`.  
  
```  
sn -tp publicKey.snk  
```  
  
 Aşağıdaki komutu derlemesini doğrular `MyAsm.dll`.  
  
```  
sn -v MyAsm.dll  
```  
  
 Aşağıdaki komut siler `MyContainer` CSP varsayılan.  
  
```  
sn -d MyContainer  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](../../../docs/framework/tools/index.md)
- [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [Kesin Adlandırılmış Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/strong-named-assemblies.md)
- [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
