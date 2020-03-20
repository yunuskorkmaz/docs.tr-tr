---
title: COR_ARRAY_LAYOUT Yapısı
ms.date: 03/30/2017
api_name:
- COR_ARRAY_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ARRAY_LAYOUT
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: aa20ac3d-6f60-4aa2-91c5-f3a86f82eba8
topic_type:
- apiref
ms.openlocfilehash: ca2d00611a7530dfb0d1c2a27123947bdf69820d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179347"
---
# <a name="cor_array_layout-structure"></a>COR_ARRAY_LAYOUT Yapısı
Bellekte bir dizi nesnesinin düzeni hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct COR_ARRAY_LAYOUT {  
    COR_TYPEID componentID;  
    CorElementType componentType;  
    ULONG32 firstElementOffset;  
    ULONG32 elementSize;  
    ULONG32 countOffset;
    ULONG32 rankSize;
    ULONG32 numRanks;
    ULONG32 rankOffset;
} COR_ARRAY_LAYOUT;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`componentID`|Dizinin içerdiği nesne türünün tanımlayıcısı.|  
|`componentType`|Bileşenin çöp toplama başvurusu mu, değer sınıfı mı yoksa ilkel mi olduğunu gösteren bir CorElementType numaralandırma değeri.|  
|`firstElementOffset`|Dizideki ilk öğeye ofset.|  
|`elementSize`|Her öğenin boyutu.|  
|`countOffset`|Dizideki öğe sayısına mahsup.|  
|`rankSize`|Rütbenin büyüklüğü, baytlar halinde.|  
|`numRanks`|Dizideki rütbe sayısı.|  
|`rankOffset`|Rütbelerin başladığı ofset.|  
  
## <a name="remarks"></a>Açıklamalar  
 Alan, `rankSize` çok boyutlu bir dizideki bir sıralamanın boyutunu belirtir. Tek boyutlu diziler için de doğrudur.  
  
 Tek boyutlu `numRanks` bir dizi ve `N` çok boyutlu boyutlar dizisi `N` için değeri 1'dir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata ayıklama](index.md)
