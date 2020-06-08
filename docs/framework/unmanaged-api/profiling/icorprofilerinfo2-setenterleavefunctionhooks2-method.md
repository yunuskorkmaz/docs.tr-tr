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
ms.openlocfilehash: 78489aae840ff17e68b10bd7593fb7be4dae1af7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496743"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a>ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Yöntemi
Yönetilen işlevlerin "Enter", "Leave" ve "cloncall" kancalarının güncelleştirilmiş sürümlerinde çağrılacak Profil Oluşturucu uygulanmış işlevleri belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 `SetEnterLeaveFunctionHooks2`Yöntemi [ICorProfilerInfo:: Setenterleavefunctionkancalar](icorprofilerinfo-setenterleavefunctionhooks-method.md) yöntemine benzer. ENTER/Leave/bir çağrı geri çağırmaların daha yeni sürümleri olarak kullanılacak işlevleri belirtmek için, önceki ' ni kullanın ve ENTER/Leave/, çağrı geri çağırmaların eski sürümleri olarak kullanılacak işlevleri belirtin.  
  
 Tek seferde yalnızca bir geri çağırma kümesi etkin olabilir. Bu nedenle, bir profil oluşturucu hem hem de çağırır `ICorProfilerInfo::SetEnterLeaveFunctionHooks` `SetEnterLeaveFunctionHooks2` , `SetEnterLeaveFunctionHooks2` kullanılır.  
  
 `SetEnterLeaveFunctionHooks2`Yöntemi yalnızca Profiler 'ın [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) geri çağrısından çağrılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
