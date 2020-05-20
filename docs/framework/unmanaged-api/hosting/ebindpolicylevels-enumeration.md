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
ms.openlocfilehash: 94d2ec12309249afbecdc4130f8fe20c927b0a9b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616378"
---
# <a name="ebindpolicylevels-enumeration"></a>EBindPolicyLevels Numaralandırması
Derleme ilkesini uygulamak veya değiştirmek için kullanılacak düzeyi belirleyen bayraklar sağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
|`ePolicyPortability`|İlkenin .NET Framework bütünleştirilmiş kod uygulamaları arasında taşınabilirliği desteklemesi gerektiğini belirtir. Bkz. [ \< supporttaşınabilirlik>](../../configure-apps/file-schema/runtime/supportportability-element.md) yapılandırma dosyası öğesi.|  
|`ePolicyUnifiedToCLR`|İlkenin ortak dil çalışma zamanı (CLR) ile birleştirilmiş olması gerektiğini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu numaralandırma, uygulama ilkesindeki değişiklikleri belirtmek için [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) arabiriminin yöntemlerine geçirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyIdentityManager Arabirimi](iclrassemblyidentitymanager-interface.md)
- [Barındırma Sabit Listeleri](hosting-enumerations.md)
