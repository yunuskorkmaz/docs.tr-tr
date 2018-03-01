---
title: "COR_PRF_SUSPEND_REASON Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 713360b3cdc30ce7bca3e0df115016d66e59b0df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corprfsuspendreason-enumeration"></a>COR_PRF_SUSPEND_REASON Numaralandırması
Çalışma zamanı askıya alınmış nedenini gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|Çalışma zamanı bir atık toplama isteğine hizmet askıya alınır.<br /><br /> Çöp toplama ile ilgili geri aramalar arasında ortaya [Icorprofilercallback::runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) ve [Icorprofilercallback::runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) geri aramalar.|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|Çalışma zamanı askıya böylece bir `AppDomain` kapatılabilir.<br /><br /> Çalışma zamanı askıya alınmış durumdayken, çalışma zamanı hangi iş parçacığı bulunan belirleyecek `AppDomain` diğer bir deyişle kapatılır ve bunlar sürdürdüğünüzde iptal etmek için bunları ayarlayın. Var olan hiçbir `AppDomain`-bu askıya alma sırasında belirli geri aramalar.|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|Böylece kodu pitching oluşabilir çalışma zamanı askıya alındı.<br /><br /> Kod pitching yalnızca tam zamanında (JIT) derleyici etkin kodu pitching ile etkin olduğunda ensues. Kod pitching geri aramalar ortaya arasında `ICorProfilerCallback::RuntimeSuspendFinished` ve `ICorProfilerCallback::RuntimeResumeStarted` geri aramalar. **Not:** bu değer 2. 0'kullanılmaması CLR JIT işlevlerini .NET Framework sürüm 2.0, aralık değil.|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|Böylece kapatmak, çalışma zamanı'askıya alındı. İşlemi tamamlamak için tüm iş parçacıklarını askıya alma gerekir.|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|Çalışma zamanı işlemde hata ayıklamak için askıya alındı.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|Çöp toplama için hazırlamak için çalışma zamanı askıya alındı.|  
|`COR_PRF_SUSPEND_FOR_REJIT`|Çalışma zamanı JIT yeniden derlenmek üzere askıya alınır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yönetilmeyen kodunda tüm çalışma zamanı iş parçacıklarının bunlar çalışma zamanı yeniden devam edene dek bu noktada bunlar da askıya alınacak çalışma zamanı yeniden girmeyi deneyin kadar çalışmaya devam etmesine izin verilir. Bu durum, çalışma zamanı girin yeni iş parçacığı için de geçerlidir. Çalışma Zamanı Modülü içindeki tüm iş parçacıklarının kesilebilir kodda olmaları durumunda hemen askıya, ya da bunlar kesilebilir kod ulaştığında askıya istenir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil Oluşturma Sabit Listeleri](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
