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
ms.openlocfilehash: 3f6928832d822422177ebd7def142422953468a0
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274287"
---
# <a name="clrdata_il_address_map-structure"></a>CLRDATA_IL_ADDRESS_MAP Yapısı

Bir Il 'yi eşlemek için bir Il tanımlar.

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
| `ilOffset`     | Kapsanan adres aralığı için Il kayması              |
| `startAddress` | Aralığın başlangıç adresi.                        |
| `endAddress`   | Aralığın bitiş adresi.                          |
| `type`         | Verilerin türü. Bu değer şu anda kullanılmıyor |

## <a name="remarks"></a>Açıklamalar

Bu yapı çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez. Kullanmak için, yapıyı yukarıda belirtilen şekilde tanımlayın; burada `CLRDATA_ADDRESS` 64 bitlik işaretsiz bir tamsayıdır.

## <a name="requirements"></a>Gereksinimler

**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
**Üst bilgi** Yok.  
**Kitaplığı** Yok.   
**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [CLRDataSourceType numaralandırması](clrdatasourcetype-enumeration.md)
- [Hata Ayıklama](index.md)
- [Hata Ayıklama Yapıları](debugging-structures.md)
