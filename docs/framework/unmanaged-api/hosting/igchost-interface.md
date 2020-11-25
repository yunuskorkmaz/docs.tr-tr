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
ms.openlocfilehash: 8965797321e68443c01d05f97d147f2320a76739
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724305"
---
# <a name="igchost-interface"></a>IGCHost Arabirimi

Çöp toplama sistemi hakkında bilgi edinmek ve çöp toplamanın bazı yönlerini denetlemek için yöntemler sağlar.  
  
> [!NOTE]
> 4,5 .NET Framework başlayarak, [IGCHost2:: SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) yöntemini kullanarak bir çöp toplama kesiminin boyutunu ve çöp toplama sisteminin en büyük boyutunu `DWORD` [SetGCStartupLimits](igchost-setgcstartuplimits-method.md) yöntemi tarafından uygulanan sınırdan daha büyük değerlere ayarlayabilirsiniz.  
  
> [!NOTE]
> Bu arabirim yalnızca uzman kullanımı içindir. Yanlış kullanılırsa, bir uygulamanın performansını etkileyebilir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Collect Yöntemi](igchost-collect-method.md)|Geçerli çöp toplamanın durumundan bağımsız olarak, belirli bir oluşturma için bir koleksiyonu meydana gelecek şekilde zorlar.|  
|[GetStats Metodu](igchost-getstats-method.md)|Çöp toplama sisteminin geçerli durumunun istatistiklerini alır.|  
|[GetThreadStats Yöntemi](igchost-getthreadstats-method.md)|Çöp toplama için iş parçacığı başına istatistikleri alır.|  
|[SetGCStartupLimits Yöntemi](igchost-setgcstartuplimits-method.md)|Oluşturma 0 ' nın segment boyutunu ve en büyük boyutunu ayarlar.|  
|[SetVirtualMemLimit Yöntemi](igchost-setvirtualmemlimit-method.md)|Çalışma zamanının sanal belleğinin en büyük boyutunu ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** GCHost. IDL, GCHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Arabirimleri](hosting-interfaces.md)
- [CorRuntimeHost Ortak Sınıfı](corruntimehost-coclass.md)
