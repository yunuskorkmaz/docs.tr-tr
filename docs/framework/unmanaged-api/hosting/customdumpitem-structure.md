---
description: 'Daha fazla bilgi edinin: CustomDumpItem yapısı'
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
ms.openlocfilehash: 9bd7b2bb59675bc01e24dc6e6d0ce524f3d35466
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716906"
---
# <a name="customdumpitem-structure"></a>CustomDumpItem Yapısı

Hata raporlamada özel bir döküme eklenecek bir öğe tanımlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`itemKind`|Eklenecek öğe türünü gösteren bir [ECustomDumpItemKind](ecustomdumpitemkind-enumeration.md) değeri.|  
|`pReserved`|Şu anda kullanılmıyor. Birleşime eklenen öğelerin işaretçi boyutundan büyük olmaması gerekir. Bir `struct` gerekliyse, onu ayrı olarak ayırmanız ve üzerine işaret etmeniz gerekir.|  
  
## <a name="remarks"></a>Açıklamalar  

 [ICLRErrorReportingManager:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) türünde bir parametre alır `CustomDumpItem` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. IDL  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Yapıları](hosting-structures.md)
