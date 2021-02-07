---
description: 'Daha fazla bilgi edinin: COR_SEGMENT Yapısı'
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
ms.openlocfilehash: 9bbc452b2c2036d019175ac1be8b9917ffa07b6a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712200"
---
# <a name="cor_segment-structure"></a>COR_SEGMENT Yapısı

Yönetilen yığında bir bellek bölgesi hakkındaki bilgileri içerir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;
    CORDB_ADDRESS end;
    CorDebugGenerationTypes gen;
    ULONG heap;
} COR_SEGMENT;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`start`|Bellek bölgesinin başlangıç adresi.|  
|`end`|Bellek bölgesinin bitiş adresi.|  
|`gen`|Bellek bölgesinin üretimini gösteren [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) sabit listesi üyesi.|  
|`heap`|Bellek bölgesinin bulunduğu yığın numarası. Daha fazla bilgi için Açıklamalar bölümüne bakın.|  
  
## <a name="remarks"></a>Açıklamalar  

 `COR_SEGMENTS`Yapı, yönetilen yığında bir bellek bölgesini temsil eder.  `COR_SEGMENTS`nesneler, [ICorDebugProcess5:: Enumerateheapregion](icordebugprocess5-enumerateheapregions-method.md) yöntemi çağırarak doldurulan [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) koleksiyon nesnesinin üyeleridir.  
  
 `heap`Alan, bildirilen yığına karşılık gelen işlemci numarasıdır. İş istasyonları yalnızca bir atık toplama yığınına sahip olduğundan, iş istasyonu atık toplayıcıları için değeri her zaman sıfırdır. Sunucu çöp toplayıcıları için, değeri yığının eklendiği işlemciye karşılık gelir. Çöp toplayıcısının uygulama ayrıntıları nedeniyle gerçek işlemcilerin olduğu daha fazla veya daha az atık toplama yığınlarının olabileceğini unutmayın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
