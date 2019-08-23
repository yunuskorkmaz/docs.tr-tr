---
title: ICLRAppDomainResourceMonitor::GetCurrentCpuTime Metodu
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10245541718fd5e5f30ef6bba4ab289bcef767fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950214"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a>ICLRAppDomainResourceMonitor::GetCurrentCpuTime Metodu
Uygulama etki alanı oluşturulduğundan bu yana geçerli uygulama etki alanında yürütme sırasında tüm iş parçacıkları tarafından kullanılan toplam işlemci süresini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwAppDomainId`  
 'ndaki İstenen uygulama etki alanının KIMLIĞI.  
  
 `pMilliseconds`  
 dışı Uygulama etki alanı oluşturulduktan sonra geçerli uygulama etki alanında yürütülürken tüm iş parçacıkları tarafından kullanılan toplam işlemci zamanı işaretçisi. Bu parametre `null`olabilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|COR_E_APPDOMAINUNLOADED|Uygulama etki alanı kaldırıldı veya yok.|  
|E_FAIL|Uygulama etki alanı kaynak izleme etkin değil.<br /><br /> -veya-<br /><br /> Diğer tüm arızalar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, yönetilen <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> özelliğin yönetilmeyen eşdeğeridir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** MetaHost. h  
  
 **Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAppDomainResourceMonitor Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Uygulama Etki Alanı Kaynak İzleme](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
