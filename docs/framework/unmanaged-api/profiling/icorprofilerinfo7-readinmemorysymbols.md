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
ms.openlocfilehash: 53c01d2db44f4d0adf1ba5b9cc225ab49581aa5d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868349"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7:: ReadInMemorySymbols
[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]  
  
 Bellek içi sembol akışından gelen baytları okur.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 dışı Verilerin kopyalanacağı arabelleğe yönelik bir işaretçi. Arabellekte kullanılabilir alan `countSymbolBytes` olmalıdır.  
  
 `countSymbolBytes`  
 'ndaki Kopyalanacak bayt sayısı.  
  
 `pCountSymbolBytesRead`  
 dışı Yöntemi döndüğünde, okunan bayt sayısını içerir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 sıfır olmayan bir bayt sayısı okundum `S_OK`.  
  
 Modül <xref:System.Reflection.Emit>kullanılarak oluşturulduysa `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="remarks"></a>Açıklamalar  
 `ReadInMemorySymbols` yöntemi, bellek içi akış içindeki `symbolsReadOffset` uzaklığında başlayarak verilerin `countSymbolBytes` okumaya çalışır. Veriler, kullanılabilir alan `countSymbolBytes` olması beklenen `pSymbolBytes`kopyalanır.     `pCountSymbolsBytesRead`, okunan bayt sayısını içerir, bu, akışın sonuna ulaşılırsa `countSymbolBytes` daha az olabilir.  
  
> [!NOTE]
> Geçerli uygulama Reflection. yayma 'yi desteklemiyor. Modül Reflection. yayma kullanılarak oluşturulduysa, yöntemi `CORPROF_E_MODULE_IS_DYNAMIC`döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo7 Arabirimi](icorprofilerinfo7-interface.md)
