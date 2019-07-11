---
title: ICorDebugProcess::SetThreadContext Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b949961e854facf8414c81c47f995b2ac57af3f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755388"
---
# <a name="icordebugprocesssetthreadcontext-method"></a>ICorDebugProcess::SetThreadContext Yöntemi
Bu işlemde belirli iş parçacığı bağlamını ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `threadID`  
 [in] Hangi bağlamını ayarlamak iş parçacığı kimliği.  
  
 `contextSize`  
 [in] Boyutu `context` dizisi.  
  
 `context`  
 [in] İş parçacığı bağlamı açıklayan bir bayt dizisi.  
  
 Bağlam, iş parçacığının yürütülmekte olan işlemci mimarisini belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklayıcı Win32 yerine bu yöntemi çağırmanız gerekir `SetThreadContext` iş parçacığı, onun içeriği geçici olarak değiştirildi "ele geçirilen" bir durumda olabileceğinden, işlev. Bu yöntem, yalnızca bir iş parçacığı yerel kodda olduğunda kullanılmalıdır. Kullanım [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) yönetilen kodda iş parçacığı için. Hiçbir zaman bir bant dışı (OOB) hata ayıklama olayı sırasında bir iş parçacığı bağlamı değiştirmek gerekir.  
  
 Geçirilen veriler, geçerli platform için bir bağlam yapısı olması gerekir.  
  
 Bu yöntem, çalışma zamanı yanlış kullandıysanız bozabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
