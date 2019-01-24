---
title: ICorProfilerInfo3::GetFunctionTailcall3Info Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a91684ea3712c8fe20d1902f86e3880bf0ad340
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660287"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a>ICorProfilerInfo3::GetFunctionTailcall3Info Metodu
Profil Oluşturucu tarafından bildirilen işlev yığın çerçevesinde sağlar [Functiontailcall3withınfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) işlevi. Bu yöntem yalnızca sırasında çağrılabilir `FunctionTailcall3WithInfo` geri çağırma.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetFunctionTailcall3Info(   
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] `FunctionID` Döndüren işlev.  
  
 `eltInfo`  
 [in] Belirli bir yığın çerçevesi ilgili bilgileri temsil eder bir donuk tanıtıcısı. Profil Oluşturucu, aynı sağlamalıdır `eltInfo` değişken için Profil Oluşturucu tarafından `FunctionTailcall3WithInfo` işlevi.  
  
 `pFrameInfo`  
 [out] Genel türler belirtilen yığın çerçevesi bilgilerini temsil eden bir donuk tanıtıcısı. Bu işleyici yalnızca sırasında geçerli `FunctionTailcall3WithInfo` profil oluşturucu çağrılır, geri çağırma `GetFunctionTailcall3Info` yöntemi.  
  
## <a name="remarks"></a>Açıklamalar  
  
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
