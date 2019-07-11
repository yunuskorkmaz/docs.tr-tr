---
title: CLRDATA_ADDRESS_RANGE Yapısı
ms.date: 01/16/2019
api.name:
- CLRDATA_ADDRESS_RANGE Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_ADDRESS_RANGE Structure
helpviewer.keywords:
- CLRDATA_ADDRESS_RANGE Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: afcb4e642c9b54107423f7474771fdc28cde709e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741021"
---
# <a name="clrdataaddressrange-structure"></a>CLRDATA_ADDRESS_RANGE Yapısı

Bir adres aralığı tanımlar.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
typedef struct
{
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
} CLRDATA_ADDRESS_RANGE;
```

## <a name="members"></a>Üyeler

| Üye         | Açıklama                     |
| -------------- | ------------------------------- |
| `startAddress` | Aralığın başlangıç adresi. |
| `endAddress`   | Aralığın bitiş adresi.   |

## <a name="remarks"></a>Açıklamalar

Bu yapı, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez. Bunu kullanmak için yapı, yukarıda belirtildiği gibi burada tanımlarsınız `CLRDATA_ADDRESS` 64-bit işaretsiz tamsayıdır.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
**Üst bilgi:** Yok.  
**Kitaplığı:** None  
**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
