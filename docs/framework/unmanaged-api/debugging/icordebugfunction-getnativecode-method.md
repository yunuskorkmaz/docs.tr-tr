---
title: ICorDebugFunction::GetNativeCode Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type:
- apiref
ms.openlocfilehash: 98aee38415709974d84873df50c39263490f2f23
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213276"
---
# <a name="icordebugfunctiongetnativecode-method"></a>ICorDebugFunction::GetNativeCode Yöntemi
Bu ICorDebugFunction örneğiyle temsil edilen işlevin yerel kodunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppCode`  
 dışı Bu işlev için yerel kodu temsil eden ICorDebugCode örneğine yönelik bir işaretçi veya bu işlev tam zamanında (JıT) derlenmiş Microsoft ara dili (MSIL) kodu ise null.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu örnek tarafından temsil edilen işlev `ICorDebugFunction` JIT olarak derlenmişse, genel türler söz konusu olduğunda, `GetNativeCode` rastgele bir yerel kod nesnesi döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
