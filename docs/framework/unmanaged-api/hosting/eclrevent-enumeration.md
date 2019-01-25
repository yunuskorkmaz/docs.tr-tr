---
title: EClrEvent Numaralandırması
ms.date: 03/30/2017
api_name:
- EClrEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrEvent
helpviewer_keywords:
- EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d66e010340d186eed2222ae2ba8cfb24b8e8d7b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658578"
---
# <a name="eclrevent-enumeration"></a>EClrEvent Numaralandırması
Konak geri çağırmaları kaydedebilirsiniz ortak dil çalışma zamanı (CLR) olaylarını açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`Event_ClrDisabled`|Önemli bir CLR hata belirtir.|  
|`Event_DomainUnload`|Belirli bir eklentiyi belirtir <xref:System.AppDomain>.|  
|`Event_MDAFired`|Yönetilen hata ayıklama Yardımcısı (MDA) iletisini oluşturulduğunu belirtir.|  
|`Event_StackOverflow`|Bir yığın taşması hata oluştuğunu belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ana bilgisayar tarafından açıklanan olay türlerinden herhangi birini geri kaydedebilirsiniz `EClrEvent` yöntemleri çağırarak [Iclroneventmanager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) arabirimi. Konak, çağırarak bu arabirim için bir işaretçi alır [Iclrcontrol::getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) yöntemi.  
  
 `Event_CLRDisabled` Ve `Event_DomainUnload` birden çok kez ve bir kaldırma veya CLR devre dışı bırakma sinyal farklı iş parçacıklarından olayları'nin yükseltilebilir.  
  
 `Event_MDAFired` Olayını oluşturulmasını bir [Mdaınfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) MDA ileti ayrıntılarını içeren örneği. Mda'leri hakkında daha fazla bilgi için bkz: [yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IActionOnCLREvent Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [ICLRControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
