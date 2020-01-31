---
title: ICorProfilerCallback::JITCachedFunctionSearchStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type:
- apiref
ms.openlocfilehash: 964ea11b8e8c8f494066249f7da2057970d7e8f4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866266"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a>ICorProfilerCallback::JITCachedFunctionSearchStarted Yöntemi
Profil oluşturucuyu, önceden yerel görüntü Oluşturucu (NGen. exe) kullanılarak derlenen bir işlev için bir aramanın başlatıldığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a>Parametreler

- `functionId`

  \[içinde] aramanın gerçekleştirildiği işlevin KIMLIĞI.

- `pbUseCachedFunction`

  \[out], yürütme altyapısının bir işlevin önbelleğe alınmış sürümünü (varsa) kullanması gerekiyorsa `true`; Aksi takdirde `false`. Değer `false`ise, yürütme motoru JıT-derlenen bir sürümü kullanmak yerine, işlevi derler.

## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürüm 2,0 ' de, normal NGen görüntülerinde tüm işlevler için `JITCachedFunctionSearchStarted` ve [ICorProfilerCallback:: JITCachedFunctionSearchFinished Yöntem](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) geri çağırmaları yapılmayacak. Yalnızca bir profil için iyileştirilmiş NGen görüntüleri görüntüdeki tüm işlevler için geri çağrılar oluşturacaktır. Bununla birlikte, ek yük nedeniyle, profil oluşturucu en iyi duruma getirilmiş NGen görüntülerini yalnızca bir işlevin tam zamanında (JıT) derlenmesi için bu geri çağırmaları kullanmayı amaçladığında istemelidir. Aksi takdirde, profil oluşturucunun işlev bilgilerini toplamak için bir yavaş strateji kullanması gerekir.  
  
 Profil oluşturucular, profili oluşturulmuş bir uygulamanın birden çok iş parçacığının aynı yöntemi eşzamanlı olarak çağıran durumları desteklemelidir. Örneğin, bir çağrı `JITCachedFunctionSearchStarted` iş parçacığı ve profil oluşturucu, JıT derlemesini zorlamak için *pbUseCachedFunction*değerini false olarak ayarlayarak yanıt verir. Sonra bir A iş parçacığı [ICorProfilerCallback:: JCOR, Started](icorprofilercallback-jitcompilationstarted-method.md) ve [ICorProfilerCallback:: JCOR, finished işlemini](icorprofilercallback-jitcompilationfinished-method.md)çağırır.  
  
 Şimdi iş parçacığı B aynı işlev için `JITCachedFunctionSearchStarted` çağırır. Profil Oluşturucu, işlevi JıT-Derle öğesine belirtse de, profil oluşturucu ikinci geri aramayı alır çünkü bu, {1} iş parçacığı, Oluşturucu A 'nın `JITCachedFunctionSearchStarted`çağrısına yanıt vermeden önce geri çağırma işlemini gönderir. İş parçacıklarının çağrı yaptığı sıra, iş parçacıklarının nasıl zamanlandığına bağlıdır.  
  
 Profil Oluşturucu yinelenen geri çağrılar aldığında, `pbUseCachedFunction` tarafından başvurulan değeri tüm yinelenen geri çağırmalar için aynı değere ayarlaması gerekir. Diğer bir deyişle, `JITCachedFunctionSearchStarted` aynı `functionId` değeri ile birden çok kez çağrıldığında, profil oluşturucunun her seferinde aynı yanıt vermesi gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
