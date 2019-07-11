---
title: ICorDebugManagedCallback::BreakpointSetError Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.BreakpointSetError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::BreakpointSetError
helpviewer_keywords:
- BreakpointSetError method [.NET Framework debugging]
- ICorDebugManagedCallback::BreakpointSetError method [.NET Framework debugging]
ms.assetid: f2b773a4-c4d0-429c-9717-51d6e2ed86af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3ef4b284676608363281e04087f6435dcb1ef74
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759844"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a>ICorDebugManagedCallback::BreakpointSetError Yöntemi
Hata ayıklayıcı ortak dil çalışma zamanı öncesinde bir işlev yalnızca derlenmiş zamanında (JIT) ayarlanan bir kesme noktası doğru şekilde bağlanamıyor olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 [in] İlişkisiz bir kesme noktası içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.  
  
 `pThread`  
 [in] İlişkisiz bir kesme noktası içeren iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.  
  
 `pBreakpoint`  
 [in] İlişkisiz kesme noktasını temsil eden bir Icordebugbreakpoint nesne işaretçisi.  
  
 `dwError`  
 [in] Hata gösteren bir tamsayı.  
  
## <a name="remarks"></a>Açıklamalar  
 Belirtilen kesme noktası hiçbir zaman ulaşırsınız. Hata ayıklayıcı, devre dışı bırakma ve onu yeniden bağlayın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
