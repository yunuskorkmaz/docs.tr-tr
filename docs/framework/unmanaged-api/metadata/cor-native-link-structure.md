---
description: 'Daha fazla bilgi edinin: COR_NATIVE_LINK yapısı'
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
ms.openlocfilehash: 09c715af698a0614fd4a9a17679df6908a1497a6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678581"
---
# <a name="cor_native_link-structure"></a>COR_NATIVE_LINK Yapısı

Yerel kodu bağlamak için kullanılan bilgileri içerir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`m_linkType`|Yerel koda bağlanacak tür. Bu değer, [Cornativelınktype](cornativelinktype-enumeration.md) değerlerinden biridir.|  
|`m_flags`|Yerel kod bağlanırken bağlayıcı tarafından kullanılan bayraklar. Bu değer, [Cornativelınkflags](cornativelinkflags-enumeration.md) değerlerinden biridir.|  
|`m_entryPoint`|Giriş noktasını temsil eden MemberRef meta veri belirteci. Biçim `lib:entrypoint` .|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Yapıları](metadata-structures.md)
- [CorNativeLinkType Numaralandırması](cornativelinktype-enumeration.md)
- [CorNativeLinkFlags Numaralandırması](cornativelinkflags-enumeration.md)
