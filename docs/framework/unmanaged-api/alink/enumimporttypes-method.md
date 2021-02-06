---
description: 'Daha fazla bilgi edinin: EnumImportTypes yöntemi'
title: EnumImportTypes Yöntemi
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
ms.openlocfilehash: 39570740f3560f5bfef8ba80b95c0eb2aca41f59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638125"
---
# <a name="enumimporttypes-method"></a>EnumImportTypes Yöntemi

Her kapsamdaki her türü numaralandırır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a>Parametreler

`hEnum`\
Numaralandırıcı için tanıtıcı.

`dwMax`\
Alınacak maksimum tür sayısı.

`aTypeDefs`\
Tür belirteçlerini alır, aşılamaz `dwMax` .

`pdwCount`\
İçindeki gerçek tür sayısını alır `aTypeDefs` .

## <a name="return-value"></a>Dönüş Değeri

Yöntem başarılı olursa S_OK döndürür.

## <a name="requirements"></a>Gereksinimler

ALink. h gerektirir

## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
