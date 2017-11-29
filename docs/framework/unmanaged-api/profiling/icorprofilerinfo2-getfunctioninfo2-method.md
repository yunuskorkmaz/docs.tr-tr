---
title: ICorProfilerInfo2::GetFunctionInfo2 Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetFunctionInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetFunctionInfo2
helpviewer_keywords:
- GetFunctionInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetFunctionInfo2 method [.NET Framework profiling]
ms.assetid: 0aa60f24-8bbd-4c83-83c5-86ad191b1d82
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8b0c288b88c868bc6e324ec57b3956344f03f34e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a>ICorProfilerInfo2::GetFunctionInfo2 Metodu
Üst sınıf, meta veri simgesi alır ve `ClassID` işlevinin varsa, her tür bağımsız değişkenin.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `funcId`  
 [in] Üst sınıf ve diğer bilgileri almak üzere işlevi kimliği.  
  
 `frameInfo`  
 [in] A `COR_PRF_FRAME_INFO` noktalarını yığın çerçevesi hakkında bilgi için değer.  
  
 `pClassId`  
 [out] İşlev üst sınıfı için bir işaretçi.  
  
 `pModuleId`  
 [out] İşlevin üst sınıf tanımlandığı modül için bir işaretçi.  
  
 `pToken`  
 [out] İşlev için meta veri simgesi için bir işaretçi.  
  
 `cTypeArgs`  
 [in] Boyutunu `typeArgs` dizi.  
  
 `pcTypeArgs`  
 [out] Toplam sayısını gösteren bir işaretçi `ClassID` değerleri.  
  
 `typeArgs`  
 [out] Bir dizi `ClassID` değerleri, her biri kimliğidir işlevinin tür bağımsız değişkeni. Yöntem döndüğünde `typeArgs` bazılarını veya tümünü içerecek `ClassID` değerleri.  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu kod çağırabilir [Icorprofilerınfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) elde etmek için bir [meta veri](../../../../docs/framework/unmanaged-api/metadata/index.md) verilen modülü için arabirim. Tarafından başvurulan konuma döndürülen meta veri simgesi `pToken` işlevi için meta verilerine erişmek için kullanılabilir.  
  
 Aracılığıyla döndürülen sınıfı kimliği ve tür bağımsız değişkenleri `pClassId` ve `typeArgs` geçirilen değer parametreleri bağlı `frameInfo` aşağıdaki tabloda gösterildiği gibi parametre.  
  
|Değeri `frameInfo` parametresi|Sonuç|  
|----------------------------------------|------------|  
|A `COR_PRF_FRAME_INFO` uygulamasından edinilen değeri bir `FunctionEnter2` geri çağırma|`ClassID`, Döndürülen başvurduğu konumda `pClassId`, ve tüm tür bağımsız değişkenleri, döndürülen `typeArgs` dizisi, tam olacaktır.|  
|A `COR_PRF_FRAME_INFO` , elde bir kaynaktan dışındaki bir `FunctionEnter2` geri çağırma|Tam `ClassID` ve tür bağımsız değişkenleri belirlenemiyor. Diğer bir deyişle, `ClassID` null olabilir ve bazı tür bağımsız değişkenleri gelebilir olarak geri <xref:System.Object>.|  
|Sıfır|Tam `ClassID` ve tür bağımsız değişkenleri belirlenemiyor. Diğer bir deyişle, `ClassID` null olabilir ve bazı tür bağımsız değişkenleri gelebilir olarak geri <xref:System.Object>.|  
  
 Sonra `GetFunctionInfo2` döndürür, doğrulamalısınız `typeArgs` arabellek tüm içerecek şekilde büyük `ClassID` değerleri. Bunu yapmak için değeri karşılaştırın, `pcTypeArgs` değeriyle işaret `cTypeArgs` parametresi. Varsa `pcTypeArgs` işaret eden daha büyük bir değere `cTypeArgs` boyutu tarafından ayrılmış bir `ClassID` değeri, daha geniş bir ayırma `pcTypeArgs` arabellek, güncelleştirme `cTypeArgs` yeni, büyük boyutu ve çağrı `GetFunctionInfo2` yeniden.  
  
 Alternatif olarak, ilk çağırabilirsiniz `GetFunctionInfo2` sıfır uzunluklu ile `pcTypeArgs` arabellek doğru arabellek boyutu elde edilir. Döndürülen değer için arabellek boyutu ayarlayabilirsiniz `pcTypeArgs` boyutu tarafından ayrılmış bir `ClassID` değeri ve çağrı `GetFunctionInfo2` yeniden.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icorprofilerınfo arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Icorprofilerınfo2 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Profil oluşturma arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
