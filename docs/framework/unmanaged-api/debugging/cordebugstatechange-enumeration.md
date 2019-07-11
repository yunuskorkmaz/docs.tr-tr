---
title: CorDebugStateChange Numaralandırması
ms.date: 02/07/2019
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 676489880cb30ca540cb78d70797dbf4eedf7395
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739589"
---
# <a name="cordebugstatechange-enumeration"></a>CorDebugStateChange Numaralandırması

Değişiklikler iş akışına dayalı atılması gerekir önbelleğe alınan veri miktarı açıklar.

## <a name="syntax"></a>Sözdizimi

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a>Üyeler

| Üye            | Açıklama                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | İşlem, iletme yürütme aracılığıyla yeni bir bellek durumuna erişmedi.            |
| `FLUSH_ALL`       | İşlem bellek öncekinden rasgele farklı olabilir. |

## <a name="remarks"></a>Açıklamalar

 Üye `CorDebugStateChange` numaralandırma hata ayıklayıcı çağırdığında bir bağımsız değişken olarak sağlanan `ProcessStateChanged` yöntemi ile birlikte [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) veya [Icordebugprocess6:: ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)

## <a name="requirements"></a>Gereksinimler

 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

 **Üst bilgi:** CorDebug.idl, CorDebug.h

 **Kitaplığı:** CorGuids.lib

 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](debugging-enumerations.md)
- [Hata Ayıklama](index.md)
