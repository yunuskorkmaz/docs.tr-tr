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
ms.openlocfilehash: 9d5f8c80937c36e975d42d6efb0a83295cb28be9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73104977"
---
# <a name="peverifyexe-peverify-tool"></a>Peverify.exe (PEVerify Aracı)
PEVerify aracı, Microsoft ara dili (MSIL) (derleyici yazıcıları, betik motor geliştiricileri vb.) oluşturan geliştiricilere, MSIL kodlarının ve ilişkili meta verilerinin güvenlik koşullarına uygun olup olmadığını belirlemede yardımcı olur. Bazı derleyiciler yalnızca belirli dil yapılarını kullanmaktan kaçındığınızda doğrulanabilir şekilde tür kullanımı uyumlu kod üretir. Bir geliştirici olarak, bilgisayar kullanıyorsanız, kodunuzun tür güvenliğini tehlikeye atmadığınızı doğrulamak isteyebilirsiniz. Bu durumda, MSIL ve meta verileri denetlemek için dosyalarınızda PEVerify aracını çalıştırabilirsiniz.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
peverify filename [options]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*filename*|MSIL ve meta verilerinin denetleneceği taşınabilir yürütülebilir (PE) dosyası.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/break=** *maxErrorCount*|*MaxErrorCount* hatalarından sonra doğrulamayı iptal eder.<br /><br /> Bu parametre .NET Framework sürüm 2.0 ve sonrasında desteklenmez.|  
|**/saat**|Milisaniye olarak aşağıdaki doğrulama zamanlarını ölçer ve bildirir:<br /><br /> **MD Val. döngüsü**<br /> Meta veri doğrulama döngüsü<br /><br /> **MD Val. saf**<br /> Meta veri doğrulama safı<br /><br /> **IL Ver. döngüsü**<br /> Microsoft ara dili (MSIL) doğrulama döngüsü<br /><br /> **IL Ver saf**<br /> MSIL doğrulaması saf<br /><br /> **MD Val döngüsü** ve IL **Ver. çevrim** süreleri, gerekli başlatma ve kapatma yordamlarını gerçekleştirmek için gereken süreyi içerir. **MD Val. saf** ve IL Ver **saf** kez doğrulama veya doğrulama gerçekleştirmek için gerekli süreyi yansıtır.|  
|**/yardım**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/hresult**|Onaltılık biçimde hata kodlarını görüntüler.|  
|**/ignore=** *hex.code* [, *hex.code*]|Belirtilen hata kodlarını dikkate almaz.|  
|**/ignore=@** *yanıtıDosya*|Belirtilen yanıt dosyasında listelenen hata kodlarını dikkate almaz.|  
|**/il**|*Dosya adı*ile belirtilen derlemede uygulanan yöntemler için MSIL türü güvenlik doğrulama denetimleri gerçekleştirir. Araç, **/sessiz** seçeneğini belirtmediğiniz sürece bulunan her sorun için ayrıntılı açıklamalar döndürür.|  
|**/md**|*Dosya adı*ile belirtilen derlemede meta veri doğrulama denetimleri gerçekleştirir. Bu, dosya içindeki tüm meta veri yapısını ölçer ve karşılaşılan tüm doğrulama sorunlarını rapor eder.|  
|**/nologo**|Ürün sürümü ve telif hakkı bilgilerinin görüntülenmesini önler.|  
|**/nosymbols**|.NET Framework sürüm 2.0'da, geriye doğru uyumluluk için satır numaralarını gizler.|  
|**/sessiz**|Sessiz mod kullanılacağını belirtir; doğrulama sorunu raporlarının çıkışını önler. Peverify.exe dosyanın tür kullanımı uyumlu olup olmadığını bildirmeye devam eder, ancak tür güvenliği doğrulamasını önleyen sorunlar hakkında bilgi vermez.|  
|`/transparent`|Yalnızca saydam yöntemleri doğrulayın.|  
|**/benzersiz**|Yinelenen hata kodlarını dikkate almaz.|  
|**/ayrıntılı**|.NET Framework sürüm 2. 0'da, MSIL doğrulama iletilerinde ek bilgiler görüntüler.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı, güvenlik ve yalıtım mekanizmalarını zorlamaya yardımcı olmak için uygulama kodunun tür kullanımı uyumlu yürütülmesini kullanır. Normalde, [doğrulanabilir türde güvenli](../../standard/security/key-security-concepts.md#type-safety-and-security) olmayan kod çalıştırılamaz, ancak güvenilen ancak doğrulanamayan kodun yürütülmesine izin verecek güvenlik ilkesi ayarlayabilirsiniz.  
  
 **/md** veya **/il** seçenekleri belirtilmemişse, Peverify.exe her iki denetim türünü de gerçekleştirir. Peverify.exe ilk gerçekleştirir **/ md** kontrolleri. Hata **yoksa, /il** denetimleri yapılır. Hem **/md** hem de **/il**, **/il** denetimleri belirtirseniz, meta verilerde hata olsa bile yapılır. Bu nedenle, meta veri hatası yoksa, **peverify** dosya *adı* **peverify** *dosya adı* **/md /il** **/il**' e eşdeğerdir.  
  
 Peverify.exe, veri akışı analizine ve geçerli meta veriye ilişkin birkaç yüz kuralı içeren bir listeye göre kapsamlı MSIL doğrulama denetimleri yapar. Peverify.exe'nin gerçekleştirdiği denetimler hakkında ayrıntılı bilgi için Windows SDK'daki Araçlar Geliştiricileri Kılavuzu klasöründeki "Meta veri doğrulama belirtimi" ve "MSIL Yönerge Sayarki" bölümüne bakın.  
  
 .NET Framework sürüm 2.0 veya daha sonra `byref` aşağıdaki MSIL yönergeleri kullanılarak `dup` `ldsflda`belirtilen `ldflda` `ldelema`doğrulanabilir getirileri desteklediğini unutmayın: , , , `call` ve `unbox`.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, derlemede `myAssembly.exe`uygulanan yöntemler için meta veri doğrulama denetimleri ve MSIL türü güvenlik doğrulama denetimleri gerçekleştirir.  
  
```console  
peverify myAssembly.exe /md /il  
```  
  
 Yukarıdaki isteğin başarıyla tamamlanmasından sonra Peverify.exe aşağıdaki iletiyi görüntüler.  
  
```output
All classes and methods in myAssembly.exe Verified  
```  
  
 Aşağıdaki komut, derlemede `myAssembly.exe`uygulanan yöntemler için meta veri doğrulama denetimleri ve MSIL türü güvenlik doğrulama denetimleri gerçekleştirir. Araç bu denetimleri gerçekleştirmek için gereken süreyi görüntüler.  
  
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
  
 Aşağıdaki komut, derlemede `myAssembly.exe`uygulanan yöntemler için meta veri doğrulama denetimleri ve MSIL türü güvenlik doğrulama denetimleri gerçekleştirir. Ancak en fazla hata sayısı olan 100'e ulaştığında Peverify.exe durur. Araç belirtilen hata kodlarını dikkate almaz.  
  
```console  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 Aşağıdaki komut yukarıdaki önceki örnekle aynı sonucu üretir, ancak yanıt dosyasında `ignoreErrors.rsp`yoksayılaması gereken hata kodlarını belirtir.  
  
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
- [Doğrulanabilir Tür-Güvenli Kod Yazma](../misc/code-access-security-basics.md#typesafe_code)
- [Tip Güvenliği ve Güvenliği](../../standard/security/key-security-concepts.md#type-safety-and-security)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
