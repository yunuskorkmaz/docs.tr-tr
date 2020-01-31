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
ms.openlocfilehash: b52a0e7f993629c1005883723c734996d75300a7
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868440"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>ICorProfilerInfo4::InitializeCurrentThread Yöntemi
Geçerli iş parçacığını aynı iş parçacığında sonraki profil oluşturucu API çağrılarından önce başlatır, böylece kilitlenme kaçınılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Askıya alınmış iş parçacıkları varken profil oluşturucu API çağrısı yapılacak herhangi bir iş parçacığında `InitializeCurrentThread` çağırmalarını öneririz. Bu yöntem genellikle, hedef iş parçacığı askıya alınırken yığın izlenecek yol için [ICorProfilerInfo2::D oStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) metodunu çağırmak üzere kendi iş parçacığını oluşturan örnekleme profil oluşturucular tarafından kullanılır. Profil Oluşturucu ilk olarak örnekleme iş parçacığını oluşturduğunda `InitializeCurrentThread` bir kez çağırarak, profil oluşturucular ilk çağrı sırasında CLR 'nin geçici `DoStackSnapshot` olarak gerçekleştireceği yavaş iş parçacığı başlatma işleminin başka bir iş parçacığı askıya alınmadıkça güvenli bir şekilde gerçekleşmemesini sağlayabilir.  
  
> [!NOTE]
> `InitializeCurrentThread`, kilitleri kilitleyen ve kilitlenmeleri gereken görevleri tamamlamak için önceden başlatma işlemi yapar. Yalnızca askıya alınmış iş parçacığı olmadığında `InitializeCurrentThread` çağırın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo4 Arabirimi](icorprofilerinfo4-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
