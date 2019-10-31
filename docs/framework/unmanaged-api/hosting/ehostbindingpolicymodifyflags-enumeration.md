---
title: EHostBindingPolicyModifyFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- EHostBindingPolicyModifyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EHostBindingPolicyModifyFlags
helpviewer_keywords:
- EHostBindingPolicyModifyFlags enumeration [.NET Framework hosting]
ms.assetid: 0339af16-ee1d-48ec-837d-a79d9a9c89f8
topic_type:
- apiref
ms.openlocfilehash: a2faf22b48dd0b809d6c3668a37f2119733a9b18
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129444"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a>EHostBindingPolicyModifyFlags Numaralandırması
Ana bilgisayarın bir kaynak derlemeden hedef derlemeye ilke değişiklikleri uygularken gerçekleştirmesi gereken ortak dil çalışma zamanının (CLR) yeniden yönlendirme türünü belirtmesini sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|CLR 'nin, kaynak derlemenin ilke değerlerini hedef derlemeye göre zincirlemesini belirtir.|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|CLR 'nin varsayılan eylemi gerçekleştireceğini belirtir.|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|CLR 'nin hedef derlemenin ilke değerlerini en fazla değere ayarlayacaksınız.|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|CLR 'nin hedef derlemenin ilke değerlerini kaynak derlemeden değiştirecek şekilde değiştirmesini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ICLRHostBindingPolicyManager:: ModifyApplicationPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) yöntemi `EHostBindingPolicyModifyFlags`türünde bir parametre alır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRHostBindingPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
