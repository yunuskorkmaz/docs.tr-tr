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
ms.openlocfilehash: 7eac42e1d8132ca9e6d6c6b43efd43b88c1e5d3d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868596"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a>ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Yöntemi
Yönetilen işlevlerin "Enter", "Leave" ve "cloncall" kancalarının güncelleştirilmiş sürümlerinde çağrılacak Profil Oluşturucu uygulanmış işlevleri belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pFuncEnter`  
 'ndaki [FunctionEnter2](functionenter2-function.md) geri çağırması olarak kullanılacak uygulamaya yönelik bir işaretçi.  
  
 `pFuncLeave`  
 'ndaki [FunctionLeave2](functionleave2-function.md) geri çağırması olarak kullanılacak uygulamaya yönelik bir işaretçi.  
  
 `pFuncTailcall`  
 'ndaki [FunctionTailcall2](functiontailcall2-function.md) geri çağırması olarak kullanılacak uygulamaya yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `SetEnterLeaveFunctionHooks2` yöntemi [ICorProfilerInfo:: Setenterleavefunctionkancalar](icorprofilerinfo-setenterleavefunctionhooks-method.md) yöntemine benzer. ENTER/Leave/bir çağrı geri çağırmaların daha yeni sürümleri olarak kullanılacak işlevleri belirtmek için, önceki ' ni kullanın ve ENTER/Leave/, çağrı geri çağırmaların eski sürümleri olarak kullanılacak işlevleri belirtin.  
  
 Tek seferde yalnızca bir geri çağırma kümesi etkin olabilir. Bu nedenle, bir profil oluşturucu hem `ICorProfilerInfo::SetEnterLeaveFunctionHooks` hem de `SetEnterLeaveFunctionHooks2`çağırırsa `SetEnterLeaveFunctionHooks2` kullanılır.  
  
 `SetEnterLeaveFunctionHooks2` yöntemi yalnızca Profiler 'ın [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) geri çağrısından çağrılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
