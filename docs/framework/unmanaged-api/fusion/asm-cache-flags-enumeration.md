---
title: "ASM_CACHE_FLAGS Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ASM_CACHE_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CACHE_FLAGS
helpviewer_keywords:
- ASM_CACHE_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 82e9a7da-321b-48b8-b239-52eaffda6be8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 87dce9a2daf7067409d78a9f389695b6b01f23c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="asmcacheflags-enumeration"></a>ASM_CACHE_FLAGS Numaralandırması
Tarafından temsil edilen bir derleme kaynağını gösterir [Iassemblycacheıtem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) genel derleme önbelleğinde.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|Önceden derlenmiş derlemeleri önbelleğini Ngen.exe kullanarak sıralar.|  
|`ASM_CACHE_GAC`|Genel Derleme Önbelleği numaralandırır.|  
|`ASM_CACHE_DOWNLOAD`|İsteğe bağlı olarak indirilebilir veya gölge kopyalar silinmiş derlemeleri numaralandırır.|  
|`ASM_CACHE_ROOT`|Belirten [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) işlevi, ortak dil çalışma zamanı (CLR) sürüm 2.0 için genel derleme önbelleğine yolu döndürmelidir. Yalnızca bir çağrı bağlamında anlamlı [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).|  
|`ASM_CACHE_ROOT_EX`|Belirten [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) işlevi döndürmelidir yolu genel derleme önbelleğine CLR sürüm 4. Yalnızca bir çağrı bağlamında anlamlı [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Fusion.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [GetCachePath İşlevi](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 [IAssemblyCacheItem Arabirimi](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)  
 [Fusion Sabit Listeleri](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
