---
title: ICorProfilerFunctionControl::SetILInstrumentedCodeMap Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetIILInstrumentedCodeMap method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: ecf56646-7e5f-46c4-8340-f3a04e88920f
topic_type:
- apiref
ms.openlocfilehash: b2fca16b3b859df8bd7409149eb5a3cf7b011c5c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864589"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a>ICorProfilerFunctionControl::SetILInstrumentedCodeMap Yöntemi
Belirtilen ortak ara dil (CıL) eşleme girdilerini kullanarak belirtilen işlev için bir kod Haritası ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cILMapEntries`  
 'ndaki Eşlemedeki girdi sayısı.  
  
 `rgILMapEntries`  
 'ndaki COR_IL_MAP girdilerinin çağıran ayrılmış dizisi. Bu girdilerin yorumu [ICorProfilerInfo:: Setilınstrumentedcodemap](icorprofilerinfo-setilinstrumentedcodemap-method.md) yöntemi ile aynıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntemi çağırarak eşlemenin ayarlanması, [ICorDebugILCode2:: GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)çağırarak hata ayıklayıcının eşlemeyi almasına izin verir. Ayrıca, yığın izlemeleri ve değişken yaşam süreleri için Il farklarını hesaplarken hata ayıklayıcının eşlemeyi dahili olarak kullanmasına de olanak tanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
