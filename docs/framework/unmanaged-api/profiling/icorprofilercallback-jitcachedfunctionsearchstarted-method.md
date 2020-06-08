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
ms.openlocfilehash: d8f4a04abea0bd5eb9bf38629a8fcaf76479bcc9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500069"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a>ICorProfilerCallback::JITCachedFunctionSearchStarted Yöntemi
Profil oluşturucuyu, önceden yerel görüntü Oluşturucu (NGen. exe) kullanılarak derlenen bir işlev için bir aramanın başlatıldığını bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a>Parametreler

- `functionId`

  \[' de] aramanın gerçekleştirildiği işlevin KIMLIĞI.

- `pbUseCachedFunction`

  \[out] `true` yürütme altyapısının bir işlevin önbelleğe alınmış sürümünü kullanması gerekiyorsa (varsa); Aksi takdirde `false` . Değer ise `false` , yürütme ALTYAPıSı JIT-derlenmiş olmayan bir sürümü kullanmak yerine, işlevi derler.

## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürüm 2,0 ' de, `JITCachedFunctionSearchStarted` ve [ICorProfilerCallback:: JITCachedFunctionSearchFinished Yöntem](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) geri çağırmaları normal Ngen görüntülerinde tüm işlevler için yapılmayacak. Yalnızca bir profil için iyileştirilmiş NGen görüntüleri görüntüdeki tüm işlevler için geri çağrılar oluşturacaktır. Bununla birlikte, ek yük nedeniyle, profil oluşturucu en iyi duruma getirilmiş NGen görüntülerini yalnızca bir işlevin tam zamanında (JıT) derlenmesi için bu geri çağırmaları kullanmayı amaçladığında istemelidir. Aksi takdirde, profil oluşturucunun işlev bilgilerini toplamak için bir yavaş strateji kullanması gerekir.  
  
 Profil oluşturucular, profili oluşturulmuş bir uygulamanın birden çok iş parçacığının aynı yöntemi eşzamanlı olarak çağıran durumları desteklemelidir. Örneğin, bir çağrı iş parçacığı `JITCachedFunctionSearchStarted` ve profil oluşturucu, JIT derlemesini zorlamak Için *pbUseCachedFunction*değerini false olarak ayarlayarak yanıt verir. Sonra bir A iş parçacığı [ICorProfilerCallback:: JCOR, Started](icorprofilercallback-jitcompilationstarted-method.md) ve [ICorProfilerCallback:: JCOR, finished işlemini](icorprofilercallback-jitcompilationfinished-method.md)çağırır.  
  
 Şimdi aynı işlevi için iş parçacığı B çağrıları `JITCachedFunctionSearchStarted` . Profil Oluşturucu, işlevi JıT-Derle öğesine belirtse de, profil oluşturucu ikinci geri aramayı alır çünkü bu, {1} iş parçacığı, ' A iş parçacığı A 'nın çağrısına yanıt vermeden önce geri çağırma işlemini gönderir `JITCachedFunctionSearchStarted` . İş parçacıklarının çağrı yaptığı sıra, iş parçacıklarının nasıl zamanlandığına bağlıdır.  
  
 Profil Oluşturucu yinelenen geri çağrılar aldığında, başvurulan değeri `pbUseCachedFunction` tüm yinelenen geri çağırmalar için aynı değere ayarlaması gerekir. Diğer bir deyişle, `JITCachedFunctionSearchStarted` aynı değer ile birden çok kez çağrıldığında `functionId` , profil oluşturucunun her seferinde aynı yanıt vermesi gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
