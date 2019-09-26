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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bd274b1eb14532629580e777288317186544912
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274157"
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
|`parentID`|Bu türe üst türün tanımlayıcısı. Bu, tür kimliği öğesine <xref:System.Object?displayProperty=nameWithType>KARŞıLıK geliyorsa, null tür kimliği (token1 = 0, token2 = 0) olacaktır.|  
|`objectSize`|Bu türdeki bir nesnenin temel boyutu. Bu, değişken olmayan ölçekli nesnelerin toplam boyutudur.|  
|`numFields`|Bu türün nesnelerine dahil edilen alan sayısı.|  
|`boxOffset`|Bu tür paketlenise, bir nesne alanlarının başlangıç boşluğu. Bu alan, yalnızca temel öğeler ve yapılar gibi değer türleri için geçerlidir.|  
|`type`|Bu türün ait olduğu CorElementType.|  
  
## <a name="remarks"></a>Açıklamalar  
 Sıfırdan büyükse, bu türdeki alanlarla ilgili bilgi almak için [ICorDebugProcess5:: GetTypeFields](icordebugprocess5-gettypefields-method.md) metodunu çağırabilirsiniz. `numFields` `ELEMENT_TYPE_STRING` [](cor-typeid-structure.md) , `type` Veya`ELEMENT_TYPE_SZARRAY`ise, bu türün nesnelerinin boyutu değişkendir ve COR_TYPEID yapısını [ICorDebugProcess5:: GetArrayLayout](icordebugprocess5-getarraylayout-method.md) metoduna geçirebilirsiniz. `ELEMENT_TYPE_ARRAY`  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
