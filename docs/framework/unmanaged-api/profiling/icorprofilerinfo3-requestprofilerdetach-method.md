---
title: "ICorProfilerInfo3::RequestProfilerDetach Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.RequestProfilerDetach Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::RequestProfilerDetach
helpviewer_keywords:
- RequestProfilerDetach method [.NET Framework profiling]
- ICorProfilerInfo3::RequestProfilerDetach method [.NET Framework profiling]
ms.assetid: ea102e62-0454-4477-bcf3-126773acd184
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4d155c68f1b7743e0a888c78f6eeecf967c16570
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a>ICorProfilerInfo3::RequestProfilerDetach Yöntemi
Profil Oluşturucu ayırmak için çalışma zamanı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwExpectedCompletionMilliseconds`  
 [in] Milisaniye cinsinden süre ortak dil çalışma zamanı (CLR) profil oluşturucu kaldırmak güvenli olup olmadığını görmek için denetlemeden önce beklemesi gerekir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Ayırma isteği geçerli değil ve ayırma yordamı artık başka bir iş parçacığında devam ediyor. Ayırma tam olarak tamamlandığında, bir `ProfilerDetachSucceeded` olay verildi.|  
|E_ CORPROF_E_CALLBACK3_REQUIRED|Profil Oluşturucu başarısız bir [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) için denemesi [Icorprofilercallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md) ayırma işlemi desteklemek için uygulamalıdır arabirimi. Detach başlatılmamış.|  
|CORPROF_E_IMMUTABLE_FLAGS_SET|Profil Oluşturucu başlangıçta değişmez bayrakları çünkü ayrılmayı mümkün değildir. Ayrılmayı denendi değil; Profil Oluşturucu hala tam olarak eklenir.|  
|CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT|Ayrılmayı Microsoft Ara dili (MSIL) kod kullanılan profil oluşturucu izleme eklenmiş olduğundan imkansız veya eklenen `enter` / `leave` kancaları. Ayrılmayı denendi değil; Profil Oluşturucu hala tam olarak eklenir.<br /><br /> **Not** MSIL izlenmiş olan kodu kullanarak profil oluşturucu tarafından sağlanan kodudur [Setılfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) yöntemi.|  
|CORPROF_E_RUNTIME_UNINITIALIZED|Çalışma zamanı, yönetilen bir uygulamada henüz başlatılmadı. (Diğer bir deyişle, çalışma zamanı tamamen yüklendi değil.) Profil Oluşturucu geri çağırma içinde 's ayrılmayı istendiğinde bu hata kodu döndürülebilir [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) yöntemi.|  
|CORPROF_E_UNSUPPORTED_CALL_SEQUENCE|`RequestProfilerDetach`desteklenmeyen bir zamanda çağrıldı. Yönetilen iş parçacığı üzerinde ancak içinden değil yöntem çağrıldığında bu saptanmışsa bir [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) yöntemi veya içinden bir [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) çöp toplama genişliğinin kullanılmasını yöntemi. Daha fazla bilgi için bkz: [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 Ayırma iş parçacığı (özel profil oluşturucu ayırmak için oluşturulan iş parçacığı) ayırma yordamı sırasında bazen tüm iş parçacıklarının Profil Oluşturucu'nın kod çıkış olup olmadığını denetler. Profil Oluşturucu nasıl bu aracılığıyla sürmesi gerektiğini, tahmini sağlamalıdır `dwExpectedCompletionMilliseconds` parametresi. Tipik profil oluşturucu ayırdığı herhangi bir iç verilen süre miktarını kullanmak için iyi bir değer olan `ICorProfilerCallback*` yöntemi; bu değer, bu profil oluşturucu bekliyor harcadığınız için en uzun süreyi değerinden yarısı olmamalıdır.  
  
 Ayırma iş parçacığı kullanan `dwExpectedCompletionMilliseconds` ne kadar süreyle profil oluşturucu geri çağırma kodu tüm yığınlarını Sil'i olup olmadığını denetlemeden önce uyku moduna karar vermek için. Aşağıdaki algoritması ayrıntılarını gelecek sürümlerde CLR değişebilir karşın, bir yolu gösterilmektedir `dwExpectedCompletionMilliseconds` profil oluşturucu kaldırmak güvenli olduğunda belirlerken kullanılabilir. Ayırma iş parçacığı için önce uyku `dwExpectedCompletionMilliseconds` milisaniye. Uykudan Uyandırma sonra CLR Profil Oluşturucu geri çağırma kodu hala mevcut olduğunu bulursa, Ayır iş parçacığı yeniden, bu kez iki kez uyku moduna geçer `dwExpectedCompletionMilliseconds` milisaniye. Bu ikinci uykudan Uyandırma sonra ayırma iş parçacığı profil oluşturucu geri çağırma kodu hala mevcut olduğunu bulursa, yeniden denetlemeden önce 10 dakika uykuda bekler. Ayırma iş parçacığı 10 dakikada bir yeniden denetlemek devam eder.  
  
 Profil Oluşturucu belirtiyorsa `dwExpectedCompletionMilliseconds` 0 (sıfır) olarak CLR 10 saniye sonra yeniden 5 saniye sonra bir denetimi gerçekleştirir ve her 10 bundan sonra dakika anlamına gelir 5000, varsayılan değeri kullanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icorprofilerınfo3 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Profil oluşturma arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
