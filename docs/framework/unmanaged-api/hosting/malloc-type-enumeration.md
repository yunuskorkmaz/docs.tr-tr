---
title: MALLOC_TYPE Numaralandırması
ms.date: 03/30/2017
api_name:
- MALLOC_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MALLOC_TYPE
helpviewer_keywords:
- MALLOC_TYPE Enumeration
ms.assetid: c02476f9-23a2-4af7-9282-aa9c42c7429b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 695f69c8d9c3a295a705971743733339cf8aab13
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211952"
---
# <a name="malloctype-enumeration"></a>MALLOC_TYPE Numaralandırması
Ayrılan bellek özelliklerini belirten değerleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|Ayrılan bellek bir yürütülebilir dosya içerebilir.|  
|`MALLOC_THREADSAFE`|Ayrılan bellek, iş parçacığı açısından güvenlidir. Diğer bir deyişle, bellek, herhangi bir eşitleme olmadan birden çok iş parçacığı tarafından erişilebilir.<br /><br /> Bu bayrak ayarlanmazsa çağrıları nesnede seri hale getirilmelidir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Numaralandırmaları](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
