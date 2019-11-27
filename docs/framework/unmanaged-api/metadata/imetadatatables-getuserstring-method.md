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
ms.openlocfilehash: 5936ca837c9ab452e992fcb09aacb476ab37316a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431428"
---
# <a name="imetadatatablesgetuserstring-method"></a>IMetaDataTables::GetUserString Metodu

Geçerli kapsamdaki dize sütununda belirtilen dizinde sabit kodlanmış dizeyi alır.

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
'ndaki Sabit kodlanmış dizenin alınacağı dizin değeri.

`pcbData`\
dışı `ppData`boyutuna yönelik bir işaretçi.

`ppData`\
dışı Döndürülen dizeye bir işaretçi işaretçisi.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** Cor. h

**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır

**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataTables Arabirimi](imetadatatables-interface.md)
- [IMetaDataTables2 Arabirimi](imetadatatables2-interface.md)
