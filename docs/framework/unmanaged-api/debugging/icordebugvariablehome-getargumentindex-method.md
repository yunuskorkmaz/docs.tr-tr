---
description: ': Icordebugvariablehome:: Getargumentındex yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 827ef55d3e3509cbfbfc8213ef5b53fbe2e2220e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690047"
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

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** CorDebug. IDL, CorDebug. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugVariableHome Arabirimi](icordebugvariablehome-interface.md)
