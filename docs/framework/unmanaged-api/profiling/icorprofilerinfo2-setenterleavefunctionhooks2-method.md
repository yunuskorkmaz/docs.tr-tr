---
title: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9f95a404ce7124a76ee527cdc70ccccf103838b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763184"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a>ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Yöntemi
Profil Oluşturucu uygulanan işlevleri güncelleştirilmiş sürümlerine ilişkin "enter", "Ayrıl" ve "tailcall" hooks yönetilen işlevlerin çağrılmasına belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pFuncEnter`  
 [in] Bir işaretçi olarak kullanılmak üzere uygulamaya [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) geri çağırma.  
  
 `pFuncLeave`  
 [in] Bir işaretçi olarak kullanılmak üzere uygulamaya [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) geri çağırma.  
  
 `pFuncTailcall`  
 [in] Bir işaretçi olarak kullanılmak üzere uygulamaya [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) geri çağırma.  
  
## <a name="remarks"></a>Açıklamalar  
 `SetEnterLeaveFunctionHooks2` Yöntemi benzer [Icorprofilerınfo::setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) yöntemi. Önceki eski sürümleri enter/bırakma/tailcall geri çağırmaları kullanılacak işlevleri belirtmek için daha yeni sürümleri enter/bırakma/tailcall geri çağrıları ve ikinci kullanılacak işlevleri belirtmek için kullanın.  
  
 Bir kerede yalnızca bir dizi geri çağırmaları etkin olabilir. Bu nedenle, her ikisi de bir profil oluşturucu çağırırsa `ICorProfilerInfo::SetEnterLeaveFunctionHooks` ve `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` kullanılır.  
  
 `SetEnterLeaveFunctionHooks2` Yöntemi yalnızca profil oluşturucuyu 's adlı [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) geri çağırma.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
