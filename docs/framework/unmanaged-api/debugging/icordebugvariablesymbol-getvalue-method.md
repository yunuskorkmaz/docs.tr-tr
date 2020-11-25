---
title: 'ICorDebugVariableSymbol:: GetValue yöntemi'
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
ms.openlocfilehash: 0a57b1a31e1ef4b0db317012b25bc65ecbbaf011
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725969"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a>ICorDebugVariableSymbol:: GetValue yöntemi

Bir değişkenin değerini bir bayt dizisi olarak alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Bağımsız değişkenin bayt cinsinden boyutu `context` .  
  
 `context`  
 'ndaki Değeri okumak için kullanılan iş parçacığı bağlamı.  
  
 `cbValue`  
 'ndaki Arabelleğin bayt cinsinden boyutu `pValue` .  
  
 `pcbValue`  
 dışı Gerçekte arabelleğe yazılan bayt sayısı `pValue` .  
  
 `pValue`  
 dışı Değişkenin değerini içeren bir bayt dizisi.  
  
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
