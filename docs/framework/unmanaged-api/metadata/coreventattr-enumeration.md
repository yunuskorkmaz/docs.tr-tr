---
title: CorEventAttr Numaralandırması
ms.date: 03/30/2017
api_name:
- CorEventAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorEventAttr
helpviewer_keywords:
- CorEventAttr enumeration [.NET Framework metadata]
ms.assetid: dc2b3281-3820-487e-930d-350b66dc6417
topic_type:
- apiref
ms.openlocfilehash: 554f47cc4bd948e2b6106c1d71a2a4b7968d43f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718871"
---
# <a name="coreventattr-enumeration"></a>CorEventAttr Numaralandırması

Bir olayın meta verilerini tanımlayan değerleri içerir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`evSpecialName`|Olayın özel olduğunu ve adının nasıl olduğunu belirtir.|  
|`evReservedMask`|Ortak dil çalışma zamanı tarafından iç kullanım için ayrılmıştır.|  
|`evRTSpecialName`|Ortak dil çalışma zamanının olay adının kodlamasını denetlemesi gerektiğini belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
