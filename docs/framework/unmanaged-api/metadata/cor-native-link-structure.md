---
title: COR_NATIVE_LINK Yapısı
ms.date: 03/30/2017
api_name:
- COR_NATIVE_LINK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_NATIVE_LINK
helpviewer_keywords:
- COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type:
- apiref
ms.openlocfilehash: a11b7d5939c4c20504b1ff3dfb4613f85bca0db4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007981"
---
# <a name="cor_native_link-structure"></a>COR_NATIVE_LINK Yapısı
Yerel kodu bağlamak için kullanılan bilgileri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`m_linkType`|Yerel koda bağlanacak tür. Bu değer, [Cornativelınktype](cornativelinktype-enumeration.md) değerlerinden biridir.|  
|`m_flags`|Yerel kod bağlanırken bağlayıcı tarafından kullanılan bayraklar. Bu değer, [Cornativelınkflags](cornativelinkflags-enumeration.md) değerlerinden biridir.|  
|`m_entryPoint`|Giriş noktasını temsil eden MemberRef meta veri belirteci. Biçim şöyledir: `lib:entrypoint`.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Yapıları](metadata-structures.md)
- [CorNativeLinkType Sabit Listesi](cornativelinktype-enumeration.md)
- [CorNativeLinkFlags Sabit Listesi](cornativelinkflags-enumeration.md)
