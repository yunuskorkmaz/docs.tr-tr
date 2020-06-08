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
ms.openlocfilehash: f5438ddc655f0f6a7c11d978a47b1bf9e2a13059
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497016"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a>ICorProfilerInfo2::GetFunctionInfo2 Yöntemi
Bir işlevin varsa, üst sınıfı, meta veri belirtecini ve `ClassID` her tür bağımsız değişkenini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki `COR_PRF_FRAME_INFO`Yığın çerçevesi hakkındaki bilgileri gösteren bir değer.  
  
 `pClassId`  
 dışı İşlevin üst sınıfına yönelik bir işaretçi.  
  
 `pModuleId`  
 dışı İşlevin üst sınıfının tanımlandığı modüle yönelik bir işaretçi.  
  
 `pToken`  
 dışı İşlevin meta veri belirtecine yönelik bir işaretçi.  
  
 `cTypeArgs`  
 'ndaki `typeArgs`Dizinin boyutu.  
  
 `pcTypeArgs`  
 dışı Toplam değer sayısına yönelik bir işaretçi `ClassID` .  
  
 `typeArgs`  
 dışı `ClassID`Her biri işlevin tür bağımsız DEĞIŞKENININ kimliği olan bir değer dizisi. Yöntemi döndürüldüğünde, `typeArgs` değerlerin bazılarını veya tümünü içerecektir `ClassID` .  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu kodu, belirli bir modül için [meta](../metadata/index.md) veri arabirimi elde etmek üzere [ICorProfilerInfo:: GetModuleMetaData öğesini](icorprofilerinfo-getmodulemetadata-method.md) çağırabilir. Tarafından başvurulan konuma döndürülen meta veri belirteci, `pToken` daha sonra işlevin meta verilerine erişmek için kullanılabilir.  
  
 Ve parametreleri aracılığıyla döndürülen sınıf KIMLIĞI ve tür bağımsız değişkenleri, `pClassId` `typeArgs` `frameInfo` Aşağıdaki tabloda gösterildiği gibi, parametresine geçirilen değere bağlıdır.  
  
|`frameInfo`Parametrenin değeri|Sonuç|  
|----------------------------------------|------------|  
|`COR_PRF_FRAME_INFO`Bir geri aramadan alınan bir değer `FunctionEnter2`|`ClassID`Tarafından başvurulan konumda döndürülen, `pClassId` ve dizide döndürülen tüm tür bağımsız değişkenleri `typeArgs` tam olarak olacaktır.|  
|`COR_PRF_FRAME_INFO`Geri çağırma dışında bir kaynaktan alınan bir `FunctionEnter2`|Tam `ClassID` ve tür bağımsız değişkenleri belirlenemiyor. Diğer bir deyişle, `ClassID` null olabilir ve bazı tür bağımsız değişkenleri yeniden gelebilir <xref:System.Object> .|  
|Sıfır|Tam `ClassID` ve tür bağımsız değişkenleri belirlenemiyor. Diğer bir deyişle, `ClassID` null olabilir ve bazı tür bağımsız değişkenleri yeniden gelebilir <xref:System.Object> .|  
  
 `GetFunctionInfo2`Geri döndüğünde, `typeArgs` arabelleğin tüm değerleri içerecek kadar büyük olduğunu doğrulamanız gerekir `ClassID` . Bunu yapmak için, işaret eden değeri `pcTypeArgs` parametresinin değeriyle karşılaştırın `cTypeArgs` . `pcTypeArgs`Değerin boyutuyla daha büyük bir değere işaret ediyorsa `cTypeArgs` `ClassID` , daha büyük bir `pcTypeArgs` arabellek ayırır, `cTypeArgs` Yeni, daha büyük boyutla güncelleştirin ve `GetFunctionInfo2` yeniden çağırın.  
  
 Alternatif olarak, `GetFunctionInfo2` `pcTypeArgs` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz. Daha sonra, arabellek boyutunu `pcTypeArgs` bir değer boyutuna bölünen olarak döndürülen değere ayarlayabilir `ClassID` ve `GetFunctionInfo2` yeniden çağırabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
