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
ms.openlocfilehash: ec64f9bec0ee9b63796958b17c7f10b87692f1d0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686156"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a>EHostBindingPolicyModifyFlags Numaralandırması

Ana bilgisayarın bir kaynak derlemeden hedef derlemeye ilke değişiklikleri uygularken gerçekleştirmesi gereken ortak dil çalışma zamanının (CLR) yeniden yönlendirme türünü belirtmesini sağlar.  
  
## <a name="syntax"></a>Syntax  
  
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

 [ICLRHostBindingPolicyManager:: ModifyApplicationPolicy](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) yöntemi türünde bir parametre alır `EHostBindingPolicyModifyFlags` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRHostBindingPolicyManager Arabirimi](iclrhostbindingpolicymanager-interface.md)
- [Barındırma Numaralandırmaları](hosting-enumerations.md)
