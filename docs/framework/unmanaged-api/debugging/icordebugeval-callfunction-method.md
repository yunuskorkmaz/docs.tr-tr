---
title: ICorDebugEval::CallFunction Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CallFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type:
- apiref
ms.openlocfilehash: 4ac26ef4449dc02230f26b1247616b4587d217b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085167"
---
# <a name="icordebugevalcallfunction-method"></a>ICorDebugEval::CallFunction Yöntemi

Belirtilen işleve bir çağrı kurar.

Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor. Bunun yerine [ICorDebugEval2:: CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) kullanın.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a>Parametreler

`pFunction`\
'ndaki Çağrılacak işlevi belirten ICorDebugFunction nesnesine yönelik işaretçi.

`nArgs`\
'ndaki İşlevin bağımsız değişken sayısı.

`ppArgs`\
'ndaki Her biri, işleve geçirilecek bir bağımsız değişken belirten ICorDebugValue nesnesine işaret eden bir işaretçiler dizisi.

## <a name="remarks"></a>Açıklamalar

İşlev sanal ise `CallFunction` sanal dağıtım yapar. İşlev farklı bir uygulama etki alanında ise, tüm bağımsız değişkenler de bu uygulama etki alanında olduğu sürece bir geçiş meydana gelir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** CorDebug. IDL, CorDebug. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:** 1,1, 1,0

## <a name="see-also"></a>Ayrıca bkz.

- [CallParameterizedFunction Yöntemi](icordebugeval2-callparameterizedfunction-method.md)
