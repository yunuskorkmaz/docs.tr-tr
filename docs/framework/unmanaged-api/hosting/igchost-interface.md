---
title: IGCHost Arabirimi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d3f588bfc9799ed4591114b28d081ab417678b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914804"
---
# <a name="igchost-interface"></a>IGCHost Arabirimi
Çöp toplama sistemi hakkında bilgi edinmek ve çöp toplamanın bazı yönlerini denetlemek için yöntemler sağlar.  
  
> [!NOTE]
> 4,5 .NET Framework başlayarak, [IGCHost2:: SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) yöntemini kullanarak bir çöp toplama segmentinin boyutunu ve çöp toplama sisteminin en büyük boyutunu 0 ' dan `DWORD` daha büyük değerlere ayarlayın. [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) yöntemi tarafından uygulanan sınır.  
  
> [!NOTE]
> Bu arabirim yalnızca uzman kullanımı içindir. Yanlış kullanılırsa, bir uygulamanın performansını etkileyebilir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Collect Yöntemi](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|Geçerli çöp toplamanın durumundan bağımsız olarak, belirli bir oluşturma için bir koleksiyonu meydana gelecek şekilde zorlar.|  
|[GetStats Yöntemi](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|Çöp toplama sisteminin geçerli durumunun istatistiklerini alır.|  
|[GetThreadStats Yöntemi](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|Çöp toplama için iş parçacığı başına istatistikleri alır.|  
|[SetGCStartupLimits Yöntemi](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|Oluşturma 0 ' nın segment boyutunu ve en büyük boyutunu ayarlar.|  
|[SetVirtualMemLimit Yöntemi](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|Çalışma zamanının sanal belleğinin en büyük boyutunu ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** GCHost. IDL, GCHost. h  
  
 **Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost Coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
