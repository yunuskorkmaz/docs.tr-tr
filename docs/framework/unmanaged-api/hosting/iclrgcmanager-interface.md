---
title: ICLRGCManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager
helpviewer_keywords:
- ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e284f94ad0dac9523bd6267e7bc1034a079503d
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380291"
---
# <a name="iclrgcmanager-interface"></a>ICLRGCManager Arabirimi
Ortak dil çalışma zamanının atık toplama sistem ile etkileşimde bulunmak konak izin vermek için yöntemler sağlar.  
  
> [!NOTE]
>  Kullanabileceğiniz .NET Framework 4.5 ile başlayarak, [Iclrgcmanager2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) bir çöp toplama kesim boyutunu ve en büyük boyutu çöp toplama sistemin nesil 0 değerine ayarlanacak yöntemi büyüktür `DWORD` tarafından uygulanan sınır [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) yöntemi.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Collect Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|Bir çöp toplama işlemi için belirtilen oluşturmanın zorlar.|  
|[GetStats Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|Çöp toplama sistemi geçerli İstatistikler kümesini alır.|  
|[SetGCStartupLimits Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|Bir çöp toplama kesim boyutunu ve çöp toplama sistemin nesil 0 en büyük boyutunu ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı (CLR) yönetilen, atık toplama mekanizması uygular <xref:System.GC> türü. Çöp toplama sistemi hakkında daha fazla bilgi için bkz: [çöp toplama](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik Bellek Yönetimi](../../../../docs/standard/automatic-memory-management.md)
- [COR_GC_STATS Yapısı](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [ICLRControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [CLR Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
