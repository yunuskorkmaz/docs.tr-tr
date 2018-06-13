---
title: WAIT_OPTION Numaralandırması
ms.date: 03/30/2017
api_name:
- WAIT_OPTION
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAIT_OPTION
helpviewer_keywords:
- WAIT_OPTION enumeration [.NET Framework hosting]
ms.assetid: 962fc293-8ded-4b3b-90ce-2c21a4f1b244
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb37394799db39baa406ef332066d5ebb2dbf19d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441935"
---
# <a name="waitoption-enumeration"></a>WAIT_OPTION Numaralandırması
Bir ana bilgisayar ortak dil çalışma zamanı (CLR) bloklarla istenen işlem, eylemde gösteren değerler içeriyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|Ana bilgisayar CLR çağırırsa, görev uyandırdı olduğunu bildirir [Ihosttask::alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) yöntemi.|  
|`WAIT_MSGPUMP`|Ana iş parçacığı engellenmiş duruma gelirse, geçerli işletim sistemi iş parçacığı iletileri göndermelidir bildirir. Çalışma zamanı yalnızca bu değeri belirten bir <xref:System.Threading.ApartmentState.STA> iş parçacığı.|  
|`WAIT_NOTINDEADLOCK`|Konak belirtilen eşitleme isteği bir ana bilgisayar tarafından ayrılmış bildirir. Diğer bir deyişle, konak döndüremez `HOST_E_DEADLOCK`.|  
  
## <a name="remarks"></a>Açıklamalar  
 [Ihosttaskmanager::Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) ve [Ihosttaskmanager::switchtotask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) yöntemleri hem bu türde bir parametre alın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
