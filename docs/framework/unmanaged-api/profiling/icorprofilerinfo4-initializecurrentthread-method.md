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
ms.openlocfilehash: 51f16523c00cc3dd95b786f1586ccfd75ce8d5f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733834"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>ICorProfilerInfo4::InitializeCurrentThread Yöntemi

Geçerli iş parçacığını aynı iş parçacığında sonraki profil oluşturucu API çağrılarından önce başlatır, böylece kilitlenme kaçınılabilir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>Açıklamalar  

 `InitializeCurrentThread`Askıya alınmış iş parçacıkları varken profil oluşturucu API 'si çağıran herhangi bir iş parçacığında çağrı yapmanızı öneririz. Bu yöntem genellikle, hedef iş parçacığı askıya alınırken yığın izlenecek yol için [ICorProfilerInfo2::D oStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) metodunu çağırmak üzere kendi iş parçacığını oluşturan örnekleme profil oluşturucular tarafından kullanılır. `InitializeCurrentThread`Profil Oluşturucu ilk olarak örnekleme iş parçacığını oluşturduğunda, profil oluşturucular, clr 'nin ilk çağrı sırasında gerçekleştireceği yavaş iş parçacığı başlatma `DoStackSnapshot` işleminin, başka bir iş parçacığı askıya alınmadıkça güvenli bir şekilde gerçekleşmemesini sağlayabilir.  
  
> [!NOTE]
> `InitializeCurrentThread` başlatma işlemi, kilitleri olan görevleri tamamlamak için önceden ve kilitlenme olabilir. `InitializeCurrentThread`Yalnızca askıya alınmış iş parçacığı olmadığında çağırın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo4 Arabirimi](icorprofilerinfo4-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
