---
title: ICorProfilerInfo4::RequestRevert Yöntemi
ms.date: 03/30/2017
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
ms.openlocfilehash: c7ced05692e3030bace10dab9a6793a29fac6c26
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444831"
---
# <a name="icorprofilerinfo4requestrevert-method"></a>ICorProfilerInfo4::RequestRevert Yöntemi
Belirtilen işlevlerin tüm örneklerini orijinal sürümlerine geri döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cFunctions`  
 'ndaki Döndürülecek işlev sayısı.  
  
 `moduleIds`  
 'ndaki Geri döndürülecek işlevleri tanımlayan (`module`, `methodDef`) çiftlerinin `moduleId` bölümünü belirtir.  
  
 `methodIds`  
 'ndaki Geri döndürülecek işlevleri tanımlayan (`module`, `methodDef`) çiftlerinin `methodId` bölümünü belirtir.  
  
 `status`  
 dışı Bu konunun ilerleyen kısımlarında "durum HRESULTs" bölümünde listelenen HRESULTs dizisi. Her HRESULT, paralel diziler `moduleIds` ve `methodIds`belirtilen her bir işlevi döndürmeye çalışırken başarılı veya başarısız olduğunu gösterir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Tüm istekleri dönüştürmek için bir girişimde bulunuldu; Ancak, döndürülen durum dizisinin hangi işlevlerin başarıyla geri döndürüldüğünü belirleyebilmek için denetlenmesi gerekir.|  
|CORPROF_E_CALLBACK4_REQUIRED|Bu çağrının desteklenmesi için profil oluşturucunun [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) arabirimini uygulaması gerekir.|  
|CORPROF_E_REJIT_NOT_ENABLED|JıT yeniden derleme etkinleştirilmemiş. `COR_PRF_ENABLE_REJIT` bayrağını ayarlamak için [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yöntemini kullanarak başlatma sırasında JIT yeniden derlemeyi etkinleştirmeniz gerekir.|  
|E_INVALIDARG|`cFunctions` 0 ' dır veya `moduleIds` veya `methodIds` `NULL`.|  
|E_OUTOFMEMORY|CLR belleği tükendiğinden isteği tamamlayamadı.|  
  
## <a name="status-hresults"></a>Durum HRESULTS  
  
|Durum dizisi HRESULT|Açıklama|  
|--------------------------|-----------------|  
|S_OK|Karşılık gelen işlev başarıyla geri döndürüldü.|  
|E_INVALIDARG|`moduleID` veya `methodDef` parametresi `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|Modül henüz tam olarak yüklenmedi veya kaldırılıyor sürecinde.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Belirtilen modül dinamik olarak üretildi (örneğin, `Reflection.Emit`). Bu nedenle, bu yöntem tarafından desteklenmez.|  
|CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND|Karşılık gelen bir etkin yeniden derleme isteği bulunamadığı için CLR belirtilen işlevi döndüremedi. Yeniden derleme işlemi hiç istenmedi ya da işlev zaten geri döndürüldü.|  
|Diğer|İşletim sistemi, CLR denetimi dışında bir hata döndürdü. Örneğin, bir bellek sayfasının erişim korumasını değiştirmek için bir sistem çağrısı başarısız olursa, işletim sistemi hatası görüntülenir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yeniden çağrılan işlev örneklerinin bir sonraki saatinde, işlevlerin özgün sürümleri çalıştırılır. Bir işlev zaten çalışıyorsa, çalıştıran sürümü yürütmeyi tamamlayacaktır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
