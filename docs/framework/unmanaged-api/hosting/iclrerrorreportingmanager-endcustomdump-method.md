---
description: ': ICLRErrorReportingManager:: EndCustomDump yöntemi hakkında daha fazla bilgi edinin'
title: ICLRErrorReportingManager::EndCustomDump Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.EndCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::EndCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::EndCustomDump method [.NET Framework hosting]
- EndCustomDump method [.NET Framework hosting]
ms.assetid: 88a5da04-8729-4108-82c4-af206a7d483e
topic_type:
- apiref
ms.openlocfilehash: 406d7d77f4cd63c69fec56acb0819d56c6271630
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689475"
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a>ICLRErrorReportingManager::EndCustomDump Yöntemi

Daha önceki bir çağrıda belirtilen özel yığın dökümü yapılandırmasını [ICLRErrorReportingManager:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) metoduna kaldırır.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`EndCustomDump` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 `EndCustomDump`Yöntemi, yöntemi için daha önceki bir çağrı tarafından ayarlanan özel yığın dökümü yapılandırmasını temizler `BeginCustomDump` ve ilişkili tüm durumları boşaltır. Özel yığın dökümü tamamlandıktan sonra çağrılmalıdır.  
  
> [!IMPORTANT]
> Çağırma hatası, `EndCustomDump` belleğin sızmasını sağlar.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CustomDumpItem Yapısı](customdumpitem-structure.md)
- [ECustomDumpFlavor Numaralandırması](ecustomdumpflavor-enumeration.md)
- [ICLRErrorReportingManager Arabirimi](iclrerrorreportingmanager-interface.md)
