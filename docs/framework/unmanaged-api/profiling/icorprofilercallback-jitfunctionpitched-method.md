---
title: "ICorProfilerCallback::JITFunctionPitched Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITFunctionPitched
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 48432911d7844e6519689961c985da37219179a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a>ICorProfilerCallback::JITFunctionPitched Yöntemi
Profil Oluşturucu bildirir, tam zamanında (JIT) boyunca işlevi-derlenmiş bellekten kaldırıldı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] Kaldırıldı işlevi kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 Kaldırılan işlevi çağrıldıysa profil oluşturucu işlevi derlenmiştir yeni JIT derleme olayları alır. Şu anda, böylece bu geri çağırma şu anda kullanılmaz ve Profil Oluşturucu tarafından alınan olmayan ortak dil çalışma zamanı (CLR) JIT Derleyici işlevleri bellekten kaldırmaz.  
  
 Değeri `functionId` işlevi derlenmiştir kadar geçerli değil. İşlev derlenmiştir, aynı `functionId` değeri kullanılacak.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
