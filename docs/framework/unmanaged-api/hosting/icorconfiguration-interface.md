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
ms.openlocfilehash: 80bb68486e555d6c96cf8ee56ed6d60e41c7c5c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127810"
---
# <a name="icorconfiguration-interface"></a>ICorConfiguration Arabirimi
Ortak dil çalışma zamanını (CLR) yapılandırmak için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[AddDebuggerSpecialThread Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|Hata ayıklayıcı yönetilen veya yönetilmeyen hata ayıklama senaryolarında durdurulan bir uygulamaya sahip olsa da, belirli bir iş parçacığının yürütmeye devam etmesine izin verilmesi gerektiğini hata ayıklama hizmetlerine bildirir.|  
|[SetDebuggerThreadControl Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|Hata ayıklama Hizmetleri, CLR iş parçacıkları engellenen ve hata ayıklama için engellenmemiş olarak çağralacak geri arama arabirimini ayarlar.|  
|[SetGCHostControl Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|Sanal bellek sınırlarını değiştirmek üzere Konağı istemek için çöp toplayıcı tarafından kullanılacak geri çağırma arabirimini ayarlar.|  
|[SetGCThreadControl Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|Bir çöp toplama işlemi için engellenmeyen çalışma zamanı olmayan görevler için iş parçacıkları zamanlama için geri çağırma arabirimini ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost Coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
