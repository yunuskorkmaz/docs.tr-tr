---
title: ICorDebugVariableSymbol::SetValue yöntemi
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5c1c77b92d94062206cf9eb38981f38ff2a1cad
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775460"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a>ICorDebugVariableSymbol::SetValue yöntemi
Bir bayt dizisi değeri bir değişkene atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `offset`  
 [in] Değişkenin değerini ayarlamak, başlangıç uzaklığı. Bu parametre, bir nesne üyesi alanlara yazılırken kullanılır.  
  
 `threadID`  
 [in] İş parçacığı tanımlayıcısı, iş parçacığı bağlamı yeni değeri gösterecek şekilde güncelleştirilmesi gerekir.  
  
 `cbContext`  
 [in] İş parçacığı içeriğinin bayt cinsinden boyutu.  
  
 `context`  
 [in] Değeri yazmak için kullanılan iş parçacığı bağlamı.  
  
 `cbValue`  
 [in] Bayt cinsinden boyutu `pValue` arabellek.  
  
 `pValue`  
 [in] Ayarlanacak değer içeren arabellek.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugVariableSymbol Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
