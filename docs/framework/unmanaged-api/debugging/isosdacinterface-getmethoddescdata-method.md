---
description: 'Şu konuda daha fazla bilgi edinin: ısosdacınterface:: GetMethodDescData yöntemi'
title: 'Iosdacınterface:: GetMethodDescData yöntemi'
ms.date: 01/16/2019
api.name:
- ISOSDacInterface::GetMethodDescData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescData Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescData Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a1284aa4d810ed9d6db7ad3c1b471702b1dad54d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790431"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a>Iosdacınterface:: GetMethodDescData yöntemi

Verilen MethodDesc işaretçisi için verileri alır.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

## <a name="parameters"></a>Parametreler

`methodDesc`\
'ndaki MethodDesc adresi.

`ip`\
'ndaki Metodun IP adresi.

`data`\
dışı İç API 'lerden döndürülen MethodDesc ile ilişkili veriler.

`cRevertedRejitVersions`\
dışı Geri döndürülen yeniden JIT sürümü sayısı.

`rgRevertedRejitData`\
dışı İç API 'lerden döndürülen geri döndürülen yeniden JIT sürümleriyle ilişkili veriler.

`pcNeededRevertedRejitData`\
dışı Geri döndürülen ReJIT sürümleriyle ilişkili verileri depolamak için gereken bayt sayısı.

## <a name="remarks"></a>Açıklamalar

Belirtilen yöntem arabirimin bir parçasıdır `ISOSDacInterface` ve sanal yöntem tablosunun 21 yuvasına karşılık gelir. Bunları kullanabilmeniz için, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) 64 bitlik işaretsiz bir tamsayı olarak tanımlanmalıdır.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
**Üst bilgi:** Seçim  
**Kitaplık:** Seçim  
**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [ISOSDacInterface Arabirimi](isosdacinterface-interface.md)
