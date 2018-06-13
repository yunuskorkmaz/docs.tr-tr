---
title: ICorDebugVariableSymbol::SetValue yöntemi
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ccdb78e522cb037821135c52bf762707f7de76c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422363"
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
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugVariableSymbol Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
