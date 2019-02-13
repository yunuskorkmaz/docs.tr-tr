---
title: ICorDebugProcess4 arabirimi
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4
helpviewer_keywords:
- ICorDebugProcess4 interface [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 1bdc958f2516bcd7c2eb74312fbf478e6d49535a
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221381"
---
# <a name="icordebugprocess4-interface"></a>ICorDebugProcess4 arabirimi

İşlem yürütme denetimi dışında için destek sağlar.

## <a name="methods"></a>Yöntemler

| Yöntem                                                                 | Açıklama                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) | Icordebug ardışık düzen işlemi hata ayıklayıcı dışı debugee'nın yürütülmesine devam etmesini bildirir. |

## <a name="remarks"></a>Açıklamalar

Bu arabirim, çalışma zamanı içinde bulunur ve herhangi bir üst bilgiler veya kitaplık dosyaları kullanıma. Ancak, bu, türetilen bir COM arabirimidir `IUnknown` GUID'e sahip `E930C679-78AF-4953-8AB7-B0AABF0F9F80` normal COM mekanizmalar aracılığıyla edinilebilir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** Hiçbiri

**Kitaplığı:** Hiçbiri

**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
