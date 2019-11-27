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
ms.openlocfilehash: ca7c7570aff63aa328dddc0626648fa74397addc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448739"
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
Tür belirteçlerini alır, `dwMax`aşmamak için kullanılamaz.

`pdwCount`\
`aTypeDefs`gerçek tür sayısını alır.

## <a name="return-value"></a>Dönüş Değeri

Yöntem başarılı olursa S_OK döndürür.

## <a name="requirements"></a>Gereksinimler

ALink. h gerektirir

## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
