---
description: 'Daha fazla bilgi edinin: ETaskType numaralandırması'
title: ETaskType Numaralandırması
ms.date: 03/30/2017
api_name:
- ETaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ETaskType
helpviewer_keywords:
- ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type:
- apiref
ms.openlocfilehash: 7cb241765b2ff3b4a3402221c6b3e2b7ff6305c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785412"
---
# <a name="etasktype-enumeration"></a>ETaskType Numaralandırması

Bir [ICLRTask](iclrtask-interface.md) veya [IHostTask](ihosttask-interface.md) arabirimi tarafından temsil edilen görevin türünü gösteren değerleri içerir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum ETaskType {  
    TT_DEBUGGERHELPER           = 0x1,  
    TT_GC                       = 0x2,  
    TT_FINALIZER                = 0x4,  
    TT_THREADPOOL_TIMER         = 0x8,  
    TT_THREADPOOL_GATE          = 0x10,  
    TT_THREADPOOL_WORKER        = 0x20,  
    TT_THREADPOOL_IOCOMPLETION  = 0x40,  
    TT_ADUNLOAD                 = 0x80,  
    TT_USER                     = 0x100,  
    TT_THREADPOOL_WAIT          = 0x200,  
    TT_UNKNOWN                  = 0x80000000  
} ETaskType;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`TT_ADUNLOAD`|Arabirim bir uygulama etki alanı kaldırma görevini temsil eder.|  
|`TT_DEBUGGERHELPER`|Arabirim bir hata ayıklayıcı Yardımcısı görevini temsil eder.|  
|`TT_FINALIZER`|Arabirim bir Sonlandırıcı görevini temsil eder.|  
|`TT_GC`|Arabirim bir çöp toplama görevini temsil eder.|  
|`TT_THREADPOOL_GATE`|Arabirim bir kapı iş parçacığı görevini temsil eder.|  
|`TT_THREADPOOL_IOCOMPLETION`|Arabirim bir g/ç iş parçacığı görevini veya tamamlama bağlantı noktası iş parçacığı görevini temsil eder.|  
|`TT_THREADPOOL_TIMER`|Arabirim bir zamanlayıcı iş parçacığı görevini temsil eder.|  
|`TT_THREADPOOL_WAIT`|Arabirim bir bekleme iş parçacığı görevini temsil eder.|  
|`TT_THREADPOOL_WORKER`|Arabirim bir çalışan iş parçacığı görevini temsil eder.|  
|`TT_UNKNOWN`|Görev bilinmiyor.|  
|`TT_USER`|Arabirim bir Kullanıcı görevini temsil eder.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Numaralandırmaları](hosting-enumerations.md)
