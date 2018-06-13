---
title: ICorProfilerInfo4::RequestReJIT Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestReJIT
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be7184e07815ebe222b8ff8736c26fd3879c8777
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460714"
---
# <a name="icorprofilerinfo4requestrejit-method"></a>ICorProfilerInfo4::RequestReJIT Yöntemi
JIT derleme belirtilen işlevler tüm örneklerinin ister.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cFunctions`  
 [in] Yeniden derleyin işlevleri sayısı.  
  
 `moduleIds`  
 [in] Belirtir `moduleId` kısmı (`module`, `methodDef`) derlenmesi için işlevleri tanımlamak çiftleri.  
  
 `methodIds`  
 [in] Belirtir `methodId` kısmı (`module`, `methodDef`) derlenmesi için işlevleri tanımlamak çiftleri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|JIT derleme için tüm yöntemlerini işaretlemek için girişimde bulunuldu. Profil Oluşturucu uygulamalıdır [Icorprofilercallback4::rejıterror](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) hangi yöntemlerin JIT yeniden derlenmek üzere başarıyla işaretlenen belirlemek amacıyla yöntemi.|  
|CORPROF_E_CALLBACK4_REQUIRED|Profil Oluşturucu uygulamalıdır [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) desteklenmesi için bu çağrı için arabirim.|  
|CORPROF_E_REJIT_NOT_ENABLED|JIT derleme etkin değil. JIT derleme başlatma sırasında kullanarak etkinleştirmelisiniz [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) ayarlamak için yöntemin `COR_PRF_ENABLE_REJIT` bayrağı.|  
|E_INVALIDARG|`cFunctions` 0 ' dır veya `moduleIds` veya `methodIds` olan `NULL`.|  
|||  
|E_OUTOFMEMORY|Bellek yetersiz çalıştırdığınız için CLR isteği tamamlayamıyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çağrı `RequestReJIT` belirtilen sayıda işlevi yeniden derleyin çalışma zamanı için. Kod profil oluşturucu sonra kullanabileceğiniz [Icorprofilerfunctioncontrol](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) işlevleri derlenir olduğunda oluşturulan kodu ayarlamak için arabirim. Bu, şu anda yürütülen İşlevler, yalnızca gelecekteki işlev çağrılarını etkilemez. Belirtilen işlevler birini daha önce yapılmışsa JIT yeniden derlenmesi, bir derleme isteyen dönüştürülüyor ve işlevi yeniden derlenmesi için eşdeğerdir. JIT Derleyici bir işlev özgün sürümü derlediğinde reversibility, korumak için yalnızca özgün sürümleri satır içi kullanım kararları için kendi callees dikkate alır. JIT derleme işlevi yeniden derler, geçerli sürümleri (derlenmiş veya özgün) için kendi callees dikkate satır içi kullanım.  
  
 Bir profil oluşturucu genellikle çağırır `RequestReJIT` profil oluşturucuyu bir veya daha fazla yöntemleri izleme isteyen kullanıcı girişine yanıt. `RequestReJIT` genellikle kendi iş bazıları yapın ve potansiyel olarak tetikleyici çöp toplama olabilir için çalışma zamanı askıya alır. Bu nedenle, profil oluşturucu çağırmalıdır `RequestReJIT` bir iş parçacığından, daha önce oluşturduğunuz ve bir CLR oluşturulan iş parçacığından, şu anda bir profil oluşturucu geri yürütülmüyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
