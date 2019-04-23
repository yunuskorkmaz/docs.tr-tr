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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6cbbe85a99d0c78bd3d95ee654bdc13e376d017d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125230"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a>ICorProfilerInfo::SetFunctionIDMapper Yöntemi
Profil Oluşturucu uygulanan eşlemek için çağrılacak işlevi belirtir `FunctionID` değerleri oluşturucunun geçirilen alternatif, işlev girişi/çıkışı kancaları.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pFunc`  
 [in] Bir işaretçi [Functionıdmapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) eşlemek için çağrılacak olan uygulama `FunctionID` alternatif değerlerine değerleri.  
  
## <a name="remarks"></a>Açıklamalar  
 Alternatifleri için `FunctionID` profil oluşturucunun işlev girişi/çıkışı kancaları için değerleri geçirilir ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), ve [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) tarafından belirtilen [Icorprofilerınfo2::setenterleavefunctionhooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) yöntemi.  
  
 `FunctionIDMapper` Yalnızca bir kez ayarlanabilir ve onu ayarladığınız önerilir [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) geri çağırma.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
