---
description: ': ICorProfilerCallback:: kapanıyor yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::Shutdown Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
ms.openlocfilehash: 7afc274579f248ee190e379160f2709b5cb9881a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657326"
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown Yöntemi

Profil oluşturucuyu uygulamanın kapandığını bildirir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>Açıklamalar  

 Profil Oluşturucu kodu, yöntemi çağrıldıktan sonra [ICorProfilerInfo](icorprofilerinfo-interface.md) arabiriminin yöntemlerini güvenli bir şekilde çağıramaz `Shutdown` . Yöntemlere yapılan çağrılar `ICorProfilerInfo` , yöntemin dönüşden sonra tanımsız davranışa neden olur `Shutdown` . Bazı sabit olaylar, kapatmadan sonra yine de gerçekleşebilir; Profil Oluşturucu, bu gerçekleştiğinde hemen döndürülmelidir.  
  
 `Shutdown`Yöntemi yalnızca, profili oluşturulan yönetilen uygulama yönetilen kod olarak (yani, işlem yığınındaki ilk çerçeve yönetiliyorsa) başlatıldığında çağrılır. Uygulama, yönetilmeyen kod olarak başlatıldıysa ancak daha sonra yönetilen koda atlamışsa, bu nedenle ortak dil çalışma zamanının (CLR) bir örneğini oluşturur, ardından `Shutdown` çağrılmaz. Bu gibi durumlarda, profil oluşturucu kendi kitaplığına `DllMain` , herhangi bir kaynağı boşaltmak ve verilerin temizleme işlemini gerçekleştirmek için DLL_PROCESS_DETACH değerini kullanan bir yordamı içermelidir.  
  
 Genel olarak, profil oluşturucunun beklenmedik kapanmalar ile Cope olması gerekir. Örneğin, bir işlem Win32's yöntemi tarafından durdurulur `TerminateProcess` (Winbase. h içinde bildirilmiştir). Diğer durumlarda CLR, belirli yönetilen iş parçacıklarını (arka plan iş parçacıkları) bunlar için düzenli olarak yok etme iletileri teslim etmeden durdurur.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [Initialize Yöntemi](icorprofilercallback-initialize-method.md)
