---
title: "COR_SEGMENT Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_SEGMENT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_SEGMENT
helpviewer_keywords: COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9414aa1c36ba059d9ee1101f6183dc8a669f9e6f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corsegment-structure"></a>COR_SEGMENT Yapısı
Yönetilen yığın bellekte bir bölge hakkında bilgiler içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`start`|Bellek bölge başlangıç adresi.|  
|`end`|Bellek bölge bitiş adresi.|  
|`gen`|A [cordebuggenerationtypes sabit](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) bellek bölge neslini belirten numaralandırma üyesi.|  
|`heap`|Bellek bölge bulunduğu yığın sayısı. Daha fazla bilgi için Açıklamalar bölümüne bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_SEGMENTS` Yapısı Yönetilen yığın bellekte bölgesini temsil eder.  `COR_SEGMENTS`nesneleri üyeleri olan [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) çağırarak doldurulur koleksiyon nesnesi[Icordebugprocess5::enumerateheapregions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) yöntemi.  
  
 `heap` Raporlandığını yığın karşılık gelen işlemci numarası bir alandır. İş istasyonları yalnızca bir atık toplama yığın olduğundan iş istasyonu atık toplayıcıları, değeri sıfır, her zaman olduğu. Sunucu atık toplayıcıları değerini öbek iliştirildiği işlemci karşılık gelir. Olabileceğini daha fazla veya daha az atık toplama yığınlardaki atık toplayıcı uygulama ayrıntılarını nedeniyle gerçek işlemciler çok dikkat edin.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
