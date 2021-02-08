---
description: 'Hakkında daha fazla bilgi edinin: _AxlPublicKeyBlobToPublicKeyToken Işlevi'
title: _AxlPublicKeyBlobToPublicKeyToken İşlevi
ms.date: 03/30/2017
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
topic_type:
- apiref
ms.openlocfilehash: df0b484bad64051eb892d4898a6c90777cc2d5cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781941"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a>\_AxlPublicKeyBlobToPublicKeyToken Işlevi

Bir CSP PUBLICKEYBLOB biçiminden tanımlayıcı ad ortak anahtar belirtecini hesaplar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT _AxlPublicKeyBlobToPublicKeyToken (
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,
    [out] LPWSTR                 *ppwszPublicKeyToken
);
```

## <a name="parameters"></a>Parametreler

 `pCspPublicKeyBlob`\
 'ndaki CSP ortak anahtar blobu.

 `ppwszPublicKeyHash`\
 dışı Onaltılık kodlanmış ortak anahtar karmasını almak için bir WCHAR * işaretçisi.

## <a name="return-value"></a>Dönüş Değeri

 `S_OK` işlev başarılı olursa; Aksi takdirde `S_FALSE` .

## <a name="requirements"></a>Gereksinimler

**Bütünleştirilmiş kod**: clr.dll

## <a name="see-also"></a>Ayrıca bkz.

- [Authenticode](index.md)
