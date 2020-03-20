---
title: CLRDATA_IL_ADDRESS_MAP Yapısı
ms.date: 01/16/2019
api.name:
- CLRDATA_IL_ADDRESS_MAP Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure
helpviewer.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e680a7a0dc3209d1988f6c84be0864572a74b3a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179370"
---
# <a name="clrdata_il_address_map-structure"></a>CLRDATA_IL_ADDRESS_MAP Yapısı

Adres eşleme için bir IL tanımlar.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a>Üyeler

| Üye         | Açıklama                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | İçerdiği adres aralığı için IL ofset              |
| `startAddress` | Aralığın başlangıç adresi.                        |
| `endAddress`   | Aralığın son adresi.                          |
| `type`         | Verilerin türü. Bu değer şu anda kullanılmaz |

## <a name="remarks"></a>Açıklamalar

Bu yapı çalışma zamanı içinde yaşar ve üstbilgi veya kitaplık dosyaları aracılığıyla açıklanmaz. Kullanmak için, 64 bit imzasız `CLRDATA_ADDRESS` tamsayı olduğu yapıyı yukarıda belirtildiği gibi tanımlayın.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
**Üstbilgi:** Hiçbiri  
**Kütüphane:** Yok **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [CLRDataSourceType Numaralandırma](clrdatasourcetype-enumeration.md)
- [Hata ayıklama](index.md)
- [Hata Ayıklama Yapıları](debugging-structures.md)
