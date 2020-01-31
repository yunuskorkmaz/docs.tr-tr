---
title: 'Icordebugvariablehome:: Getargumentındex yöntemi'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetArgumentIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
ms.openlocfilehash: 12d4e63480f03bfad613f30362ddaeaf12b57a88
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791044"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a>Icordebugvariablehome:: Getargumentındex yöntemi

Bir işlev bağımsız değişkeninin dizinini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a>Parametreler

`pArgumentIndex`\
dışı Bağımsız değişken dizinine yönelik bir işaretçi.

## <a name="return-value"></a>Dönüş Değeri

Yöntemi aşağıdaki değerleri döndürür.

|Değer|Açıklama|
|-----------|-----------------|
|`S_OK`|Yöntem çağrısı geçerli bir bağımsız değişken dizini döndürdü.|
|`E_FAIL`|Geçerli [ıcordebugvariablehome](icordebugvariablehome-interface.md) örneği yerel bir değişkeni temsil eder.|

## <a name="remarks"></a>Açıklamalar

Bağımsız değişken dizini bu bağımsız değişken için meta verileri almak için kullanılabilir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** CorDebug. IDL, CorDebug. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugVariableHome Arabirimi](icordebugvariablehome-interface.md)
