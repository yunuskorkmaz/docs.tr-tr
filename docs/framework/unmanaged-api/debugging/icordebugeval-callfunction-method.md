---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıbgeval:: CallFunction yöntemi'
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
ms.openlocfilehash: c0978ab3bdffc83e3eb5e3a6553e7f374ab6d5da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694194"
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

İşlev sanal ise, `CallFunction` sanal dağıtım yapar. İşlev farklı bir uygulama etki alanında ise, tüm bağımsız değişkenler de bu uygulama etki alanında olduğu sürece bir geçiş meydana gelir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** CorDebug. IDL, CorDebug. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:** 1,1, 1,0

## <a name="see-also"></a>Ayrıca bkz.

- [CallParameterizedFunction Yöntemi](icordebugeval2-callparameterizedfunction-method.md)
