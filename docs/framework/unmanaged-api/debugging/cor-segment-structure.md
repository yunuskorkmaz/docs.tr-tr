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
ms.openlocfilehash: a5c743064b8ca645cf45d02b8800c88187bf4c6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179281"
---
# <a name="cor_segment-structure"></a>COR_SEGMENT Yapısı
Yönetilen yığındaki bellek bölgesi hakkında bilgi içerir.  
  
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
|`gen`|Bellek bölgesinin oluşumunu gösteren [bir CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) numaralandırma üyesi.|  
|`heap`|Bellek bölgesinin bulunduğu yığın numarası. Daha fazla bilgi için Açıklamalar bölümüne bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yapı, `COR_SEGMENTS` yönetilen yığındaki bellek bölgesini temsil eder.  `COR_SEGMENTS`nesneler [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) toplama nesnesi, [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) yöntemi çağırarak doldurulur üyeleridir.  
  
 Alan, `heap` bildirilen yığına karşılık gelen işlemci numarasıdır. İş istasyonu çöp toplayıcıları için değeri her zaman sıfırdır, çünkü iş istasyonlarında yalnızca bir çöp toplama yığını vardır. Sunucu çöp toplayıcıları için değeri, yığının bağlı olduğu işlemciye karşılık gelir. Çöp toplayıcının uygulama ayrıntıları nedeniyle gerçek işlemcilerden daha fazla veya daha az çöp toplama yığını olabileceğini unutmayın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata ayıklama](index.md)
