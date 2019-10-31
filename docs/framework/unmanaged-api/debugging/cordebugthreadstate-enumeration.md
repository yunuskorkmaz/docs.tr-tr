---
title: CorDebugThreadState Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugThreadState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugThreadState
helpviewer_keywords:
- CorDebugThreadState enumeration [.NET Framework debugging]
ms.assetid: a3ccdf18-4ec6-494d-9024-48e5c8c724f5
topic_type:
- apiref
ms.openlocfilehash: 1ff36e8ef6b7c02eea5b02bc22587bc3889df093
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133698"
---
# <a name="cordebugthreadstate-enumeration"></a>CorDebugThreadState Numaralandırması
Hata ayıklama için bir iş parçacığının durumunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`THREAD_RUN`|Bir hata ayıklama olayı gerçekleşmediği takdirde iş parçacığı serbestçe çalışır.|  
|`THREAD_SUSPEND`|İş parçacığı çalıştırılamıyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklayıcı, bir iş parçacığının yürütmesini denetlemek için `CorDebugThreadState` numaralandırmayı kullanır. Bir iş parçacığının durumu [ICorDebugThread:: SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) veya [ICorDebugController:: SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) yöntemi kullanılarak ayarlanabilir.  
  
 [BARıNDıRMA API](../../../../docs/framework/unmanaged-api/hosting/index.md) 'sine sunulan bir geri çağırma, ileti balonları, bu nedenle kesintiye uğramış bir durum gerekli değildir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
