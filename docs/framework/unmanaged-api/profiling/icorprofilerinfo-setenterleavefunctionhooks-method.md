---
title: ICorProfilerInfo::SetEnterLeaveFunctionHooks Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type:
- apiref
ms.openlocfilehash: 18aed5c5314fc1057767b599c538952a1d4d6b57
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722238"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a>ICorProfilerInfo::SetEnterLeaveFunctionHooks Yöntemi

Yönetilen işlevlerin "Enter", "Leave" ve "cloncall" kancalarında çağrılacak Profil Oluşturucu uygulanmış işlevleri belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pFuncEnter`  
 'ndaki [FunctionEnter](functionenter-function.md) geri çağırması olarak kullanılacak uygulamaya yönelik bir işaretçi.  
  
 `pFuncLeave`  
 'ndaki [FunctionLeave](functionleave-function.md) geri araması olarak kullanılacak uygulamaya yönelik bir işaretçi.  
  
 `pFuncTailcall`  
 'ndaki [Functionsemblycall](functiontailcall-function.md) geri çağırması olarak kullanılacak uygulamaya yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 .NET Framework sürüm 1,0 ' de, her işlev işaretçisi ilgili geri çağırma işlemini devre dışı bırakmak için null olabilir.  
  
 Tek seferde yalnızca bir geri çağırma kümesi etkin olabilir. Bu nedenle, bir profil oluşturucu hem hem de `SetEnterLeaveFunctionHooks` [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)' ı çağırırsa, `SetEnterLeaveFunctionHooks2` öncelik kazanır.  
  
 `SetEnterLeaveFunctionHooks`Yöntemi yalnızca Profiler 'ın [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) geri çağrısından çağrılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
