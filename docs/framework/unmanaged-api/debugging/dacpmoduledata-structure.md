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
ms.openlocfilehash: 2e27082ba4c35bc10eb65139b2af6c81c10d79a6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739128"
---
# <a name="dacpmoduledata-structure"></a>DacpModuleData Yapısı

Bir modülün çalışma zamanı bilgileri için transport arabellek tanımlar.

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
| `Address` | Modülü nesnesi adresi.                                           |
| `File`    | Taşınabilir yürütülebilir (PE) dosyası için bir işaretçi.                       |
| `ilBase`  | Yüklenen görüntü adresini temel.                                 |
| `payLoad` | Çalışma zamanı tarafından kullanılan modül ek bilgi için yükü arabellek. |

## <a name="remarks"></a>Açıklamalar

Bu yapı, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez. Bunu kullanmak için yukarıda belirtildiği gibi yapısını tanımlar.

## <a name="requirements"></a>Gereksinimler
**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
**Üst bilgi:** None  
**Kitaplığı:** Yok.  
**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
