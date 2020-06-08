---
title: 'ICorProfilerInfo7:: ReadInMemorySymbols'
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
ms.openlocfilehash: 6732457220d795bbf8ae54277ef9f5c07cf96359
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495365"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7:: ReadInMemorySymbols
[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]  
  
 Bellek içi sembol akışından gelen baytları okur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
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
 'ndaki Bellek içi akışı içeren modülün tanıtıcısı.  
  
 `symbolsReadOffset`  
 'ndaki Bayt okumaya başlamak için bellek içi akış içindeki fark.  
  
 `pSymbolBytes`  
 dışı Verilerin kopyalanacağı arabelleğe yönelik bir işaretçi. Arabellekte `countSymbolBytes` kullanılabilir alan olması gerekir.  
  
 `countSymbolBytes`  
 'ndaki Kopyalanacak bayt sayısı.  
  
 `pCountSymbolBytesRead`  
 dışı Yöntemi döndüğünde, okunan bayt sayısını içerir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`sıfır olmayan bir bayt miktarı okundum.  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`, modül kullanılarak oluşturulduysa <xref:System.Reflection.Emit> .  
  
## <a name="remarks"></a>Açıklamalar  
 `ReadInMemorySymbols`Yöntemi, `countSymbolBytes` `symbolsReadOffset` bellek içi akış içinde uzaklığında başlayarak verileri okumaya çalışır. Veriler `pSymbolBytes` , kullanılabilir alan olması beklenen öğesine kopyalanır `countSymbolBytes` .     `pCountSymbolsBytesRead`okunan toplam bayt sayısını içerir, bu da `countSymbolBytes` akışın sonuna ulaşılırsa daha az olabilir.  
  
> [!NOTE]
> Geçerli uygulama Reflection. yayma 'yi desteklemiyor. Modül Reflection. yayma kullanılarak oluşturulduysa, yöntemi döndürür `CORPROF_E_MODULE_IS_DYNAMIC` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo7 Arabirimi](icorprofilerinfo7-interface.md)
