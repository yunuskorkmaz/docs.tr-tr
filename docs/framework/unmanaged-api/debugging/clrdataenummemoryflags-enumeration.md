---
title: CLRDataEnumMemoryFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CLRDataEnumMemoryFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLRDataEnumMemoryFlags
helpviewer_keywords:
- CLRDataEnumMemoryFlags enumeration [.NET Framework debugging]
ms.assetid: e249f9fc-e24a-4506-903c-92781f6eab7c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67b85917be590bdba7ed3f10972ad39b731dbcdd
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274237"
---
# <a name="clrdataenummemoryflags-enumeration"></a>CLRDataEnumMemoryFlags Numaralandırması
Hangi bellek bölgelerinin [ıclrdataenummemoryregion:: EnumMemoryRegion](iclrdataenummemoryregions-enummemoryregions-method.md) yöntemine yönelik bir çağrı içermesi gerektiğini gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|Bir mini döküm, diğer bir deyişle seyrek bellek dökümü.|  
|`CLRDATA_ENUM_MEM_HEAP`|Tam bir yığın dökümü.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** ClrData. IDL, ClrData. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](debugging-enumerations.md)
