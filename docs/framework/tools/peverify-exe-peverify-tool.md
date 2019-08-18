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
ms.openlocfilehash: 1de17ec2537282fe87b5613a63e2a954383aeab6
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567324"
---
# <a name="peverifyexe-peverify-tool"></a>Peverify.exe (PEVerify Aracı)
PEVerify aracı, Microsoft ara dili (MSIL) (derleyici yazıcıları, betik motor geliştiricileri vb.) oluşturan geliştiricilere, MSIL kodlarının ve ilişkili meta verilerinin güvenlik koşullarına uygun olup olmadığını belirlemede yardımcı olur. Bazı derleyiciler yalnızca belirli dil yapılarını kullanmaktan kaçındığınızda doğrulanabilir şekilde tür kullanımı uyumlu kod üretir. Bir geliştirici olarak, bilgisayar kullanıyorsanız, kodunuzun tür güvenliğini tehlikeye atmadığınızı doğrulamak isteyebilirsiniz. Bu durumda, MSIL ve meta verileri denetlemek için dosyalarınızda PEVerify aracını çalıştırabilirsiniz.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
peverify filename [options]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*kısaltın*|MSIL ve meta verilerinin denetleneceği taşınabilir yürütülebilir (PE) dosyası.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/break=** *maxErrorCount*|*MaxErrorCount* hatalarından sonra doğrulamayı iptal eder.<br /><br /> Bu parametre .NET Framework sürüm 2.0 ve sonrasında desteklenmez.|  
|**/Saat**|Milisaniye olarak aşağıdaki doğrulama zamanlarını ölçer ve bildirir:<br /><br /> **MD Val. Cycle**<br /> Meta veri doğrulama döngüsü<br /><br /> **MD Val. Pure**<br /> Meta veri doğrulama safı<br /><br /> **Il ver. Cycle**<br /> Microsoft ara dili (MSIL) doğrulama döngüsü<br /><br /> **Il ver saf**<br /> MSIL doğrulaması saf<br /><br /> **Md Val. Cycle** ve **Il ver. Cycle** süreleri, gerekli başlatma ve kapatılma yordamlarını gerçekleştirmek için gereken süreyi içerir. **Md Val. saf** ve **Il ver saf** süreleri yalnızca doğrulamayı veya doğrulamayı gerçekleştirmek için gereken süreyi yansıtır.|  
|**/ Help**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/HRESULT**|Onaltılık biçimde hata kodlarını görüntüler.|  
|**/Ignore =** *Hex. Code* [, *Hex. Code*]|Belirtilen hata kodlarını dikkate almaz.|  
|**/Ignore = @** *yanıt dosyası*|Belirtilen yanıt dosyasında listelenen hata kodlarını dikkate almaz.|  
|**/İl**|*Dosya adı*tarafından belirtilen derlemede uygulanan metotlar için MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir. Araç, **/quiet** seçeneğini belirtmediğiniz müddetçe bulunan her bir sorun için ayrıntılı açıklamalar döndürür.|  
|**/MD**|*Dosya adı*tarafından belirtilen derlemede meta veri doğrulama denetimleri gerçekleştirir. Bu, dosya içindeki tüm meta veri yapısını ölçer ve karşılaşılan tüm doğrulama sorunlarını rapor eder.|  
|**/nologo**|Ürün sürümü ve telif hakkı bilgilerinin görüntülenmesini önler.|  
|**/nosymbols**|.NET Framework sürüm 2.0'da, geriye doğru uyumluluk için satır numaralarını gizler.|  
|**/quiet**|Sessiz mod kullanılacağını belirtir; doğrulama sorunu raporlarının çıkışını önler. Peverify.exe dosyanın tür kullanımı uyumlu olup olmadığını bildirmeye devam eder, ancak tür güvenliği doğrulamasını önleyen sorunlar hakkında bilgi vermez.|  
|`/transparent`|Yalnızca saydam yöntemleri doğrulayın.|  
|**/Unique**|Yinelenen hata kodlarını dikkate almaz.|  
|**/verbose**|.NET Framework sürüm 2. 0'da, MSIL doğrulama iletilerinde ek bilgiler görüntüler.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı, güvenlik ve yalıtım mekanizmalarını zorlamaya yardımcı olmak için uygulama kodunun tür kullanımı uyumlu yürütülmesini kullanır. Normalde, güvenlik ilkesini güvenilir ancak doğrulanamayan kodun yürütülmesine izin verecek şekilde ayarlayabilseniz de, doğruıolarak olmayan [tür güvenli](../../../docs/standard/security/key-security-concepts.md#type-safety-and-security) olmayan kod çalıştırılamaz.  
  
 **/Md** veya **/Il** seçeneklerinin hiçbiri belirtilmediyse, Peverify. exe her iki denetim türünü de gerçekleştirir. Peverify. exe önce **/md** denetimleri gerçekleştirir. Hata yoksa, **/Il** denetimleri yapılır. Hem **/md** hem de **/Il**belirtirseniz, meta verilerde hata olsa bile **/Il** denetimleri yapılır. Bu nedenle, meta veri hatası yoksa, **PEVerify** *Dosya* adı **PEVerify** *dosya adı* **/md** **/Il**ile eşdeğerdir.  
  
 Peverify.exe, veri akışı analizine ve geçerli meta veriye ilişkin birkaç yüz kuralı içeren bir listeye göre kapsamlı MSIL doğrulama denetimleri yapar. Peverify. exe ' nin gerçekleştirdiği denetimler hakkında ayrıntılı bilgi için, Windows SDK araçlar Geliştirici Kılavuzu klasöründe "meta veri doğrulama belirtimi" ve "MSIL yönerge kümesi belirtimi" başlığına bakın.  
  
 .NET Framework sürüm 2,0 veya sonraki bir sürümün aşağıdaki MSIL yönergeleri `byref` kullanılarak belirtilen doğrulanabilir dönüşler desteklediğini unutmayın: `dup`, `ldsflda`, `ldflda` `ldelema` `call` , ve `unbox`.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, derlemede `myAssembly.exe`uygulanan yöntemler için meta veri doğrulama denetimleri ve MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir.  
  
```  
peverify myAssembly.exe /md /il  
```  
  
 Yukarıdaki isteğin başarıyla tamamlanmasından sonra Peverify.exe aşağıdaki iletiyi görüntüler.  
  
```  
All classes and methods in myAssembly.exe Verified  
```  
  
 Aşağıdaki komut, derlemede `myAssembly.exe`uygulanan yöntemler için meta veri doğrulama denetimleri ve MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir. Araç bu denetimleri gerçekleştirmek için gereken süreyi görüntüler.  
  
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
  
 Aşağıdaki komut, derlemede `myAssembly.exe`uygulanan yöntemler için meta veri doğrulama denetimleri ve MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir. Ancak en fazla hata sayısı olan 100'e ulaştığında Peverify.exe durur. Araç belirtilen hata kodlarını dikkate almaz.  
  
```  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 Aşağıdaki komut, yukarıdaki önceki örnekle aynı sonucu üretir, ancak yanıt dosyasında `ignoreErrors.rsp`yoksayılacak hata kodlarını belirtir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](../../../docs/framework/tools/index.md)
- [Verifi, türü güvenli kod yazma](../../../docs/framework/misc/code-access-security-basics.md#typesafe_code)
- [Tür güvenliği ve güvenlik](../../../docs/standard/security/key-security-concepts.md#type-safety-and-security)
- [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
