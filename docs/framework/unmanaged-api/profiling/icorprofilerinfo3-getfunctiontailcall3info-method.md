---
title: ICorProfilerInfo3::GetFunctionTailcall3Info Yöntemi
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
ms.openlocfilehash: 5346792cb2a1309268cb4ba48625aa559777fbaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177000"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a>ICorProfilerInfo3::GetFunctionTailcall3Info Yöntemi
[FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) işlevi tarafından profilciye bildirilen işlevin yığın çerçevesini sağlar. Bu yöntem yalnızca `FunctionTailcall3WithInfo` geri arama sırasında çağrılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetFunctionTailcall3Info(
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionId`  
 [içinde] Geri `FunctionID` dönen işlevin.  
  
 `eltInfo`  
 [içinde] Belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden opak bir tutamaç. Profil oluşturucu, `eltInfo` `FunctionTailcall3WithInfo` işlev tarafından profilciye verilenin aynısını sağlamalıdır.  
  
 `pFrameInfo`  
 [çıkış] Belirli bir yığın çerçevesi hakkında genel bilgileri temsil eden opak bir tanıtıcı. Bu tanıtıcı yalnızca `FunctionTailcall3WithInfo` profilleyicinin `GetFunctionTailcall3Info` yöntemi çağırdığı geri arama sırasında geçerlidir.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorProf.idl, CorProf.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [FonksiyonEnter3WithInfo](functionenter3withinfo-function.md)
- [FonksiyonLeave3WithInfo](functionleave3withinfo-function.md)
- [FonksiyonTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3 Arabirimi](icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil oluşturma](index.md)
