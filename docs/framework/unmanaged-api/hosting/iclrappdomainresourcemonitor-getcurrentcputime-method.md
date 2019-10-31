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
ms.openlocfilehash: de57fec05c338e51d0691ccfa0d0bffb334848de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126792"
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
|E_FAıL|Uygulama etki alanı kaynak izleme etkin değil.<br /><br /> veya<br /><br /> Diğer tüm arızalar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, yönetilen <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> özelliğinin yönetilmeyen eşdeğeridir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAppDomainResourceMonitor Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Uygulama Etki Alanı Kaynak İzleme](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
