---
title: 'ICorDebugVariableSymbol:: GetName metodu'
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: 172eea452442aa94ea010e2c434908ab8d040a93
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790918"
---
# <a name="icordebugvariablesymbolgetname-method"></a>ICorDebugVariableSymbol:: GetName metodu
Bir değişkenin adını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cchName`  
 'ndaki `szName` arabelleğindeki karakterlerin sayısı.  
  
 `pcchName`  
 dışı Gerçekten `szName` arabelleğine yazılan karakter sayısına yönelik bir işaretçi.  
  
 `szName`  
 Değişken adını içeren bir karakter dizisine yönelik bir işaretçi.  
  
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
