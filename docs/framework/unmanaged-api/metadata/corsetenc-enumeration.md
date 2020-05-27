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
ms.openlocfilehash: 93a194ea72ab894544927cf96304397b7211b5ac
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009164"
---
# <a name="corsetenc-enumeration"></a>CorSetENC Numaralandırması
Meta veri oluşturma sırasında davranışı etkilemek için kullanılan değerleri içerir.  
  
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
