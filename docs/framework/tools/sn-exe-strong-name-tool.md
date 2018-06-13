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
ms.openlocfilehash: c7e58d14eb29939ea1b91b5bdb75f691f5233d8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401127"
---
# <a name="snexe-strong-name-tool"></a>Sn.exe (Tanımlayıcı Ad Aracı)
Tanımlayıcı ad Aracı (Sn.exe) oturum Derlemelerle yardımcı [tanımlayıcı adlar](../../../docs/framework/app-domains/strong-named-assemblies.md). Sn.exe; temel yönetim, imza oluşturma ve imza doğrulaması için seçenekler sağlar.  
  
 Güçlü adlandırma ve tanımlayıcı adlı derlemeler hakkında daha fazla bilgi için bkz: [Strong-Named derlemeleri](../../../docs/framework/app-domains/strong-named-assemblies.md) ve [nasıl yapılır: bir derlemeyi tanımlayıcı adla oturum](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
 Tanımlayıcı Ad aracı Visual Studio ile birlikte otomatik olarak yüklenir. Aracı'nı başlatmak için geliştirici komut istemi (veya Windows 7'de Visual Studio komut istemi) kullanın. Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
> [!NOTE]
>  64-bit bilgisayarlarda, Visual Studio komut istemi ve 64-bit sürümünü Visual Studio x64 Win64 komut istemi kullanarak Sn.exe 32-bit sürümünü çalıştırın.  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
sn [-quiet][option [parameter(s)]]  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**-a** *identityKeyPairFile* *signaturePublicKeyFile*|Oluşturur <xref:System.Reflection.AssemblySignatureKeyAttribute> kimlik anahtarı imza anahtarı dosyadan geçirmek için veri.|  
|**-ac** *identityPublicKeyFile* *identityKeyPairContainer* *signaturePublicKeyFile*|Oluşturur <xref:System.Reflection.AssemblySignatureKeyAttribute> kimlik anahtarı imza anahtarına bir anahtar kapsayıcı geçirmek için veri.|  
|**-c** [*csp*]|Tanımlayıcı ad imzası için kullanılacak varsayılan şifreleme hizmeti sağlayıcısı (CSP) ayarlar. Bu ayar tüm bilgisayara uygulanır. Bir CSP adı belirtmezseniz, Sn.exe geçerli ayarı temizler.|  
|**-d** *kapsayıcı*|Belirtilen anahtar kapsayıcısını tanımlayıcı ad CSP'sinden siler.|  
|**-D***assembly1 assembly2* |İki derlemenin yalnızca imza farkı olduğunu doğrular. Bu çoğunlukla, bir derleme farklı bir anahtar çifti ile yeniden imzalandıktan sonra denetim olarak kullanılır.|  
|**-e***derleme outfile* |Ortak anahtarı ile ayıklar *derleme* ve depolar *outfile.*|  
|**-h**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**-i** *GirişDosyası kapsayıcısı*|Gelen anahtar çifti yükler *GirişDosyası* içinde belirtilen anahtar kapsayıcısı. Anahtar kapsayıcısı, tanımlayıcı ad CSP'sinde bulunur.|  
|**-k** [*anahtar boyutu*] *outfile*|Yeni bir oluşturur <xref:System.Security.Cryptography.RSACryptoServiceProvider> belirtilen boyuttaki anahtar ve belirtilen dosyaya yazar.  Hem ortak hem de özel anahtar dosyaya yazılır.<br /><br /> Bir anahtar boyutu belirtmezseniz, makinenizde Microsoft gelişmiş şifreleme sağlayıcısı yüklü ise varsayılan olarak 1,024-bit bir anahtar oluşturulur, yüklü değilse 512-bit anahtar oluşturulur.<br /><br /> *Anahtar boyutu* parametresi yüklü Microsoft Gelişmiş Şifreleme Sağlayıcısı varsa bu 384 bitten anahtar uzunluklarını 16.384 BITS 8 bit artışlarla destekler.  Makinenizde Microsoft temel şifreleme sağlayıcısı yüklüyse, 8 bitlik artışlarla 384 bit'ten 512 bit'e kadar olan anahtar uzunluklarını destekler.|  
|**-m** [**y** *&#124;* **n**]|Anahtar kapsayıcılarının bilgisayara özgü mi yoksa kullanıcıya özgü mü olduğunu belirtir. Belirtirseniz *y*, anahtar kapsayıcıları bilgisayara özel. Belirtirseniz *n*, anahtar kapsayıcıları kullanıcıya özgü.<br /><br /> y ne n öğelerinden hiçbirini belirtmezseniz, bu seçenek geçerli ayarı görüntüler.|  
|**-o***GirişDosyası* [*outfile*]  |Ortak anahtarı ile ayıklar *GirişDosyası* ve bir .csv dosyasında depolar. Ortak anahtarın her baytı virgülle ayrılır. Bu biçim, kaynak kodunda başlatılmış diziler olarak anahtarlara ilişkin sabit kodlama başvuruları için yararlıdır. Belirtmezseniz, bir *outfile*, bu seçenek çıktı panoya yerleştirir. **Not:** bu seçenek giriş yalnızca bir ortak anahtar olduğunu doğrulamaz. Varsa `infile` anahtar çiftini içeren özel bir anahtarla özel anahtarı da ayıklanır.|  
|**-p** *GirişDosyası ÇıkışDosyası* [*KarmaAlgoritma*]|Anahtar çiftini gelen ortak anahtarı ayıklar *GirişDosyası* ve depolar *outfile*, isteğe bağlı olarak tarafından belirtilen RSA algoritmasını kullanarak *KarmaAlgoritma*. Bu ortak anahtar olabilir kullanarak bir derlemeye geciktirin için kullanılan **/delaysign+** ve **/keyfile** seçeneklerini [derleme bağlayıcı (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Derleme gecikmeli imzalanmış olduğunda, yalnızca ortak anahtar derleme zamanında ayarlanır ve özel anahtarı bulunduğunda, daha sonra eklenecek bir imza için dosyada alan ayrılır.|  
|**-pc***kapsayıcı* *outfile* [*KarmaAlgoritma*]  |Anahtar çiftini gelen ortak anahtarı ayıklar *kapsayıcı* ve depolar *outfile*. Kullanırsanız *KarmaAlgoritma* seçeneği, RSA algoritması, ortak anahtar ayıklamak için kullanılır.|  
|**-Pb** [**y** *&#124;* **n**]|Tanımlayıcı ad atlama ilkesinin uygulatılıp uygulatılmayacağı belirtir. Belirtirseniz *y*, güçlü tam güven derlemeler tam güvene yüklendiğinde doğrulanmaz için adları <xref:System.AppDomain>. Belirtirseniz *n*, tanımlayıcı adlar doğruluğunu ancak belirli bir güçlü ad için doğrulanır. <xref:System.Security.Permissions.StrongNameIdentityPermission> Tam güven derlemeleri üzerinde hiçbir etkisi olmaz. Bir tanımlayıcı ad eşleştirmesi için kendi denetiminizi gerçekleştirmeniz gerekir.<br /><br /> Ne `y` ya da `n` belirtilirse, bu seçenek geçerli ayarı görüntüler. Varsayılan, `y` değeridir. **Not:** 64-bit bilgisayarlarda, bu parametre hem 32 bit hem de Sn.exe 64-bit örneklerini ayarlamanız gerekir.|  
|**-q**[**uiet**]|Sessiz mod kullanılacağını belirtir; başarı iletilerinin görüntülenmesini engeller.|  
|**-R**[**bir**] *derleme* *GirişDosyası*|Bir anahtar çifti daha önce imzalanmış veya gecikmeli imzalanmış derleme yeniden oturum açtığında *GirişDosyası*.<br /><br /> Varsa **-Ra** olan kullanıldığında, karmaları derlemedeki tüm dosyalar için yeniden.|  
|**-Rc**[**bir**] *derleme kapsayıcısı*|Bir anahtar çifti daha önce imzalanmış veya gecikmeli imzalanmış derleme yeniden oturum açtığında *kapsayıcı*.<br /><br /> Varsa **- Rca** olan kullanıldığında, karmaları derlemedeki tüm dosyalar için yeniden.|  
|**-Rh** *derleme*|Derlemedeki tüm dosyaların karma değerlerini yeniden hesaplar.|  
|**-t**[**p**] *GirişDosyası*|Ortak anahtar içinde depolanan için belirteç görüntüler *GirişDosyası*. İçeriğini *GirişDosyası* kullanarak bir anahtar çifti dosya önceden oluşturulan bir ortak anahtar olmalıdır **-p**.  Kullanmayın **-t [p]** belirteç doğrudan bir anahtar çifti dosyadan ayıklamak için seçeneği.<br /><br /> Sn.exe, ortak anahtardan bir karma işlevini kullanarak belirteci hesaplar. Alandan kazanmak için, ortak dil çalışma zamanı, tanımlayıcı bir ada sahip derlemeye bağımlılık kaydederken ortak anahtar belirteçlerini başka bir derlemenin başvurusunun parçası olarak bildirimde depolar. **- Tp** seçeneği, ortak anahtar belirteci ek olarak görüntüler. Varsa <xref:System.Reflection.AssemblySignatureKeyAttribute> özniteliği derlemeye uygulandı, kimlik anahtarıdır belirteç ve karma algoritması ve kimlik anahtarı adı görüntülenir.<br /><br /> Bu seçeneğin derleme imzasını doğrulamadığını ve güven kararları vermek için kullanılmaması gerektiğini unutmayın.  Bu seçenek yalnızca ham ortak anahtar belirteci verilerini görüntüler.|  
|**-T**[**p**] *derleme*|Ortak anahtar belirteci için görüntüler *derleme.* *Derleme* bir derleme bildirimi içeren bir dosya adı olmalıdır.<br /><br /> Sn.exe, ortak anahtardan bir karma işlevini kullanarak belirteci hesaplar. Alandan kazanmak için, çalışma zamanı, tanımlayıcı bir ada sahip derlemeye bağımlılık kaydederken ortak anahtar belirteçlerini başka bir derlemenin başvurusunun parçası olarak bildirimde depolar. **- Tp** seçeneği, ortak anahtar belirteci ek olarak görüntüler. Varsa <xref:System.Reflection.AssemblySignatureKeyAttribute> özniteliği derlemeye uygulandı, kimlik anahtarıdır belirteç ve karma algoritması ve kimlik anahtarı adı görüntülenir.<br /><br /> Bu seçeneğin derleme imzasını doğrulamadığını ve güven kararları vermek için kullanılmaması gerektiğini unutmayın.  Bu seçenek yalnızca ham ortak anahtar belirteci verilerini görüntüler.|  
|`-TS` `assembly` `infile`|Test-işaretlerini imzalı veya kısmen imzalı `assembly` anahtar çifti ile `infile`.|  
|-`TSc``assembly``container`|Test-işaretlerini imzalı veya kısmen imzalı `assembly` anahtar kapsayıcısında anahtar çifti ile `container`.|  
|**-v** *derleme*|Tanımlayıcı ad doğrular *derleme*, burada *derleme* bir derleme bildirimi içeren bir dosya adıdır.|  
|**-vf***derleme* |Tanımlayıcı ad doğrular *derleme.* Farklı **- v** seçeneği **-vf** kullanarak devre dışı olsa bile doğrulama zorlar **- Vr** seçeneği.|  
|**-Vk***regfile.reg* *derleme* [*userlist*] [*GirişDosyası*]  |Doğrulamayı atlama için belirtilen derlemeyi kaydetmek üzere kullanabileceğiniz bir kayıt girdileri (.reg) dosyası oluşturur. Adlandırma derleme için geçerli kuralları **- Vr** seçeneğini uygulamak için **– Vk** de. Hakkında bilgi için *userlist* ve *GirişDosyası* seçenekleri bkz **– Vr** seçeneği.|  
|**-Toplu Lisans**|Bu bilgisayardaki tanımlayıcı ad doğrulamasının geçerli ayarlarını listeler.|  
|**-Vr***derleme* [*userlist*] [*GirişDosyası*]  |Kaydeder *derleme* doğrulaması atlanıyor. İsteğe bağlı olarak, doğrulama atlamanın geçerli olacağı kullanıcı adlarının virgülle ayrılmış listesini belirtebilirsiniz. Belirtirseniz *GirişDosyası*, etkin doğrulama kalır, ancak ortak anahtar *GirişDosyası* doğrulama işlemlerinde kullanılır. Belirleyebileceğiniz *derleme* biçiminde  *\*, strongname* tüm derlemelerde belirtilen tanımlayıcı ad ile kaydetmek için. İçin *strongname*, onaltılık basamak parçalanmış formun ortak anahtarın temsil eden dizeyi belirtin. Bkz: **-t** ve **-T** ortak anahtar belirteci görüntülemek için Seçenekler. **Dikkat:** yalnızca geliştirme sırasında bu seçeneği kullanın. Doğrulama atlama listesine bir derleme eklemek güvenlik açığı oluşturur. Kötü amaçlı bir derleme, kimliğini gizlemek için doğrulama atlama listesine eklenmiş derlemenin tam olarak belirtilmiş derleme adını (derleme adı, sürüm, kültür ve ortak anahtar belirteci) kullanabilir. Bu, kötü amaçlı derlemenin de doğrulamayı atlamasına izin verir.|  
|||  
|**-Vu***derleme* |Kaydını siler *derleme* doğrulaması atlanıyor. Aynı kuralları, adlandırma derleme uygulamak için **- Vr** uygulamak **- Vu**.|  
|**-Vx**|Doğrulama atlama girişlerinin tümünü kaldırır.|  
|**-?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
> [!NOTE]
>  Tüm Sn.exe seçenekler büyük/küçük harfe duyarlıdır ve araç tarafından tanınması için tam olarak gösterildiği gibi yazılmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 **-R** ve **– Rc** seçenekleri gecikme imzalanmış Derlemelerle kullanışlıdır. Bu senaryoda, derleme zamanında yalnızca ortak anahtar ayarlanmıştır, imzalama ise daha sonra, özel anahtar tanındığında yapılır.  
  
> [!NOTE]
>  Parametreler için (örneğin, –**Vr)** SN.exe bir yönetici olarak Çalıştır kayıt defteri gibi korunan kaynakları için yazma.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut yeni, rastgele bir anahtar çifti oluşturur ve depolar `keyPair.snk`.  
  
```  
sn -k keyPair.snk  
```  
  
 Aşağıdaki komut anahtarında depolar `keyPair.snk` kapsayıcısında `MyContainer` güçlü CSP adı.  
  
```  
sn -i keyPair.snk MyContainer  
```  
  
 Aşağıdaki komut ortak anahtarı ile ayıklar `keyPair.snk` ve depolar `publicKey.snk`.  
  
```  
sn -p keyPair.snk publicKey.snk  
```  
  
 Aşağıdaki komut ortak anahtar ve bulunan ortak anahtar belirteci görüntüler `publicKey.snk`.  
  
```  
sn -tp publicKey.snk  
```  
  
 Aşağıdaki komutu derleme doğrular `MyAsm.dll`.  
  
```  
sn -v MyAsm.dll  
```  
  
 Aşağıdaki komut siler `MyContainer` CSP varsayılan.  
  
```  
sn -d MyContainer  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araçlar](../../../docs/framework/tools/index.md)  
 [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [Kesin Adlandırılmış Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/strong-named-assemblies.md)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
