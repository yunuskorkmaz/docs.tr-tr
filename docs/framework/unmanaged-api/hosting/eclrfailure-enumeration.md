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
ms.openlocfilehash: e07210203d8a8010890eeb511ff1c08821bfc4a7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616339"
---
# <a name="eclrfailure-enumeration"></a>EClrFailure Numaralandırması
Bir konağın ilke eylemlerini ayarlayabileceği başarısızlık kümesini açıklar.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
|`FAIL_NonCriticalResource`|Kritik olmayan bir kod bölgesinde bir kaynak (iş parçacığı, bir bellek bloğu veya kilit gibi) ayırma girişimi sırasında bir hata oluştu.|  
|`FAIL_CriticalResource`|Kritik kod bölgesinde bir kaynak (iş parçacığı, bir bellek bloğu veya kilit gibi) ayırma girişimi sırasında bir hata oluştu.|  
|`FAIL_FatalRuntime`|Ortak dil çalışma zamanı (CLR), işlemde yönetilen kodu artık çalıştıraamayacak. Henceileri, herhangi bir barındırma işlevlerine yapılan çağrılar HOST_E_CLRNOTAVAILABLE HRESULT değeri döndürür.|  
|`FAIL_OrphanedLock`|Bir iş parçacığı bir nesneden dönmeden bir kilidi serbest bırakmaya başarısız oldu <xref:System.AppDomain> . Konak, bir iş parçacığının iptal edilmesini sağlamak için bu hatayı ayarlayamadı.|  
|`FAIL_StackOverflow`|Yığın taşması oluştu.|  
|`FAIL_AccessViolation`|Korunan bellek okuma veya yazma girişiminde bulunuldu. .NET Framework 4 ' te desteklenmez.|  
|`FAIL_CodeContract`|Bir kod sözleşmesi hatası oluştu. Bkz. [Kod sözleşmeleri](../../debug-trace-profile/code-contracts.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 Konağın hata koşulları için ilke eylemlerini belirtmek için kullanabileceği [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) değerlerinin bir listesi Için [ICLRPolicyManager:: SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) yöntemine bakın. Kritik ve kritik olmayan kod bölgeleri hakkında daha fazla bilgi için bkz. [EClrOperation](eclroperation-enumeration.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRPolicyManager Arabirimi](iclrpolicymanager-interface.md)
- [SetActionOnFailure Yöntemi](iclrpolicymanager-setactiononfailure-method.md)
- [IHostPolicyManager Arabirimi](ihostpolicymanager-interface.md)
- [Barındırma Sabit Listeleri](hosting-enumerations.md)
