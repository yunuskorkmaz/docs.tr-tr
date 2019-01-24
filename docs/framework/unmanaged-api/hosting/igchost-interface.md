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
ms.openlocfilehash: 123eda65510263951895f9c7ac4c6b1781bbd5f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736698"
---
# <a name="igchost-interface"></a>IGCHost Arabirimi
Çöp toplama işleminin bazı yönlerini denetleme ve çöp toplama sistemi hakkında bilgi almak için yöntemler sağlar.  
  
> [!NOTE]
>  İle başlayarak [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], kullanabileceğiniz [Igchost2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) değerlere bir çöp toplama kesim boyutunu ve en büyük boyutu çöp toplama sistemin nesil 0 değerinden ayarlamak için yöntemi `DWORD` tarafından uygulanan sınır [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) yöntemi.  
  
> [!NOTE]
>  Uzman kullanım arabirimidir. Yanlış kullandıysanız, bir uygulamanın performansını etkileyebilir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Collect Yöntemi](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|Geçerli çöp toplama durumundan bağımsız olarak verilen oluşturma için gerçekleşmesi için bir koleksiyon zorlar.|  
|[GetStats Yöntemi](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|İstatistikleri çöp toplama sistemi için geçerli durumunu alır.|  
|[GetThreadStats Yöntemi](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|Çöp toplama iş parçacığı başına istatistiklerini alır.|  
|[SetGCStartupLimits Yöntemi](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|Nesil 0 için kesim boyutu ve en büyük boyutunu ayarlar.|  
|[SetVirtualMemLimit Yöntemi](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|Çalışma zamanının sanal bellek en büyük boyutunu ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** GCHost.idl, GCHost.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost Coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
