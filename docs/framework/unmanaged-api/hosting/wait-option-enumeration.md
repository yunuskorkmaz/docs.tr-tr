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
ms.openlocfilehash: 4c57a3fde3565a21800c60794b6c2d1c7616ddd8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008007"
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
|`WAIT_ALERTABLE`|CLR [IHostTask:: Alert](ihosttask-alert-method.md) yöntemini çağırırsa, konağın görevin başlatılabilmesi uyandırılır olması gerektiğini bildirir.|  
|`WAIT_MSGPUMP`|İş parçacığı engellenirse, konağa geçerli işletim sistemi iş parçacığında ileti göndericisi gerektiğini bildirir. Çalışma zamanı bu değeri yalnızca bir <xref:System.Threading.ApartmentState.STA> iş parçacığında belirtir.|  
|`WAIT_NOTINDEADLOCK`|Ana bilgisayara belirtilen eşitleme isteğinin bir konak tarafından bölünemez olduğunu bildirir. Diğer bir deyişle, ana bilgisayar dönemeyebilir `HOST_E_DEADLOCK` .|  
  
## <a name="remarks"></a>Açıklamalar  
 [IHostTaskManager:: Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) ve [IHostTaskManager:: SwitchToTask](ihosttaskmanager-switchtotask-method.md) yöntemlerinin her ikisi de bu türde bir parametre alır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Sabit Listeleri](hosting-enumerations.md)
