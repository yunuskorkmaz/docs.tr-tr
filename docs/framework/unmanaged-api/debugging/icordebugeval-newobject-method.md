---
title: ICorDebugEval::NewObject Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type:
- apiref
ms.openlocfilehash: 68a7e911c2bd1798ea8f34f6a6e24299fe68775d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137616"
---
# <a name="icordebugevalnewobject-method"></a>ICorDebugEval::NewObject Yöntemi
Yeni bir nesne örneği ayırır ve belirtilen Oluşturucu yöntemini çağırır.  
  
 Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor. Bunun yerine [ICorDebugEval2:: NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pConstructor`  
 'ndaki Çağrılacak Oluşturucu.  
  
 `nArgs`  
 'ndaki `ppArgs` dizisinin boyutu.  
  
 `ppArgs`  
 'ndaki Her biri oluşturucuya geçirilecek bir bağımsız değişkeni temsil eden ICorDebugValue nesnelerinin dizisi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** 1,1, 1,0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [NewParameterizedObject Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
