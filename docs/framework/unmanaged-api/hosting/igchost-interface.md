---
title: IGCHost Arabirimi
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
- IGCHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost
helpviewer_keywords:
- IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 77a2cab35785aa39571d39bdd369fa26cdbcd1d2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="igchost-interface"></a>IGCHost Arabirimi
Çöp toplama sistemi hakkında bilgi edinme ve atık toplama bazı yönlerini denetleme yöntemleri sağlar.  
  
> [!NOTE]
>  İle başlayarak [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], kullanabileceğiniz [Igchost2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) bir atık toplama kesim boyutunu ve en büyük boyutu 0 atık toplama sistemin nesil değerlere büyük ayarlamak için yöntemi `DWORD` tarafından uygulanan sınır [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) yöntemi.  
  
> [!NOTE]
>  Yalnızca Uzman kullanım arabirimidir. Yanlış kullandıysanız, bir uygulamanın performansını etkileyebilir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Collect Yöntemi](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|Geçerli çöp toplama durumu bağımsız olarak verilen oluşturma için gerçekleşmesi için bir koleksiyon zorlar.|  
|[GetStats Yöntemi](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|İstatistikleri çöp toplama sistemi için geçerli durumunu alır.|  
|[GetThreadStats Yöntemi](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|İş parçacığı başına istatistiklerini atık toplama için alır.|  
|[SetGCStartupLimits Yöntemi](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|Kesim boyutu ve en büyük boyutu 0 oluşturma için ayarlar.|  
|[SetVirtualMemLimit Yöntemi](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|En büyük çalışma zamanı'nın sanal bellek boyutunu belirler.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** GCHost.idl, GCHost.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [CorRuntimeHost Coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
