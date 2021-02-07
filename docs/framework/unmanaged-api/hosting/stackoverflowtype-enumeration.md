---
description: 'Hakkında daha fazla bilgi edinin: StackOverflowType numaralandırması'
title: StackOverflowType Numaralandırması
ms.date: 03/30/2017
api_name:
- StackOverflowType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowType
helpviewer_keywords:
- StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type:
- apiref
ms.openlocfilehash: d39ccd99331a3e839236f1ede21254edb92b2dfb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679374"
---
# <a name="stackoverflowtype-enumeration"></a>StackOverflowType Numaralandırması

Yığın taşması olayının temel nedenini gösteren değerleri içerir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`SO_ClrEngine`|Yığın taşması yürütme altyapısından kaynaklandı.|  
|`SO_Managed`|Yönetilen koddan oluşan yığın taşmasına neden oldu.|  
|`SO_Other`|Yığın taşması, yönetilmeyen koddan kaynaklandı.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu bilgiler, [IActionOnCLREvent:: OnEvent](iactiononclrevent-onevent-method.md) yöntemine yapılan bir çağrı aracılığıyla konağa geçirilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Numaralandırmaları](hosting-enumerations.md)
