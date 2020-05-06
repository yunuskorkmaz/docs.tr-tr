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
ms.openlocfilehash: d94422d25da91cd2a6653a95cbd852c3930a151a
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795696"
---
# <a name="cordebugstatechange-enumeration"></a>CorDebugStateChange Numaralandırması

İşlemdeki değişikliklere göre atılması gereken önbelleğe alınmış verilerin miktarını açıklar.

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
| `PROCESS_RUNNING` | İşlem, ileri yürütme yoluyla yeni bir bellek durumuna ulaştı.            |
| `FLUSH_ALL`       | İşlemin belleği daha önce gerekenden farklı olabilir. |

## <a name="remarks"></a>Açıklamalar

 Hata ayıklayıcı ICorDebugProcess4 ile `CorDebugStateChange` `ProcessStateChanged` yöntemi çağırdığında numaralandırma üyesi bir bağımsız değişken olarak sağlanır [::P Rocessstatechanged](icordebugprocess4-processstatechanged-method.md) veya [ICorDebugProcess6::P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)

## <a name="requirements"></a>Gereksinimler

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

 **Üst bilgi:** CorDebug. IDL, CorDebug. h

 **Kitaplık:** Corguid. lib

 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
- [Hata Ayıklama](index.md)
