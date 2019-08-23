---
title: ICLRErrorReportingManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager
helpviewer_keywords:
- ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a9d9cff0360e4eb27584fe0f22c1c20396ff8f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966254"
---
# <a name="iclrerrorreportingmanager-interface"></a>ICLRErrorReportingManager Arabirimi
Ana bilgisayarın hata raporlaması için özel yığın dökümleri yapılandırmasına izin veren yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[BeginCustomDump Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|Hata raporlama için özel yığın dökümlerinin yapılandırmasını belirtir.|  
|[EndCustomDump Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|Daha önceki bir çağrısıyla `BeginCustomDump`ayarlanan özel yığın dökümü yapılandırmasını temizler.|  
|[GetBucketParametersForCurrentException Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|Çağıran iş parçacığında geçerli özel durumun Watson demetini alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntemi `BeginCustomDump` , özel yığın dökümü yapılandırmasını ayarlar. `EndCustomDump` Yöntemi, özel yığın dökümü yapılandırmasını temizler ve ilişkili tüm durumları serbest bırakır. Özel döküm tamamlandıktan sonra çağrılmalıdır.  
  
> [!IMPORTANT]
> Çağırma `EndCustomDump` hatası, belleğin sızmasını sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** MSCorEE. h  
  
 **Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ECustomDumpItemKind Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
