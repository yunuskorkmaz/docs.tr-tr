---
title: ICorProfilerInfo3::GetFunctionEnter3Info Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetFunctionEnter3Info Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetFunctionEnter3Info
helpviewer_keywords:
- GetFunctionEnter3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionEnter3Info method [.NET Framework profiling]
ms.assetid: 542c7c65-dd56-4651-b76f-5db2465e4a15
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a75f76af924c3e75d280c36fb5f436498dc6c862
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>ICorProfilerInfo3::GetFunctionEnter3Info Metodu
Profil Oluşturucu tarafından için bildirilen işlevi yığın çerçevesi ve bağımsız değişkeni bilgi verilmektedir [Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) işlevi. Bu yöntem yalnızca sırasında çağrılabilir `FunctionEnter3WithInfo` geri çağırma.  
  
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
 [in] `FunctionID` Giriliyor işlevi.  
  
 `eltInfo`  
 [in] Verilen yığın çerçevesi ilgili bilgileri temsil eder donuk işleci. Profil Oluşturucu aynı sağlamalıdır `eltInfo` tarafından verilen [Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) işlevi.  
  
 `pFrameInfo`  
 [out] Verilen yığın çerçevesi genel türler bilgilerini temsil eden bir donuk tanıtıcısı. Bu işleme yalnızca sırasında geçerli `FunctionEnter3WithInfo` profil oluşturucu çağırıldığı geri çağırma `GetFunctionEnter3Info` yöntemi.  
  
 `pcbArgumentInfo`  
 [içinde out] Bayt olarak toplam boyutu için bir işaretçi, [cor_prf_functıon_argument_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) yapısı (artı ek [cor_prf_functıon_argument_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) tarafındanişaretbağımsızdeğişkeniaralıklarıiçinyapıları`pArgumentInfo`). Belirtilen boyut yeterli değildir, ERROR_INSUFFICIENT_BUFFER döndürülür ve beklenen boyutu depolanan `pcbArgumentInfo`. Çağrılacak `GetFunctionEnter3Info` yalnızca için beklenen değer almak için `*pcbArgumentInfo`ayarlayın `*pcbArgumentInfo`= 0 ve `pArgumentInfo`= NULL.  
  
 `pArgumentInfo`  
 [out] Bir işaretçi bir [cor_prf_functıon_argument_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) işlev bağımsız değişkenleri soldan sağa sırayla bellekte konumlarını tanımlayan yapısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu için yeterli alanı ayırmalısınız `COR_PRF_FUNCTION_ARGUMENT_INFO` Denetlenmekte olan ve boyutu belirtmelidir işlev yapısını `pcbArgumentInfo` parametresi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [Functionleave3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [Functiontailcall3withınfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [Icorprofilerınfo3 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Profil oluşturma arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
