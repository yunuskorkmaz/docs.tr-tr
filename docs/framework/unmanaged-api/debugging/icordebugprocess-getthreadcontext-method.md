---
title: ICorDebugProcess::GetThreadContext Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e45d101db946747463ba4200bc5dd3b95d21391
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessgetthreadcontext-method"></a>ICorDebugProcess::GetThreadContext Metodu
Bu işlem verilen iş parçacığı için bağlamı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `threadID`  
 [in] İçerik almak için iş parçacığı kimliği.  
  
 `contextSize`  
 [in] Boyutunu `context` dizi.  
  
 `context`  
 [içinde out] İş parçacığının içeriğini açıklayan bir bayt dizisi.  
  
 Bağlam parçacığının çalıştırdığından işlemci mimarisini belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklayıcı Win32 yerine bu yöntemi çağırmanız gerekir `GetThreadContext` yöntemi, çünkü iş parçacığı gerçekte, onun içeriği geçici olarak değiştirildi "ele geçirilen" bir durumda olabilir. Bu yöntem yalnızca bir iş parçacığı yerel kodda olduğunda kullanılmalıdır. Kullanım [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) yönetilen kodda iş parçacığı için.  
  
 Döndürülen veri geçerli platform için bir bağlam yapısıdır. Win32 gibi olduğu `GetThreadContext` çağıran Initialize yöntemi, `context` bu yöntemi çağırmadan önce parametre.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
