---
title: IHostSecurityContext Arabirimi
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
ms.openlocfilehash: f6e25bfe11880730f6f447ccc0406d716d185624
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501501"
---
# <a name="ihostsecuritycontext-interface"></a>IHostSecurityContext Arabirimi
Ortak dil çalışma zamanının (CLR) konak tarafından uygulanan güvenlik bağlamı bilgilerini korumasına olanak tanır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Description|  
|------------|-----------------|  
|[Capture Yöntemi](ihostsecuritycontext-capture-method.md)|`IHostSecurityContext` [IHostSecurityManager:: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md)çağrısından döndürülen örneğinin bir kopyasını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir konak, iş parçacığı belirteçlerine yönelik tüm kod erişimini CLR ve Kullanıcı koduna göre denetleyebilir. Ayrıca, tüm güvenlik bağlamı bilgilerinin zaman uyumsuz işlemlere veya kısıtlanmış kod erişimi olan kod noktalarına geçirilmesini de sağlayabilirsiniz. `IHostSecurityContext`çalışma zamanı için donuk olan bu güvenlik bağlamı bilgilerini kapsüller. Çalışma zamanı bu bilgileri kullanarak yakalar `Capture` ve iş parçacığı havuzu çalışan öğesi gönderimi, sonlandırıcısı yürütmesi ve modül ve sınıf oluşturucuları arasında gider.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRHostProtectionManager Arabirimi](iclrhostprotectionmanager-interface.md)
- [IHostSecurityManager Arabirimi](ihostsecuritymanager-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
