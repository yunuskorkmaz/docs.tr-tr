---
title: ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a459f8e9ec6d63dc42d6a0a8f752c129d278524
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Metodu
Alır `ClassID` belirtilen meta veri simgesi kullanarak bir türde ve `ClassID` değerleri herhangi tür bağımsız değişkenleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `moduleID`  
 [in] Türü bulunduğu modül kimliği.  
  
 `typeDef`  
 [in] Bir `mdTypeDef` türüne başvuran meta veri simgesi.  
  
 `cTypeArgs`  
 [in] Belirtilen tür için tür parametreleri sayısı. Bu değer, genel olmayan türleri için sıfır olmalıdır.  
  
 `typeArgs`  
 [in] Bir dizi `ClassID` her biri olduğunda türünde bir bağımsız değişken değerleri. Değeri `typeArgs` NULL olabilir `cTypeArgs` sıfır olarak ayarlanır.  
  
 `pClassID`  
 [out] Bir işaretçi `ClassID` belirtilen türde.  
  
## <a name="remarks"></a>Açıklamalar  
 Çağırma `GetClassFromTokenAndTypeArgs` yöntemi ile bir `mdTypeRef` yerine bir `mdTypeDef` meta veri simgesi öngörülemeyen sonuçlara sahip olabilir; arayanlar çözümlemelidir `mdTypeRef` için bir `mdTypeDef` onu geçirilirken.  
  
 Türü zaten yüklü değilse, çağırma `GetClassFromTokenAndTypeArgs` birçok bağlamlarında tehlikeli olabilecek bir işlemdir yükleme tetikler. Örneğin, çalışma zamanı döngüsel şeyler yükleme girişiminde modülleri veya diğer türleri yüklenmesi sırasında bu yöntemi çağırmadan sonsuz bir döngüye neden olabilir.  
  
 Genel olarak, kullanımı `GetClassFromTokenAndTypeArgs` önerilmez. Profil oluşturucular belirli bir tür için olaylarda ilgileniyorsanız depolamanız gerekir `ModuleID` ve `mdTypeDef` bu tür ve kullanım [Icorprofilerınfo2::getclassıdınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) denetlemek için olup olmadığını bir verilen `ClassID` budur İstenen türü.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
