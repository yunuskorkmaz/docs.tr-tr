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
ms.openlocfilehash: 66643bbb8dbc914b2e0e48a7f0c87630fe95e5d3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445843"
---
# <a name="icorprofilercallbackobjectallocated-method"></a>ICorProfilerCallback::ObjectAllocated Yöntemi
Profil oluşturucuya, yığın içindeki belleğin bir nesne için ayrıldığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a>Parametreler  
 `objectId`  
 'ndaki Belleğin ayrıldığı nesnenin KIMLIĞI.  
  
 `classId`  
 'ndaki Nesnenin bir örnek olduğu sınıfın KIMLIĞI.  
  
## <a name="remarks"></a>Açıklamalar  
 `ObjectedAllocated` yöntemi, yığından veya yönetilmeyen bellekten ayırmalar için çağrılmaz. `classId` parametresi, henüz yüklenmemiş Yönetilen koddaki bir sınıfa başvurabilir. Profil Oluşturucu, `ObjectAllocated` geri çağrısından hemen sonra bu sınıf için bir sınıf yükü geri çağırması alır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ClassLoadStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
- [ClassLoadFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
