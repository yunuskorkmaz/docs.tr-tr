---
description: 'Şu konuda daha fazla bilgi edinin: ısosdacınterface:: Getmethoddescptrfromıp yöntemi'
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
ms.openlocfilehash: 8d7c7071b7b3fc520faea71c8d7792317745cfde
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790418"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a>Iosdacınterface:: Getmethoddescptrfromıp yöntemi

Verilen yerel yönerge adresini içeren yöntemi karşılık gelen MethodDesc işaretçisini alır.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

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
dışı `MethodDesc` Belirli yöntemin adresi.

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
