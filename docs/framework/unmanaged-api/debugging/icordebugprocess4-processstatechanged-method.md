---
title: ICorDebugProcess4::ProcessStateChanged yöntemi
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
ms.openlocfilehash: b77dd1277e7d23729f30d9d495c5417055a22759
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378996"
---
# <a name="icordebugprocess4processstatechanged-method"></a>ICorDebugProcess4::ProcessStateChanged yöntemi

Icordebug ardışık düzen işlemi hata ayıklayıcı dışı debugee'nın yürütülmesine devam etmesini bildirir.

## <a name="syntax"></a>Sözdizimi

```
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a>Parametreler

 `eChange`\
[in] Üye [CorDebugStateChange numaralandırması](cordebugstatechange-enumeration.md) işlem yürütme durumundaki bir değişikliği açıklayan.

## <a name="remarks"></a>Açıklamalar

Sağlanan yöntem parçasıdır `ICorDebugProcess4` arabirim ve sanal yöntem tablosunun dördüncü yuvaya karşılık gelir.

## <a name="requirements"></a>Gereksinimler

 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

 **Üst bilgi:** Hiçbiri

 **Kitaplığı:** Hiçbiri
 
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess4 arabirimi](icordebugprocess4-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)