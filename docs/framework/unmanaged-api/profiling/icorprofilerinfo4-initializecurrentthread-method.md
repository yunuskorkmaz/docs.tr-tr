---
title: ICorProfilerInfo4::InitializeCurrentThread Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abcbfaf803e930baaaf798986a585a7da5f9134d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780793"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>ICorProfilerInfo4::InitializeCurrentThread Yöntemi
Geçerli iş parçacığı sonraki profil oluşturucu bu kilitlenme önlenebilir şekilde aynı iş parçacığında API çağrılarının tarifelerindeki başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Çağırmanızı öneririz `InitializeCurrentThread` bir profil oluşturucu çağıran herhangi bir iş parçacığı üzerinde varken API iş parçacıkları askıya alındı. Bu yöntem çağırmak için kendi iş parçacığı oluşturma örnekleme profil oluşturucular tarafından genellikle kullanılan [Icorprofilerınfo2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yığın gerçekleştirmek için yöntemi hedef iş parçacığını askıya alındığında size yol gösterir. Çağırarak `InitializeCurrentThread` zaman profil oluşturucu örnekleme iş parçacığı ilk oluşturulduktan sonra profil Oluşturucular, CLR Aksi takdirde ilk çağrı sırasında gerçekleştirecek yavaş iş parçacığı başına başlatmanın sağlayabilirsiniz `DoStackSnapshot` artık güvenli bir şekilde başka bir iş parçacığı olduğunda ortaya çıkabilir askıya alındı.  
  
> [!NOTE]
>  `InitializeCurrentThread` önceden kilit alın ve kilitlenme görevleri tamamlamak için başlatma yapar. Çağrı `InitializeCurrentThread` askıya alınan iş parçacığı olmadığında.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
