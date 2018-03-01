---
title: "ICorProfilerInfo4::InitializeCurrentThread Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f3c261068b38861dca2633a490e46d9f44371d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
 [ICorProfilerInfo4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
