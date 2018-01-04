---
title: "EBindPolicyLevels Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EBindPolicyLevels
api_location: mscoree.dll
api_type: COM
f1_keywords: EBindPolicyLevels
helpviewer_keywords: EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 52e4d4522c7401aba198deed7853ccca71752d83
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRAssemblyIdentityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
