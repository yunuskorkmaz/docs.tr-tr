---
title: ICorProfilerCallback::ExceptionCatcherLeave Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherLeave
helpviewer_keywords:
- ExceptionCatcherLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCatcherLeave method [.NET Framework profiling]
ms.assetid: 1f3dbdf5-db0c-4b07-bbb7-375de2a63673
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4f6f5dd757fde9d49fe8b5a1709d6d5876ce5b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592214"
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a>ICorProfilerCallback::ExceptionCatcherLeave Yöntemi
Denetimi uygun dışında geçirilen profil oluşturucu bildirir `catch` blok.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Yığın atık toplama izin veren bir durumda olmayabilir çünkü profil oluşturucu bu yöntemin uygulanması Engellemesi gereken değil ve bu nedenle preemptive çöp toplama etkinleştirilemez. Burada profil oluşturucu engellerse ve çöp toplama denenir, çalışma zamanı, bu geri dönene kadar engeller.  
  
 Bu yöntemin uygulanmasını profil oluşturucunun yönetilen koda veya herhangi bir yönetilen bellek ayırma yol neden çağırmalıdır değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ExceptionCatcherEnter Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)
