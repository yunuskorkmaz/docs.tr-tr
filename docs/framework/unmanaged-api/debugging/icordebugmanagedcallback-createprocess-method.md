---
title: ICorDebugManagedCallback::CreateProcess Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateProcess
helpviewer_keywords:
- ICorDebugManagedCallback::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: 8e89d5ee-e4e3-4738-8302-0b7d1cf4846e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24efa08e9c4b2e242af95112b7f055e9173aaa7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414683"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a>ICorDebugManagedCallback::CreateProcess Yöntemi
Bir işlem bağlı veya için ilk kez başlatıldığında, hata ayıklayıcı size bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pProcess`  
 [in] Bir işaretçi Icordebugprocess nesneye bağlı veya başlatılan işlem temsil eder.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, ortak dil çalışma zamanı başlatılana kadar çağrılmaz. Çoğu [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) yöntemleri CORDBG_E_NOTREADY önce döndürecektir `CreateProcess` geri çağırma.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
