---
title: ICorDebugManagedCallback::EvalException Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalException
helpviewer_keywords:
- EvalException method [.NET Framework debugging]
- ICorDebugManagedCallback::EvalException method [.NET Framework debugging]
ms.assetid: d6036345-18a3-45c1-a302-b1c6f2dced9b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 602bcd12d1fd4c5806de6db81252731baa447b7b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120022"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a>ICorDebugManagedCallback::EvalException Yöntemi
Hata ayıklayıcı, bir değerlendirme işlenmeyen bir özel durumla sona erdi bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 [in] Değerlendirme sonlandırıldı, uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.  
  
 `pThread`  
 [in] Değerlendirme sonlandırıldı, iş parçacığı temsil eden bir Icordebugthread nesne işaretçisi.  
  
 `pEval`  
 [in] Değerlendirme gerçekleştirilen kodunu temsil eden bir Icordebugeval nesne işaretçisi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
