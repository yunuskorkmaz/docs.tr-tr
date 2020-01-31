---
title: 'ICorDebugVariableSymbol:: GetValue yöntemi'
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
ms.openlocfilehash: 2dc074384d209d0740a1fb0a9a16d96ff355f02b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790880"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a>ICorDebugVariableSymbol:: GetValue yöntemi
Bir değişkenin değerini bir bayt dizisi olarak alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `offset`  
 'ndaki Değerin okunacağı değişkenin başlangıç boşluğu. Bu parametre, bir nesnedeki üye alanlarını okurken kullanılır.  
  
 `cbContext`  
 'ndaki `context` bağımsız değişkeninin bayt cinsinden boyutu.  
  
 `context`  
 'ndaki Değeri okumak için kullanılan iş parçacığı bağlamı.  
  
 `cbValue`  
 'ndaki `pValue` arabelleğinin bayt cinsinden boyutu.  
  
 `pcbValue`  
 dışı Gerçekten `pValue` arabelleğine yazılan bayt sayısı.  
  
 `pValue`  
 dışı Değişkenin değerini içeren bir bayt dizisi.  
  
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
