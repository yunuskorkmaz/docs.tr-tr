---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0cd154ac90418dd0f6f476151686ff670c01c98c
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632242"
---
# <a name="enumimporttypes-method"></a>EnumImportTypes Yöntemi

Her kapsamda her türünü numaralandırır.

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
Numaralandırıcı için işler.

`dwMax`\
Alınacak türleri sayısı.

`aTypeDefs`\
Aşmayan türü belirteçlerini alır `dwMax`.

`pdwCount`\
Türünde gerçek sayısını alır `aTypeDefs`.

## <a name="return-value"></a>Dönüş Değeri

Yöntem başarılı olursa S_OK döndürür.

## <a name="requirements"></a>Gereksinimler

ALink.h gerektirir

## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
