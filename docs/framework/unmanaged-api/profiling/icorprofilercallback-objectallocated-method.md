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
ms.openlocfilehash: fda234a6a280aeea1f497ad195d6d41efb6aa951
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674352"
---
# <a name="icorprofilercallbackobjectallocated-method"></a>ICorProfilerCallback::ObjectAllocated Yöntemi

Profil oluşturucuya, yığın içindeki belleğin bir nesne için ayrıldığını bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
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

 `ObjectedAllocated`Yöntemi, yığından veya yönetilmeyen bellekten ayırmalar için çağrılmaz. `classId`Parametresi, henüz yüklenmemiş Yönetilen koddaki bir sınıfa başvurabilir. Profil Oluşturucu, geri aramadan hemen sonra bu sınıf için bir sınıf yükü geri çağırması alır `ObjectAllocated` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ClassLoadStarted Yöntemi](icorprofilercallback-classloadstarted-method.md)
- [ClassLoadFinished Yöntemi](icorprofilercallback-classloadfinished-method.md)
