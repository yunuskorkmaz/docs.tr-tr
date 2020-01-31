---
title: ICorProfilerInfo3::GetFunctionLeave3Info Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionLeave3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionLeave3Info
helpviewer_keywords:
- GetFunctionLeave3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionLeave3Info method [.NET Framework profiling]
ms.assetid: df7083d2-fd43-44c7-9ce5-912c25cef0ff
topic_type:
- apiref
ms.openlocfilehash: 0d3b93a293d4dda9dfe7b576708c832de2e25869
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862411"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a>ICorProfilerInfo3::GetFunctionLeave3Info Yöntemi
[FunctionLeave3WithInfo işlev](functionleave3withinfo-function.md) işlevi tarafından Profiler 'a bildirilen işlevin yığın çerçevesini ve dönüş değerini sağlar. Bu yöntem yalnızca `FunctionLeave3WithInfo` geri çağırma sırasında çağrılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionId`  
 'ndaki Döndürülen işlevin `FunctionID`.  
  
 `eltInfo`  
 'ndaki Belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden donuk bir tanıtıcı. Profil Oluşturucu, [FunctionLeave3WithInfo](functionleave3withinfo-function.md) işlevi tarafından Profiler 'a verilen aynı `eltInfo` sağlamalıdır.  
  
 `pFrameInfo`  
 dışı Belirli bir yığın çerçevesiyle ilgili genel türler bilgilerini temsil eden donuk bir tanıtıcı. Bu tanıtıcı yalnızca profil oluşturucunun `GetFunctionLeave3Info` metodunu çağırdığı `FunctionLeave3WithInfo` geri çağırma sırasında geçerlidir.  
  
 `pRetvalRange`  
 dışı İşlevden döndürülen değeri içeren [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) yapısına yönelik bir işaretçi. Dönüş değeri bilgilerine erişmek için `COR_PRF_ENABLE_FUNCTION_RETVAL` bayrağının ayarlanması gerekir. Profil Oluşturucu, olay bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask yöntemini](icorprofilerinfo-seteventmask-method.md) kullanabilir.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Functionenter3withınfo](functionenter3withinfo-function.md)
- [Functionleave3withınfo](functionleave3withinfo-function.md)
- [Functiontailcall3withınfo](functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3 Yöntemi](icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
