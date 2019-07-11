---
title: EClrFailure Numaralandırması
ms.date: 03/30/2017
api_name:
- EClrFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrFailure
helpviewer_keywords:
- EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f3e39d94996f14f1ae6593b9adaa5db3ef674c5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769659"
---
# <a name="eclrfailure-enumeration"></a>EClrFailure Numaralandırması
Bir ana bilgisayar ilkesi eylemleri ayarlayabilirsiniz hataları kümesini açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`FAIL_NonCriticalResource`|Kod kritik olmayan bir bölgede (örneğin, bir iş parçacığı, bir bellek bloğu veya bir kilit) bir kaynağı ayırmak girişimi sırasında bir hata oluştu.|  
|`FAIL_CriticalResource`|Kod kritik bir bölgede (örneğin, bir iş parçacığı, bir bellek bloğu veya bir kilit) bir kaynağı ayırmak girişimi sırasında bir hata oluştu.|  
|`FAIL_FatalRuntime`|Ortak dil çalışma zamanı (CLR) artık yönetilen kod işlemde çalışan mümkün değildir. Henceforth, herhangi bir barındırma işlevleri çağrıları HOST_E_CLRNOTAVAILABLE bir HRESULT değerini döndürür.|  
|`FAIL_OrphanedLock`|Bir iş parçacığı döndürme bağlı bir kilidi serbest bırakmak başarısız bir <xref:System.AppDomain> nesne. Konak bu hatanın neden iptal etmek için bir iş parçacığı ayarlanamıyor.|  
|`FAIL_StackOverflow`|Bir yığın taşması oluştu.|  
|`FAIL_AccessViolation`|Okuma veya yazma korumalı bellek girişimde bulunuldu. .NET Framework 4'te desteklenmez.|  
|`FAIL_CodeContract`|Bir kod sözleşmesi hata oluştu. Bkz: [kod sözleşmeleri](../../../../docs/framework/debug-trace-profile/code-contracts.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 Bkz: [Iclrpolicymanager::setactiononfailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) yöntemi bir listesi için [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) değerleri konak hata koşulları için ilke eylemleri belirtmek için kullanabilirsiniz. Kod kritik ve kritik olmayan bölgeleri hakkında daha fazla bilgi için bkz. [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [SetActionOnFailure Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)
- [IHostPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
