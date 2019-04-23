---
title: ICorProfilerInfo7::GetInMemorySymbolsLength yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 422fdfef6bea40e0f4bcc7447df8dba1eab2896e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146100"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a>ICorProfilerInfo7::GetInMemorySymbolsLength yöntemi
[.NET Framework 4.6.1 ve sonraki sürümlerinde desteklenen]  
  
 Bir bellek içi sembol akış uzunluğunu döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleId`  
 [in] Bellek içi akış içeren modül tanıtıcısı.  
  
 pCountSymbolBytes  
 [out] Bir işaretçi bir `DWORD` yöntem döndürüldüğünde, akış bayt cinsinden uzunluğunu içeren bir değer.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem döndürür `S_OK` sıfır (0) olsa bile bellek akışının uzunluğu, belirlenebilir durumunda.  
  
 Yöntem döndürür `CORPROF_E_MODULE_IS_DYNAMIC` yöntemi kullanılarak oluşturulmuşsa <xref:System.Reflection.Emit?displayProperty=nameWithType>.  
  
## <a name="remarks"></a>Açıklamalar  
 Modül bellek içi simgeleri varsa, akışın uzunluğu yerleştirildi `pCountSymbolBytes`. Bellek içi sembolleri modülü yoksa `*pCountSymbolBytes = 0`.  
  
> [!NOTE]
>  Geçerli uygulama Reflection.Emit desteklemez. Modül Reflection.Emit kullanılarak oluşturulduysa, yöntem döndürür `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo7 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
