---
title: CeeSectionRelocExtra Birleşimi
ms.date: 03/30/2017
api_name:
- CeeSectionRelocExtra Union
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocExtra
helpviewer_keywords:
- CeeSectionRelocExtra union [.NET Framework metadata]
ms.assetid: d9568cf6-7f98-4cd6-ab36-0a2bd509afcc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a78a4b82d0b2064c90c938a8614b0c7594f7856
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182279"
---
# <a name="ceesectionrelocextra-union"></a>CeeSectionRelocExtra Birleşimi
Tarafından kullanılan bir adres farkı gösteren [Iceegen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) bir bölümün dışında yeniden konumlandırmakta arabirimi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`highAdj`|Bölüm için adres üst ayarlama.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Birleşimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
