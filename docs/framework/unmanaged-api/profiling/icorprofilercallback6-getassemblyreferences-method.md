---
title: ICorProfilerCallback6::GetAssemblyReferences Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerCallback6.GetAssemblyReferences
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: 8b391afb-d79f-41bd-94ce-43ce62c6b5fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3b63756fd300dc300932d070e451d2d072adc6e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621421"
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a>ICorProfilerCallback6::GetAssemblyReferences Metodu
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Profil Oluşturucu, ortak dil çalışma zamanı bir bütünleştirilmiş kod başvurusu kapanış Yürüme gerçekleştirirken bir derleme bir çok erken aşama, yükleniyor olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `wszAssemblyPath`  
 [in] Olan meta veri değiştirilecek derlemenin adı ve yolu.  
  
 `pAsmRefProvider`  
 [in] Adresine bir işaretçi bir [Icorprofilerassemblyreferenceprovider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) derlemeyi belirtir arabirimi başvuruları ekleyin.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu geri arama dönüş değerleri yok sayılır.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu geri çağırma ayarlanmasıyla denetlenir [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) çağırırken olay maskesini bayrağı [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemi. Profil Oluşturucu kayıtlıysa [Icorprofilercallback6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri çağırma yöntemi, çalışma zamanı geçirir, bir işaretçi ile birlikte yüklenecek derlemenin adı ve yolunu bir [ Icorprofilerassemblyreferenceprovider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) bu yönteme arabirimi nesnesi. Profil Oluşturucu ardından çağırabilirsiniz [Icorprofilerassemblyreferenceprovider::addassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) yöntemi ile bir `COR_PRF_ASSEMBLY_REFERENCE_INFO` her hedef derleme planları içinde belirtilen derleme başvuru yapmak için nesne `GetAssemblyReferences` geri çağırma.  
  
 Kullanım `GetAssemblyReferences` yalnızca derleme başvuruları eklemek için bir derlemenin meta verilerini değiştirmek profil oluşturucu sahipse, geri çağırma. (Ancak gerçek bir derlemenin meta verilerini değiştirilmesini yapılır Not [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)geri çağırma yöntemi.) Profil Oluşturucu uygulamalıdır `GetAssemblyReferences` modül yüklendiğinde derleme başvurularını eklenecek ortak dil çalışma zamanı (CLR) bildirmek için geri çağırma yöntemi.  Bu meta veri bütünleştirilmiş kod başvuruları daha sonra değiştirmek profil oluşturucu planları olsa da, bu erken bir aşamasında CLR tarafından alınan derleme paylaşım kararları geçerli kaldığından emin olun yardımcı olur.  Bu meta veri değişiklikleri hangi Profil Oluşturucusu'nda neden bazı örnekleri kaçınabilirsiniz bir `SECURITY_E_INCOMPATIBLE_SHARE` hata.  
  
 Profil Oluşturucu kullanan [Icorprofilerassemblyreferenceprovider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) CLR bütünleştirilmiş kod başvurusu kapanış walker bütünleştirilmiş kod başvuruları eklemek için bu yöntem tarafından sağlanan nesne.  [Icorprofilerassemblyreferenceprovider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) nesne kullanılmalıdır yalnızca içinde bu geri çağırma. Çağrılar [Icorprofilerassemblyreferenceprovider::addassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) bu geri çağırma yöntemi yok değiştirilmiş meta verilerde, ancak yalnızca değiştirilen derleme başvurusu kapanış Yürüme neden. Profil Oluşturucu hala kullanması gerekir bir [Imetadataassemblyemit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) açıkça içinde derleme başvuruları eklemek için nesne [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) başvuru için geri çağırma derleme, onu uygulayan olsa bile `GetAssemblyReferences` geri çağırma.  
  
 Profil Oluşturucu aynı derleme için bu geri çağırma yinelenen çağrıları almak hazırlıklı olmalıdır ve her tür yinelenen çağrısı için aynı şekilde yanıt vermesi gerekir (aynı yaparak [Icorprofilerassemblyreferenceprovider:: AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) çağırır).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerCallback6 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)
- [ModuleLoadFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
- [ICorProfilerAssemblyReferenceProvider Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
