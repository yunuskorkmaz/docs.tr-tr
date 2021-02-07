---
description: 'Daha fazla bilgi edinin: CorThreadSafetyOptions numaralandırması'
title: CorThreadSafetyOptions Numaralandırması
ms.date: 03/30/2017
api_name:
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
ms.openlocfilehash: 7915bcf5e7b71fa84ea83642467c1600cd38712d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707325"
---
# <a name="corthreadsafetyoptions-enumeration"></a>CorThreadSafetyOptions Numaralandırması

İş parçacığı güvenliği seçeneklerinin seçilecek bayrakları belirtir.

## <a name="syntax"></a>Syntax

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a>Üyeler

|Üye|Description|
|------------|-----------------|
|`MDThreadSafetyDefault`|Varsayılan değer. Aynı `MDThreadSafetyOff` .|
|`MDThreadSafetyOff`|Bir okuyucu/yazıcı kilidinin ayarlanamayacağını belirtir.|
|`MDThreadSafetyOn`|Bir okuyucu/yazıcı kilidinin ayarlanamayacağını gösterir.|

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** CorHdr. h

**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
