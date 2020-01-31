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
ms.openlocfilehash: e0663ff122397ba639a0a219e513be2f3f0cbbef
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862798"
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
  
 Genel olarak, `GetClassFromTokenAndTypeArgs` kullanımı önerilmez. Profil oluşturucular belirli bir tür için olaylarla ilgileniyorsa, bu türün `ModuleID` ve `mdTypeDef` depolarlar ve belirli bir `ClassID` istenen türde olup olmadığını denetlemek için [ICorProfilerInfo2:: GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
