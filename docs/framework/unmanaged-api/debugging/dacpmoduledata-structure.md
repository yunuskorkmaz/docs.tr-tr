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
ms.openlocfilehash: c24bdce64eb7e208bf3830940d7beab1ebf92e78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179196"
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
| `File`    | Taşınabilir yürütülebilir (PE) dosyasına işaretçi.                       |
| `ilBase`  | Yüklenen görüntütabanının adresi.                                 |
| `payLoad` | Çalışma zamanı tarafından kullanılan ek modül bilgileri için bir yük arabelleği. |

## <a name="remarks"></a>Açıklamalar

Bu yapı çalışma zamanı içinde yaşar ve üstbilgi veya kitaplık dosyaları aracılığıyla açıklanmaz. Kullanmak için, yapıyı yukarıda belirtildiği gibi tanımlayın.

## <a name="requirements"></a>Gereksinimler
**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
**Üstbilgi:** Hiçbiri  
**Kütüphane:** Hiçbiri  
**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama](index.md)
- [Hata Ayıklama Yapıları](debugging-structures.md)
