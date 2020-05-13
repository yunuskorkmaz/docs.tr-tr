---
title: ICorDebugProcess4::P rocessStateChanged yöntemi
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4::ProcessStateChanged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4::ProcessStateChanged
helpviewer_keywords:
- ICorDebugProcess4::ProcessStateChanged method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 910c411d2c63ce2c6cf262e28e08546657dc2a4c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213575"
---
# <a name="icordebugprocess4processstatechanged-method"></a>ICorDebugProcess4::P rocessStateChanged yöntemi

ICorDebug ardışık düzenine, işlem hata ayıklamanın dışına ayıklandığını bildirir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a>Parametreler

 `eChange`\
'ndaki İşlemin yürütme durumundaki bir değişikliği açıklayan [Cordebugstatechange numaralandırmasının](cordebugstatechange-enumeration.md) bir üyesi.

## <a name="remarks"></a>Açıklamalar

Belirtilen yöntem arabirimin bir parçasıdır `ICorDebugProcess4` ve sanal yöntem tablosunun dördüncü yuvasına karşılık gelir.

## <a name="requirements"></a>Gereksinimler

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

 **Üst bilgi:** Seçim

 **Kitaplık:** Seçim

 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess4 Arabirimi](icordebugprocess4-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
