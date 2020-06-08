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
ms.openlocfilehash: 627df3600b920e2fe2250f2fc3da51c852edc774
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496278"
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a>ICorProfilerInfo3::RequestProfilerDetach Yöntemi
Çalışma zamanına profil oluşturucuyu ayırmasını söyler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwExpectedCompletionMilliseconds`  
 'ndaki Ortak dil çalışma zamanının (CLR), profil oluşturucunun kaldırılması için güvenli olup olmadığını denetlemeden önce beklemesi gereken süre (milisaniye cinsinden).  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Ayırma isteği geçerli ve ayırma yordamı artık başka bir iş parçacığında devam ediyor. Ayırma tam olarak tamamlandığında bir `ProfilerDetachSucceeded` olay verilir.|  
|E_CORPROF_E_CALLBACK3_REQUIRED|Profil Oluşturucu, ayırma işlemini desteklemek için uygulanması gereken [ICorProfilerCallback3](icorprofilercallback3-interface.md) arabirimi için [IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) girişimi başarısız oldu. Ayırma denenmedi.|  
|CORPROF_E_IMMUTABLE_FLAGS_SET|Profil Oluşturucu başlangıçta sabit bayraklar ayarlandığı için, kesilmesi olanaksızdır. Kesilmesi denenmedi; Profil Oluşturucu hala tam olarak iliştirildi.|  
|CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT|Profil Oluşturucu, belgelenmiş Microsoft ara dili (MSIL) kodu veya eklenmiş kancalar tarafından kullanıldığından, bu, kesilmesi olanaksızdır `enter` / `leave` . Kesilmesi denenmedi; Profil Oluşturucu hala tam olarak iliştirildi.<br /><br /> **Göz önünde** Belgelenmiş MSIL, [SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) yöntemi kullanılarak profil oluşturucu tarafından belirtilen koddur.|  
|CORPROF_E_RUNTIME_UNINITIALIZED|Çalışma zamanı, yönetilen uygulamada henüz başlatılmadı. (Diğer bir deyişle, çalışma zamanı tam olarak yüklenmemiştir.) Bu hata kodu, profil oluşturucu geri çağrısının [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) yöntemi içinde, bir hastame istendiğinde döndürülebilir.|  
|CORPROF_E_UNSUPPORTED_CALL_SEQUENCE|`RequestProfilerDetach`, desteklenmeyen bir zamanda çağrıldı. Bu, yöntemi yönetilen bir iş parçacığında çağrılırsa veya bir [ICorProfilerCallback](icorprofilercallback-interface.md) yöntemi içinden ya da bir atık toplamaya tolerans yamayan [ICorProfilerCallback](icorprofilercallback-interface.md) yöntemi içinden çağrıldığında oluşur. Daha fazla bilgi için bkz. [HRESULT corprof_e_unsupported_call_sequence](corprof-e-unsupported-call-sequence-hresult.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 Ayırma yordamı sırasında, ayırma iş parçacığı (profil oluşturucuyu ayırmak için özel olarak oluşturulan iş parçacığı) zaman zaman, tüm iş parçacıklarının profil oluşturucunun kodundan çıkılmadığını denetler. Profil Oluşturucu, bu parametrenin ne kadar süreceğine ilişkin bir tahmin sağlamalıdır `dwExpectedCompletionMilliseconds` . Kullanım için iyi bir değer, profil oluşturucunun verilen herhangi bir yöntem içinde harcadığı tipik süredir `ICorProfilerCallback*` . Bu değer, profil oluşturucunun harcamayı beklediği maksimum sürenin yarısından daha az olmamalıdır.  
  
 Ayırma iş parçacığı, `dwExpectedCompletionMilliseconds` Profil Oluşturucu geri çağırma kodunun tüm yığınların yapılıp yapılmayacağını denetlemeden önce ne kadar uyku moduna geçmeye karar vermek için kullanır. Aşağıdaki algoritmanın ayrıntıları CLR 'nin gelecek sürümlerinde değişebilir, ancak `dwExpectedCompletionMilliseconds` profil oluşturucunun kaldırılması ne zaman güvenli olduğunun belirlenmesi sırasında bir yol gösterilir. Ayırma iş parçacığı ilk olarak milisaniye için uykuya geçer `dwExpectedCompletionMilliseconds` . Uyandırma sonrasında, CLR, profil oluşturucu geri çağırma kodunun hala mevcut olduğunu bulur, bu kez bu kez iki kez geçen süreyi ayırın `dwExpectedCompletionMilliseconds` . Bu ikinci Uykudan uyandırma sonra, ayırma iş parçacığı profil oluşturucu geri çağırma kodunun hala mevcut olduğunu belirlerse, yeniden denetlemeden önce 10 dakika boyunca uykuya geçer. Ayırma iş parçacığı her 10 dakikada bir yeniden denetlemeye devam eder.  
  
 Profil Oluşturucu `dwExpectedCompletionMilliseconds` 0 (sıfır) olarak belirtirse, clr varsayılan bir 5000 değeri kullanır. Bu, 5 saniye sonra, 10 saniye sonra ve sonrasında 10 dakikada bir denetim gerçekleştirecek anlamına gelir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo3 Arabirimi](icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
