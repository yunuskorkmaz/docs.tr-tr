---
title: "Peverify.exe (PEVerify Aracı)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- portable executable files, PEVerify
- verifying MSIL and metadata
- PEVerify tool
- type safety requirements
- MSIL
- PEverify.exe
- PE files, PEVerify
ms.assetid: f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5acb6da7c68f899daa4144e897e9ec31fcfa868a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="peverifyexe-peverify-tool"></a>Peverify.exe (PEVerify Aracı)
PEVerify aracı, Microsoft ara dili (MSIL) (derleyici yazıcıları, betik motor geliştiricileri vb.) oluşturan geliştiricilere, MSIL kodlarının ve ilişkili meta verilerinin güvenlik koşullarına uygun olup olmadığını belirlemede yardımcı olur. Bazı derleyiciler yalnızca belirli dil yapılarını kullanmaktan kaçındığınızda doğrulanabilir şekilde tür kullanımı uyumlu kod üretir. Bir geliştirici olarak, bilgisayar kullanıyorsanız, kodunuzun tür güvenliğini tehlikeye atmadığınızı doğrulamak isteyebilirsiniz. Bu durumda, MSIL ve meta verileri denetlemek için dosyalarınızda PEVerify aracını çalıştırabilirsiniz.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
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
|**/break=** *maxErrorCount*|İptalleri doğrulamadan sonra *maxErrorCount* hataları.<br /><br /> Bu parametre .NET Framework sürüm 2.0 ve sonrasında desteklenmez.|  
|**/Clock**|Milisaniye olarak aşağıdaki doğrulama zamanlarını ölçer ve bildirir:<br /><br /> **MD elden döngüsü**<br /> Meta veri doğrulama döngüsü<br /><br /> **MD elden saf**<br /> Meta veri doğrulama safı<br /><br /> **IL sürüm döngüsü**<br /> Microsoft ara dili (MSIL) doğrulama döngüsü<br /><br /> **Saf IL Ver**<br /> MSIL doğrulaması saf<br /><br /> **MD elden döngüsü** ve **IL sürüm döngüsü** kez dahil etmeniz gereken başlatma ve kapatma işlemleri gerçekleştirmek için gereken süre. **MD elden saf** ve **IL Ver saf** saatler doğrulama veya yalnızca doğrulama gerçekleştirmek için gereken süreyi yansıtır.|  
|**/ Help**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/HRESULT**|Onaltılık biçimde hata kodlarını görüntüler.|  
|**/ignore=** *hex.code* [, *hex.code*]|Belirtilen hata kodlarını dikkate almaz.|  
|**Yoksay = @** *responseFile*|Belirtilen yanıt dosyasında listelenen hata kodlarını dikkate almaz.|  
|**/il**|Belirtilen derleme uygulanan yöntemleri için MSIL tür güvenlik doğrulama denetimleri gerçekleştirir *filename*. Belirtmediğiniz sürece bulunan her sorun için ayrıntılı açıklamalar aracı döndürür **/quiet** seçeneği.|  
|**/md**|Tarafından belirtilen derlemedeki meta veri doğrulama denetimlerini gerçekleştiren *filename*. Bu, dosya içindeki tüm meta veri yapısını ölçer ve karşılaşılan tüm doğrulama sorunlarını rapor eder.|  
|**/nologo**|Ürün sürümü ve telif hakkı bilgilerinin görüntülenmesini önler.|  
|**/nosymbols**|.NET Framework sürüm 2.0'da, geriye doğru uyumluluk için satır numaralarını gizler.|  
|**/quiet**|Sessiz mod kullanılacağını belirtir; doğrulama sorunu raporlarının çıkışını önler. Peverify.exe dosyanın tür kullanımı uyumlu olup olmadığını bildirmeye devam eder, ancak tür güvenliği doğrulamasını önleyen sorunlar hakkında bilgi vermez.|  
|`/transparent`|Yalnızca saydam yöntemleri doğrulayın.|  
|**/ benzersiz**|Yinelenen hata kodlarını dikkate almaz.|  
|**/verbose**|.NET Framework sürüm 2. 0'da, MSIL doğrulama iletilerinde ek bilgiler görüntüler.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı, güvenlik ve yalıtım mekanizmalarını zorlamaya yardımcı olmak için uygulama kodunun tür kullanımı uyumlu yürütülmesini kullanır. Normalde, kodları [doğrulanabilir şekilde tür uyumlu](http://msdn.microsoft.com/library/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc) çalışamaz, güvenilen ancak doğrulanamaz kod yürütmeyi izin veren güvenlik ilkesini ayarlayabilirsiniz.  
  
 Ne **/md** ya da **/il** seçenekleri belirtilirse, Peverify.exe her iki tür denetimler gerçekleştirir. Peverify.exe gerçekleştirir **/md** ilk denetler. Hiçbir hatalar varsa **/il** denetimleri yapılır. Her ikisini de belirtirseniz, **/md** ve **/il**, **/il** meta verilerde hatalar olsa denetimleri yapılır. Bu nedenle, hiçbir meta veri hatası yoksa **peverify** *filename* eşdeğerdir **peverify** *filename* **/md** **/il**.  
  
 Peverify.exe, veri akışı analizine ve geçerli meta veriye ilişkin birkaç yüz kuralı içeren bir listeye göre kapsamlı MSIL doğrulama denetimleri yapar. "Meta veri doğrulama belirtimi" ve "MSIL yönerge kümesi belirtimi" araçları Geliştirici Kılavuzu klasöründe Peverify.exe gerçekleştirir denetimleri ayrıntılı bilgi için bkz: [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
 .NET Framework sürüm 2.0 veya üstü doğrulanabilen desteklediğini unutmayın `byref` aşağıdaki MSIL yönergeleri kullanarak belirtilen döndürür: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` ve `unbox`.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komutu derlemede uygulanan yöntemleri için meta veri doğrulama denetimlerini ve MSIL tür güvenlik doğrulama denetimleri gerçekleştirir `myAssembly.exe`.  
  
```  
peverify myAssembly.exe /md /il  
```  
  
 Yukarıdaki isteğin başarıyla tamamlanmasından sonra Peverify.exe aşağıdaki iletiyi görüntüler.  
  
```  
All classes and methods in myAssembly.exe Verified  
```  
  
 Aşağıdaki komutu derlemede uygulanan yöntemleri için meta veri doğrulama denetimlerini ve MSIL tür güvenlik doğrulama denetimleri gerçekleştirir `myAssembly.exe`. Araç bu denetimleri gerçekleştirmek için gereken süreyi görüntüler.  
  
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
  
 Aşağıdaki komutu derlemede uygulanan yöntemleri için meta veri doğrulama denetimlerini ve MSIL tür güvenlik doğrulama denetimleri gerçekleştirir `myAssembly.exe`. Ancak en fazla hata sayısı olan 100'e ulaştığında Peverify.exe durur. Araç belirtilen hata kodlarını dikkate almaz.  
  
```  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 Aşağıdaki komut yukarıdaki önceki örnekteki gibi aynı sonucu verir, ancak yanıt dosyasında yoksaymak için hata kodlarını belirtir `ignoreErrors.rsp`.  
  
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
 [NIB: Doğrulanabilir şekilde tür kullanımı uyumlu kod yazma](http://msdn.microsoft.com/library/d18f10ef-3b48-4f47-8726-96714021547b)  
 [Tür güvenliği ve güvenlik](http://msdn.microsoft.com/library/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
