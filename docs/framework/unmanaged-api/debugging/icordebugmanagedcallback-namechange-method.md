---
title: ICorDebugManagedCallback::NameChange Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 975353403a82956912fa41047253bb0dbf138502
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995169"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a>ICorDebugManagedCallback::NameChange Yöntemi
Hata ayıklayıcı, bir uygulama etki alanı ya da bir iş parçacığı adı değiştiğini bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 [in] Bir işaretçi ya da bir ad değişikliği ya da sahip uygulama etki alanı temsil eden bir Icordebugappdomain nesne için bir ad değişikliği olan iş parçacığı içerir.  
  
 `pThread`  
 [in] Bir işaretçi Icordebugthread nesneye bir ad değişikliği olan iş parçacığını temsil eder.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
