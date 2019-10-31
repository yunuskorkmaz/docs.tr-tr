---
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
ms.openlocfilehash: f09c6bb79d7bd28f4d8b74237b6f343a07b79062
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141476"
---
# <a name="stackoverflowtype-enumeration"></a>StackOverflowType Numaralandırması
Yığın taşması olayının temel nedenini gösteren değerleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`SO_ClrEngine`|Yığın taşması yürütme altyapısından kaynaklandı.|  
|`SO_Managed`|Yönetilen koddan oluşan yığın taşmasına neden oldu.|  
|`SO_Other`|Yığın taşması, yönetilmeyen koddan kaynaklandı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu bilgiler, [IActionOnCLREvent:: OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) yöntemine yapılan bir çağrı aracılığıyla konağa geçirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
