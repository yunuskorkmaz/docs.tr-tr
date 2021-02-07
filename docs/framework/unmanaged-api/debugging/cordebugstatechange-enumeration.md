---
description: 'Daha fazla bilgi edinin: CorDebugStateChange numaralandırması'
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
ms.openlocfilehash: 1900baa77432daa10d0f1a32dd9cb25198b86ed1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661824"
---
# <a name="cordebugstatechange-enumeration"></a>CorDebugStateChange Numaralandırması

İşlemdeki değişikliklere göre atılması gereken önbelleğe alınmış verilerin miktarını açıklar.

## <a name="syntax"></a>Syntax

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a>Üyeler

| Üye            | Description                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | İşlem, ileri yürütme yoluyla yeni bir bellek durumuna ulaştı.            |
| `FLUSH_ALL`       | İşlemin belleği daha önce gerekenden farklı olabilir. |

## <a name="remarks"></a>Açıklamalar

 `CorDebugStateChange`Hata ayıklayıcı ICorDebugProcess4 ile yöntemi çağırdığında numaralandırma üyesi bir bağımsız değişken olarak sağlanır `ProcessStateChanged` [::P rocessstatechanged](icordebugprocess4-processstatechanged-method.md) veya [ICorDebugProcess6::P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)

## <a name="requirements"></a>Gereksinimler

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

 **Üst bilgi:** CorDebug. IDL, CorDebug. h

 **Kitaplık:** Corguid. lib

 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
- [Hata Ayıklama](index.md)
