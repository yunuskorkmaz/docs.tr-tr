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
ms.openlocfilehash: 41021a524142afe34727584265aee578e31a64b3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433213"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Metodu
Belirtilen meta veri belirtecini kullanarak bir işlevin `FunctionID` alır, sınıfı ve tür bağımsız değişkenlerinin `ClassID` değerlerini.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
 'ndaki İşlevin bulunduğu modülün KIMLIĞI.  
  
 `funcDef`  
 'ndaki İşleve başvuran bir `mdMethodDef` meta veri belirteci.  
  
 `classId`  
 'ndaki İşlevin kapsayan sınıfının KIMLIĞI.  
  
 `cTypeArgs`  
 'ndaki Verilen işlev için tür parametrelerinin sayısı. Bu değer, genel olmayan işlevler için sıfır olmalıdır.  
  
 `typeArgs`  
 'ndaki Her biri işlevin bağımsız değişkeni olan bir `ClassID` değerleri dizisi. `cTypeArgs` sıfır olarak ayarlandıysa `typeArgs` değeri NULL olabilir.  
  
 `pFunctionID`  
 dışı Belirtilen işlevin `FunctionID` bir işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetFunctionFromTokenAndTypeArgs` yönteminin `mdMethodDef` meta veri belirteci yerine `mdMethodRef` meta verileriyle çağrılması öngörülemeyen sonuçlara neden olabilir. Çağıranlar, `mdMethodRef` bir `mdMethodDef` geçirmeden çözümlenmelidir.  
  
 İşlev zaten yüklü değilse, `GetFunctionFromTokenAndTypeArgs` çağrısı, çok sayıda bağlamda tehlikeli bir işlem olan yüklemenin oluşmasına neden olur. Örneğin, modül veya tür yükleme sırasında bu yöntemi çağırmak, çalışma zamanı döngüsel olarak yükleme yapmayı denediğinde sonsuz döngüye neden olabilir.  
  
 Genel olarak, `GetFunctionFromTokenAndTypeArgs` kullanımı önerilmez. Profil oluşturucular belirli bir işlevin olaylarıyla ilgileniyorsa, bu işlevin `ModuleID` ve `mdMethodDef` depolarlar ve belirli bir `FunctionID` istenen işlevin olup olmadığını denetlemek için [ICorProfilerInfo2:: GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
