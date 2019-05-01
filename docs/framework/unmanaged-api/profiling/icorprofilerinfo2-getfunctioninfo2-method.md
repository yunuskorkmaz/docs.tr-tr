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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7b6c19c87aceffd1e199975db6f16191bc3ddd9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782557"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a>ICorProfilerInfo2::GetFunctionInfo2 Yöntemi
Üst sınıfın, meta veri belirteci alır ve `ClassID` işlevinin varsa, her tür bağımsız değişkeninin.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 [in] Üst sınıf ve diğer bilgileri almak işlev kimliği.  
  
 `frameInfo`  
 [in] A `COR_PRF_FRAME_INFO` yığın çerçevesi hakkında bilgi gösteren değer.  
  
 `pClassId`  
 [out] İşlevin üst sınıfı için bir işaretçi.  
  
 `pModuleId`  
 [out] İşlevin üst sınıfı içinde tanımlandığı modül için bir işaretçi.  
  
 `pToken`  
 [out] Meta veri belirteci işlevine yönelik bir işaretçi.  
  
 `cTypeArgs`  
 [in] Boyutu `typeArgs` dizisi.  
  
 `pcTypeArgs`  
 [out] Toplam sayısı için bir işaretçi `ClassID` değerleri.  
  
 `typeArgs`  
 [out] Bir dizi `ClassID` değerler, her biri, bir tür bağımsız değişkeni işlevin Kimliğidir. Yöntem döndürüldüğünde `typeArgs` bazılarını veya tümünü içerecektir `ClassID` değerleri.  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu kodu çağırabilir [Icorprofilerınfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) almak için bir [meta verileri](../../../../docs/framework/unmanaged-api/metadata/index.md) belirli bir modül için arabirim. Tarafından başvurulan konuma döndürülen meta veri belirteci `pToken` işlevi için meta veriler erişmek için kullanılabilir.  
  
 İle döndürülen sınıf kimliği ve tür bağımsız değişkenleri `pClassId` ve `typeArgs` geçirilen değere bağlıdır parametreleri `frameInfo` parametresi, aşağıdaki tabloda gösterildiği gibi.  
  
|Değeri `frameInfo` parametresi|Sonuç|  
|----------------------------------------|------------|  
|A `COR_PRF_FRAME_INFO` elde edildiği değeri bir `FunctionEnter2` geri çağırma|`ClassID`, Tarafından başvurulan konumda döndürülen `pClassId`, ve tüm tür bağımsız değişkenleri, döndürülen `typeArgs` dizi, tam olacaktır.|  
|A `COR_PRF_FRAME_INFO` , alınan bir kaynaktan dışındaki bir `FunctionEnter2` geri çağırma|Tam `ClassID` ve tür bağımsız değişkenleri belirlenemiyor. Diğer bir deyişle, `ClassID` null olabilir ve bazı tür bağımsız değişkenleri gelebilir olarak geri <xref:System.Object>.|  
|Sıfır|Tam `ClassID` ve tür bağımsız değişkenleri belirlenemiyor. Diğer bir deyişle, `ClassID` null olabilir ve bazı tür bağımsız değişkenleri gelebilir olarak geri <xref:System.Object>.|  
  
 Sonra `GetFunctionInfo2` döndürür, doğrulamalısınız `typeArgs` arabellek tüm içerecek şekilde büyük `ClassID` değerleri. Bunu yapmak için değeri ile karşılaştırmak, `pcTypeArgs` değeriyle işaret `cTypeArgs` parametresi. Varsa `pcTypeArgs` işaret değerinden daha büyük bir değere `cTypeArgs` boyutu tarafından ayrılmış bir `ClassID` değeri, daha büyük bir ayırma `pcTypeArgs` arabellek, güncelleştirme `cTypeArgs` yeni, daha büyük bir boyut ve çağrı `GetFunctionInfo2` yeniden.  
  
 Alternatif olarak, ilk çağırabilirsiniz `GetFunctionInfo2` sıfır uzunluklu ile `pcTypeArgs` arabellek doğru arabellek boyutu elde edilir. Arabellek boyutu döndürülen değere ayarlayabilirsiniz `pcTypeArgs` boyutu tarafından ayrılmış bir `ClassID` değeri ve çağrı `GetFunctionInfo2` yeniden.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
