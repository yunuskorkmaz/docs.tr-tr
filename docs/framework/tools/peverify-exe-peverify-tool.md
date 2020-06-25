---
title: Peverify.exe (PEVerify Aracı)
description: Microsoft ara dili (MSIL) kodu & meta verilerin .NET 'teki tür güvenlik standartlarını karşılayıp karşılamadığını belirlemesine yardımcı olması için Peverify.exe (taşınabilir yürütülebilir dosya doğrulaması) kullanın.
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
ms.openlocfilehash: 478c04a45c7f9d3ad568a6bc4a12a89fe786583a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325625"
---
# <a name="peverifyexe-peverify-tool"></a>Peverify.exe (PEVerify aracı)

PEVerify Aracı, Microsoft ara dili (MSIL) oluşturan geliştiricilere (derleyici yazarları ve betik motoru geliştiricileri gibi), MSIL kodunun ve ilişkili meta verilerin tür güvenliği gereksinimlerini karşılayıp karşılamadığını belirlemesine yardımcı olur. Bazı derleyiciler yalnızca belirli dil yapılarını kullanmaktan kaçındığınızda doğrulanabilir şekilde tür kullanımı uyumlu kod üretir. Böyle bir derleyici kullanıyorsanız, kodunuzun tür güvenliğinin tehlikeye çalışmadığını doğrulamak isteyebilirsiniz. MSIL ve meta verileri denetlemek için dosyalarınızda PEVerify aracını çalıştırabilirsiniz.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
peverify filename [options]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Description|  
|--------------|-----------------|  
|*filename*|MSIL ve meta verilerinin denetleneceği taşınabilir yürütülebilir (PE) dosyası.|  
  
|Seçenek|Description|  
|------------|-----------------|  
|**/Break =** *maxErrorCount*|*MaxErrorCount* hatalarından sonra doğrulamayı iptal eder.<br /><br /> Bu parametre .NET Framework sürüm 2.0 ve sonrasında desteklenmez.|  
|**/Saat**|Milisaniye olarak aşağıdaki doğrulama zamanlarını ölçer ve bildirir:<br /><br /> **MD Val. Cycle**<br /> Meta veri doğrulama döngüsü<br /><br /> **MD Val. Pure**<br /> Meta veri doğrulama safı<br /><br /> **Il ver. Cycle**<br /> Microsoft ara dili (MSIL) doğrulama döngüsü<br /><br /> **Il ver saf**<br /> MSIL doğrulaması saf<br /><br /> **Md Val. Cycle** ve **Il ver. Cycle** süreleri, gerekli başlatma ve kapatılma yordamlarını gerçekleştirmek için gereken süreyi içerir. **Md Val. saf** ve **Il ver saf** süreleri yalnızca doğrulamayı veya doğrulamayı gerçekleştirmek için gereken süreyi yansıtır.|  
|**/Help**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/HRESULT**|Onaltılık biçimde hata kodlarını görüntüler.|  
|**/Ignore =** *Hex. Code* [, *Hex. Code*]|Belirtilen hata kodlarını dikkate almaz.|  
|**/Ignore = @** *ResponseFile*|Belirtilen yanıt dosyasında listelenen hata kodlarını dikkate almaz.|  
|**/İl**|*Dosya adı*tarafından belirtilen derlemede uygulanan metotlar için MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir. Araç, **/quiet** seçeneğini belirtmediğiniz müddetçe bulunan her bir sorun için ayrıntılı açıklamalar döndürür.|  
|**/MD**|*Dosya adı*tarafından belirtilen derlemede meta veri doğrulama denetimleri gerçekleştirir. Bu seçenek, dosyanın içindeki tam meta veri yapısını gösterir ve karşılaşılan tüm doğrulama sorunlarını raporlar.|  
|**/nologo**|Ürün sürümü ve telif hakkı bilgilerinin görüntülenmesini önler.|  
|**/nosymbols**|.NET Framework sürüm 2.0'da, geriye doğru uyumluluk için satır numaralarını gizler.|  
|**/**|Sessiz mod kullanılacağını belirtir; doğrulama sorunu raporlarının çıkışını önler. Peverify.exe dosyanın tür kullanımı uyumlu olup olmadığını bildirmeye devam eder, ancak tür güvenliği doğrulamasını önleyen sorunlar hakkında bilgi vermez.|  
|`/transparent`|Yalnızca saydam yöntemleri doğrulayın.|  
|**/Unique**|Yinelenen hata kodlarını dikkate almaz.|  
|**/verbose**|.NET Framework sürüm 2. 0'da, MSIL doğrulama iletilerinde ek bilgiler görüntüler.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı, güvenlik ve yalıtım mekanizmalarını zorlamaya yardımcı olmak için uygulama kodunun tür kullanımı uyumlu yürütülmesini kullanır. Normalde, güvenlik ilkesini güvenilir ancak doğrulanamayan kodun yürütülmesine izin verecek şekilde ayarlayabilseniz de, [doğruıolarak olmayan tür güvenli](../../standard/security/key-security-concepts.md#type-safety-and-security) olmayan kod çalıştırılamaz.  
  
 **/Md** veya **/Il** seçeneklerinin hiçbiri belirtilmediyse Peverify.exe her iki denetim türünü de gerçekleştirir. Peverify.exe önce **/md** denetimleri gerçekleştirir. Hata yoksa, **/Il** denetimleri yapılır. Hem **/md** hem de **/Il**belirtirseniz, meta verilerde hata olsa bile **/Il** denetimleri yapılır. Bu nedenle, meta veri hatası yoksa, **PEVerify** *Dosya* adı **PEVerify** *dosya adı* **/md** **/Il**ile eşdeğerdir.  
  
 Peverify.exe, veri akışı analizine ve geçerli meta veriye ilişkin birkaç yüz kuralı içeren bir listeye göre kapsamlı MSIL doğrulama denetimleri yapar. Peverify.exe denetimleri hakkında ayrıntılı bilgi için Windows SDK araçlar Geliştirici Kılavuzu klasöründe "meta veri doğrulama belirtimi" ve "MSIL yönerge kümesi belirtimi" başlığına bakın.  
  
