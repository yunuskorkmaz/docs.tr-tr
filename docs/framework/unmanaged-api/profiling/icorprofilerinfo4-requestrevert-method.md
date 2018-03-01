---
title: "ICorProfilerInfo4::RequestRevert Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo4.RequestRevert
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8f0bf926bc6ba458745231bc17ce20dbe5cdbd1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4requestrevert-method"></a>ICorProfilerInfo4::RequestRevert Yöntemi
Özgün sürümlerine belirtilen işleve tüm örneklerini döner.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cFunctions`  
 [in] Geri dönmek için işlevleri sayısı.  
  
 `moduleIds`  
 [in] Belirtir `moduleId` kısmı (`module`, `methodDef`) döndürülmesi için işlevleri tanımlamak çiftleri.  
  
 `methodIds`  
 [in] Belirtir `methodId` kısmı (`module`, `methodDef`) döndürülmesi için işlevleri tanımlamak çiftleri.  
  
 `status`  
 [out] Bu konunun devamındaki "Durum HRESULTs" bölümünde listelenen HRESULTs dizisi. Her HRESULT başarı veya başarısızlık paralel dizilerde belirtilen her işlevi geri çalışılırken durumunu gösteren `moduleIds` ve `methodIds`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Tüm istekleri dönmek için girişimde bulunuldu; Ancak, döndürülen durum dizi hangi işlevleri başarıyla geri belirlemek için denetlenmesi gerekir.|  
|CORPROF_E_CALLBACK4_REQUIRED|Profil Oluşturucu uygulamalıdır [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) desteklenmesi için bu çağrı için arabirim.|  
|CORPROF_E_REJIT_NOT_ENABLED|JIT derleme etkin değil. JIT derleme başlatma sırasında kullanarak etkinleştirmelisiniz [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) ayarlamak için yöntemin `COR_PRF_ENABLE_REJIT` bayrağı.|  
|E_INVALIDARG|`cFunctions`0 ' dır veya `moduleIds` veya `methodIds` olan `NULL`.|  
|E_OUTOFMEMORY|Bellek yetersiz çalıştırdığınız için CLR isteği tamamlayamıyor.|  
  
## <a name="status-hresults"></a>Durum HRESULTS  
  
|Durum dizi HRESULT|Açıklama|  
|--------------------------|-----------------|  
|S_OK|Karşılık gelen işlevi başarıyla geri döndürüldü.|  
|E_INVALIDARG|`moduleID` Veya `methodDef` parametresi `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|Modül henüz tam olarak yüklü değil veya kaldırıldığında sürecinde olduğundan.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Belirtilen modül dinamik olarak oluşturulan (örneğin `Reflection.Emit`). Bu nedenle, bu yöntem tarafından desteklenmiyor.|  
|CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND|Karşılık gelen bir etkin yeniden derlenmek isteği bulunamadığından CLR belirtilen işlev geri döndürülemedi. Yeniden derleme hiçbir zaman istendi ya da işlevi zaten geri döndürüldü.|  
|Diğer|İşletim sistemi CLR denetimi dışında kalan bir hata döndürdü. Örneğin, belleğin bir sayfası erişim korumasını değiştirmek için bir sistem çağrısı başarısız olursa, işletim sistemi hatası görüntülenir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Herhangi revereted işlevi örnekleri olarak da bilinen sonraki saat işlevleri özgün sürümlerinde çalışır. Bir işlev zaten çalışıyorsa, çalışmakta olan sürümü yürütme tamamlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
