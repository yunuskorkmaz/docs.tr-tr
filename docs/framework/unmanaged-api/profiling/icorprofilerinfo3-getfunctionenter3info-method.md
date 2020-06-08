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
ms.openlocfilehash: 876ae07a432bfa36a7d9f43ae6c32ec03d7d3289
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496600"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>ICorProfilerInfo3::GetFunctionEnter3Info Yöntemi
[FunctionEnter3WithInfo](functionenter3withinfo-function.md) işlevi tarafından Profiler 'a bildirilen işlevin yığın çerçevesini ve bağımsız değişken bilgilerini sağlar. Bu yöntem yalnızca `FunctionEnter3WithInfo` geri çağırma sırasında çağrılabilir.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki `FunctionID`Girilen işlevin.  
  
 `eltInfo`  
 'ndaki Belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden donuk bir tanıtıcı. Profil Oluşturucu, `eltInfo` [FunctionEnter3WithInfo](functionenter3withinfo-function.md) işlevi tarafından verilen aynısını sağlamalıdır.  
  
 `pFrameInfo`  
 dışı Belirli bir yığın çerçevesiyle ilgili genel türler bilgilerini temsil eden donuk bir tanıtıcı. Bu tanıtıcı yalnızca `FunctionEnter3WithInfo` profil oluşturucunun yöntemi olarak çağrıldığı geri çağırma sırasında geçerlidir `GetFunctionEnter3Info` .  
  
 `pcbArgumentInfo`  
 [in, out] [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) yapısının bayt cinsinden toplam boyutuna yönelik bir işaretçi (artı tarafından işaret edilen bağımsız değişken aralıkları için ek [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) yapıları `pArgumentInfo` ). Belirtilen boyut yeterince yoksa, ERROR_INSUFFICIENT_BUFFER döndürülür ve beklenen boyut içinde depolanır `pcbArgumentInfo` . `GetFunctionEnter3Info`İçin yalnızca beklenen değeri almak üzere çağırmak için `*pcbArgumentInfo` , set `*pcbArgumentInfo` = 0 ve `pArgumentInfo` = null.  
  
 `pArgumentInfo`  
 dışı İşlevin bellekteki bağımsız değişkenlerinin konumlarını soldan sağa sırada açıklayan [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) yapısına yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu incelenen işlevin yapısı için yeterli alan ayırmalıdır `COR_PRF_FUNCTION_ARGUMENT_INFO` ve parametresindeki boyutu belirtmelidir `pcbArgumentInfo` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Functionenter3withınfo](functionenter3withinfo-function.md)
- [Functionleave3withınfo](functionleave3withinfo-function.md)
- [Functiontailcall3withınfo](functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3 Arabirimi](icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
