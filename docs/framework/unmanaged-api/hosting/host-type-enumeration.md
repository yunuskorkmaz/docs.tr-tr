---
title: HOST_TYPE Numaralandırması
ms.date: 03/30/2017
api_name:
- HOST_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- HOST_TYPE
helpviewer_keywords:
- HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfb1cff3e95c5ff86d22913745b7d14982766b48
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968611"
---
# <a name="hosttype-enumeration"></a>HOST_TYPE Numaralandırması
Bir uygulamayı başlatmadan konak türünü belirten değerleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|AppLaunch.exe uygulamayı başlatın.<br /><br /> Kısmen güvenilen uygulamalar için bu değeri kullanın.|  
|`HOST_TYPE_CORFLAG`|Uygulamayı doğrudan başlatın. Diğer bir deyişle, kendi .exe dosyası uygulamayı başlatın.<br /><br /> Bu değer, tam olarak güvenilen uygulamalar için kullanın.|  
|`HOST_TYPE_DEFAULT`|HOST_TYPE_APPLAUNCH ile aynıdır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
