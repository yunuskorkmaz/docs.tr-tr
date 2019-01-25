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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 635cf7c4e8ff715096728414506b4a7e683727b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704218"
---
# <a name="ebindpolicylevels-enumeration"></a>EBindPolicyLevels Numaralandırması
Derleme ilkesini uygulamak veya değiştirmek istediğiniz düzeyinde belirtmek için bayrakları sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`ePolicyLevelAdmin`|İlke yönetici düzeyinde uygulanması gerektiğini belirtir.|  
|`ePolicyLevelApp`|İlke uygulama düzeyinde uygulanması gerektiğini belirtir.|  
|`ePolicyLevelHost`|İlkenin ana bilgisayar düzeyinde geçerli olduğunu belirtir.|  
|`ePolicyLevelNone`|Hiçbir ilke düzeyi bayrakları belirtir.|  
|`ePolicyLevelPublisher`|İlke yayımcı düzeyinde uygulanması gerektiğini belirtir.|  
|`ePolicyLevelRetargetable`|İlke değişken düzeylerinde uygulanabilir olacağını belirtir.|  
|`ePolicyPortability`|.NET Framework derlemesinin uygulamaları arasındaki taşınabilir destek ilkesi belirtir. Bkz: [ \<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) yapılandırma dosyası öğesi.|  
|`ePolicyUnifiedToCLR`|İlke, ortak dil çalışma zamanı (CLR) birleşik olduğunu belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu numaralandırma yöntemlerini için geçirilen [Iclrhostbindingpolicymanager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) uygulama ilkesi değişiklikleri belirtmek için arabirim.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICLRAssemblyIdentityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
