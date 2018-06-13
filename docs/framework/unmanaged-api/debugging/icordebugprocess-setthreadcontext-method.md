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
ms.openlocfilehash: c9ed79eb799971dfcbc9fd787cd0290795f79d96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417979"
---
# <a name="icordebugprocesssetthreadcontext-method"></a>ICorDebugProcess::SetThreadContext Yöntemi
Verilen iş parçacığı bağlamının bu işlemde ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `threadID`  
 [in] Bağlam ayarlanacağı için iş parçacığı kimliği.  
  
 `contextSize`  
 [in] Boyutunu `context` dizi.  
  
 `context`  
 [in] İş parçacığının içeriğini açıklayan bir bayt dizisi.  
  
 Bağlam parçacığının çalıştırdığından işlemci mimarisini belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklayıcı Win32 yerine bu yöntemi çağırmanız gerekir `SetThreadContext` iş parçacığı içinde onun içeriği geçici olarak değiştirildi "ele geçirilen" bir durumda olabileceğinden, işlev. Bu yöntem yalnızca bir iş parçacığı yerel kodda olduğunda kullanılmalıdır. Kullanım [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) yönetilen kodda iş parçacığı için. Hiçbir zaman bir bant dışı (OOB) hata ayıklama olayı sırasında bir iş parçacığı bağlamı değiştirmek gerekir.  
  
 Geçirilen verileri geçerli platform için bir bağlam yapısı olmalıdır.  
  
 Bu yöntem, yanlış kullandıysanız çalışma zamanı bozabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
