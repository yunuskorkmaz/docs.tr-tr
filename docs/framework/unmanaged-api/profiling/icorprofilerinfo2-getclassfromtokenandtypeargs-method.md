---
title: ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type:
- apiref
ms.openlocfilehash: 702c5f9f2bc08c824bdc0607741a6afd65a3e89b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497263"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Yöntemi
`ClassID`Belirtilen meta veri belirtecini ve `ClassID` tür bağımsız değişkenlerinin değerlerini kullanarak bir türün türünü alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleID`  
 'ndaki Türün bulunduğu modülün KIMLIĞI.  
  
 `typeDef`  
 'ndaki `mdTypeDef`Türe başvuran bir meta veri belirteci.  
  
 `cTypeArgs`  
 'ndaki Verilen tür için tür parametrelerinin sayısı. Bu değer, genel olmayan türler için sıfır olmalıdır.  
  
 `typeArgs`  
 'ndaki `ClassID`Her biri türünün bağımsız değişkeni olan bir değerler dizisi. `typeArgs` `cTypeArgs` Sıfır olarak AYARLANDıYSA değeri null olabilir.  
  
 `pClassID`  
 dışı Belirtilen türün bir işaretçisi `ClassID` .  
  
## <a name="remarks"></a>Açıklamalar  
 `GetClassFromTokenAndTypeArgs`Yöntemi `mdTypeRef` meta veri belirteci yerine bir ile çağırmak `mdTypeDef` öngörülemeyen sonuçlara neden olabilir; çağıranlar, verileri geçirirken bir ile çözmelidir `mdTypeRef` `mdTypeDef` .  
  
 Tür zaten yüklü değilse, çağıran, `GetClassFromTokenAndTypeArgs` çok sayıda bağlamda tehlikeli bir işlem olan yüklemeyi tetikler. Örneğin, modüller veya diğer türler yüklenirken bu yöntemin çağrılması, çalışma zamanı döngüsel olarak yükleme yapmayı denediğinde sonsuz döngüye neden olabilir.  
  
 Genel olarak, kullanımı `GetClassFromTokenAndTypeArgs` önerilmez. Profil oluşturucular belirli bir tür için olaylar ile ilgileniyorsa, bu türden ve ' ı depolamalıdır `ModuleID` `mdTypeDef` ve belirli bir, istenen türde olup olmadığını denetlemek için [ICorProfilerInfo2:: GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) kullanın `ClassID` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
