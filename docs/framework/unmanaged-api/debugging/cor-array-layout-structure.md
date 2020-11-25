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
ms.openlocfilehash: 2ca6c89a671c4d7882e7cefdb820d07ac5636530
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727412"
---
# <a name="cor_array_layout-structure"></a>COR_ARRAY_LAYOUT Yapısı

Bellekte bir dizi nesnesinin yerleşimi hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Syntax  
  
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
|`componentType`|Bileşenin bir çöp toplama başvurusu, bir değer sınıfı veya temel öğe olup olmadığını gösteren bir CorElementType numaralandırma değeri.|  
|`firstElementOffset`|Dizideki ilk öğenin boşluğu.|  
|`elementSize`|Her öğenin boyutu.|  
|`countOffset`|Dizideki öğe sayısının boşluğu.|  
|`rankSize`|Derecenin bayt cinsinden boyutu.|  
|`numRanks`|Dizideki derecelendirmelerinin sayısı.|  
|`rankOffset`|Derecelendirmelerinin başlayacağı fark.|  
  
## <a name="remarks"></a>Açıklamalar  

 `rankSize`Alan, çok boyutlu bir dizideki bir derece boyutunu belirtir. Tek boyutlu diziler için de doğrudur.  
  
 Değeri, `numRanks` tek boyutlu bir dizi için ve `N` çok boyutlu bir boyut dizisi için 1 ' dir `N` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
