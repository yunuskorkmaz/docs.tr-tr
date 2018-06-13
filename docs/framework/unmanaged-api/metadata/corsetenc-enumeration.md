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
ms.openlocfilehash: 3e09bf424a41445f7e36397775d1578cdf4e7e75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442793"
---
# <a name="corsetenc-enumeration"></a>CorSetENC Numaralandırması
Meta veri oluşturma sırasında davranışını etkilemek için kullanılan değerler içeriyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`MDUpdateENC`|Meta verileri güncelleştirildi ancak belirteçleri taşınamaz gösterir.|  
|`MDUpdateFull`|Belirteçleri güncelleştirmeleri sırasında taşınabilmesi gösterir.|  
|`MDUpdateExtension`|Yalnızca eklemeler güncelleştirmeler oluşabilir gösterir. Belirteçleri taşınamaz.|  
|`MDUpdateIncremental`|Derleme artımlı olduğunu gösterir.|  
|`MDUpdateDelta`|Yalnızca değiştirilen meta verilerin kaydedilmesi gerektiğini gösterir.|  
|`MDUpdateMask`|İçeren `MDUpdateENC`, `MDUpdateFull` ve `MDUpdateIncremental`.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
