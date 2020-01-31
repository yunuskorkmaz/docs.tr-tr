---
title: 'ICorDebugVariableSymbol:: SetValue yöntemi'
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
ms.openlocfilehash: fe6b63e4c0706dd69478753b3512f606e73bee7c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790849"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a>ICorDebugVariableSymbol:: SetValue yöntemi
Bir bayt dizisinin değerini bir değişkene atar.  
  
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
 'ndaki Değişkenin değeri ayarlanacak başlangıç boşluğu. Bu parametre, bir nesnedeki üye alanlarına yazılırken kullanılır.  
  
 `threadID`  
 'ndaki Bağlamını yeni değeri yansıtacak şekilde güncellenmesi gereken iş parçacığının iş parçacığı tanımlayıcısı.  
  
 `cbContext`  
 'ndaki İş parçacığı bağlamının bayt cinsinden boyutu.  
  
 `context`  
 'ndaki Değeri yazmak için kullanılan iş parçacığı bağlamı.  
  
 `cbValue`  
 'ndaki `pValue` arabelleğinin bayt cinsinden boyutu.  
  
 `pValue`  
 'ndaki Ayarlanacak değeri içeren arabellek.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugVariableSymbol Arabirimi](icordebugvariablesymbol-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
