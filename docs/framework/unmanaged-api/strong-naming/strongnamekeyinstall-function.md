---
description: 'Daha fazla bilgi edinin: StrongNameKeyInstall Işlevi'
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
ms.openlocfilehash: 0a5d3971ac0927dda7066405adc01a5c80b7faca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670560"
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
'ndaki Bayt cinsinden boyutu `pbKeyBlob` .

## <a name="return-value"></a>Dönüş Değeri

`true` başarıyla tamamlandığında; Aksi takdirde, `false` .

## <a name="remarks"></a>Açıklamalar

Anahtar kapsayıcısını silmek için [StrongNameKeyDelete](strongnamekeydelete-function.md) işlevini kullanın.

`StrongNameKeyInstall`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** StrongName. h

**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi

**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameKeyInstall Yöntemi](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [StrongNameKeyDelete Yöntemi](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
