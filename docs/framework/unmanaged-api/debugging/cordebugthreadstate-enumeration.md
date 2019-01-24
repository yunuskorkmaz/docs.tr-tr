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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2296f6e386f35aed91a8aea4392a9cd00ec27ccb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724372"
---
# <a name="cordebugthreadstate-enumeration"></a>CorDebugThreadState Numaralandırması
Hata ayıklama için bir iş parçacığı durumunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`THREAD_RUN`|İş parçacığı, ücretsiz, hata ayıklama olayı gerçekleşmediği sürece çalıştırır.|  
|`THREAD_SUSPEND`|İş parçacığı çalıştıramazsınız.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklayıcı kullanan `CorDebugThreadState` bir iş parçacığının yürütmesini denetlemek için sabit listesi. Bir iş parçacığı durumunu kullanarak ayarlayabilirsiniz [Icordebugthread::setdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) veya [Icordebugcontroller::setallthreadsdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) yöntemi.  
  
 Sağlanan bir geri çağırma [API'sini barındıran](../../../../docs/framework/unmanaged-api/hosting/index.md) kesintiye uğramış bir duruma gerekli olmadığı için ileti Pompalama, sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDegug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
