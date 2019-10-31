---
title: EBindPolicyLevels Numaralandırması
ms.date: 03/30/2017
api_name:
- EBindPolicyLevels
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EBindPolicyLevels
helpviewer_keywords:
- EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type:
- apiref
ms.openlocfilehash: 81aef6beb9ee6d622519738d24fdd0a4d42a75b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136558"
---
# <a name="ebindpolicylevels-enumeration"></a>EBindPolicyLevels Numaralandırması
Derleme ilkesini uygulamak veya değiştirmek için kullanılacak düzeyi belirleyen bayraklar sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|İlkenin yönetici düzeyinde uygulanması gerektiğini belirtir.|  
|`ePolicyLevelApp`|Bu ilkenin uygulama düzeyinde uygulanması gerektiğini belirtir.|  
|`ePolicyLevelHost`|İlkenin ana bilgisayar düzeyinde uygulanması gerektiğini belirtir.|  
|`ePolicyLevelNone`|İlke düzeyindeki bayrakları belirtir.|  
|`ePolicyLevelPublisher`|İlkenin yayımcı düzeyinde uygulanması gerektiğini belirtir.|  
|`ePolicyLevelRetargetable`|İlkenin değişken düzeylerinde geçerli olması gerektiğini belirtir.|  
|`ePolicyPortability`|İlkenin .NET Framework bütünleştirilmiş kod uygulamaları arasında taşınabilirliği desteklemesi gerektiğini belirtir. [\<Supporttaşınabilirlik >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) yapılandırma dosyası öğesi ' ne bakın.|  
|`ePolicyUnifiedToCLR`|İlkenin ortak dil çalışma zamanı (CLR) ile birleştirilmiş olması gerektiğini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu numaralandırma, uygulama ilkesindeki değişiklikleri belirtmek için [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) arabiriminin yöntemlerine geçirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyIdentityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
