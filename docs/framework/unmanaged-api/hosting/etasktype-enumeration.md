---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73098077e3860d3f4a8a02921ecedf8dff24165b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774052"
---
# <a name="etasktype-enumeration"></a>ETaskType Numaralandırması
Tarafından temsil edilen bir görev türünü gösteren değerleri içeren bir [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) veya [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) arabirimi.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
  
|Üye|Açıklama|  
|------------|-----------------|  
|`TT_ADUNLOAD`|Arabirimi, bir uygulama etki alanı kaldırma görevi temsil eder.|  
|`TT_DEBUGGERHELPER`|Arabirimi, bir hata ayıklayıcı Yardımcısı görevi temsil eder.|  
|`TT_FINALIZER`|Arabirimi, bir sonlandırıcı görevi temsil eder.|  
|`TT_GC`|Arabirimi, bir atık toplama görevi temsil eder.|  
|`TT_THREADPOOL_GATE`|Arabirimi, bir ağ geçidi iş parçacığı görevi temsil eder.|  
|`TT_THREADPOOL_IOCOMPLETION`|Arabirimi, bir g/ç iş parçacığı görevi ya da bir tamamlanma bağlantı noktası iş parçacığı görevi temsil eder.|  
|`TT_THREADPOOL_TIMER`|Arabirimi, bir zamanlayıcı iş parçacığı görevi temsil eder.|  
|`TT_THREADPOOL_WAIT`|Arabirimi, bir bekleme iş parçacığı görevi temsil eder.|  
|`TT_THREADPOOL_WORKER`|Arabirimi, bir çalışan iş parçacığı görevi temsil eder.|  
|`TT_UNKNOWN`|Görev bilinmiyor.|  
|`TT_USER`|Arabirimi, bir kullanıcı görevini temsil eder.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
