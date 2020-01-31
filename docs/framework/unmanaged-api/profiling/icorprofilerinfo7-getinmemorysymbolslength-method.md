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
ms.openlocfilehash: a675cc301d2dd32f87e3864a3123e2044761ef91
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868362"
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
 dışı Bir `DWORD` değeri işaretçisi, yöntemin döndürdüğü, akışın uzunluğunu bayt cinsinden içerir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Sıfır (0) olsa bile, bellek akışının uzunluğu belirlenebilse, yöntem `S_OK` döndürür.  
  
 Yöntemi, yöntem <xref:System.Reflection.Emit?displayProperty=nameWithType>kullanılarak oluşturulduysa `CORPROF_E_MODULE_IS_DYNAMIC` döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Modülün bellek içi sembolleri varsa, akışın uzunluğu `pCountSymbolBytes`yerleştirilir. Modülün bellek içi sembolleri yoksa, `*pCountSymbolBytes = 0`.  
  
> [!NOTE]
> Geçerli uygulama Reflection. yayma 'yi desteklemiyor. Modül Reflection. yayma kullanılarak oluşturulduysa, yöntemi `CORPROF_E_MODULE_IS_DYNAMIC`döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo7 Arabirimi](icorprofilerinfo7-interface.md)
