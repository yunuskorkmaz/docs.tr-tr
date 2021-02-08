---
description: 'Daha fazla bilgi edinin: COR_TYPE_LAYOUT yapısı'
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
ms.openlocfilehash: 07bed0c526aae38cb380b57da505a3f02bdf4aae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801771"
---
# <a name="cor_type_layout-structure"></a>COR_TYPE_LAYOUT Yapısı

Bellekteki bir nesnenin düzeni hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Syntax  
  
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
  
|Üye|Description|  
|------------|-----------------|  
|`parentID`|Bu türe üst türün tanımlayıcısı. Bu, tür kimliği öğesine karşılık geliyorsa, NULL tür kimliği (token1 = 0, token2 = 0) olacaktır <xref:System.Object?displayProperty=nameWithType> .|  
|`objectSize`|Bu türdeki bir nesnenin temel boyutu. Bu, değişken olmayan ölçekli nesnelerin toplam boyutudur.|  
|`numFields`|Bu türün nesnelerine dahil edilen alan sayısı.|  
|`boxOffset`|Bu tür paketlenise, bir nesne alanlarının başlangıç boşluğu. Bu alan, yalnızca temel öğeler ve yapılar gibi değer türleri için geçerlidir.|  
|`type`|Bu türün ait olduğu CorElementType.|  
  
## <a name="remarks"></a>Açıklamalar  

 `numFields`Sıfırdan büyükse, bu türdeki alanlarla ilgili bilgi almak Için [ICorDebugProcess5:: GetTypeFields](icordebugprocess5-gettypefields-method.md) metodunu çağırabilirsiniz. `type` `ELEMENT_TYPE_STRING` , Veya ise, `ELEMENT_TYPE_ARRAY` `ELEMENT_TYPE_SZARRAY` Bu türün nesnelerinin boyutu değişkendir ve [COR_TYPEID](cor-typeid-structure.md) yapısını [ICorDebugProcess5:: GetArrayLayout](icordebugprocess5-getarraylayout-method.md) metoduna geçirebilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
