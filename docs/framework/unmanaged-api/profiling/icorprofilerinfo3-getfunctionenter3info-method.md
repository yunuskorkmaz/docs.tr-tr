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
ms.openlocfilehash: 50d16b8036144d6ede349149fa4ae37344064d8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177026"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>ICorProfilerInfo3::GetFunctionEnter3Info Yöntemi
[FunctionEnter3WithInfo](functionenter3withinfo-function.md) işlevi tarafından profiloluşturucuya bildirilen işlevin yığın çerçevesi ve bağımsız değişken bilgilerini sağlar. Bu yöntem yalnızca `FunctionEnter3WithInfo` geri arama sırasında çağrılabilir.  
  
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
 [içinde] Girilen `FunctionID` işlevin.  
  
 `eltInfo`  
 [içinde] Belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden opak bir tutamaç. Profil oluşturucu, `eltInfo` [FunctionEnter3WithInfo](functionenter3withinfo-function.md) işlevi tarafından verilenin aynısını sağlamalıdır.  
  
 `pFrameInfo`  
 [çıkış] Belirli bir yığın çerçevesi hakkında genel bilgileri temsil eden opak bir tanıtıcı. Bu tanıtıcı yalnızca `FunctionEnter3WithInfo` profilleyicinin `GetFunctionEnter3Info` yöntemi çağırdığı geri arama sırasında geçerlidir.  
  
 `pcbArgumentInfo`  
 [içinde, dışarı] [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) yapısının toplam boyutuna, baytlarda bir işaretçi (artı işaret `pArgumentInfo`edilen bağımsız değişken aralıkları için ek [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) yapıları). Belirtilen boyut yeterli değilse, ERROR_INSUFFICIENT_BUFFER döndürülür ve beklenen boyut `pcbArgumentInfo`. `GetFunctionEnter3Info` Beklenen değeri almak için aramak `*pcbArgumentInfo`için `*pcbArgumentInfo`, `pArgumentInfo`set =0 ve =NULL.  
  
 `pArgumentInfo`  
 [çıkış] İşlevin bağımsız değişkenlerinin konumlarını soldan sağa sırayla açıklayan [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) bir yapıya işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Profil oluşturucu, denetlenmekte `COR_PRF_FUNCTION_ARGUMENT_INFO` olan işlevin yapısı için yeterli alan ayırmalı ve `pcbArgumentInfo` parametredeki boyutu belirtmelidir.  
  
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
