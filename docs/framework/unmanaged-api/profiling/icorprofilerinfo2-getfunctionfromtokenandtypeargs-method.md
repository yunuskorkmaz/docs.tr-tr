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
ms.openlocfilehash: 7f1276e1adeece086ca7b6791eb6e870faf4d010
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502879"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Metodu
`FunctionID`Belirtilen meta veri belirtecini, sınıfını ve `ClassID` tür bağımsız değişkenlerinin değerlerini kullanarak bir işlevi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki `mdMethodDef`İşleve başvuran bir meta veri belirteci.  
  
 `classId`  
 'ndaki İşlevin kapsayan sınıfının KIMLIĞI.  
  
 `cTypeArgs`  
 'ndaki Verilen işlev için tür parametrelerinin sayısı. Bu değer, genel olmayan işlevler için sıfır olmalıdır.  
  
 `typeArgs`  
 'ndaki `ClassID`Her biri işlevin bağımsız değişkeni olan bir değer dizisi. `typeArgs` `cTypeArgs` Sıfır olarak AYARLANDıYSA değeri null olabilir.  
  
 `pFunctionID`  
 dışı `FunctionID`Belirtilen işlevin işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetFunctionFromTokenAndTypeArgs`Yöntemi `mdMethodRef` meta veri belirteci yerine meta verilerle çağırmak `mdMethodDef` öngörülemeyen sonuçlara neden olabilir. Çağıranlar, `mdMethodRef` geçişini yaparken öğesine çözmelidir `mdMethodDef` .  
  
 İşlev zaten yüklü değilse, çağırma, `GetFunctionFromTokenAndTypeArgs` çok sayıda bağlamda tehlikeli bir işlem olan yüklemenin oluşmasına neden olur. Örneğin, modül veya tür yükleme sırasında bu yöntemi çağırmak, çalışma zamanı döngüsel olarak yükleme yapmayı denediğinde sonsuz döngüye neden olabilir.  
  
 Genel olarak, kullanımı `GetFunctionFromTokenAndTypeArgs` önerilmez. Profil oluşturucular belirli bir işlev için olaylar ile ilgileniyorsa, `ModuleID` `mdMethodDef` Bu işlevin ve bu işlevi depolamalıdır ve [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) kullanarak belirli bir işlevin istenen işlevden olup olmadığını denetler `FunctionID` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
