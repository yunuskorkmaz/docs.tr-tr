---
description: 'Hakkında daha fazla bilgi edinin: _AxlRSAKeyValueToPublicKeyToken işlevi'
title: _AxlRSAKeyValueToPublicKeyToken işlevi
ms.date: 03/30/2017
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
topic_type:
- apiref
ms.openlocfilehash: 01fc4cdc1d9985375748307ca2d7fff97191c908
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747276"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a>\_AxlRSAKeyValueToPublicKeyToken işlevi

Bir mod ve üs değeri bir tanımlayıcı ad ortak anahtar belirtecine dönüştürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT _AxlRSAKeyValueToPublicKeyToken (
    [in]  PCRYPT_DATA_BLOB pModulusBlob,
    [in]  PCRYPT_DATA_BLOB pExponentBlob,
    [out] LPWSTR           *ppwszPublicKeyToken
);
```

## <a name="parameters"></a>Parametreler

 `pModulusBlob`\
 'ndaki Base64 ile kodlanmış mod Blobu (öğesinden \<Modulus> ).  [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısına bakın.

 `pExponentBlob`\
 'ndaki Base64 ile kodlanmış üs Blobu (öğesinden \<Exponent> ). [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) yapısına bakın.

 `ppwszPublicKeyToken`\
 dışı Onaltılık kodlanmış ortak anahtar belirtecini almak için bir WCHAR * işaretçisi.

## <a name="return-value"></a>Dönüş Değeri

 `S_OK` işlev başarılı olursa. Aksi takdirde, bir hata kodu döndürür.

## <a name="requirements"></a>Gereksinimler

**Bütünleştirilmiş kod**: clr.dll

## <a name="see-also"></a>Ayrıca bkz.

- [Authenticode](index.md)
