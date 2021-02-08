---
description: 'Daha fazla bilgi edinin: CertFreeAuthenticodeTimestamperInfo Işlevi'
title: CertFreeAuthenticodeTimestamperInfo İşlevi
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeTimestamperInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 3eb14c49-68c2-4516-ac89-e5bd7473831c
topic_type:
- apiref
ms.openlocfilehash: 5234a90ea1d0272a7409b1b0b4def2160b77a513
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772945"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a>CertFreeAuthenticodeTimestamperInfo İşlevi

[AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) yapısı için ayrılan kaynakları boşaltır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CertFreeAuthenticodeTimestamperInfo (
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo
);
```

## <a name="parameters"></a>Parametreler

 `pTimestamperInfo`\
 [in, out] Yayımlanacak zaman bilgileri. [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) yapısına bakın.

## <a name="return-value"></a>Dönüş Değeri

 `S_OK` işlev başarılı olursa. Aksi takdirde, bir hata kodu döndürür.

## <a name="requirements"></a>Gereksinimler

**Bütünleştirilmiş kod**: clr.dll

## <a name="see-also"></a>Ayrıca bkz.

- [Authenticode](index.md)
