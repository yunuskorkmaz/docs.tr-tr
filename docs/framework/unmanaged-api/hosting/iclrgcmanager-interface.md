---
title: ICLRGCManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6cc6c84d57e4114a28a8b363b99b98f3c4d21410
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrgcmanager-interface"></a>ICLRGCManager Arabirimi
Ortak dil çalışma zamanı 's çöp toplama sistemi ile etkileşim kurmak bir konak izin yöntemleri sağlar.  
  
> [!NOTE]
>  İle başlayarak [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], kullanabileceğiniz [Iclrgcmanager2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) bir atık toplama kesim boyutunu ve en büyük boyutu 0 atık toplama sistemin nesil değerlere büyük ayarlamak için yöntemi ' den `DWORD` tarafından uygulanan sınır [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) yöntemi.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Collect Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|Çöp toplama belirtilen oluşturma için zorlar.|  
|[GetStats Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|Çöp toplama sistemi hakkında geçerli istatistiklerini kümesini alır.|  
|[SetGCStartupLimits Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|Çöp toplama kesim boyutunu ve en büyük boyutu 0 atık toplama sistemin nesil ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı (CLR), atık toplama mekanizmasıyla yönetilen uygulayan <xref:System.GC> türü. Çöp toplama sistemi hakkında daha fazla bilgi için bkz: [çöp toplama](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Otomatik Bellek Yönetimi](../../../../docs/standard/automatic-memory-management.md)  
 [COR_GC_STATS Yapısı](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [ICLRControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [CLR Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
