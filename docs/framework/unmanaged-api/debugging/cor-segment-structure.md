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
ms.openlocfilehash: eef2d75a2c8a3445c7f8666fec5be9e4d089e3cb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740526"
---
# <a name="corsegment-structure"></a>COR_SEGMENT Yapısı
Bellek yönetilen yığında bir bölge hakkında bilgi içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
