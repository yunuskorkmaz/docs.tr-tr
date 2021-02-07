---
description: 'Bu konuda daha fazla bilgi edinin: CorDebugThreadState numaralandırması'
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
ms.openlocfilehash: 0cf83ee31547e49ccc7d09e0ab4ee85548688b36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661815"
---
# <a name="cordebugthreadstate-enumeration"></a>CorDebugThreadState Numaralandırması

Hata ayıklama için bir iş parçacığının durumunu belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`THREAD_RUN`|Bir hata ayıklama olayı gerçekleşmediği takdirde iş parçacığı serbestçe çalışır.|  
|`THREAD_SUSPEND`|İş parçacığı çalıştırılamıyor.|  
  
## <a name="remarks"></a>Açıklamalar  

 Hata ayıklayıcı, `CorDebugThreadState` bir iş parçacığının yürütmesini denetlemek için sabit listesini kullanır. Bir iş parçacığının durumu [ICorDebugThread:: SetDebugState](icordebugthread-setdebugstate-method.md) veya [ICorDebugController:: SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) yöntemi kullanılarak ayarlanabilir.  
  
 [BARıNDıRMA API](../hosting/index.md) 'sine sunulan bir geri çağırma, ileti balonları, bu nedenle kesintiye uğramış bir durum gerekli değildir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
