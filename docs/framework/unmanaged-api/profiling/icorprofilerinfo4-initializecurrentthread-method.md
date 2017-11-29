---
title: "ICorProfilerInfo4::InitializeCurrentThread Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4::InitializeCurrentThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bc19ae86c266c74097bd649aa96f532528df3d7c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>ICorProfilerInfo4::InitializeCurrentThread Yöntemi
Bu kilitlenme önlenebilir şekilde aynı iş parçacığı üzerinde API çağrılarının sonraki profil oluşturucu çalıştırılmasının geçerli iş parçacığının başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Sizi aramasını öneririz `InitializeCurrentThread` bir profil oluşturucu arayacağı herhangi bir iş parçacığı üzerinde varken API iş parçacıklarını askıya alındı. Bu yöntemi çağırmak için kendi iş parçacığı oluşturma örnekleme profil oluşturucular tarafından genellikle kullanılan [Icorprofilerınfo2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yığın yapmak için yöntemi hedef iş parçacığı askıya alınmış durumdayken anlatılmaktadır. Çağırarak `InitializeCurrentThread` profil oluşturucu örnekleme iş parçacığı ilk oluşturduğunda sonra profil oluşturucular CLR Aksi durumda ilk çağrıda sırasında gerçekleştireceği bu yavaş iş parçacığı başına başlatma sağlayabilirsiniz `DoStackSnapshot` artık güvenli bir şekilde başka bir iş parçacığı olduğunda ortaya çıkabilir askıya alındı.  
  
> [!NOTE]
>  `InitializeCurrentThread`önceden kilitleri alın ve kilitlenme görevleri tamamlamak için başlatma yapar. Çağrı `InitializeCurrentThread` yalnızca askıya alınmış iş parçacığı olduğunda.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icorprofilerınfo4 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Profil oluşturma arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
