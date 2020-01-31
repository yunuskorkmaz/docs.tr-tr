---
title: COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: 4fdc8e1074bf45de3a8ab85500a85b124ce34fa1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867340"
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
  
|Üye|Açıklama|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|Derleme için ortak anahtar veya belirtece yönelik bir işaretçi.|  
|`cbPublicKeyOrToken`|Ortak anahtar veya belirteçteki bayt sayısı.|  
|`szName`|Başvurulan derlemenin adı.|  
|`pMetaData`|Derlemenin meta verilerine yönelik bir işaretçi.|  
|`pbHashValue`|Karma ikili büyük nesne (BLOB) için bir işaretçi.|  
|`cbHashValue`|Karma BLOBUN içindeki bayt sayısı.|  
|`dwAssemblyRefFlags`|Derlemenin bayrakları.|  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_PRF_EX_CLAUSE_INFO` yapısı, ortak dil çalışma zamanının bir derleme başvuru kapanışı yürüirken dikkate alınması gereken ek derleme başvurularını bildirdiği zaman profil oluşturucu tarafından doldurulur.  
  
 Profil Oluşturucu [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri çağırma metoduna kaydolduktan sonra, çalışma zamanı yüklenecek derlemenin yolunu ve adını, bu yönteme bir [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) arabirim nesnesine yönelik bir işaretçi ile geçirir. Profil Oluşturucu daha sonra [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) yöntemini, [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri aramasında belirtilen derlemeden başvuruyu planlıyor olan her bir hedef derleme için bir `COR_PRF_ASSEMBLY_REFERENCE_INFO` nesnesi ile çağırabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Yapıları](profiling-structures.md)
- [GetAssemblyReferences Yöntemi](icorprofilercallback6-getassemblyreferences-method.md)
- [AddAssemblyReference Yöntemi](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
