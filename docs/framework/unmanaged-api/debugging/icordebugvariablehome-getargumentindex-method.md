---
title: ICorDebugVariableHome::GetArgumentIndex yöntemi
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2457dff3063e47f1fb9d040caac1bc08441e1739
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986797"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a>ICorDebugVariableHome::GetArgumentIndex yöntemi

İşlev bağımsız değişkeni dizinini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a>Parametreler

`pArgumentIndex`\
[out] Bağımsız değişken dizini için bir işaretçi.

## <a name="return-value"></a>Dönüş Değeri

Bu yöntem, aşağıdaki değerleri döndürür.

|Değer|Açıklama|
|-----------|-----------------|
|`S_OK`|Yöntem çağrısının geçerli bağımsız değişken dizini döndürdü.|
|`E_FAIL`|Geçerli [Icordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) örneği yerel bir değişken temsil eder.|

## <a name="remarks"></a>Açıklamalar

Bağımsız değişken dizini, bu bağımsız değişken için meta verilerini almak için kullanılabilir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** CorDebug.idl, CorDebug.h

**Kitaplığı:** CorGuids.lib

**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugVariableHome Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
