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
ms.openlocfilehash: b85a7893cf5271c65bc842bb6ea598c825225376
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495729"
---
# <a name="icorprofilerinfo4requestrevert-method"></a>ICorProfilerInfo4::RequestRevert Yöntemi
Belirtilen işlevlerin tüm örneklerini orijinal sürümlerine geri döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Geri `moduleId` `module` `methodDef` döndürülecek işlevleri tanımlayan (,) çiftlerinin bölümünü belirtir.  
  
 `methodIds`  
 'ndaki Geri `methodId` `module` `methodDef` döndürülecek işlevleri tanımlayan (,) çiftlerinin bölümünü belirtir.  
  
 `status`  
 dışı Bu konunun ilerleyen kısımlarında "durum HRESULTs" bölümünde listelenen HRESULTs dizisi. Her HRESULT, paralel dizilerde belirtilen her bir işlevi döndürmeye çalışırken başarılı veya başarısız olduğunu gösterir `moduleIds` `methodIds` .  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Tüm istekleri dönüştürmek için bir girişimde bulunuldu; Ancak, döndürülen durum dizisinin hangi işlevlerin başarıyla geri döndürüldüğünü belirleyebilmek için denetlenmesi gerekir.|  
|CORPROF_E_CALLBACK4_REQUIRED|Bu çağrının desteklenmesi için profil oluşturucunun [ICorProfilerCallback4](icorprofilercallback4-interface.md) arabirimini uygulaması gerekir.|  
|CORPROF_E_REJIT_NOT_ENABLED|JıT yeniden derleme etkinleştirilmemiş. Bayrağı ayarlamak için [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemini kullanarak başlatma sırasında JIT yeniden derlemeyi etkinleştirmelisiniz `COR_PRF_ENABLE_REJIT` .|  
|E_INVALIDARG|`cFunctions`0 veya veya ' `moduleIds` dir `methodIds` `NULL` .|  
|E_OUTOFMEMORY|CLR belleği tükendiğinden isteği tamamlayamadı.|  
  
## <a name="status-hresults"></a>Durum HRESULTS  
  
|Durum dizisi HRESULT|Description|  
|--------------------------|-----------------|  
|S_OK|Karşılık gelen işlev başarıyla geri döndürüldü.|  
|E_INVALIDARG|`moduleID`Or `methodDef` parametresi `NULL` .|  
|CORPROF_E_DATAINCOMPLETE|Modül henüz tam olarak yüklenmedi veya kaldırılıyor sürecinde.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Belirtilen modül dinamik olarak üretildi (örneğin, `Reflection.Emit` ). Bu nedenle, bu yöntem tarafından desteklenmez.|  
|CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND|Karşılık gelen bir etkin yeniden derleme isteği bulunamadığı için CLR belirtilen işlevi döndüremedi. Yeniden derleme işlemi hiç istenmedi ya da işlev zaten geri döndürüldü.|  
|Diğer|İşletim sistemi, CLR denetimi dışında bir hata döndürdü. Örneğin, bir bellek sayfasının erişim korumasını değiştirmek için bir sistem çağrısı başarısız olursa, işletim sistemi hatası görüntülenir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yeniden çağrılan işlev örneklerinin bir sonraki saatinde, işlevlerin özgün sürümleri çalıştırılır. Bir işlev zaten çalışıyorsa, çalıştıran sürümü yürütmeyi tamamlayacaktır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo4 Arabirimi](icorprofilerinfo4-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
