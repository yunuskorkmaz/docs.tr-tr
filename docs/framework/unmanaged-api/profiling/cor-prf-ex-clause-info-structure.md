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
ms.openlocfilehash: 5c764031f709eefe61022d0662f37bc5d3f3e281
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501007"
---
# <a name="cor_prf_ex_clause_info-structure"></a>COR_PRF_EX_CLAUSE_INFO Yapısı
Belirli bir özel durum yan tümcesi ve onunla ilişkili çerçevesini hakkında bilgi depolar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`clauseType`|Yeni girilen veya soldaki kodun özel durum yan tümcesinin türünü belirten [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) numaralandırması değeri.|  
|`programCounter`|Yan tümce işleyicisinin yerel giriş noktası — Örneğin, x86 EıP kaydının içeriği.|  
|`framePointer`|Yan tümce işleyicisi için mantıksal çerçeveye yönelik işaretçi — Örneğin, x86 EBP kaydının içeriği.|  
|`shadowStackPointer`|Gölge yığınının işaretçisi. Bu değer BSP yazmacın içerikleri ve yalnızca ıA64 için geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir özel durum bildirimi alındığında, çalıştırılmak üzere veya yalnızca çalıştırılmış olan özel durum yan tümcesinin (/Filter) yerel adres ve çerçeve bilgilerini almak için [ICorProfilerInfo2:: GetNotifiedExceptionClauseInfo](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) kullanılabilir `catch` / `finally` .  
  
 Özel durum yan tümcesinin yürütülmesi, ortak dil çalışma zamanından (CLR) bu geri çağırmaları içerir:  
  
- [ICorProfilerCallback:: ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [ICorProfilerCallback:: Exceptionunwınbir Finallyenter](icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [ICorProfilerCallback:: ExceptionSearchFilterEnter](icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [ICorProfilerCallback:: Exceptioncatch Erleave](icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [ICorProfilerCallback:: Exceptionunwınbir Finallyleave](icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [ICorProfilerCallback:: ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Yapıları](profiling-structures.md)
