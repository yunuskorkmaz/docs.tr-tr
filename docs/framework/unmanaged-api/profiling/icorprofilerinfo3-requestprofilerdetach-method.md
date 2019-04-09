---
title: ICorProfilerInfo3::RequestProfilerDetach Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.RequestProfilerDetach Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::RequestProfilerDetach
helpviewer_keywords:
- RequestProfilerDetach method [.NET Framework profiling]
- ICorProfilerInfo3::RequestProfilerDetach method [.NET Framework profiling]
ms.assetid: ea102e62-0454-4477-bcf3-126773acd184
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b04c0453d9ff8545f79f235e7d73095c55203e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083289"
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a>ICorProfilerInfo3::RequestProfilerDetach Yöntemi
Profil oluşturucuyu ayırmak için çalışma zamanı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwExpectedCompletionMilliseconds`  
 [in] Milisaniye cinsinden süre, ortak dil çalışma zamanı (CLR) profil oluşturucu kaldırmak güvenli olup olmadığını denetlemeden önce beklemeniz gerekir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Ayırma isteğini geçerli olduğundan ve ayırma yordamı artık başka bir iş parçacığında devam etmektedir. Ayırma tam olarak tamamlandığında, bir `ProfilerDetachSucceeded` olay verildiği.|  
|E_ CORPROF_E_CALLBACK3_REQUIRED|Profil Oluşturucu bir [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) için deneme [Icorprofilercallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md) arabirimi ayırma işlemi desteklemek için uygulamanız gerekir. Ayırma başlatılmamış.|  
|CORPROF_E_IMMUTABLE_FLAGS_SET|Profil oluşturucu başlatma sırasında sabit bayrakları ayarlandığından ayrılmayı mümkün değildir. Ayrılmayı denenmedi; Profil Oluşturucu hala tam olarak eklenir.|  
|CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT|Microsoft Ara dil (MSIL) kodu kullanılan profil oluşturucu izleme eklenmiş olduğundan mümkün olmayan ya da eklenen ayrılmayı `enter` / `leave` kancaları. Ayrılmayı denenmedi; Profil Oluşturucu hala tam olarak eklenir.<br /><br /> **Not** MSIL izleme eklenmiş olduğu kodu, kullanarak profil oluşturucu tarafından sağlanan kod [Setılfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) yöntemi.|  
|CORPROF_E_RUNTIME_UNINITIALIZED|Çalışma zamanı, yönetilen bir uygulamada henüz başlatılmadı. (Diğer bir deyişle, çalışma zamanı tam olarak yüklenmemiş.) Bu hata kodu, profil oluşturucu geri çağırma içinde 's ayrılmayı istendiğinde döndürülebilir [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) yöntemi.|  
|CORPROF_E_UNSUPPORTED_CALL_SEQUENCE|`RequestProfilerDetach` desteklenmeyen bir zamanda çağrıldı. Yönetilen iş parçacığı içinden değil ancak yöntemi çağrılırsa, böyle bir [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) yöntemi veya içinden bir [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) çöp toplama genişliğinin kullanılmasını yöntemi. Daha fazla bilgi için [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 Ayırma iş parçacığı (özel profil oluşturucuyu ayırmak için oluşturulan iş parçacığı) ayırma yordamı sırasında zaman zaman tüm iş parçacığı profil oluşturucu kodu çıkılana olup olmadığını denetler. Profil Oluşturucu bu aracılığıyla zamanınızı ne tahmini sağlamalıdır `dwExpectedCompletionMilliseconds` parametresi. Kullanmak iyi bir değer tipik profiler içinde verilen herhangi geçirdiği süreyi belirtir `ICorProfilerCallback*` yöntemi; bu değer, bu profil oluşturucu bekliyor harcayabileceğiniz en uzun süreyi az yarısı olmamalıdır.  
  
 Ayırma iş parçacığı kullanan `dwExpectedCompletionMilliseconds` ne kadar süreyle profil oluşturucu geri çağırma kodunun tüm yığınları devre dışı POP olup olmadığını denetlemeden önce uyku durumuna karar vermek için. Aşağıdaki algoritmadan ayrıntılarını CLR sürümleri gelecekte değişebilir olsa da, yollarından biri gösterilmektedir. `dwExpectedCompletionMilliseconds` belirlerken profil oluşturucu kaldırmaya güvenli olduğunda kullanılabilir. Ayırma iş parçacığı için önce uyku `dwExpectedCompletionMilliseconds` milisaniye. Uykudan Uyandırma sonra CLR Profil Oluşturucu geri çağırma kodunun hala mevcut olduğunu bulursa, ayırma iş parçacığı yeniden, bu kez iki kez uyku `dwExpectedCompletionMilliseconds` milisaniye. Bu ikinci uykudan Uyandırma sonra ayırma iş parçacığı profil oluşturucu geri çağırma kodunun hala mevcut olduğunu bulursa, yeniden denetlemeden önce 10 dakika uykuda bekler. 10 dakikada bir yeniden denetlemek ayırma iş parçacığı devam eder.  
  
 Profil Oluşturucu belirtiyorsa `dwExpectedCompletionMilliseconds` 0 (sıfır) 10 saniye sonra yeniden 5 saniye sonra bir denetim gerçekleştirir ve ardından her 10 bundan sonra dakika anlamına gelir. bir varsayılan değer 5000, CLR kullanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo3 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
