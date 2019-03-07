---
title: ICorDebugProcess::GetThreadContext Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28d54becc2d7cd4359c78415f25f579b968cb3f4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482346"
---
# <a name="icordebugprocessgetthreadcontext-method"></a>ICorDebugProcess::GetThreadContext Yöntemi
Bu işlem belirli bir iş parçacığı için bağlamı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `threadID`  
 [in] Bağlamı almak istediğiniz iş parçacığının kimliği.  
  
 `contextSize`  
 [in] Boyutu `context` dizisi.  
  
 `context`  
 [out içinde] İş parçacığı bağlamı açıklayan bir bayt dizisi.  
  
 Bağlam, iş parçacığının yürütülmekte olan işlemci mimarisini belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklayıcı Win32 yerine bu yöntemi çağırmanız gerekir `GetThreadContext` yöntemi, çünkü iş parçacığı aslında, onun içeriği geçici olarak değiştirildi "ele geçirilen" bir durumda olabilir. Bu yöntem, yalnızca bir iş parçacığı yerel kodda olduğunda kullanılmalıdır. Kullanım [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) yönetilen kodda iş parçacığı için.  
  
 Döndürülen veriler, geçerli platform için bir bağlam yapısıdır. İle olduğu gibi Win32 `GetThreadContext` Initialize yöntemi, çağırana `context` bu yöntemi çağırmadan önce parametresi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
