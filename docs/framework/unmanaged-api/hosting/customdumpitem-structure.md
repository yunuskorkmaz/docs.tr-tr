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
ms.openlocfilehash: 5c77a332593ba470d2e29b87cba182a770d5db7e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616443"
---
# <a name="customdumpitem-structure"></a>CustomDumpItem Yapısı
Hata raporlamada özel bir döküme eklenecek bir öğe tanımlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
|`itemKind`|Eklenecek öğe türünü gösteren bir [ECustomDumpItemKind](ecustomdumpitemkind-enumeration.md) değeri.|  
|`pReserved`|Şu anda kullanılmıyor. Birleşime eklenen öğelerin işaretçi boyutundan büyük olmaması gerekir. Bir `struct` gerekliyse, onu ayrı olarak ayırmanız ve üzerine işaret etmeniz gerekir.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ICLRErrorReportingManager:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) türünde bir parametre alır `CustomDumpItem` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. IDL  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Yapıları](hosting-structures.md)
