---
title: ICLRAppDomainResourceMonitor Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor
helpviewer_keywords:
- ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type:
- apiref
ms.openlocfilehash: 84c53f0666d0e04b898e28c1d8e146eab566ca1b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674703"
---
# <a name="iclrappdomainresourcemonitor-interface"></a>ICLRAppDomainResourceMonitor Arabirimi

Bir uygulama etki alanının belleğini ve CPU kullanımını denetleyen yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetCurrentAllocated Yöntemi](iclrappdomainresourcemonitor-getcurrentallocated-method.md)|, Atık olarak toplanmış olan belleği çıkarmadan, uygulama etki alanı tarafından yapılan tüm bellek ayırmalarının bayt cinsinden toplam boyutunu alır.|  
|[GetCurrentSurvived Yöntemi](iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|Son tam ve çöp toplamayı engelleyen ve geçerli uygulama etki alanı tarafından başvurulan bayt sayısını alır.|  
|[GetCurrentCpuTime Yöntemi](iclrappdomainresourcemonitor-getcurrentcputime-method.md)|Uygulama etki alanı oluşturulduğundan bu yana geçerli uygulama etki alanında yürütme sırasında tüm iş parçacıkları tarafından kullanılan toplam işlemci süresini alır.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ICLRAppDomainResourceMonitor`Arabirimi, aşağıdaki yönetilen özelliklere benzer işlevler sağlar:  
  
- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<appDomainResourceMonitoring> Dosyalarında](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [Uygulama etki alanı kaynak Izleme](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
- [Hosting](index.md)
