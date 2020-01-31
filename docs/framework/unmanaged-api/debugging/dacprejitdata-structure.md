---
title: DacpReJitData Yapısı
ms.date: 02/01/2019
api.name:
- DacpReJitData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpReJitData Structure
helpviewer.keywords:
- DacpReJitData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 46031f29da6916eeaeea863ebef6924a720d7155
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793824"
---
# <a name="dacprejitdata-structure"></a>DacpReJitData Yapısı

Belirli bir profil oluşturucu tarafından işaretlenmiş yöntem hakkında temel bilgileri tanımlar.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
struct MSLAYOUT DacpReJitData
{
    enum Flags
    {
        kUnknown,
        kRequested,
        kActive,
        kReverted,
    };

    CLRDATA_ADDRESS                 rejitID;
    Flags                           flags;
    CLRDATA_ADDRESS                 NativeCodeAddr;
};
```

## <a name="members"></a>Üyeler

| Üye           | Açıklama                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | Bir yöntem için ReJIT düzeltme numarası.                                                          |
| `flags`          | Metodun verilen sürüm için yeniden JIT araçlarının geçerli durumunu belirten bayrak. |
| `NativeCodeAddr` | Metodun yeniden derlenen uygulamasının temel adresi.                                         |

## <a name="remarks"></a>Açıklamalar

Bu yapı çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez. Kullanmak için, yapıyı yukarıda belirtilen şekilde tanımlayın. Yapının ayrıca Microsoft derleyicileri yoksa `ms_struct` paketleme kullanılarak tanımlanması gerekir.

## <a name="requirements"></a>Gereksinimler
**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
**Üst bilgi:** Seçim  
**Kitaplık:** Seçim  
**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [Hata Ayıklama Yapıları](debugging-structures.md)
