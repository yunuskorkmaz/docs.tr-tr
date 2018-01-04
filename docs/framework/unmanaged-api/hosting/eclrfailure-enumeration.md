---
title: "EClrFailure Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrFailure
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrFailure
helpviewer_keywords: EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e25a5378349dd476321765bb085db958e29670e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="eclrfailure-enumeration"></a>EClrFailure Numaralandırması
Bir ana bilgisayar ilkesi eylemleri ayarlayabilirsiniz hataları açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|Kod kritik olmayan bir bölgede bir kaynak (örneğin, bir iş parçacığı, bir bellek bloğu veya kilit) tahsis girişimi sırasında hata oluştu.|  
|`FAIL_CriticalResource`|Kod kritik bir bölgede bir kaynak (örneğin, bir iş parçacığı, bir bellek bloğu veya kilit) tahsis girişimi sırasında hata oluştu.|  
|`FAIL_FatalRuntime`|Ortak dil çalışma zamanı (CLR) artık işleminde yönetilen kod çalıştırabilir. Henceforth, barındırma hiçbir işlev çağrıları HOST_E_CLRNOTAVAILABLE HRESULT değerini döndürür.|  
|`FAIL_OrphanedLock`|Bir iş parçacığı döndürme bağlı bir kilidi serbest bırakmak başarısız oldu bir <xref:System.AppDomain> nesnesi. Ana bilgisayar iptal etmek bir iş parçacığı neden bu hatanın ayarlanamıyor.|  
|`FAIL_StackOverflow`|Bir yığın taşması oluştu.|  
|`FAIL_AccessViolation`|Okuma veya yazma korumalı bellek için girişimde bulunuldu. İçinde desteklenmez [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].|  
|`FAIL_CodeContract`|Kodu sözleşme hatası oluştu. Bkz: [kod sözleşmeleri](../../../../docs/framework/debug-trace-profile/code-contracts.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 Bkz: [Iclrpolicymanager::setactiononfailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) yöntemi listesini görmek için [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) değerleri konak hata koşulları için ilke eylemleri belirtmek için kullanabilirsiniz. Kod kritik ve kritik olmayan bölgeleri hakkında daha fazla bilgi için bkz: [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [SetActionOnFailure Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)  
 [IHostPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
