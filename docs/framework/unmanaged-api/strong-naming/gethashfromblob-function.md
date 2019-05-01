---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d9e7b52c9061a1a7b470f9d4abf735e605087dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000538"
---
# <a name="gethashfromblob-function"></a>GetHashFromBlob İşlevi

Derleme karması belirtilen karma algoritması kullanılarak belirtilen bellek adresinde alır.

Bu işlev kullanım dışı bırakıldı. Kullanım [Iclrstrongname::gethashfromblob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) yöntemi yerine.

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
[in] Adres karma hale getirilecek bellek bloğu için bir işaretçi.

`cchBlob`\
[in] Uzunluğu, bayt cinsinden bellek bloğu.

`piHashAlg`\
[out içinde] Sabit karma algoritmasını belirtir. Sıfır varsayılan algoritma için kullanın.

`pbHash`\
[out] Döndürülen karma arabellek.

`cchHash`\
[in] İstenen en büyük boyutunu `pbHash`.

`pchHash`\
[out] Döndürülen bayt cinsinden boyutu `pbHash`.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** StrongName.h

**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil

**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [GetHashFromBlob Yöntemi](../hosting/iclrstrongname-gethashfromblob-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)