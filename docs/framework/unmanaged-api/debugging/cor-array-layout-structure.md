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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3a5a5bb26912c87cdf37ba0d8f0cee1cf1ffa97
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142018"
---
# <a name="corarraylayout-structure"></a>COR_ARRAY_LAYOUT Yapısı
Bir dizi nesnesinin bellek düzeni hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`componentID`|Dizinin içerdiği nesnelerin türü tanımlayıcısı.|  
|`componentType`|Bileşen bir çöp toplama başvuru, değer sınıfı veya basit bir tür olup olmadığını belirten bir CorElementType sabit listesi değeri.|  
|`firstElementOffset`|Dizideki ilk öğe için olan uzaklık.|  
|`elementSize`|Her öğe boyutu.|  
|`countOffset`|Dizideki öğelerin sayısını uzaklık.|  
|`rankSize`|Boyut, bayt cinsinden boyutu.|  
|`numRanks`|Dizideki sıralamalara sahip sayısı.|  
|`rankOffset`|Başlangıçtan sıralamalara sahip başlangıç uzaklığı.|  
  
## <a name="remarks"></a>Açıklamalar  
 `rankSize` Alanı, çok boyutlu bir dizi sırası boyutunu belirtir. Tek boyutlu diziler için de doğrudur.  
  
 Değerini `numRanks` tek boyutlu bir dizi için 1'dir ve `N` çok boyutlu bir dizi için `N` boyutları.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
