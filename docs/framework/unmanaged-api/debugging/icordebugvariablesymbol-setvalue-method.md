---
title: "ICorDebugVariableSymbol::SetValue yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 12c13259d20301b0f485a6041fa884b0996cbbdc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolsetvalue-method"></a>ICorDebugVariableSymbol::SetValue yöntemi
Bir bayt dizisi değeri bir değişkene atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `offset`  
 [in] Değeri ayarlanacak adresindeki değişkeninde başlangıç uzaklığı. Bu parametre, bir nesne üyesi alanlara yazılırken kullanılır.  
  
 `threadID`  
 [in] İş parçacığı tanımlayıcısı iş parçacığının bağlamı yeni değer yansıtacak şekilde güncelleştirilmesi gerekir.  
  
 `cbContext`  
 [in] İş parçacığı içeriğinin bayt cinsinden boyutu.  
  
 `context`  
 [in] Değeri yazmak için kullanılan iş parçacığı bağlamı.  
  
 `cbValue`  
 [in] Bayt cinsinden boyutu `pValue` arabellek.  
  
 `pValue`  
 [in] Ayarlanacak değer içeren bir arabellek.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET yerel ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugVariableSymbol arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
