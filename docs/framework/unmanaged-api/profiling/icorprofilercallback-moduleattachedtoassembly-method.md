---
title: "ICorProfilerCallback::ModuleAttachedToAssembly Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleAttachedToAssembly
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6183014bf5487d0eebccf2fb70a13c363212046b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a>ICorProfilerCallback::ModuleAttachedToAssembly Yöntemi
Profil Oluşturucu bir modül kendi üst derlemeye bağlı olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `moduleId`  
 [in] İliştirilmekte olan modül kimliği.  
  
 `AssemblyId`  
 [in] Modül bağlı olduğu üst derleme kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir modülü içeri aktarma adres tablosunu (IAT) bir çağrıyla yüklenebilir `LoadLibrary`, veya bir meta veri başvuru. Sonuç olarak, ortak dil çalışma zamanı (CLR) yükleyicisi, bir modül yaşadığı derleme belirlemek için birden çok kod yolları vardır. Bu nedenle, olası bundan sonra [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) çağrılır modülü hangi derleme bilmez olarak ve üst derleme kimliği alma mümkün değildir. `ModuleAttachedToAssembly` Modülü kendi üst derleme ve kimliği elde edilebilir kendi üst derleme iliştirildiğinde yöntemi çağrılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
