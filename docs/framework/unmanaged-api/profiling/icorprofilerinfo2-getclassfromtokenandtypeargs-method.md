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
ms.openlocfilehash: 5b6c0159b432d2a70f583357bbcf714b27399633
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447177"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Yöntemi
Tür bağımsız değişkenlerinin belirtilen meta veri belirtecini ve `ClassID` değerlerini kullanarak bir türün `ClassID` alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 'ndaki Türe başvuran bir `mdTypeDef` meta veri belirteci.  
  
 `cTypeArgs`  
 'ndaki Verilen tür için tür parametrelerinin sayısı. Bu değer, genel olmayan türler için sıfır olmalıdır.  
  
 `typeArgs`  
 'ndaki Her biri türünün bağımsız değişkeni olan `ClassID` değerleri dizisi. `cTypeArgs` sıfır olarak ayarlandıysa `typeArgs` değeri NULL olabilir.  
  
 `pClassID`  
 dışı Belirtilen türün `ClassID` bir işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetClassFromTokenAndTypeArgs` yönteminin `mdTypeDef` meta veri belirteci yerine `mdTypeRef` çağrılması öngörülemeyen sonuçlara neden olabilir; çağıranlar, `mdTypeRef` bir `mdTypeDef` geçirmeden çözümlenmelidir.  
  
 Tür zaten yüklü değilse, `GetClassFromTokenAndTypeArgs` çağrısı, çok sayıda bağlamda tehlikeli bir işlem olan yüklemeyi tetikleyecektir. Örneğin, modüller veya diğer türler yüklenirken bu yöntemin çağrılması, çalışma zamanı döngüsel olarak yükleme yapmayı denediğinde sonsuz döngüye neden olabilir.  
  
 Genel olarak, `GetClassFromTokenAndTypeArgs` kullanımı önerilmez. Profil oluşturucular belirli bir tür için olaylarla ilgileniyorsa, bu türün `ModuleID` ve `mdTypeDef` depolarlar ve belirli bir `ClassID` istenen türde olup olmadığını denetlemek için [ICorProfilerInfo2:: GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
