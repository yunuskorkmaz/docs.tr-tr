---
title: CustomDumpItem Yapısı
ms.date: 03/30/2017
api_name:
- CustomDumpItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CustomDumpItem
helpviewer_keywords:
- CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type:
- apiref
ms.openlocfilehash: ae64edd8a3a628100d4c51d0b78be1bc8d49fc17
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138280"
---
# <a name="customdumpitem-structure"></a>CustomDumpItem Yapısı
Hata raporlamada özel bir döküme eklenecek bir öğe tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`itemKind`|Eklenecek öğe türünü gösteren bir [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) değeri.|  
|`pReserved`|Şu anda kullanılmıyor. Birleşime eklenen öğelerin işaretçi boyutundan büyük olmaması gerekir. Bir `struct` gerekiyorsa, bunu ayrı olarak ayırmanız ve üzerine işaret etmeniz gerekir.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ICLRErrorReportingManager:: BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) , `CustomDumpItem`türünde bir parametre alır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. IDL  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Yapıları](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
