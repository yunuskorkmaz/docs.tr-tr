---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo7:: GetInMemorySymbolsLength yöntemi'
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
ms.openlocfilehash: 5d96b17e8abbd023f2d050eff3f121a871a94754
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737122"
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
 dışı Bir değere yönelik, `DWORD` yöntemin döndürdüğü bir işaretçi, akışın uzunluğunu bayt olarak içerir.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, `S_OK` sıfır (0) olsa bile, bellek akışının uzunluğu belirlenebileceği takdirde döndürülür.  
  
 Yöntemi `CORPROF_E_MODULE_IS_DYNAMIC` , yöntemi kullanılarak oluşturulduysa döndürür <xref:System.Reflection.Emit?displayProperty=nameWithType> .  
  
## <a name="remarks"></a>Açıklamalar  

 Modülün bellek içi sembolleri varsa, akışın uzunluğu içine yerleştirilir `pCountSymbolBytes` . Modülün bellek içi sembolleri yoksa `*pCountSymbolBytes = 0` .  
  
> [!NOTE]
> Geçerli uygulama Reflection. yayma 'yi desteklemiyor. Modül Reflection. yayma kullanılarak oluşturulduysa, yöntemi döndürür `CORPROF_E_MODULE_IS_DYNAMIC` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo7 Arabirimi](icorprofilerinfo7-interface.md)
