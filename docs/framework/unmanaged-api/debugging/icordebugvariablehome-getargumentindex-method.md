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
ms.openlocfilehash: 86b2815c6f95c674c49bba7455e8497192bd8bac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125147"
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
|`E_FAIL`|Geçerli [ıcordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) örneği yerel bir değişkeni temsil eder.|

## <a name="remarks"></a>Açıklamalar

Bağımsız değişken dizini bu bağımsız değişken için meta verileri almak için kullanılabilir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** CorDebug. IDL, CorDebug. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugVariableHome Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
