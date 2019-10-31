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
ms.openlocfilehash: ee749fd40f440e92f1d1b09c2ea5e7bdd51f1cbe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131128"
---
# <a name="eclrevent-enumeration"></a>EClrEvent Numaralandırması
Konağın geri çağırmaları kaydedebileceği ortak dil çalışma zamanı (CLR) olaylarını açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`Event_ClrDisabled`|Önemli bir CLR hatası belirtir.|  
|`Event_DomainUnload`|Belirli bir <xref:System.AppDomain>kaldırılmasını belirtir.|  
|`Event_MDAFired`|Yönetilen hata ayıklama Yardımcısı (MDA) iletisinin oluşturulduğunu belirtir.|  
|`Event_StackOverflow`|Yığın taşması hatası oluştuğunu belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ana bilgisayar, [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) arabiriminin yöntemlerini çağırarak `EClrEvent` tarafından tanımlanan olay türlerinden herhangi biri için geri çağırmaları kaydedebilir. Ana bilgisayar [ICLRControl:: GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metodunu çağırarak bu arabirime yönelik bir işaretçi alır.  
  
 `Event_CLRDisabled` ve `Event_DomainUnload` olayları birden çok kez ve farklı iş parçacıklarından, CLR 'nin bir yüklemesini veya devre dışı bırakılmasını bildirmek için bir kereden fazla oluşturulabilir.  
  
 `Event_MDAFired` olay, MDA iletisinin ayrıntılarını içeren bir [Mdadınfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) örneği oluşturulmasını başlatır. MDAs hakkında daha fazla bilgi için bkz. [yönetilen hata ayıklama yardımcıları Ile hataları tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IActionOnCLREvent Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [ICLRControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
