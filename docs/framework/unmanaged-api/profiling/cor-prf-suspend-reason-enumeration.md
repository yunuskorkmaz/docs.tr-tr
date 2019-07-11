---
title: COR_PRF_SUSPEND_REASON Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_SUSPEND_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SUSPEND_REASON
helpviewer_keywords:
- COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e084bc957eca9474078ed5ca3aef0276361dbe1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745530"
---
# <a name="corprfsuspendreason-enumeration"></a>COR_PRF_SUSPEND_REASON Numaralandırması
Çalışma zamanı askıya alındığından nedenini gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum {  
    COR_PRF_SUSPEND_OTHER                   = 0x00,  
    COR_PRF_SUSPEND_FOR_GC                  = 0x01,  
    COR_PRF_SUSPEND_FOR_APPDOMAIN_SHUTDOWN  = 0x02,  
    COR_PRF_SUSPEND_FOR_CODE_PITCHING       = 0x03,  
    COR_PRF_SUSPEND_FOR_SHUTDOWN            = 0x04,  
    COR_PRF_SUSPEND_FOR_INPROC_DEBUGGER     = 0x06,  
    COR_PRF_SUSPEND_FOR_GC_PREP             = 0x07,    COR_PRF_SUSPEND_FOR_REJIT               = 8  
} COR_PRF_SUSPEND_REASON;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|Çalışma zamanı belirlenemeyen bir nedenden dolayı askıya alınır.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|Çalışma zamanı, çöp toplama isteğine hizmet askıya alınır.<br /><br /> Çöp toplama ile ilgili geri çağırmalar arasında oluşan [Icorprofilercallback::runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) ve [Icorprofilercallback::runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) geri çağırmalar.|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|Çalışma zamanı askıya böylece bir `AppDomain` kapatılabilir.<br /><br /> Çalışma zamanı askıya alındı, ancak çalışma zamanının hangi iş parçacığı bulunan belirleyecek `AppDomain` diğer bir deyişle kapatmalı ve bunlar devam edince iptal etmek için bunları ayarlayın. Var olan hiçbir `AppDomain`-bu askıya alma sırasında belirli geri çağırmalar.|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|Kod pitching gerçekleştirilmesi, çalışma zamanı askıya alınır.<br /><br /> Kod pitching yalnızca just-ın-time (JIT) derleyici etkin kod pitching ile etkin olduğunda ensues. Pitching geri çağırmaları ortaya arasında kod `ICorProfilerCallback::RuntimeSuspendFinished` ve `ICorProfilerCallback::RuntimeResumeStarted` geri çağırmalar. **Not:**  Bu değer, 2. 0'kullanılmaması CLR JIT işlevleri .NET Framework sürüm 2.0, aralık değil.|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|Böylece kapanabilir çalışma zamanı askıya alınır. İşlemi tamamlamak için tüm iş parçacıkları askıya gerekir.|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|Çalışma zamanı, işlemdeki hata ayıklama için askıya alındı.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|Çalışma zamanı, çöp toplama işlemi için hazırlamak üzere askıya alınır.|  
|`COR_PRF_SUSPEND_FOR_REJIT`|Çalışma zamanı JIT yeniden derlemesi için askıya alındı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yönetilmeyen kodda olan tüm çalışma zamanı iş parçacığı, çalışma zamanı yeniden devam edene dek bu noktada, ayrıca askıya alınır ve çalışma zamanının yeniden girmeyi deneyin kadar çalışmaya devam etmesine izin verilir. Bu, çalışma zamanı girin yeni iş parçacıkları için de geçerlidir. Çalışma zamanı içinde tüm iş parçacıkları kesilebilir kodda olmaları durumunda hemen askıya veya kesilebilir kod ulaşmadan zaman askıya istenir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Sabit Listeleri](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
