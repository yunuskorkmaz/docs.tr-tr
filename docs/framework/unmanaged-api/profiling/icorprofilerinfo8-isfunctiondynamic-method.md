---
title: 'ICorProfilerInfo8:: ısfunctiondynamic'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.IsFunctionDynamic
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 71c4e749368dce65d5250b9ab78fd8713e9d61a0
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973710"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a>ICorProfilerInfo8:: ısfunctiondynamic yöntemi
  
  Bir işlevin ilişkili meta veriye sahip olup olmadığını belirler.    
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionId` \
  'ndaki  `FunctionID` Bu işlev, söz konusu işlevi tanımlar.

  `isDynamic` \
  dışı İşlevin bir işaretçisi `BOOL` , işlevinin meta veri içermediğini belirten bir değer içerir.

## <a name="remarks"></a>Açıklamalar  
 Bir işlev, meta veri yoksa dinamik olarak değerlendirilir. Il saplamaları veya LCG yöntemleri gibi bazı yöntemlerin, IMetaDataImport API 'Leri kullanılarak alınabilecek ilişkili meta verileri yoktur. Bu yöntemlere, profil oluşturucular ile yönerge işaretçileri aracılığıyla veya [ICorProfilerCallback::D ynamicmethodjitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)' i dinleyerek karşılaşılabilir.

## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorProf. IDL, CorProf. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [! [NET_CURRENT_V472PLUS](../../../../includes/net-current-v472plus.md) Ekle  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo8 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)

