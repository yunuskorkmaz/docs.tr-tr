---
title: Peverify.exe (PEVerify Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- portable executable files, PEVerify
- verifying MSIL and metadata
- PEVerify tool
- type safety requirements
- MSIL
- PEverify.exe
- PE files, PEVerify
ms.assetid: f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57c47fab98d7def3c3548769da091951819db1b1
ms.sourcegitcommit: dfc8aa44246a97f4611cc441d9ef71b03cc31260
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2018
ms.locfileid: "49413644"
---
# <a name="peverifyexe-peverify-tool"></a>Peverify.exe (PEVerify Aracı)
PEVerify aracı, Microsoft ara dili (MSIL) (derleyici yazıcıları, betik motor geliştiricileri vb.) oluşturan geliştiricilere, MSIL kodlarının ve ilişkili meta verilerinin güvenlik koşullarına uygun olup olmadığını belirlemede yardımcı olur. Bazı derleyiciler yalnızca belirli dil yapılarını kullanmaktan kaçındığınızda doğrulanabilir şekilde tür kullanımı uyumlu kod üretir. Bir geliştirici olarak, bilgisayar kullanıyorsanız, kodunuzun tür güvenliğini tehlikeye atmadığınızı doğrulamak isteyebilirsiniz. Bu durumda, MSIL ve meta verileri denetlemek için dosyalarınızda PEVerify aracını çalıştırabilirsiniz.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
peverify filename [options]  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*Dosya adı*|MSIL ve meta verilerinin denetleneceği taşınabilir yürütülebilir (PE) dosyası.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/break=** *maxErrorCount*|Doğrulamadan sonra iptal *maxErrorCount* hataları.<br /><br /> Bu parametre .NET Framework sürüm 2.0 ve sonrasında desteklenmez.|  
|**/Clock**|Milisaniye olarak aşağıdaki doğrulama zamanlarını ölçer ve bildirir:<br /><br /> **MD Val. döngüsü**<br /> Meta veri doğrulama döngüsü<br /><br /> **MD Val. saf**<br /> Meta veri doğrulama safı<br /><br /> **IL Ver. döngüsü**<br /> Microsoft ara dili (MSIL) doğrulama döngüsü<br /><br /> **IL Ver saf**<br /> MSIL doğrulaması saf<br /><br /> **MD Val. döngüsü** ve **IL Ver. döngüsü** süreleri, gerekli başlatma ve kapatma yordamları gerçekleştirmek için gereken süreyi içerir. **MD Val. saf** ve **IL Ver saf** kez ve yalnızca doğrulamayı gerçekleştirmek için gereken süreyi yansıtır.|  
|**/ Help**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/HRESULT**|Onaltılık biçimde hata kodlarını görüntüler.|  
|**Yoksay =** *gt;hex.Code* [, *gt;hex.Code*]|Belirtilen hata kodlarını dikkate almaz.|  
|**Yoksay = @** *responseFile*|Belirtilen yanıt dosyasında listelenen hata kodlarını dikkate almaz.|  
|**/İl**|Tarafından belirtilen derlemede uygulanmış yöntemler için MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir *filename*. Araç, belirtmediğiniz sürece bulunan her sorun için ayrıntılı açıklamalar döndürür **/quiet** seçeneği.|  
|**/ MD**|Tarafından belirtilen derleme meta veri doğrulama denetimleri gerçekleştirir *filename*. Bu, dosya içindeki tüm meta veri yapısını ölçer ve karşılaşılan tüm doğrulama sorunlarını rapor eder.|  
|**/nologo**|Ürün sürümü ve telif hakkı bilgilerinin görüntülenmesini önler.|  
|**/nosymbols**|.NET Framework sürüm 2.0'da, geriye doğru uyumluluk için satır numaralarını gizler.|  
|**/quiet**|Sessiz mod kullanılacağını belirtir; doğrulama sorunu raporlarının çıkışını önler. Peverify.exe dosyanın tür kullanımı uyumlu olup olmadığını bildirmeye devam eder, ancak tür güvenliği doğrulamasını önleyen sorunlar hakkında bilgi vermez.|  
|`/transparent`|Yalnızca saydam yöntemleri doğrulayın.|  
|**/ unique**|Yinelenen hata kodlarını dikkate almaz.|  
|**/verbose**|.NET Framework sürüm 2. 0'da, MSIL doğrulama iletilerinde ek bilgiler görüntüler.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı, güvenlik ve yalıtım mekanizmalarını zorlamaya yardımcı olmak için uygulama kodunun tür kullanımı uyumlu yürütülmesini kullanır. Normalde olmayan kodu [doğrulanabilir şekilde tür güvenli](../../../docs/standard/security/key-security-concepts.md#type-safety-and-security) çalıştıramazsınız karşın, güvenilir, ancak doğrulanamaz kod yürütülmesine izin veren güvenlik ilkesini ayarlayabilirsiniz.  
  
 Kullanılmazsa **/md** ya da **/il** seçenekler belirtilir, Peverify.exe her iki tür denetimi gerçekleştirir. Peverify.exe gerçekleştirir **/md** ilk denetler. Herhangi bir hata varsa **/il** denetimleri yapılır. Her ikisini de belirtirseniz **/md** ve **/il**, **/il** meta verilerde hatalar olsa denetimleri yapılır. Bu nedenle, herhangi bir meta veri hatası yoksa **peverify** *filename* eşdeğerdir **peverify** *filename* **/md** **/il**.  
  
 Peverify.exe, veri akışı analizine ve geçerli meta veriye ilişkin birkaç yüz kuralı içeren bir listeye göre kapsamlı MSIL doğrulama denetimleri yapar. Peverify.exe gerçekleştirdiği denetimler hakkında ayrıntılı bilgi için bkz. "Meta veri doğrulama belirtimi" ve "MSIL yönergesi belirtimi" araçları Kılavuzu klasöründe [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
 .NET Framework sürüm 2.0 veya sonraki doğrulanabilir desteklediğini unutmayın `byref` şu MSIL yönergeleri kullanılarak belirtilen döndürür: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` ve `unbox`.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komutu derlemesinde uygulanmış yöntemler için meta veri doğrulama denetimlerini ve MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir `myAssembly.exe`.  
  
```  
peverify myAssembly.exe /md /il  
```  
  
 Yukarıdaki isteğin başarıyla tamamlanmasından sonra Peverify.exe aşağıdaki iletiyi görüntüler.  
  
```  
All classes and methods in myAssembly.exe Verified  
```  
  
 Aşağıdaki komutu derlemesinde uygulanmış yöntemler için meta veri doğrulama denetimlerini ve MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir `myAssembly.exe`. Araç bu denetimleri gerçekleştirmek için gereken süreyi görüntüler.  
  
```  
peverify myAssembly.exe /md /il /clock  
```  
  
 Yukarıdaki isteğin başarıyla tamamlanmasından sonra Peverify.exe aşağıdaki iletiyi görüntüler.  
  
```  
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 Aşağıdaki komutu derlemesinde uygulanmış yöntemler için meta veri doğrulama denetimlerini ve MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir `myAssembly.exe`. Ancak en fazla hata sayısı olan 100'e ulaştığında Peverify.exe durur. Araç belirtilen hata kodlarını dikkate almaz.  
  
```  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 Aşağıdaki komut Yukarıdaki örnekteki aynı sonucu üretir, ancak yanıt dosyasında yok sayılacak hata kodlarını belirtir `ignoreErrors.rsp`.  
  
```  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 Yanıt dosyası hata kodlarının virgülle ayrılmış listesini içerebilir.  
  
```  
0x12345678, 0xABCD1234  
```  
  
 Alternatif olarak, yanıt dosyası her satırda bir hata kodu olacak şekilde de biçimlendirilebilir.  
  
```  
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araçlar](../../../docs/framework/tools/index.md)  
 [Doğrulanabilir şekilde tür kullanımı uyumlu kod yazma](../../../docs/framework/misc/code-access-security-basics.md#typesafe_code)  
 [Tür güvenliği ve Emniyeti](../../../docs/standard/security/key-security-concepts.md#type-safety-and-security)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
