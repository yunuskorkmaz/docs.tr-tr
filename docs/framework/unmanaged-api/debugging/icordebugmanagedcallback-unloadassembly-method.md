---
title: 'ICorDebugManagedCallback:: UnloadAssembly yöntemi'
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type:
- apiref
ms.openlocfilehash: 4ae4856eca2c1441ea53df0d9ed3648700b39b24
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130652"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a>ICorDebugManagedCallback:: UnloadAssembly yöntemi
Hata ayıklayıcıyı ortak bir dil çalışma zamanı derlemesinin kaldırılmış olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 'ndaki Derlemeyi içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.  
  
 `pAssembly`  
 'ndaki Derlemeyi temsil eden ICorDebugAssembly nesnesine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Derleme bu geri aramadan sonra kullanılmamalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LoadAssembly Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)
- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
