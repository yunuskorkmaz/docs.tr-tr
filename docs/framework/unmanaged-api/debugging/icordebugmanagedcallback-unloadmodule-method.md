---
title: ICorDebugManagedCallback::UnloadModule Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadModule
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadModule method [.NET Framework debugging]
- UnloadModule method [.NET Framework debugging]
ms.assetid: b12bfcd9-1e29-48bf-9a3d-44bfae5df5e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12e42da015864e83663d2f4d74bab2a34052d760
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995091"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a>ICorDebugManagedCallback::UnloadModule Yöntemi
Hata ayıklayıcı Ortak Dil Çalışma Zamanı Modülü (DLL) kaldırıldı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 [in] Modül bulunan uygulama etki alanı temsil eden bir Icordebugappdomain nesne işaretçisi.  
  
 `pModule`  
 [in] Bir modülü temsil eden bir Icordebugmodule nesne işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Modül, bu çağrıdan sonra kullanılmamalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LoadModule Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)
- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
