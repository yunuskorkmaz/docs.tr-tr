---
title: ICorDebugHeapValue::IsValid Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
ms.openlocfilehash: 7edf0065fa7eb39dada167a682f2b634a438f1f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138394"
---
# <a name="icordebugheapvalueisvalid-method"></a>ICorDebugHeapValue::IsValid Yöntemi
Bu ICorDebugHeapValue tarafından temsil edilen nesnenin geçerli olup olmadığını gösteren bir değer alır.  
  
 Bu yöntem 2,0 .NET Framework sürümünde kullanımdan kaldırılmıştır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pbValid`  
 dışı Yığın üzerinde bu değerin geçerli olup olmadığını belirten bir Boolean değer işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Değer çöp toplayıcı tarafından geri kazanımışsa geçersizdir.  
  
 Bu yöntem kullanım dışı bırakıldı. .NET Framework 2,0 ' de, tüm değerler [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) çağrılana kadar geçerli olur, bu durumda değerler geçersiz kılınır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
