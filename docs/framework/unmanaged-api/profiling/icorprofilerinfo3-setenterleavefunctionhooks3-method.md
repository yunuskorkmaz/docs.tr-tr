---
title: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
ms.assetid: f0621465-b84f-40ab-a4e5-56a7abc776a7
topic_type:
- apiref
ms.openlocfilehash: eb658d682ce589b7dfdcfc0228d0c657310e6f7a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496275"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a>ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Yöntemi
[FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)ve [FunctionTailcall3](functiontailcall3-function.md) işlevlerinde çağrılacak Profil Oluşturucu uygulanmış işlevleri belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pFuncEnter3`  
 'ndaki Geri çağırma olarak kullanılacak uygulamaya yönelik bir işaretçi `FunctionEnter3` .  
  
 `pFuncLeave3`  
 'ndaki Geri çağırma olarak kullanılacak uygulamaya yönelik bir işaretçi `FunctionLeave3` .  
  
 `pFuncTailcall3`  
 'ndaki Geri çağırma olarak kullanılacak uygulamaya yönelik bir işaretçi `FunctionTailcall3` .  
  
## <a name="remarks"></a>Açıklamalar  
 [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)ve [FunctionTailcall3](functiontailcall3-function.md) kancaları yığın çerçevesi ve bağımsız değişken incelemesi sağlamaz. Bu bilgilere erişmek için,, `COR_PRF_ENABLE_FUNCTION_ARGS` `COR_PRF_ENABLE_FUNCTION_RETVAL` ve/veya `COR_PRF_ENABLE_FRAME_INFO` bayraklarının ayarlanması gerekir. Profiler, Event bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemini kullanabilir ve sonra bu işlevin uygulamanızı kaydetmek için [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) metodunu kullanabilir.  
  
 Tek seferde yalnızca bir geri çağırma kümesi etkin olabilir ve en yeni sürüm öncelikli olur. Bu nedenle, bir profil oluşturucu hem [SetEnterLeaveFunctionHooks2 yöntemini](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) hem de `SetEnterLeaveFunctionHooks3` yöntemini çağırırsa, `SetEnterLeaveFunctionHooks3` kullanılır.  
  
 `SetEnterLeaveFunctionHooks3`Yöntemi yalnızca Profiler 'ın [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) geri çağrısından çağrılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Setenterleavefunctionhooks3withınfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [FunctionTailcall3](functiontailcall3-function.md)
- [Functionenter3withınfo](functionenter3withinfo-function.md)
- [Functionleave3withınfo](functionleave3withinfo-function.md)
- [Functiontailcall3withınfo](functiontailcall3withinfo-function.md)
- [Profil Oluşturma Genel Statik İşlevleri](profiling-global-static-functions.md)
- [ICorProfilerInfo3](icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
