---
description: 'Daha fazla bilgi edinin: CorRefToDefCheck numaralandırması'
title: CorRefToDefCheck Numaralandırması
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
ms.openlocfilehash: ca9d1c7ceb3d9f82ef8d5f1f54d869db64053e69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784255"
---
# <a name="correftodefcheck-enumeration"></a>CorRefToDefCheck Numaralandırması

Kodu iyileştirmek için hangi başvurulan öğelerin tanımlarına dönüştürüleceğini denetleyen bayrakları belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`MDRefToDefDefault`|Tür başvurularının ve üye başvurularının tanımlara dönüştürülmesi gerektiğini belirtir. Bu varsayılan değerdir ( `MDTypeRefToDef` &#124; `MDMemberRefToDef` ).|  
|`MDRefToDefAll`|Başvurulan tüm öğelerin tanımlara dönüştürülmesi gerektiğini belirtir.|  
|`MDRefToDefNone`|Başvurulan hiçbir öğenin tanımlara dönüştürülmesi gerektiğini belirtir.|  
|`MDTypeRefToDef`|Yalnızca tür başvurularının tür tanımlarına dönüştürülmesi gerektiğini belirtir.|  
|`MDMemberRefToDef`|Yalnızca üye başvurularının tanımlara dönüştürülmesi gerektiğini belirtir. Diğer bir deyişle, üye başvuruları Yöntem tanımlarına veya alan tanımlarına dönüştürülmelidir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
