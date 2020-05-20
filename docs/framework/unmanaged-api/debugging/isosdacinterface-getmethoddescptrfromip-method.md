---
title: 'Iosdacınterface:: Getmethoddescptrfromıp yöntemi'
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: c3de9e5ffe23a13c126343c6f74f042bf1239609
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421013"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a>Iosdacınterface:: Getmethoddescptrfromıp yöntemi

Verilen yerel yönerge adresini içeren yöntemi karşılık gelen MethodDesc işaretçisini alır.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a>Parametreler

`ip`\
'ndaki Çalışma zamanında yöntemi içindeki bir adres.

`ppMD`\
dışı `MethodDesc`Belirli yöntemin adresi.

## <a name="remarks"></a>Açıklamalar

Belirtilen yöntem [ `ISOSDacInterface` arabirimin](isosdacinterface-interface.md) bir parçasıdır ve sanal yöntem tablosunun 22 yuvasına karşılık gelir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
**Üst bilgi:** Seçim  
**Kitaplık:** Seçim  
**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [ISOSDacInterface Arabirimi](isosdacinterface-interface.md)
