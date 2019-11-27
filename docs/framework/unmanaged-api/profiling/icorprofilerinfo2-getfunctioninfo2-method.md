---
title: ICorProfilerInfo2::GetFunctionInfo2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionInfo2
helpviewer_keywords:
- GetFunctionInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetFunctionInfo2 method [.NET Framework profiling]
ms.assetid: 0aa60f24-8bbd-4c83-83c5-86ad191b1d82
topic_type:
- apiref
ms.openlocfilehash: 11f9a186f5ec5e3b9e718a3ccd43b35b66d28078
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433183"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a>ICorProfilerInfo2::GetFunctionInfo2 Yöntemi
Bir işlevin varsa, üst sınıfı, meta veri belirtecini ve her tür bağımsız değişkeninin `ClassID` alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetFunctionInfo2(  
    [in]  FunctionID funcId,  
    [in]  COR_PRF_FRAME_INFO frameInfo,  
    [out] ClassID *pClassId,  
    [out] ModuleID *pModuleId,  
    [out] mdToken *pToken,  
    [in]  ULONG32 cTypeArgs,  
    [out] ULONG32 *pcTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `funcId`  
 'ndaki Üst sınıfı ve diğer bilgileri almak için işlevin KIMLIĞI.  
  
 `frameInfo`  
 'ndaki Yığın çerçevesi hakkındaki bilgileri gösteren `COR_PRF_FRAME_INFO` değeri.  
  
 `pClassId`  
 dışı İşlevin üst sınıfına yönelik bir işaretçi.  
  
 `pModuleId`  
 dışı İşlevin üst sınıfının tanımlandığı modüle yönelik bir işaretçi.  
  
 `pToken`  
 dışı İşlevin meta veri belirtecine yönelik bir işaretçi.  
  
 `cTypeArgs`  
 'ndaki `typeArgs` dizisinin boyutu.  
  
 `pcTypeArgs`  
 dışı `ClassID` değerlerinin toplam sayısına yönelik bir işaretçi.  
  
 `typeArgs`  
 dışı Her biri işlevin tür bağımsız değişkeninin KIMLIĞI olan `ClassID` değerleri dizisi. Yöntemi döndürüldüğünde, `typeArgs` `ClassID` değerlerinin bazılarını veya tümünü içerecektir.  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu kodu, belirli bir modül için [meta](../../../../docs/framework/unmanaged-api/metadata/index.md) veri arabirimi elde etmek üzere [ICorProfilerInfo:: GetModuleMetaData öğesini](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) çağırabilir. `pToken` tarafından başvurulan konuma döndürülen meta veri belirteci, daha sonra işlevin meta verilerine erişmek için kullanılabilir.  
  
 `pClassId` ve `typeArgs` parametreleri aracılığıyla döndürülen sınıf KIMLIĞI ve tür bağımsız değişkenleri, aşağıdaki tabloda gösterildiği gibi `frameInfo` parametresine geçirilen değere bağlıdır.  
  
|`frameInfo` parametresinin değeri|Sonuç|  
|----------------------------------------|------------|  
|`FunctionEnter2` geri çağrısından alınan `COR_PRF_FRAME_INFO` değeri|`pClassId`tarafından başvurulan konumda döndürülen `ClassID`ve `typeArgs` dizisinde döndürülen tüm tür bağımsız değişkenleri, tam olarak olacaktır.|  
|`FunctionEnter2` geri çağırma dışında bir kaynaktan alınan `COR_PRF_FRAME_INFO`|Tam `ClassID` ve tür bağımsız değişkenleri belirlenemiyor. Diğer bir deyişle, `ClassID` null olabilir ve bazı tür bağımsız değişkenleri <xref:System.Object>olarak geri gelebilir.|  
|Sıfırlama|Tam `ClassID` ve tür bağımsız değişkenleri belirlenemiyor. Diğer bir deyişle, `ClassID` null olabilir ve bazı tür bağımsız değişkenleri <xref:System.Object>olarak geri gelebilir.|  
  
 `GetFunctionInfo2` çağrıldıktan sonra, `typeArgs` arabelleğinin tüm `ClassID` değerlerini içerecek kadar büyük olduğunu doğrulamanız gerekir. Bunu yapmak için `pcTypeArgs` işaret eden değeri `cTypeArgs` parametresinin değeri ile karşılaştırın. `pcTypeArgs`, bir `ClassID` değerin boyutuyla `cTypeArgs` daha büyük bir değere işaret ediyorsa, daha büyük bir `pcTypeArgs` arabelleği ayırın, yeni, daha büyük boyuttaki `cTypeArgs` güncelleştirin ve `GetFunctionInfo2` çağırın.  
  
 Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetFunctionInfo2` sıfır uzunluklu `pcTypeArgs` arabelleği ile çağırabilirsiniz. Daha sonra arabellek boyutunu `ClassID` değerinin boyutuna bölünen `pcTypeArgs` içinde döndürülen değere ayarlayabilirsiniz ve `GetFunctionInfo2` yeniden çağırın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
