---
title: COR_PRF_REJIT_FLAGS Sabit Listesi
ms.date: 08/06/2019
api_name:
- COR_PRF_REJIT_FLAGS Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_REJIT_FLAGS
helpviewer_keywords:
- COR_PRF_REJIT_FLAGS enumeration [.NET Framework profiling]
topic_type:
- apiref
author: davmason
ms.author: davmason
ms.openlocfilehash: 8fc5f1a488826d8adc6aecb8ef122609bebbe813
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177095"
---
# <a name="cor_prf_rejit_flags-enumeration"></a>COR_PRF_REJIT_FLAGS Sabit Listesi
[ICorProfilerInfo10::RequestReJITWithLiners](icorprofilerinfo10-requestrejitwithinliners-method.md) API'nin nasıl olması gerektiğini gösteren değerler içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum  
{
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| ReJITted yöntemleri diğer yöntemlerde inlined olması engellenir. |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| Yeniden `GetFunctionParameters` canlandırılmak istenen yöntemlerin satır satırını gösteren yöntemler için geri arama alın. |  

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri.](../../../core/install/dependencies.md?pivots=os-windows)  
  
 **Üstbilgi:** CorProf.idl, CorProf.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Sabit Listeleri](profiling-enumerations.md)
