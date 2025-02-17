---
description: 'Daha fazla bilgi edinin: Ememorykritiklevel numaralandırması'
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
ms.openlocfilehash: 88965a29164de1ec7b01c2fcc8f51415127e69fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785438"
---
# <a name="ememorycriticallevel-enumeration"></a>EMemoryCriticalLevel Numaralandırması

Belirli bir bellek ayırma talep edildiğinde, ancak karşılanamaması durumunda hatanın etkisini gösteren değerleri içerir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`eAppDomainCritical`|Ayırmayı isteyen etki alanında yönetilen kodu yürütmek için ayırmanın kritik olduğunu gösterir. Bellek ayrılabileceği takdirde, CLR etki alanının hala kullanılabilir olduğundan emin olamaz. Ana bilgisayar, ayırma karşılanmıyorsa hangi eylemin yapılacağını belirler. CLR 'nin `AppDomain` otomatik olarak iptal etmesini veya [ICLRPolicyManager](iclrpolicymanager-interface.md)'daki yöntemleri çağırarak çalışmaya devam etmesini sağlayabilirsiniz.|  
|`eProcessCritical`|Ayırmanın, işlemdeki yönetilen kodun yürütülmesi için kritik öneme sahip olduğunu gösterir. Bu değer başlangıç sırasında ve sonlandırıcılar çalıştırılırken kullanılır. Bellek ayrılabileceği takdirde, CLR işlemde çalışamaz. Ayırma başarısız olursa, CLR etkin bir şekilde devre dışı bırakılır. CLR 'ye yapılan tüm sonraki çağrılar HOST_E_CLRNOTAVAILABLE ile başarısız olur.|  
|`eTaskCritical`|Ayırmayı isteyen görevi çalıştırmak için ayırmanın kritik olduğunu gösterir. Bellek ayrılabileceği takdirde, CLR görevin yürütülüp yürütülabileceğini garanti edemez. Hata durumunda, CLR <xref:System.Threading.ThreadAbortException> fiziksel işlem sistemi iş parçacığı üzerinde bir oluşturur.|  
  
## <a name="remarks"></a>Açıklamalar  

 [IHostMemoryManager](ihostmemorymanager-interface.md) ve [IHostMAlloc](ihostmalloc-interface.md) arabirimlerinde tanımlanan bellek ayırma yöntemleri bu türden bir parametre alır. Bir hata önem derecesine bağlı olarak, bir ana bilgisayar, ayırma isteğinin hemen başarısız olmasına veya karşılanmayacağı kadar bekleyip bekmeyeceğine karar verebilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRMemoryNotificationCallback Arabirimi](iclrmemorynotificationcallback-interface.md)
- [Barındırma Numaralandırmaları](hosting-enumerations.md)
