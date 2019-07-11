---
title: EMemoryCriticalLevel Numaralandırması
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26b3761ab49f36c5f687ff2c62882667e044d299
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774222"
---
# <a name="ememorycriticallevel-enumeration"></a>EMemoryCriticalLevel Numaralandırması
Belirli bir bellek ayırma istendi ancak memnun olamaz, bir hatanın etkisini gösteren değerleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`eAppDomainCritical`|Ayırma ayırma istedi etki alanındaki yönetilen kodu yürütmek için kritik olduğunu gösterir. Bellek tahsis edilemiyor, CLR etki alanı hala kullanılabilir olduğunu garanti edemez. Konak ayırma getirdiğinizde hangi eylemin karar verir. CLR'nin iptal edilmemelerini sağlayabilirsiniz `AppDomain` otomatik olarak ya da üzerinde yöntemleri çağırarak çalıştırmaya devam etmesine izin [Iclrpolicymanager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).|  
|`eProcessCritical`|Ayırma işleminde yönetilen kodun yürütülmesi için önemli olduğunu gösterir. Bu değer, başlatılırken ve sonlandırıcılar çalıştırırken kullanılır. Bellek tahsis edilemiyor, CLR'nin işlemdeki çalışamaz. Ayırma başarısız olursa, CLR etkili bir şekilde devre dışı bırakıldı. CLR hata HOST_E_CLRNOTAVAILABLE ile tüm sonraki çağırıyor.|  
|`eTaskCritical`|Ayırma ayırma istediği görevi çalıştırmak için önemli olduğunu gösterir. Bellek tahsis edilemiyor, CLR görev yürütülebilecek garanti edemez. CLR hata durumunda başlatır bir <xref:System.Threading.ThreadAbortException> fiziksel işlemi sistemi iş parçacığı üzerinde.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tanımlanan bellek ayırma yöntemleri [Ihostmemorymanager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) ve [Ihostmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) arabirimler bu türde bir parametre yararlanabilir. Bir hata önem derecesi bağlı olarak, bir konak ayırma istek hemen başarısız mı, yoksa, karşılanamayacak kadar beklenecek karar verebilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRMemoryNotificationCallback Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
