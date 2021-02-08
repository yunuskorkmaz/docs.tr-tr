---
description: 'Daha fazla bilgi edinin: IXCLRDataMethodInstance:: GetRepresentativeEntryAddress yöntemi'
title: 'IXCLRDataMethodInstance:: GetRepresentativeEntryAddress yöntemi'
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
helpviewer.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 21cc6c50ab460c0e3a3a92c11fcfe51d4a2a4606
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800805"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a>IXCLRDataMethodInstance:: GetRepresentativeEntryAddress yöntemi

Bir yöntem için tüm olası giriş noktalarının yerel derlenmesi için en temsili giriş noktası adresini alır.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

## <a name="parameters"></a>Parametreler

`addr`\
dışı Yöntemi için en temsili yerel giriş noktasının adresi.

## <a name="remarks"></a>Açıklamalar

Belirtilen yöntem [ `IXCLRDataMethodInstance` arabirimin](ixclrdatamethodinstance-interface.md) bir parçasıdır ve sanal yöntem tablosunun 20. yuvasına karşılık gelir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
**Üst bilgi:** Seçim  
**Kitaplık:** Seçim  
**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [IXCLRDataMethodInstance Arabirimi](ixclrdatamethodinstance-interface.md)
