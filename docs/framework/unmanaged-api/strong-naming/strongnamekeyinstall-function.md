---
title: StrongNameKeyInstall İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyInstall
helpviewer_keywords:
- StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type:
- apiref
ms.openlocfilehash: 9e441d4da64e9704fbda2368d2b07289aaea610a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125206"
---
# <a name="strongnamekeyinstall-function"></a>StrongNameKeyInstall İşlevi

Bir kapsayıcıya ortak/özel anahtar çifti aktarır.

Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) metodunu kullanın.

## <a name="syntax"></a>Sözdizimi

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a>Parametreler

`wszKeyContainer`\
'ndaki Anahtar kapsayıcısının adı. `wszKeyContainer` boş olmayan bir dize olmalıdır.

`pbKeyBlob`\
'ndaki İkili anahtar çifti.

`cbKeyBlob`\
'ndaki `pbKeyBlob`bayt cinsinden boyutu.

## <a name="return-value"></a>Dönüş Değeri

başarılı tamamlamada `true`; Aksi takdirde, `false`.

## <a name="remarks"></a>Açıklamalar

Anahtar kapsayıcısını silmek için [StrongNameKeyDelete](strongnamekeydelete-function.md) işlevini kullanın.

`StrongNameKeyInstall` işlevi başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** StrongName. h

**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir

**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameKeyInstall Yöntemi](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [StrongNameKeyDelete Yöntemi](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
