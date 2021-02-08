---
description: ': IXCLRDataMethodInstance:: Getıladdressmap yöntemi hakkında daha fazla bilgi edinin'
title: 'IXCLRDataMethodInstance:: Getıladdressmap yöntemi'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodInstance::GetILAddressMap Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method
helpviewer.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: ddddf593c3c18f2b4cd1682b5d6f7c8ff1985ac6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800818"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a>IXCLRDataMethodInstance:: Getıladdressmap yöntemi

Eşleme bilgilerini ele almak için Il 'yi alır.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

## <a name="parameters"></a>Parametreler

`mapLen`\
'ndaki Belirtilen haritalar dizisinin uzunluğu.

`mapNeeded`\
dışı Metodun ihtiyacı olan eşleme girdilerinin sayısı.

`maps`\
[Out, size_is (mapLen)] Harita girdilerini depolamak için dizi.

## <a name="remarks"></a>Açıklamalar

Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataMethodInstance` ve sanal yöntem tablosunun 15. yuvasına karşılık gelir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
**Üst bilgi:** Seçim  
**Kitaplık:** Seçim  
**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [IXCLRDataMethodInstance Arabirimi](ixclrdatamethodinstance-interface.md)
