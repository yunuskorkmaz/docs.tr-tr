---
title: ICorDebugVariableSymbol::GetName yöntemi
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73aa5a9ca6625ab58e451449fab4c98f8b83014e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422446"
---
# <a name="icordebugvariablesymbolgetname-method"></a>ICorDebugVariableSymbol::GetName yöntemi
Bir değişkenin adını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cchName`  
 [in] Karakter sayısını `szName` arabellek.  
  
 `pcchName`  
 [out] Gerçekte yazılan karakter sayısını gösteren bir işaretçi `szName` arabellek.  
  
 `szName`  
 Değişken adı içeren bir karakter dizisi için bir işaretçi.  
  
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
