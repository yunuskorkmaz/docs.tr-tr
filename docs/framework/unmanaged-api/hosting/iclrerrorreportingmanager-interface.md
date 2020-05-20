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
ms.openlocfilehash: dbe4129cf4160a1a9b31bc6f418095ea4b392d57
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617002"
---
# <a name="iclrerrorreportingmanager-interface"></a>ICLRErrorReportingManager Arabirimi
Ana bilgisayarın hata raporlaması için özel yığın dökümleri yapılandırmasına izin veren yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[BeginCustomDump Yöntemi](iclrerrorreportingmanager-begincustomdump-method.md)|Hata raporlama için özel yığın dökümlerinin yapılandırmasını belirtir.|  
|[EndCustomDump Yöntemi](iclrerrorreportingmanager-endcustomdump-method.md)|Daha önceki bir çağrısıyla ayarlanan özel yığın dökümü yapılandırmasını temizler `BeginCustomDump` .|  
|[GetBucketParametersForCurrentException Yöntemi](iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|Çağıran iş parçacığında geçerli özel durumun Watson demetini alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `BeginCustomDump`Yöntemi, özel yığın dökümü yapılandırmasını ayarlar. `EndCustomDump`Yöntemi, özel yığın dökümü yapılandırmasını temizler ve ilişkili tüm durumları serbest bırakır. Özel döküm tamamlandıktan sonra çağrılmalıdır.  
  
> [!IMPORTANT]
> Çağırma hatası, `EndCustomDump` belleğin sızmasını sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ECustomDumpItemKind Numaralandırması](ecustomdumpitemkind-enumeration.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
