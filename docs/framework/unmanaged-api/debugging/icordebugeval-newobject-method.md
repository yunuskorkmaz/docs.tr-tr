---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıbgeval:: NewObject yöntemi'
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
ms.openlocfilehash: 0f7feb53d061e5dbc453015772b97f2a5a59bbb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693960"
---
# <a name="icordebugevalnewobject-method"></a>ICorDebugEval::NewObject Yöntemi

Yeni bir nesne örneği ayırır ve belirtilen Oluşturucu yöntemini çağırır.  
  
 Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor. Bunun yerine [ICorDebugEval2:: NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) kullanın.  
  
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
 'ndaki `ppArgs` Dizinin boyutu.  
  
 `ppArgs`  
 'ndaki Her biri oluşturucuya geçirilecek bir bağımsız değişkeni temsil eden ICorDebugValue nesnelerinin dizisi.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** 1,1, 1,0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [NewParameterizedObject Yöntemi](icordebugeval2-newparameterizedobject-method.md)
