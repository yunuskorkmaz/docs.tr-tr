---
title: fatalExecutionEngineError MDA
ms.date: 03/30/2017
helpviewer_keywords:
- corrupted CLR
- fatal execution error
- terminated processes
- unexpected terminations
- fatal errors
- MDAs (managed debugging assistants), fatal errors
- process termination
- FatalExecutionEngineError MDA
- managed debugging assistants (MDAs), fatal errors
ms.assetid: 8b559e44-2393-4e4e-8160-7558d37a4a89
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3fd58ae8f73fd932df641ea96a44ff618dd139e2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052800"
---
# <a name="fatalexecutionengineerror-mda"></a>fatalExecutionEngineError MDA
`fatalExecutionEngineError` Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanında (CLR) önemli bir hata algılandığında etkinleştirilir. İşlem sonlandırılacak.  
  
## <a name="symptoms"></a>Belirtiler  
 Beklenmeyen işlem sonlandırma. Çeşitli nedenlerden dolayı bir CLR hatası gerçekleşebildiğinden diğer belirtiler belirlenemez.  
  
## <a name="cause"></a>Sebep  
 CLR 'nin bozulmuş olması. Bu, genellikle hatalı oluşturulmuş platform çağırma işlevlerine yapılan çağrılar ve CLR 'ye geçersiz veri geçirme gibi birçok sorun nedeniyle veri bozulması nedeniyle oluşur.  
  
## <a name="resolution"></a>Çözüm  
 Ek Mdaları etkinleştirmek sorunu belirlemenize yardımcı olur. Aşağıdaki Mdalar, sorunu tanılamak için özellikle yararlı olabilir:  
  
- [invalidOverlappedToPinvoke](invalidoverlappedtopinvoke-mda.md)  
  
- [overlappedFreeError](overlappedfreeerror-mda.md)  
  
- [pInvokeStackImbalance](pinvokestackimbalance-mda.md)  
  
- [gcUnmanagedToManaged](gcunmanagedtomanaged-mda.md)  
  
- [gcManagedToUnmanaged](gcmanagedtounmanaged-mda.md)  
  
- [callbackOnCollectedDelegate](callbackoncollecteddelegate-mda.md)  
  
- [reportAvOnComRelease](reportavoncomrelease-mda.md)  
  
- [invalidVariant](invalidvariant-mda.md)  
  
- [invalidIUnknown](invalidiunknown-mda.md)  
  
- [raceOnRCWCleanup](raceonrcwcleanup-mda.md)  
  
- [invalidFunctionPointerInDelegate](invalidfunctionpointerindelegate-mda.md)  
  
- [invalidGCHandleCookie](invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA çalışma zamanının davranışı üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Kritik hataya neden olan CLR işlevinin adresi, hatanın oluştuğu iş parçacığının KIMLIĞI ve hata kodu.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution.Cer>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
