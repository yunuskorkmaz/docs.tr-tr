---
description: 'Daha fazla bilgi edinin: CorSetENC Enumeration'
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
ms.openlocfilehash: 5ba3e41c10b082ceb2ce7d327f7ff7f857ca98a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707403"
---
# <a name="corsetenc-enumeration"></a>CorSetENC Numaralandırması

Meta veri oluşturma sırasında davranışı etkilemek için kullanılan değerleri içerir.  
  
## <a name="syntax"></a>Syntax  
  
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
  
|Üye|Description|  
|------------|-----------------|  
|`MDSetENCOn`|Kullanımdan kalktı.|  
|`MDSetENCOff`|Kullanımdan kalktı.|  
|`MDUpdateENC`|Meta verilerin güncelleştirilebileceğini, belirteçlerin taşınamayacağını gösterir.|  
|`MDUpdateFull`|Simgelerin güncelleştirmeler sırasında taşınabileceğini gösterir.|  
|`MDUpdateExtension`|Güncelleştirmelerin yalnızca eklemelerden oluşabileceğini gösterir. Belirteçler taşınamaz.|  
|`MDUpdateIncremental`|Derlemenin artımlı olduğunu gösterir.|  
|`MDUpdateDelta`|Yalnızca değiştirilen meta verilerin kaydedilmesi gerektiğini gösterir.|  
|`MDUpdateMask`|`MDUpdateENC`, `MDUpdateFull` Ve içerir `MDUpdateIncremental` .|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
