---
title: IXCLRDataMethodInstance::GetILAddressMap yöntemi
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
ms.openlocfilehash: 66e4768acff7ab735c6ac9e8f8f51a9511f7e371
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744687"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a>IXCLRDataMethodInstance::GetILAddressMap yöntemi

IL adresi eşleme bilgileri alır.

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
[in] Sağlanan haritalar dizinin uzunluğu.

`mapNeeded`\
[out] Gereken yöntemini eşleme girişleri sayısı.

`maps`\
[out, size_is(mapLen)] Eşleme girişleri depolamak için dizi.

## <a name="remarks"></a>Açıklamalar

Sağlanan yöntem parçasıdır `IXCLRDataMethodInstance` arabirim ve sanal yöntem tablosunu 14 yuvaya karşılık gelir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
**Üst bilgi:** Yok.  
**Kitaplığı:** None  
**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [IXCLRDataMethodInstance arabirimi](ixclrdatamethodinstance-interface.md)
