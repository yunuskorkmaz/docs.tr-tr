---
title: DacpModuleData Yapısı
ms.date: 02/01/2019
api.name:
- DacpModuleData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpModuleData Structure
helpviewer.keywords:
- DacpModuleData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 5d27ba2de9ff6ed184b6ddf50a517d0dae7715f5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723057"
---
# <a name="dacpmoduledata-structure"></a>DacpModuleData Yapısı

Modülün çalışma zamanı bilgileri için bir aktarım arabelleği tanımlar.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntax

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File;
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a>Üyeler

| Üye    | Açıklama                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | Modül nesnesinin adresi.                                           |
| `File`    | Taşınabilir çalıştırılabilir (PE) dosyasına yönelik bir işaretçi.                       |
| `ilBase`  | Yüklenen görüntünün tabanının adresi.                                 |
| `payLoad` | Çalışma zamanı tarafından kullanılan ek modül bilgileri için yük arabelleği. |

## <a name="remarks"></a>Açıklamalar

Bu yapı çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez. Kullanmak için, yapıyı yukarıda belirtilen şekilde tanımlayın.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
**Üst bilgi:** Seçim  
**Kitaplık:** Seçim  
**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [Hata Ayıklama Yapıları](debugging-structures.md)
