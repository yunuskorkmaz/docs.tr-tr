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
ms.openlocfilehash: a2850add9acb2f7c5297ac6956e349c9277be291
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122804"
---
# <a name="dacprejitdata-structure"></a>DacpReJitData Yapısı

Belirli bir profil oluşturucu izleme eklenmiş yöntemi ile ilgili temel bilgileri tanımlar.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

```
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
| `rejitID`        | Bir yöntem için ReJit düzeltme numarası.                                                          |
| `flags`          | Belirtilen sürüm için yöntemin ReJit izleme geçerli durumunu belirten bir bayrak. |
| `NativeCodeAddr` | Yöntemin rejitted uygulamasının temel adres.                                         |

## <a name="remarks"></a>Açıklamalar

Bu yapı, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez. Bunu kullanmak için yukarıda belirtildiği gibi yapısını tanımlar. Yapı kullanarak da tanımlanmalıdır `ms_struct` Microsoft derleyicileri kullanarak değilse paketleme.

## <a name="requirements"></a>Gereksinimler
**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
**Üst bilgi:** Yok.  
**Kitaplığı:** Yok.  
**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
