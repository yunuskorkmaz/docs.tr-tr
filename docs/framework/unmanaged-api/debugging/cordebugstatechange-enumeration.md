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
ms.openlocfilehash: 239e3a82df0e6010278669f9f429bfad0d163319
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133719"
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

 Hata ayıklayıcı, `ProcessStateChanged` yöntemini [ICorDebugProcess4::P rocessstatechanged](icordebugprocess4-processstatechanged-method.md) veya [ICorDebugProcess6::P rocessstatechanged](icordebugprocess6-processstatechanged-method.md) ile çağırdığında `CorDebugStateChange` numaralandırmanın bir üyesi olarak sağlanır

## <a name="requirements"></a>Gereksinimler

 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

 **Üst bilgi:** CorDebug. IDL, CorDebug. h

 **Kitaplık:** Corguid. lib

 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](debugging-enumerations.md)
- [Hata Ayıklama](index.md)
