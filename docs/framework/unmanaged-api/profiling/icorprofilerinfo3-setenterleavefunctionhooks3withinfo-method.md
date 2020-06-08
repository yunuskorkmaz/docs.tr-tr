---
title: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3WithInfo Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
ms.assetid: ca8ea534-e441-47b8-be85-466410988c0a
topic_type:
- apiref
ms.openlocfilehash: d40cb424306535cc502d930dd61e6a1e254667da
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496184"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a>ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Yöntemi
Yönetilen işlevlerin [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)ve [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) kancaları üzerinde çağrılacak Profil Oluşturucu uygulanmış işlevleri belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pFuncEnter3`  
 'ndaki Geri çağırma olarak kullanılacak uygulamaya yönelik bir işaretçi `FunctionEnter3WithInfo` .  
  
 `pFuncLeave3`  
 'ndaki Geri çağırma olarak kullanılacak uygulamaya yönelik bir işaretçi `FunctionLeave3WithInfo` .  
  
 `pFuncTailcall3`  
 'ndaki Geri çağırma olarak kullanılacak uygulamaya yönelik bir işaretçi `FunctionTailcall3WithInfo` .  
  
## <a name="remarks"></a>Açıklamalar  
 [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)ve [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) kancaları yığın çerçevesi ve bağımsız değişken incelemesi sağlar. Bu bilgilere erişmek için,, `COR_PRF_ENABLE_FUNCTION_ARGS` `COR_PRF_ENABLE_FUNCTION_RETVAL` ve/veya `COR_PRF_ENABLE_FRAME_INFO` bayraklarının ayarlanması gerekir. Profiler, Event bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemini kullanabilir ve sonra `SetEnterLeaveFunctionHooks3WithInfo` Bu işlevin uygulamanızı kaydetmek için yöntemini kullanır.  
  
 Tek seferde yalnızca bir geri çağırma kümesi etkin olabilir ve en yeni sürüm öncelikli olur. Bu nedenle, bir profil oluşturucu hem [SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) hem de `SetEnterLeaveFunctionHooks3WithInfo` ' i çağırırsa, `SetEnterLeaveFunctionHooks3WithInfo` kullanılır.  
  
 `SetEnterLeaveFunctionHooks3WithInfo`Yöntemi yalnızca Profiler 'ın [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) geri çağrısından çağrılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [FunctionTailcall3](functiontailcall3-function.md)
- [Functionenter3withınfo](functionenter3withinfo-function.md)
- [Functionleave3withınfo](functionleave3withinfo-function.md)
- [Functiontailcall3withınfo](functiontailcall3withinfo-function.md)
- [Profil Oluşturma Genel Statik İşlevleri](profiling-global-static-functions.md)
- [ICorProfilerInfo3 Arabirimi](icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
