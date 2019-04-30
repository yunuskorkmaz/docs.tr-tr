---
title: ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7e1498ec3ce1e5258546cec8d8f8172739af6d9d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756149"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Metodu
Alır `FunctionID` sınıf içeren belirtilen meta veri belirteci kullanarak bir işlevin ve `ClassID` herhangi bir değer türü bağımsız değişkenler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleID`  
 [in] İşlev bulunduğu modül kimliği.  
  
 `funcDef`  
 [in] Bir `mdMethodDef` işlevi başvuran meta veri belirteci.  
  
 `classId`  
 [in] Kapsayan işlevin sınıfı kimliği.  
  
 `cTypeArgs`  
 [in] Belirtilen işlev için tür parametreleri sayısı. Bu değer, genel olmayan işlevler için sıfır olmalıdır.  
  
 `typeArgs`  
 [in] Bir dizi `ClassID` işlevi bağımsız değişkeninin her biri olan değerleri. Değerini `typeArgs` NULL olabilir `cTypeArgs` sıfır olarak ayarlanır.  
  
 `pFunctionID`  
 [out] Bir işaretçi `FunctionID` belirtilen işlevin.  
  
## <a name="remarks"></a>Açıklamalar  
 Çağırma `GetFunctionFromTokenAndTypeArgs` yöntemi ile bir `mdMethodRef` meta verileri yerine bir `mdMethodDef` meta veri belirteci öngörülemeyen sonuçlara sahip olabilir. Çağıranlar çözümlemelidir `mdMethodRef` için bir `mdMethodDef` iletmeden olduğunda.  
  
 İşlev zaten yüklü değilse, çağırma `GetFunctionFromTokenAndTypeArgs` birçok bağlamlarda tehlikeli bir işlemi gerçekleşmesi, yükleme neden olur. Örneğin, çalışma zamanı, döngüsel olarak şeyler yükleme girişiminde türleri veya modüller yükleme sırasında bu yöntemin çağrılması sonsuz bir döngüye neden olabilir.  
  
 Genel olarak, kullanım `GetFunctionFromTokenAndTypeArgs` önerilmez. Profil oluşturucular için belirli bir işleve olaylarda ilgileniyorsanız depolamanız gerekir `ModuleID` ve `mdMethodDef` bu işlevi ve kullanım [Icorprofilerınfo2::getfunctionınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) denetlemek için olup olmadığını bir verilen `FunctionID` olduğu İstenen işlevi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
