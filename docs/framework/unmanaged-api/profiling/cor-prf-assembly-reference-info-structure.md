---
title: COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: 861b31e5621e9a7b40403d249c6a5c8c4ac25db8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501046"
---
# <a name="cor_prf_assembly_reference_info-structure"></a>COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı
[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Ortak dil çalışma zamanını, bir derleme başvurusu kapatma ilerlemesi gerçekleştirirken göz önünde bulundurmanız gereken bir derleme başvurusu hakkındaki bilgileri sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct _COR_PRF_ASSEMBLY_REFERENCE_INFO {  
    void* pbPublicKeyOrToken;  
    ULONG cbPublicKeyOrToken;  
    LPCWSTR szName;  
    ASSEMBLYMETADATA* pMetaData;  
    void* pbHashValue;  
    ULONG cbHashValue;  
    DWORD dwAssemblyRefFlags;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|Derleme için ortak anahtar veya belirtece yönelik bir işaretçi.|  
|`cbPublicKeyOrToken`|Ortak anahtar veya belirteçteki bayt sayısı.|  
|`szName`|Başvurulan derlemenin adı.|  
|`pMetaData`|Derlemenin meta verilerine yönelik bir işaretçi.|  
|`pbHashValue`|Karma ikili büyük nesne (BLOB) için bir işaretçi.|  
|`cbHashValue`|Karma BLOBUN içindeki bayt sayısı.|  
|`dwAssemblyRefFlags`|Derlemenin bayrakları.|  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_PRF_EX_CLAUSE_INFO`Yapı, bir derleme başvurusu kapatma ilerlemesi gerçekleştirirken ortak dil çalışma zamanının göz önünde bulundurmanız gereken ek derleme başvuruları bildirirken profil oluşturucu tarafından doldurulur.  
  
 Profil Oluşturucu [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri çağırma metoduna kaydolduktan sonra, çalışma zamanı yüklenecek derlemenin yolunu ve adını, bu yönteme bir [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) arabirim nesnesine yönelik bir işaretçi ile geçirir. Profil Oluşturucu daha sonra [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metodunu, `COR_PRF_ASSEMBLY_REFERENCE_INFO` [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri aramasında belirtilen derlemeden başvuruyu planlıyor olan her hedef derleme için bir nesneyle çağırabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Yapıları](profiling-structures.md)
- [GetAssemblyReferences Yöntemi](icorprofilercallback6-getassemblyreferences-method.md)
- [AddAssemblyReference Yöntemi](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
