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
ms.openlocfilehash: 9ecfb551b55551e5f6cc7e7e9ffb55e5a96259ee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141507"
---
# <a name="wait_option-enumeration"></a>WAIT_OPTION Numaralandırması
Ortak dil çalışma zamanı (CLR) blokları tarafından istenen işlem için bir konağın yapması gereken eylemi belirten değerleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|CLR [IHostTask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) yöntemini çağırırsa, konağın görevin başlatılabilmesi uyandırılır olması gerektiğini bildirir.|  
|`WAIT_MSGPUMP`|İş parçacığı engellenirse, konağa geçerli işletim sistemi iş parçacığında ileti göndericisi gerektiğini bildirir. Çalışma zamanı bu değeri yalnızca bir <xref:System.Threading.ApartmentState.STA> iş parçacığında belirtir.|  
|`WAIT_NOTINDEADLOCK`|Ana bilgisayara belirtilen eşitleme isteğinin bir konak tarafından bölünemez olduğunu bildirir. Diğer bir deyişle, ana bilgisayar `HOST_E_DEADLOCK`döndüremez.|  
  
## <a name="remarks"></a>Açıklamalar  
 [IHostTaskManager:: Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) ve [IHostTaskManager:: SwitchToTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) yöntemlerinin her ikisi de bu türde bir parametre alır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
