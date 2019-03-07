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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6feef7b1e1f09107cd2a57555df07bebec86effa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466992"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a>ICorDebugEval2::NewParameterizedObjectNoConstructor Yöntemi
Belirtilen sınıfın yeni bir parametreli tür nesnesi, bir yapıcı yöntemini çağırma girişimi olmadan başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pClass`  
 [in] Oluşturulacak nesnenin sınıfını temsil eden bir Icordebugclass nesne işaretçisi.  
  
 `nTypeArgs`  
 [in] Tür bağımsız değişkenleri geçirildi.  
  
 `ppTypeArgs`  
 [in] Her biri örneği oluşturulan nesne için bir tür bağımsız değişkeni temsil eden bir Icordebugtype nesneye işaret eden bir işaretçiler dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `NewParameterizedObjectNoConstructor` Yanlış sayıda tür bağımsız değişkenleri varsa yöntemi başarısız olur ya da tür bağımsız değişkeni yanlış tür geçirildi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
