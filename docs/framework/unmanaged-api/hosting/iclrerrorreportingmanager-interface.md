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
ms.openlocfilehash: d3816c8a3b6204b053505aa888eb28d696f8990b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677855"
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
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ECustomDumpItemKind Numaralandırması](ecustomdumpitemkind-enumeration.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
