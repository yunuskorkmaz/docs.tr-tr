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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7024140ed9b870b5db38dba7e9b13321dd37386a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157592"
---
# <a name="cornativelink-structure"></a>COR_NATIVE_LINK Yapısı
Yerel kod bağlantı için kullanılan bilgileri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`m_linkType`|Yerel kodda bağlanacak türü. Bu değer biridir [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) değerleri.|  
|`m_flags`|Bağlayıcı tarafından yerel kod bağlanırken kullanılan bayraklar. Bu değer biridir [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) değerleri.|  
|`m_entryPoint`|Giriş noktasını temsil eden MemberRef meta veri belirteci. Biçim `lib:entrypoint`.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Yapıları](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [CorNativeLinkType Sabit Listesi](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [CorNativeLinkFlags Sabit Listesi](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
