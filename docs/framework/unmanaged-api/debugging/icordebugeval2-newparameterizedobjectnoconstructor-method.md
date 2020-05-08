---
title: ICorDebugEval2::NewParameterizedObjectNoConstructor Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type:
- apiref
ms.openlocfilehash: 90fce1710f97341fb49be1d07f7af2edf8cb848c
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976089"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a>ICorDebugEval2::NewParameterizedObjectNoConstructor Yöntemi
Bir Oluşturucu yöntemini çağırmayı denemeden, belirtilen sınıfın yeni parametreli tür nesnesini başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pClass`  
 'ndaki Örnek oluşturulacak nesnenin sınıfını temsil eden ICorDebugClass nesnesine yönelik bir işaretçi.  
  
 `nTypeArgs`  
 'ndaki Geçirilen tür bağımsız değişkenlerinin sayısı.  
  
 `ppTypeArgs`  
 'ndaki Her biri, örneklendiği nesnenin tür bağımsız değişkenini temsil eden bir ICorDebugType nesnesine işaret eden bir işaretçiler dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yanlış `NewParameterizedObjectNoConstructor` sayıda tür bağımsız değişkeni ya da yanlış tür bağımsız değişken türleri geçirilirse yöntem başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
