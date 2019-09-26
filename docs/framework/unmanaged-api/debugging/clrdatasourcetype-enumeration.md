---
title: CLRDataSourceType numaralandırması
ms.date: 01/16/2019
api.name:
- CLRDataSourceType Enumeration
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDataSourceType Enumeration
helpviewer.keywords:
- CLRDataSourceType Enumeration [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 7ace405e2624f15b1cdb6d383222ae87c93289bb
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274102"
---
# <a name="clrdatasourcetype-enumeration"></a>CLRDataSourceType numaralandırması

CLRDATA_IL_ADDRESS_MAP yapısı tarafından kullanılan değerleri sağlar.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a>Üyeler

| Üye                        | Açıklama                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | Başka hiçbir şeyin uygulanacağını belirtmek için |

## <a name="remarks"></a>Açıklamalar

Bu numaralandırma çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez. Kullanmak için, kodunuzda yukarıda tanımlanan bir sabit listesi tanımlayın. Bu, `CLRDATA_ENUM` [ortak veri türlerinde](../common-data-types-unmanaged-api-reference.md)bahsedildiği gibi, için de başka bir ad sağlar.

## <a name="requirements"></a>Gereksinimler

**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
**Üst bilgi** Yok.  
**Kitaplığı** Yok.  
**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [Hata Ayıklama Sabit Listeleri](debugging-enumerations.md)