.NET Framework sürüm 2,0 veya üzeri `byref` , aşağıdaki MSIL yönergeleri kullanılarak belirtilen doğrulanabilir dönüşler destekler: `dup` , `ldsflda` , `ldflda` , `ldelema` , `call` ve `unbox` .  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, derlemede uygulanan yöntemler için meta veri doğrulama denetimleri ve MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir `myAssembly.exe` .  
  
```console  
peverify myAssembly.exe /md /il  
```  
  
 Yukarıdaki isteğin başarıyla tamamlanmasından sonra Peverify.exe aşağıdaki iletiyi görüntüler.  
  
```output
All classes and methods in myAssembly.exe Verified  
```  
  
 Aşağıdaki komut, derlemede uygulanan yöntemler için meta veri doğrulama denetimleri ve MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir `myAssembly.exe` . Araç bu denetimleri gerçekleştirmek için gereken süreyi görüntüler.  
  
```console  
peverify myAssembly.exe /md /il /clock  
```  
  
 Yukarıdaki isteğin başarıyla tamamlanmasından sonra Peverify.exe aşağıdaki iletiyi görüntüler.  
  
```output
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 Aşağıdaki komut, derlemede uygulanan yöntemler için meta veri doğrulama denetimleri ve MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir `myAssembly.exe` . Ancak en fazla hata sayısı olan 100'e ulaştığında Peverify.exe durur. Araç belirtilen hata kodlarını dikkate almaz.  
  
```console  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 Aşağıdaki komut, yukarıdaki önceki örnekle aynı sonucu üretir, ancak yanıt dosyasında yoksayılacak hata kodlarını belirtir `ignoreErrors.rsp` .  
  
```console  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 Yanıt dosyası hata kodlarının virgülle ayrılmış listesini içerebilir.  
  
```text
0x12345678, 0xABCD1234  
```  
  
 Alternatif olarak, yanıt dosyası her satırda bir hata kodu olacak şekilde de biçimlendirilebilir.  
  
```text
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Verifi, türü güvenli kod yazma](../misc/code-access-security-basics.md#typesafe_code)
- [Tür güvenliği ve güvenlik](../../standard/security/key-security-concepts.md#type-safety-and-security)
- [Komut Istemleri](developer-command-prompt-for-vs.md)
