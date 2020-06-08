---
title: ICorProfilerInfo4::EnumJITedFunctions2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumJITedFunctions2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumJITedFunctions2
helpviewer_keywords:
- EnumJITedFunctions2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::EnumJITedFunctions2 method [.NET Framework profiling]
ms.assetid: 40e9a1be-9bd2-4fad-9921-34a84b61c1e3
topic_type:
- apiref
ms.openlocfilehash: 2c4a89d5f96ef572518f25bf58a0005454f8e3f0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496137"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a>ICorProfilerInfo4::EnumJITedFunctions2 Yöntemi
Daha önce JıT olarak derlenen ve JıT-yeniden derlenmiş olan tüm işlevler için bir Numaralandırıcı döndürür. Bu yöntem, JıT kodlarını numaralandırmayan [ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) yönteminin yerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppEnum`  
 dışı [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) numaralandırıcısı için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem `JITCompilation` [ICorProfilerCallback:: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) yöntemi gibi geri çağırmalar ile çakışabilir. Döndürülen sabit listesi alanın değerlerini içerir `COR_PRF_FUNCTION::reJitId` . Bu yöntemin yerini aldığı [ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) yöntemi, `COR_PRF_FUNCTION::reJitId` alanı her zaman 0 olarak ayarlandığı için JIT kodlarını numaralandırmaz. Bu `ICorProfilerInfo4::EnumJITedFunctions` Yöntem, `COR_PRF_FUNCTION::reJitId` alan düzgün şekılde ayarlandığından JIT kimliklerini numaralandırır. [ICorProfilerInfo4:: EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) yönteminin bir çöp toplamayı tetikleyebileceğine, ancak [ICorProfilerInfo3:: EnumJITedFunctions metodu](icorprofilerinfo3-enumjitedfunctions-method.md) olmayacaktır.  Daha fazla bilgi için bkz. [HRESULT corprof_e_unsupported_call_sequence](corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EnumJITedFunctions Yöntemi](icorprofilerinfo3-enumjitedfunctions-method.md)
- [ICorProfilerInfo4 Arabirimi](icorprofilerinfo4-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
