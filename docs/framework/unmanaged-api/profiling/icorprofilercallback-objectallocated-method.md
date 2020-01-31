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
ms.openlocfilehash: 38d9e83e9fa0e9cd0586fb10a6fd79c29bead4a6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866110"
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

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ClassLoadStarted Yöntemi](icorprofilercallback-classloadstarted-method.md)
- [ClassLoadFinished Yöntemi](icorprofilercallback-classloadfinished-method.md)
