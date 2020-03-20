---
title: ICorDebugProcess4::ProcessStateChanged Yöntemi
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
ms.openlocfilehash: a6f36f5b86b4fa58ce2a4ef4aa23d527f797a5a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178636"
---
# <a name="icordebugprocess4processstatechanged-method"></a>ICorDebugProcess4::ProcessStateChanged Yöntemi

ICorDebug boru hattına işlem hata ayıklayıcısının debugee'nin yürütmesini devam ettiğini bildirin.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a>Parametreler

 `eChange`\
[içinde] İşlemin yürütme durumundaki bir değişikliği açıklayan [CorDebugStateChange numaralandırmasının](cordebugstatechange-enumeration.md) bir üyesi.

## <a name="remarks"></a>Açıklamalar

Sağlanan yöntem `ICorDebugProcess4` arabirimin bir parçasıdır ve sanal yöntem tablosunun dördüncü yuvasına karşılık gelir.

## <a name="requirements"></a>Gereksinimler

 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

 **Üstbilgi:** Hiçbiri

 **Kütüphane:** Hiçbiri

 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess4 Arabirimi](icordebugprocess4-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata ayıklama](index.md)
