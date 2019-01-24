---
title: ICorProfilerCallback::ObjectAllocated Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e1c777a2512306c41413377530576fbe8ad8e7ac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582298"
---
# <a name="icorprofilercallbackobjectallocated-method"></a>ICorProfilerCallback::ObjectAllocated Yöntemi
Bir nesne için bellek yığında ayrılan profil oluşturucu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `objectId`  
 [in] Kendisi için bellek ayrılan nesnesinin kimliği.  
  
 `classId`  
 [in] Nesnesinin bir örneği olduğu sınıfın Kimliğidir.  
  
## <a name="remarks"></a>Açıklamalar  
 `ObjectedAllocated` Yöntemi yığını veya yönetilmeyen bellek ayırmaları için çağrılmaz. `classId` Parametre henüz yüklü değil, yönetilen kodda bir sınıfa başvurabilir. Profil Oluşturucu o sınıf için bir sınıf yük geri alacak hemen sonra `ObjectAllocated` geri çağırma.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ClassLoadStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
- [ClassLoadFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
