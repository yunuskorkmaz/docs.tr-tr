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
ms.openlocfilehash: bf9e04ed1d3a68fed120c4c13ad992af1f777244
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433802"
---
# <a name="iclrerrorreportingmanager-interface"></a>ICLRErrorReportingManager Arabirimi
Hata bildirimi için özel yığın dökümleri yapılandırmak konak izin yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[BeginCustomDump Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|Hata bildirimi için özel yığın dökümleri yapılandırılmasını belirtir.|  
|[EndCustomDump Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|Önceki bir çağrı tarafından ayarlanan özel yığın dökümü yapılandırması temizler `BeginCustomDump`.|  
|[GetBucketParametersForCurrentException Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|Geçerli özel durumun çağıran iş parçacığı üzerinde Watson demet alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `BeginCustomDump` Yöntemi özel yığın dökümü yapılandırmasını ayarlar. `EndCustomDump` Yöntemi özel yığın dökümü yapılandırması temizler ve tüm ilişkili durumu boşaltır. Özel döküm tamamlandıktan sonra çağrılmalıdır.  
  
> [!IMPORTANT]
>  Çağrılacak hatası `EndCustomDump` bellek sızıntısı neden olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ECustomDumpItemKind Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
