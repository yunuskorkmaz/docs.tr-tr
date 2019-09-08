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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 353898b72f41acd0c49a43ff05e54f61b99444c4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798999"
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
'ndaki Anahtar kapsayıcısının adı. `wszKeyContainer`boş olmayan bir dize olmalıdır.

`pbKeyBlob`\
'ndaki İkili anahtar çifti.

`cbKeyBlob`\
'ndaki Bayt cinsinden boyutu `pbKeyBlob`.

## <a name="return-value"></a>Dönüş Değeri

`true`başarıyla tamamlandığında; Aksi takdirde `false`,.

## <a name="remarks"></a>Açıklamalar

Anahtar kapsayıcısını silmek için [StrongNameKeyDelete](strongnamekeydelete-function.md) işlevini kullanın.

İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo işlevini çağırın.](strongnameerrorinfo-function.md) `StrongNameKeyInstall`

## <a name="requirements"></a>Gereksinimler

**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi** StrongName. h

**Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir

**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameKeyInstall Yöntemi](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [StrongNameKeyDelete Yöntemi](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
