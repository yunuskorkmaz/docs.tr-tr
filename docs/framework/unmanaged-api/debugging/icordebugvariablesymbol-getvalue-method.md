---
title: ICorDebugVariableSymbol::GetValue yöntemi
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 186d9eec0aa6ad9e327b1dd4d0f19e251c79ecf9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946191"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a>ICorDebugVariableSymbol::GetValue yöntemi
Bir bayt dizisi olarak bir değişkenin değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 [in] Değer okunacağı değişkeninde başlangıç uzaklığı. Bu parametre, bir nesne üyesi alanlarına okuma sırasında kullanılır.  
  
 `cbContext`  
 [in] Bayt cinsinden boyutu `context` bağımsız değişken.  
  
 `context`  
 [in] Değeri okumak için kullanılan iş parçacığı bağlamı.  
  
 `cbValue`  
 [in] Bayt cinsinden boyutu `pValue` arabellek.  
  
 `pcbValue`  
 [out] Gerçekte yazılan bayt sayısı `pValue` arabellek.  
  
 `pValue`  
 [out] Değişkenin değerini içeren bir bayt dizisi.  
  
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
