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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17d35193f69966e02ac5e483924fcb3ee2e06758
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799026"
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

`true`başarıyla tamamlandığında; Aksi takdirde `false`,.

## <a name="remarks"></a>Açıklamalar

Ortak/özel anahtar çiftini bir kapsayıcıya içeri aktarmak için [Strongnamekeyinstall](strongnamekeyinstall-function.md) işlevini kullanın.

İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo işlevini çağırın.](strongnameerrorinfo-function.md) `StrongNameKeyDelete`

## <a name="requirements"></a>Gereksinimler

**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi** StrongName. h

**Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir

**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameKeyDelete Yöntemi](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [StrongNameKeyInstall Yöntemi](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
