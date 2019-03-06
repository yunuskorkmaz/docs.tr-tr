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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 66e51dc15f7d44ede26634571fa04c58e9735694
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364157"
---
# <a name="icordebugevalcallfunction-method"></a>ICorDebugEval::CallFunction Yöntemi

Belirtilen işlev çağrısı ayarlar.

Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor. Kullanım [Icordebugeval2::callparameterizedfunction](icordebugeval2-callparameterizedfunction-method.md) yerine.

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
[in] İşaretçi ICorDebugFunction nesneye çağrılacak işlevi belirtir.

`nArgs`\
[in] İşlev için bağımsız değişken sayısı.

`ppArgs`\
[in] İşleve geçirilecek bağımsız değişken belirtir Icordebugvalue nesneyi işaret her biri bir işaretçiler dizisi.

## <a name="remarks"></a>Açıklamalar

Sanal bir işlev ise `CallFunction` sanal gönderim yapar. İşlev farklı uygulama etki alanında ise, tüm bağımsız değişkenler de, uygulama etki alanında olduğu sürece, bir geçiş meydana gelir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** CorDebug.idl, CorDebug.h

**Kitaplığı:** CorGuids.lib

**.NET framework sürümleri:** 1.1, 1.0

## <a name="see-also"></a>Ayrıca bkz.

- [CallParameterizedFunction Yöntemi](icordebugeval2-callparameterizedfunction-method.md)