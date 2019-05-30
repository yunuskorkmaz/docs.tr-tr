---
title: ICorProfilerInfo7::ReadInMemorySymbols
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3df5324e23ebeded38f3aa9843f81701f7fd333
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251055"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7::ReadInMemorySymbols
[.NET Framework 4.6.1 ve sonraki sürümlerinde desteklenen]  
  
 Bayt bir bellek içi sembol akıştan okur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleId`  
 [in] Bellek içi akış içeren modül tanıtıcısı.  
  
 `symbolsReadOffset`  
 [in] Bellek içi akış baytlar okunduktan başlayacağı içinde uzaklığı.  
  
 `pSymbolBytes`  
 [out] Verilerin kopyalanacağı arabellek için işaretçi. Arabellek olmalıdır `countSymbolBytes` alanı kullanılabilir.  
  
 `countSymbolBytes`  
 [in] Kopyalanacak bayt sayısı.  
  
 `pCountSymbolBytesRead`  
 [out] Yöntem döndürüldüğünde, okunan bayt sayısını içerir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`, sıfır olmayan birkaç bayt okursanız.  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`, modülü kullanılarak oluşturulmuşsa <xref:System.Reflection.Emit>.  
  
## <a name="remarks"></a>Açıklamalar  
 `ReadInMemorySymbols` Yöntemi okuma girişiminde `countSymbolBytes` uzaklıkta başlayan belirli veri `symbolsReadOffset` bellek içi akış içinde. Verilerin kopyalanacağı `pSymbolBytes`, olması beklenen `countSymbolBytes` alanı kullanılabilir.     `pCountSymbolsBytesRead` Gerçek, daha az olabilir, okunan bayt sayısını içeren daha `countSymbolBytes` akışın sonuna ulaşılırsa.  
  
> [!NOTE]
>  Geçerli uygulama Reflection.Emit desteklemez. Modül Reflection.Emit kullanılarak oluşturulduysa, yöntem döndürür `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo7 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
