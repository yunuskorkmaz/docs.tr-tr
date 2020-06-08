---
title: ICorProfilerCallback6::GetAssemblyReferences Yöntemi
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
ms.openlocfilehash: 5deacbff740ebb1dcc8cb8d1fb7e4eb0d4bdcc30
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499226"
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a>ICorProfilerCallback6::GetAssemblyReferences Yöntemi
[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Profil oluşturucuyu bir derlemenin çok erken yükleme aşamasında olduğunu, ortak dil çalışma zamanı bir derleme başvurusu kapatma ilerlemesi gerçekleştirdiğinde bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `wszAssemblyPath`  
 'ndaki Meta verileri değiştirilecek olan derlemenin yolu ve adı.  
  
 `pAsmRefProvider`  
 'ndaki Eklenecek derleme başvurularını belirten [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) arabiriminin adresine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu geri aramadan döndürülen değerler yok sayılır.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu geri çağırma, [ICorProfilerCallback5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) yöntemi çağrılırken [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](cor-prf-high-monitor-enumeration.md) Event Mask bayrağı ayarlanarak denetlenir. Profil Oluşturucu [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri çağırma metoduna kaydolduktan sonra, çalışma zamanı yüklenecek derlemenin yolunu ve adını, bu yönteme bir [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) arabirim nesnesine yönelik bir işaretçi ile geçirir. Profil Oluşturucu daha sonra [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metodunu, `COR_PRF_ASSEMBLY_REFERENCE_INFO` `GetAssemblyReferences` geri çağırmada belirtilen derlemeden başvuruyu planlıyor olan her hedef derleme için bir nesneyle çağırabilir.  
  
 `GetAssemblyReferences`Geri çağırma işlemini yalnızca profil oluşturucunun derleme başvurularını eklemek için bir derlemenin meta verilerini değiştirmesi gerekiyorsa kullanın. (Ancak, bir derlemenin meta verisinin gerçek değişiminin [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)geri çağırma yönteminde yapıldığını unutmayın.) Profil Oluşturucu, `GetAssemblyReferences` Modül yüklendiğinde derleme başvurularının ekleneceği ortak dil çalışma zamanını (CLR) bilgilendirmek için geri çağırma yöntemini uygulamalıdır.  Bu, bu erken aşamada CLR tarafından yapılan derleme paylaşımı kararlarının, daha sonra meta veri derleme başvurularını değiştirme planları olmasına rağmen geçerli olmaya devam etmesine yardımcı olur.  Bu, Profil Oluşturucu meta verileri değişikliklerinin hataya neden olduğu bazı örneklerden kaçınabilir `SECURITY_E_INCOMPATIBLE_SHARE` .  
  
 Profil Oluşturucu, CLR derleme başvuru kapanışı denetçisi 'ne derleme başvuruları eklemek için bu yöntem tarafından sunulan [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) nesnesini kullanır.  [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) nesnesi yalnızca bu geri çağırma içinden kullanılmalıdır. Bu geri aramadan [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metoduna yapılan çağrılar, değiştirilen meta veriler ile sonuçlanmaz, ancak yalnızca değiştirilmiş bir derleme başvurusu kapatma ilerinde. Profil oluşturucunun, geri çağırma işlemini uyguladığından bile, başvurulan derleme için [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağrısının içinden derleme başvurularını açıkça eklemesi Için bir [IMetaDataAssemblyEmit](../metadata/imetadataassemblyemit-interface.md) nesnesi kullanması gerekecektir `GetAssemblyReferences` .  
  
 Profil Oluşturucu aynı derleme için bu geri çağrıya yinelenen çağrılar alacak şekilde hazırlanmalı ve her bir yinelenen çağrı için aynı şekilde yanıt vermelidir (aynı [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) çağrılarının kümesini yaparak).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback6 Arabirimi](icorprofilercallback6-interface.md)
- [ModuleLoadFinished Yöntemi](icorprofilercallback-moduleloadfinished-method.md)
- [COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı](cor-prf-assembly-reference-info-structure.md)
- [ICorProfilerAssemblyReferenceProvider Arabirimi](icorprofilerassemblyreferenceprovider-interface.md)
