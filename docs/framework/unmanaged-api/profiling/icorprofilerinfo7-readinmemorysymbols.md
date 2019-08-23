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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95b463b23c230d620d746e48da49d75238ef2cb7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955370"
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
 dışı Verilerin kopyalanacağı arabelleğe yönelik bir işaretçi. Arabellekte kullanılabilir alan olması `countSymbolBytes` gerekir.  
  
 `countSymbolBytes`  
 'ndaki Kopyalanacak bayt sayısı.  
  
 `pCountSymbolBytesRead`  
 dışı Yöntemi döndüğünde, okunan bayt sayısını içerir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`sıfır olmayan bir bayt miktarı okundum.  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`, modül kullanılarak <xref:System.Reflection.Emit>oluşturulduysa.  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntemi `ReadInMemorySymbols` , bellek içi akış `countSymbolBytes` içinde uzaklığında `symbolsReadOffset` başlayarak verileri okumaya çalışır. Veriler, kullanılabilir alan olması `pSymbolBytes` `countSymbolBytes` beklenen öğesine kopyalanır.     `pCountSymbolsBytesRead`okunan toplam bayt sayısını içerir, bu da akışın sonuna ulaşılırsa daha `countSymbolBytes` az olabilir.  
  
> [!NOTE]
> Geçerli uygulama Reflection. yayma 'yi desteklemiyor. Modül Reflection. yayma kullanılarak oluşturulduysa, yöntemi döndürür `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorProf. IDL, CorProf. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo7 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
