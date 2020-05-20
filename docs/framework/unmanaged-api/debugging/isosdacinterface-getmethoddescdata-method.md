---
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
ms.openlocfilehash: 105149d0abf312c33a8498e7428e3a8b23d6ae7d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421026"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a>Iosdacınterface:: GetMethodDescData yöntemi

Verilen MethodDesc işaretçisi için verileri alır.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Söz dizimi

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
