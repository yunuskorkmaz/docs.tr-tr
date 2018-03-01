---
title: "COR_PRF_EX_CLAUSE_INFO Yapısı"
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
- COR_PRF_EX_CLAUSE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_EX_CLAUSE_INFO
helpviewer_keywords:
- COR_PRF_EX_CLAUSE_INFO structure [.NET Framework profiling]
ms.assetid: 7d0d6fb7-bc9d-40f0-8163-c0d162eaba7d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 65025384aa94ac363336bae7f37f8ea88a3bab67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corprfexclauseinfo-structure"></a>COR_PRF_EX_CLAUSE_INFO Yapısı
Bir özel durum yan tümcesi örneği ve ilişkili çerçevesini ilgili bilgileri depolar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`clauseType`|Değerini [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) numaralandırma özel durum yan tümcesi yalnızca girilen kod veya sol türünü belirtir.|  
|`programCounter`|Yerel giriş noktası yan tümcesi işleyicisinin — Örneğin, X86 EIP kayıt içeriği.|  
|`framePointer`|Yan tümcesi işleyici mantıksal çerçeve işaretçisi — Örneğin, X86 EBP kayıt içeriği.|  
|`shadowStackPointer`|Gölge yığınına işaretçi. Bu değer BSP kayıt, içeriği ve yalnızca IA64 için geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir özel durum bildirimi alındığında [Icorprofilerınfo2::getnotifiedexceptionclauseınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) özel durum yan tümcesinin yerel adres ve çerçeve bilgilerini almak için kullanılan (`catch` / `finally`/filtre) hakkında çalıştırılacak veya yalnızca çalıştırın.  
  
 Özel durum yan tümcesinin yürütme bu geri aramalar ortak dil çalışma zamanı (CLR) gelen içerir:  
  
-   [Icorprofilercallback::exceptioncatcherenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
-   [Icorprofilercallback::exceptionunwindfinallyenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
-   [Icorprofilercallback::exceptionsearchfilterenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
-   [Icorprofilercallback::exceptioncatcherleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
-   [Icorprofilercallback::exceptionunwindfinallyleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
-   [Icorprofilercallback::exceptionsearchfilterleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil Oluşturma Yapıları](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
