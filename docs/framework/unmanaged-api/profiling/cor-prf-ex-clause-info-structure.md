---
title: COR_PRF_EX_CLAUSE_INFO Yapısı
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6576dc19ed092ca12846a9780236e041daa64956
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727137"
---
# <a name="corprfexclauseinfo-structure"></a>COR_PRF_EX_CLAUSE_INFO Yapısı
Bir özel durum yan tümcesi örneği ve ilişkili çerçevesini hakkındaki bilgileri saklar.  
  
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
|`clauseType`|Değerini [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) özel durum yan tümcesi yalnızca girilen kod veya sol türünü belirten sabit listesi.|  
|`programCounter`|Yerel giriş noktası yan tümcesi işleyicisinin — Örneğin, X86 EIP kaydının içeriğini.|  
|`framePointer`|Yan tümcesi işleyicisi için mantıksal çerçeve işaretçisi — Örneğin, X86 EBP kaydının içeriğini.|  
|`shadowStackPointer`|Gölge yığın işaretçisi. Bu değer BSP kaydının içeriğini ve yalnızca IA64 için geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir özel durum bildirimi alındığında [Icorprofilerınfo2::getnotifiedexceptionclauseınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) özel durum yan tümcesinin yerel adres ve çerçeve bilgilerini almak için kullanılabilir (`catch` / `finally`/filtreleme) hakkında çalıştırılacak veya yalnızca çalıştırın.  
  
 Bu geri aramalarda ortak dil çalışma zamanının (CLR) yürütme bir özel durum yan tümcesinin içerir:  
  
-   [Icorprofilercallback::exceptioncatcherenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
-   [Icorprofilercallback::exceptionunwindfinallyenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
-   [Icorprofilercallback::exceptionsearchfilterenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
-   [Icorprofilercallback::exceptioncatcherleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
-   [Icorprofilercallback::exceptionunwindfinallyleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
-   [Icorprofilercallback::exceptionsearchfilterleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Profil Oluşturma Yapıları](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
