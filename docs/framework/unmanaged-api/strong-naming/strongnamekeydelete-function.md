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
ms.openlocfilehash: dfc785a48d0cdf1cf2fdc0245a27b8ef35fd2d81
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364527"
---
# <a name="strongnamekeydelete-function"></a>StrongNameKeyDelete İşlevi

Belirtilen anahtar kapsayıcısında siler.

Bu işlev kullanım dışı bırakıldı. Kullanım [Iclrstrongname::strongnamekeydelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) yöntemi yerine.

## <a name="syntax"></a>Sözdizimi

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a>Parametreler

`wszKeyContainer`\
[in] Silinecek anahtar kapsayıcısının adı.

## <a name="return-value"></a>Dönüş Değeri

`true` başarıyla tamamlandığında; Aksi takdirde, `false`.

## <a name="remarks"></a>Açıklamalar

Kullanım [Strongnamekeyınstall](strongnamekeyinstall-function.md) bir kapsayıcıya bir ortak/özel anahtar çifti alınacak işlev.

Varsa `StrongNameKeyDelete` işlevi değil başarıyla tamamlanması, çağrı [Strongnameerrorınfo](strongnameerrorinfo-function.md) oluşturulan son hatayı alması için işlevi.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** StrongName.h

**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil

**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameKeyDelete Yöntemi](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [StrongNameKeyInstall Yöntemi](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)