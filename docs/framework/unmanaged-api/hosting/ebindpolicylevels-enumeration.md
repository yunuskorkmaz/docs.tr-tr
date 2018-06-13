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
ms.openlocfilehash: 1da1d368725ab0a2334080c1caa7d4e25f5f3bab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431129"
---
# <a name="ebindpolicylevels-enumeration"></a>EBindPolicyLevels Numaralandırması
Derleme ilkesini uygulamak veya değiştirmek için düzeyinde belirtmek için bayrakları sağlar.  
  
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
|`ePolicyLevelAdmin`|İlke Yöneticisi düzeyinde geçerli olduğunu belirtir.|  
|`ePolicyLevelApp`|İlke uygulama düzeyinde uygulanması gerektiğini belirtir.|  
|`ePolicyLevelHost`|İlke ana bilgisayar düzeyinde uygulanması gerektiğini belirtir.|  
|`ePolicyLevelNone`|Hiçbir ilke düzeyi bayrakları belirtir.|  
|`ePolicyLevelPublisher`|İlkenin yayımcı düzeyinde geçerli olduğunu belirtir.|  
|`ePolicyLevelRetargetable`|İlke değişken düzeylerinde uygulanabilir olması gerektiğini belirtir.|  
|`ePolicyPortability`|İlke .NET Framework derlemesinin uygulamaları arasındaki taşınabilirlik desteklemelidir belirtir. Bkz: [ \<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) yapılandırma dosyası öğesi.|  
|`ePolicyUnifiedToCLR`|İlke, ortak dil çalışma zamanı (CLR) birleşik olduğunu belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu numaralandırma yöntemlere iletilen [Iclrhostbindingpolicymanager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) uygulama ilkesi değişiklikleri belirtmek için arabirim.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRAssemblyIdentityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
