---
title: ICorProfilerInfo3::SetFunctionIDMapper2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetFunctionIDMapper2 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetFunctionIDMapper2
helpviewer_keywords:
- SetFunctionIDMapper2 method [.NET Framework profiling]
- ICorProfilerInfo3::SetFunctionIDMapper2 method [.NET Framework profiling]
ms.assetid: 8cdb1188-952a-4ba8-9f05-bfebc18cdd29
topic_type:
- apiref
ms.openlocfilehash: 723cb277a7df592e0494505018f7422e4e40f5f6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496158"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a>ICorProfilerInfo3::SetFunctionIDMapper2 Yöntemi
`FunctionID`Profil oluşturucunun işlev girişine/çıkış kancalarına geçirilen değerleri alternatif değerlerle eşlemek için çağrılacak Profil Oluşturucu uygulanmış işlevi belirtir. Bu yöntem, [ICorProfilerInfo:: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) yöntemini ek bir veri parametresiyle genişletir. Bu, profil oluşturucular çalışma zamanları arasında belirsizliği ortadan kaldırmak için kullanabilir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pFunc`  
 'ndaki Değerleri alternatif değerleriyle eşlemek için çağrılacak bir [FunctionIDMapper2](functionidmapper2-function.md) uygulamasına yönelik bir işaretçi `FunctionID` .  
  
 `clientData`  
 'ndaki Geçerli çalışma zamanı tarafından yapılan her [FunctionIDMapper2](functionidmapper2-function.md) işlev çağrısına geçirilen bir işaretçi. Profil Oluşturucu bu bilgileri çalışma zamanları arasından ayırt etmek için kullanabilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 FunctionID değerleri için alternatifler, profil oluşturucunun işlev giriş/çıkış kancalarına ([FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)ve [FunctionTailcall3](functiontailcall3-function.md); veya [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)ve [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)) [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) veya [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) yöntemiyle belirtilen şekilde geçirilir.  
  
 `FunctionIDMapper2`Yöntem yalnızca bir kez ayarlanabilir; [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) geri çağırması içinde ayarlamanızı öneririz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)
- [ICorProfilerInfo3 Arabirimi](icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
