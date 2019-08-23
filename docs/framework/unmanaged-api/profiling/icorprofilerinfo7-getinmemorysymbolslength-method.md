---
title: 'ICorProfilerInfo7:: GetInMemorySymbolsLength yöntemi'
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
ms.openlocfilehash: 157b0e215f8afa58cccb3d54a65baa9c307ba966
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955421"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a>ICorProfilerInfo7:: GetInMemorySymbolsLength yöntemi
[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]  
  
 Bellek içi sembol akışının uzunluğunu döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleId`  
 'ndaki Bellek içi akışı içeren modülün tanıtıcısı.  
  
 pCountSymbolBytes  
 dışı Bir `DWORD` değere yönelik, yöntemin döndürdüğü bir işaretçi, akışın uzunluğunu bayt olarak içerir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, `S_OK` sıfır (0) olsa bile, bellek akışının uzunluğu belirlenebileceği takdirde döndürülür.  
  
 Yöntemi, yöntemi `CORPROF_E_MODULE_IS_DYNAMIC` kullanılarak <xref:System.Reflection.Emit?displayProperty=nameWithType>oluşturulduysa döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Modülün bellek içi sembolleri varsa, akışın uzunluğu içine `pCountSymbolBytes`yerleştirilir. Modülün bellek içi sembolleri `*pCountSymbolBytes = 0`yoksa.  
  
> [!NOTE]
> Geçerli uygulama Reflection. yayma 'yi desteklemiyor. Modül Reflection. yayma kullanılarak oluşturulduysa, yöntemi döndürür `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorProf. IDL, CorProf. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo7 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
