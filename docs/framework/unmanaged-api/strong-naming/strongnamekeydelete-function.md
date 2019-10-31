---
title: StrongNameKeyDelete İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
ms.openlocfilehash: d37f990241ae704abef55d863da0f40a31284837
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141589"
---
# <a name="strongnamekeydelete-function"></a>StrongNameKeyDelete İşlevi

Belirtilen anahtar kapsayıcısını siler.

Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) metodunu kullanın.

## <a name="syntax"></a>Sözdizimi

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a>Parametreler

`wszKeyContainer`\
'ndaki Silinecek anahtar kapsayıcısının adı.

## <a name="return-value"></a>Dönüş Değeri

başarılı tamamlamada `true`; Aksi takdirde, `false`.

## <a name="remarks"></a>Açıklamalar

Ortak/özel anahtar çiftini bir kapsayıcıya içeri aktarmak için [Strongnamekeyinstall](strongnamekeyinstall-function.md) işlevini kullanın.

`StrongNameKeyDelete` işlevi başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** StrongName. h

**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir

**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameKeyDelete Yöntemi](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [StrongNameKeyInstall Yöntemi](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
