---
title: COR_SEGMENT Yapısı
ms.date: 03/30/2017
api_name:
- COR_SEGMENT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_SEGMENT
helpviewer_keywords:
- COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55f1c0da651d786dfdcfda6a54ee1b29db35f3d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587745"
---
# <a name="corsegment-structure"></a>COR_SEGMENT Yapısı
Bellek yönetilen yığında bir bölge hakkında bilgi içerir.  
  
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
|`start`|Bellek bölgesini başlangıç adresi.|  
|`end`|Bellek bölgesini bitiş adresi.|  
|`gen`|A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) bellek bölgesini neslini belirten sabit listesi üyesi.|  
|`heap`|Bellek bölgesini bulunduğu yığın sayısı. Daha fazla bilgi için Açıklamalar bölümüne bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_SEGMENTS` Yapıyı yönetilen yığında bellek bölgesini temsil eder.  `COR_SEGMENTS` nesneleri üyeleridir [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) çağırarak doldurulur koleksiyon nesnesine [Icordebugprocess5::enumerateheapregions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) yöntemi.  
  
 `heap` Karşılık gelen bildirilen yığın işlemci sayısı bir alandır. İş istasyonu çöp toplama yığınında yalnızca bir olduğundan iş istasyonu atık toplayıcıları değeri her zaman sıfırdır. Sunucu atık toplayıcıları, yığın bağlı işlemciye değerine karşılık gelir. Olabilir, daha fazla veya daha az çöp toplama yığınlardaki atık toplayıcının uygulama ayrıntılarını nedeniyle gerçek işlemci sayısından unutmayın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
