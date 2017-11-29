---
title: ICorProfilerInfo7::ReadInMemorySymbols
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type: COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9ada9f629c3a3c3d8b7c32ebc180c4788b6f6d3f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
 `ReadInMemorySymbols` Yöntemi çalışır okumak `countSymbolBytes` uzaklıkta başlayan veri `symbolsReadOffset` bellek içi akışındaki. Veriler kopyalanır `pSymbolBytes`, olması beklenen `countSymbolBytes` alanı kullanılabilir.     `pCountSymbolsBytesRead`Gerçek, daha az olabilir, okunan bayt sayısını içeren daha `countSymbolBytes` akışın sonuna ulaşıldı durumunda.  
  
> [!NOTE]
>  Geçerli uygulama Reflection.Emit desteklemez. Modül Reflection.Emit kullanılarak oluşturulup oluşturulmadığını, yöntem `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo7 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
