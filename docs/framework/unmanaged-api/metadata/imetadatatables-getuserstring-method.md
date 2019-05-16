---
title: IMetaDataTables::GetUserString Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4eaf426bc9c933de1d4b774928f2b0a54dfb472
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636952"
---
# <a name="imetadatatablesgetuserstring-method"></a>IMetaDataTables::GetUserString Metodu

Geçerli kapsamdaki dize sütununda belirtilen dizindeki sabit kodlanmış bir dize alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetUserString (
    [in]  ULONG       ixUserString,
    [out] ULONG       *pcbData,
    [out] const void  **ppData
);
```

## <a name="parameters"></a>Parametreler

`ixUserString`\
[in] Dizin değeri sabit kodlanmış dize alınır.

`pcbData`\
[out] Bir işaretçinin boyutuna `ppData`.

`ppData`\
[out] Döndürülen dize için bir işaretçi işaretçisi.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** COR.h

**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan

**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataTables Arabirimi](imetadatatables-interface.md)
- [IMetaDataTables2 Arabirimi](imetadatatables2-interface.md)
