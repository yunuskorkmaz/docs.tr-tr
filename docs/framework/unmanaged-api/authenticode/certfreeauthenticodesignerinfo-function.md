---
description: 'Daha fazla bilgi edinin: CertFreeAuthenticodeSignerInfo Işlevi'
title: CertFreeAuthenticodeSignerInfo İşlevi
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeSignerInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
topic_type:
- apiref
ms.openlocfilehash: 6e8a97e8fee37d885c7d32102ed8cc7654992223
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772984"
---
# <a name="certfreeauthenticodesignerinfo-function"></a>CertFreeAuthenticodeSignerInfo İşlevi

[AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) yapısı için ayrılan kaynakları boşaltır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CertFreeAuthenticodeSignerInfo (
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);
```

## <a name="parameters"></a>Parametreler

 `pSignerInfo`\
 [in, out] Yayımlanacak imzalayan bilgileri. [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) yapısına bakın.

## <a name="return-value"></a>Dönüş Değeri

 `S_OK` işlev başarılı olursa. Aksi takdirde, bir hata kodu döndürür.

## <a name="requirements"></a>Gereksinimler

**Bütünleştirilmiş kod**: clr.dll

## <a name="see-also"></a>Ayrıca bkz.

- [Authenticode](index.md)
