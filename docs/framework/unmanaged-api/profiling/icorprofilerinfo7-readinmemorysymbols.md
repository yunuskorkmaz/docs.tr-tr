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
ms.openlocfilehash: 9874c8e567a89fd3977be360666c86406f2cd395
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7::ReadInMemorySymbols
[Desteklenen [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] ve sonraki sürümlerinde]  
  
 Bayt bir bellek içi simgesi akıştan okur.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `moduleId`  
 [in] Bellek içi akış içeren modül tanıtıcısı.  
  
 `symbolsReadOffset`  
 [in] Başlatılacağı bayt okuma bellek içi akışındaki uzaklığı.  
  
 `pSymbolBytes`  
 [out] Veri kopyalanacak arabellek için bir işaretçi. Arabellek olmalıdır `countSymbolBytes` alanı kullanılabilir.  
  
 `countSymbolBytes`  
 [in] Kopyalanacak bayt sayısı.  
  
 `pCountSymbolBytesRead`  
 [out] Yöntem döndüğünde, gerçek okunan bayt sayısını içerir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`, sıfır olmayan bir bayt sayısı okuyorsanız.  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`, modül kullanarak oluşturduysanız <xref:System.Reflection.Emit>.  
  
## <a name="remarks"></a>Açıklamalar  
 `ReadInMemorySymbols` Yöntemi çalışır okumak `countSymbolBytes` uzaklıkta başlayan veri `symbolsReadOffset` bellek içi akışındaki. Veriler kopyalanır `pSymbolBytes`, olması beklenen `countSymbolBytes` alanı kullanılabilir.     `pCountSymbolsBytesRead` Gerçek, daha az olabilir, okunan bayt sayısını içeren daha `countSymbolBytes` akışın sonuna ulaşıldı durumunda.  
  
> [!NOTE]
>  Geçerli uygulama Reflection.Emit desteklemez. Modül Reflection.Emit kullanılarak oluşturulup oluşturulmadığını, yöntem `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo7 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
