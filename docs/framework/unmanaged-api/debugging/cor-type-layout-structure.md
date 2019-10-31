---
title: COR_TYPE_LAYOUT Yapısı
ms.date: 03/30/2017
api_name:
- COR_TYPE_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPE_LAYOUT
helpviewer_keywords:
- COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type:
- apiref
ms.openlocfilehash: 12c594f157c803d5fc179e09a8ca6c0ef40f3f44
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099019"
---
# <a name="cor_type_layout-structure"></a>COR_TYPE_LAYOUT Yapısı
Bellekteki bir nesnenin düzeni hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`parentID`|Bu türe üst türün tanımlayıcısı. Tür kimliği <xref:System.Object?displayProperty=nameWithType>karşılık geliyorsa, bu NULL tür kimliği (token1 = 0, token2 = 0) olacaktır.|  
|`objectSize`|Bu türdeki bir nesnenin temel boyutu. Bu, değişken olmayan ölçekli nesnelerin toplam boyutudur.|  
|`numFields`|Bu türün nesnelerine dahil edilen alan sayısı.|  
|`boxOffset`|Bu tür paketlenise, bir nesne alanlarının başlangıç boşluğu. Bu alan, yalnızca temel öğeler ve yapılar gibi değer türleri için geçerlidir.|  
|`type`|Bu türün ait olduğu CorElementType.|  
  
## <a name="remarks"></a>Açıklamalar  
 `numFields` sıfırdan büyükse, bu türdeki alanlarla ilgili bilgi almak için [ICorDebugProcess5:: GetTypeFields](icordebugprocess5-gettypefields-method.md) metodunu çağırabilirsiniz. `type` `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`veya `ELEMENT_TYPE_SZARRAY`, bu türdeki nesnelerin boyutu değişkendir ve [COR_TYPEID](cor-typeid-structure.md) yapısını [ICorDebugProcess5:: GetArrayLayout](icordebugprocess5-getarraylayout-method.md) metoduna geçirebilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
