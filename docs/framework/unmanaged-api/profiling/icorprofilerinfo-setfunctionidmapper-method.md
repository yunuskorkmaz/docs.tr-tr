---
title: ICorProfilerInfo::SetFunctionIDMapper Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetFunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetFunctionIDMapper
helpviewer_keywords:
- ICorProfilerInfo::SetFunctionIDMapper method [.NET Framework profiling]
- SetFunctionIDMapper method [.NET Framework profiling]
ms.assetid: 1a6e5dae-d366-4497-9c02-7b5b1f43f9ec
topic_type:
- apiref
ms.openlocfilehash: 5272c5bf256f6e21a83470db094ab79317932018
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497484"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a>ICorProfilerInfo::SetFunctionIDMapper Yöntemi
`FunctionID`Profil oluşturucunun işlev girişine/çıkış kancalarına geçirilen değerleri alternatif değerlerle eşlemek için çağrılacak Profil Oluşturucu uygulanmış işlevi belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pFunc`  
 'ndaki Değerleri alternatif değerleriyle eşlemek için çağrılacak [FunctionIDMapper](functionidmapper-function.md) uygulamasına yönelik bir işaretçi `FunctionID` .  
  
## <a name="remarks"></a>Açıklamalar  
 Değerler için alternatifler, `FunctionID` " [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) yöntemi tarafından belirtilen profil oluşturucunun işlev girdisine/çıkış kancalarına ([FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)ve [FunctionTailcall2](functiontailcall2-function.md)) geçirilecek.  
  
 `FunctionIDMapper`Yalnızca bir kez ayarlanabilir ve bunu [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) geri çağırması içinde ayarlamanız önerilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
