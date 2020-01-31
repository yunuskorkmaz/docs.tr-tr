---
title: ICorProfilerInfo3::GetFunctionEnter3Info Yöntemi
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
ms.openlocfilehash: 55411f187e2ef73997633d94b37a7d5d2cfd74c9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868570"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>ICorProfilerInfo3::GetFunctionEnter3Info Yöntemi
[FunctionEnter3WithInfo](functionenter3withinfo-function.md) işlevi tarafından Profiler 'a bildirilen işlevin yığın çerçevesini ve bağımsız değişken bilgilerini sağlar. Bu yöntem yalnızca `FunctionEnter3WithInfo` geri çağırma sırasında çağrılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionId`  
 'ndaki Girilen işlevin `FunctionID`.  
  
 `eltInfo`  
 'ndaki Belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden donuk bir tanıtıcı. Profil Oluşturucu, [FunctionEnter3WithInfo](functionenter3withinfo-function.md) işlevi tarafından verilen `eltInfo` aynı şekilde sağlamalıdır.  
  
 `pFrameInfo`  
 dışı Belirli bir yığın çerçevesiyle ilgili genel türler bilgilerini temsil eden donuk bir tanıtıcı. Bu tanıtıcı yalnızca profil oluşturucunun `GetFunctionEnter3Info` metodunu çağırdığı `FunctionEnter3WithInfo` geri çağırma sırasında geçerlidir.  
  
 `pcbArgumentInfo`  
 [in, out] [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) yapısının bayt cinsinden toplam boyutuna yönelik bir işaretçi (artı `pArgumentInfo`) tarafından işaret edilen bağımsız değişken aralıkları için ek [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) yapıları. Belirtilen boyut yeterince yoksa ERROR_INSUFFICIENT_BUFFER döndürülür ve beklenen boyut `pcbArgumentInfo`depolanır. `*pcbArgumentInfo`için beklenen değeri almak üzere `GetFunctionEnter3Info` çağırmak için `*pcbArgumentInfo`= 0 ve `pArgumentInfo`= NULL değerlerini ayarlayın.  
  
 `pArgumentInfo`  
 dışı İşlevin bellekteki bağımsız değişkenlerinin konumlarını soldan sağa sırada açıklayan [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) yapısına yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu, incelenen işlevin `COR_PRF_FUNCTION_ARGUMENT_INFO` yapısı için yeterli alan ayırmalıdır ve `pcbArgumentInfo` parametresindeki boyutu belirtmelidir.  
  
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
