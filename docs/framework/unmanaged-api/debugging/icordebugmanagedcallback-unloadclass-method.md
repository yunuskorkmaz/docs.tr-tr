---
title: ICorDebugManagedCallback::UnloadClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3eb8bf59ee2a91c62a6ff74b1903d92607a9ffe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995157"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a>ICorDebugManagedCallback::UnloadClass Yöntemi
Hata ayıklayıcı, bir sınıf boşaltılıyor bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 [in] Sınıfını içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.  
  
 `c`  
 [in] Bu sınıfın temsil ettiği bir Icordebugclass nesneye bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Sınıfı Bu çağrıdan sonra başvurulmaması gereken.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LoadClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)
- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
