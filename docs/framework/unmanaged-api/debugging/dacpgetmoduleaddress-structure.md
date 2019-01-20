---
title: DacpGetModuleAddress yapısı
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress Structure
helpviewer.keywords:
- DacpGetModuleAddress Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: ca9ce04e9a4770d46f88e10785f4dafd044c9212
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416134"
---
# <a name="dacpgetmoduleaddress-structure"></a>DacpGetModuleAddress yapısı

Bir modül adresi isteği için bir kapsayıcı tanımlar.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

```
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a>Üyeler

| Üye      | Açıklama                |
| ----------- | -------------------------- |
| `ModulePtr` | Modül işaretçisi. |

## <a name="methods"></a>Yöntemler

| Yöntem                                                                                               | Açıklama                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [İstek](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-request-method.md) | Belirtilen çalışma zamanı yapısı yapısından doldurmak için bir istek gerçekleştirir. |

## <a name="remarks"></a>Açıklamalar

Bu yapı, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez. Bunu kullanmak için yapı, yukarıda belirtildiği gibi burada tanımlarsınız `CLRDATA_ADDRESS` 64-bit işaretsiz tamsayıdır.

## <a name="requirements"></a>Gereksinimler
**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
**Üst bilgi:** Hiçbiri  
**Kitaplığı:** Hiçbiri  
**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca Bkz.
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
