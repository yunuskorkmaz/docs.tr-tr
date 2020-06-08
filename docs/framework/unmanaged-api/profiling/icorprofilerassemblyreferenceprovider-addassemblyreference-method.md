---
title: ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type:
- apiref
ms.openlocfilehash: 6d732c6c2871cc5e042b8504db26aabb19963f8c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500513"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a>ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Yöntemi
[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Profiler planlarının [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağırması içine eklemesi için bir derleme başvurusunun ortak dil çalışma zamanına (CLR) bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a>Parametreler

- `pAssemblyRefInfo`

  Bir derleme başvurusu kapatma ilerlemesi gerçekleştirirken göz önünde bulundurmanız gereken bir derleme başvurusu hakkındaki bilgilerle CLR sağlayan [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) yapısına yönelik bir işaretçi.
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu, `wszAssemblyPath` [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri çağrısının bağımsız değişkeninde belirtilen derlemeden başvuruyu planlıyor olan her bir hedef derleme için bu yöntemi çağırır. [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) arabirim nesnesi, bağımsız değişkende derleme yolu ve adı ile birlikte Profiler 'ın [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri aramaya geçirilir `wszAssemblyPath` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerAssemblyReferenceProvider Arabirimi](icorprofilerassemblyreferenceprovider-interface.md)
- [GetAssemblyReferences Yöntemi](icorprofilercallback6-getassemblyreferences-method.md)
- [ModuleLoadFinished Yöntemi](icorprofilercallback-moduleloadfinished-method.md)
