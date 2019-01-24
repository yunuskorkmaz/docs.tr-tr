---
title: ICorConfiguration Arabirimi
ms.date: 03/30/2017
api_name:
- ICorConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorConfiguration
helpviewer_keywords:
- ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d7abd6b4ca97173cfecbabf1a8b90afcf3c48a1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554185"
---
# <a name="icorconfiguration-interface"></a>ICorConfiguration Arabirimi
Ortak dil çalışma zamanı (CLR) yapılandırmak için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[AddDebuggerSpecialThread Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|Hata Ayıklama Hizmetleri için hata ayıklayıcı durduruldu sırasında yönetilen veya yönetilmeyen hata ayıklama senaryoları uygulama varken yürütme devam etmek için belirli bir iş parçacığına izin verileceğini gösterir.|  
|[SetDebuggerThreadControl Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|CLR iş parçacığı engellenir ve engeli kaldırılmış, hata ayıklama için hata ayıklama Hizmetleri çağıran bir geri arama arabirimini ayarlar.|  
|[SetGCHostControl Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|Sanal bellek sınırlarını değiştirmek için ana istemek için atık toplayıcı tarafından kullanılmak üzere geri arama arabirimini ayarlar.|  
|[SetGCThreadControl Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|Bir çöp toplama işlemi için normalde engellenecek çalışma zamanı olmayan görevler için iş parçacıklarını zamanlama için geri arama arabirimini ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost Coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
