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
ms.openlocfilehash: e10d1792a8dc0b57ddd121ec09854e8e1824cade
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860808"
---
# <a name="dacpmoduledata-structure"></a>DacpModuleData Yapısı

Modülün çalışma zamanı bilgileri için bir aktarım arabelleği tanımlar.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

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
