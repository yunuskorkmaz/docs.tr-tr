---
title: ASM_CACHE_FLAGS Numaralandırması
ms.date: 03/30/2017
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
ms.openlocfilehash: 6c6fab627f21977e85f9885ca4b49a0276faa5ce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732170"
---
# <a name="asm_cache_flags-enumeration"></a>ASM_CACHE_FLAGS Numaralandırması

Genel derleme önbelleğinde [IAssemblyCacheItem](iassemblycacheitem-interface.md) tarafından temsil edilen bir derlemenin kaynağını gösterir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|Ngen.exe kullanarak önceden derlenmiş derlemelerin önbelleğini sıralar.|  
|`ASM_CACHE_GAC`|Genel derleme önbelleğini numaralandırır.|  
|`ASM_CACHE_DOWNLOAD`|İsteğe bağlı olarak indirilen veya gölge kopyalanmış derlemeleri numaralandırır.|  
|`ASM_CACHE_ROOT`|[GetCachePath](getcachepath-function.md) işlevinin, ortak dil çalışma zamanı (CLR) sürüm 2,0 için genel derleme önbelleği yolunu döndürmesi gerektiğini gösterir. Yalnızca bir [GetCachePath](getcachepath-function.md)çağrısı bağlamında anlamlıdır.|  
|`ASM_CACHE_ROOT_EX`|[GetCachePath](getcachepath-function.md) işlevinin CLR sürüm 4 için genel derleme önbelleğinin yolunu döndürmesi gerektiğini gösterir. Yalnızca bir [GetCachePath](getcachepath-function.md)çağrısı bağlamında anlamlıdır.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetCachePath İşlevi](getcachepath-function.md)
- [IAssemblyCacheItem Arabirimi](iassemblycacheitem-interface.md)
- [Fusion Numaralandırmaları](fusion-enumerations.md)
