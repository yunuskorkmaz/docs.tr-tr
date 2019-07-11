---
title: CorSetENC Numaralandırması
ms.date: 03/30/2017
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2796be32154275387da891683cc5053095f534af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772320"
---
# <a name="corsetenc-enumeration"></a>CorSetENC Numaralandırması
Meta veri oluşturma sırasında davranışını etkilemek için kullanılan değerler içeriyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`MDSetENCOn`|Kullanımdan kalktı.|  
|`MDSetENCOff`|Kullanımdan kalktı.|  
|`MDUpdateENC`|Meta veri güncelleştirilebilir gelirken, belirteçleri taşınamaz gösterir.|  
|`MDUpdateFull`|Güncelleştirmeler sırasında belirteçleri taşınabilir gösterir.|  
|`MDUpdateExtension`|Güncelleştirmeleri yalnızca yapılan eklemeleri oluşabilir gösterir. Belirteçleri taşınamaz.|  
|`MDUpdateIncremental`|Derleme artımlı olduğunu gösterir.|  
|`MDUpdateDelta`|Yalnızca değiştirilen meta verilerin kaydedilmesi gerektiğini gösterir.|  
|`MDUpdateMask`|İçerir `MDUpdateENC`, `MDUpdateFull` ve `MDUpdateIncremental`.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
