---
description: 'Hakkında daha fazla bilgi edinin: WAIT_OPTION numaralandırması'
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
ms.openlocfilehash: 1d651909e0f62f2db7478a6e0b37139d1f953196
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679153"
---
# <a name="wait_option-enumeration"></a>WAIT_OPTION Numaralandırması

Ortak dil çalışma zamanı (CLR) blokları tarafından istenen işlem için bir konağın yapması gereken eylemi belirten değerleri içerir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|CLR [IHostTask:: Alert](ihosttask-alert-method.md) yöntemini çağırırsa, konağın görevin başlatılabilmesi uyandırılır olması gerektiğini bildirir.|  
|`WAIT_MSGPUMP`|İş parçacığı engellenirse, konağa geçerli işletim sistemi iş parçacığında ileti göndericisi gerektiğini bildirir. Çalışma zamanı bu değeri yalnızca bir <xref:System.Threading.ApartmentState.STA> iş parçacığında belirtir.|  
|`WAIT_NOTINDEADLOCK`|Ana bilgisayara belirtilen eşitleme isteğinin bir konak tarafından bölünemez olduğunu bildirir. Diğer bir deyişle, ana bilgisayar dönemeyebilir `HOST_E_DEADLOCK` .|  
  
## <a name="remarks"></a>Açıklamalar  

 [IHostTaskManager:: Sleep](ihosttaskmanager-sleep-method.md) ve [IHostTaskManager:: SwitchToTask](ihosttaskmanager-switchtotask-method.md) yöntemlerinin her ikisi de bu türde bir parametre alır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Numaralandırmaları](hosting-enumerations.md)
