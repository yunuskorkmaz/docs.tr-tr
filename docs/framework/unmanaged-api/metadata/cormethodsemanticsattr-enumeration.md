---
description: 'Daha fazla bilgi edinin: CorMethodSemanticsAttr numaralandırması'
title: CorMethodSemanticsAttr Numaralandırması
ms.date: 03/30/2017
api_name:
- CorMethodSemanticsAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodSemanticsAttr
helpviewer_keywords:
- CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type:
- apiref
ms.openlocfilehash: 4079e81ae2389ff0684fd11d0751b191a7289932
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784372"
---
# <a name="cormethodsemanticsattr-enumeration"></a>CorMethodSemanticsAttr Numaralandırması

Bir yöntem ile ilişkili bir özellik veya olay arasındaki ilişkiyi tanımlayan değerleri içerir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`msSetter`|Metodun `set` bir özellik için erişimci olduğunu belirtir.|  
|`msGetter`|Metodun `get` bir özellik için erişimci olduğunu belirtir.|  
|`msOther`|Metodun bir özellik veya burada tanımlananlardan farklı bir olayla ilişkisi olduğunu belirtir.|  
|`msAddOn`|Yöntemin bir olay için işleyici yöntemleri ekleyeceğini belirtir.|  
|`msRemoveOn`|Metodun bir olay için işleyici yöntemlerini kaldırdığından emin olarak belirtir.|  
|`msFire`|Yöntemin bir olay harekete geçirmediğini belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
