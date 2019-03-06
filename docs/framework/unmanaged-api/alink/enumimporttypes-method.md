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
ms.openlocfilehash: 1d0aefea7345bc3bf37bdb8d13cb2cda19cfe527
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355746"
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