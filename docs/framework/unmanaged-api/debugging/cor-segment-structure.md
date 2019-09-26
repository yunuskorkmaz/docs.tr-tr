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
ms.openlocfilehash: aabf3ac4e51280bd847d145e15ad804d514ede2c
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274004"
---
# <a name="cor_segment-structure"></a>COR_SEGMENT Yapısı
Yönetilen yığında bir bellek bölgesi hakkındaki bilgileri içerir.  
  
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
|`start`|Bellek bölgesinin başlangıç adresi.|  
|`end`|Bellek bölgesinin bitiş adresi.|  
|`gen`|Bellek bölgesinin üretimini gösteren [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) sabit listesi üyesi.|  
|`heap`|Bellek bölgesinin bulunduğu yığın numarası. Daha fazla bilgi için Açıklamalar bölümüne bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_SEGMENTS` Yapı, yönetilen yığında bir bellek bölgesini temsil eder.  `COR_SEGMENTS`nesneler, [ICorDebugProcess5:: Enumerateheapregion](icordebugprocess5-enumerateheapregions-method.md) yöntemi çağırarak doldurulan [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) koleksiyon nesnesinin üyeleridir.  
  
 `heap` Alan, bildirilen yığına karşılık gelen işlemci numarasıdır. İş istasyonları yalnızca bir atık toplama yığınına sahip olduğundan, iş istasyonu atık toplayıcıları için değeri her zaman sıfırdır. Sunucu çöp toplayıcıları için, değeri yığının eklendiği işlemciye karşılık gelir. Çöp toplayıcısının uygulama ayrıntıları nedeniyle gerçek işlemcilerin olduğu daha fazla veya daha az atık toplama yığınlarının olabileceğini unutmayın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
