---
title: ICorProfilerInfo3::GetFunctionEnter3Info Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionEnter3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionEnter3Info
helpviewer_keywords:
- GetFunctionEnter3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionEnter3Info method [.NET Framework profiling]
ms.assetid: 542c7c65-dd56-4651-b76f-5db2465e4a15
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6a12e747344f4943dafced2402e0f08a08ac6e7b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498244"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>ICorProfilerInfo3::GetFunctionEnter3Info Metodu
Profil Oluşturucu tarafından bildirilen işlev yığın çerçeve ve bağımsız değişken bilgilerini sağlar [Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) işlevi. Bu yöntem yalnızca sırasında çağrılabilir `FunctionEnter3WithInfo` geri çağırma.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] `FunctionID` İşlevinin giriliyor.  
  
 `eltInfo`  
 [in] Belirli bir yığın çerçevesi ilgili bilgileri temsil eder bir donuk tanıtıcısı. Profil Oluşturucu, aynı sağlamalıdır `eltInfo` tarafından verildiğini [Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) işlevi.  
  
 `pFrameInfo`  
 [out] Genel türler belirtilen yığın çerçevesi bilgilerini temsil eden bir donuk tanıtıcısı. Bu işleyici yalnızca sırasında geçerli `FunctionEnter3WithInfo` profil oluşturucu çağrılır, geri çağırma `GetFunctionEnter3Info` yöntemi.  
  
 `pcbArgumentInfo`  
 [out içinde] Bayt olarak toplam boyutu için bir işaretçi, [cor_prf_functıon_argument_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) yapısı (artı ek [cor_prf_functıon_argument_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) tarafındanişaretedilenbağımsızdeğişkenaralıklarıiçinyapılar`pArgumentInfo`). Belirtilen boyutu yeterli değil, ERROR_INSUFFICIENT_BUFFER döndürülür ve beklenen boyut depolanan `pcbArgumentInfo`. Çağrılacak `GetFunctionEnter3Info` yalnızca beklenen değer almak için `*pcbArgumentInfo`ayarlayın `*pcbArgumentInfo`= 0 ve `pArgumentInfo`= NULL.  
  
 `pArgumentInfo`  
 [out] Bir işaretçi bir [cor_prf_functıon_argument_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) işlev bağımsız soldan sağa doğru sırayla bellekte konumlarını tanımlayan yapısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu için yeterli alanı ayırmalısınız `COR_PRF_FUNCTION_ARGUMENT_INFO` denetlenen ve boyutunu belirtmeniz gerekir işlev yapısını `pcbArgumentInfo` parametresi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [Functionleave3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [Functiontailcall3withınfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
