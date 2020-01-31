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
ms.openlocfilehash: 69a8aabd1d79bb9bb4248259c99124ce50677600
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789240"
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
 Hata ayıklayıcı, bir iş parçacığının yürütmesini denetlemek için `CorDebugThreadState` numaralandırmayı kullanır. Bir iş parçacığının durumu [ICorDebugThread:: SetDebugState](icordebugthread-setdebugstate-method.md) veya [ICorDebugController:: SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) yöntemi kullanılarak ayarlanabilir.  
  
 [BARıNDıRMA API](../../../../docs/framework/unmanaged-api/hosting/index.md) 'sine sunulan bir geri çağırma, ileti balonları, bu nedenle kesintiye uğramış bir durum gerekli değildir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](debugging-enumerations.md)
