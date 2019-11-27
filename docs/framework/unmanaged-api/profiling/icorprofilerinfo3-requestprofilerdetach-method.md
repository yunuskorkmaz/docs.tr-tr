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
ms.openlocfilehash: 3256f6f64e2ee4678b2627eea81e12cb4a02fd1e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449615"
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a>ICorProfilerInfo3::RequestProfilerDetach Yöntemi
Çalışma zamanına profil oluşturucuyu ayırmasını söyler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwExpectedCompletionMilliseconds`  
 'ndaki Ortak dil çalışma zamanının (CLR), profil oluşturucunun kaldırılması için güvenli olup olmadığını denetlemeden önce beklemesi gereken süre (milisaniye cinsinden).  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Ayırma isteği geçerli ve ayırma yordamı artık başka bir iş parçacığında devam ediyor. Ayırma tam olarak tamamlandığında `ProfilerDetachSucceeded` bir olay verilir.|  
|E_ CORPROF_E_CALLBACK3_REQUIRED|Profil Oluşturucu, ayırma işlemini desteklemek için uygulanması gereken [ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md) arabirimi için [IUnknown:: QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) girişimi başarısız oldu. Ayırma denenmedi.|  
|CORPROF_E_IMMUTABLE_FLAGS_SET|Profil Oluşturucu başlangıçta sabit bayraklar ayarlandığı için, kesilmesi olanaksızdır. Kesilmesi denenmedi; Profil Oluşturucu hala tam olarak iliştirildi.|  
|CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT|Profil Oluşturucu, belgelenmiş Microsoft ara dili (MSIL) kodu tarafından kullanılan veya `enter`/`leave` kancaları eklenmiş olduğundan, bu, kesilmesi olanaksızdır. Kesilmesi denenmedi; Profil Oluşturucu hala tam olarak iliştirildi.<br /><br /> **Göz önünde** Belgelenmiş MSIL, [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) yöntemi kullanılarak profil oluşturucu tarafından belirtilen koddur.|  
|CORPROF_E_RUNTIME_UNINITIALIZED|Çalışma zamanı, yönetilen uygulamada henüz başlatılmadı. (Diğer bir deyişle, çalışma zamanı tam olarak yüklenmemiştir.) Bu hata kodu, profil oluşturucu geri çağrısının [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) yöntemi içinde, bir hastame istendiğinde döndürülebilir.|  
|CORPROF_E_UNSUPPORTED_CALL_SEQUENCE|`RequestProfilerDetach` desteklenmeyen bir zamanda çağrıldı. Bu, yöntemi yönetilen bir iş parçacığında çağrılırsa veya bir [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) yöntemi içinden ya da bir atık toplamaya tolerans yamayan [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) yöntemi içinden çağrıldığında oluşur. Daha fazla bilgi için bkz. [HRESULT corprof_e_unsupported_call_sequence](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 Ayırma yordamı sırasında, ayırma iş parçacığı (profil oluşturucuyu ayırmak için özel olarak oluşturulan iş parçacığı) zaman zaman, tüm iş parçacıklarının profil oluşturucunun kodundan çıkılmadığını denetler. Profil Oluşturucu, bunun `dwExpectedCompletionMilliseconds` parametresinden ne kadar süreceğine ilişkin bir tahmin sağlamalıdır. Kullanım için iyi bir değer, profil oluşturucunun verilen `ICorProfilerCallback*` yöntemi içinde harcadığı tipik zamandır; Bu değer, profil oluşturucunun harcamayı beklediği maksimum sürenin yarısından daha az olmamalıdır.  
  
 Ayırma iş parçacığı, profil oluşturucu geri çağırma kodunun tüm yığınların yapılıp yapılmayacağını kontrol etmeden önce ne kadar uyku moduna geçmeye karar vermek için `dwExpectedCompletionMilliseconds` kullanır. Aşağıdaki algoritmanın ayrıntıları CLR 'nin gelecek sürümlerinde değişebilir, ancak `dwExpectedCompletionMilliseconds` profil oluşturucunun kaldırılması ne zaman güvenli olduğunun belirlenmesi sırasında kullanılabilecek bir yolu gösterir. Ayırma iş parçacığı ilk olarak `dwExpectedCompletionMilliseconds` milisaniyelik için uykuya geçer. Uyandırma başlatıldıktan sonra CLR, profil oluşturucu geri çağırma kodunun hala mevcut olduğunu bulur, bu kez iki kez `dwExpectedCompletionMilliseconds` milisaniyelik. Bu ikinci Uykudan uyandırma sonra, ayırma iş parçacığı profil oluşturucu geri çağırma kodunun hala mevcut olduğunu belirlerse, yeniden denetlemeden önce 10 dakika boyunca uykuya geçer. Ayırma iş parçacığı her 10 dakikada bir yeniden denetlemeye devam eder.  
  
 Profil Oluşturucu 0 (sıfır) olarak `dwExpectedCompletionMilliseconds` belirtiyorsa, CLR varsayılan 5000 değerini kullanır. Bu, 5 saniye sonra, 10 saniye sonra yeniden denetim gerçekleştirecek ve sonrasında her 10 dakikada bir kontrol gerçekleştireceği anlamına gelir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
