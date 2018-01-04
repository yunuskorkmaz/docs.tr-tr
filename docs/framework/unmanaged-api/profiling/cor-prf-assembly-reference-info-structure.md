---
title: "COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b5889f8e0b0dc8faab76f637e2fcf03853709bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corprfassemblyreferenceinfo-structure"></a>COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Ortak dil çalışma zamanı bir derleme başvurusu kapatma ilerlemesi gerçekleştirirken düşünmelisiniz bir derleme başvurusu hakkında bilgi sağlar.  
  
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
|`pbPublicKeyOrToken`|Ortak anahtar veya derlemenin belirteci için bir işaretçi.|  
|`cbPublicKeyOrToken`|Ortak anahtar belirteci de bayt sayısı.|  
|`szName`|Başvurulan derleme adı.|  
|`pMetaData`|Derlemenin meta verilerini gösteren bir işaretçi.|  
|`pbHashValue`|Karma ikili büyük nesne (BLOB) için bir işaretçi.|  
|`cbHashValue`|BLOB karma bayt sayısı.|  
|`dwAssemblyRefFlags`|Derlemenin bayraklar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_PRF_EX_CLAUSE_INFO` Yapısı ortak dil çalışma zamanı, bir derleme başvurusu kapatma ilerlemesi gerçekleştirirken dikkate almanız gereken ek derleme başvuruları bildirir, Profil Oluşturucu tarafından doldurulur.  
  
 Profil Oluşturucu için kaydettiğinde [Icorprofilercallback6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri çağırma yöntemi, çalışma zamanı geçirir, bir işaretçi birlikte yüklenecek derlemenin adını ve yolunu bir [ Icorprofilerassemblyreferenceprovider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) bu yönteme arabirimi nesnesi. Profil Oluşturucu sonra çağırabilirsiniz [Icorprofilerassemblyreferenceprovider::addassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) yöntemi ile bir `COR_PRF_ASSEMBLY_REFERENCE_INFO` nesne planları belirtilen derlemesinden başvurmak için her hedef derleme için [ Icorprofilercallback6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri çağırma.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil Oluşturma Yapıları](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)  
 [GetAssemblyReferences Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)  
 [AddAssemblyReference Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
