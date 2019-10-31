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
ms.openlocfilehash: 8364d38f7ab81b73fd8b47d2251bc0ff1b2c71e8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138240"
---
# <a name="ememorycriticallevel-enumeration"></a>EMemoryCriticalLevel Numaralandırması
Belirli bir bellek ayırma talep edildiğinde, ancak karşılanamaması durumunda hatanın etkisini gösteren değerleri içerir.  
  
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
|`eAppDomainCritical`|Ayırmayı isteyen etki alanında yönetilen kodu yürütmek için ayırmanın kritik olduğunu gösterir. Bellek ayrılabileceği takdirde, CLR etki alanının hala kullanılabilir olduğundan emin olamaz. Ana bilgisayar, ayırma karşılanmıyorsa hangi eylemin yapılacağını belirler. CLR 'nin `AppDomain` otomatik olarak iptal etmesini veya [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)'daki yöntemleri çağırarak çalışmaya devam etmesini sağlayabilirsiniz.|  
|`eProcessCritical`|Ayırmanın, işlemdeki yönetilen kodun yürütülmesi için kritik öneme sahip olduğunu gösterir. Bu değer başlangıç sırasında ve sonlandırıcılar çalıştırılırken kullanılır. Bellek ayrılabileceği takdirde, CLR işlemde çalışamaz. Ayırma başarısız olursa, CLR etkin bir şekilde devre dışı bırakılır. CLR 'ye yapılan tüm sonraki çağrılar HOST_E_CLRNOTAVAILABLE ile başarısız olur.|  
|`eTaskCritical`|Ayırmayı isteyen görevi çalıştırmak için ayırmanın kritik olduğunu gösterir. Bellek ayrılabileceği takdirde, CLR görevin yürütülüp yürütülabileceğini garanti edemez. Hata durumunda, CLR fiziksel işlem sistemi iş parçacığında bir <xref:System.Threading.ThreadAbortException> oluşturur.|  
  
## <a name="remarks"></a>Açıklamalar  
 [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) ve [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) arabirimlerinde tanımlanan bellek ayırma yöntemleri bu türden bir parametre alır. Bir hata önem derecesine bağlı olarak, bir ana bilgisayar, ayırma isteğinin hemen başarısız olmasına veya karşılanmayacağı kadar bekleyip bekmeyeceğine karar verebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRMemoryNotificationCallback Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
