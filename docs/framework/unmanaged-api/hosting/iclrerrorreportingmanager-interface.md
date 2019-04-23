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
ms.openlocfilehash: a20b79dd5eda9c431511cc49e7e3adaa9486b2aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59155993"
---
# <a name="iclrerrorreportingmanager-interface"></a>ICLRErrorReportingManager Arabirimi
Özel yığının dökümlerinde hata raporlama yapılandırmak konak izin vermek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[BeginCustomDump Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|Hata bildirimi için özel bir yığın dökümlerini yapılandırmasını belirtir.|  
|[EndCustomDump Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|Önceki bir çağrı tarafından ayarlanan özel yığının döküm yapılandırmasını temizler `BeginCustomDump`.|  
|[GetBucketParametersForCurrentException Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|Watson demet çağıran iş parçacığında geçerli özel durumu alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `BeginCustomDump` Yöntemi özel yığının döküm yapılandırmasını ayarlar. `EndCustomDump` Yöntemi özel yığının döküm yapılandırmasını temizler ve herhangi bir ilişkili durumu serbest bırakır. Özel döküm tamamlandıktan sonra çağrılmalıdır.  
  
> [!IMPORTANT]
>  Aranacak hata `EndCustomDump` bellek sızıntısı neden olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ECustomDumpItemKind Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
