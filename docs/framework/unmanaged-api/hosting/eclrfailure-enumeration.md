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
ms.openlocfilehash: fa2b5052a1d569487f0c6c72699ff9ab571beefc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504400"
---
# <a name="eclrfailure-enumeration"></a>EClrFailure Numaralandırması
Bir konağın ilke eylemlerini ayarlayabileceği başarısızlık kümesini açıklar.  
  
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
  
|Üye|Description|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|Kritik olmayan bir kod bölgesinde bir kaynak (iş parçacığı, bir bellek bloğu veya kilit gibi) ayırma girişimi sırasında bir hata oluştu.|  
|`FAIL_CriticalResource`|Kritik kod bölgesinde bir kaynak (iş parçacığı, bir bellek bloğu veya kilit gibi) ayırma girişimi sırasında bir hata oluştu.|  
|`FAIL_FatalRuntime`|Ortak dil çalışma zamanı (CLR), işlemde yönetilen kodu artık çalıştıraamayacak. Henceileri, herhangi bir barındırma işlevlerine yapılan çağrılar HOST_E_CLRNOTAVAILABLE HRESULT değeri döndürür.|  
|`FAIL_OrphanedLock`|Bir iş parçacığı bir nesneden dönmeden bir kilidi serbest bırakmaya başarısız oldu <xref:System.AppDomain> . Konak, bir iş parçacığının iptal edilmesini sağlamak için bu hatayı ayarlayamadı.|  
|`FAIL_StackOverflow`|Yığın taşması oluştu.|  
|`FAIL_AccessViolation`|Korunan bellek okuma veya yazma girişiminde bulunuldu. .NET Framework 4 ' te desteklenmez.|  
|`FAIL_CodeContract`|Bir kod sözleşmesi hatası oluştu. Bkz. [Kod sözleşmeleri](../../debug-trace-profile/code-contracts.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 Konağın hata koşulları için ilke eylemlerini belirtmek için kullanabileceği [EPolicyAction](epolicyaction-enumeration.md) değerlerinin bir listesi Için [ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) yöntemine bakın. Kritik ve kritik olmayan kod bölgeleri hakkında daha fazla bilgi için bkz. [EClrOperation](eclroperation-enumeration.md).  
  
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
