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
ms.openlocfilehash: 91483d5bdf1eb8e6b03d7691e2a95074e3789317
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134874"
---
# <a name="igchost-interface"></a>IGCHost Arabirimi
Çöp toplama sistemi hakkında bilgi edinmek ve çöp toplamanın bazı yönlerini denetlemek için yöntemler sağlar.  
  
> [!NOTE]
> 4,5 .NET Framework başlayarak, [IGCHost2:: SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) yöntemini kullanarak bir çöp toplama kesiminin boyutunu ve çöp toplama sisteminin nesil 0 ' ı için en büyük boyutu `DWORD` sınırından daha büyük değerlere ayarlayabilirsiniz Bu, [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) yöntemi tarafından belirlenir.  
  
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
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** GCHost. IDL, GCHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost Coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
