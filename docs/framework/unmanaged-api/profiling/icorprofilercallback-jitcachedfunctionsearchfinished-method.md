---
title: "ICorProfilerCallback::JITCachedFunctionSearchFinished Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ffbe331399334d179cf8325e7d9e6773b5bf7012
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a>ICorProfilerCallback::JITCachedFunctionSearchFinished Yöntemi
Profil Oluşturucu, arama yerel Görüntü Oluşturucu (NGen.exe) kullanarak önceden derlenen bir işlev için tamamlandığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] Arama gerçekleştirilip gerçekleştirilmediğine işlevi kimliği.  
  
 `result`  
 [in] Değerini [cor_prf_jıt_cache](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) arama sonucu gösterir numaralandırması.  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürüm 2.0, [Icorprofilercallback::jıtcachedfunctionsearchstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) ve `JITCachedFunctionSearchFinished` geri aramalar değil oluşturulacak normal NGen görüntüleri uygulamasında tüm işlevleri için. Yalnızca bir profil oluşturucu için en iyi duruma getirilmiş NGen görüntüleri tüm işlevleri için geri çağırmaları görüntüde oluşturur. Yalnızca bir işlevin derlenmiş tam zamanında (JIT) olmasını zorlamak için bu geri aramalar kullanmaya çalışırsa, ancak ek yükü nedeniyle, bir profil oluşturucu profil oluşturucu en iyileştirilmiş NGen görseller istemeniz gerekir. Aksi takdirde, profil oluşturucu işlevi bilgilerini toplamak için yavaş bir strateji kullanmanız gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icorprofilercallback arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
