---
description: ': ICorDebugVariableSymbol:: SetValue yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugVariableSymbol:: SetValue yöntemi'
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
ms.openlocfilehash: aa36712defcf44039f17fe846113c15814549e09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800857"
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
 'ndaki Arabelleğin bayt cinsinden boyutu `pValue` .  
  
 `pValue`  
 'ndaki Ayarlanacak değeri içeren arabellek.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugVariableSymbol Arabirimi](icordebugvariablesymbol-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
