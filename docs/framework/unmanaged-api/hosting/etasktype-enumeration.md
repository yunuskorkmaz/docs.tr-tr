---
title: "ETaskType Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ETaskType
api_location: mscoree.dll
api_type: COM
f1_keywords: ETaskType
helpviewer_keywords: ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 52e027c5d2ead70bbd624fafe3021121557cd261
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="etasktype-enumeration"></a>ETaskType Numaralandırması
Tarafından temsil edilen görevi türünü belirtmek değerleri içeren bir [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) veya bir [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) arabirimi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`TT_ADUNLOAD`|Bir uygulama etki alanı kaldırılırken görev arabirimi temsil eder.|  
|`TT_DEBUGGERHELPER`|Arabirimi hata ayıklayıcı yardımcı görev temsil eder.|  
|`TT_FINALIZER`|Arabirimi sonlandırıcıyı görev temsil eder.|  
|`TT_GC`|Arabirimi bir atık toplama görevi temsil eder.|  
|`TT_THREADPOOL_GATE`|Bir ağ geçidi iş parçacığının görevi arabirimi temsil eder.|  
|`TT_THREADPOOL_IOCOMPLETION`|Bir g/ç iş parçacığı görevi veya görev tamamlama bağlantı noktası iş parçacığı görev arabirimi temsil eder.|  
|`TT_THREADPOOL_TIMER`|Zamanlayıcı iş parçacığı görevi arabirimi temsil eder.|  
|`TT_THREADPOOL_WAIT`|Arabirimi bir bekleme iş parçacığının görevi temsil eder.|  
|`TT_THREADPOOL_WORKER`|Bir çalışan iş parçacığının görevi arabirimi temsil eder.|  
|`TT_UNKNOWN`|Görev bilinmiyor.|  
|`TT_USER`|Bir kullanıcı görev arabirimi temsil eder.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma numaralandırmaları](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
