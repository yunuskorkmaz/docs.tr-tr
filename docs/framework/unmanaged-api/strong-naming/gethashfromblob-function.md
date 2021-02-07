---
description: 'Daha fazla bilgi edinin: GetHashFromBlob Işlevi'
title: GetHashFromBlob İşlevi
ms.date: 03/30/2017
api_name:
- GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromBlob
helpviewer_keywords:
- GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type:
- apiref
ms.openlocfilehash: dc5039e44440afa7a000bc61167faec0e5b6cc84
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736615"
---
# <a name="gethashfromblob-function"></a>GetHashFromBlob İşlevi

Belirtilen karma algoritmasını kullanarak, belirtilen bellek adresindeki derlemenin karmasını alır.

Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md) yöntemini kullanın.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetHashFromBlob (
    [in]  BYTE    *pbBlob,
    [in]  DWORD   cchBlob,
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE    *pbHash,
    [in]  DWORD   cchHash,
    [out] DWORD   *pchHash
);
```

## <a name="parameters"></a>Parametreler

`pbBlob`\
'ndaki Karma hale getirilen bellek bloğunun adresine yönelik bir işaretçi.

`cchBlob`\
'ndaki Bellek bloğunun bayt cinsinden uzunluğu.

`piHashAlg`\
[in, out] Karma algoritmayı belirten bir sabit. Varsayılan algoritma için sıfır kullanın.

`pbHash`\
dışı Döndürülen karma arabelleği.

`cchHash`\
'ndaki İstenen en büyük boyut `pbHash` .

`pchHash`\
dışı Döndürülen bayt cinsinden boyutu `pbHash` .

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** StrongName. h

**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi

**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [GetHashFromBlob Yöntemi](../hosting/iclrstrongname-gethashfromblob-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
