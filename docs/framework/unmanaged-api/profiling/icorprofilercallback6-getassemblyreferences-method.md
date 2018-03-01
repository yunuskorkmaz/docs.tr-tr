---
title: ICorProfilerCallback6::GetAssemblyReferences Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bc2e80d6d8207a869d43beb46cc9448bdd86dfec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a>ICorProfilerCallback6::GetAssemblyReferences Metodu
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Profil Oluşturucu ortak dil çalışma zamanı bir derleme başvurusu kapatma ilerlemesi gerçekleştirdiğinde bütünleştirilmiş bir çok erkenden aşama, yüklüyor olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `wszAssemblyPath`  
 [in] Meta veri değiştirilecek derlemenin adını ve yolunu.  
  
 `pAsmRefProvider`  
 [in] Adresine bir işaretçi bir [Icorprofilerassemblyreferenceprovider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) eklemek için derlemeyi belirtir arabirimi başvuruyor.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu geri dönüş değerleri yoksayılır.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu geri çağırma ayarlanmasıyla denetlenir [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) çağrılırken olay maskesi bayrağı [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemi. Profil Oluşturucu için kaydettiğinde [Icorprofilercallback6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri çağırma yöntemi, çalışma zamanı geçirir, bir işaretçi birlikte yüklenecek derlemenin adını ve yolunu bir [ Icorprofilerassemblyreferenceprovider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) bu yönteme arabirimi nesnesi. Profil Oluşturucu sonra çağırabilirsiniz [Icorprofilerassemblyreferenceprovider::addassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) yöntemi ile bir `COR_PRF_ASSEMBLY_REFERENCE_INFO` nesne planları belirtilen derlemesinden başvurmak için her hedef derleme için `GetAssemblyReferences` geri çağırma.  
  
 Kullanım `GetAssemblyReferences` yalnızca derleme başvurularını eklemek için bir derlemenin meta verilerini değiştirmek profil oluşturucu varsa, geri çağırma. (Ancak gerçek bir derlemenin meta verilerini değiştirilmesini yapılır Not [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)geri çağırma yöntemi.) Profil Oluşturucu uygulamalıdır `GetAssemblyReferences` modülü yüklendiğinde derleme başvurularını eklenecek ortak dil çalışma zamanı (CLR) bilgilendirmek için geri çağırma yöntemi.  Bu meta verileri derleme başvurularını daha sonra değiştirmek profil oluşturucu planları rağmen CLR tarafından bu erken aşamada derleme paylaşım kararlara geçerli kalmasını sağlamaya yardımcı olur.  Bu meta veri değişiklikleri hangi Profil Oluşturucusu'nda neden bazı örnekleri önleyebilirsiniz bir `SECURITY_E_INCOMPATIBLE_SHARE` hata.  
  
 Profil Oluşturucu kullanan [Icorprofilerassemblyreferenceprovider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) CLR derleme başvurusu kapatma walker derleme başvurularını eklemek için bu yöntem tarafından sağlanan nesne.  [Icorprofilerassemblyreferenceprovider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) nesne kullanılmalıdır yalnızca içinde bu geri çağırma. Çağrılar [Icorprofilerassemblyreferenceprovider::addassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) değiştirilmiş meta verilerde, ancak yalnızca değiştirilen derleme başvurusu kapatma ilerlemesi bu geri çağırma yöntemi neden yoktur. Profil Oluşturucu hala kullanmak zorunda olacaksınız bir [Imetadataassemblyemit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) açıkça derleme başvurularını içinden eklemek için nesne [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) başvuru için geri çağırma derleme, bunu uygulayan olsa bile `GetAssemblyReferences` geri çağırma.  
  
 Profil Oluşturucu için aynı bütünleştirilmiş kodda bu geri çağırma yinelenen çağrılarını almak hazırlıklı olmalıdır ve her tür yinelenen çağrısı için aynı kullanmalıdır (aynı dizi yaparak [Icorprofilerassemblyreferenceprovider:: AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) çağrıları).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback6 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 [ModuleLoadFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)  
 [COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)  
 [ICorProfilerAssemblyReferenceProvider Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
