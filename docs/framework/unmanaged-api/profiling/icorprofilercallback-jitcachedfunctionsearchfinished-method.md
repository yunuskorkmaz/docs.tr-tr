---
description: ': ICorProfilerCallback:: JITCachedFunctionSearchFinished yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::JITCachedFunctionSearchFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type:
- apiref
ms.openlocfilehash: b5025a7d33800047bb6244b82308ba2ab158cea7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705856"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a>ICorProfilerCallback::JITCachedFunctionSearchFinished Yöntemi

Önceden yerel görüntü Oluşturucu (NGen.exe) kullanılarak derlenen bir işlev için bir aramanın tamamlandığını bir profil oluşturucuya bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a>Parametreler

- `functionId`

  \[' de] aramanın gerçekleştirildiği işlevin KIMLIĞI.

- `result`

  \[içinde] aramanın sonucunu gösteren [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) numaralandırması değeri.

## <a name="remarks"></a>Açıklamalar  

 .NET Framework sürüm 2,0 ' de, [ICorProfilerCallback:: JITCachedFunctionSearchStarted](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) ve `JITCachedFunctionSearchFinished` geri çağrılar normal Ngen görüntülerinde tüm işlevler için yapılmayacak. Yalnızca bir profil Oluşturucu için en iyi duruma getirilmiş NGen görüntüleri görüntüdeki tüm işlevler için geri çağrılar oluşturacaktır. Bununla birlikte, ek yük nedeniyle, profil oluşturucu en iyi duruma getirilmiş NGen görüntülerini yalnızca bir işlevin tam zamanında (JıT) derlenmesi için bu geri çağırmaları kullanmayı amaçladığında istemelidir. Aksi takdirde, profil oluşturucunun işlev bilgilerini toplamak için bir yavaş strateji kullanması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
