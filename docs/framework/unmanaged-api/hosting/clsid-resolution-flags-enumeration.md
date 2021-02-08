---
description: 'Hakkında daha fazla bilgi edinin: CLSID_RESOLUTION_FLAGS numaralandırması'
title: CLSID_RESOLUTION_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- CLSID_RESOLUTION_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLSID_RESOLUTION_FLAGS
helpviewer_keywords:
- CLSID_RESOLUTION_FLAGS enumeration [.NET Framework hosting]
ms.assetid: cd8b9879-962a-4811-aa46-2e2b6bae0d84
topic_type:
- apiref
ms.openlocfilehash: 54d334147e13217f8ce20dae1b139cdc6d11a3b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799882"
---
# <a name="clsid_resolution_flags-enumeration"></a>CLSID_RESOLUTION_FLAGS Numaralandırması

Ortak dil çalışma zamanının (CLR) bir kaç çözüm içermesi gerektiğini belirten değerleri içerir `CLSID` .  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|Varsayılan davranışı gösterir.|  
|`CLSID_RESOLUTION_REGISTERED`|Çalışma zamanının kayıt defterini arayacağı ve dolgu ilkesi uyguladığı anlamına gelir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Numaralandırmaları](hosting-enumerations.md)
