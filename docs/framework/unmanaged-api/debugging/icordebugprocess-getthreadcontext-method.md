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
ms.openlocfilehash: 2bdbf373144e2fb49074cfd035e7b0ffe3c8c291
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212899"
---
# <a name="icordebugprocessgetthreadcontext-method"></a>ICorDebugProcess::GetThreadContext Yöntemi
Bu işlemdeki verilen iş parçacığının bağlamını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `threadID`  
 'ndaki Bağlamını almak için iş parçacığının KIMLIĞI.  
  
 `contextSize`  
 'ndaki `context`Dizinin boyutu.  
  
 `context`  
 [in, out] İş parçacığının bağlamını tanımlayan bir bayt dizisi.  
  
 Bağlam, iş parçacığının yürütüldüğü işlemcinin mimarisini belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetThreadContext`İş parçacığı gerçekten, bağlamı geçici olarak değiştirilen bir "ele geçirilmiş" durumda olabileceğinden, hata ayıklayıcı Win32 yöntemi yerine bu yöntemi çağırmalıdır. Bu yöntem, yalnızca bir iş parçacığı yerel kodda olduğunda kullanılmalıdır. Yönetilen koddaki iş parçacıkları için [ICorDebugRegisterSet](icordebugregisterset-interface.md) kullanın.  
  
 Döndürülen veriler, geçerli platform için bir bağlam yapısıdır. Win32 yönteminde olduğu gibi `GetThreadContext` , çağıranın `context` Bu yöntemi çağırmadan önce parametresini başlatması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
